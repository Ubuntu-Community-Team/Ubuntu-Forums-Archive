---
title: "Installing Without a CD"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Quin452 on 2009-01-17
Hi

I've used Ubuntu before, however I installed it on my harddrive alongside another Linux OS with the paritions locked off.
So, I just deleted my entire set of partitions whilst logged on (rather dangerous I found out).

Anyway, this was no major worry as I was just playing around with my harddrive, but the CD I used has since stopped working, it takes ages to load and when it does, it does not allow me to input data (the input fields are disabled or something).

So, what I've done is re-installed Windows XP - I need it for my course, but I also want Ubuntu back on.
I have set my harddrive in three partitions: Windows, Ubuntu, Storage (for all my files); I hope to access Storage so I can work with files in either OS, which will be the only communication between the two OS.  I have also around 15GB of unallocated HD space.

Anyway, so my question is, how do I install Ubuntu to its designated partition without needing using a CD?
I have no trouble in using a CD, except it is a waste, but also it will give me something to learn :)

Many Thanks

---

### Post by boof1988 on 2009-01-17
I have used unetbootin to put a bootable desktop iso on my hard drive.  It worked okay with Ubuntu 8.04.1 (for me).  The "CD integrity check" the "use without any changes to your computer" and "install" seemed to work okay.  I couldn't get it to work with Ubuntu 8.10... Can't remember the exact problem though.

My computer still has the partition with the installer (Ubuntu 8.04.1 Desktop) on it.  I haven't figured out how to boot to the partition using GrUB so I just reload the boot-portion of the MBR when I want to run the installer instead of the OS.  I like to do a lot of experimenting so it's nice to have installer on the HDD. It only takes (on my faster machine) about 6 min for the installer to do all it's read/write/configure.

I'm sure there are other ways that require more knowlwedge/capability but I haven't learned them yet.  There are a couple other threads on this but  I can't remember how to search for them.

Hope this helps a bit.

Edit:  [Here's](http://ubuntuforums.org/showthread.php?t=1035799) a link to one of the other threads I mentioned.

---

### Post by Quin452 on 2009-01-18
Hi

Thanks for the reply.
I have tried UNetBootin thing, however I do not know how to use it :)  It gives me the option of the C drive and the A drive... but also I can choose one of the other partitions when I go 'advanced' although I have no idea.
I tried with the partition, but as said, I don't know.

So, I'll do some research in how to use it, unless someone tells me over here :)

---

