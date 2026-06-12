---
title: "Non Bootable CD (want to use floppy)"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by podollb on 2006-11-07
I have a old system that won't allow me to boot via the CDROM. That isn't a big deal since I have a floppy I can use and then gain access to the CDROM. BUT, the bootable CD doesn't seem to have anything on it (like an executable) to allow me to run it from the command prompt... 

So my question is, is there a way to emulate booting from a CDROM by using some sort of bootable floppy as a pass thru...

---

### Post by michux on 2006-11-07
> **podollb said:**
> I have a old system that won't allow me to boot via the CDROM. That isn't a big deal since I have a floppy I can use and then gain access to the CDROM. BUT, the bootable CD doesn't seem to have anything on it (like an executable) to allow me to run it from the command prompt... 

So my question is, is there a way to emulate booting from a CDROM by using some sort of bootable floppy as a pass thru...

If you have another machine in the network it would be probably easier to install using this machine (just share the mounted ISO image over the intranet using NFS or FTP and pont to it during the installation from the floppy).

michuk

---

### Post by podollb on 2006-11-07
But I guess I still don't know how the bootable floppy is going to "emulate" the bootable CD by just transferring the booting operation from the floppy to the CD. I don't think sharing it via the network really gets me any closer because my current machine has a CDROM that is available and active...

---

### Post by lazyart on 2006-11-07
Go here: [http://oldfiles.org.uk/powerload/bootdisk.htm](http://oldfiles.org.uk/powerload/bootdisk.htm)

Scroll down near the bottom of the page to (or just search the page for) OLDBIOS CD Bootdisk.  This will let most machines boot to CD by using a floppy disk.  That should get you jumpstarted.  This being an older machine you might need to use the Alternate CD install, unless of course you have 256 megs of memory onboard.

---

