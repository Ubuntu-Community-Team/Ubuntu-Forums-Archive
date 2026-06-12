---
title: "Install on Intel STL2 mobo"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by samiam24 on 2009-01-31
I hope someone has had the same issue.  System configuration is dual P3 866 w/1gb ram, I am not using scsi.  I have recently upgraded from 1.1 to 1.13 BIOS in my efforts to install  Ubuntu 8.04.  I used this same CD (desktop alternate)to install on Dell 8200 Insprion laptop, so I know the CD is good and I verified the MD5 checksum. 
I have also tried the boot option with "noapic" and get an error that reads: kernal panic error could not find 03:03 device, or something like that.  Since I updater the bios, it now just goes to a blank screen with no cusor.  
If I just do the normal boot I get an error at "loading additional components" crashs at 2% and reads.

There is a problem reading data from the CD rom. Please make sure the cd is in the drive. If retrying does not work check the intergerty of the cd. 

I do the test and the cd does not pass. Why? I just used it on an install?

I have searched the forums and it appears that other users have had issues with this motherboard. 
[http://ubuntuforums.org/showthread.php?t=890755](http://ubuntuforums.org/showthread.php?t=890755)

*edit 
Inegrity test failed for cd rom check
./dists/main/hardy/binary-i386/packages.gz failed checksum.
I just loaded Hardy on my laptop, strange?  I will do the check on the laptop.

---

### Post by samiam24 on 2009-01-31
This may be a CD rom drive issue.

[http://georgia.ubuntuforums.org/showthread.php?p=6646773](http://georgia.ubuntuforums.org/showthread.php?p=6646773)

I if I do a google search for the same model there are post about this drive having issues reading burned disc.  Is this why most say to burn at 4x?

The install disc checked out ok on my laptop.

I will try to do a flash drive install.

---

### Post by samiam24 on 2009-01-31
WOOT!:D  

It was the CD rom drive.  I found another slim drive in the house to fit in the 1U chassis and it loaded right up!

---

