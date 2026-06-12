---
title: "Tosh M200 tablet. PCMCIA CDRW/DVD not happy. HELP!"
date: 2008-05-31
forum: Hardware
---

### Post by *_Paul Bryant_* on 2008-05-31
Ok, I am stunned at how good Ubuntu Heron runs on this tablet. I installed it via a DVD/CDROM drive on the docking station because the PCMCIA CDROM refused to work. Apart from a few small issues it has proceeded amazingly well.If possible I would like to get the PCMCIA CDROM/DVD drive working. This is where I am now.

The PCMCIA driver is working correctly because I slotted in a memory stick adapter and the OS mounted the 256K stick with no problems.

The Targus Noteworthy PCMCIA CDRW/DVD drive mounts correctly on my Winblows machine.

here are the entries in my fstab file;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=091c1750-de83-456b-a051-807ef4a2b959 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d9009674-13f2-4f28-88ad-cea6b0494a62 none            swap    sw              0       0
/dev/cdrom  	  /media/cdrom0   auto    ro,user,noauto,exec 0       0
/dev/floppy       /media/floppy0  auto    rw,user,noauto,exec 0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/scd0       /media/floppy0  auto    rw,user,noauto,exec 0       0

The last two lines are the original fstab lines, and the cdrom and floppy entries are my two edited version.

the following is is the mtab file

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sdc1 /media/USB\040Disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

and I'm now at a standstill.Needless to say I'm a noob and I know that I'm trying to use a machine notorious for being a PIA but apart from this issue, the enhanced display bug and the reeorienting stylus problems this is a rockin little machine. What's especially sweet is that my wife works for a certain large operating system company here in Redmond and this little machine irritates her no end so I really want to get this baby tight!

---

