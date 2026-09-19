# RSAStego

## Description

This challange is from picoCTF 2026.Here you got the encrypted flag and an image.

Here we have to find RSA private key using that image because RSA public is somehow lost

___

## Intial Analysis 

In hints sections of picoCTF,there is a hint pointing toward the metadata.

So,i try to look at the image metadata.

___

## Solution

1.While looking at metadata by exiftool

'''bash
exiftool image.jpg
'''
2.I found a large comment down there.while analysing it,i got that thing as hex encoded.

So i run 

'''bash 
echo "Comment" | xxd -r -p
'''
3. After running that command i got RSA Private Key 

4.Then i create the file named private.pem and put key in it 

### Command used to create file

'''bash
nano private.pem
'''

5.Then after that we have to decrypt the file by using key 

'''bash
openssl pkeyutl -decrypt -inkey private.pem -in flag.enc -out flag.txt
'''

6. After decryption,we have a plain text flag now.

7.Read the key using `cat`.

'''bash
cat flag.txt 
'''

8.We have a flag now.

