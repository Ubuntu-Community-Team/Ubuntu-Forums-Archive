---
title: "HFS+ support trashing Catalog file?"
date: 2008-11-28
forum: General Help
---

### Post by damiannz on 2008-11-28
hey,

i'm on a MacBook, and have only recently made the switch to Ubuntu, so i still use my old OSX partition (mounted read-write) as my main drive (for example, i'm sharing my Thunderbird mail directory from my HFS+ partition between OSX and Linux).

i'm getting fairly regular catalog corruption on the HFS+ drive. sometimes fsck/Disk Utility can repair this, sometimes it can't. for example, this is what is happening now:

```
$ sudo fsck /dev/sda2
fsck 1.41.3 (12-Oct-2008)
** /dev/sda2
** Checking HFS Plus volume.
** Checking Extents Overflow file.
** Checking Catalog file.
** Checking multi-linked files.
** Checking Catalog hierarchy.
** Checking Extended Attributes file.
   Reserved fields in the catalog record have incorrect data
(8, 138)
** Checking volume bitmap.
   Volume Bit Map needs minor repair
** Checking volume information.
   Invalid volume free block count
   (It should be 1159503 instead of 1159494)
** Repairing volume.
** The volume hdd could not be repaired.

```

this drive is still mountable read/write (although i know i should be only using it read-only while it's damaged like this...), but OSX no longer boots, and i know from prior experience that i will need to run a proprietary tool (DiskWarrior) to rebuild the catalog file to make OSX boot again.

i discovered that there is a company called 'Ardis' that make an hfsplus driver: [http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/). is this the same as included in the Linux core? (i assume not, as it mentions resource forks accessible via /rsrc, and my drive does not have a /rsrc directory). does anyone have any information about it?

is there a better forum i could ask this question? perhaps it's not so Ubuntu-specific...

---

