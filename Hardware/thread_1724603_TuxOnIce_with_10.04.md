---
title: "TuxOnIce with 10.04"
date: 2011-04-08
forum: Hardware
---

### Post by seierson on 2011-04-08
Hi Gang,

I would sure appreciate some help installing TuxOnIce correctly in 10.04.  One of the messages I get is the interface is not supported by your kernel.  Does that mean I absolutely cannot get that nice GUI progress bar while starting hibernation and also while resuming from hibernation? 

via ./install.sh, I installed: hibernate-script-2.0.tar.gz

I haven't the foggiest how to install or even if it's necessary: tuxonice-3.2-rc2-for-lucid.patch

Where do you place tuxonice.conf?  

How do you get tuxonice.conf to use a swapfile vs. partition?  

What commands do you add to grub.cfg, if any?   

/etc/initramfs-tools/conf.d:
```
RESUME=/mnt/2048.swap
```

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda3 :
UUID=c87c1395-61fe-400b-8ec9-1c6e8a41f041	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=50F6E763F6E74834	/windows	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda5 :
/mnt/2048.swap  none  swap  sw  0 0
```

As far as I know my swapfile is installed properly:
```

#swapon -s
Filename				Type		Size	Used	Priority
/mnt/2048.swap                          file		2097144	0	-1
```

Thanks for any and all help,
Christian Blackburn

---

