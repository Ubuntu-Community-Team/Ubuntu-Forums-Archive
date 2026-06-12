---
title: "External Raid 5 Array Device Number Problems with 8.10"
date: 2009-03-17
forum: Hardware
---

### Post by mikey5555 on 2009-03-17
Hello all, 

I've been wrestling with a small problem concerning my 12 Disk External Raid5 Array.  Since I installed Ubuntu 8.10 Intrepid Ibex, I have a problem with the external drives keeping the same device numbers (ie.. /dev/sdd1 /dev/sde1 etc) after a reboot.  I know how to quickly and correctly  "reassemble" the array, after checking/getting the device numbers using *qtparted* to verify what they are at that time.  
The external drive array is all SCSI, installed in a SUN A1000 Drive Array.  This problem only became an issue after upgrading to 8.10 Intrepid.  It has always been an issue when I upgrade the OS, but has always only taken ONE "reassembly" procedure, and that continued to work correctly boot after boot after boot.  Since 8.10 however, the change is "random" - meaning the drives change their device numbers every time I reboot.  This system has 4 internal drives, all SATAII: 2ea 500GB, 1ea 160GB and 1ea 300GB, and 1 external USB interfaced IDE drive.  
What I would like to know is how to make the SCSI drives be seen **last** by the system, instead of randomly changing the order the entire SCSI array is seen.  I mean that on one boot, the internal drives may be "found" by the OS as /dev/sda1, /dev/sdb1, /dev/sdo1 and /dev/sdp1, with the 12 SCSI drives being /dev/sdc1 thru /dev/sdn1.  The next boot might find the SCSI drives 1st - /dev/sda1 thru /dev/sdl1, with the Internal drives being /dev/sdm1 thru /dev/sdp1.  
It can be any order, but the SCSI Array is always 12 sequential device numbers, with the 4 internal drives being shown in their correct sequence on either end of the SCSI numbers or some at the beginning and the rest after the SCSI array, but still in their "correct sequence", but only relative to each other and not necessarily sequentially.  
I hope I have made my situation clear, and someone knows how to get those external SCSI to be **discovered last** - always.  I do not boot from the Raid 5 Array, it is just for storage - it is, however, a very important part of my system, and **must** be reliably available at all times.  
Any suggestions or assistance will be appreciated....
:):)
Regards...

mikey5555

---

