---
title: "Grub2 - unable to boot Windows 7"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by satellite360 on 2009-11-02
Hi all

Just installed Windows 7 and Ubuntu 9.10 on 2 separate HDDs.  Windows 7 boots fine when I detach the Ubuntu HDD but fails to boot from grub2.

Updating grub2 gives the following error:
```
$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
```

The device map shows only this:
```
$ cat /boot/grub/device.map 
(hd0)	/dev/sda
```

fdisk output:
```
$ sudo fdisk -l /dev/sda

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b36db89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2562    20579233+  83  Linux
/dev/sda2           38787       38913     1020127+  82  Linux swap / Solaris
/dev/sda3            2563       38786   290969280   83  Linux

Partition table entries are not in disk order
```

```
$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f2d153b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       10396    83398656    7  HPFS/NTFS
/dev/sdb3           10396       38914   229067776    7  HPFS/NTFS
```

Any idea what I need to do to get grub2 to boot Windows 7 (/dev/sdb2)?

---

### Post by satellite360 on 2009-11-03
I solved this by adding the following to /etc/grub.d/40_custom
```
menuentry "Windows 7 (on /dev/sdb1)" {
insmod ntfs
set root=(hd1,1)
chainloader +1
}
```
No idea why the os-prober is not adding the correct details but until grub2 is fixed this workaround will do.

---

### Post by yaiyuy8W on 2009-11-21
Thank you!

This fixed my infinite Windows 7 and Vista boot loop!

---

### Post by crowdofone on 2010-06-02
This looks very similar to the solution i hit on where it would boot if i placed an extra entry in /etc/grub.d/40_custom that was a copy of the Windows 7 entry from grub.cfg with the highlighted red text removed.

```

menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid [COLOR="Red"]--set 2cb8b1f1b8b1b9a2[/COLOR]
	chainloader +1
}

```

In my case i think the search parameter has to be included but the following --no-floppy & --fs-uuid were optional.

I also needed to run update-grub after to rebuild grub.cfg

.

---

### Post by garvinrick4 on 2010-06-02
> **satellite360 said:**
> I solved this by adding the following to /etc/grub.d/40_custom
```
menuentry "Windows 7 (on /dev/sdb1)" {
insmod ntfs
set root=(hd1,1)
chainloader +1
}
```No idea why the os-prober is not adding the correct details but until grub2 is fixed this workaround will do.
I do not believe grub2 is broken as long as you put grub into sda or sdb. It is a little trickier if you add Windows second. If you copy grub from a viable / and into sda or sdb wherever it is needed with a live CD it works like a charm. You have Windows first install it gets overwritten by grub when Linux installed 2nd never notice and works without touching it. Linux internal, Windows USB and wanting grub2 to work out of box without installing it is pretty tough on grub2. Glad you got her fixed up. Have a nice day.

---

### Post by en666 on 2012-07-18
None of above solutions worked for me. With these solutions Windows7 boots once, then i have to redo update-grub to make the menuentry work again.
I registered an account here only for comunicate you that I found a definitive solution. I use ubuntu 10.04 but I think that it's ok for all distros.

[http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

10.04 :guitar:s!

---

