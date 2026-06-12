---
title: "External Hard Drive Split (Lacie Big Disk) HELP PLEASE"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by Ezetreal on 2007-11-30
Hi, sorry for the repost, didn't know how to update the other one.

Here is my problem. For unknown reasons, my 400GB Lacie Big Disk drive's motherboard isn't powering up the drives anymore. I gave up on trying to fix it and instead got a case with the intention of accessing each 200GB WD drive separetely. Obviously windows couldn't read the drives, either one. It asked me to format them first. Out of the question, I need my data.
Better luck with linux. I could access in read and write one of my drives. The one that was set to master in the Lacie case.
I am a total newbie (n00b if you prefer ) but my guess is the second drive is missing boot sector stuff.
My drive was formatted in ntfs, i have ntfs3g installed, but the drive that did run showed up in fuseblk type.
Is there any way I can access that second drive ? I am all eyes and ready to post any log or whatever that you ask for.
I am running Gutsy by the way.

Thanks

PS: I have a lot of faith in linux and the linux community, but i haven't gotten a single reply with an attempt to help so far !! [-X !! (except for a friend of mine who tried to get the post more active by replying once)

---

### Post by crouton on 2007-11-30
If the Lacie had 2 200GB drives and you saw 400GB of usable space, the drives were 'striped' aka RAID0.  RAID0 is not recoverable under normal circumstances.  You might be able to do some tricks with GParted (filesystem tool) but it's highly likely that your data is gone.  The NTFS filesystem was created to span both physical drives as one logical drive, so the physical drives may have a different partition type setup entirely.  You could certainly try to convince the physical drive that the partition really is a NTFS partition but you need to prepare for complete data loss.

:(

[edit] The second drive isn't missing boot sector info (as that has no relevance when the drive isn't being booted directly) but it may be missing partition information like I mentioned above.  Check the drive using fdisk or GParted and see if it shows any partitions at all.  If so, see if you can change the filetype to NTFS without a format.  Dicey but you've been pretty lucky so far with the first drive.

---

### Post by Ezetreal on 2007-11-30
I'll try and see what I can do with Gparted, I might post back to ask the details of how to do all that if I can't figure it out.

Thank you for responding, hopefully i'll get lucky again.

---

### Post by Boule on 2007-12-03
You might want to read this topic about gparted and ntfs...
[http://ubuntuforums.org/showthread.php?t=96617](http://ubuntuforums.org/showthread.php?t=96617)

You might also find more useful ones, but that's the first one I got when searching.

I wouldn't recommend doing that though, I think your best chance of recovering your data is connecting your 2 drives to the RAID controller they have. Since the drives aren't powering up, maybe it's just the power that's busted, but the board can still be working, so you can maybe try powering the drives with an external source, like regular molex connectors...

---

