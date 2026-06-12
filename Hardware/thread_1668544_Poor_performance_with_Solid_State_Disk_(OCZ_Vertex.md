---
title: "Poor performance with Solid State Disk (OCZ Vertex 2)"
date: 2011-01-16
forum: Hardware
---

### Post by ronzo on 2011-01-16
I am using an OCZ Vertex 2 (60G) with Ubuntu Maverick.

What I am wondering about is the fact, that the SSD should reach read rates of around 250 MB/s.

hdparm reports:
/dev/sda:
 Timing cached reads:   12990 MB in  1.99 seconds = 6525.03 MB/sec
 Timing buffered disk reads:  410 MB in  3.00 seconds = 136.63 MB/sec

136 MB/s seems to be a bit slow.

What am I doing wrong?

I am using the noop scheduler.

Here's my fstab:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c6a194f2-85a4-42ee-8611-d2771777f063 /               ext4    discard,noatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=5d57a461-110a-4f3c-85ea-5fd79c54687b none            swap    sw              0       0
tmpfs		/tmp		tmpfs	defaults,noatime,mode=1777	0	0
tmpfs		/var/log	tmpfs	defaults,noatime,mode=0775	0	0
tmpfs		/var/tmp	tmpfs	defaults,noatime,mode=1777	0	0

Thanks in advance for your input!

---

### Post by gordintoronto on 2011-01-16
How fast is your CPU? How big was the file?

There's usually a world of difference between rated speeds and real world speeds.

---

### Post by psusi on 2011-01-16
I have a 60 gb first gen vertex and get 166 MB/s.  My guess is that you only have a 1.5 Gbps sata port.  Take a look in your dmesg.

---

### Post by ronzo on 2011-01-17
Thanks for the hint. You were right. It's my SATA port that limits the speed... 

Who wants to buy my 'old' Thinkpad T61p? ;-)

dmesg says:
ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)

---

### Post by ronzo on 2011-05-18
Interestingly, the T61p is capable of 3Gbps SATA but Lenovo does not support it. Searching around on the internet led me to a page with a modified BIOS for the T61p which enables the SATA-3 support.

---

