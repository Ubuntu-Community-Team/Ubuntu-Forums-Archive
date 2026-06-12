---
title: "Error 17 boot problem and BG rescue linux."
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by hantsmike on 2009-03-14
Hello 

I'm a Windows refugee to Mint – a version of Ubuntu. I have dual boot machine which was running perfectly but  had aquired an unwanted partition which I tried to delete using partition editor. This went wrong and when I now turn on the computer to run GRUB all I get is Error 17 and the boot process stops prior to running GRUB. I can get into the bios and I've changed  to load from  CD but it will not work I've tried various Linux (mint and ubuntu)  and windows rescue and boot CD / DVD disks ( I have another working computer)  and the only thing that works is BG-Rescue Linux.    ([http://www.giannone.eu/rescue/current/](http://www.giannone.eu/rescue/current/) )  which loads from two floppys (after I told the BIOS to run from floppy) . BGR then boots from RAM   and takes me to the command line 

rescue:/#

The problem is that I have little idea of what to do next . I think I should try and get it to boot and then reinstall  from my Linux Mint DVD but do not know what the correct command is . 

Can any-one guide me as to how I reload what ever it is I need to reload?.Unfortunately I do not have any command line experience. I would prefer to keep my windows partition (c drive) because it such a pain to reload and I need it for work related software. There is no data I need to preserve on the machine and obviously reloading linux is easy.   The rescue floppys that work contain also the following tools 

LINUX-Kernel**2.4.36.2 
with lzma support 
with inittar support 
with cloop*2.01 support 
with fuse*2.5.3 support 
with NTFS*2.1.6b support 
with DVDRW*Patch 
with SC92031 Ethernet Adapter Patch 
with the PocketBoy*Patch 

uClibc**0.9.29 
BusyBox**1.9.2 

with losetup-2.4 patch 
/++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++\
|[, [[, adjtimex,  ar,  ash,  awk,  basename,  bunzip2,  bzcat,  bzip2, cal, cat,| 
|chgrp, chmod, chown, chroot, chvt,  clear,  cmp,  cp, cpio, cttyhack, cut, date,|
|dd,  deallocvt,  devfsd,  df,  dirname,  dmesg,  dos2unix,  dpkg,  dpkg-deb, du,|
|dumpkmap, echo, egrep, env, expr,  false, fdflush, fdformat, fdisk, fgrep, find,|
|fold, free,  freeramdisk,  fsck.minix,  ftpget,  ftpput,  getopt,  grep, gunzip,| 
|gzip, halt, hd, hdparm,  head,  hexdump,  hostname, hwclock, id, ifconfig, init,|
|insmod, install, kbd_mode,  kill,  killall,  klogd,  length, less, ln, loadfont,| 
|loadkmap, logger, logname, losetup, ls,  lsmod, lzmacat, makedevs, md5sum, mesg,| 
|mkdir, mkfifo, mkfs.minix,  mknod,  mkswap,  mktemp,  modprobe, more, mount, mv,| 
|nameif,  nc,  netstat,  nslookup,   od,   openvt,  pidof,  ping,  pipe_progress,| 
|pivot_root,  poweroff,  printf,  ps,  pwd,  rdate,  readlink,  realpath, reboot,| 
|renice, reset, rm, rmdir,  rmmod,  route,  rpm,  rpm2cpio, sed, setkeycodes, sh,| 
|sha1sum, sleep, sort, split,  stty,  swapoff, swapon, switch_root, sync, sysctl,| 
|syslogd, tail, tar, tee, telnet,  test,  tftp, time, top, touch, tr, traceroute,| 
|true, tty, udhcpc,  umount,  uname,  uncompress,  uniq, unix2dos, unlzma, unzip,| 
|uptime, usleep, uudecode, uuencode, vconfig,  vi, watch, wc, wget, which, xargs,| 
|yes, zcat                                                                       |
\********************************************************************************/
                

Filesystem-Tools: 
cramfs**1.1 
dosfstools**2.11 
e2fsprogs**1.40.7 
ntfsprogs**2.0.0 
ntfs-3g**1.2310 
progsreiserfs**0.3.0.5 
reiserfsck**3.6.20 
umsdos-utils**1.32 

Disk-Tools: 
cloop**2.05 
dd_rescue**1.14 
gpart**0.1h* * (with support for ReiserFS 3.6) 
lilo**22.8 
mdadm**2.6.4 
ms-sys**2.1.3 
syslinux**3.60 
tphdisk 
fdisk and hdparm are integrated in BusyBox 

Compression-Utilities: 
cabextract**0.6 
rzip**2.1 
zip**2.32 
ar, bzip2, cpio, dpkg, dpkg-deb, gzip, rpm, rpm2cpio, tar, uncompress, unlzma and unzip are integrated in BusyBox 

cmdftp**0.7.6 
linld**0.97 
loadlin**1.6c 
pcmcia-cardmgr**3.2.8 
regutils**0.10 
smbclient**1.9.18p8* * (with pipe support) 


Supported Filesystems: cramfs, devfs, ext2, ext3, iso9660, minix, msdos, ntfs 2.1.6b, ntfs-3g (rw), proc, ramfs, reiserfs, tmpfs, udf, umsdos, vfat, xfs
Network filesystem: nfs


Many thanks.

---

### Post by meierfra. on 2009-03-14
Did you try  SuperGrub: It comes on CD, USB and  Floppy

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

If  Supergrub does not work, I can show you how to use "dd" to fix grub. But I need some information:

1) What  is the device name of your Linux Mint partition. It's something like  "/dev/sda3"  To figure out the device name, type

```
fdisk -lu
```

at the  BG Rescue Linux  command line 


2)   How many hard drives to you have?  


3)  Are your bios set to boot from  the hard drive containing "Linux Mint"?

