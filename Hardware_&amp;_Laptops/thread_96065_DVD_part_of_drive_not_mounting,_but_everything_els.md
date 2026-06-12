---
title: "DVD part of drive not mounting, but everything else is."
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by lerrup on 2005-11-28
My DVD drive used to work fine, but since upgrading recently I have the following problem.

My CD-RW/DVD-ROM combi-drive on my laptop is unable to detect DVDs.  When putting a DVD in the drive for example I get the following in Konqueror:

An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.

This also happens in gnome when it just sort of ignores the disc, but totem will say:

Failed to find mountpoint for device /dev/hdc in /etc/fstab

Needless to say there is one. My current fstab is the same as the one I had that produced a fully functioning DVD drive.

This seems similar to other problems that have been posted, except USB drives mount perfectly as do computer Cd's.  Audio CDs also play and can be ripped without a problem.  Both are autodetected.

I tried the hal modifying tip here: [http://www.ubuntuforums.org/showthread.php?t=79204&page=3&highlight=fstab]("http://www.ubuntuforums.org/showthread.php?t=79204&page=3&highlight=fstab").  This has not cured the problem.

The DVD drive works in windows.

---

### Post by lerrup on 2005-11-28
Anyone with any thoughts about this?

---

### Post by lerrup on 2005-11-28
It also doesn't work with DVD-roms.  

So basically the problem is that Breezy does not recognise DVDs of any sort in a combo drive.

Does anyone know how these are handled in Ubuntu?

[This thread]("http://www.ubuntuforums.org/showthread.php?t=89224&highlight=pmount") gave a temp solution - a more permanent one would be good!

---

### Post by wobster on 2005-12-25
This problem still exists with the Breezy here.

---

### Post by siempae on 2005-12-26
I am expericencing this problem as well.  After I updated the Kernel to 2.6.12-10-686 dvds stopped mounting, everything worked properly in 2.6.12-9-686.  

I think it is also important to note that when I plug in my firewire external dvd burner I can mount dvds with no problem.  So it is only the internal combo drive which experiences this issue.

However, and i find this funny, when Adept prompts me for the Kubuntu install dvd to install changes, it will read the dvd from the combo drive, eventhough it is not mounted.

---

