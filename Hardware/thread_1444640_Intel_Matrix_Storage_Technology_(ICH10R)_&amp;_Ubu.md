---
title: "Intel Matrix Storage Technology (ICH10R) &amp; Ubuntu"
date: 2010-04-01
forum: Hardware
---

### Post by Mad Dawg on 2010-04-01
I know the "Fake RAID" question has been beaten to death around here, but everything I've seen involves installing GRUB to the array. This is not my intention, and I am looking for community feedback regarding my specific scenario.

I have an Intel DG45ID mATX motherboard which has ICH10R southbridge. This is the latest and greatest chipset for Intel Matrix Storage Technology and supports RAID levels 0, 1, 5 and 10. I currently have a 250GB Western Digital SATA 3.0 drive (may switch to 128GB SSD soon for performance reasons, but that's a different story) with Karmic installed. This is NOT a dual boot system, nor do I ever intend for it to be.

Recently I decided to rip my entire CD collection, and in my madness I decided to go FLAC. That means approximately 3 albums per 1GB of drive space. It's a huge undertaking (why I decided to go FLAC, do it only once and then transcode as needed), and I will run out of space before completing the job with this drive. Also, if it is truly my intention to do this once and have it always available then I need some fault tolerance in case a drive decides to crash.

I'm thinking of installing a couple 1TB drives in a RAID 1 array. These will not be for booting. I will continue to boot off the 250GB drive (and perhaps later off the proposed SSD), so I guess you could say I intend to have an OS/Applications drive and a RAID array for music, photos, videos, documents, etc. It would be nice even to install with '/' being the boot drive and '/home' being the RAID array, but not entirely necessary. I know that with dmraid package I can sort of make this work, but my question is it worth it? Are there unforeseen problems I could run into with this configuration? Will it be 'secure' enough for what I'm planning or should I go a different route (hardware RAID controller, frequent backups to external drive)? Does anybody have an experience with the little $50-100 SATA RAID cards I see everywhere?

Also, related but different question, Western Digital makes a line of 'RAID Enhanced' drives (RE3, RE4, RE4-GP), but they're about 50% more expensive than their Caviar Black (high performance desktop line) counterparts. Is it worth spending the extra or does it really not matter in a setup like the one I'm proposing?

---

### Post by Mad Dawg on 2010-04-16
Alright, I took the plunge and ordered two Caviar Black 1TB drives. Installed them and used the motherboard's RAID configuration menu to set them up RAID 1. Installed dmraid in Ubuntu since the array was not present at the time of original install. Palimpsest Disk Utility (Disk Utility under Administration) saw the array AND each of the 1TB member drives. I tried using it to partition the array with no luck. After much fooling around, rebooting, Googling and praying for an answer or alternative, I was empty-handed and just about to go the 100% software RAID way.

As a last resort, I booted the machine with my Karmic Live CD. Once it came up, I went into its Administration dropdown where lovely gparted still resides. Gparted had no problem seeing the array (and did NOT list the member drives separately), adding a MBR and partitioning/formatting EXT4. Reboot without the Live CD and the array is there and usable. A couple caveats, it looks like a removable drive to system and, initially, the permissions are root:root. Oh well, small matters. Permissions were easily fixed and treating it as a removable disk doesn't bother me since I can still use it in the intended manner.

Anyway, posting my experience in case anyone runs into same situation I was in. I'm running Karmic and with the exception of all the time I wasted trying to get partitioning to work in Palimpsest it was a fairly painless process. If you're wondering why I went with the Caviar Black instead of the RE series drives, a little research revealed they are the exact same drives but the RE series has Time Limited Error Recovery enabled in its firmware. There is rumor of a tool out there that will turn this on in any Western Digital drive. Looking for it. If it becomes a problem I will order the RE drives and the Blacks will find themselves in external drive enclosures acting as off-server backups of the array.

---

### Post by Objekt on 2010-04-16
I admit to thorough confusion.  I understand you are not trying to dual-boot off the RAID (a good thing for your sanity).  But it sounds like you are running a software-based RAID 1 with the data drives.  In that case, isn't the ICH10R superfluous?

I am not impressed with fakeRAIDs in general.  In late 2008, I experimented briefly with trying to dual-boot Windows XP and Kubuntu 8.10 off my fakeRAID (ICH9R) in RAID 1 mode, using two 1 TB drives.  It ended in tears and probably took years off my lifespan.

---

### Post by Mad Dawg on 2010-04-17
Truly there are some benefits and niceties to Linux Software RAID, and you're probably not saving much (if any) on the CPU overhead by allowing the +r southbridge to do its job. I'm still tempted to try the fully software path. However, this is a nice, simple solution that allows me to do a clean install on the main OS drive every 6 months when a new build makes its official release (not a fan of upgrades and don't have enough "extras" to make fresh install much of a pain) and have the array right there waiting for me when I come back up (or at least I hope). In short, this seems like it will be more convenient. I'll let you know for sure when Lucid comes out in a couple weeks, and if I'm in here screaming and cursing feel free to say, "I told you so."  :)

---

### Post by Objekt on 2010-04-18
I'm surprised that you could get the -R bit to do anything at all under Linux, but it does sound like it's working, since the Live CD sees your RAID as a single drive.  That didn't happen with my ICH9R.  Maybe the -10R is more Linux-friendly?

I'm not really sure what the ICHxR does do as a RAID controller, since, as you say, it offloads some (all?) processing to the CPU.  It's sort of the RAID equivalent of Winmodems and Winprinters: not an elegant solution, just a cheap one.

---

