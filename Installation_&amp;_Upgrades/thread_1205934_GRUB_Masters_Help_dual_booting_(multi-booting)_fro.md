---
title: "GRUB Masters: Help dual booting (multi-booting) from two disks"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by ryankask on 2009-07-06
Greetings all!

My new 500MB hard disk arrived today and I installed it. I already have one disk that dual boots Kubuntu and Vista. I just installed Kubuntu again on the new disk and chose not to install a boot loader.

The first disk is /dev/sda and the second /dev/sdb. The new Kubuntu on the new disk is installed on the partition /dev/sdb1...after mounting it, it clearly is the new install

ryan@ryan-linux:/media/kubuntu$ ls .
bin   cdrom  etc   initrd.img  lost+found  mnt  proc  sbin     srv  tmp  var
boot  dev    home  lib         media       opt  root  selinux  sys  usr  vmlinuz

I can verify this by checking that /home/ryan is empty (so I have two Kubuntu installs on two different disks and I am writing to you from disk and partition /dev/sda5.

Here is a screenshot to verify this of KDiskFree:

[IMG]http://www2.ryankaskel.com/misc/images/screenshots/kdiskfree_screengrab.png[/IMG]

So I'm left wondering how to configure GRUB to boot this freshly installed OS. Here is my current GRUB menu.lst:

```
ryan@ryan-linux:/media/kubuntu$ cat /boot/grub/menu.lst
splashimage (hd0,4)/boot/grub/splashimages/83825-alisa.xpm.gz
default 0                                                    
timeout 20     #                                                                        
## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-11-generic
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=006b55f4-bf2e-4d31-978d-0a254b8658d0 ro quiet splash
initrd /boot/initrd.img-2.6.27-11-generic                                                            

title Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=006b55f4-bf2e-4d31-978d-0a254b8658d0 ro  single
initrd /boot/initrd.img-2.6.27-11-generic                                                       

title Ubuntu 8.10, kernel 2.6.27-9-generic
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=006b55f4-bf2e-4d31-978d-0a254b8658d0 ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic                                                            

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=006b55f4-bf2e-4d31-978d-0a254b8658d0 ro  single
initrd /boot/initrd.img-2.6.27-9-generic                                                       

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin  

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Dell Utility Partition
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
savedefault
makeactive

title Kubuntu 9.04 Dev OS
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1
makeactive


```

Is there anything obviously wrong you see with this configuration? Is this the correct way to load Linux on a second disk or should the entry look more like: 

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=006b55f4-bf2e-4d31-978d-0a254b8658d0 ro  single
initrd /boot/initrd.img-2.6.27-9-generic      
[B][I]
Any help is greatly appreciated!!!!![/I][/B]

Cheers,
Ryan

---

### Post by dstew on 2009-07-06
Assuming you installed the second Kubuntu on /dev/sdb1, you first should get the correct volume id (UUID) for this partition:```
vol_id /dev/sdb1
```Then, you need to create a new entry in your menu.lst file. You should look in /dev/sdb1/boot to see what the kernel (vmlinuz file) and initial ramdisk image (initrd.img) file names are. Then, create a new menu item in your first Kubuntu /boot/grub/menu list file using the proper UUID of the new partition, and the proper file names. Use the first Kubuntu menu items as a model. That should work to boot your new Kubuntu.

---

### Post by ryankask on 2009-07-06
K great. Thanks.

---

### Post by ryankask on 2009-07-06
Thanks dstew. I am typing this from the fresh OS and you can really feel the speed difference with Linux installed first.

---

### Post by hix3r on 2009-07-07
Hello guys!

I need a little help here.
Now I made a 60 GB partition on my 200 GB drive for XP(installed that first) and combined the other hard drive (160GB) and the remaining space in LVM, to a big 280 GB partition. Made boot,  made the other for encryption, divided up to root, home, swap. Now it is working however GRUB does not show XP. So I searched around, and made this. This is how my partitions look:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94673aad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25       19929   159886912+   5  Extended
/dev/sda5              25       19929   159886881   8e  Linux LVM

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb7bdb7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sdb2            7834       24792   136223167+   5  Extended
/dev/sdb5            7834       24792   136223136   8e  Linux LVM

And this is how the end of my GRUB menu.lst looks like:

# (2) Windows XP
title        Microsoft Windows XP Professional x64
rootnoverify    (hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader    +1

Now XP shows up in GRUB, but if I select it, it just give me an error message like:
"NTLDR missing Press Ctrl+Alt+Del to restart"
SO obviously ubuntu modified something in the boot area so XP does not find the partiton to boot from. How can I fix this? Do you have any idea?

---

