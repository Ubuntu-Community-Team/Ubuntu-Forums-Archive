---
title: "Ubuntu on hp dv6809wm"
date: 2008-10-08
forum: Hardware
---

### Post by icelechi on 2008-10-08
Hi,
I got an hp dv6809wm amd turion 64 x2 tl-60 and I would like to run Ubuntu on it. I do have some questions though:

Has anyone done this?
Are there things I should know before doing so?
Do I have to use the 64-bit version of Ubuntu?
Am I doomed to suffer the crashes and bugs of vista forever?

---

### Post by sergiom99 on 2008-10-09
well i cant tell you for sure without your detailed hardware specs.
It rans perfectly well in my DV6646us.
The better way to tell it is to put a LiveCD and see if all your hardware gets detected.
good luck.

---

### Post by icelechi on 2008-10-18
> **sergiom99 said:**
> well i cant tell you for sure without your detailed hardware specs.
It rans perfectly well in my DV6646us.
The better way to tell it is to put a LiveCD and see if all your hardware gets detected.
good luck.


Here are the specs:

**Operating System**            Windows Vista Home Premium
**CPU Type**                    AMD Turion 64 X2 TL-60 2.0G
**Screen** 	                    15.4" WXGA
**Memory Size** 	            3GB DDR2
**Hard Disk** 	            120GB
**Optical Drive** 	            DVD Super Multi
**Graphics Card** 	            NVIDIA GeForce 7150M
**Video Memory** 	            shared memory
**Communication** 	            Modem, LAN and WLAN
**Wireless**                    Atheros AR5009 802.11 a/b/g

Thanks

---

### Post by cl0ckwork on 2008-10-18
the only trouble you might get is with the wireless card, but with hardy its not too bad of an issuse and intrepid should be out soon (still beta) which has even better hardware recognition.

you probably won see much improvment in 64-bit vs. 32-bit

stick with 32 just for troubleshooting issues, aesier to deal with programs and such

---

### Post by sergiom99 on 2008-10-18
as you might have seen, besides the wifi card, all the rest of your hard is pretty much the same. you shouldnt have any problems installing ubuntu (or kubuntu for the same matter). And there are plenty of posts here about atheros cards to look for help if its not recognized out of the box. madwifi drivers should work ok.

---

### Post by icelechi on 2008-10-18
> **sergiom99 said:**
> as you might have seen, besides the wifi card, all the rest of your hard is pretty much the same. you shouldnt have any problems installing ubuntu (or kubuntu for the same matter). And there are plenty of posts here about atheros cards to look for help if its not recognized out of the box. madwifi drivers should work ok.


Thanks for the replies sergiom99,
Ok, I tried to install ubuntu 8.04 and it installed just fine, but there are two problems:

The screen resolution and THE WIFI!!

I am having quite a time finding posts to help with these. Could you point me to some?

Thanks

---

### Post by icelechi on 2008-10-19
Ok I have things sorted out now!!
Here's what I did:

First off, you will need to connect to the internet via an ethernet chord.

Go to *System > Administartion > Synaptic Package Manager* and go to *Settings > Repositories* and activate the boxes in the *Third-Party Software* and *Updates* tabs.
Go back to the Synaptic Package Manager and hit the *Reload* button.

**FOR THE SCREEN RESOLUTION**
Activate the Nvidia driver made available in Ubuntu by going to 
*System > Administration > Hardware Drivers*

**FOR THE WIFI**
Step-by-step instructions to get the wifi working is available at [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Hope this helps

---

### Post by sergiom99 on 2008-10-19
glad you got it working!
could also check>
-wlan: [http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)
-rest of hard: [http://ubuntuforums.org/showthread.php?p=5992241](http://ubuntuforums.org/showthread.php?p=5992241)

---

