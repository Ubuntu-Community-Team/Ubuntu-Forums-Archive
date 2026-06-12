---
title: "Bit torrent to usb hard drive"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by tmowerman on 2005-04-12
I bought a 160gb lacie usb2.0 hard drive to store downloads and backups on.  So far I have used azureus and gnome bit torrent from hoary and tried to download directly to it.  Gnome bit torrent tells me it is read only! Azureus just crashes.  

I wondered if anyone knew any options i could set to let me do this.  Then I can install windows on my laptop again and get working tv out.

One thing i think could be a problem is that my laptop has no native usb2 support, so I have added a usb 2 pcmcia card.  Hence the configuration is pci -> pcmcia -> usb2 -> scsi.  Perhaps all these layers cause a problem.

The hard drive is formatted as two fat32 partitions. 

Tim.

---

### Post by heimo on 2005-04-12
Sounds like the disk gets mounted as read only. How do you mount it? Is it automounted? Does it have its own line in /etc/fstab ? Check the parameters and watch for **ro**. Run *mount* without any parameters and send the line with your USB disk to this thread. And the line on fstab could be nice, too. :)


EDIT: Oh, mounting is the process of attaching device to filesystem. If I do *mount /dev/fd0 /mnt/floppy* I attach fd0 (floppy) to mount point /mnt/floppy

---

### Post by tmowerman on 2005-04-12
I mount it automatically with gnome volume manager.  It is not read only because i can copy files once they are downloaded onto it no problems.

The relevant fstab lines are:
```

/dev/sda1 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 )
/dev/sda2 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8 )

```

Thank you very much for helping

---

### Post by heimo on 2005-04-12
:-\ Hmm... I'm lost. I'd try another  filesystem. That may be unacceptable long term solution, but if it's possible to try.. What I'm thinking about here is the VFAT lacking file permissions. Wouldn't probably give "read only", though. :-/

---

