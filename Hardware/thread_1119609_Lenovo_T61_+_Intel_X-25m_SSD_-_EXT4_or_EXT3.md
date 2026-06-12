---
title: "Lenovo T61 + Intel X-25m SSD - EXT4 or EXT3?"
date: 2009-04-08
forum: Hardware
---

### Post by truse on 2009-04-08
When the new Ubuntu version, Jaunty jackalope is coming, I am going to install the "new" Intel X-25M SSD into my Lenovo laptop. The question that I am struggling to get a good answer to is:

Will EXT4 be a better choice for Jackalope (with the SSD in mind), or should i use EXT3 for a while longer? 
Pros? Cons? 

I appreciate serious answers. Thanks!

---

### Post by whoop on 2009-04-08
Well the problem here is that ext4 and ssd's are relatively new. So you're on uncharted territory here. If I am totally being honest there is no real mainstream file system that is optimized for ssd's. All of the current file systems have endless lines of code to deal with rotational latency, head movement and the like. This is off course totally useless for ssd's. 

The best file system for ssd's in theory is to use a raw flash memory media file system (like UBIFS for instance), but that's just a theory and probably not a viable option.

Have you thought about using ext2? I think SSD/Linux uses ext2, maybe because it doesn't use journaling. I think the main point is to minimize the wear and tear on the drive.

So personally it doesn't really matter. You can use any of the file systems. If you're a total "nerd" you could use ext2 or ext3 without journaling and with noatime to try and preserve wear and tear.

Then again, if I owned a ssd I would probably use ext4 and jump to btrfs as soon as it's stable just because it's the newest thing around.

---

### Post by bwakkie on 2009-05-08
I would go for ssd and ext4. It will speed up everything!
Perhaps it is all new so just bake more often backups with your dvd burner.  Have a look at a [Phoronix benchmark]("http://www.phoronix.com/scan.php?page=article&item=intel_x25e_filesystems&num=1") just about this subject although they talk about the E and not the M drive.


Cheers,
Bastiaan

---

### Post by whoop on 2009-05-08
> **bwakkie said:**
> I would go for ssd and ext4. It will speed up everything!
Perhaps it is all new so just bake more often backups with your dvd burner.  Have a look at a [Phoronix benchmark]("http://www.phoronix.com/scan.php?page=article&item=intel_x25e_filesystems&num=1") just about this subject although they talk about the E and not the M drive.


Cheers,
Bastiaan

That's what I would do as well. although hardware techies might go for ext2, I think.
Just be sure to keep a look out for brtfs, it's not quite ready for use yet, but it is what we all should/will be using in the future (if the predictions are correct) and it has specific optimization for ssd's.

---

