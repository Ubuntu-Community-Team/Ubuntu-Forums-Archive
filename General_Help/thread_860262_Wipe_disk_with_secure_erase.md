---
title: "Wipe disk with secure erase"
date: 2008-07-15
forum: General Help
---

### Post by littletwinkel on 2008-07-15
Hello,

I want to wipe my harddisk completely on a save method. Because the DBAN tool ([http://dban.sourceforge.net/](http://dban.sourceforge.net/))
does not wipe the hpa and dco, I want to use hdparm. This method supports 'Secure Erase' witch is now build in
modern disks.

The problem that I've got is the frozen status of the disk. Does anybody now how to avoid this without doing any physical actions ? 

Or does anybody know an (open source and free) solution to wipe the hpa and dco on a secure way ?

Thanks a lot,

LittleTwinkel

---

### Post by cariboo on 2008-07-15
THe first thing to do is to see if hpa is enabled. You can do this using hdparm:

```
sudo hdparm -N /dev/sdx
```

Where sdx is your hard drive. Unless you've specifically used HPA you should have no worries.

IF you want to securely wipe your hard drive ahve a look at **wipe**. It is available in the repositories and you can use Add/Remove Programs or Synaptic Package Manager to install it. For more info in a terminal type:

```
man wipe
```

Jim

---

### Post by littletwinkel on 2008-07-16
Jim: thanks for answering my question.

I'm not sure if the 'wipe' command remove the HPA/DCO of a disk. I think that it just rewrite the disk with zeros and ones depending on the algoritm (like the DoD method) nd it leaves the HPA/DCO intact.

The 'secure erase' method (see [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)) uses a function in the (modern) harddisk.

hdparm support that function also, but I've got some troubles with tool. What I'm doing, I always get an error 5 when using it.

 Issuing SECURITY_SET_PASS command, password="test", user=master, mode=high
 Problem issuing security command: Input/output error
Error: 5

 Issuing SECURITY_UNLOCK command, password="test", user=master
 Problem issuing security command: Input/output error
Error: 5

 HDIO_DRIVE_CMD(erase prepare) failed: Input/output error
 Problem issuing security command: Input/output error
Error: 5

---

### Post by tamasrepus on 2009-11-07
Sorry to resurrect an old post: from your description, your BIOS has probably locked you out from using the ATA Secure Erase command.

A good resource for the ATA Secure Erase command and Linux: [http://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](http://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

### Post by jaygo on 2010-06-15
I'll re-resurrect this post again...
In my experience, not all modern drives have secure erase enabled, and I would input/output errors on the drives that didn't support it. So if it's not your BIOS blocking you, it may well be the drive.

---

