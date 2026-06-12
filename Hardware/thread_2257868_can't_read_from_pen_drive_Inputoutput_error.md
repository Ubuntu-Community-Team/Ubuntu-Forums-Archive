---
title: "can't read from pen drive: Input/output error"
date: 2014-12-23
forum: Hardware
---

### Post by black8 on 2014-12-23
Hey, I want to install kali linux from a usb. I used ```
dd
``` to burn the iso image on the usb. I followed [this guide. ]("http://docs.kali.org/installation/kali-linux-live-usb-install")But when I try to mount the usb on my lap, so that I can make it EFI bootable, I get this error message:

[img]http://i.imgur.com/8Iiditx.png[/img]

I tried twice and it is not working. What do I do? 

This is how I used ```
dd
```
```

sudo dd if=kali-linux-1.0.9a-amd64.iso of=/dev/sdb1 bs=512k
```

---

### Post by sudodus on 2014-12-23
You should not write to a partition but to the whole drive (start at the head of the drive)

This would probably work

```
sudo dd if=kali-linux-1.0.9a-amd64.iso of=/dev/sdx bs=512k
```

where **x** is the drive letter.

But it is risky. I suggest that you use ***mkusb*** instead, It 'wraps security' around ***dd*** (which is nick-named 'disk destroyer').

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

*Edit*: **x** is the drive letter, and there should be *no* partition number, **x** is **b** or **c** or **d** ...

---

### Post by black8 on 2014-12-23
@sudous, thankyou for your response. After a restart, the flash drive is automounted, but only as Read Only. In dmesg it is written that write protect is off, but when I try to mount manually, i get this message:

```
mount: /dev/sdb1 is write-protected, mounting read-only
```

 But anyway, I'll run dd again, how you asked me to do this. Before I do it, will you confirm for me if I am doing it right?

This is my dmesg output when i connect the pen drive:
```
[  602.909346] usb-storage 3-4:1.0: USB Mass Storage device detected
[  602.909676] scsi7 : usb-storage 3-4:1.0
[  603.908426] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer Blade     2.01 PQ: 0 ANSI: 6
[  603.909634] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  603.911869] sd 7:0:0:0: [sdb] 31266816 512-byte logical blocks: (16.0 GB/14.9 GiB)
[  603.912758] sd 7:0:0:0: [sdb] Write Protect is off
[  603.912773] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[  603.913105] sd 7:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  603.921240]  sdb: sdb1
[  603.923499] sd 7:0:0:0: [sdb] Attached SCSI disk

```

so is 'sdx' 'sdb1' or simply 'sdb'?

---

### Post by ajgreeny on 2014-12-23
The flash drive is /dev/sdb, the partition on that flash drive is /dev/sdb1.

You need to write to /dev/sdb, ie the whole drive not to the partition.

If you're not sure about these things it might have been easier to use something like unetbootin.

---

### Post by sudodus on 2014-12-23
+1 to *ajgreeny*'s advice:

You need to write to /dev/sdb, ie the whole drive not to the partition if the b drive, or /dev/sdc if the c drive. No partition number. But a simple typing error or mistaken drive letter might ruin your family pictures. This is why I was suggesting mkusb and *ajgreeny* suggests Unetbootin.

If it still does not work with the target /dev/sdb or with mkusb, you might need to make the iso file a hybrid iso file (described [here]("https://help.ubuntu.com/community/mkusb")).

---

### Post by black8 on 2014-12-23
The issue has been solved. My problem was that I didnot know how devices and partitions are named in linux, though I knew that the bootable media has to be written at the beginning of the device. Hence I ran the command again with target as /dev/sdb(as my pendrive is named sdb) and everything worked well.


I am new to linux and am in a phase of rapid learning. Thank you again for helping me out, *ajgreeny and sudous....*

---

