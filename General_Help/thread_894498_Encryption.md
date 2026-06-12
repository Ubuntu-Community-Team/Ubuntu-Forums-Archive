---
title: "Encryption"
date: 2008-08-19
forum: General Help
---

### Post by Kain000 on 2008-08-19
Does anyone know what the encrypt option the comes up in the menu when you right click a folder does?  I wanted to encrypt a folder so my dad could download it form my server without anyone else being able to access it.    When I click the encrypt option it brings up a window to choose recipients but nowhere to add someone new.  Doesnt anyone know how to use this feature?

---

### Post by rjack on 2008-08-19
Can't help  with the menu front-end, but here's some bash-fu.

Compress and encrypt with a passphrase:```
tar -czf - your_directory | gpg --symmetric --output your_directory.tar.gz.cast5
```Enter the same passphrase twice and upload.

Decrypt and decompress:```
gpg --decrypt your_directory.tar.gz.cast5 | tar -xzf -
```Bonus: download, decrypt and decompress: ```
curl -s http://www.example.com/your_directory.tar.gz.cast5 | gpg --decrypt | tar -xzf -
```

---

### Post by Potatoj316 on 2008-08-19
you need to get your dad's public key and add it to you list of keys.  Then when you choose to encrypt encrypt it with your dad's public key and then he will be able to decrypt it

---

### Post by indiv on 2008-08-19
The part you're missing is that you need to have an encryption key.  When you right click and do Encrypt, the empty window that comes up is because you have no keys.

Click Applications | Accessories | Passwords and Encryption Keys.

The window that comes up is where you generate your own private key and import your dad's public key.

What I think you're supposed to do is have your dad generate a private key.  He sends you his public key and you import it into your key ring.  Now when you right click and Encrypt, you'll see your dad's key in the list, and you encrypt with his key.  Then you send the encrypted file to him, and he decrypts it with his private key (that he's assigned a password to, so he types in that password as well).

That's a real pain to coordinate.  I couldn't figure out how to make it decrypt with just a passphrase and no key exchange like the command-line given above.

---

### Post by Potatoj316 on 2008-08-20
> **indiv said:**
> That's a real pain to coordinate.  I couldn't figure out how to make it decrypt with just a passphrase and no key exchange like the command-line given above.

you only exchange keys once.  the command line version also requires a key exchange ahead of time

---

### Post by Kain000 on 2008-08-20
Alright, so If create new key, The profile that I am creating is for my self, ie: my email and name, and then  ask my dad to do the same and export a public key.  I then import his public key to my keyring and am then able to encrypt files for him.?

---

