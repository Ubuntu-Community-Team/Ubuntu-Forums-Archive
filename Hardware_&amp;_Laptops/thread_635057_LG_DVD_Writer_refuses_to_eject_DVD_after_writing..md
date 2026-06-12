---
title: "LG DVD Writer refuses to eject DVD after writing."
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by avlex on 2007-12-08
Hi everyone,

I have a seamingly rare problem with my DVD Writer. Most of the time, it works just fine, but sometimes after it finishes writing, it just wont eject the DVD. I have already tried the eject command as well as cdrecord to force the eject, but it just doesnt work. The funny thing about this is, that sometimes the burned DVD is just fine, while sometimes it is damaged and I really dont know where the problem is.

eject -vv tells me this (but doesnt actually eject the DVD)
```
eject: benutze Standardgerät `cdrom' (eng.: eject: using default device 'cdrom')
eject: Gerätename ist `cdrom' (eng.: device name is 'cdrom')
eject: erweiterter Name ist `/dev/cdrom' (eng.: extended name is '/dev/cdrom')
eject: `/dev/cdrom' ist eine Verknüpfung auf `/dev/hdc' (eng.: '/dev/cdrom' is a symbolic link to '/dev/hdc')
eject: `/dev/hdc' ist nicht eingehängt (eng.: '/dev/hdc' is not mounted)
eject: `/dev/hdc' ist kein Einhängepunkt (eng.: '/dev/hdc' is not a mount point)
eject: `/dev/hdc' ist ein Gerät mit mehreren Partitionen (eng.: '/dev/hdc' is a block device)
eject: versuche `/dev/hdc' mit dem CD-ROM-Auswerfen-Befehl auszuwerfen (eng.: trying to eject '/dev/hdc' with CD-ROM eject command)
eject: CD-ROM erfolgreich ausgeworfen (eng.: successfully ejected CD-ROM)
```

cdrecord -scanbus shows (for example):
```
Cdrecord-ProDVD-ProBD-Clone 2.01.01a33 (i686-pc-linux-gnu) Copyright (C) 1995-2007 J####Schilling
Linux sg driver version: 3.5.27
Using libscg version 'schily-0.9'.
...
        1001,0,0 100100) '/devices' '/pci0000:00/0000' ':00:' not present Simple direct access
...
```or```
        1001,0,0 100100) 't-ascend' 'ing.gif' 'ing.' NON CCS Optical Storage
```

And because of that, K3B and other frontends just ignore the device. I would really appreciate some help in the matter, since I dont like to restart my server everytime I need to transport rendering data (which can actually grow over multiple DVDs).

Edit: I found out, that activating DMA via hdparm -d 1 makes ejecting the DVD possible, but if I leave it active, the DVD is messed up because the whole system freezes. Any suggestions about that?

Thanks,


Avlex.

P.S.: The DVD Writer is a LG GSA 4167B and the server is running Ubuntu Gutsy.

---

