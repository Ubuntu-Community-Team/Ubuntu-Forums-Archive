---
title: "ASUS A6Kt live cd and install problem"
date: 2006-03-15
forum: Hardware &amp; Laptops
---

### Post by Harlyman on 2006-03-15
hi

i have problem with loading live cd and installing ubuntu on my new laptop, after it starts to boot it stops at this point:

[429467.671000]ACPI: Looking for DSDT in initrd... not found!
[429467.713000] not found!

after this it just hang, have been browsing the forum and it looks like other users have been able to install on asus a6000 series, any idea anyone what it could be?

i run ubuntu on 2 servers and my girlfiends laptop (toshiba) and i love it, its almost a shame if i have wasted money on a laptop i only can use with windows:(

hardware details below

ASUS A6Kt 15.4"WXGA
ATI X1600-128
Turion MT34
2x512MB ram
100GB harddrive
DVD±RW
WLAN/BT,
XPH

---

### Post by djroadrash on 2006-03-15
try turning acpi off and see if it works
at boot type on install
```
linux acpi=off 
```
if it stops at all then just add dma=off
for live cd 
```
live acpi=off dma=off
```
maybe that will help:KS

---

### Post by Harlyman on 2006-03-15
yeah that did help, thanks alot:), but xserver will not start, it says its not setup right, guess i have some work to do now, finding driver for it

---

### Post by m4t7e0 on 2006-06-13
Hello, i'm italian the real problem is the USB Mouse, when this is connected the kernel don't Boot!! disconnect the mouse and power on the PC!! :D

---

### Post by krazyd on 2006-06-13
[QUOTE=m4t7e0]Hello, i'm italian the real problem is the USB Mouse, when this is connected the kernel don't Boot!! disconnect the mouse and power on the PC!! :D[/QUOTE]I have the same notebook (ASUS A6000KT) and the same problem. It's kinda a dumb problem to have, no?

Has anyone had any luck getting a workable system up and running on the same notebook?

---

### Post by Harlyman on 2006-06-14
[QUOTE=krazyd]I have the same notebook (ASUS A6000KT) and the same problem. It's kinda a dumb problem to have, no?

Has anyone had any luck getting a workable system up and running on the same notebook?[/QUOTE]

have any of you got the grafic card to work?? i have an ATI M56 P(X1600) and can't get this card to work.

---

### Post by Mooncore on 2006-06-29
Wlan, Graphic Card is not working i tried soo many variations but not a chance :( seems i ll go back suse :(( Really want to use ubuntu but without wlan and graphic card its kinda useless

---

### Post by krazyd on 2006-06-29
Okay, I now have a workable Ubuntu install on my ASUS A6KT / A6000KT notebook :D
There are, however, a few small hardware-related problems...

Graphics card (ATI Radeon X1600) works almost flawlessly (can't seem to set up vsync for opengl apps properly, resulting in page tearing. Will keep investigating... :( )

Wireless works, but with three caveats:
[LIST]
[*] apparently it is a known bug that bcm43xx shows 100% signal strength at all times on the 4318 broadcom chip.
[*]  signal has to be really strong for wireless. Has nowhere near the range wireless in XP does. By this I mean that Network Manager shows the network listed (at 100% signal strength) but cannot connect to it unless I'm really close to the AP.
[*]little blue LED doesn't light up on the front of the notebook :-({|= 
[/LIST]
I still have the boot freeze. I can get past it with 'acpi=off', but that severely reduces the usefulness of a notebook :( :(. At the moment, I just unplug everything from the usb ports when booting which also solves my problem.

If anyone has any help for me regarding the problems mentioned above, I'd be very appreciative!! :)

Also, if anyone is interested in how I set up the rest of the notebook, please ask!!

Cheers.

---

### Post by Mooncore on 2006-06-30
if you can tell us how did you activate all things i mean wlan and x1600 graphic card i ll b really appriciate :)

---

### Post by krazyd on 2006-07-02
Well as far as I can remember this is what I did. You need an internet connection (wired ethernet works out-of-the-box):
The graphics card was the first thing I installed after doing a system update / upgrade on a new install. I followed these instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Worked straight away! :D

The wireless was tricker, however. We have to rely on the recently developed bcm43xx driver which is now part of Dapper (latest updated kernel).
Find the WinXP directory in your windows installation which has the bcmwl5.sys and bcmwl5.inf in it (I've attached mine to this post in case it's deleted or something). Use the bcm43xx-fwcutter tool (you may have to install it using synaptic) to extract your firmware to /lib/firmware. I believe the command was:```
sudo bcm43xx-fwcutter -w /lib/firmware PATH_TO_YOUR_.SYS_FILE
```

Install network-manager-gnome (and wpa-supplicant if it is not already installed) using Synaptic, and reboot. Network Manager should automagically appear in the tray, and if your wireless is installed properly, right clicking network manager should list any wireless networks in your vicinity. Let me know how it goes.. :)

---

### Post by seomaster on 2006-07-24
[http://www.allfdameds.com](http://www.allfdameds.com)
[http://www.medshealth.com](http://www.medshealth.com)
[http://www.yourbetterpharmacy.com](http://www.yourbetterpharmacy.com)
[http://www.rxmeds4you.net](http://www.rxmeds4you.net)
[http://www.storerxmeds.com](http://www.storerxmeds.com)

---

