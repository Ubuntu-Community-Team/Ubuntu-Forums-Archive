---
title: "Inconsistent CD automount mount point."
date: 2011-04-29
forum: Hardware
---

### Post by RS14 on 2011-04-29
Using Ubuntu 11.04.

The mount point of automounted CDs is inconsistent.

For instance, the Diablo II install disk is mounted at /media/INSTALL/ while the play disk is at /media/PLAYDISK/. I just want them to always be mounted on /cdrom/.

The device is /dev/sr0. This does not appear in /etc/fstab. Should it?

Output of 'mount -l | grep sr0': 

/dev/sr0 on /media/INSTALL type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500) [INSTALL]

Any advice is appreciated.

---

### Post by gen-X^2 on 2011-06-21
I spent a week in these forums, and only found a way to HARD SET mount point for my NEC ND-3550A DVD-RW in /media
Any other base directory breaks automounting.

You can set /dev/??? to mount to /media/cdrom and it will automount to /media/cdrom instead of /media/{VOLUME_NAME}

Play around with the options if you want different ones, but the key to fixing Wine and VirtualBox is setting mount point INSIDE the /media folder.

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=48122c53-b77c-4975-8d41-5aa3bf6ec054 /               ext4    errors=remoun$
# swap was on /dev/sda6 during installation
#UUID=2ae727f1-9557-4b3b-8f45-84b806c72ccd none            swap    sw          $
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sr0        /media/cdrom    auto    noauto,defaults,users,exec      0 0


Gen-X^2 : Idiocy Squared.

---

### Post by lefox on 2011-11-12
Thanks RS14! That solved my wine / DVDfab cdrom autodetection issue. I was struggling to get DVDFab to auto detect new DVDs into the drive since my installation of Oneiric. This solved it for me.

---

