---
title: "Backup-imaging tool for Breezy?"
date: 2005-11-23
forum: General Help
---

### Post by jblaty on 2005-11-23
What is the best way to backup/image the O/S drive for a Breezy installation?  I would like to place a compressed backup image on a separate hard drive and/or DVD-R on the same box.  In case of emergency, I should be able to restore the image.  Is there a backup imaging tool that anyone can recommend?

---

### Post by gapplewagen on 2005-11-23
I have always used g4u.  It's free and does a great job.  Compresses image from HD into a single compressed file and then ftp's it to whereever you want (if you have an ftp server to store the image).  Check it out at [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by jblaty on 2005-11-23
Thanks for that reply.  That is a floppy/CD-ROM based solution, meaning that you need to boot the machine to back it up or restore it.  I'm looking for a live backup solution...that is you can backup the machine's image (on a regular schedule) while the server is running, and without having to reboot.

Any other suggestions that might fit this?

---

### Post by gapplewagen on 2005-11-23
Ahhh I see.  Sorry, I'm not aware of anything that does exactly that.

---

### Post by gapplewagen on 2005-11-23
It may not be a full image, but perhaps this will help you: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by jblaty on 2005-11-23
Well, that's a filesystem-based solution.  Unfortunately, I have several filesystems that I would want to exclude from that backup, so I'd have to selectively tar up the paths I need.  Yes, it will work, but it also will require a working knowledge of the O/S filesystem structure and what to back up.  If anyone has any ideas on a live image-based backup/recovery tool, I'd love to hear them...?

Examples:  I have used Symantec Ghost 9 and Acronis TrueImage on the Windows platform.  I'm looking for a Linux equivalent.  Preferably, one that isn't extremely expensive.

---

### Post by ranf on 2005-11-23
[QUOTE=jblaty]Well, that's a filesystem-based solution.  Unfortunately, I have several filesystems that I would want to exclude from that backup, so I'd have to selectively tar up the paths I need.  Yes, it will work, but it also will require a working knowledge of the O/S filesystem structure and what to back up.  If anyone has any ideas on a live image-based backup/recovery tool, I'd love to hear them...?

Examples:  I have used Symantec Ghost 9 and Acronis TrueImage on the Windows platform.  I'm looking for a Linux equivalent.  Preferably, one that isn't extremely expensive.[/QUOTE]
I haven't used it, but some guys at my local LUG where talking about it and seemed to like it: `bacula' (it is in universe).

---

### Post by jblaty on 2005-11-27
I found the following live backup tool for Linux (Mondorescue), and you may want to check it out:

[http://www.mondorescue.org/](http://www.mondorescue.org/)

FYI, I had no joy in installing the mindi and mondo package using Synaptic or apt-get, because of an unlisted dependency.  I went ahead and downloaded the Debian packages and dependencies, and installed it using fpkg.

I'm running a backup now to my hard drive.  It also supports CD-R, -R/W, DVD-R, etc.

Happy Backing Up!

Regards,
Joe

---

### Post by peterx14 on 2005-11-27
You could try Partition Image (partimage):

[http://www.partimage.org/](http://www.partimage.org/)

although I'm not sure this would suit if you're trying to backup the partition that you're running from; it might be okay.... but it might not!

In any case, therre seems to be [a problem with it working on Ubuntu 5.10 so you'd need to fix that first (hint hint!)](http://www.ubuntuforums.org/showthread.php?t=94953) :D

---

