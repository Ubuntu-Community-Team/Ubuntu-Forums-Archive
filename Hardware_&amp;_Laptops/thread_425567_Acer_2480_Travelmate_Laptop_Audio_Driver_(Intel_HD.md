---
title: "Acer 2480 Travelmate Laptop Audio Driver (Intel HD Audio / Realtek HD Audio)"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by Espionage724 on 2007-04-27
I have a Acer 2480 Laptop
I am running Kubuntu 7.04
Heres a list when I do lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
**00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)**
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

I want to get my sound to work. On windows my sound driver is Realtek HD. I heard you can use Realtek HD or Intel HD drivers in linux (google). Can anyone help me with getting sound?

---

### Post by Espionage724 on 2007-04-27
I messed with my mixer settings and volume. (Turned everything but mic on and max volume.)

---

### Post by Downtown on 2007-05-02
Did something in particular work?  I have the same laptop with the same problem.

---

### Post by nwadams on 2007-05-06
i have a toshiba laptop with the same audio
mine appears to just work but is quiter compared to how it is in windows

---

### Post by gleble on 2007-12-07
I have an Acer Aspire 3680 with  Intel Corporation 82801G (ICH7 Family) audio. I have installed Ubuntu and have no sound. Can anybody help?

---

### Post by baxterdog on 2008-01-24
Right click on the volume icon in a taskbar and open the volume control, unmute everything, and turn up the volume bars. The surround category was the one that did it for me. You can add or remove these categories as well in 'edit->preferences.

I have an Acer 2480 also but this should work for most if not all laptops. There are quite a number of threads on this very issue in the forums.

---

### Post by Downtown on 2008-02-01
For the last year or so, I've gone back and forth from WinXP to Ubuntu on my Acer TM 2480 laptop about a million times.  The problem that I always have coming back to Ubuntu is getting sound to work.  I always figure it out, but the next  time I come back to it, I forget how I fixed it.  So this post is as much for my archives as it is to help others.

What worked for me (may not work for you):

1. Use [this guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto") to update to the newest version of the alsa driver, lib, and utils (as of this writing, they are version 1.0.16rc2).
2. Restart.
3. Open terminal and type
```
sudo gedit /etc/modprobe.d/alsa-base
```
4. After the last line, add this line
```
options snd-hda-intel model=toshiba
```
5. Save the file and close it.
6. Restart.

Don't ask me why it works with the model as Toshiba when this is an Acer, but this is what worked for me.  I can now plug in my headphones and the speakers turn off.  The speakers also work when I take off the headphone.  All audio can be controlled through the mixer in the notification area.

Hope it helps others.

---

### Post by JCCyC on 2008-02-05
The procedure below worked perfectly for me, too. I have an Acer Aspire 5570Z. Oddly, I also needed "model=toshiba". Thanks!

> **Downtown said:**
> For the last year or so, I've gone back and forth from WinXP to Ubuntu on my Acer TM 2480 laptop about a million times.  The problem that I always have coming back to Ubuntu is getting sound to work.  I always figure it out, but the next  time I come back to it, I forget how I fixed it.  So this post is as much for my archives as it is to help others.

What worked for me (may not work for you):

1. Use [this guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto") to update to the newest version of the alsa driver, lib, and utils (as of this writing, they are version 1.0.16rc2).
2. Restart.
3. Open terminal and type
```
sudo gedit /etc/modprobe.d/alsa-base
```
4. After the last line, add this line
```
options snd-hda-intel model=toshiba
```
5. Save the file and close it.
6. Restart.

Don't ask me why it works with the model as Toshiba when this is an Acer, but this is what worked for me.  I can now plug in my headphones and the speakers turn off.  The speakers also work when I take off the headphone.  All audio can be controlled through the mixer in the notification area.

Hope it helps others.

---

