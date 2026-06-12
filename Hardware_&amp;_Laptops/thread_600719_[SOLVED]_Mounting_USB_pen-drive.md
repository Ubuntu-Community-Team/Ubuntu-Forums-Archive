---
title: "[SOLVED] Mounting USB pen-drive"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by Nordkraft on 2007-11-02
Hi!

I'm trying to get my laptop to access a USB pen-drive. However, plugging the pen in while the computer is turned on doesn't automount the drive. In fact, typing 

```
sudo fdisk -l 
```

produces this:

```
Disk /dev/sda: 160.0 Gb, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16159dc6

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1       18528   148826128+  83  Linux
/dev/sda2           18591       19457     6964177+   7  HPFS/NTFS
/dev/sda3           18529       18590      498015   82  Linux swap / Solaris

```

which obviously indicates that the pen-drive isn't even detected :(

Plugging the drive in while the laptop is turned off and then powering up mounts the drive alright but I really need to be able to mount the pen-drive while the computer is turned on so that doesn't help me much.

Any suggestions?

Cheers

---

### Post by tech9 on 2007-11-02
> **Nordkraft said:**
> Hi!

I'm trying to get my laptop to access a USB pen-drive. However, plugging the pen in while the computer is turned on doesn't automount the drive. In fact, typing 

```
sudo fdisk -l 
```

produces this:

```
Disk /dev/sda: 160.0 Gb, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16159dc6

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1   *           1       18528   148826128+  83  Linux
/dev/sda2           18591       19457     6964177+   7  HPFS/NTFS
/dev/sda3           18529       18590      498015   82  Linux swap / Solaris

```

which obviously indicates that the pen-drive isn't even detected :(

Plugging the drive in while the laptop is turned off and then powering up mounts the drive alright but I really need to be able to mount the pen-drive while the computer is turned on so that doesn't help me much.

Any suggestions?

Cheers

for kicks... try 

sudo mount /dev/sdb1

while your USB Drive is connected to your computer

---

### Post by Nordkraft on 2007-11-02
Tells me it can't find /dev/sdb1 in /etc/fstab or /etc/mtab:

```
mount: kunne ikke finde /dev/sdb1 i /etc/fstab eller /etc/mtab

```

---

### Post by tech9 on 2007-11-02
is this a new thumb drive? Maybe there is something wrong with it - it should auto mount

---

### Post by Nordkraft on 2007-11-02
No, it's not new actually. I've had it work flawlessly with previous versions of Ubuntu (except Feisty). Furthermore, it does mount when it's plugged in before boot up; just not when I'm plugging it in after having booted :confused:

---

### Post by coquimbo on 2007-11-04
I'm having the same problem.  lsusb doesn't show the drive either now, though it would previously.  I've tried the same things suggested in this thread with no luck.  Any suggestions?  What's the next step?

---

### Post by coquimbo on 2007-11-04
K, so as I was messing around with the partitions, I noticed my windows partition hadn't mounted because it was hibernated.  I shut down windows  and rebooted linux without the pen drive inserted.  After I was booted, I inserted the pen drive and could see it using "fdisk -l" but after rebooting again, it's no longer listed.  So...I don't know what that means, but maybe somebody does.  Any help is appreciated.

---

### Post by ryandle on 2007-11-04
I too am having isses with my USB thumb drive.  It worked fine on feisty but gutsy does not seem to recognize it.  My wireless mouse has a usb adaptor that is working.  I have tried 2 other usb thumb drives, none work!  Any help would be appreciated.

---

### Post by damu on 2007-11-04
Same problem here with external usb HD, and usb sticks. It has been working since dapper and is broken in Gutsy...Gosh, I upgraded 2 computers of friends to 7.10 and I really can't say I am impressed (on the other one the printer doesn't work anymore...wish I was paid for the support I try to deliver to them... I told them Ubuntu was just working...it obviously doesn't)

I tried to uninstall ntsf-3g as on one of the message , there was an issue with NTFS, but to no avail . So here are some screenshots of the details reported by Ubuntu when I try to mount either a fat32 usb stick or a NTFS ext usb drive (I had to take a screenshot as I can't copy the text of the details given by Ubuntu about the issue...how stupid is that!).


Thanks for your help and patience!

---

### Post by petteriIII on 2007-11-05
Shot to darkness: are three first squares filled in your: System / Settings / Removable drives and media ?
- sorry if translation is not accurate.

---

### Post by 73man on 2007-11-05
> **petteriIII said:**
> Shot to darkness: are three first squares filled in your: System / Settings / Removable drives and media ?
- sorry if translation is not accurate.

Having the same problem here with a Kingston 1gb and 7.10. And I have these settings turned on.

---

### Post by Nordkraft on 2007-11-05
Yes, I too have these options enabled.
Still not working...:(

---

### Post by 73man on 2007-11-07
> **73man said:**
> Having the same problem here with a Kingston 1gb and 7.10. And I have these settings turned on.

However a 512mb pen drive is picked up instantly. Does this problem have to do with the size of the drive?

---

### Post by Nordkraft on 2007-11-12
Ok, I figured it out :)

Turns out It was a problem with my laptop (hp dv6507eo) and the uvcvideo module used for the built-in webcam. I solved it by blacklisting the module: 

```
sudo nano -w /etc/modprobe.d/blacklist
```

Then add this at the end of the file:

```
blacklist uvcvideo
```

:)

---

