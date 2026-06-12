---
title: "Is it safe to resize Vista partition with GParted?"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by darlyn on 2009-09-24
I would like to repartition a drive that currently has Vista on it, so that I can install another version of Windows on a new partition. This is easily done from the Vista Disk Management tools, but I do not have the admin permissions to access these tools. Therefore, I assume I can use Gparted (on a LiveCD/USB) to resize the current Vista partition and make room for the new one. Doing so would corrupt the current Vista partition, but a quick run with the Vista install DVD should repair and restore it.

Would my assumption be correct? I absolutely cannot risk damaging the current Vista partition, so I ask if this is safe. According to Howtogeek, [this exact procedure is indeed]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") safe for the current Vista partition as long as you repair it with the DVD afterwards, but I would like a second opinion.

---

### Post by wojox on 2009-09-24
Make sure you defrag the Vista partition a couple times first. Why don't you have Admin privileges? You really are safer resizing with Vista. I have heard of people using gparted before though.

---

### Post by raymondh on 2009-09-24
> **darlyn said:**
> I would like to repartition a drive that currently has Vista on it, so that I can install another version of Windows on a new partition. This is easily done from the Vista Disk Management tools, but I do not have the admin permissions to access these tools. Therefore, I assume I can use Gparted (on a LiveCD/USB) to resize the current Vista partition and make room for the new one. Doing so would corrupt the current Vista partition, but a quick run with the Vista install DVD should repair and restore it.

Would my assumption be correct? I absolutely cannot risk damaging the current Vista partition, so I ask if this is safe. According to Howtogeek, [this exact procedure is indeed]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/") safe for the current Vista partition as long as you repair it with the DVD afterwards, but I would like a second opinion.

-Back-up your files and defrag
-Suggest you use a gparted liveCD (standalone) rather than the gparted that comes with the Ubuntu liveCD.
-Untick the checkbox that "aligns to bounderies".  That way, you do not move the first sector of windows (which will then cause boot problems)

Yes, it's possible.

[Herman's take on this]("http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17").

Good luck.

---

### Post by bumanie on 2009-09-24
Gparted will usually do it without problems, but the native vista partitioning tool does a better job on vista as it is designed for working on vista partitions. Vista can shrink and expand partitions, whereas xp could only expand partitions.

---

### Post by rreese6 on 2009-09-24
This sounds like a topic for a GPARTED Forum Not Ubuntu Installation.

Since you do not have Administrator permission, I must assume that the Computer is not yours. I would be very careful about changing a corporate computer because the Administrators have ways of finding out if your system has changed and the result might be a loss of your job.
Many companies have policies that prohibit any changing or tampering with the computer partitions or OS. All I am saying is it would better to check with your administrator first. 

Since those questions are on my mind, I will withhold any help on this post.

---

### Post by Bartender on 2009-09-24
+1 rreese's comments.

This person doesn't have admin rights.  Well, OK.  How come?  Because it's not their PC most likely.  The OP "absolutely cannot risk damaging vista"...what does that tell you?

And the DVD referred to in the HowToGeek instructions is a genuine Vista install DVD, not a recovery DVD.  How many people have genuine Vista discs?

---

### Post by Mark Phelps on 2009-09-24
> **Bartender said:**
> This person doesn't have admin rights.  Well, OK.  How come?  Because it's not their PC most likely.  The OP "absolutely cannot risk damaging vista"...what does that tell you?
Wow -- the "voice of reason"!! BTW, I'm NOT being facetious; I'm being supportive.  

If you can "absolutely not risk" damaging something, there is only one sensible response -- LEAVE IT ALONE.

Or, to phrase it the way folks in my generation use to say it -- If it ain't broke, don't fix it!

> And the DVD referred to in the HowToGeek instructions is a genuine Vista install DVD, not a recovery DVD.  How many people have genuine Vista discs?

Since this appears NOT to be the OP's personal computer, my guess is that they do NOT have a Vista DVD -- which is yet another good reason for leaving it alone.

---

### Post by darlyn on 2009-09-27
No, the computer is not a corporate machine, and no one will be harmed if it's modified. It's mostly a throughaway spare (i.e. guest computer -- nieces should not be fiddling with my main machine) to me, but I still would rather leave the Vista partition in its current state. Simple fact is that I really don't want to go through the trouble of reconfiguring, reinstalling, or disk imaging the thing. A quick partitioning and install would save me the boredom.

> Since this appears NOT to be the OP's personal computer, my guess is that they do NOT have a Vista DVD -- which is yet another good reason for leaving it alone.

I have a stock DVD, and the necessary drivers are all on a second partition.

---

