---
title: "Unwanted automount of old filesystems"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by ratioswitch on 2007-08-01
First time caller, long time listener ...

I have a new Dell Inspiron E1505n that came from Dell with only Ubuntu installed. I'm new to Linux but I do have some programming experience. I wanted to install Ruby on Rails but hosed a bunch of different things during the installation of the numerous required pieces. Since I got this laptop to experiment with I simply started over by reformatting the hard drive and reinstalled Ubuntu. I've done this twice now.

Now I have 3 extra "drives" that show up in the left column of my Ubuntu File Browser. One called "OS", another called "os_part", and a third called "os_part_". I still have a "drive" called "File System" that I'm positive is the current file system being used. I also have another drive called "DellUtility" that I believe is to be used for the MediaDirect feature (which does not work anyways).

Clicking on any of the following (OS, os_part, or os_part_) asks for my admin password and them mounts the drive so that I can see it's contents. OS and os_part both had vmliunz within but os_part_ had a Grub folder.

Do I need these, what seem to be, extra drives?
How do I get rid of these 3 extra automounted drives?
How do I prevent the created (or saving) of these extra drives when I want to do a clean install again?

Thanks,
_rs

---

### Post by ratioswitch on 2007-08-13
Based on another of my forum threads ([http://tinyurl.com/22co7n](http://tinyurl.com/22co7n)) I was able to figure this issue out as well. Yeah, no more auto-mounting partitions!

_rs

---

