---
title: "External HD renaming"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by divineleft on 2006-10-01
I have an external hard drive, Western Digital "My Book", that I use mainly for storing music, pictures, and programming sources/applications.

Basicly it comes down to this: Whenever I drag a file from the drive into a terminal to run it, it doesn't work because the name of the drive has a space ("M_y B_ook"). The only way to get around this is to either cd to the directory or add a "\" to the path which is extremely annoying.

I was wondering if there is any way to rename it so that there is no space? Thanks.

---

### Post by kidders on 2006-10-01
Depends on the filesystem. For instance, if you were using ReiserFS, you could do a **reiserfstune -l "MyBook"** to relabel it. (See man reiserfstune for details.)

---

### Post by divineleft on 2006-10-01
How would I know if I had a ReiserFS file system?

I tried it but I couldn't figure out how to use the label things with reiserfstune.

---

### Post by kidders on 2006-10-01
> **kidders said:**
> if you were using ReiserFS, you could do a **reiserfstune -l "MyBook"** to relabel it.

You can check what filesystem you're using in a number of ways:

[LIST]
[*]You probably formatted it, so you might remember :confused:
[*]See what **mount** says the filesystem type is
[*]See if there's a reference to it in /etc/fstab
[*]Make **cfdisk** or another disk partitioner tell you what filesystem is on that particular partition.
[/LIST]

My ReiserFS suggestion was only meant as an example of how you would generally relabel filesystems. It's just a matter of a single command :-)

---

### Post by divineleft on 2006-10-01
Mount:
> /dev/sda1 on /media/My Book type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid =1000, gid=1000, umask=077, iocharset=utf8
haha, I didn't know what you meant. Sorry, I just installed ubuntu today. It's a fat32.

There's no reference to it in fstab though. I ran a search and I was wondering if changing the mount point thing would make a difference? If so I have no idea how to do that.

---

### Post by kidders on 2006-10-01
Oh my... you're *that* new to Ubuntu?! Sorry.

Changing the mount point would be just as effective, but if you'd prefer to just tweak the label, **mlabel** is the utility you want. It's specifically for MSDOS filesystems.

**man mlabel** will give you more information.

---

### Post by divineleft on 2006-10-01
> **kidders said:**
> Oh my... you're *that* new to Ubuntu?! Sorry.

Changing the mount point would be just as effective, but if you'd prefer to just tweak the label, **mlabel** is the utility you want. It's specifically for MSDOS filesystems.

**man mlabel** will give you more information.

I really appreciate the help.

But, when I run mlabel in a terminal it says:
> bash: mlabel: command not found
and there is no manual for it either. Can it be downloaded or does it come with a specific shell?

---

### Post by kidders on 2006-10-01
You probably need to install the package that contains the mlabel app. Do a **sudo apt-get install mtools** or install **mtools** however you would usually do it. That should sort you out :-)

---

### Post by divineleft on 2006-10-01
Awesome, thanks. Now i've got mlabel but I can't figure out how to use it (sorry :(). it's on sdb1 and the name right now is "My\ Book".

---

### Post by kidders on 2006-10-01
Hey again,

There is a fairly thorough post on using mtools already on this forum at [http://ubuntuforums.org/showpost.php?p=897856&postcount=10](http://ubuntuforums.org/showpost.php?p=897856&postcount=10). Have you seen it? For some reason, mtools is a bit more complicated to use that the equivalents for other filesystems.

---

### Post by divineleft on 2006-10-01
> **kidders said:**
> Hey again,

There is a fairly thorough post on using mtools already on this forum at [http://ubuntuforums.org/showpost.php?p=897856&postcount=10](http://ubuntuforums.org/showpost.php?p=897856&postcount=10). Have you seen it? For some reason, mtools is a bit more complicated to use that the equivalents for other filesystems.

It worked! Thanks so much!

nice.

---

### Post by kidders on 2006-10-01
No problem :-)

---

