---
title: "A few questions before installing Ubuntu."
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Tom Gilroy on 2009-04-08
Hello everybody! I'm completely new to Linux and intend to install Ubuntu within the next day or so. I've downloaded and burned the live cd, and after booting from the cd I noticed no problems, bar the touchpad of my laptop being unresponsive (my USB mouse works perfectly, and there are no wireless issues). This problem strikes me as somethings that's probably easy to fix, or am I mistaken?

My laptop is quite high spec (64-bit architecture, 8GB of RAM and so on), and Vista was the supplied OS. 

I would like to have a triple boot system, Vista and two Linux distros (this is so I can experiment with different distros easily and find which suits me best), and I have a few questions.

I've been told that I'll need a swap partition, and that it should be twice the RAM I have available. Is this really necessary with 8GB of RAM available? If it's still advisable, is 16GB really necessary? Surely 1-2GB would be plenty?

I've also read [here]("http://www.psychocats.net/ubuntu/partitioning") that a home partition would be useful, how large should a home partition be?

Also, as I said, I'd prefer to have another Linux distro available when booting. Will one swap partition suffice for both? If I make home partitions for each, will the distros keep to their own home partition?

As I see it, I need 7 (maybe 8) partitions. One for Vista (NTFS), one for shared documents (FAT32), a partition for each linux distro and a home partion for each (Ext3), a swap partition and I may choose to keep the Windows recovery partition, or does anybody have another suggestion?

---

### Post by Therion on 2009-04-08
Instead of all that partitioning and installing, I'd suggest you try LiveCD's to make your decision about which distro, or distos, you want to install to your hard drive.  

LiveCD's let you take a distro on a test-drive without all the fuss of a hard drive-based install.

---

### Post by lisati on 2009-04-08
I have Ubuntu 8.10 64-bit installed on the laptop I'm using now, in a dual-boot configuration with Vista Home Premium.

1) 32-bit or 64-bit versions of Ubuntu:  Depending on what you're doing 32-bit can suit some people better than 64-bit - it will run fine. To get the most out of your machine, 64-bit may be the way to go, but can sometimes involve a little extra work if you need to run something that only comes in a 32-bit version
2) Partitions (and sawp): there is no substitute for careful planning. It looks like you've put in some thought to this. Being lazy, my preference when doing a fresh install is to use the partition manager on the Live CD to free up some space, and then tell the installer to use the largest contiguous/continous free space, and let the installer take care of the rest. Your suggestion of 1-2Gb for the swap sounds good. Separate home partition? I haven't gone down that road yet so I can't help.
3) Touchpad: Sorry, can't help. I tend to use a USB mouse, so haven't noticed any problems with the touchpad (other than side effects of bumping it accidentally when typing.)

Hope these thoughts, together with what others have to say, are of some help.

---

### Post by Wobblybob on 2009-04-08
Wow that's a lot of partitions for a first time install! If it was me, I'd have one for Vista, one for each of my linux o/s no more than about 10GB each, a single home as big as you can and a single swap of no more than 2GB. You could make your home fat32 so that Vista can share. When you install your linux o/s use the manual option so you can select the separate home partition and use a different username on each so i.e Bob1 & Bob2, this will allow you to have 2 separate home folders in the one home partition without each linux o/s getting the various config files stored at hidden files in your home dir mixed up.

---

### Post by oldos2er on 2009-04-08
You'll only need one Linux swap partition; how large it should be depends on whether or not you plan to use the hibernate function. If you're going to hibernate, use 8GB. If not, a 512MB partition should be sufficient.

 Having a /home partition is nice, but only if you're going to be running a distro on a more or less permanent basis. If you're going to be distro-hopping, I'd say keep it all in one / partition, but that's just my opinion.

---

### Post by Tom Gilroy on 2009-04-08
Thanks for the suggestions so far. 

Therion, I'm not really concerened about fuss, but I appreciate your comment. I've tried a few live CDs so far, I really think I'd like to get a better feel for a few of the ones I've tried. MEPIS seems very, for example.

lisati, I think I'm going to stick with the 64-bit system. More work doesn't really bother me, the primary reason I decided to start using Linux was to get a better feel for working with computers. I have put alot of thought into this, I really don't want to muck it up!

---

### Post by tlois on 2009-04-08
I came across this guy's blog the other day (who knows why) and maybe it would be of interest to you.  

I think it is a good idea to get them totally on your hard drive to get the real feel for them. 

