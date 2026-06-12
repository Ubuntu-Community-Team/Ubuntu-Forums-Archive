---
title: "Recover corrupt partition"
date: 2008-08-10
forum: General Help
---

### Post by zchenyu on 2008-08-10
Ok, I ran into a serious problem recently. I moved my HD to a new computer and it was shown as "BAD". So I moved the HD back to the original computer and started showing some bad signs. I couldn't mount my /home partition due to numerous errors. So naturally I ran fsck on the partition. The fsck went on to prompt to fix thousands of errors. I ctl+c the fsck part-way through and used ddrescue to copy the HD over to a new HD. I then proceeded to run fsck -y on the original /home partition to completion. It appears that it placed ALL of the files in /home/lost+found, as opposed to only some of them.  This makes it almost impossible to sift through all of the data and re-organize them. Is there an easier way to do this?

There's an interesting thing about my particular case. I normally run Gentoo Linux, and prior to running fsck, I chrooted into Gentoo (from Ubuntu, where I ran the fsck) and I could use the /home just fine.

Timeline:
Move HD to new computer
Received BAD from BIOS
Moved HD back to old computer (dual-booting Ubuntu and Gentoo)
Tried booting into Gentoo, failed
Booted into Ubuntu
chrooted into Gentoo, found everything worked
Ran fsck on all partitions, /home is the only partition with errors
Ran fsck on /home, received thousands of errors
Cancelled fsck
Copied /home to a new HD using ddrescue
Continued with fsck on /home using -y

So essentially what I want to ask is if there's any way to recover my files on /home without destroying the directory structure?

---

### Post by pytheas22 on 2008-08-10
I'm not sure whether it always works this way, but the one time that my ext3 /home partition became corrupted (on Fedora, by the way), I used fsck to fix the errors and, as in your case, it dumped everything into lost+found.

Within lost+found, all of the directories had weird names that appeared randomly generated.  But I found that overall, the directory structure of /home had been preserved--it was just that all of the subdirectories had weird names.  For instance, /home/Desktop was now /home/lost+found/sadlfkjds or whatever.  But all of the files that used to be in Desktop were in that folder.  By figuring out which folder inside lost+found corresponded to which subdirectory of /home, I was able to rebuild my /home directory without too much effort.  It still took maybe half-an-hour, but that was preferable to losing all of my data and user preferences.

I don't know if fsck always works like this, but it's worth a try to see if it did in your case.

Otherwise, maybe you could take a look at the fsck man pages.  I don't know, but perhaps there's an option to tell it to try to preserve the directory hierarchy.

---

### Post by Mgiacchetti on 2008-08-10
Best thing I would say is add -V  and/or pass it to a log file so you can discern all the folders if noted.

---

### Post by zchenyu on 2008-08-11
> **pytheas22 said:**
> I'm not sure whether it always works this way, but the one time that my ext3 /home partition became corrupted (on Fedora, by the way), I used fsck to fix the errors and, as in your case, it dumped everything into lost+found.

Within lost+found, all of the directories had weird names that appeared randomly generated.  But I found that overall, the directory structure of /home had been preserved--it was just that all of the subdirectories had weird names.  For instance, /home/Desktop was now /home/lost+found/sadlfkjds or whatever.  But all of the files that used to be in Desktop were in that folder.  By figuring out which folder inside lost+found corresponded to which subdirectory of /home, I was able to rebuild my /home directory without too much effort.  It still took maybe half-an-hour, but that was preferable to losing all of my data and user preferences.

I don't know if fsck always works like this, but it's worth a try to see if it did in your case.

Otherwise, maybe you could take a look at the fsck man pages.  I don't know, but perhaps there's an option to tell it to try to preserve the directory hierarchy.
I checked, and the lost+found directory contains only a bunch of files named "#0000000" where 0 is some number. =K

There doesn't seem to be any option in fsck that preserves directory hierarchy.


> Best thing I would say is add -V and/or pass it to a log file so you can discern all the folders if noted.
How would I do that (pass to a log file)?

---

### Post by pytheas22 on 2008-08-11
> How would I do that (pass to a log file)?

Maybe there's a better way, but wouldn't it work to use:
```

fsck [...] > log.txt
```

---

### Post by zchenyu on 2008-08-11
> **pytheas22 said:**
> Maybe there's a better way, but wouldn't it work to use:
```

fsck [...] > log.txt
```

That doesn't quite work since fsck needs input from the terminal. I also tried piping to tee, but received the same problem.

---

### Post by pytheas22 on 2008-08-11
Does it create a log at /var/log/fsck?  The Internet seems to think it does...

---

