---
title: "How safe is it to dual-boot Ubuntu with Vista?"
date: 2008-09-03
forum: General Help
---

### Post by DanJC on 2008-09-03
I've been thinking of dual-booting Ubuntu with Vista, but I'm not sure.  I've heard plenty of success stories getting Linux to dual boot, but I've heard plenty of horror stories too.  I really can't risk my Vista partition (I don't care about it, but my grandmother uses it), especially because HP neglected to include a Vista reinstallation CD should anything go wrong.

How safe is it?

---

### Post by oilchangeguy on 2008-09-03
> **DanJC said:**
> I've been thinking of dual-booting Ubuntu with Vista, but I'm not sure.  I've heard plenty of success stories getting Linux to dual boot, but I've heard plenty of horror stories too.  I really can't risk my Vista partition (I don't care about it, but my grandmother uses it), especially because HP neglected to include a Vista reinstallation CD should anything go wrong.

How safe is it?

done properly it's easy to set up a dual boot. always, always back up any data first. and your computer should have a recovery partition. DO NOT touch it! and do some research in here. use the search bar at the upper right of the page and look for how to dual boot.

---

### Post by linux5uper on 2008-09-03
If you follow the simple instructions for installing ubuntu, it's quite safe i'd say. The Ubuntu installer realizes that there is another operating system on you hard drive and will include it in the booting options. The most critical step is partitioning - just be careful not to step into vista's boundaries here and you'll be fine. You can find detailed instructions on how to do the whole process safely, either here in the forums or just ask google.

---

### Post by TeoBigusGeekus on 2008-09-03
Vista has a service with which you can create a recovery disk. I don't use Vista but a bit of googling could help you out.

You can easily dual boot Ubuntu&Vista. When you reach the partition manager in the Ubuntu installation choose the manual setting and you can do anything you want with your hard disks.

---

### Post by DanJC on 2008-09-03
I googled the Vista recovery disc, and I'll be sure to create one later.  I found a tutorial here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Does it appear to be reliable?

---

### Post by TeoBigusGeekus on 2008-09-03
> **DanJC said:**
> I googled the Vista recovery disc, and I'll be sure to create one later.  I found a tutorial here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Does it appear to be reliable?

It looks OK mate...
Create a recovery disk and give it a shot.

Good luck!!!:)

---

### Post by oilchangeguy on 2008-09-03
> **DanJC said:**
> I googled the Vista recovery disc, and I'll be sure to create one later.  I found a tutorial here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Does it appear to be reliable?

did you read post #2? your computer should have a recovery partition, if so there's no need to waste time or a cd.

---

### Post by DanJC on 2008-09-03
Thanks... but I'm not sure if I'm going to go through with it yet.  I'm using Wubi right now, and I have 23 gigs of memory available (my hard drive is huge), but the only thing that bothers me is when Vista begins to go down the tubes, Ubuntu will too. :(

First I'll make a recovery disc.  Then I'll see where I go from there.

---

### Post by 0004tom on 2008-09-03
Mine had a recovery partition, i'm on a hp g6030ea, however when pressing F11 on the bios screen as instructed by the manual. I couldn't boot into it, so I removed the recovery partition, and gained 6GB back of my hard drive.

The risky thing, when dual booting, is the partitioning. just make sure you don't delete/refomat the vista partition.

---

