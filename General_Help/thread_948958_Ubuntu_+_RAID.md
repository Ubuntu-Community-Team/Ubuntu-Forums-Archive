---
title: "Ubuntu + RAID"
date: 2008-10-15
forum: General Help
---

### Post by DrIdiot on 2008-10-15
I'm setting up an Ubuntu server and I'm having some issues regarding RAID setup.  I've got a few questions:

1) What is a RAID setup that you recommend?  The only requirement is mirroring.

2) With RAID-1 mirroring, when a hard drive fails, will Ubuntu notify you?  Is there some way to know when a hard drive fails?

3) The motherboard comes with its own RAID adapter (it's probably nothing special).  Should I use the motherboard's RAID controller or run software RAID?

4) Can I add additional hard drives to the a RAID-1 setup without losing data?  What about RAID 10 or RAID 01?

5) Should I invest in an actual RAID controller?

This is a relatively low-traffic server and usage is internal.  Right now I am looking at RAID 10.

Thanks,
-Harrison

---

### Post by penguinpi.com on 2008-10-16
> 1) What is a RAID setup that you recommend? The only requirement is mirroring.

RAID 1 will be perfect then.

> 2) With RAID-1 mirroring, when a hard drive fails, will Ubuntu notify you? Is there some way to know when a hard drive fails?

What kind of drives are they SCSI, SATA, IDE? If you do software raid the kernel probably will complain of a degraded cluster or something like that. Also there are various SNMP utilities that you could use.

> 3) The motherboard comes with its own RAID adapter (it's probably nothing special). Should I use the motherboard's RAID controller or run software RAID?

Thats your preference, if the hardware RAID controller offers you exactly what you want then that would be fine. I would recommend software RAID if you have fast drives and are running a relatively fast machine with a good amount of RAM. If your system resources are limited go with HW RAID. 

> 
4) Can I add additional hard drives to the a RAID-1 setup without losing data? What about RAID 10 or RAID 01?

It depends on your controller. If you are using software RAID there is a neat tool called mdadm (Multi-Disk-Admin or somethig) do a 

~# mdadm -help   or check the man pages. I almost positive you can add a drive with this utility.
  

> 
5) Should I invest in an actual RAID controller?
Probably Not.

---

### Post by atryus28 on 2008-10-16
I am having an issue with RAID on my Ubuntu 8.04 server.  I have it setup to use RAID 5 with 3 500g drives.  The problem is It is telling me that I only have 500gs of space instead of the terabyte it should be showing.  Is there any reason for that?  When I used another distro it showed up as having the full TB, problem was that the NIC was not supported so I am trying with Ubuntu.

Any ideas or comments would be great.

Thanks

---

### Post by DrIdiot on 2008-10-16
So uh, let's say I decided to do a software RAID 10.  Let's say for now I have 4 1-TB drives: A,B,C,D.  A,B I set up in RAID-1, C,D are set up in RAID-1.  Then I make a RAID-0 out of the two RAID-1 setups.  How would I add more space?  Would I be able to add say, 2 more drives to each of the RAID-1 setups?  Would I be able to add a new RAID-1 array (identical) to the RAID-0?  Could I do both?

Thanks

---

