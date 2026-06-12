---
title: "CD rom does not work in Kubuntu Jaunty"
date: 2009-07-06
forum: Hardware
---

### Post by erkokite on 2009-07-06
I am using Kubuntu 9.04.  I have a Liteon DVDRW drive that is no longer detected by the OS.  The BIOS picks it up fine.  I apologize if this post is long but I want to post everything that I can think of that people will ask me to post.:)  I have posted below the results of sudo mount:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /home type ext3 (rw)
none on /proc/bus/usb type usbfs (rw,devgid=119,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

The contents of my /etc/fstab are as follows:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=af342637-851f-42ec-ae67-18825c5cb9b3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=7bf4e859-89de-4742-bbf4-d8e7e196f38c /home           ext3    defaults        0       2
# /dev/hda3
UUID=cdac7399-84e4-4ec2-9095-c438abdc8ce8 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

#usbfs
none /proc/bus/usb usbfs devgid=119,devmode=664 0 0

Interestingly enough, my hard drive partitions all show up in mount as sda, even though I have an IDE drive, and they should be hda.  I have no /dev/cdrom, but I have a number of other interesting devices.  I have posted the listing of files in my /dev/ directory below:

adsp             loop6               ram6        tty14  tty44           usbdev2.1_ep81   
audio            loop7               ram7        tty15  tty45           usbdev2.2_ep00   
block            lp0                 ram8        tty16  tty46           usbdev2.2_ep81   
bus              MAKEDEV             ram9        tty17  tty47           usbdev3.1_ep00   
cdrom2           mapper              random      tty18  tty48           usbdev3.1_ep81   
cdrw2            mem                 rfcomm0     tty19  tty49           usbmon0          
char             mixer               rfcomm1     tty2   tty5            usbmon1          
console          net                 rtc         tty20  tty50           usbmon2          
core             network_latency     rtc0        tty21  tty51           usbmon3          
cpu_dma_latency  network_throughput  scd0        tty22  tty52           vboxdrv          
disk             null                sda         tty23  tty53           vcs              
dri              nvidia0             sda1        tty24  tty54           vcs1             
dsp              nvidiactl           sda2        tty25  tty55           vcs2             
dvd2             oldmem              sda3        tty26  tty56           vcs3             
dvdrw2           parport0            sequencer   tty27  tty57           vcs4             
ecryptfs         pktcdvd             sequencer2  tty28  tty58           vcs5             
fd               port                sg0         tty29  tty59           vcs6
fd0              ppp                 sg1         tty3   tty6            vcs7
full             psaux               shm         tty30  tty60           vcs8
fuse             ptmx                snapshot    tty31  tty61           vcsa
hidraw0          pts                 snd         tty32  tty62           vcsa1
hpet             ram0                sndstat     tty33  tty63           vcsa2
initctl          ram1                sr0         tty34  tty7            vcsa3
input            ram10               stderr      tty35  tty8            vcsa4
kmem             ram11               stdin       tty36  tty9            vcsa5
kmsg             ram12               stdout      tty37  ttyS0           vcsa6
log              ram13               tty         tty38  ttyS1           vcsa7
loop0            ram14               tty0        tty39  ttyS2           vcsa8
loop1            ram15               tty1        tty4   ttyS3           xconsole
loop2            ram2                tty10       tty40  urandom         zero
loop3            ram3                tty11       tty41  usbdev1.1_ep00
loop4            ram4                tty12       tty42  usbdev1.1_ep81
loop5            ram5                tty13       tty43  usbdev2.1_ep00


Nothing shows in in my /media/cdrom folder.  I have tried the following commands:

sudo mount -t iso9660 /dev/scd0 /media/cdrom
sudo mount -t iso9660 /dev/cdrom2 /media/cdrom

and both times I get the following error:
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I currently have an audio cd in the drive.  Anyone have any ideas?

Many thanks.

---

