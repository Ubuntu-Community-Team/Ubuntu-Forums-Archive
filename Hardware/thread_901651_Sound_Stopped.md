---
title: "Sound Stopped"
date: 2008-08-26
forum: Hardware
---

### Post by TCSnyder on 2008-08-26
My sound stopped working this morning . i get this message when i try to click the volume control

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."



"lspci | grep audio" shows nothing. 

the only thing i did was install and uninstall some virtualbox modules

---

### Post by Crafty Kisses on 2008-08-26
Post the results of this command > lspci

---

### Post by TCSnyder on 2008-08-26
here it is

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
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by TCSnyder on 2008-08-27
i have done everything from here [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting), and i don't get any errors but it doesn't work. the only sound i can get out of it is the system beep when i move all the way to the left on the terminal, and i don't think that happened befroe it stopped

---

### Post by Trizzy on 2008-10-10
I'm having the exact same problem after I installed virtualbox. My sound card is:

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

Good luck to you, but I've been scouring forums everywhere for days to no avail. One solution I did read that worked for a few people was editing the /etc/modprobe.d/options file by adding

# for soundchip snd_atiixp
options snd_atiixp ac97_codec=0

at the end. They had the atiixp sound driver that I use, so it probably won't work for you if you have something else. It didn't work for me anyway but maybe it will help someone else help you. :):)

---

### Post by Trizzy on 2008-10-10
I found the link to that forum thread.
[http://ubuntuforums.org/archive/index.php/t-365342.html](http://ubuntuforums.org/archive/index.php/t-365342.html)

---

### Post by Trizzy on 2008-10-10
I just solved my issue, which had symptoms like yours.
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

That is an excellent resource if you haven't already found it. The very first step solved my problem, that part about updating missing kernel modules.

---

