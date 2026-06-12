---
title: "External Hard Drive Won't Mount: $MFTMirr does not match (record 0)."
date: 2009-10-05
forum: Hardware
---

### Post by Steve00 on 2009-10-05
I am now unable to mount my external USB hard drive in Ubuntu 8.10. When I try I get a "$MFTMirr does not match (record 0)." error. I can access the drive from windows XP. I also did the double windows boot, running chkdsk /f which did not solve the problem.

I did search on the error and do not understand the suggested fixes. 

Running sudo blkid

results in:

/dev/sda1: UUID="9644A86344A847B7" TYPE="ntfs" 
/dev/sda5: UUID="5c434659-3c42-45ba-853a-4b8a7ad802fe" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="b9e3da8b-a682-4314-82ee-4f658eda8ae0" 
/dev/sda7: UUID="ce379d48-34bf-45ef-a603-61108a5ae20c" TYPE="ext3" 
/dev/sdb1: UUID="FA74C0B974C07A41" LABEL="FreeAgent Drive" TYPE="ntfs" 
/dev/sdb2: LABEL="Ubuntu 9.04 i386" TYPE="iso9660" 
/dev/loop1: UUID="d3440751-b8c1-4af9-8d9a-0e447ac8ac55" TYPE="ext3" 

and my /etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5c434659-3c42-45ba-853a-4b8a7ad802fe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=ce379d48-34bf-45ef-a603-61108a5ae20c /home           ext3    relatime        0       2
# /dev/sda6
UUID=b9e3da8b-a682-4314-82ee-4f658eda8ae0 none            swap    sw              0       0

Don't have a clue where to go from here.

Any suggestions will be greatly appreciated.

Thanks.

--Steve

---

### Post by Steve00 on 2009-10-07
Kept digging and finally found:

[http://blog.herrmann.pro.br/mftmirr_does_not_match_mft/]("http://blog.herrmann.pro.br/mftmirr_does_not_match_mft/")

and it worked as advertised and I've got my external drive back up and running.

---

