---
title: "Two 160GB drived RAIDed together, how should I dual-boot with Vista?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2009-05-24
I just ordered a ThinkPad W700 yesterday with 320 GB of total hard drive space, comprised of two 160 GB drives RAIDed together (I'm assuming; I bought it refurbished from Lenovo's outlet store so details about the exact configuration were sparse).
I haven't dual-booted before, so I'm not sure how to go about doing this. My first impulse was just to un-RAID the drives (if possible?) and install an OS on each of them, but I want to be able to share stuff between them. For example, I want my documents, music and movies to be saved on a separate partition so that I can access them from either OS, but I don't want to have to mount a whole separate hard drive to do so. If I had saved all my music in a folder in Vista, for example, I'd have to mount the whole Vista partition to get to it. I know Ubuntu can read/write to NTFS partitions, but I'd like to keep it separate just to make things less of a hassle (hopefully).
How should I do this? Of the 320 GB total, I was thinking around 120 GB for Ubuntu, 150 for Vista (going to have heavy apps on it like AutoCAD, etc), and about 50 GB for the shared partition. If it was only one hard drive I could probably figure it out confidently, but I was hoping to get some tips before I go messing with two hard drives.

---

### Post by ronparent on 2009-05-24
Since you are plannig to dual boot with vista you will have to use the 'fakeraid' version of raid implementation in ubuntu. You didn't say whether it was a raid0 or raid1 setup. My guess is that it will be raid0 which give you the total 320 gb in a 'stripped' array. This leaves you very vulnerable in a disk failure since the loss of one drive results in loss of everything on both drives. Depending on how it would get handled around, this could make me very nerveous. So you should plan on a good backup scheme. Presuming it is a raid0, be very careful how you partition. The usual advise is to install with the alternate cd. 

Until you run dmraid (the fakeraid software) raid0 drives would show up as two separate unallocated spaces. Even after running dmraid, two unallocted component drives will show in the partioner as wel as the parttioned array as a sepearate drive. Under no circumstance try to partition the unallocated drive as that would wipe out all programs and data on both drives. If it sounds scary,it is and you have to study what you are dealing with and plan your moves carefully. I recommend that as your first step you study the following sites:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/](http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/)

The primary tricky part is to get the ubuntu up and running on a raid0. Once accomplished the results should be completely satisfying. Keep us posted on how it is coming.

---

### Post by rainwalker on 2009-05-24
I'm pretty sure it's raid0, that sounds familiar. I don't have the laptop yet, nor do I know when it will get here (yet), so I can't really physically mess with it.
Having never messed with partitioning before, much less RAID, I really don't know what you're talking about.
Sorry for my lack of know-how, but I get lost at step 5 of [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). It looks like quite a bit of setup and tweaking that's way beyond my skill level...would it be easier to just un-raid the drives and install an OS on each of them? I'm not quite sure how setups like this work.
[http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/](http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/) appears to be for a setup with only Ubuntu being installed. 

When I run the Ubuntu live CD, what will it show? Two hard drives? One 320 GB drive? Will Ubiquity see the Vista install? Why can't I use it to just resize the raid0 partition? Sorry for all my questions, I'm trying to get as much of this lined out as I can before I jump into things.

---

### Post by ronparent on 2009-05-24
When you run the live cd you will not be able to see any sign of the drives because they aren't be mounted. When you run gparted on the live cd, it will show two empty drives (160gb unallocate space in each). To see the two drives as one raid0 array you have to install and rum dmraid and mount the symbolic links for existing raid partitions shown in /dev/mapper to a file system mount point. I don't think the process will become clear to tyou until you have the laptop in front of you and can try commands and experiment.

---

### Post by rainwalker on 2009-05-24
Ohhh okay, that makes more sense. How come when I run a live CD on my laptop I have now, though, it always shows the hard drive already mounted as "x GB Volume"?
Also, I just finished talking to someone about this setup and it sounds like I could just put one OS on each drive and mount the other one like an external hard drive whenever I need to access it. Technically I'd lose that third "sharing" partition, but if I can' browse the hard drives from either OS, I don't think it will matter. Assuming I can figure out how to un-raid the drives, does that sound like it would work? I know Ubuntu can read/write to NTFS volumes and I'm pretty sure there's a driver for Vista to read ext volumes, so it doesn't sound like I have much to worry about.

---

### Post by rainwalker on 2009-05-25
So I've done some more research and I think this is what I'm going to try and do:
Once the laptop arrives, I'm going to install all the normal stuff (Firefox, codecs, etc) and then create an image of the install (not sure what software I should use, any recommendations?). Then I'll disable RAID0 through the BIOS and just use the image I created to install back onto one of the drives. Then I'm free to install Ubuntu on the other drive.
Does that sound right? I still need to figure out how I should make the image of the Vista install, and how to install it again afterwards, but overall does this plan sound doable?

---

