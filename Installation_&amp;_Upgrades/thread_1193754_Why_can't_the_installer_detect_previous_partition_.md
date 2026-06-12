---
title: "Why can't the installer detect previous partition schemes?"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by HyperHacker on 2009-06-21
This is just something that kinda bothered me. I use the install disc to ugrade from Xubuntu 8.10 to 9.04 because I've never had any luck with the in-place upgrade. When I do, it detects a previous install, but doesn't detect which partitions were mounted where. You'd think both of them being Xubuntu it would be able to do that and fill it in automatically.

---

### Post by Bachstelze on 2009-06-21
> **HyperHacker said:**
> This is just something that kinda bothered me. I use the install disc to ugrade from Xubuntu 8.10 to 9.04 because I've never had any luck with the in-place upgrade. When I do, it detects a previous install, but doesn't detect which partitions were mounted where. You'd think both of them being Xubuntu it would be able to do that and fill it in automatically.

Short answer is no.

Long answer is that the mount points aren't stored anywhere in the filesystem's metadata. To achieve what you're suggesting, the system would have to try mounting each partition, then look for a [font="monospace"]/etc/fstab[/font] file on each of them, and if it finds one, get the mount points from it. And what if you had two systems installed? Which one should it get the mount points from?

---

### Post by -kg- on 2009-06-21
> **HymnToLife said:**
> Short answer is no.

Long answer is that the mount points aren't stored anywhere in the filesystem's metadata. To achieve what you're suggesting, the system would have to try mounting each partition, then look for a [font="monospace"]/etc/fstab[/font] file on each of them, and if it finds one, get the mount points from it. And what if you had two systems installed? Which one should it get the mount points from?

Exactly.  You have to know your partitioning scheme yourself...which partitions are what...and since you're upgrading 8.10 to 9.04, you would need to mark at least your 8.10 root partition as root for the 9.04 install.

I am unsure whether you can perform an upgrade from an installation disk, since I never upgrade anyway...I always clean install.  I copy any of my critical files to another location, make the install, do the updates, install the software that I want, and migrate my data and files into the new install (or more often, leave them where they're at and access them from the install).  Is that what you're wanting to do?

From re-reading your post, you seem to have upgraded from a disk in the past...maybe you could teach me something. :D

---

### Post by HyperHacker on 2009-06-22
I just do the install like normal, set up partitions manually, keep them all the same as before and don't format any. It will remove what it has to of the old system and keep things like the home directories and settings intact. It's not perfect (looks like some programs have been uninstalled) but it's easier than trying to manually move everything out and back.

Is mounting each filesystem read-only to look for an fstab not feasible? I'm not sure why two systems would have different fstabs, but in that case you'd probably just want to ask which to use.

---

### Post by -kg- on 2009-06-22
> Is mounting each filesystem read-only to look for an fstab not feasible? I'm not sure why two systems would have different fstabs, but in that case you'd probably just want to ask which to use.

Yes, it's quite feasible, but likely not necessary unless you made your installation in several different partitions, like /boot, /home, and others besides your root partition.  Even then, it wouldn't be necessary to set the mount points at installation time, as you could do that later.

As to the different fstabs, HymnToLife was talking about different installations.  Each installation (say, Xubuntu and Ubuntu) would have it's separate fstab files to mount the appropriate partitions when you boot it up.

> I just do the install like normal, set up partitions manually, keep them all the same as before and don't format any. It will remove what it has to of the old system and keep things like the home directories and settings intact. It's not perfect (looks like some programs have been uninstalled) but it's easier than trying to manually move everything out and back.


I didn't know it would do that.  I figured that if you launched the installer on a previously existing partition that it would completely replace everything.  I suppose that makes sense, though...the only way to *really* start fresh would be to re-format those partitions.  If you don't format them, the information that was there would remain there, though it seems to me that it would overwrite some of the config files, so the installer must be smart enough to leave those alone if they exist.

As for the programs, yes, some of the programs would need to be unloaded.  You would need programs that have been updated for the new distro, if such was necessary.  If they were incompatible with the new distro, aptitude would likely uninstall them.

---

