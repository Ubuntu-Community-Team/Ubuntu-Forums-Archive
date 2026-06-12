---
title: "Dell server"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by SKL BOI on 2009-06-09
HI

I am extremely new to Linux but very interested in learning.

I'm am turning a old Dell Desktop into a Server and when installing the Ubuntu Server 9.04 it has set it all up but then displays the message:
 "Please insert the disc labeled: "Ubuntu-server 9.04 _Jaunty Jackalope_ - Release i386 (20090421.1)" in the drive  "/cdrom/" and press enter."

This is whats in the drive. freshly downloaded form the ubuntu website the i386 version of the ubuntu server 9.04!

So what does it mean and how can i fix it?

Any help will be greatly appreciated1

Thanks

SKL BOI

---

### Post by dstew on 2009-06-09
What happens when you press enter?

EDIT: You can remove or comment-out the "cdrom" lines in your /etc/apt/sources.list file.```
sudo nano /etc/apt/sources.list
```

---

### Post by SKL BOI on 2009-06-10
Hi

Sorry but I realised while fiddling about with it that i can't seem to set up my dell to boot from USB so I'm currently on the Dell Forum finding a way when I get an answer (either way) then ill give it another go on a hard disk.

It does nothing when I pressed enter it just kept the same message up! 

Thanks

SKL BOI

---

