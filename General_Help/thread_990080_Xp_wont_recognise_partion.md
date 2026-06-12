---
title: "Xp wont recognise partion"
date: 2008-11-22
forum: General Help
---

### Post by larrikin71 on 2008-11-22
I am running a 100% Ubuntu 64bit machine, but unfortunately i need to install Window$ XP for game purposes ( i stress unfortunately). Anyhoo i have a 180gb HDD which is partitioned thus :


ext3     131.69Gib
fat32     48.83Gib
Extended   5.79Gib
Linux-swap 5.79Gib

Now the problem i have is when i try to install XP the installer only picks up one partition of 131072mb as unknown. I tried formatting the fat32 partiton as NTFS and FREE SPACE but that didnt work either.

How do i get XP to recognise the designated partition?

---

### Post by Bucky Ball on 2008-11-22
131072mb as unknown

That is your EXT3 partition (131gb) and windoze has not a clue about that format so the 'unknown' is correct. Your fat32 partition should be the only thing it will recognise, I would advise backing up and installing windoze first, then ubuntu. It is easiest in the long run. There are ways around this problem, but you are going to need to free up a partition to install windoze whichever way you go. One way would be backup the fat32, kill it in ubuntu gparted (delete), leave it as free space and your windoze installer should pick that up. The you could make a 10gb for wdoze and the rest for whatever. Personally, I would start again with a beverage of choice, a piece of paper and a pen and .

See, the problem is Windoze wants the first partition, so if you don't put it there, you need to trick it into thinking you did.

ps: windoze needs to be on a primary partition, incidentally. That is another reason you are going to need to create a partition.

---

### Post by sirjoebob on 2008-11-22
XP should see the fat partition. I am not sure why it wouldn't.

---

### Post by larrikin71 on 2008-11-22
to be honest if i could get Age of Empires III  and a couple of other games to work under wine i would quite happily chuck windoze in the trash.

---

### Post by sirjoebob on 2008-11-22
> **larrikin71 said:**
> to be honest if i could get Age of Empires III  and a couple of other games to work under wine...

According to the [winehq app database]("http://appdb.winehq.org/appview.php?iAppId=2441"), Age of Empires III should work great in wine. That may be a good option for you. Wine has come a long way in the last few months. Left 4 Dead demo worked great :guitar:

---

### Post by Bucky Ball on 2008-11-22
> **larrikin71 said:**
> to be honest if i could get Age of Empires III  and a couple of other games to work under wine i would quite happily chuck windoze in the trash.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795)

---

### Post by sirjoebob on 2008-11-22
> **Bucky Ball said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3795)

That's better than the one I posted and includes a fairly painless-looking howto.

---

### Post by lukjad on 2008-11-22
There's also something called Crossover Linux for about $40. I've never used it, but it is said to be able to run games.

---

### Post by Bucky Ball on 2008-11-22
Sorry sirjoebob, didn't see you pop in before me there. Yep, all reports seem to say AoE III working fine. Not a gamer myself so couldn't validate this personally ... good luck, might save yourself some hassle, larrikin71 ...

---

### Post by arashiko28 on 2008-11-22
Why don't you install VMWare ot VirtualBox and install windows inside linux, that way, you can play your games in "linux".

---

### Post by sirjoebob on 2008-11-22
> **lukjad007 said:**
> There's also something called Crossover Linux for about $40.

From my understanding, crossover is not that much better than wine to warrant spending $40 on it when WINE is free and easily downloaded from the repos.

---

### Post by lukjad on 2008-11-22
I wouldn't know as I have never tried it in comparison with WINE.

---

### Post by RizSilverthorn on 2008-11-22
> **sirjoebob said:**
> From my understanding, crossover is not that much better than wine to warrant spending $40 on it when WINE is free and easily downloaded from the repos.

The main advantage I have found to owning a license for Crossover Pro is that each application can be installed separately from any others you may have. If I try one and it does not work, I just delete the 'bottle' (their term for an individual wine configuration) I created for it without worrying about the rest. Also, if application x requires winXP and application y needs Win98, keeping them separate means I can have both. You can, of course, install several apps into one bottle if you need to - I have DVDDecrypter & DVDShrink installed together for example. As far as I'm aware, wine installs everything together.

Ohh, and now there is Crossover Games which means I have ditched the not so good Cedega for my WoW addiction. But this is straying from the original question.

VMWare, VirtualBox, etc are not able to run most games atm due to the lack of 3D acceleration/DirectX support.

If you want to dual boot WinXP/Vista and Linux, I always thought WinXP must be installed into the first primary partition of your drive and installed before Linux. However [this guide]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") shows how to dual boot with XP installed after Linux. I haven't tried it myself so good luck!

---

### Post by larrikin71 on 2008-11-22
Thanks for the repllies, i have tried both VMWare and Wine, cedaga and have issues with all of them so it looks like i am gonna have to go ahead with XP. So i guess i am back to square one, is there n e way for the xp installer to recognise the partition i have created for it??

Failing that i have installed alot of software on my Ubuntu machine so i really do not want to wipe it off, how would i go about doing a total backup and a reinstallation of my Ubuntu system if i was to wipe my machine and start over with an Xp installation first???

Is there a recommended program or method for doing this?

---

### Post by RizSilverthorn on 2008-11-22
> **larrikin71 said:**
> Failing that i have installed alot of software on my Ubuntu machine so i really do not want to wipe it off, how would i go about doing a total backup and a reinstallation of my Ubuntu system if i was to wipe my machine and start over with an Xp installation first???

Is there a recommended program or method for doing this?

Not sure about the backing up of all the installed programs you have. If I ever need to reinstall Ubuntu I reinstall the whole lot. I keep my home in a separate partition so all my settings are saved though. If you do not have a separate home partition, copy the contents (including the hidden files & directories) to a safe location first, then copy them back after installing Windows and re-installing Ubuntu.

Alternatively, if you do not have anything worth saving in your FAT32 partition and it is primary not logical, just delete it in the Gnome Partition Editor, then boot from the Windows install CD. It will detect that there is free space and offer to install there.

Take note of what the link I gave before says about drive letter assignment in windows. From experience, if the windows installer tries to install into other than a C: partition because it has to create a new one, create the partition in the windows installer, then press F3 to abort the install. Reboot and re-run the installer. It will usually find the newly created partition and assign it the correct drive letter - C:

---

### Post by Bucky Ball on 2008-11-23
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

That might be what you are after ...

---

### Post by larrikin71 on 2008-11-23
k,

   Problem is solved, it seems that windozo xp wont recognize the partition unless it is of the sp2 or above variety. I installed using a sp3 version of Windoze an all worked well... So if anyone else encounters this problem thats your solution.
:guitar:

   Unfortunately i had no success with cadega, or wine to run those games which is a real shame as i have had resort to back to an inferior operating system for my gaming purposes.

---

### Post by Bucky Ball on 2008-11-23
Could you mark this thread as 'solved' from 'Thread Tools' so others might find a fix here. :)

---

### Post by sedawk on 2008-11-23
Another solution might have been to change the "activation" flag with fdisk. Setting the FAT32 partition active, not the Ext3 one might be one of the tricks to make the XP installer work.

Another alternative would have been to install XP from inside a virtual PC that uses the FAT32 partition as drive "C:".
Gaming doesn't work inside the virtual PC (DirectX support sucks with all virtual PCs), but the installation should work and then, after adding the new OS to grub, it should boot on the real hardware.
(But that only works if your XP is not dongled to the hardware or XP does
 a normal installation, not a recovery that messes up the whole disk ...
 who said Linux is difficult to install?)

---

