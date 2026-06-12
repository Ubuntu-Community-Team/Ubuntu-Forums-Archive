---
title: "Dual Boot Partition Madness"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by wlg on 2009-04-03
:confused:  This newb is at his wit's end.  I'm using live CD here.  I've been trying for a week to dual boot XP & Hardy (tried Intrepid too).  1st I had Hardy installed.  Tried 2 different web suggested procedures to get XP installed, including the use of GParted and Super Grub.  I gave up, wiped my HD and put XP in 1st (much web reading suggested XP 1st) proceeding to the Hardy install I got stuck at partitioning.--  Auto resize Error:  'No root file system is defined...'  I got no 'Who are you' screen to enter info.  I then tried manual resize and get Error: 'An error occurred while writing the changes to the storage devices. The resize operation has been aborted.' I had no better luck with Garted or Super Grub (which doesn't make sense to me) I feel like one of those guys who knows just enough to cause trouble with computers.  If I can get my linux install solved then I can begin to figure out why XP won't connect on my broadband.  I sure would like to find a way to shorten the learning curve...   Thanks and pardon the rants. wlgoode

---

### Post by ronparent on 2009-04-03
Without knowing your setup, specific instructions are difficult. To take a stab at getting ubuntu up and running - if yuo have it installed boot up from the live cd (ubuntu install disk).

Open a terminal and type:

sudo grub
grub> find /boot/grub/stage1

This last stement will locate your ubuntu install. Use the locarion output, probably (hd0,1) or whatever as follows:

grub> root (hd0,1)
setup (hd0)

The output from this last command will tell you if you succeeded. If yes, remove the cd and reboot. Everything working, you will be presented with an automatically generated menu that will allow you to boot either ubuntu or winXP (providing of course that they are bootable). If this doesn't sove your problem, return to this massage thread for further instruction.

---

### Post by ajgreeny on 2009-04-03
If you have only windows installed and not ubuntu, I suggest you defrag once or twice, to be on the safe side, then shutdown and boot to the ubuntu liveCD.  Using that fire up the System > Administration > Partition Editor, click in the windows partition and choose to resize the windows partition as you wish.  If you have a large hard disk you could use it half : half for windows : ubuntu, but it is impossible to give specifics without knowing you specs; make sure you have a minimum of 10GB for ubuntu, or I think you will quickly run out of space.  If the resize option on the taskbar is greyed out right click in the windows partition and choose "Unmount" as you can not work on a mounted partition.  That may be what your previous problem was.

Now in the live CD start the installation again, but when you get to the partitioning choose manual, and in the screen that appears choose the unallocated space and make a new partition for ubuntu, leaving about 512 - 1024 MB at the end of the space for swap.  I'm sure it will all become more obvious when you get started, and you will learn quite a lot about partitioning from doing this, but if you are still stuck, come back again for more help.

Also have a look at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) which is very helpful.

---

### Post by Jon@bayleys.org.uk on 2009-04-03
Stupid question, you have got room on the disk to install Ubuntu haven't you? I.e., if you let it, XP will use the whole disk, if that's the case, I'd start again, manually define the size of your windows partition, so that there's enough free space for your Ubuntu partition to go in, as ajgreeny says, a minimum of 10GB. And yes, stick XP on first. it'll make your life a whole lot easier.

---

### Post by wlg on 2009-04-03
> **ajgreeny said:**
> If you have only windows installed and not ubuntu, I suggest you defrag once or twice, to be on the safe side, then shutdown and boot to the ubuntu liveCD.  Using that fire up the System > Administration > Partition Editor, click in the windows partition and choose to resize the windows partition as you wish.  If you have a large hard disk you could use it half : half for windows : ubuntu, but it is impossible to give specifics without knowing you specs; make sure you have a minimum of 10GB for ubuntu, or I think you will quickly run out of space.  If the resize option on the taskbar is greyed out right click in the windows partition and choose "Unmount" as you can not work on a mounted partition.  That may be what your previous problem was.

Now in the live CD start the installation again, but when you get to the partitioning choose manual, and in the screen that appears choose the unallocated space and make a new partition for ubuntu, leaving about 512 - 1024 MB at the end of the space for swap.  I'm sure it will all become more obvious when you get started, and you will learn quite a lot about partitioning from doing this, but if you are still stuck, come back again for more help.

Also have a look at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) which is very helpful.
Many thanks fellow Penquinista!  OK, I did as you suggested -System >Admin.>Partition I split it about 50/50,  When I got to Partitioning in the CD install, the XP partition was at 9%, not 50%, I clicked Manual >Continue and I get an Error re: no info root.  As before there is no pop up for "Who are you?" to enter the root info. Your sage advice is beseeched.  PS- Spread the word: Global warming is killing the Penquins!

---

### Post by wlg on 2009-04-03
> **Jon@bayleys.org.uk said:**
> Stupid question, you have got room on the disk to install Ubuntu haven't you? I.e., if you let it, XP will use the whole disk, if that's the case, I'd start again, manually define the size of your windows partition, so that there's enough free space for your Ubuntu partition to go in, as ajgreeny says, a minimum of 10GB. And yes, stick XP on first. it'll make your life a whole lot easier.
Thanks Jon@bayleys -Ah, but there are no stupid questions.  Good question, but plenty of room, thanks   PS-Save the Penquins!

---

### Post by ronparent on 2009-04-03
Ah ha. Thats clearer, I think.  On a manual install you have to select a root - probably / to keep it simpler for your purposes. If none is selected the install process aborts.

---

### Post by wlg on 2009-04-03
Thanks ronparent- If no "Who are you pops" up how do I enter root info?  wlg -- PS Tennessee Tuxedo lives!

---

### Post by ronparent on 2009-04-03
To recap an install from the cd - after selecting to install you pass through three preliminary screens until the partitioner loads. That is the point you selected manual install - correct? The next screen proceeding on a manual install allows you to select the partition or unallocated space to install to. You should have, at that point selected edit (for that partition). The edit screen allows you to select file system, a checkbox to format (or not) and a root. You must select a root at that point, preferably /, for the install to proceed. Only then will you get the 'who are you'. If you did all the above, then the problem is elsewhere.

---

