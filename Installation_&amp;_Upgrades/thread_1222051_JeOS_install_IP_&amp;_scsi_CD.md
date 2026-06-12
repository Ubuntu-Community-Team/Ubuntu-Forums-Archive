---
title: "JeOS install: IP &amp; scsi CD"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by InUse on 2009-07-24
Recent install of JeOS 8.04 appeared to succeed, but once booted showed configuration problems   In particular the scsi CD drive appears to be missing.  It worked during the install.  In fact I booted the install CD on the drive in question, which is a Plextor PX-32Cse acting through an AIC-7880 port.

The symptom of the problem is that there is no block device for the CD.  Mknod /dev/scd0 b 11 0 appears to complete successfully, but mount fails to recognize it as a "valid block device" and rebooting leaves the system with no /dev/scd0 and dmesg makes no mention of scsi or cdroms (except for the mis-named "scsi" channel connecting the IDE drive).

I'm pretty sure this is a simple config issue.  I have several decades of experience in system admin, but none on Linux.  So I probably have the background experience to understand the problem but definitely lack the foreground experience to pin it down.

What should I be looking for?

[Admins: should there be a thread prefix for JeOS?  I stuck it under other, maybe it belongs in std::ubuntu]

---

### Post by Cheesemill on 2009-07-24
You're not trying to install JeOS on actual hardware are you?
JeOS is only designed to be installed as a VM, it only contains kernel drivers for virtual hardware (VMware, KVM, etc).

---

### Post by InUse on 2009-07-24
Hmmm.  I checked the doc and found that you are correct.  Apparently I missed the "within" condition applied to "virtualization environment".  I suspect the fact that I was looking for a thin host OS blinded me to the reality of JeOS.

In retrospect I find this situation unique.  My error was compounded by the fact that the install worked except for one fairly esoteric detail.  Given that software properly installed often does not work, how rude of JeOS to actually work when improperly installed!  Perhaps a warning or error message might be useful.

Clearly this is an impressively robust package.  However, the fundamentally unfair success of the improperly installed software indicates that there is a lot of non-virtual substance in the current package that is not really needed for use in a guest-only OS.

Thanks for the help.

---

### Post by Cheesemill on 2009-07-24
If you're looking for a lightweight VM host you should check out VMware ESXi. It's a bare metal hypervisor which means that it's a translation layer which runs between the virtual machines and the hardware, you should get native performance from your VM's and it only takes 32MB of space to install.
 
It's quite picky about the hardware it can run on but definately worth looking into.

---

