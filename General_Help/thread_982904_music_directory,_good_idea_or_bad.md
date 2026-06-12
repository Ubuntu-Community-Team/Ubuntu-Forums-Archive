---
title: "/music directory, good idea or bad?"
date: 2008-11-15
forum: General Help
---

### Post by christophski on 2008-11-15
When i recently installed Ubuntu 8.10 I was at the time thinking of a better solution as to where to keep my music library, so i decided to make an extra Ext3 partition and get the installer it to mount it as /music and I gave it full read/write permissions for anybody, is this a bad idea?
Also, when I was trying to backup my music using the cp command it kept saying "directory /music has been omitted" and I don't know why.

---

### Post by doug1212 on 2008-11-15
Hi,
The convention is to put the mount point in /mnt/<mountpoint>
I do this on my file server machine then change the owner to me:me.
777 permissions are best avoided, to be able to play your music other users should only require read permissions on the files.

these must be my most used commands :) used to set correct permissions for both files and directories which have to executable.

```
find /path/to/music-directory -type d -exec chmod a+rx {} \;

find /path/to/music-directory -type f -exec chmod a+r {} \;

```

Doug

---

### Post by Tom--d on 2008-11-15
Why not just put /home on another partition when installing. Thats the way I've done. Seperate to the system. Easyer to upgrade (no need to format the /home so all your configurations and personal files stay) and if the system partition fails. You still keep all your files :D

---

### Post by Th3Professor on 2008-11-15
> **christophski said:**
> When i recently installed Ubuntu 8.10 I was at the time thinking of a better solution as to where to keep my music library, so i decided to make an extra Ext3 partition and get the installer it to mount it as /music and I gave it full read/write permissions for anybody, is this a bad idea?
Also, when I was trying to backup my music using the cp command it kept saying "directory /music has been omitted" and I don't know why.

If you have multiple hard drives you could consider your /music going into a RAID set-up and putting other things, like OS/apps, on a separate drive that is independent of the RAID.

Here's a quick summary of the more popular RAID types:
0 = striped = improved performance (ideal for speed addicts)
1 = mirrored = redundancy (ideal for securing data)
5 = a bit of both, basically, very basically. ;)

You can also use various combinations of RAID "levels".

You can use 2 hard drives on level 0 or 1, and you can use 3+ drives on level 5.

In any case, something to consider. It's pretty neat how it works. At the moment I'm working on setting up my RAID5 with LVM so I can manipulate how volumes are handled within my RAID.

One of the purposes in my RAID is to mirror data - my music library, specifically (audio/music recordings that I create in my music studio), though also to store gobs of music from CDs/DVDs and gobs of TV shows/movies - that's all on drives 2, 3, 4. My 1st hard drive consists of my Windows Vista (gaming), Linux (music studio), Unix (general), and a section reserved for editing music that will be moved to the RAID group when not editing or when complete.

...somethin' to think about...

:guitar:

---

### Post by CatKiller on 2008-11-15
> **christophski said:**
> When i recently installed Ubuntu 8.10 I was at the time thinking of a better solution as to where to keep my music library, so i decided to make an extra Ext3 partition and get the installer it to mount it as /music and I gave it full read/write permissions for anybody, is this a bad idea?

I did that too. I subsequently mounted it as /mnt/music, but I made a symlink to it called /music in case any of the other users of my computer had put shortcuts or what-have-you to the old location.

It's your computer - whatever file location makes most sense to you is the correct one.

---

### Post by Th3Professor on 2008-11-18
> **CatKiller said:**
> It's your computer - whatever file location makes most sense to you is the correct one.

...I believe the OP was asking for suggestions or recommendations.

---

### Post by amp_man on 2008-11-18
> **christophski said:**
> Also, when I was trying to backup my music using the cp command it kept saying "directory /music has been omitted" and I don't know why.

you need to use cp -r (or --recursive) to copy folder contents. Add -v (--verbose) too to have each file name displayed as it's copied.

---

