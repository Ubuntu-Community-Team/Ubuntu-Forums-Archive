---
title: "Raid problems on install"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by EdwardFisher on 2008-12-11
Hi Guys.
I have a dell desktop configured as follows:
500Gb HD Raid 0 (third party raid drivers)
C: 250Gb - Windows XP (NTFS)
D: 150Gb - Music, Apps etc (NTFS)
E: 100Gb - Linux (currently NTFS, but needs to be ext3)

So windows recognises all three partitions and treats the two hard drives as one, as per the Raid 0 configuration. I would like to install Ubuntu onto partition E, however it seems that even in manual partition setup it does not detect the raid setup and instead prompts to install on a new partition on one of the drives (i.e. No Raid)

Is this a problem with the installer, ive done a search and seems others have a similar problem. I posted a thread on here too but no resolution to the problem ([http://ubuntuforums.org/showthread.php?p=5939682#post5939682](http://ubuntuforums.org/showthread.php?p=5939682#post5939682))

Cheers.
Ed

---

### Post by Pumalite on 2008-12-11
This might help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

### Post by EdwardFisher on 2008-12-11
Thanks very much for the links.
Seems my setup has a FakeRaid rather than the true hardware raid. 
I don't really fancy reformatting and losing the windows stuff, I've only just managed to sort it all out again after the last time.

Anyone getting an error with that last link its here: [http://www.ubuntu-in.org/wiki/index.php/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/index.php/SATA_RAID_Howto)

Cheers.
Ed

---

