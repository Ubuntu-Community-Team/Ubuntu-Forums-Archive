---
title: "Problems with my NTFS formatted External Hard Drive"
date: 2007-10-08
forum: Hardware &amp; Laptops
---

### Post by pykus on 2007-10-08
I was quite impressed when my external hard drive automatically showed up on my desktop with Ubuntu, which is one of the reasons I installed it, but I can't write to it. It's mounted as read only. I did some research and found [a post about ntfs3g](http://ubuntuforums.org/showthread.php?t=217009/), and subsequently I learned that Linux doesn't like ntfs. Mostly this wouldn't be a problem, but two things make it a problem:

1) I'd change it to fat32, but I have over 300 gigs of stuff on it and I have no where else to put it while I'm working on the reformatting.

2) [Instructions for installing ntfs3g](http://ubuntuforums.org/showthread.php?t=217009/) look like they require access to at least one website, and right now I haven't yet gotten my wireless working on this laptop while Ubuntu is running. It's nice to be able to read from the drive, but it's causing problems that I can't write files to it. Am I interpreting [the instructions](http://ubuntuforums.org/showthread.php?t=217009/) correctly?

---

### Post by sdlvx on 2007-10-08
ntfs-3g should be in the repositories, but it's not installed by default, probably because it's still in development.

You can just use synaptic or adept and search for ntfs, and install ntfs-3g.  If you want to do it from the command like, you can go with.

sudo apt-get install ntfs-3g

That's it.  I can't use the regular ntfs driver, it mounts as the wrong user or something.

---

### Post by pykus on 2007-10-08
Are the repositories online? Because I ran the command you gave and it failed. I got two messages about preparing things (i forget what exactly) then it ended.

---

