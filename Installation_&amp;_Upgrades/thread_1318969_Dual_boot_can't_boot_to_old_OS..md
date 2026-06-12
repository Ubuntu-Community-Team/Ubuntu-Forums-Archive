---
title: "Dual boot can't boot to old OS."
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2009-11-08
Hi,

I just installed Karmic on my system as dual-boot.  The other OS is Jaunty.  This was intended to be a safe upgrade, rather than a true dual boot.

I got the install up, but the first issue for the upgrade came up when I can't just copy my .evolution directory over and have it work.  I need to boot into Jaunty, back up my email (among other things) and then boot back to Karmic to load the settings.

The problem is, I can't boot to the old setup.  I just want to be able to get to the boot menu, so I can select an alternate configuration.

I'm familiar with Lilo, not with grub.  I looked in menu.lst and it appears to be only the Jaunty stuff, there is no mention of my Karmic partition.  There seems to be two Grubs running, and I have no idea how to get my old setup to work.

I checked menu.lst and it seems to be wrong.  It shows Ubuntu 9.10 for /dev/md5, which should be Ubuntu 9.04.  I've confirmed this with the mount settings, and the partitions are loaded the way I expected.

I saw in the docs that I should be able to wait for Grub to start, then hit escape within 3 seconds.  This gets me to a root console prompt without logging in.  How do I get to an alternate dual boot configuration?

Every bit of documentation I find tells me Grub just takes care of itself, but it's not taking care of itself.

Thanks.

mount:
```

/dev/md3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/mapper/vg-shared_tmp on /tmp type ext2 (rw)
/dev/mapper/vg-shared_archives on /archives type xfs (rw)
/dev/md1 on /boot type ext2 (rw)
/dev/mapper/vg-shared_home on /home type ext3 (rw)
/dev/mapper/vg-shared_opt on /opt type ext3 (rw)
/dev/mapper/vg-shared_vmware on /vmware type xfs (rw)
/dev/md5 on /mnt/jaunty type ext3 (rw)
/dev/mapper/vg-ubuntu_usr on /mnt/jaunty/usr type ext3 (rw)
/dev/mapper/vg-ubuntu_var on /mnt/jaunty/var type ext2 (rw)
/dev/mapper/vg-ubuntu_vartmp on /mnt/jaunty/var/tmp type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ken/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ken)


```

menu.lst:
```

default         0
timeout         6
hiddenmenu
title           Chainload into GRUB 2
root            (hd0,0)
kernel          /grub/core.img

title           ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title           When you have verified GRUB 2 works, you can use this command to
root

title           complete the upgrade:  upgrade-from-grub-legacy
root

title           ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title           Ubuntu 9.10, kernel 2.6.31-14-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.31-14-generic root=/dev/md5 ro quiet splash
initrd          /initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.31-14-generic root=/dev/md5 ro single
initrd          /initrd.img-2.6.31-14-generic

title           Ubuntu 9.10, kernel 2.6.28-16-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.28-16-generic root=/dev/md5 ro quiet splash
initrd          /initrd.img-2.6.28-16-generic

title           Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.28-16-generic root=/dev/md5 ro single
initrd          /initrd.img-2.6.28-16-generic

title           Ubuntu 9.10, kernel 2.6.28-15-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.28-15-generic root=/dev/md5 ro quiet splash
initrd          /initrd.img-2.6.28-15-generic

title           Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.28-15-generic root=/dev/md5 ro single
initrd          /initrd.img-2.6.28-15-generic

title           Ubuntu 9.10, kernel 2.6.28-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.28-11-generic root=/dev/md5 ro quiet splash
initrd          /initrd.img-2.6.28-11-generic

title           Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.28-11-generic root=/dev/md5 ro single
initrd          /initrd.img-2.6.28-11-generic

title           Ubuntu 9.10, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin


```

---

### Post by 1clue on 2009-11-09
Bump.

---

### Post by skyiscrying on 2009-11-09
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  Hi - I was reading about Grub in a another post. It might help you, I hope.

---

### Post by atoztoa on 2009-11-11
Use LILO... this will say how...

[http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html](http://www.atoztoa.com/2009/11/booting-ubuntu-910-part-1-downfall.html)

---

### Post by 1clue on 2009-11-13
Irrelevant now.  I messed up my new install, couldn't boot to the old one and so I re-installed.

---

