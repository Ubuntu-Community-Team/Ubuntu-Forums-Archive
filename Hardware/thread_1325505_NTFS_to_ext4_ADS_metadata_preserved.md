---
title: "NTFS to ext4: ADS metadata preserved?"
date: 2009-11-13
forum: Hardware
---

### Post by VulcanTourist on 2009-11-13
I am considering migrating some data from an NTFS partition to an ext4 partition.  Some of the files in question have alternate data streams attached, which contain metadata like comments.  If I boot into Ubuntu and actually copy such files to an ext4 partition, is that ADS metadata recognized and replicated in some fashion, or is it lost entirely?  Is the answer less clear-cut, perhaps dependent upon which specific NTFS driver package I use or which software I use to do the copying?

Also, what happens to NTFS junctions in such a scenario?  Are they universally lost, or can they be converted to ext symlinks?

---

### Post by VulcanTourist on 2009-11-14
Anybody?  It's not so arcane a question that I've stumped everyone, is it?

I don't like the idea of bumping my own thread, but in three hours I watched it disappear onto the third summary page, and further downhill from there.  Getting a question noticed here without some marketing might be harder than the computers-and-tech section of Craigslist. :(

---

### Post by John Bean on 2009-11-14
> **VulcanTourist said:**
> Anybody?  It's not so arcane a question that I've stumped everyone, is it?
Probably ;-)

I've done no formal testing but being as user of both my observations are that ADS is ignored. You could probably find hard answers in the ntfs-3g documentation, since that's what will be used to read the data from the NTFS volume.

I can't remember all the obscure Microsoft terminology so you'll have to remind me what a "NTFS junction" is. If it's what I think it is - a volume mount point in another volume - then it will also be ignored. Best to consult the primary documentation though.

---

### Post by VulcanTourist on 2009-11-14
Thanks, John.  It's not the educated guesses I'd hoped to hear, of course.  Yep, NTFS junctions are mount points to another volume.  I don't have a lot of them, and I think I'll live in their absence, but it would have been nice if they were carried over.  Those ADS comments and such are the bigger deal, and might be a deal-breaker.  I've confirmed that Windows 7 would recognize a GPT disk, but I'm trying to avoid feeding the beast yet again.

NTFS-3G isn't my only option for NTFS access, though, is it?  There's another package, whose name escapes me (and I'm back in Windows, having borked Ubuntu by trying to install KDE/Kubuntu on top of it from Synaptic); I wonder if it might handle this scenario better when NTFS-3G can't?  What happens if I install both?  How do I configure which one will be used for handling NTFS?


As a potential tangent, I've encountered a bizarre problem with the RAID volume being recognized in Ubuntu: it's completely invisible until I run GPartEd, after which it magically appears in Nautilus.  It's an NVRAID volume, not mdadm(?), using four 1TB drives; GPartEd identifies it as some "mapper" device, but then also shows the four individual drives as empty (which I've been careful to leave the heck alone).  I used GPartEd earlier to create the needed GPT structure on the volume, and then partitioned it as ext4.

It doesn't appear as an item in /media until after GPartEd is run; I don't have to actually manipulate anything, just run it and then exit, and then the RAID volume magically shows up.  It remains visible and usable until I reboot, and then I have to rinse and repeat.

I seem to be able to create all sorts of trouble with Ubuntu; at least with Windows I had the experience to get in under the hood and fix things when the Registry got corrupted, etc.  At the moment I'm feeling like I can't troubleshoot my way out of a paper bag in Linux.

---

### Post by John Bean on 2009-11-15
> **VulcanTourist said:**
> NTFS-3G isn't my only option for NTFS access, though, is it?
ntfs-3g is the most advanced (and feature rich) driver for NTFS volumes, I have no experience of others. Which you use is is defined at mount time so it's up to you to specify which to use, for example "mount -t ntfs-3g /dev/hda1 /mnt/windows", whatever.

> I seem to be able to create all sorts of trouble with Ubuntu; at least with Windows I had the experience to get in under the hood and fix things when the Registry got corrupted, etc.  At the moment I'm feeling like I can't troubleshoot my way out of a paper bag in Linux.I know the feeling. I've used both Windows and Unix-like systems for years but can still be relied on to break either at (usually) the least opportune moment. Usually I can now unbreak them as well, but I still remember that awful feeling of helplessness when finding my way around an unfamiliar OS.

---

