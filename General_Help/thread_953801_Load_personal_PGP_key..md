---
title: "Load personal PGP key."
date: 2008-10-20
forum: General Help
---

### Post by superbenny on 2008-10-20
I just reinstalled ubuntu, and I need to know how I can reload my PGP key into seahorse so I can sign other keys.

---

### Post by Dr Small on 2008-10-20
Do you have your GPG Private Key on file?
If so, just run:
```
gpg --import filename
```

---

### Post by superbenny on 2008-10-20
> **Dr Small said:**
> Do you have your GPG Private Key on file?
If so, just run:
```
gpg --import filename
```


no only the public...unfortunately.

---

### Post by kevdog on 2008-10-21
Dont you need a private key to due the actual signing?

---

### Post by Nepherte on 2008-10-21
> **kevdog said:**
> Dont you need a private key to due the actual signing?
Yes, without the private key you can forget about signing.

---

### Post by geirha on 2008-10-21
Did you back up your homedir before reinstalling? If you have the ".gnupg" directory from your old homedir, you'll be able to get your secret key back.

---

### Post by Dr Small on 2008-10-21
> **superbenny said:**
> no only the public...unfortunately.
Well basically your key is useless now, since if someone encrypts to it, you won't be able to decrypt the contents. It is good practice to backup your .gnupg directory before reinstalling, and better practice to keep that directory on a floppy disc or thumb drive.

---

