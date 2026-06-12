---
title: "[resolved] iBook cdrecord issues"
date: 2004-12-16
forum: Hardware &amp; Laptops
---

### Post by mpfleger on 2004-12-16
Hey all.

I've been having the same problem as some other people with CD burning, however the UbuntuPPC install on my iBook didn't install any SCSI devices in /dev/.  I might have done something daft during install, but I can't remember.  Is there a relatively painless way to put the required scsi devices in there with the correct major and minor numbers, etc?

I might need some help configuring the system to use the drive via ide-scsi, too, but I've never been in this exact situation before =/

The cdrecord spew presently looks like this:
cdrecord -scanbus
<snip>
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

cdrecord -scanbus -dev=ATAPI
<snip>
scsidev: 'ATAPI'
devname: 'ATAPI'
scsibus: -2 target: -2 lun: -2
Warning: Using ATA Packet interface.
Warning: The related libscg interface code is in pre alpha.
Warning: There may be fatal problems.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/hda exclusively (Permission denied)... retrying in 1 second.



Thanks in advance for any help,
m

---

### Post by mpfleger on 2004-12-20
Hi all.

Apparently the 2.6.x kernel doesn't need to use ide-scsi (or even have scsi devs) to talk to various IDE/ATAPI devices.  I guess I might have known that if I read the kernel documentation =/

Anyway; in case anyone else is wondering:
     cdrecord -dev=/dev/cdrom
-does the trick.

I did this from the command line and also using cdrtoaster, and the latter is perfectly happy allowing the use of this device instead of its default.  I removed all of my Gnome packages recently, so I can't comment on any of the Gnome tools...

I hope that this is helpful to someone.

whee!
m

---

