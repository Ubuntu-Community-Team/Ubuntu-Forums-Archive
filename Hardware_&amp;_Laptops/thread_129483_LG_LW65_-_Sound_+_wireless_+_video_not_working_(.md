---
title: "LG LW65 - Sound + wireless + video not working :("
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by Trojan1313 on 2006-02-13
sudo lspci gives this output:
```
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4351 (rev 10)
0000:06:00.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:00.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 8032
0000:06:00.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:06:00.4 0805: Texas Instruments: Unknown device 8034
0000:06:02.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
```

**Sound:**
The sound module in use is the intelhda module, but it's not working. I don't get any sound whatsoever. I belive I'm supposed to use the Azalia driver module, but I don't know where to find it or how to install it, and I'm not even sure it's the one for me. =/

**Wireless:**
I don't know much about this, except that KDEs wifimanager don't find anything and that there's supposed to be an encrypted network here (another one of our computers find it) called "synhall".

**Video:**
Using the i810 driver in xorg.conf and with only 1280x800 pixels put in under the resoultion-part in the xorg.conf I still have 1024x768.
sudo xresprobe i810 gives the output
id:
res: 1280x800
freq:
disptype: lcd/lvds


I don't really know what else to say, please request any info that can help!

---

### Post by bananasontoast on 2006-04-23
I am just curious if you have had any luck with these issues? I am having pretty much the exact problems so if you have gotten to fixing them I would very much like to know how?

---

### Post by nolongerlivecd on 2006-04-23
Here's my tip: Do a fresh install. It worked for my wireless and battery problems. Only thing was that I had to insert my battery at the time

---

### Post by bananasontoast on 2006-04-23
Mine is a completely fresh install, but I still have no sound or wireless. Are you using the same model laptop?

---

### Post by Burkey on 2006-04-24
Did you try plugging in a headset?  I have the same sound device on my Dual core and it works ok then.  Cannot get audio out the built-in speakers though! aargh!

Using snd_hda_intel module

Otherwise my Wireless is a ipw3945 and is working ok.

---

### Post by bananasontoast on 2006-04-24
I think I have a slightly different laptop, [here are my specs]("http://au.lge.com/md/product/prodcategorylist.do?actType=detail&currPage=1&categoryId=0200000045&parentCategoryId=0200000603&categoryLevel=4&productId=1100000768&productImage=&selectModel=1100000768#"). Mine uses an Intel Pro/Wireless 2915ABG(802.11a/b/g).

Sound card does seem to work with headphones, but it doesn't matter whether it's set to 1% volume or 100% volume it comes out at 100% and cannot be listened to.

Video is fine except for when exiting ubuntu, it goes all grey and staticy until the system is shut down.

---

### Post by Burkey on 2006-04-24
Hmm, i think my volume works with headset.. mine is the P1 Express Dual (GO LG!)

[http://au.lge.com/md/product/prodcategorylist.do?leftMenu=true&actType=list&categoryId=1000000194&parentCategoryId=0200000603&categoryLevel=4](http://au.lge.com/md/product/prodcategorylist.do?leftMenu=true&actType=list&categoryId=1000000194&parentCategoryId=0200000603&categoryLevel=4)

Also, I am on Dapper.

---

### Post by bananasontoast on 2006-04-24
I honestly didn't think it was so much to ask that Wireless worked out of the box after all the stuff I've heard about ubuntu. Maybe it's just like every other distro afterall.

---

### Post by Trojan1313 on 2006-04-24
Sadly, I have not had it working much better.

With headphones the sound works, without it doesnt. With the pcspkr-module I get beeps out of the computer's built-in speakers, but only console-beeps (exept a little better than an average console beep, since it's in the speakers, but still bad).

The wireless card seems to be working though. I don't know how to connect to a wireless network, but I can see them in wifi-radar and stuff. This was done by downloading source code for rt2500 or something like that from the repository and compile it, then just ifconfig ra0 up or something. :)

It's been a while ago since I had Internet on it (I'm studying abroad now! :D) and could try to fix with these things, so some names on programs or drivers might be wrong, but I think it's close anyway. :)

---

### Post by nolongerlivecd on 2006-04-24
I'm using a different laptop, and I had troubles with my initial install too. After a few days, I decided to reformat the Ubuntu partition, and it brought to me my wireless...

---

### Post by jimikimble on 2006-04-25
Had the same problem with resolution on my laptop.  The i810 driver doesn't set up the vBios correctly, to overcome this use the 855resolution utility (915 resolution in dapper). Here's the wiki page: [https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28855resolution%29]("https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28855resolution%29").

---

### Post by bananasontoast on 2006-07-25
I've downloaded the latest version of Ubuntu (6.06 LTS) and now I can't even seem to boot the CD into Ubuntu? Did I just buy a really bad laptop to try and install Ubuntu on?

---

