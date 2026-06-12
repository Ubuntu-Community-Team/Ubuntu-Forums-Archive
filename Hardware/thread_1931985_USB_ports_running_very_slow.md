---
title: "USB ports running very slow"
date: 2012-02-26
forum: Hardware
---

### Post by williepabon on 2012-02-26
I run Ubuntu 10.04 from an external drive (USB connected). A few days ago after doing some maintenance on my pc, apparently, I connected my hard drive to a different USB port. Now my boot process is extremely slow. When I go to the disks utility, it says that the connection is running at 12 MB/sec instead of 480 MB/sec. All disk activity now takes longer. Is this a bug on the OS? Changing to a different USB port shouldn't change the performance of disk activity. If it is, are there workarounds? Including information about my machine:

williepabon@WP-WrkStation:~$ uname -a
Linux WP-WrkStation 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux

williepabon@WP-WrkStation:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid


williepabon@WP-WrkStation:~$ sudo hdparm -tT /dev/sdc
[sudo] password for williepabon: 

/dev/sdc:
 Timing cached reads:    84 MB in  2.00 seconds =  41.96 MB/sec
 Timing buffered disk reads:    4 MB in  3.81 seconds =   1.05 MB/sec

This is a very slow transfer rate from a hard drive.

---

### Post by ahallubuntu on 2012-02-26
First of all, no USB 2 hard drive can go 480 MBytes per second.  The theoretical maximum speed for USB 2 is 480 MBITS per second - with 8 bits per bytes, your maximum theoretical transfer rate is 60 MBytes per second.  And you rarely get the exact theoretical maximum speed in practice - best you can hope for if that you get close.  I'm pretty sure the quoted 12MBytes rate from Ubuntu really IS BYTES not BITS, though - too slow but not nearly as far off from optimal speed as you probably think.

I like to debug these things by trial and error: change one thing and see what's different.  You said before that this happened just when you added RAM.  I'm not sure why that would cause your problem.  In any case, here's what I'd try:

- boot Ubuntu 10.10 from the flash drive, and try the hdparm there.  If you get the same result, then it seems unlikely your Ubuntu 10.04 install is messed up.
- try your hard drive on another computer - boot your Ubuntu 10.10 flash stick there.  If you get the same results, then you've ruled out your old's hardware computer (probably) as the problem.

At that point, I'd point to the hard drive itself.  You could try GSmartControl as I suggested on the other thread.  You can query S.M.A.R.T. on many external drives - the trick is finding the controller so you can tell SmartMonTools to add an option for that control so it can pick up S.M.A.R.T. from that drive.  I have done this for several external drives myself.

Did you try the Parted Magic tool (on the Ultimate Boot CD)?  You can use it to do GSmartControl instead of using Ubuntu.  I forget how you ran it before.  You may have to install a newer version of SmartMonTools that supports external drives better - I think I had to do that.  In Ubuntu 10.04 or 10.10, you'd probably have to build the latest version of SmartMonTools yourself (using a "make" in a terminal) but it's not really all that hard.

---

### Post by williepabon on 2012-02-26
> **ahallubuntu said:**
> First of all, no USB 2 hard drive can go 480 MBytes per second.  The theoretical maximum speed for USB 2 is 480 MBITS per second - with 8 bits per bytes, your maximum theoretical transfer rate is 60 MBytes per second.  And you rarely get the exact theoretical maximum speed in practice - best you can hope for if that you get close.  I'm pretty sure the quoted 12MBytes rate from Ubuntu really IS BYTES not BITS, though - too slow but not nearly as far off from optimal speed as you probably think.

I like to debug these things by trial and error: change one thing and see what's different.  You said before that this happened just when you added RAM.  I'm not sure why that would cause your problem.  In any case, here's what I'd try:

- boot Ubuntu 10.10 from the flash drive, and try the hdparm there.  If you get the same result, then it seems unlikely your Ubuntu 10.04 install is messed up.
- try your hard drive on another computer - boot your Ubuntu 10.10 flash stick there.  If you get the same results, then you've ruled out your old's hardware computer (probably) as the problem.

At that point, I'd point to the hard drive itself.  You could try GSmartControl as I suggested on the other thread.  You can query S.M.A.R.T. on many external drives - the trick is finding the controller so you can tell SmartMonTools to add an option for that control so it can pick up S.M.A.R.T. from that drive.  I have done this for several external drives myself.

Did you try the Parted Magic tool (on the Ultimate Boot CD)?  You can use it to do GSmartControl instead of using Ubuntu.  I forget how you ran it before.  You may have to install a newer version of SmartMonTools that supports external drives better - I think I had to do that.  In Ubuntu 10.04 or 10.10, you'd probably have to build the latest version of SmartMonTools yourself (using a "make" in a terminal) but it's not really all that hard.


First of all, I really appreciate your help in trying to solve this problem. The tools that you mention in the thread (Ultimate Boot CD) I'm not familiar with. I'm also not familiar with SmartMonTools (sorry, I'm user, with a long way to get some technical expertise with Ubuntu). When I boot from a flash drive that has Ubuntu 10.10, these are the results of hdparm:

For the external hard drive:

williepabon@Precision-WorkStation-670:~$ sudo hdparm -tT /dev/sdd
[sudo] password for williepabon: 

/dev/sdd:
 Timing cached reads:   1758 MB in  2.00 seconds = 879.50 MB/sec
 Timing buffered disk reads:   94 MB in  3.03 seconds =  31.00 MB/sec

For the flash drive that I booted from:

williepabon@Precision-WorkStation-670:~$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   1726 MB in  2.00 seconds = 862.85 MB/sec
 Timing buffered disk reads:   84 MB in  3.05 seconds =  27.58 MB/sec

On both cases the disk utility says that the connection is USB at  480 MB/s. I know that this is the theoretical maximum. But, the results above may seem to indicate that the problem is the 10.04 OS. I'm not interested at this time to upgrade to 10.10 (as somebody suggested) because 10.04 is the LTS version and all my critical files and data are done on that version. So, I want to fix the problem. Please, advise what other steps or tests I should make. Thanks again.
wp

---

