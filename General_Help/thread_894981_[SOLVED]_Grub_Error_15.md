---
title: "[SOLVED] Grub Error 15"
date: 2008-08-19
forum: General Help
---

### Post by jackn on 2008-08-19
Issue:
I get Grub's "error 15":
[INDENT]Grub Loading stage 1.5
Grub loading  please wait
Error 15[/INDENT]
Obviously, as a result, I can now boot and access my files only with a live CD. Note that the boot stops before Grub's menu displays.

System:
Dual boot, XP and Hardy. Asus A8JS laptop.

Background:
This came about after the following: In order to create a new virtual hard disk for Virtualbox, I had to make my /home partition larger. Since it was stuck between two other partitions, I had to copy it and move it to a new position, using gParted.
When I was done, I was no longer able to boot.

Measures taken:
I've tried all of the following, to no avail:
* Restored the partition to its original location and size.
Following various threads in the forums, I've also tried other measures:
* Ran grub-install after mounting the root partition. The response was that 'sda' was not found or was not a block device.
* Ran Grub and used 'find' to get the parameters of 'hd':
```
grub>find /media/sda5/boot/grub/stage1
```.
This gave 'Error 15, file not found".
* As it seemed root's device name has changed (sda6 to sda5), I changed all of the (hd0,5) in /boot/grub/menu.lst to (hd0,4).


Can you please help?

Jackn

---

### Post by spiderbatdad on 2008-08-19
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by jackn on 2008-08-28
Thank you kindly, spiderbatdad.

To me, the following advice was particularly instructive:
```

sudo mount -t proc none /mnt/root/proc

sudo mount -o bind /dev /mnt/root/dev
```

It is often omitted that these mounts, too, will be necessary.

Belated, but hearty, thanks.

jackn

---

