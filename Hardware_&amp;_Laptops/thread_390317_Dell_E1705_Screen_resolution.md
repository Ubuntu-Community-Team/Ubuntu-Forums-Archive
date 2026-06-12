---
title: "Dell E1705 Screen resolution"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by Kamikaze Wardriver on 2007-03-21
I recently installed ubuntu on my new Dell E1705. I downloaded the 915 screen resolution. I then ran dpkg reconfigure xserver-xorg to configure the xserver. Everything was fine until rebooted. After that I was no longer able to log into ubuntu. It load the splash screen and then just freezes. I can logon to ubuntu in recovery mode, so I am pretty sure that it is the video settings that is freezing things up. I was just wondering if anyone has experienced this problem before. I would like to know what I might have set wrong before I go around changing things blindly. By the way my dell has the ATI card not the NVIDA one.

---

### Post by strabes on 2007-03-21
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

That should work and you shouldn't need 915resolution. Once you install xorg-driver-fglrx, rerun dpkg reconfigure xserver-xorg and choose fglrx as your video card driver. If you still can't boot into ubuntu normally and you need to add the following to your xorg.conf, you can use the safe mode and edit xorg.conf from a terminal using "sudo nano /etc/X11/xorg.conf"

> Section "Extensions"
        Option      "Composite" "0"
EndSection

I made the same mistake of choosing the ATI card over Nvidia. I have the exact same laptop (E1705). Which ATI card do you have? I have the Mobility X1400. 

Hope this helps.

---

### Post by Kamikaze Wardriver on 2007-03-21
> **strabes said:**
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

That should work and you shouldn't need 915resolution. Once you install xorg-driver-fglrx, rerun dpkg reconfigure xserver-xorg and choose fglrx as your video card driver. If you still can't boot into ubuntu normally and you need to add the following to your xorg.conf, you can use the safe mode and edit xorg.conf from a terminal using "sudo nano /etc/X11/xorg.conf"



I made the same mistake of choosing the ATI card over Nvidia. I have the exact same laptop (E1705). Which ATI card do you have? I have the Mobility X1400. 

Hope this helps.


Thanks,

I saw about 50 post on how to resolve the screen resolution but all of them were for the NVIDA. I never saw the link you gave. That looks promising. Thanks.

---

### Post by digitalbenji on 2007-05-18
I have the ATI card and I've got some nice resolutions going for me.  I used the aticonfig tool I believe.  If you like, I can post my xorg.conf for you, as mine should work for you.  Mine is also tweaked for beryl with xgl.  

Thanks,

---

