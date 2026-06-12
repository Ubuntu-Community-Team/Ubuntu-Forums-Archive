---
title: "Getting Speakers working on Acer 5570Z laptop"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by Steve1496 on 2007-10-09
Hi, I got an Acer Aspire 5570Z at bestbuy a month ago, couldn't pass up the sweet deal.  Anyways, I just installed Ubuntu (Gutsy), and I've managed to get everything working except the speakers.  I just got the headphones working using the site.

If anyone can point me to a tutorial or help me out, it'd be greatly appreciated.  Here is the output from terminal.
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


Thanks!
Steve

---

### Post by m2montazari on 2007-10-20
hi
all you need is to download and install "gnome alsa mixer" OR "alsa mixer" then go to application>sound>alsa mixer and unmute surround. BE LUCKY!

---

### Post by icaris13 on 2007-12-29
Hi, I also have an Acer Aspire 5570z.  I installed gnome-alsamixer and unmuted surround and now my sound works!  Awesome!  The only problem is my volume control (either from the taskbar or my key shortcuts) don't work.  Any suggestions?

---

### Post by jkrtest on 2007-12-29
Funny, on my 5570 the Fn buttons work for sound.
I just followed these steps here to get the sound working (works fine, thx) and I can use Fn + F8 to mute/unmute, and I can use the Fn + up/down arrows to adjust the volume.
Did you maybe change any other settings in the mixer?

---

### Post by icaris13 on 2007-12-31
Nope, I didn't change any other settings in the gnome-alsamixer.  I'm about to go forum hunting to see if anyone has had a similar problem.

---

### Post by g_dwarf on 2008-03-30
I have a similar problem on my Acer Aspire 5050, the volume control works but only controls the "Front" Channel and not the main "PCM"-channel. If you found a solution then please let me know, I remember having seen it before somewhere.

---

### Post by g_dwarf on 2008-03-30
Ok I've got it working with the solution I found in [this]("http://ubuntuforums.org/showthread.php?t=209907&page=2#post4033868") thread:

System -> Preferences -> Sound, select PCM, Close.

In the other thread they say to select both PCM and Master but I don't have Master listed there and PCM works fine, I can change volume with Fn-Up/Down and mute with Fn-F8 as well as with the slider in the system tray.

Now I just have to find a way to mute the speakers when using the headphones...

---

