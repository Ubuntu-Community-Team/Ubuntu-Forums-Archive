---
title: "Hardy fails to install"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Hooya on 2009-01-24
I'd been using Hardy since it came out, tried Ibex for a while and didn't like it, so I wanted to go back to Hardy using a fresh install.  I have a separate /home partition.

The Hardy install fails to complete.  I'm using the Live install CD for AMD 64 of 8.04.2

The installer gets to about 80% then crashes.  It should ask me to reboot when it's done, but it doesn't.  If I reboot I get a Grub 15 error.  There is no /boot/grub folder, although there are images in /boot.

Obviously since I"m using my own /home partition I have to do the manual partition setup.  I'm choosing to format /dev/sda1 to ext3 and format.  I've tried setting up the boot loader as (hd0) and as /dev/sda

There are no errors given during install.  I don't know how to run the install with the command line so that it gives me output...

Any ideas?  The last thing that I see on the install thing is "Creating user" when it craps out.

---

### Post by Hooya on 2009-01-24
I love how these questions usually get only a handfull of views even.  It's not like I didn't google search to try and find the answer out first.

Anyway, I eventually decided to let the installer just install its own /home directory in the / partition.  Then the installer worked fine.  After that I just deleted everything from within the newly made /home directory and set fstab manually.  I don't see why the installer can't handle it.  Of course, after that I needed to figure out how to take ownership again, which is a story for another day.

Anyway, if anyone ever looks at this post.  That's what you have to do.  Have the partitioner not use any of your other partitions, then manually edit your fstab file and adjust ownerships as needed.

---

