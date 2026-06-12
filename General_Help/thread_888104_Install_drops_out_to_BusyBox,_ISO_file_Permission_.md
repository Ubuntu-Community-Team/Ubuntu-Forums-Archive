---
title: "Install drops out to BusyBox, ISO file Permission problem [SOLVED]"
date: 2008-08-12
forum: General Help
---

### Post by spike.robinson on 2008-08-12
For some reason the ISO CD image in /isodevice/ubuntu/install was giving “Permission Denied” during the install. The symptoms were that the installation was dropping out to a black screen and BusyBox. The Permission Denied errors were found in the casper.log file. I had to go back to Windows and examine NTFS properties of the .iso file in the host Windows NTFS file system.  The .iso file had been set Read-only (probably OK) and Encrypted (not OK). Also, the .iso file had been marked as Blocked by a Security Policy. I cleared the Blocked status and the Encrypt flag. The installation then proceeded normally without incident.

---

### Post by Tuexnovia on 2013-03-11
> **spike.robinson said:**
> For some reason the ISO CD image in /isodevice/ubuntu/install was giving &#8220;Permission Denied&#8221; during the install. The symptoms were that the installation was dropping out to a black screen and BusyBox. The Permission Denied errors were found in the casper.log file. I had to go back to Windows and examine NTFS properties of the .iso file in the host Windows NTFS file system.  The .iso file had been set Read-only (probably OK) and Encrypted (not OK). Also, the .iso file had been marked as Blocked by a Security Policy. I cleared the Blocked status and the Encrypt flag. The installation then proceeded normally without incident.


I'm having the same problem with all my distros in two different computers...

How did you proceeded?

I don't understand the explanation sorry...


My real problem is in a HDD with WIN already I want to install Ubuntu lubuntu and so son... BUT I want to do it from my wubi boot USB and everthing work until I see that SCREEN of the hell...

Busybox

(initramfs) Unable to find a medium containing a live file system


And I can't install it...

---

### Post by Tuexnovia on 2013-03-11
I got the same problem with 2 computers... And in the bios of each one tehre is not too many option to mess with ASCHI, SATA...

Any help please...

---

### Post by Tuexnovia on 2013-03-12
Any idea? I can't find anything in google...

---

