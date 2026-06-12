---
title: "No sound on Medion MD96290, Ubuntu 9.10"
date: 2009-11-07
forum: Hardware
---

### Post by Eax.exe on 2009-11-07
Hello there.

I have a Medion MD96290 which runs Ubuntu 9.10.
The sound works when I plug in a headphone plug (it works in the headphones) but the onboard speakers do not work at all. There's just no sound.

Here is "lspci":
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
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
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

And "cat /proc/asound/version":
```
Advanced Linux Sound Architecture Driver Version 1.0.20.
```

Also "aplay -l":
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Can anyone please help? :)

---

### Post by Eax.exe on 2009-11-07
Anyone please? :)

---

### Post by Eax.exe on 2009-11-08
Can anyone please help?

---

### Post by D_T on 2009-12-17
I have the same problem, but no results on many of many actions...

---

### Post by pc10pc on 2010-01-15
im looking for a solution too, just found this
[http://marc-spoor.blogspot.com/2008/02/2008-02-19-sound-finally.html]("http://marc-spoor.blogspot.com/2008/02/2008-02-19-sound-finally.html")

ill let you know

---

### Post by pc10pc on 2010-01-15
it worked!
im running mint on a persistent USB drive.
restart after adding the line

---

### Post by Rastanarcharismarx on 2010-05-13
For those not feeling comfortable doing every step done the link, including all the deleting (and reinstalling).
This is what I did in Ubuntu 10.04 Lucid Lynx:
I opened the terminal and entered
```
gksudo gedit
```
then I opened alsa-base.conf (found in the folder /etc/modprobe.d ) in the gedit window, and added the line "options snd-hda-intel position_fix=1 model=auto" at the end of the file  and rebooted.

laptop speakers now work properly!
thanks to ActionParsnip for breaking the post on the link down to these simple steps and thanks pc10pc for sharing the link.

---

### Post by koenr on 2010-06-03
Thanks a lot for this tip. I changed the subject line to make it easier to find for 10.04 Lucid Lynx users. 
The fix is the same as for 9.10, but the file seems to be moved.
[LIST]Start terminal[/LIST]
[LIST]sudo pico /etc/modprobe.d/alsa-base.conf[/LIST]
[LIST]add to the file
      options snd-hda-intel position_fix=1 model=auto[/LIST]
[LIST]reboot[/LIST]

---

