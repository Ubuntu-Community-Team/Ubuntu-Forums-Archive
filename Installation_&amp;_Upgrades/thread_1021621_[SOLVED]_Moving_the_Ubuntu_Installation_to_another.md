---
title: "[SOLVED] Moving the Ubuntu Installation to another partition"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by Jofarmer on 2008-12-25
So I managed to convince my parents to dump MS altogether. Partitions 1&2 get deleted (windows & apps on another partition) and the Ubuntu partition  should be freed from the logical partition it has been sharing with the swap for quite some time now. Since I also upgraded the RAM I created a new swap partition and a new primary partition (ext3) for Ubuntu. Using```
sudo dd if=/dev/sda6 of=/dev/sda2 bs=2M
``` I "copied" the perfectly running Ubuntu installation to the bigger new partition. But no matter how much I have been fiddling with grub, it will only boot the old partition, even refuses to see the new one... Any how-to I overlooked? I HAVE to use the old working install and want it to reside in the new partition.
Any help will be greatly appreciated!

---

### Post by sisco311 on 2008-12-25
you need to change the uuid of sda2

i.) unmount the partition:
```
sudo umount /dev/sda2
```

ii.) change the uuid:
```
sudo tune2fs -U random /dev/sda2
```

iii.) get the new uuid:
```
sudo blkid /dev/sda2
```

iv.) mount the partition and replace the old uuid in:

[list]
[*]*mount/point*/boot/grub/menu.lst 
[*]*mount/point*/etc/fstab 
[*]*mount/point*/etc/initramfs-tools/conf.d/resume[/list]

```
gksu gedit *path/to/file*
```

v.) add a new entry to the menu.lst:
> title  UBUNTU
uuid <uuid of sda2 here>
kernel /boot/vmlinuz[..] root=UUID=<uuid of sda2> ro [...]
initrd /boot/initrd[..]


vi.) reboot

vii.) if that works, then reinstall grub to MBR or to sda2:

```
sudo grub

root (hd0,1)
setup (hd0)
```

or

```
sudo grub

root (hd0,1)
setup (hd0,1)
```

---

### Post by caljohnsmith on 2008-12-25
Have you checked to make sure you can mount the partition you copied? Because you could be missing the last 2 MB of the partition the way you copied it with dd. You should use something like:
```
sudo dd if=/dev/sda6 of=/dev/sda2 bs=2M [COLOR="Blue"]conv=notrunc[/COLOR]
```
That way if the partition is not an exact multiple of 2 MB, you will be sure to copy every single byte of the partition. Also, was the sda2 partition originally the exact same size as the sda6 partition? Because if not, then your HDD's partition table will unfortunately be corrupt now. How about posting the output of the following script so I can get a better picture of your current setup:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post.

---

### Post by Jofarmer on 2008-12-26
> **sisco311 said:**
> 

iv.) mount the partition and replace the old uuid in:

[list]
[*]*mount/point*/boot/grub/menu.lst 
[*]*mount/point*/etc/fstab 
[*]*mount/point*/etc/initramfs-tools/conf.d/resume[/list]


I think you want me to mount the new partition and replace the old uuid with the new one, right? The problem is, I cannot mount the new partition. Probably because both the new and the old want to be mounted as "/" :(

---

### Post by Jofarmer on 2008-12-26
> **caljohnsmith said:**
>  Also, was the sda2 partition originally the exact same size as the sda6 partition? Because if not, then your HDD's partition table will unfortunately be corrupt now.
No, it wasn't - that was the whole point, to have more space. Time fore an installation of testdisk?> **caljohnsmith said:**
>   How about posting the output of the following script so I can get a better picture of your current setup:Will do, coming up in a few hours.

---

### Post by piojunbabia on 2008-12-26
i dont understand what are you all talking about.. but i want to learn... i think these have something to do with the systems of linux and i want to learn how to do stuffs in linux - ubuntu. Im planning to use linux in the future coz im still using winxp today.

i need help, please answer post on this thread. thank you/
[http://ubuntuforums.org/showthread.php?t=1021905](http://ubuntuforums.org/showthread.php?t=1021905)

---

### Post by Jofarmer on 2008-12-26
Another possible solution to my dilemma could be a complete new install of Ubuntu while preserving the home folder in a fashion described [here]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/"). Would that work even with multiple users?

(Still no access to the system in question, it is in the currently occupied guest room)

---

### Post by Jofarmer on 2008-12-26
> **caljohnsmith said:**
> please copy/paste the contents of that file to your next post.

I did not want to paste 537 lines of text, so please find it zipped and attached to this post.

---

### Post by caljohnsmith on 2008-12-26
Well the good news is that it appears you can mount sda2 OK, but part of the problem right now is that the new sda2 partition and the old sda6 partition have the same UUIDs since you did an exact clone. How about changing the UUID of your old sda6 partition to something different with:
```
sudo tune2fs -U random /dev/sda6

```
Then reboot, and when you choose to boot Ubuntu from your Grub menu, you should be booting into sda2 and not sda6. If you can boot successfully into Ubuntu, please post the output of:
```
mount
df -h
```
And we can work from there. :)

---

### Post by Jofarmer on 2008-12-26
Unfortunately I had changed both uuids by now, still grub only boots sda6 (hd0,5). By now I feel like there's a /boot/grub/menu.lst on every partition and I don't know which to change.

Interestingly I saved your RESULT to my desktop, but even though /dev/sda6 is the only mounted fs, its not here on reboot. Please find the most up-to-date RESULT attached.

---

### Post by caljohnsmith on 2008-12-26
OK, I believe I see the problem. How about while you are booted into sda6, do the following:
```
sudo mount /dev/sda2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then change your Ubuntu entries as follows:
```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR]
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2ad23796-968a-4a75-bb68-2283b6a35274 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR]
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2ad23796-968a-4a75-bb68-2283b6a35274 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR] ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR]
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR] ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```
Also be sure to change the "# kopt=...." line:
```
# kopt=root=UUID=[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR] ro
```
Next open the fstab:
```
gksudo gedit /mnt/etc/fstab
```
And change it to:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/[COLOR="Blue"]sda2[/COLOR]
UUID=[COLOR="Blue"]2ad23796-968a-4a75-bb68-2283b6a35274[/COLOR] /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4cae9688-2d1e-437c-93e8-15177ee8ac4c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Save, reboot, and I think you should be all set, but let me know how it goes.

---

### Post by Jofarmer on 2009-01-04
Wow! A big thank you, you really went out of your way to help me - and it worked perfectly :-)

I could not try it before because I "had" to go to Sweden on holiday before I could find time... (Great country, btw - everyone speaks English)

No the last remaining issue is that because I used dd to "copy" the partition, it *thinks* it is as small as the old one (see attached screenshot), but maybe I get that figured out by myself until I come visit my parents again (in a months time) - I am thinking about booting the CD and using gparted to grow sda2 to the size of sda2+sda3.

Happy new year to all!

---

### Post by caljohnsmith on 2009-01-04
Hi Jofarmer, I think we might have a solution to your sda2 lost space issue, courtesy of forum member meierfra. How about posting the output of all the following commands:
```
df -h
sudo umount /dev/sda2
sudo e2fsck -f /dev/sda2
sudo resize2fs /dev/sda2
df -h
```

---

### Post by Jofarmer on 2009-01-31
Thanks a lot, that did the trick!:KS

---

