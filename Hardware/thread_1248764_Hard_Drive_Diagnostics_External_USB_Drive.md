---
title: "Hard Drive Diagnostics External USB Drive"
date: 2009-08-24
forum: Hardware
---

### Post by SneakPeak on 2009-08-24
[Solved] edit:  See post number 5 for a link to some software that works with external USB drives.  Unfortunately it works under Windows only but if you have access to a windows machine that you can plug your external drive into it does work.  See post 5 for more details.

Hi,

My system suddenly crashed on Sunday morning with no warning.  By using TestDisk and Supergrub I managed to get back to normal booting and all my stuff is still there.

BUT.... I am scared my hard drive is dodgy and will crash catastrophically in the near future.  My whole linux system runs on an external USB Fijitsu Siemens hard drive.  I just setup my work laptop (which has windows XP) to boot from USB first.  My Ubuntu hard drive is then plugged into the USB port and it boots and I am a for away a fully functional Ubuntu system and I just ignore the stupid XP.  

I checked out the Fujitsu diagnostic tool on "UltimatebootCD" but it runs in dos has all sorts of disclaimers and my drive type is not listed in the supported hard drives.  I would hate to crash my drive by trying to run the wrong diagnostic tool on it.  

Long story short: I am looking for a reliable safe hard drive diagnostic tool that I can run on an external USB Fujitsu Siemens hard drive. (320GB)

Thanks

Sneaks

---

### Post by recluce on 2009-08-24
> **SneakPeak said:**
> Hi,

Long story short: I am looking for a reliable safe hard drive diagnostic tool that I can run on an external USB Fujitsu Siemens hard drive. (320GB)



In all likelyhood, there is none. This has nothing to do with the OS, the problem is that 99% of USB bridges do not support the commands required for SMART or other meaningful diagnostics.

Your best bet would be to connect the drive temporarily to a PC using the native interface, PATA or SATA, to run diagnostics. This would involve removal of the drive from the external case and possibly voiding your warranty.

Software: once you remove the drive, you will be able to see who manufactured the drive. Go to the manufacturer's website to download the diagnostic tools.

And before you do anything: MAKE A BACKUP!

---

### Post by SneakPeak on 2009-08-25
Thanks for the advice but I am a bit scared to take the drive out of its external casing.  I will just back up my home directory on a daily basis and see what happens.

Cheers

Sneaks

---

### Post by louieb on 2009-08-25
command line tool to access the drives built-in diagnostics. 
```
sudo apt-get install smartmontools
```

GUI front end GSmartControl is on the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") and will be available for Ubuntu starting with v9.10

---

### Post by SneakPeak on 2009-08-25
Hi

This software was recommended in another post:

[http://hddguru.com/content/en/softwa...01.22-HDDScan/](http://hddguru.com/content/en/softwa...01.22-HDDScan/)

It does work with USB drives and will do S.M.A.R.T testing if you have a recognized / compatible USB drive.  (I don't)  If your drive is not compatible / recognized then it will do some basic "Read" and "Butterfly Read" and "Erase" and "Verify" tests although there is a warning against using "Verify" if your drive is not recognized / compatible.

Cheers

Sneaks

---

### Post by mmmmna on 2009-08-25
> **recluce said:**
> In all likelyhood, there is none. This has nothing to do with the OS, the problem is that 99% of USB bridges do not support the commands required for SMART or other meaningful diagnostics.

Your best bet would be to connect the drive temporarily to a PC using the native interface, PATA or SATA, to run diagnostics. This would involve removal of the drive from the external case and possibly voiding your warranty.

Software: once you remove the drive, you will be able to see who manufactured the drive. Go to the manufacturer's website to download the diagnostic tools.

And before you do anything: MAKE A BACKUP!
FWIW, I built an external USB drive for use as a backup drive, I built it using a common kit ("I/O Magic", purchased at retail store "Staples"). For that device, all Windows XP administration tools (as well as all the SMART utilities I tried) and also the utilities in PCLinuxOS (fsck, fdisk, etc) all worked  perfectly when the Maxtor hard disk that I built with began to fail.

The USB layer was never a question for my device. I simply trusted that USB was acting as a serial data stream, communicating between 2 translator chips.

Your suggestion of removing the internal disk drive, although complex, is worthy; yet, my experience would suggest attempting diagnosis while still packaged as a factory assembled USB device.

---

