---
title: "Partitioning - input/output error trying to write"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by kacheng on 2005-12-14
Upon trying to write the partition table, I get the error:

"input/output error trying to write to /dev......."

What might be causing this?

---

### Post by NotJustANewbie on 2005-12-14
What program are you using to do so?
What file system type are you creating?
Have you formatted the partiton first?

---

### Post by kacheng on 2005-12-14
I'm installing from the install CD - it does not get to the point where it formats the partition.

This happens for reiserfs+swap or for ext3+swap.

I'm trying to install to Virtual Server 2005, which emulates a plain vanillla computer.

Thanks.

---

### Post by poptones on 2005-12-14
LOL. Apparently, *not quite*.

---

### Post by kacheng on 2005-12-14
Now I'm getting this error:
[B]
The attempt to mount a file system with type ext3 in IDE1 master, partition #1 (hda1) at /boot failed.

You may resume partitioning from the partitioning menu.

Do you want to resume partitioning?[/B]

It doesn't seem to allow me to progress.  I've been here in the Partitioner about 30 times!!  ARGH!   I can't install without partitions!  Arrrgh!

---

### Post by kacheng on 2005-12-14
Strangely, I was able to get through an install yesterday.

What's different today?  I can't get past the partition creation.

---

### Post by NotJustANewbie on 2005-12-14
Try the live-Ubuntu CD install, then updating from there.

It must be something really small. Try tomorrow! lol

---

### Post by kacheng on 2006-01-07
I think that it has something to do with the use of **noacpi **or **nolapic **options at the boot menu.
Virtual Server 2005 seems to require these.

I created the image using Virtual PC 2004 without problems!

---

### Post by izardstreet on 2006-02-28
does anyone have a fix for this?
it seems that when I installed suse and did the safe install, i was able to get past this issue that re-arises in ubuntu.
the safe install disables some things like acpi or something.
anyoen?

---

### Post by arckeda on 2006-02-28
Gparted stand alone cd

---

