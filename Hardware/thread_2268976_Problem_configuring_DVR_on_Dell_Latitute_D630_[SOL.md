---
title: "Problem configuring DVR on Dell Latitute D630 [SOLVED]"
date: 2015-03-12
forum: Hardware
---

### Post by rioguia2 on 2015-03-12
i needed to back up a collection of photos onto a DVD.  I am using a Dell Latitude D630 with Ubuntu 14.04.  I attemped to use the common GUI's for burnin DVD like Brasero, etc. but each time the burns were incomplete, failing at the final step of making a checksum.

So I abandoned the GUI's and attempted command line burning with wodim.  I like wodim because it creates a fairly easy to read /etc/wodim.conf file.  After I failed at burning a DVD at the command line I read the wodim.conf file and saw that it hadn't detected my DVD burner.  I found a[ https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/1203559]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/1203559") bug report that suggested a work around which I was able to adapt after doing some more research.  I am putting my notes here in case it might spare someone the frustration and spoiled DVD's.

As suggested in the bug report, I edited the wodim.conf by adding the following line at the end of the file.

```
# this is just a comment explaining the next line was added per https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/1203559
wodim dev=/dev/sr0 --devices
```

Next, I checked to see if wodim would recognize my DVD writer and got the following response:

```
 $ wodim dev=/dev/sr0 -checkdrive
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'DVD+-RW TS-L632H'
Revision       : 'D400'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
wodim: Cannot load media with this drive!
wodim: Try to load media by hand.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
```

Next, create an image for burning.  I'm using the joliet and rock options so this backup will be most accessible in other systesm.  The input charset is just the local character setting on my machine.  I think if you leave it out mkisofs will automatically detect it.   The -o will be the name of the .iso image to be created and 2014_test is the directory that mkisofs will turn into an image.

```
mkisofs -iso-level 3 -J -joliet-long -rock -input-charset utf-8 -o 2014.iso 2014_test]
```

now insert blank disk and burn the dvd

```
/home/me:~/Pictures$ wodim -eject -v -data -sao speed=1 dev=/dev/sr0 2014_part_2.iso
```


And everything worked fine.  I hope this helps someone else.

---

### Post by Hulk_Joshua on 2015-03-13
thank you for the information, had given up burning on my ubuntu box so will definetly try this

---

