---
title: "Sony vaio problem whit X"
date: 2009-01-14
forum: Hardware
---

### Post by Nightly on 2009-01-14
I have a Sony vaio VGN-FW145E with GMA X4500HD, I installed the 32-bit version of kubuntu Intrepid, I am able to get to the login screen, but after I log in, the screen is messed up. I have tried to install driver. and config xorg.conf but I'm not sure if I'm doing it right." X system work only whit "vesa" driver . but work only 800x600 i want 1600x900
try whit i810 and intel driver.. but nothing... 
xorg-server 2:1.5.2.-2ubuntu3
2.6.24-19-I686 Ubuntu

---

### Post by metapaso on 2009-01-18
> **Nightly said:**
> I have a Sony vaio VGN-FW145E with GMA X4500HD, I installed the 32-bit version of kubuntu Intrepid, I am able to get to the login screen, but after I log in, the screen is messed up. I have tried to install driver. and config xorg.conf but I'm not sure if I'm doing it right." X system work only whit "vesa" driver . but work only 800x600 i want 1600x900
try whit i810 and intel driver.. but nothing... 
xorg-server 2:1.5.2.-2ubuntu3
2.6.24-19-I686 Ubuntu

Sometimes its hard to get the right people to see your new posts.  Consider revising your post to add a little more detail and put it onto the end of the X4500HD WOES forum 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=889323&page=18](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=889323&page=18)

Also, Attaching your xorg.conf file to your post is very important.

Some tips before you post:
make sure you have the xorg-edgers ppa enabled in your sources list so that you get the most recent drivers.  Make sure your computer is fully updated.  If you don't know how to do these steps, you can ask me.

---

### Post by Entwicklung Medizinproduk on 2009-01-18
Sony vaio have nice features but I've heard a lot of problem about it. I'm planning to buy one but I'm really confused about what I've heard.

---

### Post by densou on 2009-01-20
> **Entwicklung Medizinproduk said:**
> Sony vaio have nice features but I've heard a lot of problem about it. I'm planning to buy one but I'm really confused about what I've heard.

Indeed: (related to intel-video-drivers)
**Known Issues**
- *GM45 Sony Vaio panels (known impacted models: VGN SR11M, SR19XN, FW140E/H, FW170J, FW235, Z11WN) startup fails: bug#17292.*

or buy one with an ATI or a nVidia card ;)

---

