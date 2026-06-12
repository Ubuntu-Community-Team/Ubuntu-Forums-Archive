---
title: "Dual Boot With XP:  No &quot;Side by Side&quot; Option!"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by Topher88 on 2009-11-08
I'm trying to install Karmic on my girlfriend's computer which is running XP, and I would like to set up a dual boot.  I am supposed to see an option to install Windows and Ubuntu side by side, but all I see is this:

[ATTACH]135411[/ATTACH]

Every source I can find says that this should only happen if you don't have enough space or if you haven't defragged...  Well, there are 200G of space on her drive, and she's used up maybe 30 or 40 of that, so space is no problem, and before the installation, I ran scandisk, disabled paging (because that's caused a problem with me before), and then defragged.  So what is the deal??

---

### Post by AW36 on 2009-11-08
i might be wrong... but its probably those unmovable system files.

---

### Post by Topher88 on 2009-11-08
> **AW36 said:**
> i might be wrong... but its probably those unmovable system files.

Right.  I had a problem with that when I tried to install Jaunty on my own desktop with XP, and I was instructed to disable paging and then defrag, which solved my problem that time.  I did the same thing this time, however, and to no avail.

Is there something ELSE I need to do other than disabling the paging file??

---

### Post by AW36 on 2009-11-08
i've tried this many many times before... and i must say the only thing that worked for me is to reformat, install windows, then ubuntu.

---

### Post by Topher88 on 2009-11-08
> **AW36 said:**
> i've tried this many many times before... and i must say the only thing that worked for me is to reformat, install windows, then ubuntu.

Mmm, great...  Her brother built this computer (or helped build, or bought it from someone who built it, not quite sure) a long time ago, I highly doubt he still has the original Windows CD.  Oh well, she doesn't really NEED Ubuntu on here, if it's going to be a huge ordeal...

---

### Post by rich97 on 2009-11-08
You need to partition the hard drive. It's not because the drive is full, it's cause that portion of the hard drive is specified as the XP partition, and that is a fixed size. You have to manually resize the XP partition to the allow Ubuntu to create it's own EXT4 partion.

I already wrote up instructions on preparing your drive for dual boot [here]("http://ubuntuforums.org/showpost.php?p=8240563&postcount=25")

Edit: I assume you know about partitioning in that case... Can't you even manually partition? I've never seen a side-by-side option.

---

### Post by Topher88 on 2009-11-09
> **rich97 said:**
> You need to partition the hard drive. It's not because the drive is full, it's cause that portion of the hard drive is specified as the XP partition, and that is a fixed size. You have to manually resize the XP partition to the allow Ubuntu to create it's own EXT4 partion.

I already wrote up instructions on preparing your drive for dual boot [here]("http://ubuntuforums.org/showpost.php?p=8240563&postcount=25")

Edit: I assume you know about partitioning in that case... Can't you even manually partition? I've never seen a side-by-side option.

It does have the option, I used it the first time I installed Ubuntu.

And yes, manually partitioning was my next thought, so I tried it out with Gparted live and found out that, for some reason, Gparted cannot read the information on the windows partition, therefore does not give me any indication of what space is used and isn't, and also will not let me shrink it.  However, I can expand it to fill in the 8MB of unallocated space, but I don't think that would do me any good...  lol.  

I also just initiated a second defrag, and all problems still persist.  So, basically...  For some reason, I am not able to shrink down the Windows partition by any means at the moment.

Any ideas??

---

### Post by plusnplus on 2009-11-09
Hi Topher88,
if i'm not wrong, have bad sector in harddisk also will make same problem during instalation.

---

### Post by Topher88 on 2009-11-09
> **plusnplus said:**
> Hi Topher88,
if i'm not wrong, have bad sector in harddisk also will make same problem during instalation.

Is there any way that I can find out if that is the case, and if it is, what can I do?

---

### Post by plusnplus on 2009-11-09
Hi Topher88,
I dont know how to check bad sector in ubuntu.
in win xp, you just defrag or scandisk. it will show the bad sector(if have).

As i know there is nothing you can do if the harddisk have a bad sector. Mean, just buy another harddisk.

---

### Post by Topher88 on 2009-11-09
> **plusnplus said:**
> Hi Topher88,
I dont know how to check bad sector in ubuntu.
in win xp, you just defrag or scandisk. it will show the bad sector(if have).

As i know there is nothing you can do if the harddisk have a bad sector. Mean, just buy another harddisk.

Oh, okay...  Well, I did both of those things, and all it shows are the normal non-movable files, contiguous files, free space, etc.  Judging from the refrag report, everything looks fine...

---

### Post by Topher88 on 2009-11-09
Well, I'll probably just not worry about it...  It's really not worth all of the fuss, she doesn't really even want Ubuntu, anyway.  I just really wanted to see what a fresh install of Karmic would look like.  :-( oh well...

---

### Post by wilee-nilee on 2009-11-09
Resize the XP partition leaving a open space for Linux, but make sure the live cd is not corrupted, the side by side and slider for adjusting the partition sizes is always there. If your sister doesn't  want it then leave the cd to try out it may give her a chance to see the benefits of dual booting.

---

### Post by Topher88 on 2009-11-09
> **wilee-nilee said:**
> Resize the XP partition leaving a open space for Linux, but make sure the live cd is not corrupted, the side by side and slider for adjusting the partition sizes is always there. If your sister doesn't  want it then leave the cd to try out it may give her a chance to see the benefits of dual booting.

Manually partitioning doesn't work as of yet, see above posts.

UPDATE:  I've just realized that I'm a dummy, and didn't actually disable paging like I thought I did, so...  I will do that and initiate yet another defrag, and retry the installation again tomorrow.  Might not make a difference at all, but I'll let you know what happens!

---

### Post by Topher88 on 2009-11-09
Success!

Keeping in mind what someone said about bad sectors, I ran another scandisk and, this time told it to repair bad sectors if possible.  After that, I disabled paging, ran another defrag, initiated the install, and voila!  The side by side option was available!  The installation is taking place as I type this.

Thanks, everyone!

---

### Post by wilee-nilee on 2009-11-09
> **Topher88 said:**
> Success!

Keeping in mind what someone said about bad sectors, I ran another scandisk and, this time told it to repair bad sectors if possible.  After that, I disabled paging, ran another defrag, initiated the install, and voila!  The side by side option was available!  The installation is taking place as I type this.

Thanks, everyone!

That gives me a warm fuzzy feeling, good job on using the forum for help. ;)

---

