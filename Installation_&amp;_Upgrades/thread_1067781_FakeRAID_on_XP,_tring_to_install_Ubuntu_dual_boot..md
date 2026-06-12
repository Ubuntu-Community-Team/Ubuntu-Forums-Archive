---
title: "FakeRAID on XP, tring to install Ubuntu dual boot."
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2009-02-12
My XP computer has, I believe, a RAID-5 configuration. Ubuntu tutorials refers to this as a FakeRAID.
Here is Quote from,
[I][http://www.hardwareanalysis.com/content/topic/67628/](http://www.hardwareanalysis.com/content/topic/67628/)
RAID-5 &#8211; Striping with Parity &#8211; 3 disk minimum:
This is the most widely used RAID array used today. What RAID-5 does is the parity information gets distributed amongst all drives within the array unlike RAID-3 or 4. A certain amount of total disk space becomes unavailable on the array so that the parity data can be written to disk. Usually, the amount of drive space given for parity information is equal to the size of one entire drive in the array. Example, an array of 4x10GB drives would give you approximately 30GB of space for your data while the left over 10GB would be reserved for the parity information.[/I]

Here's the IDE HD setup. C: 120gb; master. F: 200gb as slave on same cable as C:. G: 120gb with pin sideways, neither master or slave on it's own cable.
On my 1st attempt to install Ubuntu I took a safe approach. I cleared all of F: (200gb), made it master & disconnected C: & G:. It was when I reconfigured BIOS for CD boot that I remembered it was RAID but didn't give it a thought; THEN!
Ubuntu CD loaded, installed & on reboot all was extra slow & eventually failed to boot. Finally, I abandoned & successfully reset everything & it was before, all XP no Ubuntu.
I found this in the forum, [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) but it mentions *you must use the Alternate Install CD*. I've looked but cannot find an Alternate Ubuntu Install CD. The article also note issues in *RAID-5 Notes* when installing with Nvidia present, which is what it is.
Any ideas?

---

### Post by GARoss on 2009-02-12
Anyone?

---

### Post by avtolle on 2009-02-12
Try [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) for the alternate install iso. Good luck.

---

