---
title: "Install Partioner Doesn't Recognize Windows XP Is There"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by ufusername on 2009-03-04
I attempted to install Ubuntu on a Compaq laptop with Windows XP, as a dual boot.  Following the installation instructions on the screen, and on the Ubuntu site, I expected the partioner to allow me to shrink windows and install Ubunbtu on the created free space.  But, my install does not recognize that there is a Windows there, and insists upon installing Ubuntu on the entire partition.  The "How do you want to partition the disk?" menu from [https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall") never appears. It jumps straight from "Select a Disk" to "Ready to Install" complete with "WARNING:  This will destroy..." whereupon I had the good sense to quit, and Windows is still intact.  

I was using a Live CD that runs fine as a live cd.  Any suggestions?

Thanks.

---

### Post by solwic on 2009-03-04
> **ufusername said:**
> I attempted to install Ubuntu on a Compaq laptop with Windows XP, as a dual boot.  Following the installation instructions on the screen, and on the Ubuntu site, I expected the partioner to allow me to shrink windows and install Ubunbtu on the created free space.  But, my install does not recognize that there is a Windows there, and insists upon installing Ubuntu on the entire partition.  The "How do you want to partition the disk?" menu from [https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall") never appears. It jumps straight from "Select a Disk" to "Ready to Install" complete with "WARNING:  This will destroy..." whereupon I had the good sense to quit, and Windows is still intact.  

I was using a Live CD that runs fine as a live cd.  Any suggestions?

Thanks.

What version of Ubuntu are you trying to install?  Those instructions you found look outdated.

---

### Post by ufusername on 2009-03-04
8.10.  I assume the CD is good, since the laptop works fine with it as a live CD.

Thanks.

---

### Post by avtolle on 2009-03-04
Did you defrag the HDD before trying to begin the installation?

---

### Post by ufusername on 2009-03-04
Yes, it has been defragmented. Easeus partition manager says it has 55.86G unused on the primary partition, so there is more than adequate space to make a partition there.

I considered using Easeus to make a partition for Ubuntu, but after seeing all the forum threads about failures installing into a free partition, I'm wondering if this problems indicates that Ubuntu will still mange to hose up XP, which would bring down the wrath of the SO, who owns the laptop, upon me :D

---

### Post by avtolle on 2009-03-04
Hmm, this is XP and not Vista, right? From the live CD, open a terminal (go to the top panel, click on Applications, then Accessories from the menu, and then Terminal) and paste the output of ```
fdisk -lu
```

---

### Post by ufusername on 2009-03-04
Can't paste, it's another machine from where I'm posting, but the gist is:
Device  Boot Start End     Blocks   Id  System
/dev/sda1 *  63   156280319 78140128+ 7 HPFS/NTFS

---

### Post by avtolle on 2009-03-04
Thank you. That lets us know that there is but one partition on the HDD, which is the Windows partition. Perhaps at this point you should use the XP tool to shrink the partition and leave the remaining space unallocated, and then boot the Live CD and try to install within the unallocated space. 

I'd also suggest that another defragging session might be called for, as I suspect (but do not know) that there might still be file fragments existing on the HDD even though you've done it at least once.

---

### Post by ufusername on 2009-03-04
Thanks for the help.  I've iteratively defragmented it on several occasions, so it's not going to get any better than it is (with the Windows defrag tool, anyway).  At this point, I'll think about whether to proceed with Ubuntu or not.  Ubuntu would be 'nice but not necessary', while a hosed up Windows would not contribute to domestic tranquility, so I'll see how lucky I feel;)

---

### Post by ufusername on 2009-03-05
> **avtolle said:**
> ... as I suspect (but do not know) that there might still be file fragments existing on the HDD even though you've done it at least once.

You are correct, it turns out.  Using the Windows help sites on defragmentation ([http://www.pcmag.com/article2/0,1895,1765751,00.asp]("http://www.pcmag.com/article2/0,1895,1765751,00.asp"), among others) I finally found out that the MFT has become so fragmented on this PC that the Ubuntu partitioner doesn't find enough space to make a partition.

I don't think the Ubuntu install handled this situation very elegantly- if you aren't alert, you end up wiping your Windows without intending to do so.  But, that's computers for you, I suppose.

Based on this, I no longer believe that the Windows freebie partition tool Easeus [http://www.easeus.com/]("http://www.easeus.com/")is really telling me the truth when it implies that it can shrink the windows partition and make a free partition for me.  If Ubuntu install can't do it, can Easeus be that much more capable?  Anyway, I'm not going to do the experiment.

I wonder how many "Ubuntu ate my Windows" help pleas on this forum arise from this issue?

Thanks again to avtolle for the help.

---

### Post by betrunkenaffe on 2009-03-05
I've never had a partition that I couldn't defrag. How full is that Windows partition? Is there anything you can delete from it (without wrath) like temp/install files, trash, etc..

I've ran into an issue where I was told I couldn't defrag any further, I uninstalled a few large games I didn't play anymore and deleted my temp and somehow the defrag could magically work :P

You could also try a free defrag tool available online and see if they can do it.

---

### Post by ufusername on 2009-03-05
Thanks for the comments.  Yes, I did remove everything that can be removed without harm- a disk cleanup, in other words. And, yes, I did try the online defrag tools, including the one that Microsoft support actually rceommends.  None of them can move the MFT blocks, so by process of elimination I've found that must be what my 4 blocks of unmovable files are.

The thing I don't know is this-  one partition tool (ubuntu's) says that there is no way to partition the disk, presumably because of those MFT blocks.  Another partition tool (Easeus) says "sure, no problem, ready to do it?".  So, who's lying to me?  To this point, I've not tried the experiment to see which partition tool is correct.

I think the problem arose due to this machine's past.  It was used for a while with only 512Mb of memory, and a lot work of pictures, big files, etc. got done.  When I got to it, I added the 2GB memory to get the thing able to move, but by then the swap files and the MFT had grown several times, into a very fragmented disk.  I can get rid of the swap files, but the MFT blocks are stuck out there, so the disk is effectively unfragmentable, although there is tons of actual space between the MFT blocks.

---

### Post by betrunkenaffe on 2009-03-05
My suggestion would be to  backup everything off it (disk image) to a backup location and then try the one that says it can do it. If you have problems, restore.

---

