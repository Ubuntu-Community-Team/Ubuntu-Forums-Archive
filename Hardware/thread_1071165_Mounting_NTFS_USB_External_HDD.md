---
title: "Mounting NTFS USB External HDD"
date: 2009-02-15
forum: Hardware
---

### Post by Ome Knomee on 2009-02-15
Hey guys, 
           I have recently installed Ubuntu 8.10 and I have a Fujitsu 40GB External Harddrive and when I plug it into the USB Ports it comes up with 'Unmountable Volume'. All i would like to do is get the files off my Harddrive so I can listen to my music.

Can anyone please give me a list of things that I need to do to get it working? 

Thanks 
Ome Knomee

---

### Post by MarblePanther on 2009-02-15
Try going back into windows and safely remove it, then try in linux again.

If you just yank it out in windows instead of safely removing it, this can happen.

It could be another problem, but try this first

---

### Post by Ome Knomee on 2009-02-15
Hey, I do not have access to a Windows Computer. I sold my Windows laptop and now I am using Ubuntu on another laptop. Is there any other way of fixing this apart from unmounting in Windows?

Thanks

---

### Post by MarblePanther on 2009-02-15
What filesystem is it using?  (NTFS, FAT, EXT3, etc...)

What OS was running on the last computer it was plugged into?

---

### Post by Ome Knomee on 2009-02-15
The External Hard Drive is in NTFS Format and the last computer that the External HD was plugged into had Windows XP on it (my mates computer up north).

---

### Post by MarblePanther on 2009-02-15
I'm assuming this is a "safely remove" issue (this happens all the time)

My advice is to find a friends computer to plug into, or take it to a computer store and plug it in and safely remove.

---

### Post by Ome Knomee on 2009-02-15
Ok. Thank you for your help :)

---

### Post by MarblePanther on 2009-02-15
You can also download the windows 7 beta and use that to safely remove...

---

### Post by Ome Knomee on 2009-02-16
Hey i havent been able to get onto a windows computer and i dont think i will be able to get on one before i move to australia. Is there any other way that i can mount my HD?

Thanks

Ome Knomee

---

### Post by vanadium on 2009-02-16
An unclean drive can be mounted anyway with the force option, at the risk of the user. This is a good option if all you want to do is copy the data to another drive and then reformat the drive to ext3. If you do not plan to use that drive on a windows system, you should do that anyway.

There is also the ntfsfix utility, which is part of the ntfsprogs tools "ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS consistency check for the first boot into Windows."

---

### Post by Acradon on 2009-03-31
Thank you Ubuntu Forums. Another problem solved. 

@Vanadium

Will the ext3 format not work on windows? I use my drive for both operating systems (laptop has XP...sigh).

Acradon

---

