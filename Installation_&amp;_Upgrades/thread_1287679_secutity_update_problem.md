---
title: "secutity update problem"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by dlteach2 on 2009-10-10
I was able to retrieve my password - thank you. However, as soon as I opened ubuntu, there was a popup about several security files to be updated. I used the update manager and got the following response:

"w. failed to fetch [http://security.ubuntu.com/ubuntu/po...2.2-11.3ubuntu]("http://security.ubuntu.com/ubuntu/pool/main/n/newt/python-newt_0.52.2-11.3ubuntu") 3.1-1386.deb
could not resolve 'security.ubuntu.com'



"w. failed to fetch [http://security.ubuntu.com/ubuntu/po...tu3.1-i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/n/newt/librewto.52_O.52.2-11,3ubuntu3.1-i386.deb") 
could not resolve 'security.ubuntu.com'


Also, the games stopped working - can't move the cards in solitaire. 

Please advise, thank you.

---

### Post by Partyboi2 on 2009-10-11
Open a terminal (Applications>Accessories>Terminal) and reload the package list first.
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dlteach2 on 2009-10-12
Okay. Could you confirm first, as this is my first time doing this, that the following current text in the terminal area is accurate. Do I just enter the code you recommended after that? I would like to change the name of the laptop as soon as I can. Can I safely do it even without the security updates? How do I do it?

Current text gives my laptop name followed by a colon followed by a squiggle and then a dollar sign and colon

---

