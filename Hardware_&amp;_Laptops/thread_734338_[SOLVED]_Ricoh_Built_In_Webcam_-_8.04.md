---
title: "[SOLVED] Ricoh Built In Webcam - 8.04"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by moinster on 2008-03-24
Hello everyone.
I am using Ubuntu 8.04 on a HP Pavilion dv1000.

I have a built in webcam that just wont work(but have a usb plug in webcam that works fine).  I want to use it with Skype so I can talk to my family in Germany.  I was doing some looking and found out that r5u870 was working for some people.  But it would work with an older version of the kernel, from my understanding.  Is there an update of that driver that would work with 8.04 and 2.6.24-12-generic?

My lsusb is
```

Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c510 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

```

Any help would be nice.

Thank you.

EDIT

PS here is my lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by teaker1s on 2008-03-24
may help
[https://wiki.ubuntu.com/HP_dv6000_Series?highlight=%28dv6000%29#head-ad1d9176c133fb2f0463c5f254b511654fa68b6e]("https://wiki.ubuntu.com/HP_dv6000_Series?highlight=%28dv6000%29#head-ad1d9176c133fb2f0463c5f254b511654fa68b6e")

---

### Post by syko21 on 2008-03-25
[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)
That updated driver works with the new kernel.

---

### Post by samcompton on 2008-04-20
I am running Ubuntu 8.04 rc.  Under Gutsy my webcam worked great using the r5u870 driver.  I was able to install the deb and everything was good.  Of course that same deb will not install in Hardy Heron being a new kernel.  I downloaded a new version (tarball was all I could find  [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870))   I compiled the new driver.  It works somewhat.  It does not work with cheese.  So I tested it with Ekiga.  Ekiga recognizes my webcam.  When it first starts up, everything looks good for a second or two.  Then the webcam output slowly distorts and ends up looking like a negative image.   Any help would be very appreciated.

Thanks

---

### Post by syko21 on 2008-04-20
The driver only works with skype for me and outputs a normal picture to xawtv. It also works when testing in gstreamer-properties. From gutsy to hardy cheese and effectv broke with this webcam.

---

### Post by samcompton on 2008-04-21
Thanks syko.  I had not tried xawtv before.  When I installed it there were some dependencies installed that I didn't have before.  Sorry I didn't pay attention to what they were.  Whatever they were.  It got rid of the negative image effect.  Now I have clear output with xawtv, Skype and Ekiga.  

Thanks for the help.

---

### Post by oooh on 2008-04-28
Downloaded the trunk version of the driver R5u870 (version 0.11.1) from [http://wiki.mediati.org/Installation](http://wiki.mediati.org/Installation). Made in root:
-make
-make install
-modprobe r5u870
Restarted and:
-works in gstreamer-properties
-works in Ekiga, and Skype
-does not work in amsn (dark screen and no chance to control brightness, -contrast and so) 
-does not work in cheese (does not recognize device)

---

### Post by syko21 on 2008-04-28
I just recently found the program wxcam which helps set the brightness/contrast/hue for your webcam. It's found here [http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)
I can't vouch for it in Hardy but I'm using it without problem in Gutsy.

---

### Post by oooh on 2008-04-29
syko21 , it looks as if it is only for i386 arquitecture, and mine is 64, so it does not let me install it ... is there a way to control brightness directly with gstreamer?

---

### Post by syko21 on 2008-04-29
no clue, I just found this software recently and until then I always used proper(excessive) lighting to get a good view out of my webcam. You can try compiling the source code using the instructions on the wxcam website and see how that goes.

---

### Post by quiricada on 2008-04-30
patrick niklaus built a package for it, am using it, no problem on sony vaio vgn-fe48g/h

[https://bugs.launchpad.net/ubuntu/+bug/120434](https://bugs.launchpad.net/ubuntu/+bug/120434)

---

### Post by syko21 on 2008-04-30
He has not built a package for the Hardy kernel and the version that is at the link on the bug report is version 0.10 which does not compile on 2.6.24.

---

### Post by charlemagne86 on 2008-05-23
okay ppl

i installed the r5u870 driver version 11 and ekiga detect my webcam




only problem is cheese does not.....can i fix this?


and also after jus a couple of seconds, the image begins turning all distorted with green and red shades everywhere.....



help!!

---

### Post by charlemagne86 on 2008-05-23
okay installed xawtv and the funny colors are gone.....what about cheese then??



UPDATE>>camorama can't detect the devide....error reports Cant connect to video devide /dev/video0 (which is the correct video devide)

any suggestions>?

---

### Post by charlemagne86 on 2008-05-23
HELP!!


after reboot the funny colors are back again.......however if in ekiga i readjust the brightness meter by even a sliver, the funny colors are gone..agian...upto the next reboot!!!



wat do i do >??????????:confused::confused::confused::confused:

---

### Post by syko21 on 2008-05-23
Search synaptic package manager for any package associated with video4linux, v4l. One of them fixes the issue its just that I don't know which one. It only fixes the weird shades of color though, cheese is still incompatible with the r5u870 driver.

---

### Post by anpu1 on 2008-05-23
i have the same problem with the negative image colors!! any help??? what to do? i'm using hardy

---

### Post by charlemagne86 on 2008-05-24
> **syko21 said:**
> Search synaptic package manager for any package associated with video4linux, v4l. One of them fixes the issue its just that I don't know which one. It only fixes the weird shades of color though, cheese is still incompatible with the r5u870 driver.
hmmm will look into the colors tho....

but before this i was using cheese with the r5870 driver in gutsy....

either there;'s some tweak necessary or coz i tried so many things back then, i must've installed sumthing else too...anyways thanks..

---

### Post by anpu1 on 2008-05-24
It would be nice to repair this thing cause the other day i was talking to a friend and when i tried the video call we started to laught cause of the negative image colors!!

Would be happy to repair this and i know you gents and ladys know how or will finde the way :D

---

