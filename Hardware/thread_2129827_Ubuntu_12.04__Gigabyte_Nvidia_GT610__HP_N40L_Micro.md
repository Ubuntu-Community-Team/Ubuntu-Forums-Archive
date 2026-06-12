---
title: "Ubuntu 12.04 / Gigabyte Nvidia GT610 / HP N40L Micro - Purple and Black Boot Screen"
date: 2013-03-27
forum: Hardware
---

### Post by Simon1049 on 2013-03-27
Hi,

I have the following media server setup:
HP MicroServer N40L
Ubuntu 12.04 LTS (Using Gnome instead of Unity)

My system was running fine, until I tried to install a graphics card (Gigabyte Nvidia GT610) to use the system as a media server and not just a file server. The system boots to a purple screen with black bars and lines. I have never installed NVidia drivers or anything.

The system does boot again if I remove the card, and works fine, but before booting it says PXE-E61 Media Test Failure, check cable.
One of the hard drives is quite old but the same error appears even if that drive is taken out. After the message is displayed it boots normally.

What would be my next step? (Would like to try and minimise the number of times I need to add and remove this card from the system.)

---

### Post by Simon1049 on 2013-03-27
[http://imgur.com/Lu8bM5u](http://imgur.com/Lu8bM5u)

---

### Post by oldfred on 2013-03-27
With nVidia you need nomodeset until you install the nVidia drivers.

It seems you have network boot (PXE) before hard drive boot in BIOS boot order?

       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

