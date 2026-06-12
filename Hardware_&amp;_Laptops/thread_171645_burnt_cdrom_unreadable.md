---
title: "burnt cdrom unreadable"
date: 2006-05-07
forum: Hardware &amp; Laptops
---

### Post by russelld on 2006-05-07
Hi All

After burning a CD-R/RW, the freshly burnt CD is not readable when mounted, whereas a CD-R/RW burnt last week/month will read.

mounting CDROM from console:
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

the message in /var/log/messages:
attempt to access beyond end of device
hdc: rw=0, want=68, limit=4
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

and fstab is:
# <file system> <mount point>  <type>   <options>  <dump>  <pass>
 proc                /proc              proc       defaults    0             0
 /dev/hda2        /                    ext3       defaults,errors=remount-ro  0  1
 /dev/hda5        none               swap      sw          0             0
 /dev/hda6        /home             ext3       rw,users,exec,auto   0             1 
/dev/hda7         /mnt/hda7        ext3       rw,users,exec,auto   0             0 
/dev/hdc           /media/cdrom0  iso9660   ro,user,noauto    0             0 
/dev/sda1          /mnt/camera0   vfat       rw,noauto,user    0              0

I've tried different kernels, 2.6.12 and 2.6.15 which the burner used to work in.  And this happens using k3b, nero, gnomebaker, graveman and command line.

It this a permission issue?
What could be looked at to fix this?

TIA

---

### Post by Sef on 2006-05-07
It seems like there is a problem with the CD-RW.  Can the CD-RW read the CD if you reboot the computer after burning the it?

---

### Post by russelld on 2006-05-07
The CD is still unreadable after rebooting......

---

