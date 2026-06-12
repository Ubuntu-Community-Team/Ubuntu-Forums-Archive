---
title: "Unable to install new HDD in Feisty"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by ArchVile on 2007-08-17
hi folks,

i just got myself a new seagate ST3500630NS 500gig hd and installed in on my feisty machine which runs on an asus m2n-x main board (MCP65 SATA controller). however, the drive doesn't show up, not in gparted, not in parted, not with "sudo fdisk -l", not in the "hardware information" applet.

cabling and hdd are fine. BIOS detection is perfect. actually, the drive is detected by the feisty live cd (as expected as /dev/sdb, since it is on the secondary sata port after my first hd). i formatted it, fsck'ed it, wrote data to it... no prob, but back in my normal system, it's still not there.

sorry for the cynicism, but where is the "find new hardware" button? seriously: does anyone know how to get ubuntu to recognize the new disk? help is greatly appreciated.

cheers!
a/v

---

### Post by ArchVile on 2007-08-18
should anyone have this problem with the asus m2n-x (or any mcp65-based board): i solved the problem by putting the second (new) hd in the SATA3 slot. when in SATA2, the only distros (of the many i tried) which recognized the hd were: feisty live cd i686 (though NOT the AMD64 live cd) and fedora 7. now everything is fine.

i gues there are some quirks in the mcp65 support...

EDIT: ok, the problem is there again. i think i finally found out why different live cds kept supporting/not supporting the drive. it is only recognized exactly once after i plug it in a new SATA port. right now i'm downloading gutsy to get a 2.6.22 system, but hopes are low, to be honest.

---

### Post by ArchVile on 2007-08-24
the 2.6.22 kernel (i.e., the gutsy install) solved the problem. apparently, it's really a problem with the support for the mcp65 in the older kernels.

---

