---
title: "BACKUP Program for UBUNTU?"
date: 2008-11-10
forum: General Help
---

### Post by Bigs11 on 2008-11-10
Basically, I would like to know what's recommended to backup a ghost image of my Ubuntu partition?

Also, can anyone solve my problem as outlined below?
I am now running Ubuntu 8.10, and in the past have used Acronis True Image to back up any type of partition. eg:- NTFS, FAT32, EXT3.
I tried to back up my Ubuntu 8.10 partition (after installing it to an IDE internal drive), to an external USB drive.
Whether I use the Boot CD for Acronis, or do a live backup from inside Windows (which I've successfully done many times in the past),
the whole system just locks up after about 15 mins.
The first 10-15 of backup is incredibly slow.
I also get a warning message from Acronis saying "Some partitions contain errors and can be imaged only sector-by-sector".

Any ideas, anyone?

---

### Post by kaibob on 2008-11-10
Take a look at these threads:

[http://ubuntuforums.org/showthread.php?t=964793&highlight=acronis](http://ubuntuforums.org/showthread.php?t=964793&highlight=acronis)

[http://ubuntuforums.org/showthread.php?t=899190&highlight=acronis+trueimage](http://ubuntuforums.org/showthread.php?t=899190&highlight=acronis+trueimage)

The problem is that Intrepid uses 256-byte inodes which are not compatible with True Image Home.

---

### Post by scouser73 on 2008-11-11
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by Bigs11 on 2008-11-11
> **scouser73 said:**
> What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

I will have a look at those links when I get home, and thanks for the help.
I understand now why Acronis isn't working with the Ext3 partition.

Earlier today I did a apt-get install of Mondo, but for the life of me can't see it anywhere in any of the menus.
So I looked in Synaptic, and it was there, so uninstalled and reinstalled it, logged off and on, but it still doesn't show up anywhwere.
What am I doing wrong?

---

### Post by scouser73 on 2008-11-11
I had to Google what Mondo actually was, I see it's similar to Remastersys, could it be named something else in the lists. I ask this because when I have installed Gparted, it shows in the lists as Partition Manager (or similar). Just a guess at the moment.  Anyway good luck with Remastersys and APTonCD, and let me know if you need any further help with it.

---

### Post by Bigs11 on 2008-11-12
Still can't find Mondo anywhere in my Menus.
Also did a apt-get install of Partition Image, which was successful,
but that also does not show up in menus.

So then, I made a boot cd of System Rescue CD, which has Part Image on it.
Ran the GUI after booting off it, then launched Part Image.
I can manage to get an image of selected partition going, but can someone tell me if I'm typing the right info for the file destination?
I've been using the path that Gparted shows, eg:- "/dev/sdd5/Ubuntu"
"Ubuntu" being the file name I've selected.
If I just use "/dev/sdd5", I get a message saying there's not enough space.
Dunno what I'm doing wrong, but the time I've spent, I could have reformatted my Ext3 partition to 128node,
reinstalled Ubuntu, and then used Acronis True Image.

---

### Post by Slim Odds on 2008-11-12
Clonezilla

---

### Post by Bigs11 on 2008-11-13
> **Slim Odds said:**
> Clonezilla

Why didn't you say that 2 days ago. :)

I'm sure Part Image works fine, but after trying Clonezilla (did both a backup and restore)
I think that's the one I'll keep using.

Thanks for the help.

---

### Post by shane19174 on 2008-11-14
Just wondering, was clonezilla able to restore GRUB for you? I tried it recently because Acronis no longer works, and I had to reinstall GRUB with the help of an Intrepid live Cd after doing the restore with clonezilla. Not a big deal for me, but nothing I can recommend to my wife or others with only Windows experience (and no desire or time to play around).

Thanks

---

### Post by Slim Odds on 2008-11-14
> **Bigs11 said:**
> Why didn't you say that 2 days ago. :)

I'm sure Part Image works fine, but after trying Clonezilla (did both a backup and restore)
I think that's the one I'll keep using.

Thanks for the help.

I'll try to improve my ESP skills...

Glad to help

---

### Post by rbmorse on 2008-11-14
Clonezilla, a convenient and rather clever front-end for Partimage and a couple of other disk-imaging utilities, defaults to backing up the MBR and track0 information for each disk it backs u.

So yes, it will backup and restore an MBR containing the GRUB bootsector.

---

### Post by Bigs11 on 2008-11-14
> **shane19174 said:**
> Just wondering, was clonezilla able to restore GRUB for you? I tried it recently because Acronis no longer works, and I had to reinstall GRUB with the help of an Intrepid live Cd after doing the restore with clonezilla. Not a big deal for me, but nothing I can recommend to my wife or others with only Windows experience (and no desire or time to play around).

Thanks

I think I took the option, when restoring the Clonezilla image, to not touch MBR with Grub.
In other words, I only restored the Ubuntu partition, and not the MBR.
And I think if Grub is on the MBR of another HDD, which it is in my case, then it won't get backed up with the Clonezilla backup.
Just forget what the options were when backing up.


Sorry, didn't see above Post!!

---

### Post by wersdaluv on 2008-11-14
As for me, I just use Dropbox. hehe. I put my program files on it then made a link to my ~/

---

### Post by scenerio on 2008-11-15
Can I use clonezilla with commnand line, or is there a better option? My hard drive (ubuntu drive) is about to fail as it sometimes does not load on start-up and is 10+ years old. I just bought a 500 gig USB simpledrive so that I can create a clone of my current ubuntu drive (28 gig) and if it fails I could then use my backup to load it onto a new hard drive or just boot straight from my USB. This computer currently has windows on the master drive and Ubuntu 8.04 on the slave. I use the grub boot loader to select which operating system I want at startup. I have only been using Ubuntu and command line for a few months so I am new and rusty. Any suggestions would be appreciated.

---

### Post by Slim Odds on 2008-11-15
> **scenerio said:**
> Can I use clonezilla with commnand line......

There are two ways to use Clonezilla:
1) Bootable CD
2) USB drive.

The bootable CD is the easiest.

---

