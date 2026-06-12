---
title: "help on some words"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by ChuPp0 on 2008-01-04
Hello everyone
i'm new in da  ubuntu house :)
I have HP6720 s note book and have some problems on it

i tried to install compiz fusion but i can't enable desktop effects.
I tried to do something and i often have this answer in 

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

what is that public key? i have that warning often...

and please help me with desktop effects

---

### Post by Blindraven on 2008-01-04
```
gpg --keyserver subkeys.pgp.net --recv 2D6CFB44DD800CD9
gpg --export --armor 2D6CFB44DD800CD9 | sudo apt-key add -
```

---

