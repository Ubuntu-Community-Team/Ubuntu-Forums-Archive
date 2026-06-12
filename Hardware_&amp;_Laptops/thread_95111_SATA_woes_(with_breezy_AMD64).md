---
title: "SATA woes (with breezy AMD64)"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by rootneg1 on 2005-11-25
I've had Ubuntu up and running on this computer for a while, with pretty much everything working out of the box.  Recently, however, I got a new sata hard-drive and I would like to use this as the only hard-drive.  After prepartitioning it from a live CD and a (seemingly) succesful installation, on it's first solo boot it gets as far as

GRUB Loading stage 1.5.

and then stops, with no apparent hard-drive activity.  Since I was able to partition the drive from a live session (and verify it on a subsequent boot) I think the problem lies in the motherboard sata controller.  I would really like to use 160GB as more than a paperweight, any suggestions....?

OS: Ubuntu 5.10 AMD64
CPU: AMD64 3200+
Motherboard: DFI K8M800-MLVF (with onboard VIA sata/raid controller)
HDD: 160 GB seagate sata drive

---

### Post by transactionlogfiller on 2005-11-25
can you post what is in /boot/grub/menu.lst

It sounds like it is still trying to boot from the (now removed) ide hard drive.

---

### Post by teaker1s on 2005-11-25
[https://wiki.ubuntu.com/FakeRaidHowto]("https://wiki.ubuntu.com/FakeRaidHowto")

---

### Post by rootneg1 on 2005-11-25
In trying to get it to work i've since installed an old 1GB ide i had lying around for the boot partition. and now it goes slightly farther managing to get out

```
GRUB Loading, stage 1.5...

GRUB Loading, please wait...
```

and here's the grub default entry, so it's booting (or trying to) from the right drive.

```
title		Ubuntu, kernel 2.6.12-9-amd64-generic Default 
root		(hd0,0)
kernel		/vmlinuz root=/dev/sda1 ro quiet splash
initrd		/initrd.img
savedefault
boot
```

Teaker:  I don't want a RAID, I just have a single drive and I want it to behave as such.  I can properly mount it, partition it, read and write it as a regular old scsi drive from a live session; dmraid gives me no new devices...

---

### Post by teaker1s on 2005-11-25
suggested on other threads but as I only have another pc on sata with xp so anymore I don't know but  when i set xp up it needed to be tricked into a raid driver and other threads seem to suggest if ubuntu wont install perfectly this is a way

re reading your thread I understand it installs but won't boot check out some of the usb harddisk installs as they edited grub as it needed to be pointed to the right location or it fails to boot maybe thats your issue

---

### Post by transactionlogfiller on 2005-11-26
Can I ask, why did you partition the drive from a live CD an not just us the partitioning tool on the installation CD?

Here's something to try:

sudo fdisk /dev/sda

type 'p' to get a list of partions
the partition you want to boot from should have a * next to it.

When I had a similar problem I re-ran the installation CD up to the point where it asks about partitioning disks, just mounted all the existing partitions without formatting anything and then skipped to the installing grub section of the installation, then rebooted an it worked. Not a very elegant solution though.

---

