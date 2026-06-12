---
title: "Formatting Harddrives (newbie question)"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by Panhead Bill on 2006-03-02
I am trying to build a Dual tuner PVR and learn Ubuntu  as my first try at Linux.  My finances dictate that this will start out as a low dollar project, with upgrades as the wallet allow.

  I have both software and hardware questions, but I will confine this post to the first hardware issues I have.

My intent is to build a Linux only unit, using 4 hard drives, One 40 Gig for the OS, and three 120 Gig drives in a striped array for video recording both tuner outputs at once as needed.

Q1)  What format should I use for the drives, and how best to format them prior to loading Ubuntu onto the soon to be assembled PC?  From what I've gleaned from the posts so fat it seems that NTFS would not be a good choice.  Can whatever the preferred format is be loaded on a machine running the live CD?

Q2)  My reading of RAID posts tells me that the Rocket raid 100 card is a "software" raid card and will rely on CPU overhead, and that linux software may be better suited to perform the striping.  (My initial MB will be an older K& based unit running at 1 ghz)  Where can I find more information on RAID's so I can learn what would be the optimal approach.

Panhead Bill  (Waiting for the Keir Thomas book "Beginning Ubuntu Linux" to ship from Amazon)

---

### Post by renzokuken on 2006-03-02
i would use either "gparted" or "qtparted" and format as ext3 or reiserfs

they are both in synaptic and excellent for formatting/partitioning.

another option would be to use the gparted LiveCD ( [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) )

no idea for question 2 though, not my "area" i guess

---

### Post by glug101 on 2006-03-02
Wow, are you building a MythTV box?  I would love to build one of those. (can someone donate ~$500 US?)  Raid is something that I think to much about and would love to build also.  Perhaps someday if my current business venture works, I'll be able to put the two together. (mwahaha)

Anyway, getting back to question 2.  I did a quick search for a good RAID guide, and found this one: 

[http://www.accs.com/p_and_p/RAID/index.html](http://www.accs.com/p_and_p/RAID/index.html)

It seems to be well written, and gives a good list of the terminology. (There is more than you imagine, and MUCH more than is really needed IMHO;) )

One word of caution with the setup that you are using, a 1ghz processor seems VERY ill suited to the task of real time video recording and running a software raid.  I would HIGHLY recommend getting a board with more under the hood than that if you are thinking of recording TV.  Something like an Athlon 1800 or faster.  (the faster the better)

---

### Post by wrtrdood on 2006-03-02
I agree that 1GHz is going to be painful.  Even with external encoding the playback is poor.

Check out The Software-RAID HOWTO for info on using RAID.  As for a filesystem, XFS has been recommended since you'll be using a few very large files.  NTFS is a bad choice if your OS is going to be GNU/Linux.

---

### Post by Panhead Bill on 2006-03-02
Thanks for the responses !

The 1 Ghz board is on hand, so my plan is to prove the concept out, then upgrade the MB/CPU, then the menory, then the hard drives, then . . .  (ad dinerium) 

The old MB will then go into another case and become a file server for the home net, with the old hard drives, video card, . . . (ad cheapscateium)

---

### Post by Panhead Bill on 2006-03-02
Okay 2 coasters later and then I remember how to burn gparted as an ISO with Nero 5.xx  

(File>burn image, select file, then burn; hitting NO other buttons.)


Follow up question:  3 file systems were suggested; XFS, EXT3, and reiserfs.  Advantages/disadvanteges?  

Since I will have a boot drive and three striped drives for video storage, I assume that I'll probably end up with two different file systems.

UPON FURTHER REVIEW . . .
After reading the ReiserFS 4 Thread/discussion/flamewar I think I'll go with EXT3 for all 4 drives initally, and watch for further discussions.

Latest update: Boot drive formatted as EXT3 on my (XP) PC using the gparted CD, on to the pc under construction . . .

---

