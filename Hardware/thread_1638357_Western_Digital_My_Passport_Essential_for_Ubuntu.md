---
title: "Western Digital My Passport Essential for Ubuntu"
date: 2010-12-05
forum: Hardware
---

### Post by phineas1996 on 2010-12-05
Hello,

I have a 1TB Western Digital My Passport Essential portable hard drive and I want to know if it work with Ubuntu 10.04, I am planning on upgrading to Ubuntu 10.10. I use it on Windows 7 Home Premium for right now. I have all my music and videos on this portable hard drive.

---

### Post by ajgreeny on 2010-12-05
Why not simply try it; it is a USB drive I assume, isn't it?

---

### Post by DaithiF on 2010-12-05
> **phineas1996 said:**
> Hello,

I have a 1TB Western Digital My Passport Essential portable hard drive and I want to know if it work with Ubuntu 10.04, I am planning on upgrading to Ubuntu 10.10. I use it on Windows 7 Home Premium for right now. I have all my music and videos on this portable hard drive.

yes, i have a couple of these and have never had trouble using them across several versions of ubuntu, (and several other distros, for that matter).

---

### Post by graben3 on 2011-01-17
This drive does not work form me... it needs a driver in XP and Vista and just works in Win 7. In Ubuntu, it's just not working... in every OS, it just pops up an HD drive along with a fake/virtual CD ROM that asks you all the time to install their scrap-ware... I hate this disk. You can't format it in everything you like like any normal disk. It seems the HD chipset is faking having 512B sectors while having 4k sectors for real...so the chipset is lying to XP to make it work on XP and therefore not working on Ubuntu since the drive is lying and Ubuntu is listening to the drive (the right move in that case)... i'm gonna exchange it... I don't recommend this to anybody on anything other than win 7... it works natively like a charm on win 7.... but not vista.

---

### Post by mastablasta on 2011-01-17
you need to align it then. in WinXP you need to use the software provided by WD.

---

### Post by caseman7 on 2011-01-17
Hey y'all - just thought I'd throw in my 2 bits. I run that exact same device, and all I did was plug it in to my usb port in ubuntu 10.04, and the system had it listed in 'places' within about 8 seconds and the unit was fully accessible. 

Cheers, 

Casey

---

### Post by graben3 on 2011-01-17
What did you do to make it work ? Nothing ?

When i plug this 1TB hd in ubuntu, here is what I see in my log files :

Jan 17 09:06:06 TL-Quad kernel: [  333.321483] usb 1-2: USB disconnect, address 4
Jan 17 09:06:06 TL-Quad kernel: [  333.700233] hub 1-0:1.0: unable to enumerate USB device on port 2
Jan 17 09:06:07 TL-Quad kernel: [  334.200020] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jan 17 09:06:07 TL-Quad kernel: [  334.330010] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:07 TL-Quad kernel: [  334.563758] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:07 TL-Quad kernel: [  334.790025] usb 3-2: new full speed USB device using uhci_hcd and address 3
Jan 17 09:06:07 TL-Quad kernel: [  334.920010] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:08 TL-Quad kernel: [  335.163763] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:08 TL-Quad kernel: [  335.392518] usb 3-2: new full speed USB device using uhci_hcd and address 4
Jan 17 09:06:08 TL-Quad kernel: [  335.813760] usb 3-2: device not accepting address 4, error -71
Jan 17 09:06:08 TL-Quad kernel: [  335.933762] usb 3-2: new full speed USB device using uhci_hcd and address 5
Jan 17 09:06:09 TL-Quad kernel: [  336.352835] usb 3-2: device not accepting address 5, error -71
Jan 17 09:06:09 TL-Quad kernel: [  336.352845] hub 3-0:1.0: unable to enumerate USB device on port 2

---

### Post by tonywhelan on 2012-01-24
> **graben3 said:**
> What did you do to make it work ? Nothing ?

When i plug this 1TB hd in ubuntu, here is what I see in my log files :

Jan 17 09:06:06 TL-Quad kernel: [  333.321483] usb 1-2: USB disconnect, address 4
Jan 17 09:06:06 TL-Quad kernel: [  333.700233] hub 1-0:1.0: unable to enumerate USB device on port 2
Jan 17 09:06:07 TL-Quad kernel: [  334.200020] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jan 17 09:06:07 TL-Quad kernel: [  334.330010] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:07 TL-Quad kernel: [  334.563758] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:07 TL-Quad kernel: [  334.790025] usb 3-2: new full speed USB device using uhci_hcd and address 3
Jan 17 09:06:07 TL-Quad kernel: [  334.920010] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:08 TL-Quad kernel: [  335.163763] usb 3-2: device descriptor read/64, error -71
Jan 17 09:06:08 TL-Quad kernel: [  335.392518] usb 3-2: new full speed USB device using uhci_hcd and address 4
Jan 17 09:06:08 TL-Quad kernel: [  335.813760] usb 3-2: device not accepting address 4, error -71
Jan 17 09:06:08 TL-Quad kernel: [  335.933762] usb 3-2: new full speed USB device using uhci_hcd and address 5
Jan 17 09:06:09 TL-Quad kernel: [  336.352835] usb 3-2: device not accepting address 5, error -71
Jan 17 09:06:09 TL-Quad kernel: [  336.352845] hub 3-0:1.0: unable to enumerate USB device on port 2

I had intermittent problems with recognition of WD Passport drive via my USB3 PCIex hub, but it was fine via USB2 ports. Edited /etc/modprobe.d/blacklist.conf to add the line "blacklist uas" which helped. Also have just upgraded my PC's power supply unit from 450w to a quality 600W unit, and the Passport drive is being recognised in USB3 port every time. Maybe problem was partly related to the power drain on the old PSU, really don't know what else would explain it.

**Edit: I spoke too soon. Its intermittent still. Sometimes works, mostly not.**

---

