---
title: "Lorex DMC2161 Webcam Help"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by radioraheem on 2008-03-14
I just picked up a Lorex DMC2161 (part of the mCam series) and for the life of me I cannot find a working solution. It's basically [this camera]("http://dealscctv.lorextechnology.com/product.aspx?id=1734"), and [this link]("http://dealscctv.lorextechnology.com/mediaresults.aspx?modelNo=DMC2161") goes to Lorex's specific page for this model's documentation.

 I've tried installing gqcam, camstream, cheese, amsn, and camorama.  

Of course after I tried installing all of these I found a thread that talked about the lsusb command (VERY handy, can't believe I never ran into it before) and it does not appear that the camera is being detected.

> 
jallen@optimus:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 12d5:0100  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 046d:c512 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  


The Logitech line is my wireless keyboard/mouse combo.

I'm having a really hard time finding the chipset this webcam is based on, so I'm hoping someone can point me to a reference or other documentation (lorex does not appear to have this info on their web site).  Or even better, maybe someone out there has tried to setup this camera in Linux and can set me on the right path.

This is basically my last option for help before I have to setup a windows box to handle it, and I'd rather not do that as my house has been Windows-free for over 2 years now thanks to Ubuntu.

Many thanks in advance for any help people have to offer!

---

### Post by linuxwizard on 2008-03-14
Searching around I can not find anything on your cam > Bus 001 Device 002: ID 12d5:0100 > not sure where else to look. Just a suggestion can you take back this cam and find one that is supported in Linux.

---

