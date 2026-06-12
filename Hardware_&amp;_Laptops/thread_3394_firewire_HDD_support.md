---
title: "firewire HDD support?"
date: 2004-11-05
forum: Hardware &amp; Laptops
---

### Post by kelvinty on 2004-11-05
Hiya,
  After distro-hopping for an entire month (with 2 weeks devoted to trying to get a Gentoo-box up, had compilation nightmares ala Matrix-style the entire code-trip), I fell in love with Ubuntu. Fast for an i386 base, funky name and of course Synaptic!

  Back to the topic at hand, has anyone got a firewire harddisk to work? I've checked and saw that Ubuntu has loaded the required module (sbp2) and I see my firewire loading in the boot screen. However when I plug in my Sarotech cutie firewire harddisk nothing comes out. Any ideas?

  Thanks in advance!

By the way, the harddisk is formatted with FAT32, and I believe Ubuntu has enabled vfat support in the kernel, because my USB thumbdrive works.

Kelvin

---

### Post by diebels on 2004-11-06
My firewire hdd(vfat partitions) works most of the time. But I've had some random errors with this new utopia autodriverloading and automounting stuff.

I don't know much about this. New stuff, haven't found much documentation about it yet.

See if your hald is running. If not, run it with "sudo /usr/sbin/hald --drop-privileges --verbose=yes". Maybe you can get somewhere from there.

---

### Post by mattyh on 2004-11-07
I have an external Firewire HD formatted as FAT32.  There is a bug in the bugzilla right now about external devices being finicky about mounting.  If I have it on while I boot, it doesn't show up as mounted, BUT after I get into gnome I flip it off and then back on and it usually mounts.  Sometimes I have to do that a couple of times but it usually works pretty well.  It's a minor annoyance in my opinion.

---

### Post by kelvinty on 2004-11-07
I have just discovered why my Firewire HDD doesn't work when plugged in -

The cable is loose.

DOH!!~ -laughs- Of all things I fall prey to the most common follible known to idiot ocmputer users. There's indeed a dog day for everyone.

Anyway once the cable was settled, I plugged it in and Gnome showed a disk icon on the desktop. Funky. :)

Had some trouble unmounting the drive though, for it seems to always be busy. Digged around the net and discovered most probably it was due to the FAMD process that auto-updates file contents.

Work around : Drop to term, and then "sudo umount /media/sdd1 -l" replace "sdd1" with your firewire harddisk device pointer. There, the firewire harddisk should have unmounted.

Cheers and may you all suffer not loose cables!

---

