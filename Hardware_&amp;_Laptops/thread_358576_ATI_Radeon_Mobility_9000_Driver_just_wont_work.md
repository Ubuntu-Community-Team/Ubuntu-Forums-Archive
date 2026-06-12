---
title: "ATI Radeon Mobility 9000 Driver just wont work"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by rwyankees on 2007-02-11
I currently have a Dell 600m with a ATI Radeon Mobility 9000.  I had it running about 3 weeks ago then I started messing with beryl and ended up screwing up my system and having to reformat.  I am really new to Ubuntu so I probably didn't have to reformat I just didn't know what else to do.  Ever since then I can not get my graphics card to work right.  I mean it displays stuff but doesn't do any 3d rendering.  My panel at the bottom always seems to have scrambled lines behind the icons, web pages scroll SUPER SLOW, I just can't seem to get it working.  I can't seem to EVER get the driver to install right.  I have re formated at least 3 times in the past couple days cause I keep messing with the xorg.conf file trying to get it all to work and then i mess something up.  If someone can PLEASE PLEASE help me get this card installed and working properly it would be much appreciated.

](*,)  ](*,)  ](*,)

---

### Post by Waappu on 2007-02-11
Hi

Do you try install "fglrx" driver?
Open source driver working ok to me with ATI 9250. Here is my /etc/X11/xorg.conf file for example
[http://koti.mbnet.fi/waappu/download/xorg.conf](http://koti.mbnet.fi/waappu/download/xorg.conf)
Also I have collected few good links here
[http://koti.mbnet.fi/waappu/](http://koti.mbnet.fi/waappu/)

---

### Post by mrmustardman on 2007-12-23
i am in the same situation, although i am sure a reformat would solve all my issues, i own a 600m aswell... with 9000 mobility... my destop is fine, i dont have any lines behind my icons, but ever since i started ******* with beryl, my games dont work at all, and ive recently been having some issues with my xorg.conf file randomly being deleted, and suddenly being changed... its all very strange but ive seemed to have worked around it all... you could try typing
dpkg-reconfigure xserver-xorg
but in essence, that should have happened when you reinstalled the whole OS...

dont know, only thing that wont work on my 600m is the games... lines for textures, some not even rendering...

---

