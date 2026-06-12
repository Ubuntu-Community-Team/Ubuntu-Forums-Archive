---
title: "unable to activate broadcom"
date: 2009-11-12
forum: Hardware
---

### Post by menabeorth on 2009-11-12
hello,

i followed this thread [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865) and successfully installed 'dkms' and 'bcmwl-kernel-source' via usb, in hope that Broadcom will be detected.

it did work! but the problem is after many efforts to activate through Hardware Drivers, on my right it is still 'this driver is not activated'.

02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

have i overlooked something simple? (or perhaps not so!) or is there something else can be done about it? really really miss networking.. updating packages and.. stuff... thank you very much in advance!

---

### Post by wandalalakers on 2009-11-12
I'm using a Dell D620 with Broadcom 4312 and I was able to get my wireless working using the Karmic Live CD.
This is what I see installed using Synaptic.  
Try and see if the programs below are installed.
If not, download the debs for those to your usb also.

bcmwl-kernel-source - you already have on usb
bcmwl-modaliases
wireless-tools
libiw29
wireless-crda
pcmciautils
wpasupplicant

I also enabled: broadcom sta wireless driver using hardware drivers.

---

### Post by uberlube on 2009-11-12
If none of that works try the howto in my guide

---

### Post by JBAlaska on 2009-11-12
> **pcdoctor said:**
> i'm using a dell d620 with broadcom 4312 and i was able to get my wireless working using the karmic live cd.
This is what i see installed using synaptic.

**bcmwl-kernel-source**
bcmwl-modaliases
wireless-tools
libiw29
wireless-crda
pcmciautils
wpasupplicant

**i also enabled: Broadcom sta wireless driver using hardware drivers**.

**+1**

---

### Post by wandalalakers on 2009-11-12
Guess what.
Just for giggles, I installed 9.10 on my laptop with LM 8.04 kde and now I can't use the wireless with 9.10.  The Broadcom STA wireless driver will not activate once I installed it to the hard drive but it would activate the Broadcom STA using the Live CD.  I already have LM 8.04 KDE on the laptop and I just trying to see if 9.10 would see my wireless once I installed it to the hard drive.

---

### Post by mikewhatever on 2009-11-12
That appears to be a known bug, cause Broadcom drivers were auto activated in Jaunty. If someone wants a more detailed solution with pictures and stuff, check out the link below.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by menabeorth on 2009-11-12
thank you everyone for your suggestion! but..!

to pcdoctor:
all debs you listed have been installed. when i opened Hardware Drivers, 'Broadcom STA proprietary wireless driver' is detected. then on i activated it, entered my password for authentication. and it still shows *"This driver is not activated."* however, didn't forget to restart. i reopened my Hardware Drivers again to check. Broadcom is still not activated!

to uberlube:
for some reason, LiveCD doesn't work for me, it should have, no? Karmic and all file installations from the beginning have been done through USB. from there i realised that i had to install 'ndiswrapper-common' before 'ndiswrapper-utils'.

to mikewhatever:
i wish i could give your solution a go! but my LAN also doesn't work.

i have a massive wish to know what's wrong. if anyone can figure out any other way, i would really appreciate it. i don't want to give up on Karmic just yet. tasted a little bit of its development, and heard it is a fantastic version!

---

### Post by davidshere on 2009-11-12
> **mikewhatever said:**
> That appears to be a known bug, cause Broadcom drivers were auto activated in Jaunty. If someone wants a more detailed solution with pictures and stuff, check out the link below.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

I mainly use Ubuntu as a Live CD, and have gone back to Jaunty because of this problem only.  If 9.10.1 comes out, with this problem solved, I'd use that.  I can (sometimes) successfully activate and use the wireless drivers (which doesn't require me to connect with a wire), but most of the time the computer becomes unresponsive after I do so.

I sure wish I had particiapted in testing because I'd certianly have pointed this out.  When I looked into testing Karmic, I was under the impression that Karmic would not be avialable as a Live CD, so I didn't pursue it.

---

### Post by menabeorth on 2009-11-14
i have left Karmic to Jaunty today! what an afternoon delight!

---

### Post by mikewhatever on 2009-11-14
> **menabeorth said:**
> thank you everyone for your suggestion! but..!

to pcdoctor:
all debs you listed have been installed. when i opened Hardware Drivers, 'Broadcom STA proprietary wireless driver' is detected. then on i activated it, entered my password for authentication. and it still shows *"This driver is not activated."* however, didn't forget to restart. i reopened my Hardware Drivers again to check. Broadcom is still not activated!

to uberlube:
for some reason, LiveCD doesn't work for me, it should have, no? Karmic and all file installations from the beginning have been done through USB. from there i realised that i had to install 'ndiswrapper-common' before 'ndiswrapper-utils'.

to mikewhatever:
i wish i could give your solution a go! but my LAN also doesn't work.

i have a massive wish to know what's wrong. if anyone can figure out any other way, i would really appreciate it. i don't want to give up on Karmic just yet. tasted a little bit of its development, and heard it is a fantastic version!

Could that be because of ndiswrapper? The proprietary driver you've been trying to activate works natively on Linux. If you want to use ndiswrapper, get Windows driver instead.

[http://en.wikipedia.org/wiki/NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper)

---

