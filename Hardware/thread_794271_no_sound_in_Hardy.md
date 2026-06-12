---
title: "no sound in Hardy"
date: 2008-05-14
forum: Hardware
---

### Post by dancer58 on 2008-05-14
Help
I've searched and tried all I found but still no sound. 
I will try anything :confused: ( i've rebuilt Hardy twice trying different things)

linux 2.6.24-17
Ubuntu 8.04
mother board = Asus P5B
processor = Intel core 2 duo

--------------------------------------------------------------------------------------------

audio = Intel 82801H (on mother board)
   pci.product = '82801H (ICH8 Family) HD Audio Controller'

THIS IS FROM HWINFO:
31: PCI 1b.0: 0403 Audio device
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.kURRCMIOEo3
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "ASUSTeK HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "HD Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x81ec 
  Revision: 0x02
  Memory Range: 0xfebf8000-0xfebfbfff (rw,non-prefetchable)
  IRQ: 3 (no events)
  Module Alias: "pci:v00008086d0000284Bsv00001043sd000081ECbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is not active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Alsa.sh does not find a sound card

   !!Loaded ALSA module

   !!Soundcards recognised by ALSA
   --- no soundcards ---

   !!PCI Soundcards installed in the system
   00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

--------------------------------------------------------------------------------------------

Agere V.92 winmodem
video = nVidia G72 (GEForse 7300 LE)
2 hard drives
keyboard & mouse are USB
USB bluetooth BCM2045A

Thanks
Harold

---

### Post by nic2 on 2008-05-17
The following thread worked for me:
[http://ubuntuforums.org/showthread.php?t=616845&highlight=lenovo+3000+n200+%2B+sound]("http://ubuntuforums.org/showthread.php?t=616845&highlight=lenovo+3000+n200+%2B+sound")

---

### Post by dancer58 on 2008-05-18
Thanks for the info
I tried but still no sound

---

