---
title: "[SOLVED] Cannot get Ubuntu into my machine for love nor money!!"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by karamu on 2008-12-08
I've been using Ubuntu for about six months now and am very happy to have made the switch from Wondows! Recently due to a hardware problem I rebuilt my machine (the specs are in my signature)- since I did though I am experiencing severe installation problems for the first time- it worked like charm on my previous machine! I have tried three different ways to install Ubuntu which I will detail here- any pointers/ ideas/ suggestions would be very welcome as I am getting severely frustrated with using Windows (I want my cube back!!)

1) Using Ubunto 8.10 live CD- after the initial screen where you can choose to install Ubuntu, check CD etc, when I try to launch Ubuntu, I get a black sceen and a message something like "(some numbers- sorry didn't write them down) error aperture too small 32MB not 64MB".

Nowhere in my BIOS can I find a setting related to aperture- the onboard video RAM is set at 256MB. I have the same problem whether I use 32 or 64 bit (I want to use 64)

2) Ubuntu 8.04 (64bit) live CD launches fine- get to the desktop environment and launch the installer program and then it starts to act strange. I have a minimal XP installation on the disc already- about 4gig- when I get to the partitioner section, it won't let me allocate any less than about 30gig to XP- it says too small. I then start the partitioner and it starts to work then hangs at 0%- the screen freezes and I need to do a hardware reset.

3( Ubuntu 8.04 alternate install CD (64bit). Everything seems to go OK- the partitioner runs OK, although I still get too small when I try to give XP 10 or even 20 gigs. The installation proceeds fine until the very end when it trys to install GRUB- this fails for some reason!

Sorry for the length of this post but I wanted to explain as well as possible. I am guessing there is some issue with my HDD? I downloaded a diagnostic program from Seagate and it finds no errors on the drive.

And, yes I have checked the CD for defects each time- no errors are found.

I have thought about WUBI and installing in Windows but I really want to have Ubuntu on its own partition- I don't plan on using Windows much and want to give the bulk of my drive to Ubuntu.
I have another HDD which I might put in the machine and see if Ubuntu installs to that but I really can't understand why I am having so many problems installing when the previous time it was plain sailing!!

---

### Post by Kevbert on 2008-12-08
It looks like your boot sector size is too small. How to increase the size I don't know (unless you re-install everything from scratch). What may be possible is to get rid of some of the old kernels from there (assuming you have other versions of *buntu and linux installed).

---

### Post by linux_tech on 2008-12-08
Try downloading gparted and make a gparted cd to boot from and preformat partition in ext3.  Alternately f you are using live cd, you should also be able to format ext3 using the gparted on it. So either way.

---

### Post by karamu on 2008-12-08
It is a fresh install- XP was the first thing to go on it...... The HDD that was in my old machine isn't running right now (my new MOBO only had one IDE controller but I have two HDDs + DVDRAM- I got an IDE- SATA converter to hook up the drive but it isn't recognised by the computer- another little niggle I need to sort out!!)

---

### Post by karamu on 2008-12-08
and, I'll try partitioning with the live cd GParted tomorrow- it's getting late and I can't face it tonight. One other thing I didn't mention is that intermittently when I boot the live cd the video doesn't seem to initiate- after the loading screen, the screen goes black and the monitor goes into power saving mode....!!

---

### Post by karamu on 2008-12-08
and thanks for taking an interest both of you!!

---

### Post by Kevbert on 2008-12-08
> **karamu said:**
> and, I'll try partitioning with the live cd GParted tomorrow- it's getting late and I can't face it tonight. One other thing I didn't mention is that intermittently when I boot the live cd the video doesn't seem to initiate- after the loading screen, the screen goes black and the monitor goes into power saving mode....!!

Do you have any problems with video in XP ? What's the display adapter make and model ?
Please take a look at this [[COLOR="Red"]page[/COLOR]]("https://help.ubuntu.com/community/BootOptions"). An option you could try is 'noacpi' which may help.

---

### Post by cmay on 2008-12-08
> **karamu said:**
> It is a fresh install- XP was the first thing to go on it...... The HDD that was in my old machine isn't running right now (my new MOBO only had one IDE controller but I have two HDDs + DVDRAM- I got an IDE- SATA converter to hook up the drive but it isn't recognised by the computer- another little niggle I need to sort out!!)

i think this sata thinghy has a bit to with it. i have never had any problems with installing linux on plain old e-ide disks but i once had a very similar problem with an sata drive. which i formatted completly using windows. then i made a whole partion for windows and installed it just to let ubuntu take over the whole disk. and it did. i heard about some people that complaint over sata drives not being easy to use with linux but i cant say i have much knowledge on it. i only have one sata drive myself. the few post inohter linux forums about this is also a few years old by now. but you ca partion with windows xp cd when you make the partions you want for both linux and windows if yu are planiing on doing dual boot. which is what iwould recomend over using gparted if you already have a master plan for how it should be installed. 
i hope you get good luck installing you systems.

---

### Post by karamu on 2008-12-08
XP video seems fine- I've watched a few movies on it (although one vid I tried to watch in Firefox was all screwed up- the colours were all orange/ yellow/ green red).

The vid comes from the onboard chipset:

- AMD 690G Chipset
- Integrated ATI Radeon X1250-based graphics

according to the ASUS website.

I don't think the sata issue is related because the problems I had all were there before I tried to connect the second drive.

---

### Post by cmay on 2008-12-08
i think you are right.   do not have any solution as such i am sorry to say. i do have so much time either but i wanted to say i think your  right , 
good luck to you anyway.

---

### Post by karamu on 2008-12-09
Got it!! Writing from my new installation of Ubuntu 8.04- booted into the live CD and used GParted to sort out the partitions before installing using manual partition option. 

The only problem I had was that there were a couple of logical partitions on the drive (presumably from the previous aborted installation attempts) which GParted wouldn't let me delete. I booted using a Windows install CD which let me delete everything other the main NTFS partition- I then went back into the Ubuntu live environment, set up the ext3 partition and the swap space and it installed no problem!!

SO happy to have Ubuntu back!!

---

