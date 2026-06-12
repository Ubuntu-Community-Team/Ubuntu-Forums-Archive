---
title: "Setting Up GRUB to Boot from Ext. Drive"
date: 2008-09-27
forum: General Help
---

### Post by Locutus_of_Borg on 2008-09-27
On my internal hard drive I have GRUB installed and would like to set it up to boot up assorted Linux's that are installed on my external hard drive

In grub I have
```
title Slackware Linux
root (hd1,5)
kernel /boot/vmlinuz root=/dev/sdb6 ro
```

With this entry, the kernel will load, but then I get an error when sdb6 is not recognized and the root filesystem is unable to mount

Interestingly, ```
title Ubuntu Linux
root (hd1,4)
kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sdb5 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

```

Will boot Ubuntu just fine (the loading is a little different than when installed on the primary drive, but it still works)

When I get that error on Slackware, I am told to append the correct "root=" line to my kernel sequence, and it gives available options, however the partitions it says are possible are all on my internal drive

How can I get grub to point not only to the kernel location, but also the root file system's location?

Arch and Ubuntu are currently the only two out of six that will boot properly.  Arch complains about a root filesystem not being found, but manages to boot anyway (???), the other give kernel panic/sync error.

I have installed grub also onto the external drive, and tried to boot directly from th external by changing BIOS settings, but I still get the same error of unable to find a root filesystem with those entries.

So obviously the problem is with designating root=/dev/sdb# although I have the same rate of failure when I use root=UUID=#### syntax.

I know the installation works as I can chroot into it and even start an X session in Slackware from my normal internal Gentoo system, but just cannot boot into it.

Any help would be appreciated.

Thanks.

---

### Post by Locutus_of_Borg on 2008-09-27
Anyone here that has Linux installed on a second hard drive care to share their grub.conf?

---

### Post by confused57 on 2008-09-27
You might try /dev/hdb6 instead of sdb6:
```
title Slackware Linux
root (hd1,5)
kernel /boot/vmlinuz root=/dev/hdb6 ro
```

or possibly /dev/hda6

---

### Post by louieb on 2008-09-27
I guess the Linux installs on the external have there own copy of grub too. well maybe not slack since it uses lilo.
but suppose I had  a linux test install on my on my second drive and my PC boots to a Linux install on the 1st drive. I could use the configfile option to load the test linux menu.lst

```
title load another menu.lst
configfile (hd1,0)/boot/grub/menu.lst 
```or if I install the grub pointer in the boot sector of the test linux partition I could chainload its copy of grub. (this will work if your using LILO too.)

```
title        Linux on (hd1,0) chainload
   root (hd1,0)
   chainloader    +1
```more here just seach for chainload or config file. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Locutus_of_Borg on 2008-09-28
I have determined the problem is that the kernel is trying to mount the root file system before it loads the needed modules to recognize the usb drive.  I am trying to create an initrd to load the necessary modules first, but am still having a problem.

I can now boot into the initramfs, but when trying to mount the actual root file system I get an error saying /dev/sdb6 does not exist, yet an fdisk -l from that terminal, will show that it is there.  If I try to mount it myself with "mount -t ext3 /dev/sdb6 /mnt/" I am told that gfs2 is missing as well as /dev/sdb6 cannot be found.  I can at this point mount my internal partitions with no problem though.

I do not really know what the problem is, but I imagine I am missing some kernel modules in my initrd.  Right now I am loading usc-storage.ko ehci-hcd.ko uhci-hcd.ko ext3.ko and gfs2.ko then pausing for ten seconds before trying to mount /dev/sdb6

I have no usbcore.ko module available, and do not know of any other modules I might need to get mounting of the external drive's partitions to work.

---

