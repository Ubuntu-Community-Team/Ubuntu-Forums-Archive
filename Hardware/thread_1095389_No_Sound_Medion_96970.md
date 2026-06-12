---
title: "No Sound Medion 96970"
date: 2009-03-13
forum: Hardware
---

### Post by mpcsm on 2009-03-13
Hi,
I'm New to Ubuntu so please be patient :)

I installed Ubuntu 8.10 as duel boot with Windows and applied all upgrades.
Sound is working fine under Windows but not Ubuntu.

After the install and upgrade, the speaker had a red cross on it.
I read some posts and found that I may be able to fix the problem by 
sudo gedit /etc/modprobe.d/alsa-base
and adding 
options snd-hda-intel model=medion

After reboot, I now have a speaker icon and ensured nothing is muted.
Still no sound. I've read in some posts that sound may be faint. In my case, there is no sound at all from the speaker or headphones.

Some early diagnostics below....Hope you can help me. Thanks

cat /proc/asound/card0/codec\#*|grep Codec
Codec: Realtek ALC888
Codec: Realtek ALC268

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 5: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M G (rev a1)
02:00.0 Mass storage controller: Silicon Image, Inc. Sil 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
0a:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

---

### Post by kestrel1 on 2009-03-13
You may also want to add this to the options file:```
sudo gedit /etc/modprobe.d/options
```
& add this line ```
options snd-hda-intel model=medion
```

---

### Post by mpcsm on 2009-03-13
Made the change and rebooted....Still no sound

---

### Post by kestrel1 on 2009-03-13
Open the Volume control & check everything. Go to the preferences in volume control & put a tick in the boxes next to items that are not shown & check that they are not muted. Also change the device & do the same.

---

### Post by mpcsm on 2009-03-13
All on max setting. Nothing is muted. Still no sound

---

### Post by kestrel1 on 2009-03-13
Can you post the output from this command```
lspci
```

---

### Post by mpcsm on 2009-03-13
Has not changed from what I provided in the 1st post.

---

### Post by kestrel1 on 2009-03-13
> **mpcsm said:**
> Has not changed from what I provided in the 1st post.

I must be getting tired :)
At a bit of a loss at present. Maybe I need to sleep.

---

### Post by mpcsm on 2009-03-13
No Problem..Thanks for your help.

In the mean time, if anyone else is able to help.....please.

---

### Post by mpcsm on 2009-03-14
Problem resolved by using new Advanced Linux Sound Architecture Driver Version 1.0.19.

This site had step by step instructions.

[http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/](http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/)

---

### Post by kestrel1 on 2009-03-15
Sorry I was unable to help any further. Glad you got it sorted though. Well done :D

---

