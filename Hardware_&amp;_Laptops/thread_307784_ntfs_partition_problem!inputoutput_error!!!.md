---
title: "ntfs partition problem!input/output error!!!"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by TheGraz on 2006-11-27
Hi everybody! I got troubles with the Ubuntu installation. I installed ubuntu on my friend laptop in this way

put live cd
resize htfs partition
reallorace the new size with ext3 and swap
continue installation

Ubuntu start, mount the ntfs partition but when I try to open it, ubuntu give me an input/output error, and i can't read what i have on that partition. Moreover, at the start i donnot have the opportunity to choose among windows and Ubuntu. The grub just give me Ubuntu as operating system. Ok who cares about windows but i need to take data from ntfs partitio otherwise this friend is going to kill me!!!!! 


Please help me. Tell me if u need some infos more.

---

### Post by xyz on 2006-11-27
Please post the output of both:
```
 cat /boot/grub/menu.lst

```
```
 cat /etc/fstab

```
Also see this:
[NTFS with read/write support using ntfs-3g ]("http://www.ubuntuforums.org/showthread.php?t=217009")
Good luck and feel free to ask questions.

---

### Post by TheGraz on 2006-11-27
Hi, 
here it is what u asked. I tried to put in the grub menu list also the (hd0,1) to get windows. It try to boot but give me that an error occured, ask to run win in safe model and bla bla bla i tried but it doesn't start. I think that windows file system broke up...Waht we can do?


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

