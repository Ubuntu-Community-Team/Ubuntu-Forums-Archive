---
title: "BenQ BL DW1640"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by Corvus on 2005-07-06
Recently i have bought this dvd writer. I added the needed line to fstab and the system mounts it correctly, but i can't read anything. I know the unit is fine because i tried the unit in a firends computer (he has windows). What can i do ?

this is my fstab line:

/dev/hdd        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0

Maybe cdrom0 isn't the better name for it, anyway i think that i don't have to worry about the name.

Another interesting thing is that i tried hdparm with this result:

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

Can anyone tell me any indication about what i can see/read to try to solve this problem ?

Thank you,

---

### Post by bluetoad on 2005-09-22
I was wondering if anyone had a solution to this problem.  It fails to read during  installation and live CDs after the cd detection when reading libc.  I can boot up a Knoppix 3.7 live CD on both the 2.4 and 2.6.9 kernel versions.  The firmware version is quite old - BSHB.  

                                                                                             ...Peter

---

### Post by Corvus on 2005-09-23
I fixed it a month ago or so. I don't know about live cd's i haven't tried them. When i installed the normal distro i used the expert option and when passing options to hdparm i put dma = on and it worked.

Now i'm still missing the joypad, i don't know how to get it working  :|

---

### Post by bluetoad on 2005-09-27
Thanks  I got it working, as well.  I went into expert mode and unchecked the 
module  via82cxxx and the installation worked.  I've got an Intel motherboard.

---

