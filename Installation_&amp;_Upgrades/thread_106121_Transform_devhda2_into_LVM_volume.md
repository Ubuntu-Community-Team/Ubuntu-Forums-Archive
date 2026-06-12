---
title: "Transform /dev/hda2 into LVM volume?"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by ShiftyPowers on 2005-12-19
Here's what I'm trying to do.  Below is the result of df -T -h on my system.  I originally partitioned the drives as below without doing much thinking or knowing anything about LVM.

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdc1     ext3    112G  3.0G  103G   3% /
tmpfs        tmpfs    253M     0  253M   0% /dev/shm
tmpfs        tmpfs    253M   13M  240M   5% /lib/modules/2.6.12-10-k7/volatile
/dev/hda1     ntfs     15G  5.3G  9.4G  36% /media/windows
/dev/hdb1     ext3    276G  174G   88G  67% /mythtv
/dev/hda2     ext3    261G   48G  200G  20% /media/HTPCStorage2

Now, what I think I can do is move all the data from /dev/hda2 to /dev/hdb1.  Then hda2 will be empty and I can create an LVM volume there through pvcreate.  Once that is created and a partition created within it I can move all the data back onto /dev/hda2 from /dev/hdb1. 

Finally, I can then (now that it's empty) append hdb1 to the LVM volume.

Does that make sense?  Is this possible with LVM?  

Does anyone have a link to a howto for LVM that would be simliar to this?

---

### Post by kosmic on 2005-12-20
Yes what you are asking is possible :)
 
Only one recomendation put the /boot partition outside your LVM.
 
A great Howto-> [http://www.tldp.org/HOWTO/LVM-HOWTO/]("http://www.tldp.org/HOWTO/LVM-HOWTO/")

---

### Post by ShiftyPowers on 2005-12-20
pardon my ignorance but I'm pretty sure that the "/" is the boot partition right?

I think i'm safe because i'm not moving /dev/hdc1 into the lvm

---

### Post by ShiftyPowers on 2005-12-20
here's the new df -h -T output

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hdc1     ext3    112G  3.0G  103G   3% /
tmpfs        tmpfs    253M     0  253M   0% /dev/shm
tmpfs        tmpfs    253M   13M  240M   5% /lib/modules/2.6.12-10-k7/volatile
/dev/hda1     ntfs     15G  5.3G  9.4G  36% /media/windows
/dev/mapper/HTPCvg-MythLV
          reiserfs    100G   33M  100G   1% /MythTV
/dev/mapper/HTPCvg-HTPClv
          reiserfs    445G  166G  279G  38% /MainDrive

---

### Post by ShiftyPowers on 2005-12-20
this brings up another point, does anyone know how to remove the windows part of a dual-boot system like I have above. I have /dev/hda1 that I'd like to remove

---