### Post by jespdj on 2008-09-03
Just watch out during the Ubuntu installation process. As far as I remember, the default setting for the installer is to use the whole harddisk for Ubuntu (deleting anything that's already on there). Just read the instructions in the installer carefully and setup the partitions manually during the installation process - take care not to delete the Windows Vista partition.

[COLOR="Lime"](Yay, this is my 1,000th post on the forums!)[/COLOR]

---

### Post by DanJC on 2008-09-03
Yeah, I found out I do have a recovery partition, but I'm still going to make a recovery disc.

EDIT: Good thing the recovery partition works (I just tried to load it, and it worked, haven't actually recovered anything though), because I just tried to create a Windows recovery disc.  Seems Microsoft thought to include a recovery disc creator, but it didn't occur to them that they should make it work; the program doesn't actually load anything.

---

### Post by DanJC on 2008-09-03
Okay, I need some more advice.  I read some of the comments on that tutorial, and I'm confused as to which partitioner I should use.  A lot of people have been trying the Shrink disc function built into Windows, as the tutorial suggests, but they've been having trouble getting Ubuntu to recognize the partition.  Other people have been using the partition built into the Ubuntu installer, but they've been having problems getting Vista to boot after using it.

So what should I use?  Shrink disc, the Ubuntu installer partitioner, or a live CD of Gparted (which I have on hand)?

---

### Post by DanJC on 2008-09-03
Bump

---

### Post by suff0beast on 2008-09-03
I dual boot w/ Vista (yeah I know... it's only temporary). Anyways, you will need to reinstall windows and specify it's partition size if only on a single harddisk system. Once you've done that then go ahead and run Ubuntu CD to install.. Select the Manual partition setup option and create your swap and boot partition for Ubuntu. After all that, you are done and works great. I haven't had a problem and been using it actively daily for about 9mo... including upgrading ubuntu to current 8.04 version.

Since you are unsure, my advice is Install Vista First! We all know how MS is, and Ubuntu will show Vista in GRUB w/o you needing to tell it it's there!

---

### Post by DanJC on 2008-09-03
Can't do that... if you read my earlier posts, HP neglected to include a recovery disc or reinstallation disc, instead opting for a standalone partition with the recovery data on it.

I'm going to try the Shrink partition function in Vista, after it's done defraging.

EDIT: Also, I've got another worry.  Since GRUB installs on the MBR, will I still be able to access the recovery partition should something go wrong?  Right now, to access the recovery partition, all I have to do is press F11 at the HP Logo, before I even get to the bootloader.

---

### Post by oilchangeguy on 2008-09-03
> **DanJC said:**
> Can't do that... if you read my earlier posts, HP neglected to include a recovery disc or reinstallation disc, instead opting for a standalone partition with the recovery data on it.

I'm going to try the Shrink partition function in Vista, after it's done defraging.

EDIT: Also, I've got another worry.  Since GRUB installs on the MBR, will I still be able to access the recovery partition should something go wrong?  Right now, to access the recovery partition, all I have to do is press F11 at the HP Logo, before I even get to the bootloader.

as long as you pay attention to what you are doing when you install ubuntu. and make sure it only touches the c: drive. you'll be fine.

---

### Post by suff0beast on 2008-09-03
You should still be able to run the complete system recovery via the boot options when turning your box on. When you specify a complete system recovery in theory "should" give you the whole setup features of vista and ask you to select a partition, create partition, delete partition... for you to do that.

I use a Toshiba laptop that only has the recovery partition deal too, and that's just what I did.

In any event that's what my experience has been

yes you would still be able to access the system recovery

---

### Post by DanJC on 2008-09-03
> **oilchangeguy said:**
> as long as you pay attention to what you are doing when you install ubuntu. and make sure it only touches the c: drive. you'll be fine.

I'll keep an eye out, but what should I look for?  Will it ask me where I want to install Grub?

Sorry for all the questions, but I want to make sure I know exactly what I'm doing.  If I screw up the computer, it'll be my head... :(

---

### Post by oilchangeguy on 2008-09-03
> **DanJC said:**
> I'll keep an eye out, but what should I look for?  Will it ask me where I want to install Grub?

Sorry for all the questions, but I want to make sure I know exactly what I'm doing.  If I screw up the computer, it'll be my head... :(

this thread is over three hours old. you're making life much harder than it has to be. just follow the prompts. and pay attention. better yet, instead of using your main computer and maybe losing your head over a screw up. do you have another computer you can learn on? if so use it.

---

### Post by DanJC on 2008-09-03
I have an older computer, but it's so old it doesn't run much of anything.

I'll try the install, and if there's anything I'm unsure/worried about, I'll bail out and be satisfied with the Wubi install I have now.

Thanks for the help! :)

---

### Post by bodhi.zazen on 2008-09-03
> **DanJC said:**
> I've been thinking of dual-booting Ubuntu with Vista, but I'm not sure.  I've heard plenty of success stories getting Linux to dual boot, but I've heard plenty of horror stories too.  I really can't risk my Vista partition (I don't care about it, but my grandmother uses it), especially because HP neglected to include a Vista reinstallation CD should anything go wrong.

How safe is it?

It is not safe at all => get rid of Vista while you still can :)

Seriously , installing an OS is a major undertaking and you should prep yourself first :

1. back up your data

2. make sure you know how to re-install vista if needed.

3. defragment your vista partition.

4. make sure you understand the installation process and partitions before you start.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

99.5 % of the time the installation with default options is just fine. That is not the issue.

The real issue is : ***you should understand how to back up and restore your Vista installation before you start.***

---

### Post by DanJC on 2008-09-03
Okay, I'll be sure I make sure I know what I'm doing before I start.  And like I said earlier, if something in the installer worries me, I'll bail out before I install and be happy with my Wubi install.

---