---

### Post by hantsmike on 2009-03-15
Hello Meierfra, 

Many thanks for your help .Busy couple of days but will try on tuesday and report back. I am stunned that you have spent your own time replying -- thanks again. 

Mike.

---

### Post by upchucky on 2009-03-15
perhpa a mod can sticky this somewhere?


[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/HOWTO_GRUB_BOOTLOADER_AND_TROUBLE_SHOOTER](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/HOWTO_GRUB_BOOTLOADER_AND_TROUBLE_SHOOTER)

---

### Post by MooseNSquirrel on 2009-03-16
I hope everyone doesn't mind me jumping here as well... Today I decided my windows crash was my last so I downloaded the latest build from ubuntu, created an image disk and ran the install. 

The first time I ran the install I accepted the defaults and Ubuntu was installed on my primary 160 gig IDE drive. Of course when I rebooted I booted into Vista which I had installed on the 250 gig (SATA) drive. I re-ran the install and installed Ubuntu on my 250 gig SATA drive and when I rebooted I get a Grub error 17.

My bios see the drives as SATA, Primary Master and Slave IDE. In the bios I did change the TYPE to User on all drives and no fix. All are set to AUTO as well. Below is my sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device 

E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8afc8af 

    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312579759   156289848+  42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc8afc8b0 

    Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   312578820   156289379    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc874c874   

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   476262989   238131463+  83  Linux
/dev/sdc2       476262990   488392064     6064537+   5  Extended
/dev/sdc5       476263053   488392064     6064506   82  Linux swap / Solaris

grub> find /boot/grub/stage1  returns (hd2,0)

I have read alot of threads an I understand when needs to be done but since this is still day one with Linux I could use a lil help. I am not sure what commands to execute and how sdc1, sdc2 and sdc5 correspond to (hd?,?).

Kind Regards,
Moose

---

### Post by meierfra. on 2009-03-16
MooseNSquirrel: Please start you own thread. Trying to solve two problems in one thread leads to unnecessary confusions.

To get you started in the new thread:

In order to get a clearer picture of your setup, I suggest to boot from your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.


But post "RESULTS.txt" in the new thread. Not here

---

### Post by hantsmike on 2009-03-17
Hello Meierfra, 

Yep,  Supergrubdisk floppy version seems to have got me back on track --feel stupid for not trying the floppy version myself. 

So, many thanks, you're another reason why I'll continue with Linux /Ubuntu/ Mint and continue to recommend them to my familly and associates. 

Regards

Mike

---

### Post by meierfra. on 2009-03-17
> Supergrubdisk floppy version seems to have got me back on track

Great. Supergrub floppy did seem the be the canonical solution.(But secretly I was hoping that supergrub would fail: I know how to fix grub just using "dd", but I actually have never done it. So I was looking forward to putting my theoretical knowlegde to practical use :))

---

