---
title: "Mount .ISO as CD-rom"
date: 2008-07-27
forum: General Help
---

### Post by Uruz on 2008-07-27
Hey,

Is it possible to mount a .ISO as a CD rather than a drive? Program I'm using doesn't look at hardrives, just CD-Drives and AcetoneISO only mounts as a normal drive as far as I can tell.

Thanks

---

### Post by Tim Sharitt on 2008-07-27
You could mount the iso in the /media/cdrom0 directory.
```
sudo mount *isoimage.iso* /media/cdrom0 -o loop
```
This will make the iso appear as a cdrom.

BTW, put the full path to the iso where I put isoimage.iso

---

### Post by dexter.deepak on 2008-07-27
you should better try :
```
sudo mount -t iso9660 -o ro,loop=/dev/loop0 <ISO_File> /media/cdrom0
```
otherwise you may get a demand for the filesystem type.

---

