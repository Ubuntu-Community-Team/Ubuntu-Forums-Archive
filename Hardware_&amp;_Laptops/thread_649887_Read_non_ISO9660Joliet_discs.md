---
title: "Read non ISO9660/Joliet discs?"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by canny_h on 2007-12-25
I recently switched over from windows to ubuntu...
I performed a clean install, after backing up all my data to DVDs. But now i can't mount any of my backup DVDs.  I burnt them with the **_ISO9660/Joliet format with relaxed restrictions,(longer file-names and path depths)_** under Nero and I could easily read them under windows.
When I try to mount them under ubuntu, i get the following message box:

" Invalid mount option when attempting to mount the volume"

[FONT="Courier New"]root@TRNSLTR-U:/# mount -o ro /dev/hda /media/cdrom0
mount: you must specify the filesystem type[/FONT]

the fstab file is as follows: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c345684-7ca8-42c3-b0e7-1e57f77d046d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fb270ae5-c463-4194-bb43-bef7d20953ec none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I've also tried installing Nero for Linux, it's also got the same options to relax restrictions , but I still can't figure out how to read the disks :confused:

Any help will be highly appreciated. I shall be very grateful .

Canny_h

---

### Post by canny_h on 2007-12-26
1.Contrary to general perception, device hda DOES exist:
[COLOR="Blue"][FONT="Courier New"]root@TRNSLTR-U:/# ls /dev/hd*
/dev/hda[/FONT][/COLOR]
My harddisk , being SATA is reported as /dev/sda

2.Specifying filesystem doesn't help:

[COLOR="#0000ff"][FONT="Courier New"]root@TRNSLTR-U:/#  mount -t udf -o ro  /dev/hda /media/cdrom0
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@TRNSLTR-U:/# dmesg | tail
[15804.376000] attempt to access beyond end of device
[15804.376000] hda: rw=0, want=68, limit=4
[15804.376000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[15944.396000] attempt to access beyond end of device
[15944.396000] hda: rw=0, want=68, limit=4
[15944.404000] attempt to access beyond end of device
[15944.404000] hda: rw=0, want=1252, limit=4
[15944.404000] attempt to access beyond end of device
[15944.404000] hda: rw=0, want=1028, limit=4
[15944.404000] UDF-fs: No partition found (1)
root@TRNSLTR-U:/#[/FONT][/COLOR]
or even:
[COLOR="Blue"][FONT="Courier New"]root@TRNSLTR-U:/#  mount -t iso9660 -o ro  /dev/hda /media/cdrom0
mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@TRNSLTR-U:/# dmesg | tail
[15553.084000] attempt to access beyond end of device
[15553.084000] hda: rw=0, want=68, limit=4
[15553.088000] attempt to access beyond end of device
[15553.088000] hda: rw=0, want=1252, limit=4
[15553.088000] attempt to access beyond end of device
[15553.088000] hda: rw=0, want=1028, limit=4
[15553.088000] UDF-fs: No partition found (1)
[15804.376000] attempt to access beyond end of device
[15804.376000] hda: rw=0, want=68, limit=4
[15804.376000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
root@TRNSLTR-U:/#[/FONT][/COLOR]

3.The DVDs are still working on windows, but I have only ubuntu gutsy gibbon 7.10 installed on my pc

Any, (I  mean ANY) help in this regard will be highly appreciated, I'd  be really thankful. :)

---

