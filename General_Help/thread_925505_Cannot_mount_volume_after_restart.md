---
title: "Cannot mount volume after restart"
date: 2008-09-20
forum: General Help
---

### Post by Caps18 on 2008-09-20
I just installed a second SCSI drive in my Mythbuntu machine and thought I set it up correctly.  It was working and I wrote 2 GB (that I knew I could lose) to the drive.  I was copying those files off to an external drive and the computer locked up and had to have the plug pulled.  Now when I restarted it, I get the error:

> Cannot mount volume

Unable to mount the volume

Details

mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.  In some cases useful info is found in syslog -try    dmesg | tail or so

> Failed to mount "1T volume"

Failed to determine the mount point for /dev/sdb1

Is this some type of root permission issue since I am only a user logging in?  When I type sudo mount -t jfs /dev/sdb1 /mnt/sdb1 into the terminal I get the same error as above:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error.  
In some cases useful info is found in syslog -try
dmesg | tail or so

I'm not sure if I setup my /etc/fstab file correctly though.  I added this manually:

> 
#/dev/sdb1
UUID=     /mnt/sdb1    jfs     defaults    0    0

I'm not sure if I need to give it a UUID, or find it's UUID, or have it enter it automatically or something...

dmesg | tail doesn't have anything useful (ip6 router can't be found NFSD grace period, AGP stuff), and it can't find the syslog command.

Did I kill this drive or something?  What else can I try to get it working?  What advice do you have to set it up so this can't happen again and just works?  

Thanks!

---

