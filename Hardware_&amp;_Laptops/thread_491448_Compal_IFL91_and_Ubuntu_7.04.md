---
title: "Compal IFL91 and Ubuntu 7.04"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by victorperezmon on 2007-07-03
Hi friends.
this is my first post here from Spain and i expect you can help me.
I have a new notebook Compal IFL91 with following hardware: Chipset Intel 965 GM, Core 2 Duo T7300, 1 gb RAM 667 Mhz, X3100 intel graphics, Sata hard disk 60 Gb, Audio ALC268, PCI express card, SD/MMC Card Reader, DVD+-RW, Broadcom net 10/100, etc... 

I have tried to install Ubuntu 7.04 with desktop cd-rom but i have problems because Live-cd does not boot at all.
I have done following
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)

I do it and i can boot live cd but i don get video, so i can't install it.

Then i have tried another method. i use alternate cd and i can install ubuntu 7.04 but when installation is finished and i reboot system i have my system installed wtihout video, that i can get with xserver-xorg-video-intel package, but i can't access cd-rom unit because it is not recognized by system.

I need help to install Ubuntu. I have booted system with knoopix 5.1 and its ok...

Can anybody help me....

If you have any doubt please ask me it...

Thanks and regards.

---

### Post by Innomatics on 2007-07-04
> **victorperezmon said:**
> 
I have a new notebook Compal IFL91 with following hardware: Chipset Intel 965 GM

Hi 

Yes that's a very new model! I'm not sure if there will be many people with this brand new chipset (Santa Rosa) up and running already with Ubuntu.  Could be that intel integrated display drivers  for 965GM/X3100 are not in the repository just yet, so you may have to compile you own, or wait until support in offered.

Have you been here?

[http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)

Sorry I can't more help just now, although I am very interested in your outcome as I have just ordered a notebook also compal with the same chipset.

---

### Post by victorperezmon on 2007-07-05
Yeah i will inform you about my advances with this new model.

I am trying to get sound working. I have sound but there is no micro .
I have got video 1280*800 and direct rendering yes but i am going to try to install intel drivers now.

Thanks and regards.

---

### Post by quizy101 on 2007-08-15
I am having troubles on my own IFL-90, but I have an Nvidia 8600M GT but no video. Let me know if anyone figures this out. Thanks!

---

### Post by Innomatics on 2007-12-06
In case you haven't already found it, this page is the authority on Ubuntu and the IFL90:

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/)

Much is relevant also to the IFL91, except for video/display issues.

---

### Post by TornMorals on 2007-12-07
I was going to get an IFL90 but the wait was too long I got fed up at 3 months of release and my screen size was having production problems so I upgraded to the Sager NP9261, but I did have a problem like this.  I had an error similar to this though.  I have read the fix is in the xorg.conf and you need to switch terminals CTRL+ALT+F1-7 and switch the driver.  But mine was not getting that far.  If that guide dose not work I'd suggest removing the 2 options at the end the boot menu. I beleave that they are Silent and Quick.  F2 should allow you to change that before the CD boots.  You will have to edit the Grub menu by mounting it manually and doing that before your fist boot too.  I'm going ahead and saying this because that was related to my video card and could be related as the 8700m seams to be an overclocked 8600m GT.

---

### Post by c1rcu17 on 2008-01-02
I have the IFL90 and am on Gusty now. Upgrade to 7.10, the new kernel supports many more hardware pieces than 7.04 Feisty did. Also, the 

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/)

is a great resource for that notebook.

---

### Post by Stunts on 2008-02-19
> **c1rcu17 said:**
> I have the IFL90 and am on Gusty now. Upgrade to 7.10, the new kernel supports many more hardware pieces than 7.04 Feisty did. Also, the 

[http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/](http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/)

is a great resource for that notebook.

Hi I've also got this model working with Ubuntu 7.10. Everything except sound and memory card reader worked out of the box! I just followed the how-to's in the mentioned website to get them up & running. The only thing that is not working right now is the fingerprint reader, and that is due to the lack of software for it on linux.

This is lot more than I can say for Win XP, which refused to install since it didn't recognize my SATA HD. Had to hack the CD to get it running...

There are also four buttons that I cannot get to do anything tho. The "Wow Video" and "Wow Audio" buttons on the top of the keyboard and and the two buttons with the power plug and USB symbols pn the left of the keyboard. Anyone got these to do anything?

---

