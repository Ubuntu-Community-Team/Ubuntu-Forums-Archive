---
title: "Help installing Real_Player"
date: 2005-11-09
forum: General Help
---

### Post by ubuntu27 on 2005-11-09
I been folowing ths instruction from the WIki: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2508483)

This is what I get:
```

ubuntu27@heaven:~$ chmod +x RealPlayer10GOLD.bin
ubuntu27@heaven:~$ sudo ./RealPlayer10GOLD.bin
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ubuntu27@heaven:~$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ubuntu27@heaven:~$ 
```

Thanks in advance !! :D

---

### Post by krye on 2005-11-09
have you tried installing the library?

sudo apt-get install libstdc++5

(I guess it's v5 the one it asks for)

---

### Post by strawman on 2005-11-09
i ran into that problem also.  what worked for me was adding these lines to my /etc/apt/sources.list

 deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

run sudo apt-get update and install realplay which will install libstdc++.so.5 along with Realplayer10 for you.  this worked for me.

---

### Post by ubuntu27 on 2005-11-09
Thanks, everybody. I was able to solve my priblem by installing the libstdc++5 Library.  

It kind of get my attetion [I wonder]... that even thougu I had libstdc++6, I needed the version 5... that's weird...

---

