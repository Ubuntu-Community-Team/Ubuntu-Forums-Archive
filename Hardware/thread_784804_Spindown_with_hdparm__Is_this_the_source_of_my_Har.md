---
title: "Spindown with hdparm : Is this the source of my Hardy problems?"
date: 2008-05-06
forum: Hardware
---

### Post by acl123 on 2008-05-06
I think that all my Hardy problems (hangs requiring hard reset) may be due to having my hard drive spinning down. I was using hdparm to set the spin down time to 20 minutes, like this: **hdparm -S240 /dev/sda1**

Could this be causing troubles? Does hdparm even work in Hardy?

When I type **hdparm /dev/sda1** I get the following output:
> 
/dev/sda1:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 479283147, start = 63


That doesn't look too good.

I've disabled spindowns now, and haven't experienced any lock ups so far... although I can't be sure because they have been occurring so randomly.

When my computer was locking up, I would hit Control-Alt-Backspace. I would drop back to the command prompt and then if I sat and waited I would see a variety of error messages. Things like this (not necessarily in this order):
> 
[124.058330] ata 2.00: revalidation failed (errno=-5)
.
.
.
EXT3=fs error (device sda1):ext3_get_inode_loc: unable to read inode block - inode=8618454, block = 17235984
.
.
.
[224.871822] Buffer I/O Error on device sda1, logical block 46953927
.
.
.
ata 2.00:Status {DRDY}
ata 2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen


What do you think?
If spinning down the drive is the source of my problems, how can I go back to having it spin down?

---

### Post by sdennie on 2008-05-06
I don't think the spindown is causing the problems.  Unless you've explicitly done some things to set the ext3 journal commit interval and vm dirty writeback, it's not likely your disk was ever idle for 20 minutes and so probably never spun down.

I could be wrong though.

---

### Post by acl123 on 2008-05-06
Yeah, you're right - the computer just hung again.

---

