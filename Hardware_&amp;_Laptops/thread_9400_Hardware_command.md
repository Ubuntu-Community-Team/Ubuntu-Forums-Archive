---
title: "Hardware command"
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by LongTooth on 2004-12-28
Some hardware are listed in a way that will not change. Such as your harddrive. It will always be /dev/hda. But some hardware listings are not constant. Such as when one adds a USB device. What is the proper command to give that will list your hardware? On a test box, I've added a USB CD-burner. By trial and error I found that the proper device name for it is /dev/sr0. While the internal CD is listed as /dev/CDrom. So, if I didn't know how a peice of equipment is listed, what is the command that will tell me?
Thanks.

---

### Post by diebels on 2004-12-28
ls -l /dev/

---

### Post by LongTooth on 2004-12-28
Hum? Here is the results of this command:

-----------------------------------------------------------------------------
longtooth@ubuntu:~ $ ls -l /dev/
total 0
crw-rw----    1 root     audio     14,  12 2004-12-28 14:25 adsp
crw-rw----    1 root     video     10, 175 2004-12-28 14:25 agpgart
crw-rw----    1 root     audio     14,   4 2004-12-28 14:25 audio
lrwxrwxrwx    1 root     root            3 2004-12-28 14:25 cdrom -> hdd
crw-rw----    1 root     root       5,   1 2004-12-28 14:25 console
lrwxrwxrwx    1 root     root           11 2004-12-28 14:25 core -> /proc/kcore
crw-rw----    1 root     audio     14,   3 2004-12-28 14:25 dsp
drwxr-xr-x    4 root     root          120 2004-12-28 14:25 evms
lrwxrwxrwx    1 root     root           13 2004-12-28 14:25 fd -> /proc/self/fd
brw-rw----    1 root     floppy     2,   0 2004-12-28 14:25 fd0
crw-rw-rw-    1 root     root       1,   7 2004-12-28 14:25 full
brw-rw----    1 root     disk       3,   0 2004-12-28 14:25 hda
brw-rw----    1 root     disk       3,   1 2004-12-28 14:25 hda1
brw-rw----    1 root     disk       3,   2 2004-12-28 14:25 hda2
brw-rw----    1 root     disk       3,   5 2004-12-28 14:25 hda5
brw-rw----    1 root     cdrom     22,   0 2004-12-28 14:25 hdc
brw-rw----    1 root     cdrom     22,  64 2004-12-28 14:25 hdd
prw-------    1 root     root            0 2004-12-28 14:25 initctl
drwxr-xr-x    2 root     root          160 2004-12-28 14:25 input
crw-r-----    1 root     kmem       1,   2 2004-12-28 14:25 kmem
crw-rw----    1 root     root       1,  11 2004-12-28 14:25 kmsg
srw-rw-rw-    1 root     root            0 2004-12-28 14:25 log
crw-rw----    1 root     lp         6,   0 2004-12-28 14:25 lp0
crw-------    1 root     root     109,   0 2004-12-28 14:25 lvm

-------------------------------------------------------------------------------

I've got a CDROm and a CD-R (burner). I see the floppy, HD and CDRom listed but not the Writer. Should I do something else to force it to be listed? 

Maybe I should start at the begining. A PC geek recommended I install both when building a machine. He gave me many reasons and they were all sound. So when I look into burning CDs from the CDRom to the CD-R or burning iso files to the writer how do I go about listing the writer? I still have to load the software. I understand there are problems with K3B on Ubuntu. That's an other problem to tackle. But I'll have to start with how my CD-R is listed. 

Thanks.

---

### Post by LongTooth on 2004-12-28
Did a /et/fstab and this is the results: 

--------------------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

-----------------------------------------------------------------------------

so if I was to install Xcdroast and it asked me for the hardwar information would I input /dev/hdc or /media/cdrom1? Or should I just jump into it and see if I luck out and it picks it up by it self? 

Thanks.

---

### Post by diebels on 2004-12-28
Well, usb is not 100% bugfree yet. Maybe loading sg will help.
"sudo modprobe sg"
Then ls -l /dev/ will show somhting like:
brw-rw----  1 root cdrom 11, 0 2004-12-28 22:51 /dev/scd0
crw-rw----  1 root cdrom 21, 0 2004-12-28 22:51 /dev/sg0
crw-rw----  1 root disk  21, 1 2004-12-28 22:51 /dev/sg1
lrwxrwxrwx  1 root root      4 2004-12-28 22:51 /dev/sr0 -> scd0

Most burning programs should be able to autoconfigure burning devices. If it works allright, you add sg to /etc/modules

---

### Post by LongTooth on 2004-12-29
Just to let this forum know I've solved my problem. I used the /etc/fstab command to see how my CDs are listed. See my post above. The information need was /dev/hdd for the reader and /dev/hdc for the writer/burner. 

Since I've never had any luck using K3B with Ubuntu without screwing up my install, I decided to give XCDRoast a shot. The reason for my post is because XCDRoast asked for a manual input of these devices. If the information is correct, XCDRoast will take it and your CD drive will be listed. I did that just that and both my reader and writer showed up. I have just now burned an iso file. So all is well. I feel like a complete man.

---

### Post by alex847831 on 2007-05-15
> **LongTooth said:**
> Some hardware are listed in a way that will not change. Such as your harddrive. It will always be /dev/hda. But some hardware listings are not constant. Such as when one adds a USB device. What is the proper command to give that will list your hardware? On a test box, I've added a USB CD-burner. By trial and error I found that the proper device name for it is /dev/sr0. While the internal CD is listed as /dev/CDrom. So, if I didn't know how a peice of equipment is listed, what is the command that will tell me?
Thanks.


[magnets demonstrate Equity Loans mapquest Equity Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

### Post by pigor7239 on 2007-05-15
> **LongTooth said:**
> Some hardware are listed in a way that will not change. Such as your harddrive. It will always be /dev/hda. But some hardware listings are not constant. Such as when one adds a USB device. What is the proper command to give that will list your hardware? On a test box, I've added a USB CD-burner. By trial and error I found that the proper device name for it is /dev/sr0. While the internal CD is listed as /dev/CDrom. So, if I didn't know how a peice of equipment is listed, what is the command that will tell me?
Thanks.


[Equity Line Credit Debt Consolidation food science insects Skin care](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

