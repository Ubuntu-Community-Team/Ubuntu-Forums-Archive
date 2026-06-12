---
title: "How to add a drive with already installed Kubuntu to a Windows box?"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by f3tus on 2006-03-18
Ok so I've got this PC running XP, and I want to add a drive which has Kubuntu already installed.
Whenever I boot, XP loads straight away, but I want GRUB to load so I can choose from either XP or Kubuntu.
Please help me out :/

Sorry for posting twice.

---

### Post by peppermint on 2006-03-18
All you need to do is change the boot order in the bios settings so your kubuntu drive boots first.

After that, you will need to edit grub to let you boot into windows from grub.

---

### Post by aysiu on 2006-03-18
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by f3tus on 2006-03-21
Sorry it took me so long to reply, but... I tried that and it is not working.

```
grub> root (hd0,4)
 Filesystem type unknown, partition type 0x5
```

It's ReiserFS

This is the menu.lst from grub:
```
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdc5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdc5 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

This is the fstab:
```

/dev/hdc5       /               reiserfs notail          0       1
/dev/sda1       /media/sda1     ntfs    uid=500,gid=500,umask=000,exec,dev,rw 1 0
/dev/hdc6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /mnt/sdb1       auto  noauto,user 0 0

```

fdisk -l output:
```

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc5             949        4604    29366788+  83  Linux
/dev/hdc6            4605        4734     1044193+  82  Linux swap / Solaris

```

Please help, I've got too much stuff on this drive I don't want to lose.

---

### Post by al108 on 2006-03-22
Could you be more specific on what it did when it din't work? Did you try changing Boot order in BIOS? Most probably you can't load it because your drives have different names in a new system. ie whatever was hdc now could be hda or hdb... So if you can simply make that drive (by connecting it to a different cable on your controller) to be whatever it was (hdc?), and making it a boot disk in BIOS you'll be able to boot from it without changing anything else. 

If everything else fails - install ubuntu on a differnet partition and copy the stuff from your drive, or use live CD to boot and copy your stuff.

---

### Post by f3tus on 2006-03-22
As you can see, the names are unchanged. And no, I have not tried anything with BIOS.

I have done everything like it says on the wiki, but got the grub error message instead.

I'll try this tomorrow [http://www.linux.com/article.pl?sid=04/11/18/232240](http://www.linux.com/article.pl?sid=04/11/18/232240) but, Ubuntu/Kubuntu can't be booted with the rescue parameter. Is this going to be a problem?

---

### Post by al108 on 2006-03-24
[QUOTE=f3tus]...I have not tried anything with BIOS. [/QUOTE]

Changing boot order in bios is a lot faster and easyer than using rescue mode, and since you don't change anything on the hard drive you don't have a risk of  loosing data, and you have a good chance of it to just boot into your kubuntu. From there like pepperimt sayed you can modify grub if you need.
Alternatively, you can try to disconnect you win hard disk temporarily and see if you can boot your kubuntu, that should make your kubuntu the only drive in a system and it should boot from it. It's worth a try at least.

The article from linux.com describes using a CD to boot into a rescue mode, so which "rescue mode" are you talking about the one in grub or on CD?

Good luck

---

