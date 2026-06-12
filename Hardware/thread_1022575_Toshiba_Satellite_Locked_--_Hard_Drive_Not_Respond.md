---
title: "Toshiba Satellite Locked -- Hard Drive Not Responding"
date: 2008-12-26
forum: Hardware
---

### Post by AggroSA on 2008-12-26
Last night I was pissing about on my laptop (Toshiba Satellite 4000 series), when my kitten decided to leap onto my chest with claws outstretched. Like a complete moron, I dropped my laptop. When I picked it up, it had frozen, and I held down the power button and hoped for the best.

Well, as of now, my computer boots up. Only problem is that it takes about an hour to do so, which says to me that the hard drive is on its way out.

I loaded an Ubuntu LiveCD and tried to mount the drive as per this guide: [http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

However, I received these errors:

```
Unable to mount "AggroDrive"

DBUs error org.freedesktop.DBus.Error.NoReply: Did
not receive a reply. Possible causes include: the
remote application did not send a reply, the message
bus security policy blocked the reply, the reply timeout
expired, or the network connection was broken.
``````
Cannot mount volume
Unable to mount volume "AggroDrive"

ntfs_attr_pread: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/error NTFS is
either inconsistent, or you have hardware faults, or you
have a SoftRAID/FakeRAID hardware. In the first case
run chkdsk /f on Windows then reboot into Windows
TWICE. The usage of the /f parameter is very important!
If you have SoftRAID/FakeRAID then first you must
activate it and mount a different device under the /dev/
mapper/ directory. (e.g. /dev/mapper/
nvidia_eahaabcc1). Please see the 'dmraid'
documentation for details.
```

Is there anything else I can try? I recently backed up my drive, so I'm not incredibly concerned, but I left my backup at school. As such, I'm screwed until the 13th. Thanks for the help.

---

