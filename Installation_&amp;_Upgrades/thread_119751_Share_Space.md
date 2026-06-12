---
title: "Share Space"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by Yes_It's_Me on 2006-01-20
Hi all, ok, I'll be gettin my new AMD system very soon and want to set up a duel boot with Ubuntu and Windows (which i realy hate now but i need it for games) any way i will be getting a 160 or 200gb hdd
i was planning on having:
for 160gb, 120gb for windows (for all the games) 30gb for Ubuntu and 10 for a shared space for music and so on or:
for 200gb, 150 for win, 40 for ubuntu and 10 for shared, anyway i want to know how do i use this shared space, do i boot from it? or is it a drive (like in windows with c:\ etc)?
Also is it possible to have itunes manage the music i store on the shared partition and have a linux equiverlent (suggestions?) manage the same music? or do i have to put it on the dedicated drives.
and finally what format do i make this shared space? or do i leave it as "free space" (ill use the ubuntu partitioner)

thanks guys.:confused:

---

### Post by nkhansen on 2006-01-20
I don't know how iTunes manages it's music, but if I can use both Quod Libet as well as Rhythmbox, I would guess that it would be possible.

I currently have five partitions:

hda1 NTFS (C:) 8gb for windows and base software (OOo, Firefox, Civilization IV)
hda5 ext3 (D: and /srv/media) 90gb media library (music, recorded tv and so on) 
hda6 reiserfs (/)
hda8 reiserfs (/home)

WindowsXP can read ext2/3 with a driver (If you plan to use this, I could find the link). An alternative could be to format your 10gb partition as FAT32.

If you just make the partitions
Then install Windows (on c:)
Then install Ubuntu (on the appropriate partition), and during the partition editing - which you have to do manually - select to mount the 10gb partition as something sensible (such as /srv/media).

---

### Post by Xumbi on 2006-01-20
I use a FAT32 partition between my Linux and Windows installations.

These links might help you:

[http://www.linuxquestions.org/questions/showthread.php?t=193406](http://www.linuxquestions.org/questions/showthread.php?t=193406)
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=112555](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=112555)

---

### Post by Yes_It's_Me on 2006-01-20
Ok, thanx guys.
so say i have a 200bg hdd, should i set up the partitioning like this:
150 as ntfs as primary (win)
40 as ext3 as primary (ubuntu)
9 as fat32 as logical (shared)
1 as swap as logical (swap)
?
And when i put files on this shared drive, do i just copy and paste to the new drive?

thanks for all the help.

---

