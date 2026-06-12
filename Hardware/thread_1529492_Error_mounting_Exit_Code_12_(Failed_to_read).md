---
title: "Error mounting: Exit Code 12 (Failed to read)"
date: 2010-07-12
forum: Hardware
---

### Post by Danish989 on 2010-07-12
I am running Ubuntu 10.04 on a 64-bit Sony Vaio CS, and everything was working fine until about 10 minutes ago when I put the system on standby, and when it came back and I tried accessing a drive partition, I got the following error:

Error mounting: mount exited with exit code 12: Failed to read last sector ( 403879528 ): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


Does anyone know what could have gone wrong? I'm an ubuntu newb, and any help would be appreciated. Thanks in advance!

---

### Post by Danish989 on 2010-07-15
Bump. =[

---

### Post by Danish989 on 2010-08-06
Bump again! I haven't found a solution for this one yet..

---

### Post by utilitytrack on 2010-08-06
Hello, probable something broken in [FONT="Courier New"]pm-utils[/FONT] package. Look at this: [https://launchpad.net/ubuntu/+source/pm-utils/+bugs]("https://launchpad.net/ubuntu/+source/pm-utils/+bugs") and at this: [http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=pm-utils;dist=unstable]("http://bugs.debian.org/cgi-bin/pkgreport.cgi?pkg=pm-utils;dist=unstable")

---

### Post by theonhighgod on 2010-08-09
> **Danish989 said:**
> Bump. =[

i've got this problem but i'm not sure what caused it, but it's not a problem with pm-utils, when i make progress i'll let you know.

Normally with corrupt boot partions i use testdisk but with this drive it crashes! only drive i've see it crash with!

any how, whatch this space

---

### Post by F W Adams on 2010-08-26
I just bought a brand new 2 TB drive and it comes up consistently with precisely the above problem with a different last sector number. Connected on USB, running 10.04, 32 bit. The same drive seems ok on XP.

Will post again if I fix it or get more info. but not feeling that confident.

---

### Post by F W Adams on 2010-08-26
Well I fixed mine just by reformatting the drive. Used GPARTED and NTFS. Had no data on it. Now working fine.

---

### Post by UniversityAve on 2012-11-15
The linux command "ntfsfix" rectified this problem for me.

Example: sudo ntfsfix /dev/sda2

See this post for details!
[http://ubuntuforums.org/showpost.php?p=8515846&postcount=5](http://ubuntuforums.org/showpost.php?p=8515846&postcount=5)

---

### Post by ashish-coolguy on 2013-09-01
thanks man.  i was getting same error with my 1TB NTFS HDD. you saved me :)

---

