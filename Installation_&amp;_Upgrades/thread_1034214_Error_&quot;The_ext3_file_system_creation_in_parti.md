---
title: "Error: &quot;The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed&quot;"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by bo_gs on 2009-01-08
Hi everyone, I'm hoping you'll be able to help me.

I have decided to try making a move to Linux but things are starting a little rough. I have been trying to install Ubuntu 8.10 on a Toshiba laptop that was previously host to Windows Vista. Everytime I try to install the o/s, I get the following error:
> The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed
As a note, I did verify the integrity of the disk. 
I have been selecting "Guided - use entire disk".
The computer is a toshiba A205-S4629
2GB RAM
200GB HDD

Thank you for any help you can provide.

---

### Post by bo_gs on 2009-01-08
I have been reading through other posts and did try the fix lited in the 8th post of this thread, but it didn't fix the problem.
[http://ubuntuforums.org/showthread.php?t=1031111&highlight=ext3+file+system+creation+partition+%231]("http://ubuntuforums.org/showthread.php?t=1031111&highlight=ext3+file+system+creation+partition+%231")

---

### Post by canoemoose on 2009-01-08
Right.  It sounds like the partitioner is failing to correctly create the partition.  Do you know what you're doing enough to manually partition your drive?  If so, try that.  If you need a hand or more detailed instructions, just ask!

---

### Post by bo_gs on 2009-01-08
I'll probably need a little help. I pretty computer oriented, but my background is pretty much completely in Microsoft products. If you could point me in the right direction for what size and type each partition needs to be I should be able to go at it manually.

---

### Post by bo_gs on 2009-01-08
Ok, when I went to manual install, there were already 2 partitions set up. The pirst encompassed almost the whole drive but was listed as "do not use". The second partition was roughly 6 GB and was listed as the swap are. I edited the first partition and set it to ext3 and mount as /. I left the swap file alone.

It's been running as I typed this and it just posted the same error.

---

### Post by canoemoose on 2009-01-08
Okaly dokaly.  I suppose the first thing you could do is try just deleting the existing partitions before installing Ubuntu.  Before you launch the Install wizard, unmount the drive if it is mounted, launch gparted (System>Administration>Partition Editor) and delete whatever partitions are on the drive.  Disclaimer: this will delete everything on the drive  so back up anything you need (You probably know this, I'm just covering my back.)  Launch the install wizard and see if the "automatic using entire disk" option works.

---

### Post by bo_gs on 2009-01-08
Alright, I wiped the whole system clean so that it showed the drive as 100% free space. I ran the Automated install, "Guided - Use entire space", and I still got the same error.

---

### Post by canoemoose on 2009-01-08
Oh, piggies.  Manual install it is then.  How much RAM do you have in your machine and are you going to want to hibernate your computer??  How big is your hard drive??

---

### Post by bo_gs on 2009-01-08
I will probably want it to be able to hibernate as I used that feature alot in windows when I carry the laptop at school. It currently has 2GB of RAM, and a 200GB HDD

---

### Post by canoemoose on 2009-01-08
Righto.  To hibernate, your swap partition needs to be at least the smae size as your RAM.  I'd say give 3GB to swap so you're covered if you decide to upgrade your RAM.  You may as well give 20GB to be mounted at / and the rest of the drive can be mounted at /home.  This makes it easier to do upgrades as your data is separated from Ubuntu's.
Have I told you enough?  I've got to go to college now but I'll be back in about 2 and a half hours time when I have Computing.

---

### Post by bo_gs on 2009-01-08
I'll try that and see where I'm at. I'll post up my results. I'll probably try to get a little sleep after that as it is early morning here. Good luck in class and thank you for your help so far. I look forward to this working, or continuing our conversation if it doesn't.

---

### Post by bo_gs on 2009-01-08
Ok, I ran it as manual install. I set the first partition to 20GB ext3 /, the second partition was set to roughly 175GB ext3 /home, the third was set to 4GB swap.

There is a progress window open just like the other times. It says "Installing System" and is at 5%. under this it says "Creating ext3 file system for /home in partition #5 of SCSI1 (..." at this point, just like the other times, it stops and another alert window opens titled "Failure to create a file system" This box contains the error measage: "The ext3 file system creation in partition #5 of SCSI1 (0,0,0) (sda) failed."

I know how hard it is to troubleshoot computer issues without being able to actually see the issue so I'm trying to be as specific as possible.

---

### Post by canoemoose on 2009-01-08
Don't worry, you're being plenty specific enough :D
Umm... I'll have a think and post back here when I've thought of something.

---

### Post by canoemoose on 2009-01-08
Righto, had an idea.  How about trying to create the partitions <i>before</i> running the installer??  Use gparted with the same partition sizes as earlier.  In the manual install, you should be able to select each partition and give it a mount point (/, /home, swap).  I've not tryed for a while and don't have a system to bork finding out, so you'll have to bear with me if my instructions don't fit the options available.

---

### Post by bo_gs on 2009-01-08
Ok, I'll give that a try and see where we are at

---

### Post by bo_gs on 2009-01-08
Ok, I thought we had something going there for a while becuase it seemed to be going right along but then it just stayed at the same point:
> Installing system
35%
Copying files...
It stayed on this measage box for a while then after about 4-5 minutes it came up with the following error box:
> Installation Failed
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/Output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens. To check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

Well basically thats telling me it thinks I have one or more of three issues, a bad cd, a bad Hard Drive, or the laptop is in an environmentally bad area, lol. I can pretty much rule out the last one so I guess my next course of action will be to reburn an Ubuntu disk, and to run some hardware diags on the HDD. 

Is there any other things you can think of or do you want me to try those and post up my results? Oh, and again, thank you for all your help so far.

---

### Post by canoemoose on 2009-01-08
Well, I'm glad we got further.  Is one of the CD boot options "check CD for defects" or is that my bad memory?? Try that before burning another disk. Actually, disks are cheap, do what you want!
I <i>hope</i> we can rule out the bad DVD drive so that just leaves overheating.  What surface is the laptop on??  Is it possible to prop it up somehow so that it gets a greater airflow??  I had this problem once and made a triangular cross-section piece of wood about 25mm / 1 inch high I could put under the back of my laptop if I was doing anything “harsh” to it that would generate a lot of heat.  Overkill I know but propping up the laptop to sort out heaty issues is always a good idea.

Oh, and not digging for compliments or anything, but there's a “thanks” button down there.:p -->

---

### Post by bo_gs on 2009-01-08
Sorry, hadn't really payed enough attention to the forum itself to realyze there was a thanks button, you definitly deserved one though so I just did it. 

I know its not overheating. The laptop is on a laminate counter top that I use as a desk, and it has an extended cell battery that lifts the rear about 3/4 of an inch of the surface. There is plenty of airflow and the system is cool to warm to the touch.

I did verify the integrity of the disk, but as you said they are cheap so I have another one burning as we speak. As a side note, I work at Best Buy as a service tech and still have about a year left on a service plan through them so if I do have bad hardware, I can get it swapped out pretty easy. I just find it a little strang that the problem has only showed it's head now that I'm trying to dump vista, lol.

---

### Post by canoemoose on 2009-01-08
OK. Being English and unaware, I take it Best Buy is a comp store??
Let me know what happens with the new CD.

---

### Post by bo_gs on 2009-01-08
Yeah Best Buy is pretty much the largest electronics retailer over here. The are the parent company of Geek Squad. I know we have a Geek Squad presence in the UK.

I'm getting ready to try the new disk, I'll let you know how it goes, but I'm starting to get a bad feeling about my hard drive...

---

### Post by bo_gs on 2009-01-08
Ok, I tried the new disk, but I had the same result. I ran a few diagnostic tests with Eurosoft and the hard drive failed pretty much all the tests. I took it into work today and should have it fixed tomorrow. Im sure that is probably what my problem was but if I still have issues after I get the new drive put in, I'll let you know. Thanks again for all your help!

---

### Post by bo_gs on 2009-01-09
Well I ran several tests on the harddrive with Eurosoft and it pretty much failed everything, read, write, mechanical, etc. I should be able to get the drives switched out at work tomorrow and I'll have another go at getting this all loaded up. I'll let you know if it works and if it does, I'll mark this thread as solved. Thank You again for all you're help and patience.

---

### Post by hovvit on 2009-01-26
...I'll add my 2 cents as I have just been dealing with this same problem, except on an old Dell Inspiron 1100...

at first I thought it was a problem with the hard disk as this laptop is old and doesn't run very well (I still think that might be the problem)... but I created the install CD I am using on my other laptop which also runs Ubuntu... for some reason it burns too quickly even though I reduce the burning speed, and my burned CD's only work 50% of the time.

To make the partitioner and installation run correctly I just ran it over and over... eventually it can read the CD an it works.  It took me about 5 tries, then it just worked. 

not very technical, and no new information really, but that is what worked for me.

---

### Post by liljoentx on 2009-01-30
This is a subtle issue, which I am also experiencing.
Put a new, raw, 80 Gig (ST380215A) hard drive in a working desktop system that had a bad 80 gig in it. Tried to load Ubuntu 8.04 from a newly created and verified Live CD. Same situation!

Finally noticed after doing a "sudo lshw -C disk" that both the hard drive and CDROM were showing up as SCSI devices! This is not right and I have no idea how to correct it! The BIOS battery is good, I've reset the CMOS and all jumpers are correct on the drives and motherboard.

Any suggestions?

Thanks before hand!

Lil'Joe

---

