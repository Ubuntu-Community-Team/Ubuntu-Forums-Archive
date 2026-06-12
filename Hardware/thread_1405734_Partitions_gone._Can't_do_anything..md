---
title: "Partitions gone. Can't do anything."
date: 2010-02-13
forum: Hardware
---

### Post by consuminSilence on 2010-02-13
I have no 'C:' drive or whatever. NOTHING. No partition. I can't start up my Wins7. My drives and partitions are gone!

 It all started when I was installing Ubuntu the advanced way (I didn't know what I was doing) and when it was installing into the partition or something, I pulled the plug, because it was taking too long (I know, what a f***ing nub). Now, I have nothing. I can access the F1-f12 menu Bios thing. But, nothing will come up afterwards. I don't have a partition. I cant start up the laptop. Help...

Now, how can I gain back my 'C:' drive, partition, or whatever, main partition!? 

I'm sorry, I surfed through many, many threads. No help. No savior. No anything. Is there anyone smart enough to help this nub? I'll try to not be as begging, nub-ish, and explain all the details if asked. 

Please and thank you fellow internetlings!

---

### Post by balaknair on 2010-02-13
This looks as if it's FUBAR. It depends on what stage of the install the plug was pulled and what changes you had made to the default 'safe' partitioning scheme. What boot error message do you get? Is it something like 'No Bootable Medium Found' or something similar?
If your hard drive isn't dead or you haven't wiped the C:\ partition, it might be possible to save at least some of your data.
What I would do under similar circs is boot from the Ubuntu LiveCD and see if the drive can be accessed. 
If yes, then you can copy essential personal files onto a USB drive, and then try to recover the hard drive.
If you can't access the drive with LiveCD, then maybe the partition table is corrupted. If you haven't tried to overwrite the disc, it should be possible to recover it using testdisk. I recommend removing the hard drive and connecting it to another PC which has Ubuntu installed on it to run testdisk, but you can also run it within a LiveCD session. You will need internet access to download and install testdisk though.

In the spare PC/livecd session, install testdisk with this command
*sudo apt-get install testdisk*

Then run it with the command 
*sudo testdisk*

*Now you see a list of actions choose from; choose 'Create'-->
*Testdisk will now scan connected drives and list drives and partitions with sizes.
*Select the drive(they will be listed sda, sdb, sdc and so on) you want-->
*Select what type of partition table it uses if the correct is not automatically selected(in this case it should probably be 'Intel PC')-->
*You get a list of actions to choose from; choose 'Analyse'-->
*Wait, be patient and don't pull the plug; search can take a long time depending on the size of your hard drive.
*You will see a list of partitions on the disc. Choose 'Quick Search' to search the filesystem to get the actual partition tables. It should return a list of partitions. You can then choose to do a 'Deeper Search' if you think anything is missing. In this case since it's a boot partition you need and your laptop might have had a backup boot superblock, do the deep search.-->
*Once you have completed the deep search, and have verified the resulting list(all partitions listed, sizes correct), choose 'Write'; Testdisk will repair the corrupted partition table and show you the completed list at the end-->
*Now you can 'Quit' testdisk and shut down the PC, remove the LiveCD and try booting from the hard drive.

If everything went well, you should now have a functioning hard drive with a C:\ drive and all that stuff.

Hope this works for you.
All the best

---

### Post by consuminSilence on 2010-02-13
> **balaknair said:**
> This looks as if it's FUBAR. It depends on what stage of the install the plug was pulled and what changes you had made to the default 'safe' partitioning scheme. What boot error message do you get? Is it something like 'No Bootable Medium Found' or something similar?
If your hard drive isn't dead or you haven't wiped the C:\ partition, it might be possible to save at least some of your data.
What I would do under similar circs is boot from the Ubuntu LiveCD and see if the drive can be accessed. 
If yes, then you can copy essential personal files onto a USB drive, and then try to recover the hard drive.
If you can't access the drive with LiveCD, then maybe the partition table is corrupted. If you haven't tried to overwrite the disc, it should be possible to recover it using testdisk. I recommend removing the hard drive and connecting it to another PC which has Ubuntu installed on it to run testdisk, but you can also run it within a LiveCD session. You will need internet access to download and install testdisk though.

In the spare PC/livecd session, install testdisk with this command
*sudo apt-get install testdisk*

Then run it with the command 
*sudo testdisk*

*Now you see a list of actions choose from; choose 'Create'-->
*Testdisk will now scan connected drives and list drives and partitions with sizes.
*Select the drive(they will be listed sda, sdb, sdc and so on) you want-->
*Select what type of partition table it uses if the correct is not automatically selected(in this case it should probably be 'Intel PC')-->
*You get a list of actions to choose from; choose 'Analyse'-->
*Wait, be patient and don't pull the plug; search can take a long time depending on the size of your hard drive.
*You will see a list of partitions on the disc. Choose 'Quick Search' to search the filesystem to get the actual partition tables. It should return a list of partitions. You can then choose to do a 'Deeper Search' if you think anything is missing. In this case since it's a boot partition you need and your laptop might have had a backup boot superblock, do the deep search.-->
*Once you have completed the deep search, and have verified the resulting list(all partitions listed, sizes correct), choose 'Write'; Testdisk will repair the corrupted partition table and show you the completed list at the end-->
*Now you can 'Quit' testdisk and shut down the PC, remove the LiveCD and try booting from the hard drive.

If everything went well, you should now have a functioning hard drive with a C:\ drive and all that stuff.

Hope this works for you.
All the best

Thanks for replying, I shall try this as soon as possible. I will get back to you on this!

Is there any way I can just create a new C: partition? I can access the "demo" Ubuntu, but it isn't installed. Whenever I try to install the Ubuntu it says: No root file system is defined. Please correct this from the partitioning menu." But in my partition table (or whatever) I have nothing in there. It's empty. 

Looking forward for you're advice!

---

### Post by balaknair on 2010-02-13
By 'demo' Ubuntu, I assume you're referring to the LiveCD session(booting from the Ubuntu CD). Right?

Installing Ubuntu at this point isn't advisable at this point if you want to recover your old Windows 7 stuff. You'd end wiping the old data. So try the testdisk method above before going for an Ubuntu install. In fact for best results avoid doing anything to the hard disk till you have had a chance to run testdisk.

If you want to install Ubuntu(for eg. if testdisk recovery didn't work for you), you need to consider whether you want to have both Win 7 and Ubuntu as dual boot(choosing which OS to boot from a list at system start-up), or if you want to install Ubuntu as the only OS. If you want a dual-boot setup, install Win 7 first and then install Ubuntu, because Windows cannot handle being installed alongside another OS.

So my advice is
1) run testdisk first
2) If your Win 7 setup now works, you can proceed to install Ubuntu
3) If Win 7 doesn't work, try to repair/reinstall Win 7 using the Win 7 DVD, and then proceed to install Ubuntu

