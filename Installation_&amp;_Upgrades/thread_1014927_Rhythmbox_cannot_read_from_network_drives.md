---
title: "Rhythmbox cannot read from network drives"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by torsten.st on 2008-12-18
Hi,
after the upgrade to 8.10 Rhythmbox cannot read from smb drives.
I think I have seen a bug report but cannot find it.
Can somebody confirm the bug or even help me with that please.
cheers
Torsten

---

### Post by Mark Phelps on 2008-12-18
Sorry, don't use Rhythmbox; use audacious. But back in an earlier release (7.04?) I believe I was able to read (and play) audio files from a networked SMB drive by clicking the file in Nautilus.

Now (in 8.10), I find I have to manually mount the drive before I can access it.

I do that using an entry in FSTAB so the drive shows up on my desktop and I can select it through audacious.

Hope this helps.

---

### Post by torsten.st on 2008-12-19
Hi again,

no it doesn´t. Rhythmbox could access SMB drives in 8.04 but after the release change . . . it does not update the library and does not play from networked drives.
Does not seem to be a networking problem since totem works just fine. 
cheers
T

---

### Post by torsten.st on 2009-01-05
Hi again,

I mounted the networked drives with cifs instead of smb . . . that worked now. 
Thanks anyway . . . 
cheers
Torsten

---

