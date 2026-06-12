---
title: "Strange problem with CDROM drives"
date: 2004-12-17
forum: Hardware &amp; Laptops
---

### Post by ghetto on 2004-12-17
Hi all,
I've just upgraded my PC with a new SATA HD and installed a fresh Ubuntu. Before I was using an ATA100 HD and everything was fine.
Now gnome won't automount the CD automatically, however I can mount them manually, but if I try to copy some data (in fact to transfer data, copy, lanuch executables or whatever) I receive an input/output error.
I've been able to access some CD, for example one with an avi video (one big file, don't know if it matter), so it's not a rule...

Another strange fact is that I received once an error message saying "the (blah...) cannot be found" (don't remember exactly, blame me!) when I added universe to Synaptic and tried to reload the lists. Some time later I've seen this error also tryng to access a CD.
In synaptic was solved launching apt-get update once manually.
Really I don't know if the two are binded but seemed like the same problem, no data transfer...

Any ideas? thank you

P.S. the same with a DVD-ROM and a PLEXTOR CD writer, both on IDE

---

### Post by scoon on 2004-12-17
Hey there, 

The drives may be the same but the addition of new hardware may have changed the way they are used.  Could you figure out what that error is and also post your /etc/fstab ?


scoon

---

### Post by ghetto on 2004-12-17
This is what:

ghetto@gondolin:~ $ cp /cdrom/Software/firefox-1.0.installer.tar.gz ./
cp: lettura di `/cdrom/Software/firefox-1.0.installer.tar.gz': Input/output error

However I can ls and see what's on the CD.... 

Nothing else!

Some CD are working, some other not, it's not a problem with my CDs because I can read them wherever else.

Here's my (default) fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I've read something similar but during the installation process, the system boot but after it can't access cdrom. Maybe a bug with SATA driver?

Hope there's a work-around, I really won't stop using Ubuntu!!!

---

