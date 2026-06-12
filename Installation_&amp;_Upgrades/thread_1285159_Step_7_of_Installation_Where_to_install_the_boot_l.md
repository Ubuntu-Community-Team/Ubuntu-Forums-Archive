---
title: "Step 7 of Installation: Where to install the boot loader?"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2009-10-07
Ubuntu 9.04

Sighhh...
Apologies in advance; concise this ain't. :oops:

A few weeks ago, I inadvertently made my Ubuntu installation useless (don't ask) and have since made 4 attempts to reinstall it.  Some preface, however:

Before initially installing Ubuntu (in April), I inserted the CD into the drive and allowed it to install some boot wrapper; since then, whenever I boot Windows (even before I installed Ubuntu) I get a menu asking if I wish to boot Windows XP (my installed Windows) or Ubuntu.  After I successfully installed Ubuntu, when I got this menu and chose Ubuntu, it gave me the GRUB menu: Windows or one of 3 flavors of Ubuntu boot.  I believe that initial menu has saved me from a booting disaster, but I get ahead of myself...

I saved the screen shots as went along so I can show them here.   I have 2 hard drives; my main boot drive, seen as /dev/sda, with 200 GB and 3 partitions, as well as a 320GB USB drive, /dev/sdb, with 4 partitions.  At installation time, it is not my intention to do anything with the USB drive.  Hence, when prompted with the box in attachment "step4a-of 7.png" you see I have chosen [Yes].

(As an aside, sorry about the attachments; I would prefer to insert the images into the message body but I the "Insert Picture" tool seems to allow only for a URL, not a local file.)

Since I need my XP partition, I choose manual partitioning.  (See Step4b-of7.png) I have already used the Live GRUB CD to partition this drive into the 3 partitions you see in Step4c-of7.png:
[LIST=1]
[*]The original XP partition
[*]The designated SWAP space, to be mounted as /swap
[*]The main Ubuntu partition, to be mounted as /
[/LIST]

(Due the old BIOS on my dinosaur box, I have a max of 4 partitions and none may begin past 128GB on the drive.)

In any case, I muddled my way through to step 7 and clicked [Advanced]. Referring to attachment Step7e-of7.png, you see that I have chosen to install the boot loader in the root partition. In the little panel that now reads /dev/sda3, the default was (hd0). Here is the kicker, in two parts:

[LIST=1]
[*]When I chose the default (hd0), it appeared to succeed but when I reboot the box, I do not even get a boot menu. Instead, I get this message on the black screen:
> GRUB loading Stage 1.5
GRUB loading, please wait...
Error 18
I had to use the gparted Live CD to recover my MBR.
[*]When I choose /dev/sda3, it succeeded as well, it would have you believe.  However, when I booted this time, I meet that familiar XP or Ubuntu menu I described in the preface. If I choose XP, all is well (Thank G-D!) But when I choose Ubuntu, expecting the 4-part GRUP menu, I get another black screen with some information (more than I cared to copy after midnight) but essentially:
> GRUB4DOS 0.4.4 2008-10-27 ...
grub>
[/LIST]
So I believe I have a complete Ubuntu installation that is inaccessible because the GRUB boot menu script cannot be found.

My only choices for the location of the GRUB appear to be:
[LIST]
[*]On the XP partition, /dev/sda1, which makes me fear for the MBR.
[*]On the hard drive before partitioning, /dev/sda, a similarly scary prospect.
[/LIST]

Anyone (who has slogged through this tome) able to supply me with an idea of how to proceed from here?  Try again, choosing /dev/sda in step 7?  Or is there a way I can locate the menu script (probably in /boot/grub, accessible if I boot the Ubuntu CD) and make it accessible at boot time?

Thanks much.

(Whew!) ](*,)

---

### Post by oldos2er on 2009-10-07
So, your Wubi installed Grub4dos boot loader is overwritten by grub from the later installation, but can't boot properly because of an older BIOS.

 [B]Grub error 18 refers to the limitations of your BIOS: 

Selected cylinder exceeds maximum supported by BIOS.

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

[/B] Have you checked if there is a BIOS update available for your computer? Or, you could create a /boot partition within the 128GB limit, and allow grub to overwrite your MBR.

---

### Post by rpaskudniak on 2009-10-07
oldos2er, I think you may have just tickled the main difference between the current partitioning scheme and the scheme where it had worked, in the installation I damaged.

