---
title: "PNY Vibe mp3 player weird behavior"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by Arjunanda on 2006-12-26
I am facing strange issue with my PNY Vibe 1Gb mp3 player: There is very loud noise when I try to play some files. These MP3 files play perfectly when copied to my Ubuntu laptop, and they used to play well on Vibe as well. Now some of the files have horrible loud noise, alternating with the music. It is almost as if I was listening a radio station where the signal is low and one moment I am hearing the music for a second, then loud noise, then music again, then loud noise. The noise comes in irregular intervals and the music plays also irregularly. At the same time, there are certain files that play perfectly. Also the sound recorder works well and I can also listen the files. I have the problem only with the music player function.

I assume the memory/filesystem is corrupt. Could this be the reason?

I tried reformatting the stick, I tried both FAT32 and FAT16, but it just said "Error! Reformat media. FAT only!" I am using Linux mkdosfs for formatting. And tried both, FAT and FAT32. Did not work.

I re-formatted the player under windows to FAT and got rid of the "Error! Reformat media" -message.

Returning to Ubuntu, I copied some files to the player and got them playing. No noise! Wow, it works! But: When adding some more files, it seem to have corrupted the earlier files, and all files have the same noise, again. Grrr! If I copy the files to my PC, all files are played perfectly. If I copy them back to the PNY player, I hear the same noise again.

I assume it has something to do with fragmentation of the filesystem or the way linux handles the filesystem. Perhaps it has something to do with the fact that the files are not copied directly to the media, but only afer I umount the filesystem. Perhaps the files are non-continuous or something like that. Really weird issue. Any ideas?

---

