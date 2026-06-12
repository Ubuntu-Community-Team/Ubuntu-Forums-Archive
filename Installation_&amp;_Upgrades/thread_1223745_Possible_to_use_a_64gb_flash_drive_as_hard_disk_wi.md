---
title: "Possible to use a 64gb flash drive as hard disk with an dell mini 9?"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by yoshiki2 on 2009-07-26
Im about to buy the dell mini 9, with 4 gigabytes. Can i use a flash drive (64 gb) or memory card (32 gb) as a hard drive? can i install programs on a memory card or flash drive?
Sorry for the noob question, but am moving from my vista laptop to a linux netbook. thx:P

---

### Post by Mark Phelps on 2009-07-26
You can certainly treat a flash stick as if it were a hard drive, by copying files to it, but it's a bad idea to install to it as if it was your primary hard drive.  Flash memory has a limited number of reads and writes.  For a data drive, this is generally not a problem, but treating it as your OS drive exposes it to almost constant use --  event logs, temporary internet files, account files, cache files, even routine updates -- all perform writes to the flash drive.

In netbooks, the caching and logging (and other functions) are turned off by default for flash drives in order to improve their useful life.

You would do better upgrading the size of the internal drive in the Dell, rather than relying on flash drives.

---

### Post by yoshiki2 on 2009-07-26
the mini 9 costs 199 with 4 gigabytes, to upgrade it to 16 gigabytes it costs 75 dollars.. not worthy i think. and is bluetooth working with ubuntu? not so sure about adding it for 20 more dollars

---

### Post by Mighty_Joe on 2009-07-27
> **Mark Phelps said:**
>  it's a bad idea to install to it as if it was your primary hard drive.  Flash memory has a limited number of reads and writes.  

I don't think so.  First, flash drives can handle a [tremendous number of writes]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html") (90.5 million in that guy's case!). Second, it's pretty simple to move the logs, cache and other busy files to tmpfs.  
I use an 8Gb flash drive to boot Ubuntu on my work laptop when I'm at home (no reason The Man needs to know what I browse).  They're less than $20.  Get one with a warranty and if it fails, send it back.  Mine's 2 months old and still humming.
See my post [here ]("http://ubuntuforums.org/showpost.php?p=7497700&postcount=4")for instructions on using tmpfs and other optimizations for flash drive installs.

---

