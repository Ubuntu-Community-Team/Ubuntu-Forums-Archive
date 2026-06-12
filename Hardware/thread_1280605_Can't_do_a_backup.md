---
title: "Can't do a backup"
date: 2009-10-02
forum: Hardware
---

### Post by cmcanulty on 2009-10-02
I have tried all file systems but no externals will mount or they mount and randomly unmount. Currently I am trying to mount my 2gb flash drive which used to automount. I type sudo su in terminal and mount but I don't know how to designate the drive as it isn't mounted to find it's path I tried sudo su mount media with no luck can someone say exactly what I should type in terminal? Currently I get the error: Cannot mount volume detailsBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
I also get no permission errors even when signed in as root. I have NTFS config manager, storage device manager, and ntfs-3g installed. I have also set permissions in the authorizations . Is there a way to get this working I need to back up and would like a way to keep them permanently mounted and permissions permanent. I don't always have them plugged in though, thanks. I also get all kinds of input/output errors in the short time I sometimes manage to mount something. I am afraid all the tweaks and fixes I have tried has only made things worse.

---

### Post by louieb on 2009-10-02
What version of Ubuntu? Specs of the machine? Have you tried booting with a live CD and see if it can access your drives? 

> I tried sudo su mount media with no luck can someone say exactly 

Thats really vague. Would help to know the exact commands

> Currently I get the error: Cannot mount volume detailsBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

Does not sound good. Can't tell if the error is due to hardware or software. That is why I suggest seeing what happens with the live CD.

---

### Post by cmcanulty on 2009-10-02
Well it is for sure software as 5 devices I have mount in windows but not ubuntu, used to at least mount the flash drives but now nothing. I am going nuts with this have spent hours trying to fix and everything suggested does nothing. I have tried ntfs ext3 fat 32 no luck. If I can't solve this I have to quit Ubuntu but I can't even do that without a backup first.

---

### Post by louieb on 2009-10-03
You forgot to say which version of Ubuntu. The newer ones will auto mount most files-systems automatically. 
IF you think its software try using a Live CD. Have you done that?

If the live CD fails then Please post the output of 

```
sudo fdisk -l
``` (lowercase L at the end) and 

```
sudo blkid -c /dev/null
```

---

### Post by cmcanulty on 2009-10-03
Yes I got backed up with live CD so now I will reinstall Ubuntu, should I try the bets Karmic or Jaunty?

---