Now for the root file system thing. That usually only comes up if you're doing a manual partitioning. The root partition is the top level partition on Linux/Unix OSes, denoted by **/**. All other devices, folders, system files and other files, are subfolders of the root partition(vaguely like the C:\ drive in preinstalled Windows) and are represented like **/home** or **/dev/media/cdrom0**. When installing using the automatic settings, Ubuntu sets up everything for you, but when setting up partitions manually, you have to tell the installer where you want to put /
 
To do this in the partitioner, create a new partition in the space you want to install Ubuntu into, by right clicking the empty space > new partition--> You get a pop-up box where you can set the size of the partition(set at least 5 GB for the root partition, preferably 10 GB) and filesystem type(default for Ubuntu 9.10 is ext4); there will also be an option to set **mount point**, where you can set it as /, /home, /var and so on. You need to set a partition as **/**, and you can choose whether or not to have seperate a **/home** partition(for your user files, like the C:\Documents and Settings\ folder in Windows).

More info on assigning a root partition and a seperate /home partition is available here(with screenshots)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Hope that was helpful.

If there's any other info or clarification you need, just reply here.

All the best.

---

### Post by consuminSilence on 2010-02-13
> **balaknair said:**
> By 'demo' Ubuntu, I assume you're referring to the LiveCD session(booting from the Ubuntu CD). Right?

