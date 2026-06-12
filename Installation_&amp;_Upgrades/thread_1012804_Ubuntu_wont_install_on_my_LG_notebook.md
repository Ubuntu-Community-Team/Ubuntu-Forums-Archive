---
title: "Ubuntu wont install on my LG notebook"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by cnkt on 2008-12-16
hi,

i have LG K.APGWT model laptop and i want to use Ubuntu. i have downloaded Ubuntu 8.10 iso and burn it on a cd. the cd works on my desktop pc but it doesn't work on my laptop. when i select "install ubuntu..." the orange progress bar comes and it stop immediatly.

thanks for help.

---

### Post by taurus on 2008-12-16
What's the spec of your notebook?

---

### Post by cnkt on 2008-12-16
LG E500-K.APGWT
Intel® CoreTM2 Duo Processor T7250, 2MB L2 Cache, 2.0GHz, 800MHz FSB
Windows Vista® Ultimate
Mobile Intel® PM/GM 965 Express
2048 MB DDR2(667Mhz,Dual Channel Support, )
15.4" WxGA FB TFT 1280x800
Ati ® Radeon Mobility HD 2400  (256 MB VRAM, *TurboCache Support)  
160GB(SATA)  5400Rpm
Super Multi DVD± RW, DVD-RAM Optik Sürücü 
5.1CH Dolby Digital, 24bit High Definition,
4*USB, *RJ11,RJ45,VGA,S-Video Out, HP Out(SPDIF),Mic-in,Line-in,DC In,IEEE1394
Intel® Pro/Wireless 3945ABG(802.11a/b/g) or 802.11b/g Dual Quad-band Antenna
56kbps Modem  / 10/100MB Ethernet
Bluetooth v2.0+EDR
Bluetooth, 1 x IEEE1394, 3x USB, 802.11abg WiFi Kablosuz Arabirim, 
Gigabit LAN, Card Reader 5-1, VGA, RJ11, RJ45, S-Video, Mic-in, Line-in, S/PDIF.
4-in-1 (SD/MMC/MS/MS Pro)

---

### Post by taurus on 2008-12-16
Do you plan to install Ubuntu along side windows or will Ubuntu be the only OS on that laptop?  You can always try the alternate CD since it's a text based installer but should be fairly easy to follow.

---

### Post by cnkt on 2008-12-16
first i want to install ubuntu. after that if i cant do some of my works with ubuntu i will think about dual boot. but ubuntu made me disappointed from start :(

---

### Post by cnkt on 2008-12-16
i also tried the alternate cd but when i select the install ubuntu option the cursor blinks and nothing happens.

---

### Post by taurus on 2008-12-16
How fast did you burn the CD?  Did you run the option to check cd for defects at the initial screen?

---

### Post by cnkt on 2008-12-16
it doesnt found any CD errors and the same cd works on my desktop pc

---

### Post by cnkt on 2008-12-16
has anybody got any idea?

---

### Post by Rucas on 2008-12-16
I had the exact same problems. Burnt over 5 CD's and nada.
Yes i did burn the iso, (do know how to do it), Checked cd for defects.
All cd's boot, menu comes up, and even choosing just try ubuntu without installing, no go, same for install.
At the same time, the fans on my laptop went like crazy, the machine really heated up to levels it never did before within seconds and by just booting a cd!
Eventually i somehow managed to force the Cd to painfully install by pressing enter, spacebar, etc anything to try and wake the cd.
Not good. 8.10 was way too slow, thingz where working very weird, and again the fans and heat where crazy. So back to 8.4 and all is working fine.
I actually posted here after that and suggested that it could be possible that some mirrors that host the download might have the wrong CD Image, by this i mean only the 64 bit versions and not the 32bit for normal Intel chipsets. It simply does not make cense to me.
But some people claim they manged to install the i386 version, so, i dont know...

---

### Post by cnkt on 2008-12-17
i tested it with 8.04 too. but nothing new.

please help me.

---

### Post by Rucas on 2008-12-17
Do you mean that you cannot also install 8.04?
Does the Cd Boot, you get the Install menu?

---

### Post by rdjse on 2009-01-04
Try passing nolapic_timer as a kernel parameter before you proceed with the installation. It worked for me with a similar LG E500 setup.

---

