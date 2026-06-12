---
title: "Hard Drive Problem"
date: 2009-01-27
forum: Hardware
---

### Post by slimboarder003 on 2009-01-27
Hi, okay I got two hard drives in my box. One is a normal IDE one and the other is a sata drive. I have both of them set has IDE in the the bios. The problem I'm facing is Ubuntu can't still see or read that single sata drive even now when it is set has a IDE or I drive. I don't know what to do and it would be nice if anyone could help.

---

### Post by taurus on 2009-01-27
Have you installed Ubuntu on your machine or are you still running it from the LiveCD?  What happens to the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by slimboarder003 on 2009-01-27
Install it on my other hard drive for now. because it only see's that one. here is what I get.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x201b201b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5768    46331428+   7  HPFS/NTFS
/dev/sda2            5769        9729    31816732+   5  Extended
/dev/sda5            5769        9560    30459208+  83  Linux
/dev/sda6            9561        9729     1357461   82  Linux swap / Solaris

It does not even see the other drive only this one that is a 80gb one. The other is a 250gb one.

---

### Post by slimboarder003 on 2009-01-27
bump

---

### Post by AKADAP on 2009-01-28
Check the bios, and see if the bios can see the SATA drive. If the bios can't see the drive, it is not a Linux problem.

---

### Post by mrowl on 2009-02-07
Hi,
I'm having the same problem but I think my situation is slightly different. My two drives worked together fine on a different board with a AMD64 Athlon processor. Now I have Intel Dual-Core E2200. I expected to have some programs not work properly because they were AMD64 packages. I plan to upgrade to "Hardy" when I finish the projects I'm working on at present. 

The SATA drive shows up in the BIOS but not in /dev/disk/...
or when I try "sudo fdisk -l" in a terminal.

How can I correct this situation?
Should I post a separate thread?

---

### Post by caljohnsmith on 2009-02-07
Mrowl, do you have "AHCI" mode available for your SATA drive in BIOS? If so, how about enabling that, and then on start up when you get the Grub menu, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and at the end of the kernel line add:
```
pci=nomsi
```
Press enter to save the change, and then press "b" to boot; see if that works or not. If your BIOS doesn't have "AHCI" available, you could also try "RAID" mode in case you have that instead. Or if your BIOS has "SATA Native Support" enabled, try disabling it. Let me know how that goes.

---

### Post by mrowl on 2009-02-07
Thank you caljohnsmith:KS

that did the trick - so simple

---

### Post by caljohnsmith on 2009-02-08
> **mrowl said:**
> Thank you caljohnsmith:KS

that did the trick - so simple
Glad to hear you got it to work, but just for my own information, which BIOS setting actually worked for you?

---

### Post by mrowl on 2009-02-08
I have a ASUS P5Q Pro board and the AHCI setting was the one I used.
I backed up and edited grub/menu.lst before rebooting. Then I went into the BIOS setup on restart and changed the SATA drive settings. Straightforward and simple. I thank you again for your help.

I looked up AHCI on Wiki: [http://en.wikipedia.org/wiki/AHCI](http://en.wikipedia.org/wiki/AHCI)
Glad I'm no longer in the windoze world!

I have a PCIe graphics card installed, do I loose anything, perfromance wise, with the pci=nomsi switch?  At some point I'll try booting without the switch to see what happens.

---

