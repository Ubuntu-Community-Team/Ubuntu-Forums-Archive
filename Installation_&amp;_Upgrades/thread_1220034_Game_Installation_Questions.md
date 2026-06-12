---
title: "Game Installation Questions"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by Ericj1186 on 2009-07-22
This is a two-part question.

I have two hard drives on my computer, one is 106GB and one is 500GB.  The 106 GB one is split 30/60 with Ubuntu to Windows.  The 500GB, when I am on Windows, is my folder to install things to such as Steam, and any programs really.

First part, how do I install games and such to the second hard drive on Ubuntu?  I currently have files for Penny Arcade: On the Rain-Slick Precipice of Darkness, episodes 1 and 2, on the drive, but when I click the file to load it, nothing happens.

Second part, is there any way I can set my repository downloads (ala Synaptic and Apt-Get) to download and install in the second hard drive?  I am not suffering from a lack of space, yet, but I have a feeling it will happen sooner rather than later.

Any advice?

---

### Post by dstew on 2009-07-22
When installing any program on a Linux system, the program does not install to a single place, like it does in Windows. Pieces of the program go to various folders according to the [standard scheme]("http://www.tuxfiles.org/linuxhelp/linuxdir.html"). At least, this is what happens with Debian packages. So, if you are running out of room in your Ubuntu filesystem, you might need to expand it somehow.

If you cannot expand the Ubuntu root filesystem because of the size of your disk, an alternative is to use logical volume management to create one large logical partition out of several smaller ones that can be spread across many disks. It is a bit tricky to do on an existing system, but here is a [How-To]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall") about it.

The bulk of the code for installed programs goes into /usr, so you could also create a new partition for the /usr directory on the big disk. Here is a [How-To]("http://www.psychocats.net/ubuntu/separatehome") about moving a directory to a new partition. It involves the /home directory, but the same method should work for the /usr directory.

---

### Post by Ericj1186 on 2009-07-22
Hmm.  I am still at about 30GB, but I just wanted to solve that problem early.  Thanks for the help.  Also, I wasn't sure if I was following correctly, but would I be able to take about 100GB from my second HDD and link it to the Linux one on the first drive?  I think that's what you were saying those links did, but I wanted to be sure before I started trying stuff.

Also, I have Penny Arcade installed on the second HDD, but there was nothing telling me how to install/play the game.  I found only one file that looked like the .bin, but I have no idea how to cd to that drive.  Any suggestions?

---

### Post by dstew on 2009-07-23
> would I be able to take about 100GB from my second HDD and link it to the Linux one on the first drive?Yes, that is what Logical Volume Management does. It is not very easy to do, as you can tell from the links, especially on an already-installed system, but that is what you can do with LVM.> Also, I have Penny Arcade installed on the second HDD, but there was nothing telling me how to install/play the game.How are you trying to install the game? Where did you get it from? What is the name of the file you have? Most programs on an Ubuntu system are installed using the Synaptic graphical interface, which is a front-end for the command line apt-get and dpkg systems. Almost always, you will be installing Debian packages. Trying to install software that is not packaged is an advanced technique.

To cd to the partition on your other disk, you need to mount it first. Look in the Ubuntu Places window and see if the partition is there. If so, you can right-click it, and choose "Mount Volume". After it is mounted, you can use Nautilus to navigate to it.

---

### Post by Ericj1186 on 2009-07-23
> **dstew said:**
> Yes, that is what Logical Volume Management does. It is not very easy to do, as you can tell from the links, especially on an already-installed system, but that is what you can do with LVM.How are you trying to install the game? Where did you get it from? What is the name of the file you have? Most programs on an Ubuntu system are installed using the Synaptic graphical interface, which is a front-end for the command line apt-get and dpkg systems. Almost always, you will be installing Debian packages. Trying to install software that is not packaged is an advanced technique.
 
To cd to the partition on your other disk, you need to mount it first. Look in the Ubuntu Places window and see if the partition is there. If so, you can right-click it, and choose "Mount Volume". After it is mounted, you can use Nautilus to navigate to it.
 
Going through the links, it was a bit over my head, but I will read up on it a bit more.  I want to partition my second hard drive (the 500 GB) into two ~250GB drives, with one linking to Ubuntu.  Thanks for getting me started.  I'll research a bit more.
 
The game comes from Penny Arcade's game server: Greenhouse Games.  The file came as a tar.gz.  I unpackaged that on my second hard drive, and when I did they had two files called "Rainslick", but I didn't see any extensions.  When I get home, I'll give you the exact extension, but I believe they were .bin files.

---

### Post by tswann on 2009-07-23
I'm having the same problem.  I've just downloaded a game which when extracted appears as a .bin file and a .cue file.  I've been trying all day to mount these but it's not working.  So far, I've installed bcchunk and iat through the synaptic package manager but nothing happens (they don't appear in the applications and when I try to open the files with them it doesn't do anything at all).  I read that I should use these programmes to turn the files into .iso so that I can use kiso to mount them.  I've also tried cdemu but can't get it to install.  I put the sources into the source window but they aren't being recognised.

---

### Post by dstew on 2009-07-23
A tar.gz file is just an archive (tar = archive, gz = zipped or compressed). A tar.gz file that has a program may contain source code that must be compiled to be used, or it may contain pre-compiled binary files. Installing from software this way is an advanced topic. You would need to look at the installation instructions contained withing the tar.gz file, or go to the software creator for instructions. If you need to compile it, here is a [How-To]("http://ubuntuforums.org/showthread.php?t=323939").

---

### Post by Ericj1186 on 2009-08-02
So, I have been reading through this stuff a lot before I get started, and I wanted to know, how likely am I to lose all my data?  It says to back-up my stuff, which would be no problem as I have a 1TB external HDD, but how likely is it to happen?

Also, the guides I am reading are a bit confusing for LVM.  I simply want to add 220GB from my second hard drive and link it to the first hard drive, so when I install repo games/games from the internet, I don't have to worry about space, but the guide seems to be for moving my /home or even my /boot.  Can someone give me a bit more guidance here?

---

