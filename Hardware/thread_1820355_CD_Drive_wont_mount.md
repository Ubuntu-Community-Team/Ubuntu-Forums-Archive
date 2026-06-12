---
title: "CD Drive wont mount"
date: 2011-08-07
forum: Hardware
---

### Post by amnite on 2011-08-07
My cd drive isnt mounting automatically and wont let me mount it manually on certain cds... Some cds work and mount others dont.... sudo mount /dev/cdrom, /mnt/cdrom, /dev/scd0 all get mount point doesnt exist errors, but the scd0 it takes awhile and the drive runs before the error pops up. And I know the cds aint bad i can burns iso from the via command line or k3b, but I cant get just linux to recognize...

---

### Post by amnite on 2011-08-08
****BUMP**** Would kinda like to use my cd drive as of 3 days ago lol

---

### Post by kblumy on 2011-08-08
I'm having a similar problem with my CD/DVD drive. It was working perfectly fine for ages until recently, when I began getting this error:
 "Unable to mount the selected volume. The Volume is probably in a format that cannot be mounted."
I attempted to mount the drive, and got no error from the terminal, but when I tried to open a DVD on my computer, the error reappeared.
If you have any suggestions, I'd really love to know.

also, when I try to mount I get this error:
 "wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
I'm fairly new to the linux os, so I'm nearly clueless as to what that even means, let alone try to solve the problem.

---

### Post by amnite on 2011-08-08
Additional Info...
 When I type mount this is output.
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda3 on /media/Acer type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/SYSTEM RESERVED type fuseblk (rw,nosuid,nodev,allow_other,blksize=512)

Nothing related to cd in there...(there is a disk in the drive)

Then I type dmesg | tail and recieve...
[ 3170.096018] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 04 3d e2 00 00 02 00
[ 3170.096027] end_request: I/O error, dev sr0, sector 1111944
[ 3170.096031] Buffer I/O error on device sr0, logical block 138993
[ 3177.020932] sr 1:0:0:0: [sr0] Unhandled sense code
[ 3177.020936] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3177.020940] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 3177.020944] sr 1:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 3177.020951] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 04 3d e2 00 00 02 00
[ 3177.020959] end_request: I/O error, dev sr0, sector 1111944
[ 3177.020964] Buffer I/O error on device sr0, logical block 138993

---

### Post by amnite on 2011-08-09
I ask a question about a game and boom! Not even 24 hours later I have an answer... I ask a question about how to make my drives work(a crucial part of computing) and nuthin... wtf?

---

### Post by rvguest on 2011-08-11
I found your question because I have the same problem.  If I find an answer, I'll try to find my way back.

---

### Post by amnite on 2011-08-12
Ditto dude...

---

