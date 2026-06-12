---
title: "GRUB Issue Fedora 9 Windows Vista Dual Boot"
date: 2008-08-20
forum: General Help
---

### Post by Mohnki on 2008-08-20
Good evening guys.

I'm pulling my hair out at the moment over a GRUB boot problem I am having... 
I installed Fedora 9 on my laptop that has Vista Business on it. It  ran perfectly until today. I saw that the drive that i had partitioned from a 150gig split into a hundred and a 50. Fedora is on the 50... Well was... I saw today that my partition had gone back to being 150gigs and my fedora partition was gone. I have no idea how that happened but now when i boot up my PC I get this:

GNU GRUB version 0.97 (619K lower /2095808K upper memory)

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename.]

grub>

I am writing this off of a sceond PC as i can go no further. Is there a command i can use to get it to boot into Vista without having to reinstall? I need a temp fix to get my data and i'll reinstall fedora as soon as i get my DVD back...

Any help would be greatly appreciated.

---

### Post by louieb on 2008-08-20
Doesn't sound like your Fedora partition is gone. Why do you think it is gone? What program showed you that?  What you are seeing is the grub prompt. and the grub stage2 program is somewhere in your Fedora install.

By default Fedora doesn't install itself like Ubuntu. Last time I played with it it created a separate /boot and put the the rest of it on a different partition with LVM. (Fedora 5).   

Anyway guess you don't have a VISTA CD? If you do try restoring the MBR to boot windows with it.   Boot in recovery mode and run the **fixmbr **command.

Or try a [Super Grub Disk ]("http://forjamari.linex.org/projects/supergrub/") and see if it will fix your boot problems.
Good Luck.

---

### Post by Mohnki on 2008-08-20
ok after 3 hours of lokking this up i found this:

[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

Worked for me...

---

