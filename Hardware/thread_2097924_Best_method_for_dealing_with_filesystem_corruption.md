---
title: "Best method for dealing with filesystem corruption?"
date: 2012-12-24
forum: Hardware
---

### Post by ahallubuntu on 2012-12-24
I recently learned a few lessons in dealing with a corrupted filesystem.  This happened to me recently on a backup disk with two ext4 partitions.  It was a laptop drive in a USB enclosure.  I plugged the drive into a USB port that apparently didn't have enough power.  I kept getting a disk read error trying to access it so I tried to remove it safely but could not.  Both partitions were automounted by Nautilus and I was unable to un-mount them - I simply had to yank the USB cord. When I plugged it into another computer, both partitions refused to mount - bad superblock or something to that effect.

(Side note: I know about USB cables with two headers to get 2X the power; I should have plugged into the back USB port of this particular computer in the first place, to avoid this, instead of the weakly-powered front port.  Another story.)

This was not a disaster for me as everything was backed up anyway - this WAS the backup disk.  I could have just wiped the disk and re-copied everything.  But I decided to use it as a learning exercise.

First I simply ran e2fsck on each partition.  I had to do so manually, automatic mode refused to run.  (I finally just issued the -y switch to avoid answering thousands of questions.)  The biggest partition took about 20 minutes.  At the end I could mount that partition again, but everything was gone from the top-level filesystem, moved into Lost+Found.  Turns out all the files were intact, even the subdirectory structure of each subdirectory was intact.  I was able to recreate the top-level structure manually from memory in about ten minutes and restore most of the files to the way they were.

So, had this been a real recovery, everything would have been fine - just a bit of a pain with a bunch of manual work but no files lost.

Was there a better way to go about this than running e2fsck at this point?  It seems that the journal of each filesystem had simply gotten corrupted.  I'm very unfamiliar with the journaling of ext3 and ext4.  Is there some way to back up the journals to make a recovery a lot easier?  Can I assume if a backup of the journal had existed that e2fsck would have tried to use it automatically?

(Another lesson re-enforced: even just READING from a filesystem you have mounted could result in corruption in these weird cases.  I was not WRITING any files!  It's important to be very careful when removing these external drives - best to eject them or "Safely Remove" them when you can!)

---

### Post by CharlesA on 2012-12-24
Even if you are just reading from a file system that is mounted a read-write, it could possibly be written to. The only "safe" way to make sure nothing is written to the drive is to mount it as read-only.

Your method seems sound, but I would not have forced fsck to automagically repair the errors - it is understandable why you chose to do it that way, but it's not a good thing to do in general.

---

### Post by ahallubuntu on 2012-12-24
> **CharlesA said:**
> Your method seems sound, but I would not have forced fsck to automagically repair the errors - it is understandable why you chose to do it that way, but it's not a good thing to do in general.

So what would you have done instead?  That's really what I'm asking here.

---

### Post by CharlesA on 2012-12-25
> **ahallubuntu said:**
> So what would you have done instead?  That's really what I'm asking here.

Probably clone the bad drive to another drive and work on the other drive and leaving the original alone.

That way the information isn't totally lost in case of failure.

---

### Post by ahallubuntu on 2012-12-25
OK, if this had been a real recovery (had this been my only copy), I can see having done the clone, just in case.  The wise, cautious choice.

But because this was just an exercise (since it was just a backup that I could have lived without), I probably didn't need to do that cautious step.  So then - instead of running fsck, should I have done something else?  Was there any possible hope of recovering the file structure at that point?  Would fsck have probably salvaged the file structure had it been possible to do so?

I briefly looked at testdisk, but that didn't seem like it would find the file structure, just individual files in case they had ben accidentally deleted or something.  It seems fsck was the best approach then?

If there's some way to make backups of my ext3 or ext4 journal in the future, perhaps that's something I should consider?

---

### Post by CharlesA on 2012-12-25
I don't really think you could have done anything differently.

As far as I know photorec and testdisk work on files, but I haven't really worked with them much.

If the file system itself it hosed fsck is probably a good option.

---

