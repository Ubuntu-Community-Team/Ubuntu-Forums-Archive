---
title: "mozilla-acroread memory leak?"
date: 2008-09-07
forum: General Help
---

### Post by brodiepearce on 2008-09-07
Hello,

I have an ongoing problem when I open PDFs in Firefox, I'm using the mozilla-acroread plugin.

I only need to open a PDF once (in Firefox), and then eventually, over the course of a day, the acroread process will end up using anywhere between 40% and 60% of my physical RAM (Total available 1GB).  

Once this starts to happen my swap partition (I'm guessing) gets reamed for everything that wont fit into the RAM, and I have to drop to a terminal to kill the acroread process as the system becomes completely unusable as a desktop environment.

I've found a few references between acroread, mozilla-acroread and memory usage, but nothing concrete.  I found [this](http://ubuntuforums.org/showthread.php?t=754944) thread that fits my scenario pretty well.  There is a recommendation to remove ld-linux.so.2 and install lsb.  I've done this, but the problem remains.  :(

I would just switch to evince completely but that's another bag of problems.

Has anyone had similar problems to these?

---

### Post by robinl on 2009-03-15
Just a me-too post here, have also installed the lsb package and nothing changed. I'm using x64 Intrepid so perhaps it's a bug between acroread and the wrapper?

---

