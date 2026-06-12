---
title: "Windows not being detected by update-grub"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by Buzzdee on 2007-12-31
Hi.
I had Gutsy installed for a while. Then I added Windows and restored GRUB by doing
```
find /boot/grub/stage1
root (hd0,0)
setup (hd0,0)
```
after mounting my root partition.
I have only one SATA-2 drive installed, partitioned to 
sda1 ext3
sda3 ntfs
sda5 swap
while the Device Manager (System -> Preferences) seems to refer to the entire drive as "sda2", according to the size of the individual devices. 

```
title Windows 95/98/NT/2000/XP
root (hd0,2)
makeactive
chainloader +1
```
gave me a working Windows. This will unfortunately be overwritten the next time a new kernel is installed. 
Now my problem is, that
```
sudo grub-update
``` doesn't find the windows partition, although it can be read in Nautilus (SATA-2, NTFS formatted), i.e. drivers are there. 
Could someone please help me?

System info:
Gutsy Gibbon 64bit, Thinkpad T61p with a Core2Duo, SATA-2 160 GiB formatted 
sda1 ext3 ubuntu
sda3 ntfs vista
sda5 swap
```
fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6375       18711    99096952+  83  Linux
/dev/sda2           18712       19457     5992245    5  Extended
/dev/sda3   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda5           18712       19457     5992213+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Thanks a lot in advance, 

Bastian

PS: There was a similar thread in "General Help", but this seems to be dead, no-one answered  there.

---

### Post by Sef on 2007-12-31
> fdisk -l:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6375       18711    99096952+  83  Linux
/dev/sda2           18712       19457     5992245    5  Extended
/dev/sda3   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda5           18712       19457     5992213+  82  Linux swap / Solaris

Partition table entries are not in disk order

Windows likes to be on the first partition.  That could be the problem (or a part of it.)

---

### Post by matburton on 2007-12-31
Hey,

You should put static boot options after the ### END DEBIAN AUTOMAGIC KERNELS LIST so that when update-grub happens these entries are preserved.

Here's the relevant part of my menu.lst:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a68734ce-8920-43ff-a980-9b1498587bf1 ro ramdisk_size=65536 quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a68734ce-8920-43ff-a980-9b1498587bf1 ro ramdisk_size=65536 single
initrd		/boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Hope that helps ;)

Mat

---

### Post by mridkash on 2007-12-31
I have this problem too, and windows is on the first partition. It started happening when I resized the windows partition to install ubuntu. It was fine before that.
I have fixed that with a static entry in grub list.

I'm wondering why the problem occurred? I thought it wiped my windows installation the moment it didn't add windows to the boot menu.

---

### Post by Buzzdee on 2007-12-31
Yes, I've read about the static fix outside the automatic region.
This should, by my understanding, work. Nontheless, I wonder why the partition isn't recognised by update-grub. Let's consider the problem solved (or should I say 'worked around'?), but if someone happens to know the cause of the problem, I'll check back from time to time and would appreciate any information on that topic.

edit: yes, my partitions are ordered on the hard drive: 1st windows ntfs, 2nd linux ext3, 3rd swap

---

