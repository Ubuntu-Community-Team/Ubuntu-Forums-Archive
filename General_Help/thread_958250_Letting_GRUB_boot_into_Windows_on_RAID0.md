---
title: "Letting GRUB boot into Windows on RAID0"
date: 2008-10-25
forum: General Help
---

### Post by Davidhal on 2008-10-25
Hi, I'm new to these forums so I apologize if this is the wrong section. 

I'm trying to set up a "triple" boot, Windows XP 32-bit, Windows Vista 64-bit and Ubuntu 8.04 64-bit. 

Here's how my hard drives are set up:

2x 320GB (RAID0): Windows XP | Windows Vista | Games 
200GB: Ubuntu
500GB: Storage
500GB: Storage

Apparently I missed the part where I choose where to install GRUB, and it installed on HD0 I guess, because it loads GRUB instead of the Windows MBR, even though GRAID is first boot in the BIOS.

Is there any way to let GRUB boot into a RAID0 array? 

Or if not, move GRUB to another disk, so that I can access the Vista MBR, which IIRC can be set to boot into Ubuntu with some tweaks.

Thanks for your help in advance.

---

### Post by _sAm_ on 2008-10-25
David this info might be interesting for you:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by caljohnsmith on 2008-10-25
Since you have Grub working, you could just add an entry to boot Windows in your Grub menu. You can open up your Grub's menu.lst by opening a terminal (applications > accessories > terminal) and doing:
```
gksudo gedit /boot/grub/menu.lst
```
Because it sounds like Grub was installed to the MBR (Master Boot Record) of your Windows drive, then you should be able to use the following entry to boot Windows (just add it to the end of the menu.lst file):
```
title Windows Vista
root (hd0,0)
chainloader +1
```
If that doesn't work, then please post:
```
sudo fdisk -lu
```
Otherwise, let me know how it goes. :)

---

### Post by Davidhal on 2008-10-25
> **caljohnsmith said:**
> Since you have Grub working, you could just add an entry to boot Windows in your Grub menu. You can open up your Grub's menu.lst by opening a terminal (applications > accessories > terminal) and doing:
```
gksudo gedit /boot/grub/menu.lst
```
Because it sounds like Grub was installed to the MBR (Master Boot Record) of your Windows drive, then you should be able to use the following entry to boot Windows (just add it to the end of the menu.lst file):
```
title Windows Vista
root (hd0,0)
chainloader +1
```
If that doesn't work, then please post:
```
sudo fdisk -lu
```
Otherwise, let me know how it goes. :)
I restored the MBR of windows and then I installed GRUB on the same disk running Ubuntu. Right now I just set my Ubuntu disk to boot before the GRAID in BIOS.

Here's my fdisk report:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         419         419           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2               0    60817407    30408704    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sda3        83951616    83951616           0    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sda4      2619167861  6461634220  1921233180    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sda2: 31.1 GB, 31138512896 bytes
255 heads, 63 sectors/track, 3785 cylinders, total 60817408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sda2p1   *         419         419           0    0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sda2p2               0    60817407    30408704    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sda2p3        83951616    83951616           0    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sda2p4      2619167861  6461634220  1921233180    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x32383237

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   314568764   157284351    7  HPFS/NTFS
/dev/sdb2       314568765   629137529   157284382+   7  HPFS/NTFS
/dev/sdb3       629137530  1250162234   310512352+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e42bc65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   374796449   187398193+  83  Linux
/dev/sdc2       374796450   390716864     7960207+   5  Extended
/dev/sdc5       374796513   390716864     7960176   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e5d5476

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd60ed60e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   976751999   488375968+   7  HPFS/NTFS

```

---

### Post by caljohnsmith on 2008-10-25
OK, from the Linux Live CD:
```
sudo mount /dev/sdc1 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
Change the line that has "# groot=(hdX,Y)" to:
```
# groot=(hd0,0)
```
Also change all your Ubuntu entries to use (hd0,0) similar to:
```
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```
Then add the following entries at the end for Windows:
```
title	   Windows XP/Vista (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP/Vista (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP/Vista (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title	   Windows XP/Vista (hd4)
root       (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
One of those entries should work to boot either XP or Vista, depending on which is in the first partition of the Windows drive, and depending on whether Vista put its boot files in the first partition when you installed it.

---

