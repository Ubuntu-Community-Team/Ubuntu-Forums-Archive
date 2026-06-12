---
title: "Changing file permissions originating from OS X"
date: 2008-10-22
forum: General Help
---

### Post by Average_Joe on 2008-10-22
Hello.  Thanks in advance for reading.

A friend who is a user of Macs exclusively, gave me her failed external hard drive to try and save data from it.  I have managed to do that -- thanks to Ubuntu, by the way -- since I never could get Windows Logical Disk Manager to work with this old IDE drive without threatening to zap it first.

Now then, there is a single file folder which I cannot copy, in this attempt to save data from this external drive.  It is a file folder of type "mbox" and unfortunately seems to be locked as a Read-Only file system.  It makes good sense that OS X would have locked down permissions on this kind of e-mail related file.

I have tried chmod 777 both as user and as root, that is I tried to chmod this particular file folder only.  I also tried to chmod this file folder only recursively , with switch -R , but nothing will work, because of the Read-Only nature of the file system for this one folder.

I'd appreciate guidance on how to change the attributes of this one file folder, then change its ownership, so that I may use my installed Ubuntu to copy it over to a safe place like I did the other 15.4 GB of data from this old external drive.

THANKS again!!

---

### Post by dcstar on 2008-10-23
> **Average_Joe said:**
> Hello.  Thanks in advance for reading.

A friend who is a user of Macs exclusively, gave me her failed external hard drive to try and save data from it.  I have managed to do that -- thanks to Ubuntu, by the way -- since I never could get Windows Logical Disk Manager to work with this old IDE drive without threatening to zap it first.

Now then, there is a single file folder which I cannot copy, in this attempt to save data from this external drive.  It is a file folder of type "mbox" and unfortunately seems to be locked as a Read-Only file system.  It makes good sense that OS X would have locked down permissions on this kind of e-mail related file.

I have tried chmod 777 both as user and as root, that is I tried to chmod this particular file folder only.  I also tried to chmod this file folder only recursively , with switch -R , but nothing will work, because of the Read-Only nature of the file system for this one folder.

I'd appreciate guidance on how to change the attributes of this one file folder, then change its ownership, so that I may use my installed Ubuntu to copy it over to a safe place like I did the other 15.4 GB of data from this old external drive.

THANKS again!!

```
ls -al thefilename
``` and post the output here.

---