The previous installation was partitioned as follows:
[LIST=1]
[*]/dev/sda1: 100GB Windows (NTFS) partition
[*]/dev/sda2:  20GB root partition (ext2 or 3
[*]/dev/sda3:   4GB swap partition
[*]/dev/sda4:  74GB or so partition for the rest of the disk, ext3 or course. I think I mounted /var there.
[/LIST]

Old BIOS -> that's it for partitions on main drive.

Thus, if the boot loader was in /dev/sda2, it had to be within the 128GB limit of the BIOS.

This leads me to question: Why in *&^%$@! would the boot loader be placed at the end of the partition rather than at the beginning.  Regardless of the answer, if that's the way it is, I just have to live with it.

So, what ***would*** _y'all_ mount in a 74GB partition?  /opt? /var? /home?  And no, it will not work to create an extended partition there with these sub-partitions. Been there, done that. If any of the extended partitions begin past the 128GB mark, the box won't boot.  (No BIOS update has been available for the past 8 or 9 years. :(  )

Plan: Revise the scheme again to 3 Ubuntu partitions (including /swap). Arbitrarily (unless I get reasonable-sounding advice to the contrary), I will mount /var on the 74GB partition.

When I start posting on the perl and postgres newsgroups/forums again, I'll be in business! :guitar:

Thanks much!

---

### Post by rpaskudniak on 2009-10-07
Whoops oldos2er, There was a remark in there I failed to address:
> Have you checked if there is a BIOS update available for your computer? Or, you could create a /boot partition within the 128GB limit, and allow grub to overwrite your MBR.

Questions:
[LIST=1]
[*]With such a low limit on partitions, why would I expend one on a separate /boot partitions?
[*]Suppose I go that way, how large should said boot partition be? A couple of MB? 1GB? Unlikely to need that much, of course, but I am currently ignorant on this issue.
[*]As to overwriting the MBR: I think I did that when I chose the default hd0 (or was that hd1?) to locate the boot loader.  Perhaps it would this time because the bootable partition (be it / or /boot) would all lie within the 128GB limit.  In any case, I still have the question: Do I install the boot loader in hd0, /dev/sda (the drive at a lower level than the partitions; probably not), or /dev/sda1, the XP partition?
[*]Why did it fail to dual boot when I installed the dual loader in the / partition (that was /dev/sda3). It's a safe bet it would still not work if I were to choose the root partition for the dual loader. I'd really like to understand why that is.
[/LIST]

Thanks ever so much for the advice.

---

### Post by oldos2er on 2009-10-09
Linux doesn't require primary partitions (nor does its swap); it's perfectly happy with extended logical ones.

 The idea of having /boot within a certain size range is to overcome the limitations of your BIOS. 

 If I were you, I'd let grub install to the MBR. One thing that may be confusing you (or me!) is that there are two parts or "stages" to grub; one resides in the MBR (by default), then the MBR passes on the rest of the boot process to /boot/grub, or to Windows, whichever you choose. As you saw, if you install grub 1st stage to your Ubuntu partition (instead of the MBR), you will then require some other boot loader in the MBR that can point to grub.

 I hope I'm not confusing the issue for you. 

 More info on grub here: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by rpaskudniak on 2009-10-11
oldos2er (AKA Ann),
One question remains after your recent explanation. To install the boot loader in the MBR, do I choose:
[LIST]
[*]/dev/sda (which I guess covers the whole drive) but may be just another alias for (hd0) - and I have already had to repair the MBR from that.
[*]/dev/sda1 - the XP partition.
[/LIST]
At this point, I am quite the [IMG]http://robshearer.com/blog/wp-content/uploads/2009/03/chicken.jpg[/IMG] about messing with the MBR. :redface:

And since I have already messed this up a couple of times, I might request of the nice folks performing this feat (probably before breakfast ;-)  ) that the install process not present me with non-viable or useless choices in the menu.  Feature request for 9.10?

Thanks much for the advice so far.

BTW, reading the grubHowTo doc you referenced, there is one cute reason I have not opted for a /boot partition:  How big do I make it?A fe hundred MB? 4GB? Larger? Something in-between?  Now that I have asked the question, I will start searching the forums for replicants.  But I wanted to get it out of the way.  Now I think it *may* be the way out of the little mess.

This is not getting simpler!

---

### Post by oldfred on 2009-10-12
Why do you not go back to the partition scheme that worked?
The previous installation was partitioned as follows:
[LIST=1]
[*]/dev/sda1: 100GB Windows (NTFS) partition
[*]/dev/sda2:  20GB root partition (ext2 or 3
[*]/dev/sda3:   4GB swap partition
[*]/dev/sda4:  74GB or so partition for the rest of the disk, ext3 or course. I think I mounted /var there.
[/LIST]
I would not put /var in sda4. I would make it either /home or a /data where most of your data goes instead of /home. All the other /var,/boot,/usr etc are for server installs or where very experience users are testing or want special software with unique requirements. The average user is fine with everything in root (/). Some suggest a separate partition for /home so when you install a new update you can do a clean install without losing all the settings & data in /home. I like a separate /data for most data and /home only has settings & hidden settings to backup.

If you have your partitions set up with a gparted liveCD you can use the manual install in Ubuntu but you have to tell it which partition is root and swap. If /home is separate you also have to specify it as part of the manual install. Grub should be installed in linux sda or  hd0 in grub which is the MBR, master boot record that the BIOS immediatly goes to.

If you were starting from scratch I also would recommend a separate /boot as the first partition, but renumbering and moving partitions around at this point is a lot of work for not much gain.

---

### Post by rpaskudniak on 2009-10-14
Oldfred,
I didn't quite return to the original layout because I felt it was not that important.  As it happens, the layout now is:
[LIST]
[*]The 100 GB NTFS (Windows-XP) partition
[*]4GB Swap space
[*]20 GB root space
[*]74GB space mounted as /home.  (I had to sacrifice some reasonableness.)
[/LIST]
I did set the boot loader in /dev/sda at installation time and that seems to have done the job.  I could probably have succeeded the same with only the 4GB /swap and the 94GB root but paranoia had already led me to keep the root entirely within the 128GB limit so it's staying that way now.  BTW, both mounted partitions are ext3 now.

I would like to mark this thread SOLVED but I don't see an icon or other widget to make it so.

OK, on to other threads and warts. (I have discovered a few already. :twisted:  )

---

### Post by louieb on 2009-10-15
> **rpaskudniak said:**
> ... paranoia had already led me to keep the root entirely within the 128GB limit so it's staying that way now.  BTW, both mounted partitions are ext3 now.

I would like to mark this thread SOLVED but I don't see an icon or other widget to make it so...OK, on to other threads and warts. (I have discovered a few already. :twisted:  )

lol - thats the safe and sure way to deal with grub error 18. 
Anyway yo mark as solved - click on **thread tools > solved**

---

