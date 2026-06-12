---
title: "Card Reader doesn` t work in Jaunty"
date: 2009-06-14
forum: Hardware
---

### Post by Tashi on 2009-06-14
Hi all

I recently upgraded to Jaunty. Now my Card Readers stop working. When I insert a Memory Card it doesn` t mount anymore. I try it with three different USB Card Readers.

Here is the output from /var/log/messages, dmesg, lsusb, lsmod and fdisk.



/var/log/messages

```

Jun 14 11:47:23 togobop kernel: [ 3348.444026] usb 3-3: new full speed USB device using ohci_hcd and address 12
Jun 14 11:47:23 togobop kernel: [ 3349.068027] usb 3-3: new full speed USB device using ohci_hcd and address 13
Jun 14 11:47:24 togobop kernel: [ 3349.692016] usb 3-3: new full speed USB device using ohci_hcd and address 14
Jun 14 11:47:25 togobop kernel: [ 3350.236020] usb 3-3: new full speed USB device using ohci_hcd and address 15

```

dmesg
```

[ 3348.584029] usb 3-3: device descriptor read/64, error -62
[ 3348.828024] usb 3-3: device descriptor read/64, error -62
[ 3349.068027] usb 3-3: new full speed USB device using ohci_hcd and address 13
[ 3349.208020] usb 3-3: device descriptor read/64, error -62
[ 3349.452023] usb 3-3: device descriptor read/64, error -62
[ 3349.692016] usb 3-3: new full speed USB device using ohci_hcd and address 14
[ 3350.100019] usb 3-3: device not accepting address 14, error -62
[ 3350.236020] usb 3-3: new full speed USB device using ohci_hcd and address 15
[ 3350.644034] usb 3-3: device not accepting address 15, error -62
[ 3350.644069] hub 3-0:1.0: unable to enumerate USB device on port 3

```

lsusb
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 131d:0156 Natural Point 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 002: ID 046a:0023 Cherry GmbH Cymotion Master Linux Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fe202aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3947    31703040    7  HPFS/NTFS
/dev/sda2            3947       16105    97656250    7  HPFS/NTFS
/dev/sda3           16106       60801   359020620    5  Extended
/dev/sda5   *       16106       28263    97659103+  83  Linux
/dev/sda6           59346       60801    11695288+  82  Linux swap / Solaris

```

lsmod

```

Module                  Size  Used by
usb_storage            94912  0 
ppdev                  16904  0 
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
autofs4                38408  0 
video                  29204  0 
output                 11648  1 video
input_polldev          12688  0 
sbp2                   34700  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_pcm_oss            52352  0 
snd_hda_intel         557364  2 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_pcm_oss,snd_hda_intel
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  14 snd_pcm_oss,snd_hda_intel,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                64028  0 
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
pcspkr                 11136  0 
i2c_piix4              20112  0 
serio_raw              14468  0 
joydev                 20864  0 
fglrx                2376104  33 
hid_cherry             10752  0 
ohci1394               42036  0 
ieee1394              108288  2 sbp2,ohci1394
usbhid                 47040  0 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

---

### Post by Tashi on 2009-06-14
bump

---

### Post by memeri on 2009-06-14
Is this a clean install of ubuntu -- do you need to reload the driver for the card reader? Just wondering.

---

### Post by Tashi on 2009-06-14
Hi Memeri

It`s not a fresh Install. I upgraded from 8.04. I also read treads about reloading drivers(uhci_hcd, ehci_hcd, ohci_hcd). In some threads I read reloading these drivers is now obsolet(with 9.04), cause the drivers is not longer a module. It`s now in the kernel integrated. And Tests I done confirm that. When I look at lsmod. I don` t see any drivers like uhci_hcd, ehci_hcd, ohci_hcd.

But I don`t now much about this driver stuff :(

---

### Post by memeri on 2009-06-14
Oh, I see. This is over my head now. Good luck.

---

### Post by Tashi on 2009-06-15
bump

I hope I get this working again. Otherwise I have to reinstall Ubuntu(like the Windows reinstalling orgies).

---

### Post by Tashi on 2009-06-16
bumpy

---

### Post by Tashi on 2009-07-03
People from the german board give me some advice: [http://forum.ubuntuusers.de/topic/card-reader-funktionieren-nicht-mehr-seit-upg/#post-2029461](http://forum.ubuntuusers.de/topic/card-reader-funktionieren-nicht-mehr-seit-upg/#post-2029461)

Here how it works for me(if someone has the same problem):

temporary
```

sudo modprobe -v usb_storage

```

and permanent
```

sudo echo usb_storage >> /etc/modules

```

---

### Post by zoomy942 on 2009-07-03
hmm.  i just noticed my sd reader doesnt work either

---