[http://hydtech.wordpress.com/2009/03/26/lenovo-thinkpad-x60-with-fedora-10-opensuse-11-ubuntu-904-and-windows-xp/](http://hydtech.wordpress.com/2009/03/26/lenovo-thinkpad-x60-with-fedora-10-opensuse-11-ubuntu-904-and-windows-xp/)

---

### Post by Tom Gilroy on 2009-04-08
Thanks for that, actually guys thanks for everything so far, certianly food for thought. 

Some further questions. Which partitions should be primary and which should be logical? I'd imagine the operating systems should be on primary partitions, with home and swap on logical partitions of another primary partition? Or something else possibly?

---

### Post by mtopro on 2009-04-08
My two cents..  I had a 64bit nice laptop that came with Vista and I wanted 64bit Ubuntu in dual boot.  Linux writes to the disk nicely, but Vista fragments it's disk space.  Anyway I think thats why the boot partition may have been overwritten one time when I was working in Vista.  What a pain if you don't have the Vista CD and just a full manufacturer install CD.  You're looking at having to reinstall/repartition the entire disk then reinstalling Linux too.

I went all the way Linux but have some experience on other computers and knew I wouldn't miss it too much.  However now I use VirtualBox.  A great program.  Experience the best of both worlds from the Linux environment.  This is the most stable setup I've ever had.

My suggestion would be to get an external hard drive for your 'home directory' and a second one for backup.  This way you can always get your data no matter what happens, and share with both distros.

Also I read some advice somewhere, expect to muck up your first install.  Maybe even second or third.  It helps you to learn, and as long as you have a solid backup it's not that big of a deal.  I can install a new Ubuntu OS the way I like it setup in 30min.  I just keep notes each time and keep refining the process.

Anyway. Hope that helps. :)

---

### Post by Tom Gilroy on 2009-04-08
Thanks. I have the Vista reinstallation disc (along with separate discs for device drivers etc), so I'm sure it will see some exercise soon! I know I probably will muck up the first install, but I've always felt that careful planning allows us to muck things up minimally. 

This has been very helpful, thanks guys.

---

### Post by oldos2er on 2009-04-08
> **Tom Gilroy said:**
> Some further questions. Which partitions should be primary and which should be logical? I'd imagine the operating systems should be on primary partitions, with home and swap on logical partitions of another primary partition? Or something else possibly?

 Only Vista needs a primary. If I were you , I'd keep the rest logical.

---

### Post by lisati on 2009-04-08
One thing I forgot to mention, it's probably "obvious": The laptop I use 64-bit Ubuntu on came with Vista, a couple of partitions used for recovery and installation, but no recovery disk(s). One of the first things I did before tinkering with the software on it (including installing Ubuntu) was to make a backup of the recovery partition - Toshiba had thoughtfully provided a utility for this purpose.

---

### Post by Tom Gilroy on 2009-04-08
Thanks. I've a pretty good idea what I should be doing now, I think. Any other pearls of wisdom any of you wish to share?

---

### Post by Tom Gilroy on 2009-04-08
Hi guys, I'm having trouble partitioning. When I start up the Ubuntu installer, it doesn't give me the option of resizing my existing Vista partition. I tried booting the GParted live CD and it had the same problem. Neither partitioner can read how much free space is left on that partition, and therefore refuses to resize it. Any ideas how to fix this other than formatting all partitions and reinstalling Vista?

---

### Post by oldos2er on 2009-04-08
I've no personal experience with this, but I have read from knowledgeable people in this forum that you should use Vista's own disk management software to manipulate its partition, otherwise Vista gets "upset."

---

### Post by Wobblybob on 2009-04-09
I had problems with Vista and found this thread helpful

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Martin

---

### Post by wilcan34 on 2009-04-09
Thanks for the info.
Am doing a dual boot with xp snd ubuntu,been at it for months,ages,lots of reading in the forum do noe am going to give it a go.
Made a lot of stuffups and was good to see your post saying do not expect to get ot right first time,hearing that gives me confidence.
!
Thanks.
Will let you know how it goes.
G

---

### Post by wilcan34 on 2009-04-09
well,The dual boot worked.
Installed win xp last nite and this morn just put the ubuntu disc in and see what happens.
Am now able to access both xp and Ubuntu from the boot loader and they both run well.
Have 2 HDD,one 6g and one 30g.
Install the xp on the 6g and the Ubuntu on the 30g,though the xp keep saying not enough room,running low on memory.
Though 6g would be enough?
More reading I guess.
Anyway,can access both systems and the exercise worked.
Thank you to all the forums and the people who offered advice and Help.
G

---

### Post by cguy on 2009-04-10
Why would you need a swap partition when you have 8GB of ram? :w00t:

I have only 2 GB, no swap partition and never had any problems, although I had Matlab, OpenOffice, VirtualBox with WinXp and a few more open @ the same time.

Swap is for those with just a little RAM.

---

### Post by mtopro on 2009-04-11
> **Tom Gilroy said:**
> Hi guys, I'm having trouble partitioning. When I start up the Ubuntu installer, it doesn't give me the option of resizing my existing Vista partition. I tried booting the GParted live CD and it had the same problem. Neither partitioner can read how much free space is left on that partition, and therefore refuses to resize it. Any ideas how to fix this other than formatting all partitions and reinstalling Vista?

Tom,
Have you tried defragmenting your Vista partition.  As I mentioned previously, Windows fragments the drive.  If you don't have a large enough continuous segment due to fragmentation, you may not be able to create the partition..

---

