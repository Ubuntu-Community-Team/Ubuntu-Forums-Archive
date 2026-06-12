---
title: "Ubuntu NTFS drive not visible..?"
date: 2011-03-01
forum: Hardware
---

### Post by Mudvayne on 2011-03-01
Hi guys! Just learning my way around linux-ubuntu so far all has been going good except for some reason my internal sata NTFS storage drive is not showing up in places any more and I have changed nothing. Im a big fan of things working the way they should so could someone fill me in on how to mount or relocate my drive. The disk utility indicates it as not mounted when I click mount volume its pukes an error and says already mounted..am i missing something!?
Thanks very much guys really looking forward to being a linux user! :)

Edit: After a couple of full restarts the drive appears again..happy but not really these are the sorts of things that steer me away from Linux things should just work, not be intermittent! :/

---

### Post by towheedm on 2011-03-01
Welcome to ubuntu.  These things happen off and on.  They sort themselves out as patches and updates are released.  My menu items on the top panel re-arranges themselves for no obvious reason.  I just re-arrange them and hope for the best.  At least 99.9999.....% of things in Linux are free.  Plus no virus or malware, no more paying for McAfee or ZoneAlarm.

Be patient.  When I started using ubuntu in Dec 2009, I almost went back to Wiindows after about 2 months but after I got the hang of it, that was that.

---

### Post by Mudvayne on 2011-03-03
Ya I will figure it out just a pain when you goto click on a drive and its not there!? LOL It did it again this morning but a restart and it mounted fine I think its an automount issue or something in Ubuntu not 'remembering' which drives are where!? I do have Win7 still installed on a separate drive but my main drive has Ubuntu 10.10 and I have been using it for over a week now that's the first time ever I've used Linux that long I have played with it before but never lasted longer than a day! I almost went with Mandriva but just found some of the programs hard to compile, but it is a nice OS.

---

### Post by Mudvayne on 2011-03-05
Sorry guys still having issues with frigin Ubuntu and my drives I just tried to transfer some large files from my spare internal drive to an additional hard drive I plugged into a free IDE cable and could not get ubuntu to mount the drive it would either mount one or the other not both. I did try disk utility mount volume it spit an error that it was already mounted. 
1) So Linux wizards how does one manual edit and mount drives? 
2)Why does it not auto mount and sort drives itself like say a windows box? 

Im suspecting its a auto mount issue trying to mount where something is already mounted!? 

3) Once my main drives are mounted correctly is there away to save that setting incase I want to plug an extra drive in, I dont want it moving drives around once working!?

Sorry to admit I had to boot up my windows 7 which had no trouble at all seeing all 4 hard drives I had plugged in.
Thx guys little frustrated here...

---

### Post by dabl on 2011-03-05
> **Mudvayne said:**
> 

 I had to boot up my windows 7 which had no trouble at all seeing all 4 hard drives I had plugged in.


What?  Microsoft's proprietary closed-source OS was able to read Microsoft's proprietary closed-source filesystem?  I'm shocked!  :shock:

But seriously ...

I think you've probably got two or three different issues all tangled up there.

1. USB operations -- any storage device that you connect to your computer via the USB connector will be "hot plugged" or mounted automatically via that part of the OS.  I don't actually know what happens when you try it with a NTFS formatted hard drive -- if I did that it was numerous years ago on a far older version of Linux.

2. NTFS filesystem format.  Recent versions of *buntu have native NTFS support built in, so when mounted manually, or automatically by /etc/fstab, a NTFS partition will be there.

3. How to mount a filesystem. Google will answer this one, and/or maybe #15 here will also help:  [http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

---

### Post by Mudvayne on 2011-03-05
> **dabl said:**
> What?  Microsoft's proprietary closed-source OS was able to read Microsoft's proprietary closed-source filesystem?  I'm shocked!  :shock:

LOL..Actually what's shocking is Ubuntu having issues with it, Win7 just works I'm not knocking Ubuntu as its my main os right now to accomplish the same thing as win7 I need to read 14 pages of help files! I can format and mount drives via the disk  utility (in Ubuntu). If I can reproduce the error I get when trying to mount a drive  can I post a jpeg screen of it here!?
Thx

---

