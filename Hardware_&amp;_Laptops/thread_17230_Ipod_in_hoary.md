---
title: "Ipod in hoary"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by John McClane on 2005-02-27
Sometimes hoary (kernel 2.6.10-3) find my ipod (3rd and firewire) and mount it in media/IPOD automatically but other times hoary not find my ipod and i must reboot the system.

Kernel messages when hoary find ipod:

```
Feb 27 08:37:57 localhost kernel: scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
Feb 27 08:37:57 localhost kernel: ieee1394: sbp2: Logged into SBP-2 device
Feb 27 08:37:57 localhost kernel:   Vendor: Apple     Model: iPod              Rev: 1.51
Feb 27 08:37:57 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Feb 27 08:37:57 localhost kernel: sda: Spinning up disk....ready
Feb 27 08:37:57 localhost kernel: SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB)
Feb 27 08:37:57 localhost kernel: sda: test WP failed, assume Write Enabled
```

When hoary not find the ipod i haven't no messages.

ps: sorry for my english

---

### Post by r00 on 2005-02-28
i have the same problem...
when i first installed, the ipod was detected no problem..
then, after trying unsuccessfully to get my sound blaster extigy working (and rebooting) it stopped automounting the ipod.. i assume i could do it through fstab
but it would lead to the same problems i had in the other linux distros :
it would conflict with my usb external drive.. and only mount the usb drive..
also, if you look in media, it makes several extra names for mount points from previous reboots, which might be part of the problem.. i'm gonna keep researching.. if i can possibly find an answer, i'll post back here...

other than those two little problems, ubuntu is the best!  :razz:

---

### Post by John McClane on 2005-03-03
[QUOTE=r00]i have the same problem...
when i first installed, the ipod was detected no problem..
then, after trying unsuccessfully to get my sound blaster extigy working (and rebooting) it stopped automounting the ipod.. i assume i could do it through fstab
but it would lead to the same problems i had in the other linux distros :
it would conflict with my usb external drive.. and only mount the usb drive..
also, if you look in media, it makes several extra names for mount points from previous reboots, which might be part of the problem.. i'm gonna keep researching.. if i can possibly find an answer, i'll post back here...

other than those two little problems, ubuntu is the best!  :razz:[/QUOTE]
 this is a bug?

---

### Post by bored2k on 2005-03-03
i usually hav a really hard time mkng the ipod work on warty 

i do modprobe mount automount whatever, doesnt do it


gtkpod doesnt read as user/nor root

it mounts [ican see the deorganised files in nautilus[ but i cant see it in gtkpod

---

