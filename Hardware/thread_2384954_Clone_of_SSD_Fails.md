---
title: "Clone of SSD Fails"
date: 2018-02-14
forum: Hardware
---

### Post by Rick St. George on 2018-02-14
Running UbuntuStudio v16.04 and when attempting to clone/image main drive (SSD) with Acronis or CloneZilla it FAILS. Has anyone else discovered this problem with Cloning SSD drives?

Currently I am backing up with "rsync" and Zipping to a Storage HDD that I ONLY turn on when doing BUs.
But every quarter I would like to have an IMAGE BU of the SSD. Just can't seem to do it.

Thanks!

---

### Post by #&amp;thj^% on 2018-02-14
I don't use "rsync" Clonezilla will do this>>Now you have many options : Create an image of only '/' (saveparts) and clone it to any partition of your other SDD. 
More Here: [https://askubuntu.com/questions/741723/moving-entire-linux-installation-to-another-drive](https://askubuntu.com/questions/741723/moving-entire-linux-installation-to-another-drive)

---

### Post by Rick St. George on 2018-02-14
Sorry "1fallen", but as stated CloneZilla FAILS when attempting to use on an SSD. But I don't remember if I tried "/", or if it even gives that option. I will burn latest CloneZilla and try that version. Will post back.

---

### Post by oldfred on 2018-02-14
If you have reasonably fast Internet, often easier just to do a new install.
You cannot keep both drives installed if you clone as then you have duplicate UUIDs.
If you have to keep both drives, you must change UUIDs, reinstall grub, edit fstab and perhaps a few more things.
Or ;you have to disconnect or reformat old drive.

If you do a new install, then you have new UUIDs, and then reinstall apps, and rsync /home over from old install.
Also can restore data from backup, as test of your backup procedure as you still  then have old install to go back and get anything your are missing.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by #&amp;thj^% on 2018-02-14
> **Rick St. George said:**
> Sorry "1fallen", but as stated CloneZilla FAILS when attempting to use on an SSD. But I don't remember if I tried "/", or if it even gives that option. I will burn latest CloneZilla and try that version. Will post back.

Works for me. :P I can be up and running inside of 30 minutes.
There's no need to be sorry, we all have area's where we struggle at times. (And my methods are sometimes not the norm);)
And there are so many ways to to the same thing with Linux.
Your in excellent hands with oldfred.
And sometimes its the magician behind the wand. :)

---

### Post by Rick St. George on 2018-02-14
In going through the process, I remembered why it failed. With 8 cores it would go full blast until it overheated and died.

Since then I've installed a new Heatsink and Big Silenz Fan. Machine has been running quiet and cool. When making image of SSD to #2 HDD - no problem. Guess I haven't tried CloneZilla since adding the new heatsink. CloneZilla (09052017) backs-up via image fine ... but took 4 hours.
Rsync after 1st Run, now takes less than 5 minutes. So I do that weekly. Every month off-load to ext. HDD. 
Thanks OldFred for you Links as I have a file that Rsync looks for items/folders to exclude. 

Case closed.

---

