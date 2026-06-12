---
title: "Install Ubuntu 5.10, keeping home dir. from old Linux install?"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by mattlach on 2005-12-23
Can the above be done?

I currently use Gentoo (and have been for 4 years), and I got tired of things breaking every time I ran an update, so the human-friendly aspect of Ubuntu appeals to me.

My problem is that I have approx 70Gb of files that are important to me in my home directory on my current linux install, and I don't have the means to back it up.

If I were to remove all files except my home folder from my old linux install, and rename the home folder to something benign on the disk, is there a way I can install Ubuntu without it reformatting my partition?

I booted from the disk and was checking out the install, but a method like this was not immediately apparent.

Help much appreciated!

Thanks,
Matt

---

### Post by Koybe on 2005-12-24
You can just start installing, and when it comes to partitioning, choose not the format the home partition but assign the mount point to that partition. It should work, but maybe you'll need to tweak a bit afetr install concerning uid/gid of your user.

Anyway backup are always good ;)

---

### Post by mattlach on 2006-04-03
[QUOTE=Koybe]You can just start installing, and when it comes to partitioning, choose not the format the home partition but assign the mount point to that partition. It should work, but maybe you'll need to tweak a bit afetr install concerning uid/gid of your user.

Anyway backup are always good ;)[/QUOTE]

Agreed, backups are a good smart thing to do, but even with my DVD burner I'd be backing up many many discs :(

So the Ubuntu installer will install to a partition (ext3) without formatting or erasing it?

And the tweaking of which you speak to me would seem like all I need to do is as root chown my files recursively to my new user name...

---

### Post by slightly72 on 2006-04-03
I had the same problem (migrating from Fedora 3). As far as I could tell, Ubuntu installer can attach ext3 partitions in the directory hierarchy, but requires a newly formated partition to install (i.e. will neither install itself on the previous partition, nor make previous ext3 partitions the root of the hierarchy). You might get around this by freeing up a few gigs on your hdd (pretty "complete" Ubuntu requires at most 2 gigs), and then use the installer to use that space for the root partition (the installer can resize partitions). After installation, you can start deleting old Gentoo system files and resize partitions to achieve a balance between system files and your files. In my case, I have backed up the important stuff on an external HDD, and deleted the Fedora 3 partition so to make a clean start.

---

### Post by mattlach on 2006-04-03
[QUOTE=slightly72]I had the same problem (migrating from Fedora 3). As far as I could tell, Ubuntu installer can attach ext3 partitions in the directory hierarchy, but requires a newly formated partition to install (i.e. will neither install itself on the previous partition, nor make previous ext3 partitions the root of the hierarchy). You might get around this by freeing up a few gigs on your hdd (pretty "complete" Ubuntu requires at most 2 gigs), and then use the installer to use that space for the root partition (the installer can resize partitions). After installation, you can start deleting old Gentoo system files and resize partitions to achieve a balance between system files and your files. In my case, I have backed up the important stuff on an external HDD, and deleted the Fedora 3 partition so to make a clean start.[/QUOTE]


This could be a little bit tricky as well, as the partition numbers are going to change (hda1, hda2, hda3 etc.) but worth looking into.

What do you use to resize partitions in linux?  Gparted?

---

