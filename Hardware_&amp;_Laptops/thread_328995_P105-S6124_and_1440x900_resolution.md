---
title: "P105-S6124 and 1440x900 resolution?"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by Nomadadon on 2006-12-31
I'm trying to put Edgy on a P105 with the i945 chipset  and get it into 1440x900 widescreen resultion.  I've tried the i810, intel and vesa drivers but none of them give me anymore than 1280x1024.  

If someone has it working can you post an xorg.conf ortell me what's wrong?  

If I run 915resultion it reports the 1440x900 as detected but thats as close as I can get.

---

### Post by Nomadadon on 2007-01-05
No one has a P105 working in 1440x900?  I know it works in windows just fine.

---

### Post by mcdsco on 2007-08-17
The best way is to do the following:

Open your terminal and issue the following command:

     sudo apt-get install xserver-xorg-video-intel

rebooting your system should result in the proper display mode as 1440x900 ... if not ... 

Click on System --> Preferences --> Screen Resolution ...

---