Installing Ubuntu at this point isn't advisable at this point if you want to recover your old Windows 7 stuff. You'd end wiping the old data. So try the testdisk method above before going for an Ubuntu install. In fact for best results avoid doing anything to the hard disk till you have had a chance to run testdisk.

If you want to install Ubuntu(for eg. if testdisk recovery didn't work for you), you need to consider whether you want to have both Win 7 and Ubuntu as dual boot(choosing which OS to boot from a list at system start-up), or if you want to install Ubuntu as the only OS. If you want a dual-boot setup, install Win 7 first and then install Ubuntu, because Windows cannot handle being installed alongside another OS.

So my advice is
1) run testdisk first
2) If your Win 7 setup now works, you can proceed to install Ubuntu
3) If Win 7 doesn't work, try to repair/reinstall Win 7 using the Win 7 DVD, and then proceed to install Ubuntu

Now for the root file system thing. That usually only comes up if you're doing a manual partitioning. The root partition is the top level partition on Linux/Unix OSes, denoted by **/**. All other devices, folders, system files and other files, are subfolders of the root partition(vaguely like the C:\ drive in preinstalled Windows) and are represented like **/home** or **/dev/media/cdrom0**. When installing using the automatic settings, Ubuntu sets up everything for you, but when setting up partitions manually, you have to tell the installer where you want to put /
 
To do this in the partitioner, create a new partition in the space you want to install Ubuntu into, by right clicking the empty space > new partition--> You get a pop-up box where you can set the size of the partition(set at least 5 GB for the root partition, preferably 10 GB) and filesystem type(default for Ubuntu 9.10 is ext4); there will also be an option to set **mount point**, where you can set it as /, /home, /var and so on. You need to set a partition as **/**, and you can choose whether or not to have seperate a **/home** partition(for your user files, like the C:\Documents and Settings\ folder in Windows).

More info on assigning a root partition and a seperate /home partition is available here(with screenshots)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Hope that was helpful.

If there's any other info or clarification you need, just reply here.

All the best.

Yes... The LiveCD session - I can go on that. Sorry. Several minutes ago I found out that's what I meant. Lol.

No, I don't want to recover anything from my Wins7 anymore. I don't mind wiping all of my data really. I'm actually on a computer with a Wins7 and a Ubuntu. It's working perfectly. But the problem I'm having is in my laptop, you see, I dropped it a few weeks ago, it didn't start up. And I decided to install Ubuntu - to retrieve my files back, but I didn't know what I was doing so I turned the power off during, if I remember correctly, the manual partition (?). It's all coming back to me I think. I held the button and retried installing Ubuntu, but then my main C:\ is gone, so I couldn't install Ubuntu nor Wins7. I tried the Wins7 DVD thing, it says I can 'Load drivers' from a USB, DVD, or external... Well, where can I download these "drivers"? 

Well, you said that I need internet for installing the apt testdisk. In LiveCD, I did ctrl-alt-F2, after typing: **sudo apt-get install testdisk** it says: 
"Reading package list... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package testdisk"

I used the ctrl-alt-F2 method, because the panels didn't show up in my laptop. 

My only easy solution for this complicated problem is: I can just go get my laptop fixed. (How expensive would you think it'd be?) Do you recommend this solution, saving you the trouble of not getting a headache with this nub? Or I can just buy a new laptop? I think my guardians can afford another, but they say I am a money-burner (I broke one laptop before by dropping H2o on the keyboards, haha.)... 

Sorry to bother, you're a kind internet user. :)

---

### Post by balaknair on 2010-02-13
Try using Synaptic to install testdisk; it's in the Universe repositories, maybe you need to enable it(Settings> Repositories> check the box next to 'Community-maintained open source software(Universe)' and click reload)

As for the laptop, it's quite possible that the fall damaged something in the laptop, most probably the hard drive(hard disk drives are rather fragile things and susceptible to physical damage from impact or electrical variations while in use, though most laptop drives have shock protection built in to lessen the damage) can you hear any unusual sounds like loud whirring or clicking sounds when the hard drive is in use?
 It could also be the battery/power supply or any number of things, hard to say what it could be and how much it would cost to repair without opening the case. Unless you're comfortable with opening laptops and messing with the innards, I'd suggest you get someone qualified to take a look at it, especially since it could be more than one broken component in there.

In any case try testdisk if you can, especially if you have some data that you want to retrieve on the disk. Most service guys will just format the drive and reinstall Windows. It's easier for them than repairing Windows, especially if you have OEM discs or restore images with all the drivers etc preloaded.

So I suggest you
1) try testdisk one more time- if it works, backup your data and settings if you want to, and see if you can install Win7 and/or Ubuntu. It's an amazing tool, and I've saved terabytes of files for Windows using friends and colleagues with it. As long as your disc has some life left in it, testdisk is worth trying.

