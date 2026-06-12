---
title: "SCSI Device not being detected anfter first reboot."
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by Ian Christie on 2005-02-22
I have a system that is mixed IDE and SCSI. 13GB IDE master, main drive. 9GB SCSI secondary drive that I'm trying to install Warty on.

System is a Dell PowerEdge 1300, 256MB Ram, 600MHz P3

SCSI controller = Adaptec AIC-7890

The IDE drive is to have /boot, / and swap and my home directory is to be on the SCSI drive, this is where I run into trouble.

When I first boot the install CD, the SCSI controller is loaded no problem, partitions get setup and everything. Then the system reboots and the install attempts to check the drives, IDE partitions check fine, however, at this point the SCSI controller hadsn't been loaded and the check fails on the SCSI drive. Also the system attempts to mount my home directory, no luck, again because the controller drivers aren't loaded.

I believe that eventually the controller  is activated, but it seems strange that it wasn't loaded before attempting to mount and check. This also happens with Debian Sarge, but not with any other distro I've tried (Peanut, Slackware, CentOS, even OpenBSD has no problems).

Any ideas why it does that?

---

### Post by alastair on 2005-02-22
Not sure - it's sometimes painful mixing, even with respect to PC BIOS.

It's worth checking that your have the adaptec module present under :

  /lib/modules/<kernel version>/

e.g.

find /lib/modules/2.6.10-3-386/ -name 'aic*'

(change to suit your kernel)

If present, you could try adding the module to those loaded at boot i.e.

Add "aic7xxx" to :

/etc/modules

A guess .... Good luck.

---

### Post by Ian Christie on 2005-02-23
Thanks for the sugestion, attempted another install, it turns out the module fails to load after the fsck stage.

The first boot, from the CD installs the module, no problem, it's the second boot where it (a) attempts an FSCK and mounting of the scsi drive before it installs the module then (b) the module appears to fail to load, the attempt to load the module is late, after the fsck and mounting attempts.

---

