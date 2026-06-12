---
title: "No Public Key?"
date: 2008-10-23
forum: General Help
---

### Post by Gondee on 2008-10-23
Here what i get when i attempt to do sudo apt-get update, well actully it says it when its done, but yeah.

```
W: GPG error: http://deb.mulx.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268
W: You may want to run apt-get update to correct these problems

```

What does this mean, and how do i fix it??

-Josh

---

### Post by scragar on 2008-10-23
try running:
```
wget -q http://deb.mulx.net/pol.gpg -O- | sudo apt-key add -
```
and run the apt-get update again.

---

### Post by Gondee on 2008-10-23
That did it. Thanks man

What did that do by the way?

---

### Post by scragar on 2008-10-24
The gpg file is used to veryify the identity of the server apt is comunicating with, so when apt couldn't find it then it complained at you, I opened up the downain you pointed to, spotted the download link for the .gpg file, and inserted it into that line:
```
wget                    Download
-q                         Quite, no messages
http://deb.mulx.net/pol.gpg        the gpg file
-O-                         and otput it
|                         into
sudo                       admin rights to
apt-key                    key manager
add                        add a key
-                         from input
```
hope that explains it well enough.

---

### Post by hafthanhf on 2009-06-22
hey guy, I've done as you said but, ubuntu reply me as follows:
gpg: no valid OpenPGP data found.

---

### Post by Agent ME on 2009-06-22
mulx.net doesn't seem to exist any more.

Did you get the same exact error message that the original poster did? It seems like maybe you got a similar one and decided to ask for help here; post your error message, since it's probably for a different key.

---

