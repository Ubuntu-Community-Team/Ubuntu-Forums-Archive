---
title: "Automount not working anymore. VFS problem?"
date: 2005-03-02
forum: Hardware &amp; Laptops
---

### Post by NRios on 2005-03-02
Hi there!

Originally, my Ubuntu installation used to pop up a window whenever I plugged in a flash bar or I popped in a CDROM, but not anymore.

If I add the appropriate lines to fstab, I can mount the drives with a click and can then view the contents.

If at any moment I run the command `mount /dev/hdc  /tmp/mtpoint` with or without the fstab line, a window pops up with the CD contents. Same with a flash bar.

It won't work if I comment out the /dev/hdc and /dev/sda1 lines in /etc/fstab, but ensure that gnome prefs are to mount and examine removable drives and disks.  What happens in this case is:

*    I put a disk in the CD drive and close the tray
*    The drive spins up, then down
*    There is some hard disk activity
*    Activity stops
*    dmesg has the following message at the end:

VFS: Can't find a HFS filesystem on dev hdc
 
If I run `pmount /dev/hdc cdrom` I get the same spin up-down behavior, and then:
        mount: block device /dev/hdc is write-protected, mounting read-only
        mount: wrong fs type, bad option, bad superblock on /dev/hdc,
                 or too many mounted file systems
        Error: mount failed

Where do I have to touch to fix this?

Thanx!
_Nacho_

---

