---
title: "Partitions recommendations?"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by busgeek on 2006-07-12
Hi.  I want to put Ubuntu as a dual boot with Windows XP on my laptop - a Dell D600 with a 40Gb HD.

Any recommendations?
What file-system types should I use?  
How do I get them/format them?
Is it best to have a separate / and /home partition?
Can I have a shared partition? (To be used from Linux & XP?)

Thanks!

Howard

---

### Post by Dr. Nick on 2006-07-12
> **busgeek said:**
> Hi.  I want to put Ubuntu as a dual boot with Windows XP on my laptop - a Dell D600 with a 40Gb HD.

Any recommendations?
What file-system types should I use?  
How do I get them/format them?
Is it best to have a separate / and /home partition?
Can I have a shared partition? (To be used from Linux & XP?)

Thanks!

Howard

What file-system types should I use?
[B]ext3 is the default I think, It should suffice

[/B] How do I get them/format them?
[B]All done from the installer
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

[/B] Is it best to have a separate / and /home partition?
[B]I would do this, incase the system has to be reinstlalled you can keep your personal files/settings as long as you dont format the home partition


[/B] Can I have a shared partition? (To be used from Linux & XP?)
[B]You can make a fat32 partiton, both ubuntu and windows can read/write to it. Dont do a ntfs because linux cant write to it.
You could do one ext2 as their are windows programs you can get to write to ext3

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)
[/B]

---

### Post by busgeek on 2006-07-12
And any thoughts on how big I ought to make the partitions?
How much would I need for root?

I'm thinking a 40Gb drive ought to be something like...

Linux Root : EXT3                         10Gb
Swap       : ?                             2Gb
Home       : FAT32                        20Gb
Windows XP : (whatever is already there)  18Gb

---

### Post by Tao-Tao on 2006-07-12
Hi,

There are quite extensive guides - also from Community Ubuntu Documentation - for your questions which I found in around 60 seconds... ;)

But first my personal opinions before I cut and paste the links.

If the hard drive is empty, install XP first.  Then you don't have to resize the ntfs partion later on when you install Ubuntu.  Don't worry about other partitions at that point.

After that install Ubuntu.  The graphical installer makes and formats you the partitions you want during the installation.  It is really easy. ( if it works )

Things to consider: You can read NTFS from Ubuntu but not write.  You can't generally read linux partitions from XP as such.  You can solve the problem of moving files from Ubuntu to XP by

A) Using USB-stick  
B) Making an extra partition - say 1 Gb - with FAT32 filesystem which can be read by both sides
C) depending by what filesystem you use on your Ubuntu  with certain windows programs ( i.e. Reiser file tool etc. )

I'd suggest you to make atleast these partitions:
/boot ( say 50 Mb, ext3 )
/swap ( 2 * your RAM, no filesystem as such )
/     ( the remaining, I use Reiserfs - just remember to add "noatime and notail" -options to /etc/fstab, but I haven't really tried ext3 or xfs so, that's just a suggestion )

the Advantages of separate / and /home are naturally that you can install the system without the need to backup your ~.  As you're highly unlikely to make big compiles with Ubuntu free space in the compiling partition is not an issue.  Also with separate partitions if some program crashes and writes the disk full, it's just that partition.  Those are the reasons I can quickly come up with.

Here's the Windows Dual Boot help
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by Tao-Tao on 2006-07-12
Your division adds up to 50 Gb...

But I'm pretty sure that with 10 Gb for / you'll never run out of space.
I have now pretty much everything I need installed, and it takes 'round 3 Gb.

IM(H)O Don't use FAT32 for your home.  FAT is an obsolete filesystem for such use, wastes space etc. etc.,

Plus Journaling filesystem makes your life just so makes nicer.
[Wikipedia]("http://en.wikipedia.org/wiki/Journaling_filesystem") 


If your XP is already there you get to learn the joy of resizing NTFS... :(

---

### Post by busgeek on 2006-07-12
I'm sure I'll find my way round the documentation soon!
I'll go and read up on it...

Thanks for the pointers though!

:)

---

### Post by Tao-Tao on 2006-07-12
No problem, I'm glad if I could help.  It is just that usually the existing Wikis and Howtos are easier to read and better written than what I can come up with.  ;)

Here's a [chapter]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4#doc_chap4") from Gentoo Linux's handbook.  You can pretty much ignore all of it, but read 4.b and 4.d.

Here is the link to [Ubuntu Installation Docs]("https://help.ubuntu.com/community/Installation")

---