2) if it doesn't work(you can't install testdisk), give the LiveCD a good try, see if you can access all the stuff other than your hard drive, like sound, USB ports, battery charging/discharging times, DVD drives(use a data DVD or CD or an audio CD). This may help you identify damaged hardware. Then see if you can install Ubuntu and run it.

3) if testdisk installs but fails to repair the disc or if the laptop doesn't work even after repairing the disc , the disc is likely in bad shape or some other hardware component is broken. Again, try the LiveCD to pinpoint any troublesome hardware. If a lot of stuff seems to be failing, it would probably be safer to get a new laptop, since in my experience, laptops rarely last long after being repaired.
In this case you might be better off getting it looked at by a service tech for an assessment of the costs involved.

I hope it doesn't come to that.
Either way, lots of luck.

Take care.

---

### Post by consuminSilence on 2010-02-13
> **balaknair said:**
> Try using Synaptic to install testdisk; it's in the Universe repositories, maybe you need to enable it(Settings> Repositories> check the box next to 'Community-maintained open source software(Universe)' and click reload)

As for the laptop, it's quite possible that the fall damaged something in the laptop, most probably the hard drive(hard disk drives are rather fragile things and susceptible to physical damage from impact or electrical variations while in use, though most laptop drives have shock protection built in to lessen the damage) can you hear any unusual sounds like loud whirring or clicking sounds when the hard drive is in use?
 It could also be the battery/power supply or any number of things, hard to say what it could be and how much it would cost to repair without opening the case. Unless you're comfortable with opening laptops and messing with the innards, I'd suggest you get someone qualified to take a look at it, especially since it could be more than one broken component in there.

In any case try testdisk if you can, especially if you have some data that you want to retrieve on the disk. Most service guys will just format the drive and reinstall Windows. It's easier for them than repairing Windows, especially if you have OEM discs or restore images with all the drivers etc preloaded.

So I suggest you
1) try testdisk one more time- if it works, backup your data and settings if you want to, and see if you can install Win7 and/or Ubuntu. It's an amazing tool, and I've saved terabytes of files for Windows using friends and colleagues with it. As long as your disc has some life left in it, testdisk is worth trying.

2) if it doesn't work(you can't install testdisk), give the LiveCD a good try, see if you can access all the stuff other than your hard drive, like sound, USB ports, battery charging/discharging times, DVD drives(use a data DVD or CD or an audio CD). This may help you identify damaged hardware. Then see if you can install Ubuntu and run it.

3) if testdisk installs but fails to repair the disc or if the laptop doesn't work even after repairing the disc , the disc is likely in bad shape or some other hardware component is broken. Again, try the LiveCD to pinpoint any troublesome hardware. If a lot of stuff seems to be failing, it would probably be safer to get a new laptop, since in my experience, laptops rarely last long after being repaired.
In this case you might be better off getting it looked at by a service tech for an assessment of the costs involved.

I hope it doesn't come to that.
Either way, lots of luck.

Take care.

Alright, I'll do that tonight. For it is Chinese New Years tomorrow, my family and relatives are going to celebrate tonight. I wish you a Happy Chinese New Years. I'm glad you reply and tried to help me out. I'll come back to you, if not today, then tomorrow. :)

Happy Chinese New Year!

---

### Post by balaknair on 2010-02-13
OK.
Thanks for the wishes.
Good luck then, and I wish you a Happy New Year as well.
:D

---

