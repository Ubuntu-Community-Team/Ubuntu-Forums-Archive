---
title: "FSCK ruined my drive"
date: 2008-07-14
forum: General Help
---

### Post by blairbo on 2008-07-14
Well, ok, I used fsck -y /dev/sdd and it "fixed" my drive my clearing all inodes and moving everything into the lost+found.  How helpful.  Ok, so, panic mode has set in.  I've unmounted my drive.  I've run it through testdisk, etc, and nothing.

Is there any way to get the files back in their original directory structure with proper file names?

We're talking about 150 gigs of MP3s, archived from years of CD collecting.

.. and no i don't have it backed up to an online service or something.. sheesh.. why would I bother with this then, hm? </crabbyness> sorry it's getting to me...

:(

---

### Post by perlluver on 2008-07-14
You should be able to pull it all back out of lost+found, but it might be time consuming.

---

### Post by blairbo on 2008-07-14
> **perlluver said:**
> You should be able to pull it all back out of lost+found, but it might be time consuming.

But everything in there is just numbered files.  Is there any way to recovery the structure and/or filenames?

wait.. scratch that.. ok.. so I went to terminal, did sudo nautilus...  went to the lost+found folder, switched to list view to get a better view of this.. and the file names are still there!  YAY!!! but the folders are all numbered mush... like "#7987248"

yeah.. whoa.. I think i remember there bing like 30000 folders or something...

so.. i'm 30 years old now.. so i'll have this cleaned up by the time I retire... greeeeeeat...

ok.. smarties..  anyone out there have a keen idea as to how to automate this malarchy?

---

### Post by perlluver on 2008-07-14
Maybe this thread will be of help [http://ubuntuforums.org/showthread.php?t=615680]("http://ubuntuforums.org/showthread.php?t=615680")

---

### Post by blairbo on 2008-07-14
Ok.. so what I've learned:
-My data is fine, just in the lost+found directory
-the directory names are the inode names of what used to be in the root, subfolders are still correctly named
-if I were to be able to build a table of inode-to-directory-names, I would be sailing, but i think the inode table is long gone
-since these are mostly MP3s, if I could find a program that could rename these directories based on the ID3 tags, that would be something worth looking into

thanks perlluver for your assistance!

---

### Post by Herman on 2008-07-14
confused57 told me he was in a similar situation recently and did 'gksudo nautilus' and right-clicked on the /lost+found and changed the file ownership and permissions. 
Then dragged and dropped the directories from there into a spare partition and recovered them all his data from there.

Please keep posting about how you get along as any information you can provide will likely help others in the future. Fortunately this type of thing doesn't happen very often, so when it does if we can learn from it at least we can get some good out of it.

Regards, Herman :)

---

### Post by CatKiller on 2008-07-14
> **blairbo said:**
> since these are mostly MP3s, if I could find a program that could rename these directories based on the ID3 tags, that would be something worth looking into

I think EasyTag can do this.

---

