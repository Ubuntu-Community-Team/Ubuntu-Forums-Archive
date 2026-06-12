---
title: "[SOLVED] PGP key strength not what I selected"
date: 2008-11-16
forum: General Help
---

### Post by g0l3m on 2008-11-16
Hello all,

Using the Passwords and Encryption Keys app, I've created a new PGP key (this is all under Ubuntu 8.10).

Under the advanced options, when creating the key, I chose DSA Elgamal and a strength of 4096 bits. Key was created and all seemed good.

However, when I right click on the newly created key and choose properties, under the details tab it shows a strength of 1024!

Am I doing something wrong? I chose 4096...why did it create one with 1024 bits?

cheers,
g.

---

### Post by Th3Professor on 2008-11-16
You might have better luck via command line:
```
gpg --gen-key
```

---

### Post by g0l3m on 2008-11-18
Same thing via command line.
I think I may be looking at the output from the UI wrong.
Under the details tab (when you right click on a key and do properties) it says type DSA, strength 1024. BUT, when I expand the subkeys, there's another key with type ElGamal and strength 4096.

---

