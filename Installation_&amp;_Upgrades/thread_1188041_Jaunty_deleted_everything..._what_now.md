---
title: "Jaunty deleted everything... what now?"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by beukesma on 2009-06-15
Hi all,

I used custom partitioning to install 9.04 but something went terribly wrong. I made double sure I only checked the format tick box on one of the drive partitions (my previous distro's /). But it seems all my files on my other ext3 drives was deleted. 

How could this have happened??? 

Installation said that it would delete any system files on mounted drives but it never warned that it would wipe everything.

What now?

Can I get my data back?

:(

---

### Post by burntwater on 2009-06-15
I know there are tools that allow one to retrieve deleted files from disks, though I am not sure what these are... will consult Dr Google and let you know what will work with these drives of yours.

Were they ext3, ntfs or fat32?

Holding thumbs that your data can be recovered!

Regarding the installer.... no idea?! Pretty odd behaviour I'd say, I've never had issues with the installer before.

---

### Post by beukesma on 2009-06-15
> **burntwater said:**
> I know there are tools that allow one to retrieve deleted files from disks, though I am not sure what these are... will consult Dr Google and let you know what will work with these drives of yours.

Were they ext3, ntfs or fat32?

Holding thumbs that your data can be recovered!

Regarding the installer.... no idea?! Pretty odd behaviour I'd say, I've never had issues with the installer before.

Drives used ext3 then and now, it does not seem like a format happened... more like a "rm" on all the files on my other drives. 

Which log files will show where things went wrong during the installation? 
Is there a way of checking if this happened due to a choice I made during the installation?

---

### Post by khelben1979 on 2009-06-15
> **beukesma said:**
> Which log files will show where things went wrong during the installation?

I'm not sure, but have you looked in /var/log/term.log ? On my system I can see a lot of information in there that is related to installing and uninstalling of packages, maybe you'll find something?

One program which comes to my mind here is [SpinRite]("http://en.wikipedia.org/wiki/Spinrite"), but I'm not sure if it's what you're looking for. :-/ It's not a Linux application, I know, but it's no problem if you're running dual boot or have other solutions for running it.

---

### Post by burntwater on 2009-06-15
This link appears to hold the most hope of the lot... contains some very educational reading as well!

[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

