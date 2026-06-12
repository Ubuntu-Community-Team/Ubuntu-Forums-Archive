---
title: "Robust recursive file copy tool?"
date: 2009-03-26
forum: Hardware
---

### Post by jrowberg on 2009-03-26
I used an amazing tool for data recovery a few months back, and now for the life of me I can't find it again.  I thought it was rdd-copy, but that doesn't seem to be able to do a batch operation.  The tool I used was kind of like a robust version of rsync, where you could give it a source directory and a target directory, and it would copy each file it encountered, except if it hit a bad sector, it would immediately shrink the "copy block" size down to a user-specified number, and try to copy tiny bits of the file at a time in sequence.  After a certain number of tries, it would give up on that block, copy zeros instead, and move on to the next block.

Does anyone know what this tool is?  I haven't found the right set of google terms to locate it.  There are a lot of "bad sector" recovery tools out there, but most of them seem to be device-oriented instead of file-oriented (e.g. making a raw image of an entire drive), and I need to run it on a directory with a wildcard instead.

---

### Post by jrowberg on 2009-03-26
I'm still interested in the tool that I'm thinking of, but I found a way to use rdd-copy that will suit my needs for now.  Basically, imaging the entire drive (or partition, as necessary) onto another drive, then mounting the image.  It copies through all of the failing data very nicely.

---

### Post by bolocholo on 2013-04-15
> **jrowberg said:**
> I'm still interested in the tool that I'm thinking of, but I found a way to use rdd-copy that will suit my needs for now.  Basically, imaging the entire drive (or partition, as necessary) onto another drive, then mounting the image.  It copies through all of the failing data very nicely.

Safecopy. You can find it in Ubuntu's own repositories or here: [http://safecopy.sourceforge.net/](http://safecopy.sourceforge.net/)

---

### Post by overdrank on 2013-04-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

