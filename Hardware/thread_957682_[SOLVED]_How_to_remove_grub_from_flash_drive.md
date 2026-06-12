---
title: "[SOLVED] How to remove grub from flash drive?"
date: 2008-10-24
forum: Hardware
---

### Post by josephellengar on 2008-10-24
I was trying to create a multiboot flash drive, but with the new usb boot feature in intrepid, I made one that way.  And, now I can't remove grub from teh flash drive so it doesn't work at all.  Thanks!

---

### Post by caljohnsmith on 2008-10-24
Grub gets installed to the MBR (Master Boot Record) of the drive so that it is bootable, but that should not affect whether you can mount the drive and use it. When you say the flash drive "does not work at all", if you mean can't even mount the drive and transter files to and from the drive, then that's not Grub's fault; removing Grub from the MBR will unfortunately not help. What exactly do you mean by "does not work at all"?

---

### Post by josephellengar on 2008-10-24
> **caljohnsmith said:**
> Grub gets installed to the MBR (Master Boot Record) of the drive so that it is bootable, but that should not affect whether you can mount the drive and use it. When you say the flash drive "does not work at all", if you mean can't even mount the drive and transter files to and from the drive, then that's not Grub's fault; removing Grub from the MBR will unfortunately not help. What exactly do you mean by "does not work at all"?

I'm trying to install ubuntu to it.  Now, when I try to reboot after using the intrepid "create usb startup disk" thing, it puts me into a grub screen, with links to partitions that aren't there.

---

### Post by caljohnsmith on 2008-10-24
Can you be more specific? You get the Grub menu on start up, but when you choose an OS it won't boot? Or what do you mean by "links to partitions that aren't there"?

---

### Post by josephellengar on 2008-10-24
> **caljohnsmith said:**
> Can you be more specific? You get the Grub menu on start up, but when you choose an OS it won't boot? Or what do you mean by "links to partitions that aren't there"?

The flash drive thinks that the partitions I am trying to access are on the flash drive, when somehow they are actually the partitions that are on my main hard drive ubuntu, windows, Fedora etc.

---

### Post by caljohnsmith on 2008-10-24
That sounds like it may be a simple problem with your Grub's menu.lst. With your flash drive connected, how about booting your Live CD and posting:
```
sudo fdisk -lu
```
From the above results, figure which is your Ubuntu partition on the flash drive in the form sdXY (like sdb2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```

sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
Post the results of the above commands; also, for whichever drive is your flash drive, like [COLOR="Red"]sdb[/COLOR] for example, post the results of:
```
sudo dd if=/dev/[COLOR="Red"]sdb[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/[COLOR="Red"]sdb[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump

```
That should hopefully give us enough info to fix your problem.

---

### Post by josephellengar on 2008-10-24
Thank you very much.  I managed to figure it out though.  I pasted a dd command that someone else gave me on another linux forum and that managed to fix it.

---

