---
title: "Is a HD that reports bad sectors definitely dead?"
date: 2013-11-27
forum: Hardware
---

### Post by chortle on 2013-11-27
I have an external Western Digital My Book Essential 2TB drive. I was using it to back up data from elsewhere. I started having trouble with files being corrupted. I thought it might be some s/w problem. So I took off the files and used Western Digital's LifeGuard s/w to test the drive. That failed on both the quick and extended test. The s/w said the drive has too many errors to continue. 

Good news I got all data off the drive. 

Is the drive definitely toast, or is this perhaps a housing problem, firmware, or something else?

Right now I'm writing the whole drive with zeros to clear any of my data prior to returning the drive (1 year into 3 year warranty) and also to see what that says about the drive state.

This is a USB 3.0 drive. I was able to detect it under Windows but not Ubuntu. I put that down to an Ubuntu issue with USB 3.0 - but perhaps now it was just showing some underlying problems with the drive/housing.

---

### Post by Yellow Pasque on 2013-11-27
Post SMART data:
```
sudo apt-get install smartmontools
sudo smartctl -a <devpath> -q noserial
```
<devpath> = /dev/sda, for example. If you're not sure of the devpath, look at:
```
sudo fdisk -l
```

---

### Post by chortle on 2013-11-28
Thanks for your reply. Hope your certification goes well.

I can't get this drive "loaded" in Ubuntu. In Virtual Box it shows as a device to add, but I can never add it.

In Windows I managed to write zeros to every sector using Western Digital's software. That took about 15 hours. Once again I tried to do a quick scan with their s/w and that failed. Now I'm running HD Tune Pro 5.5 and that is showing loads of errors. So I guess this drive is really screwed and I managed to get it out just in time. The only remaining thing to check is if the USB 3.0 cable is stuffed. But I guess that is not the problem.

---

