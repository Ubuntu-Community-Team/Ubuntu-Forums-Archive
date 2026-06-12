---
title: "[SOLVED] Suggestons for partitions"
date: 2008-10-18
forum: General Help
---

### Post by crazyness003 on 2008-10-18
Hello. I was wondering if anyone has a "tried and true" method of partitioning their HDD.

I currently have II 8.10 beta installed, and am wanting to wipe clean and reinstall when final release, but before I do that, i wanna get a really nice partition scheme going so next time I decide to install a newer version, i get maximum progress (minimum reset settings etc.)

***In the attachment is my current table. (better screenshot)

What I wish to do is have 
1. A small partition to install Arch, Puppy or any other distro for near instant booting when i need to just use the full web (with java and flash preferably).
2. Swap
3. Normal install of Ubuntu
4. Space to test any distro I want without VM (wanting to get to Gentoo or Slackware eventually)
5. 'Obligatory' windows partition (gonna use virtualbox to VM whenever i need to access any programs from there. Boot in when gaming)

I would also like to share all my personal data between all the installed OS's. What i currently try to do is use my windows (ntfs) partition. Not very effctive since ntfs is not cool at all. And dangerous since its on a same partition as win!!!eek!

Would you recommend a separate partition (ext3 or fat32) or just use what i currently use?

I have a "160 gb" HDD (total usable space: 149 gb) on a HP Pavillion tx1000 laptop

---

### Post by jerome1232 on 2008-10-18
Partitions are just such a subjective thing and are down to personal taste :) This is how I would do it, not for everyone though. I only use windows for gaming and could care less if it has access to my data.

This is a bit of a complicated setup, I like it because LVM is easy to expand (it can even expand across multiple disks) I use xfs because it seems easier to resize than ext3 and it's going to be the partition that does the growing.

Of course you can add as many rootvolumes as you want and share that data volume across distro's. I backup the data volume to an external drive so if Windows really needs access to music and such that's how it can get it.

This is just my prefrence and I don't recommend LVM unless you learn about it first.

```

/dev/sda1  /media/Windows ntfs 30G
/dev/sda2  /boot ext3 1G
/dev/sda3  Physical Volume for LVM the rest of the drive


Volume Group 'Linux' Physical Volumes - '/dev/sda3'

Logical Volumes on Volume Group 'Linux'
----ubuntuRoot  6G / ext3 (only mounted under ubuntu)
----linuxData  30G /mnt/data xfs (all Linux distro's have it mounted here)
----gentooRoot  4G / ext3 (only mounted under gentoo)
```

---

### Post by crazyness003 on 2008-10-18
> **jerome1232 said:**
> ```

/dev/sda1  /media/Windows ntfs 30G
/dev/sda2  /boot ext3 1G
/dev/sda3  Physical Volume for LVM


Volume Group 'Linux' Physical Volumes - '/dev/sda3'

Logical Volumes on Volume Group 'Linux'
----ubuntuRoot  6G / ext3 (only mounted under ubuntu)
----linuxData  30G /mnt/data xfs (all Linux distro's have it mounted here)
----gentooRoot  4G / ext3 (only mounted under gentoo)
```

Okay, so you have your grub installed at /boot. 
**[COLOR=Red][Q][/COLOR]** Does this allow you to merge your ubuntu and gentoo menu.lst's so that if theres a kernel upgrade, it auto syncs?

I was thinking of having a minimal install distro take care of grub. 
**[COLOR=Red][Q] [/COLOR]**Is that a good Idea?

I've never heard of XFS. Im assuming its a file system type. 
**[COLOR=Red][Q] [/COLOR]**Is the resizing thing the only benefit? 

I use an Acronis "live cd" (part of hirens or multi-boot software disks) to do all my heavy-duty partition work (and it does wonders resizing, moving or deleting any partition type...even ntfs MOST of the times. It faild once)

**[COLOR=Red][Q] [/COLOR]**Also, is a 6gb partition sufficient for Ubuntu? If so, 10gb would be plenty, I guess.

sorry if this is too much to ask.

thanks

---

### Post by jerome1232 on 2008-10-18
Well using LVM it's not a real issue to grow the filesystems. I start out with really small Logical Volumes and grow them as I see the need. If it fills up I can either grow the filesystem or migrate out /var or /usr (those tend to be the space eaters) It's very easy for me to just pop in another Logical Volume. This is my first go at using LVM so I'll see how well it scales :)

xfs has more features, online resizing, online defragging, and other shiny things. I've heard it's faster when handling large files.

ext3 is rock hard stable.

I let Ubuntu control the menu.list, and hand edit if I need to for Gentoo. I only installed Gentoo as an experiment and have gotten rid of it since.

Another variation that might work better for you (no lvm in this one)
```

sda1 /media/windows ntfs 30G
sda2 /boot ext3 1G
sda3 extended
-----sda5 / ext3 10G
-----sdaX If you wan't other distro's make as many partitions as you need for their root partitions
-----sda14 /mnt/data rest of the drive (that was alot of other distros!)I like to put symlinks in each distro's home folder to folders on this drive, makes the separate partition transparent to me
```

---

### Post by crazyness003 on 2008-10-18
> **jerome1232 said:**
> Another variation that might work better for you (no lvm in this one)
```

sda1 /media/windows ntfs 30G
sda2 /boot ext3 1G
sda3 extended
-----sda5 / ext3 10G
-----sdaX If you wan't other distro's make as many partitions as you need for their root partitions
-----sda14 /mnt/data rest of the drive (that was alot of other distros!)I like to put[COLOR=Red]** symlinks**[/COLOR][[SIZE=1](?)[/SIZE]] in each distro's home folder to folders on this drive, makes the separate partition transparent to me
```

So my smaller "Quick Boot" partitions should reside in the extended with Ubuntu? Okay.

[COLOR=Red]**[Q]**[/COLOR] Also, whats a symlink and how do you implement that? Im guessing its like using that partition as the Home folder for each distro.

---

### Post by jerome1232 on 2008-10-18
A symlink is just a 'shortcut'.

I keep /home's separate because configurations will conflict. Instead i'll make a symlink in my /home called Music, that points to /mnt/media/Music.

So when I save things into the Music symlink they are actually getting put in that data partition. I'll do that with every folder in /home so that everything ends up on that data partition.

---

