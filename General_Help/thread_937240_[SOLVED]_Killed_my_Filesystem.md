---
title: "[SOLVED] Killed my Filesystem?"
date: 2008-10-03
forum: General Help
---

### Post by Zeotronic on 2008-10-03
I'm probably too confused to be of much use, but using something along the lines of '**sudo dd if=boot.img of=hdb**' (I'm not entirely sure what the command was, but I failed to take note that it was to my second hard drive, until it was too late) I seem to have killed the filesystem on my second harddrive, which is where my Ubuntu was housed. The partitions there were a ext3 with a swap partition, but now they seem to think their one big fat16 (and even so, I cant access it). I had a good amount of data on there that I would like to try to get back... I'm not expecting to revive my Ubuntu installation (without reinstalling) but does anyone have any ideas on how I could access the data in there which is still intact?

---

### Post by knattlhuber on 2008-10-03
You could try to run testdisk (it's in the repos) from the Live CD to restore the partition.

---

### Post by Zeotronic on 2008-10-04
I had it analyze the hard drive, but it didn't come up with any results (thats what I was supposed to do right?). I don't suppose anyone has any other ideas?

---

### Post by knattlhuber on 2008-10-05
Frag.
Check out this thread. Maybe that can save your data:
[http://ubuntuforums.org/showthread.php?t=343691]("http://ubuntuforums.org/showthread.php?t=343691")

---

### Post by Zeotronic on 2008-10-05
Yea, that had occurred to me. I'm going to put off doing it until I can backup the hard drive though... because if that doesn't work it probably won't leave me with another shot.

Most people don't learn their lesson... you'll never catch me without a backup again.

---

