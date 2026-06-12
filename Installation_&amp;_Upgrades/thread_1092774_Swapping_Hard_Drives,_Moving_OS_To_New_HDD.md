---
title: "Swapping Hard Drives, Moving OS To New HDD"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by OKKARE on 2009-03-10
I need to move everything on my current (40 gigabyte :( ) hard drive to my new ("new" 80 GB) drive. This includes the the Ubuntu OS and all other files. What's the easiest way to do this?

---

### Post by upchucky on 2009-03-10
it would be great if you can run both drives at the same time, then no need to move anything. If this can not be done then back up all your important files, lets say to a cdrom, usb stick, DVD, or a second pc if you have it networked. partition the new drive with a ubuntu partition a home partition and a swap partition. swap is typically about half the size of the amount of ram on the sys. ubuntu should be happy with about 15gigs and home can have the rest for all your files. then reinstall ubuntu and then restore the backed up files to the home partition

---

### Post by OKKARE on 2009-03-10
I guess if I have no other choice...

---

### Post by Neo_The_User on 2009-03-11
Well you can do it by transferring over the partitions but I'd need a lot of info on your HDDs and writing a guide would take awhile.

Terminal:

```

man fdisk
man mount

```

---

### Post by bpalone on 2009-03-11
Another thought would be to do a complete backup with Mondo.  Information on Mondo can be found here: [http://www.mondorescue.org/](http://www.mondorescue.org/)

It appears that you can restore to a new disk of a different size.  It does require a bit of understanding how to set up a new disk from the command line though. There is plenty of information available online, but you may want another computer available so you can check such information while in the middle of the project.

Mondo is in the repository, so it is an easy install. There may be an easier method out there.

---

### Post by Neo_The_User on 2009-03-11
> **bpalone said:**
> Another thought would be to do a complete backup with Mondo.  Information on Mondo can be found here: [http://www.mondorescue.org/](http://www.mondorescue.org/)

It appears that you can restore to a new disk of a different size.  It does require a bit of understanding how to set up a new disk from the command line though. There is plenty of information available online, but you may want another computer available so you can check such information while in the middle of the project.

Mondo is in the repository, so it is an easy install. There may be an easier method out there.

Whats easier than installing it via repo? Not that I really care but I'm interested. I compile everything from source anyways.

---

### Post by bpalone on 2009-03-11
> **Neo_The_User said:**
> Whats easier than installing it via repo? Not that I really care but I'm interested. I compile everything from source anyways.

My bad construction.  I was referring to the original question of moving the system and files to a new home.  I shall be at the wall for my 40 lashings with a wet noodle.;)

---

### Post by OKKARE on 2009-03-11
Thanks for the replies. I wish I had waited for them before going ahead! I backed up all my files onto my Hackintosh.

Then this happened:

[http://ubuntuforums.org/showthread.php?t=1093081](http://ubuntuforums.org/showthread.php?t=1093081)

---

### Post by bpalone on 2009-03-29
An update for anyone reading this at a later date.

I found a mention of using a Gparted Live CD to move the system over.  I have since done this myself and it works great and is really painless.  Just use the copy and paste function in Gparted.  Don't remember the thread I found it in, but do recall mentioning to check UID and fstab (if my memory is correct).  I did not have any problems and didn't check anything other than repairing Grub.

---

### Post by combatwombat_nz on 2009-03-29
Or try the brilliant CloneZilla live cd. It is for cloning disks or partitions to another or to an image or to a network. No PC techie should be without it.

---

### Post by robert shearer on 2009-03-29
Or try making a remaster live cd of your running install with remastersys

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

Then swap drives and use the Remastersys disk to reinstall.

---

