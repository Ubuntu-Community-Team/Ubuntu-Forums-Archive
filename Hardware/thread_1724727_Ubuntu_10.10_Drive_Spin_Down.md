---
title: "Ubuntu 10.10 Drive Spin Down"
date: 2011-04-08
forum: Hardware
---

### Post by ThePol1 on 2011-04-08
I built a headless server using Ubuntu 10.10 (amd64). I have two drives that I use for weekly backup that I would like to spin down when not in use. They are formatted using ext4. I have modified hdparm.conf to reference the drives as such:

#-----------------------------------
/dev/sde {
spindown_time = 241
}
/dev/sdf {
spindown_time = 241
}
#-----------------------------------

How do I verify the drives are being spun down?

---

### Post by ThePol1 on 2011-04-08
> **ThePol1 said:**
> I built a headless server using Ubuntu 10.10 (amd64). I have two drives that I use for weekly backup that I would like to spin down when not in use. They are formatted using ext4. I have modified hdparm.conf to reference the drives as such:

#-----------------------------------
/dev/sde {
spindown_time = 241
}
/dev/sdf {
spindown_time = 241
}
#-----------------------------------

How do I verify the drives are being spun down?

I should also add that my fstab looks like this:
UUID=(UUID) /media/(UUID)     ext4    rw,suid,dev,exec,auto,user,async,noatime 0 2

I believe that *noatime* will stop the kernel from accessing the drive every 5 seconds and allow it to spin down. I'd like some way to confirm that the drive has spun down, however.

---

### Post by ThePol1 on 2011-04-08
Found the solution:
[http://ubuntuforums.org/showthread.php?t=1416047](http://ubuntuforums.org/showthread.php?t=1416047)

---

