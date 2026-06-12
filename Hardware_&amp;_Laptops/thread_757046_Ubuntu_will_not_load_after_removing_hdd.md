---
title: "Ubuntu will not load after removing hdd"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by ledek on 2008-04-16
Using Ubuntu 7.10

My computer have 3 hdds, lets call them:
hddA
hddB
hddC
(bought and installed in that order)

My ubuntu installation is located on hddB and everything works great.


The thing is that I intend to give hddA (the smallest one) to my parents.

Soo... I shut down, remove hddA and restarts. Everything should work right?
But of course it doesn't. The GRUB is located on hddA :(
So I pop in the live cd and set up an new GRUB on hddB, restarts.
Yay, the OS selection screen shows up and everything seems to work... 
But when selecting Ubuntu from the list I get "Error 5: Partition table invalid or corrupt" :(:(
Apparently the GRUB thinks hddB is "hd1" which it was before hddA was removed, now hddB is known to the GRUB as hd0, so I pop in the live cd again and edit /boot/grub/menu.lst and restarts.

Now it should work right???
It does not :(:(:(

I get past the GRUB and get the load screen with the bar but the bar stops after about 2mm and nothing happens. So WHY does ubuntu hang/freeze while loading?

---

### Post by metalf8801 on 2008-04-16
Have you try putting hddA and booting from it? If so what happened? 

If you can't try that this might work but I can understand why you might now what to try. 
Find another Linux distribution that you want to try like Linux Mint then repartition B or C  then install Linux Mint on the new partition while both drives are connected. Ubuntu should now be listed below Linux Mint with all the other OS you have on your computer.  

Oh you might need to undo your last few changes for that to work.

If you find a better way to fix your problem please post what you did and if not I hope this helps.  

Good luck 
Dan

---

### Post by ledek on 2008-04-16
I'm not sure I understand you correctly. Do you suggest that I install MINT (or other distro) in order to get a new, fresh, fully working GRUB?

I'm pretty certain that the GRUB's not the problem right now since I'm getting past it.

My guess is that ubuntu somehow expects to find hddA while loading. But since I don't know what to do about it that doesn't really help.

I forgot to say so but everything works perfectly fine as soon as I put hddA back.

Unless anyone can help me I guess I'll keep the drive until 8.04 goes live and then reinstall ubuntu. Though I'd rather avoid it if possible.

Thanks anyway, and I might try it if nothing else helps.

---

### Post by lswest on 2008-04-16
Well, if you could, remove hddA, then, at the GRUB menu, select the first Ubuntu partition and hit "e" to edit the entry, and on the 3rd line, hit "e" again to edit it and delete "usplash" from the line.  Then hit enter and then "b" to boot it with the temporarily altered boot parameters.  See what error it gives when it hangs.  (basically the process above just removes the GUI from the boot process for this one instance)

---

### Post by ledek on 2008-04-16
I didn't find any "usplash" parameter but I did find "splash" on line 2. When I removed it and tried to boot I didn't get any further than:

Starting up...
Loading, please wait...

Thanks for helping out btw :)

---

### Post by metalf8801 on 2008-04-16
> **ledek said:**
> I'm not sure I understand you correctly. Do you suggest that I install MINT (or other distro) in order to get a new, fresh, fully working GRUB?

I'm pretty certain that the GRUB's not the problem right now since I'm getting past it.

My guess is that ubuntu somehow expects to find hddA while loading. But since I don't know what to do about it that doesn't really help.

I forgot to say so but everything works perfectly fine as soon as I put hddA back.

Unless anyone can help me I guess I'll keep the drive until 8.04 goes live and then reinstall ubuntu. Though I'd rather avoid it if possible.

Thanks anyway, and I might try it if nothing else helps.

I have had problems like this and i have used the live cd to restore grub and it didn't work I would get grub but it wouldn't load OS and ended up installing an other OS i don't remember which one but it might have been Linux Mint and for some reason that work.

---

### Post by ledek on 2008-04-16
So Ubuntu started working again when you installed Mint (or whatever it was)?

---

### Post by metalf8801 on 2008-04-16
yes

---

### Post by prshah on 2008-04-16
> **ledek said:**
> 
I get past the GRUB and get the load screen with the bar but the bar stops after about 2mm and nothing happens. So WHY does ubuntu hang/freeze while loading?

Use Ctrl+Alt+F1 and/or Ctrl+Alt+F8; anything useful you can tell use (Just the last couple or so lines of output?)

---

### Post by ledek on 2008-04-16
Starting up...
Loading, please wait...

Is all I get when pressing Ctrl+Alt+F1 (Ctrl+Alt+F8 doesn't do anything).

I'll post some files that might help:

/boot/grub/menu.lst (excluding all the comments)
```

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=2844115b-935f-40f3-a2a3-5346bd5a4b71 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=2844115b-935f-40f3-a2a3-5346bd5a4b71 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2844115b-935f-40f3-a2a3-5346bd5a4b71 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2844115b-935f-40f3-a2a3-5346bd5a4b71 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

/boot/grub/device.map
```

(hd0)	/dev/sda
(hd1)	/dev/sdb

```

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system>	<mount point>	<type>		<options>			<dump>	<pass>

proc		/proc		proc		defaults			0	0
/dev/sdb3	/		ext3		defaults,errors=remount-ro 	0	1
/dev/sdc	/home		ext3		defaults			0	2
#/dev/sda1	/media/sda1	ntfs-3g		defaults,locale=sv_SE.UTF-8	0	1
#/dev/sda5	/media/sda5	ntfs-3g		defaults,locale=sv_SE.UTF-8	0	1
/dev/sdb5	/media/sdb5	ntfs-3g		defaults,locale=sv_SE.UTF-8	0	1
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec		0	0
/dev/fd0	/media/floppy0	auto		rw,user,noauto,exec		0	0
/dev/sdb1	none		swap		sw				0	0

```

---

### Post by prshah on 2008-04-17
> **ledek said:**
> Starting up...
Loading, please wait...

Is all I get when pressing Ctrl+Alt+F1 (Ctrl+Alt+F8 doesn't do anything).

I'll post some files that might help:```

# /etc/fstab: static file system information.
#
# <file system>	<mount point>	<type>		<options>			<dump>	<pass>

proc		/proc		proc		defaults			0	0
/dev/sdb3	/		ext3		defaults,errors=remount-ro 	0	1
[color=red]/dev/sdc	/home		ext3		defaults			0	2[/color]
#/dev/sda1	/media/sda1	ntfs-3g		defaults,locale=sv_SE.UTF-8	0	1
#/dev/sda5	/media/sda5	ntfs-3g		defaults,locale=sv_SE.UTF-8	0	1
/dev/sdb5	/media/sdb5	ntfs-3g		defaults,locale=sv_SE.UTF-8	0	1
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec		0	0
/dev/fd0	/media/floppy0	auto		rw,user,noauto,exec		0	0
/dev/sdb1	none		swap		sw				0	0

```

Your /home partition entry seems to be wrong. I don't think you can have a partition /dev/sdc.. it should be "/dev/sdc1" or something like that. Can you boot to recovery mode? (Scratch that question, obviously, you can... )

The output of ```
fdisk -l /dev/sdc
``` may help. (No "sudo" required in recovery mode, else add "sudo")

---

### Post by ledek on 2008-04-17
```

fdisk -l /dev/sdc

Disk /dev/sdc: 250,0 GB, 250059350016 byte
255 heads, 63 sectors, 30401 cylinders
Units = cylinders of 16065 · 512 = 8225280 byte
Diskidentifier: 0x00000000

Disk /dev/sdc have no valid partition table.

```
Translated from swedish



Invalid partition table does indicate that something is wrong. But as I've said I have NO problems whatsoever as long as the disk I want to remove stays plugged in. sdc works perfectly as /home.

I guess it still could mess things up though I don't know how.


I'll give you the output from
fdisk -l /dev/sda
and
fdisk -l /dev/sdb
as well (not traslated though)
```

Disk /dev/sda: 120,0 GB, 120034123776 byte
255 huvuden, 63 sektorer/spår, 14593 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x014e014d

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1         653     5245191    7  HPFS/NTFS
/dev/sda2             654       14592   111965017+   f  W95 Utökad (LBA)
/dev/sda5             654       14592   111964986    7  HPFS/NTFS


Disk /dev/sdb: 200,0 GB, 200049647616 byte
255 huvuden, 63 sektorer/spår, 24321 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x00b38b80

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1            2222        2482     2096482+  82  Linux växling / Solaris
/dev/sdb2            2483       24320   175413735    f  W95 Utökad (LBA)
/dev/sdb3   *           1        2221    17840151   83  Linux
/dev/sdb5            2483       24320   175413703+   7  HPFS/NTFS

Posterna i partitionstabellen är inte i diskordning

```
The last line states that the posts in the partition table of sdb is not in "diskorder" or something like that.

---

### Post by lavinog on 2008-04-17
> **ledek said:**
> ```

Disk /dev/sdb: 200,0 GB, 200049647616 byte
255 huvuden, 63 sektorer/spår, 24321 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x00b38b80

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1            2222        2482     2096482+  82  Linux växling / Solaris
/dev/sdb2            2483       24320   175413735    f  W95 Utökad (LBA)
/dev/sdb3   *           1        2221    17840151   83  Linux
/dev/sdb5            2483       24320   175413703+   7  HPFS/NTFS

Posterna i partitionstabellen är inte i diskordning

```
The last line states that the posts in the partition table of sdb is not in "diskorder" or something like that.

since your linux partition is on sdb
shouldn't your menu.lst read:
```

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=2844115b-935f-40f3-a2a3-5346bd5a4b71 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386
quiet

```
*changed root (hd0,2) to root (hd1,2)*

something doesn't seem to match up with menu.lst, fstab and fdisk

---

### Post by prshah on 2008-04-17
> **ledek said:**
> ```

fdisk -l /dev/sdc

Disk /dev/sdc have no valid partition table.

```
Translated from swedish
Invalid partition table does indicate that something is wrong. But as I've said I have NO problems whatsoever as long as the disk I want to remove stays plugged in. sdc works perfectly as /home.



Maybe because when you plug that other disk in, _it_ becomes hdc and you have a /home on that which is being used?

In any case, except for this; I don't know if anything else is wrong.

---

