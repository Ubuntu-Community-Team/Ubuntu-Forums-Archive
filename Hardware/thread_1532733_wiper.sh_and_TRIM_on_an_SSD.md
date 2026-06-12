---
title: "wiper.sh and TRIM on an SSD"
date: 2010-07-16
forum: Hardware
---

### Post by wiresquire on 2010-07-16
Hi

I've recently got a G.Skill Phoenix Pro 60GB drive ( [FM-25S2S-60GBP2](http://www.gskill.com/products.php?index=286) ), a sandforce SF-1200 based drive. I'm interested in checking TRIM is working correctly. 

Installed:
* I have installed Maverick Meerkat (with all updates) on an ext4 partition. This has a kernel that includes TRIM support.
* Edited /etc/fstab to add the discard option which enables TRIM
* I have downloaded the wiper.sh 2.7 files [directly from hdparm](http://sourceforge.net/projects/hdparm/files/) project, as wiper.sh was not included in meerkat that I could find.

To see if the kernel TRIM was working, I followed some [simple steps](http://www.ocztechnologyforum.com/forum/showthread.php?63843-The-truth-about-firmware-1.4-and-Linux&p=479503&viewfull=1#post479503). Everything looks fine, and I am seeing the correct output according to that guide. I read the sector and see all the zeroes 0000 0000 output.

I have run wiper.sh manually on another ext4 partition that has 10.04 installed (stock, all updates). When I boot into that it does not have a TRIM enabled kernel. So, I booted into Meekat and ran wiper.sh against that partition to 'clean it up'.

When I run it, it seems to run successfully. 
```

$ sudo ./wiper.sh --commit /dev/sda4

wiper.sh: Linux SATA SSD TRIM utility, version 2.7, by Mark Lord.
Preparing for online TRIM of free space on /dev/sda4 (ext4 mounted read-write at /mnt/ubuntu1004).

This operation could silently destroy your data.  Are you sure (y/N)? y
Creating temporary file (9251416 KB).. 
Syncing disks.. 
Beginning TRIM operations..

/dev/sda:
trimming 18502832 sectors from 325 ranges
succeeded
Removing temporary file..
Syncing disks.. 
Done.
```

There is disk activity for a little while, and so it appears to work.

But:
*when I re-run the command, it shows exactly the same output, ie trimming 18502832 sectors from 325 ranges. Does this mean it hasn't worked?
*when I use the --verbose flag and then examine one of the sectors that is reported to be going to be TRIM'ed, it still shows data in it, ie it hasn't been zeroed as in when the kernel does the TRIM.

Is the above normal? Is wiper.sh actually working?

TIA
ws

---

### Post by dcstar on 2010-09-10
> **wiresquire said:**
> Hi

I've recently got a G.Skill Phoenix Pro 60GB drive ( [FM-25S2S-60GBP2](http://www.gskill.com/products.php?index=286) ), a sandforce SF-1200 based drive. I'm interested in checking TRIM is working correctly. 
.........
Is the above normal? Is wiper.sh actually working?

TIA
ws

AFAIK the whole process just tells the SSD what are actually free blocks, and then the SSD just marks them as available to use.

Because you are not actually changing the available free blocks, repeating the process will always return the same numbers.

I assume you have put the **discard** option in your /etc/fstab file so you system now automatically handles TRIM (assuming you are using a TRIM enabled kernel)? Example of my SSD fstab line below:

```
UUID=adaf9c80-1d4e-40d8-a7f6-171f6523c8e1	/ext4	errors=remount-ro,noatime,nodiratime,**discard**	0  1
```

---

