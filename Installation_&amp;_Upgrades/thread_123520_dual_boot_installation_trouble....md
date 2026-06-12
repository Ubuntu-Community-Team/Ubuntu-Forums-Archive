---
title: "dual boot installation trouble..."
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by asinsh on 2006-01-30
I've got a pc running winXP and I figured I'd give ubuntu a shot (dual boot).  

My pc has two HDs but I wanted to reserve the second one for backup so I decided to try to install ubuntu on the same HD as XP.  XP had the only partition on the drive so I tried to resize XP's partition and found out too late that resizing it kills the stuff inside it (where is partition magic when you need it?).  However except for that 'little problem' the installation worked perfectly and on reboot grub allowed me to boot into either ubuntu or a nonexistant XP (ubuntu worked fine).

So, I fugured I'd start from scratch and I therefor wiped the HD clean and partitioned it into three partitions: first partition 150GB ntfs for XP, second partiion 50gb for linux (set for fat32 but I figured the ubuntu installation program would reformat that partition in ex when the time came) and third partition 100gb fat32 so I could share files between the two o/s's.

I then installed XP in the first partition and got it up and running.  Finally, I ran the ubuntu installation cd but I keep running into problems this time around.  It takes me to a guided partition task but I don't want to do any of the things it is asking me to do.  I tried to do it manually but when I thought I was asking it to format the second partition it didn't work right and messed up my XP installation again.

I figured that since I had not told it to do anything at all to the first partition where I had put XP that the problem was simply a MBR problem.  So to go back to where I was, I used an XP disk, went to the console recovery mode and tried fixmbr.  That didn't work at all...when I tired to boot it told me no valid o/s.

So, once again I wiped the drive clean, set up three partitions on the HD, loaded up XP on the first partition and I am now totally ready to install ubuntu.  But I really don't want to mess up again.  Any guidance on what I should do now that I have XP in the first partition (ntfs) and two other fat32 partitions and I am ready to try to ireformat the second one and nstall ubuntu on it?

---

### Post by Finncannon on 2006-01-30
Try looking at this page: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It's very helpful.  It worked for me.

---

### Post by asinsh on 2006-01-30
[QUOTE=Finncannon]Try looking at this page: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It's very helpful.  It worked for me.[/QUOTE]

That does look extremely helpful...thanks.

I can see from that guide that it recommends manually editing the partition table rather than 'resize master and use freed up space'.  When I started this process with my old and very well tweaked XP installation I used the 'resize master' alternative and to my surprise it killed XP (I had thought that option would just resize without hurting what's inside).  I guess manually editing the partition talbe is the way to go.  I'll post back here once I've given it a try.

---

### Post by asinsh on 2006-01-30
Just to avoid other people getting misled by me, I see from reading that guide that the resize master option is supposed to leave the stuff that was on the original partition entact so that if you start with an XP installation on the partition and you use that option it should not kill that installation.  As I mentioned earlier, I did manage to hose my XP installation so I must have done something wrong there, and going forward I'm going to use the manually edit partition table option anyway.

---

