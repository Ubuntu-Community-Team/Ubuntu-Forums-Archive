---
title: "Advantages of Wubi versus VM"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by BobJam on 2009-07-13
I'm a noob and a soon to be refugee from Windows, so be gentle.

The reason I am fleeing Windows is not all that pertinent to this post, but suffice it to say that the recent automatic update controversy . . . "***It's confirmed: Windows may update unexpectedly***" found on the Windows Secrets newsletter explains it [here]("http://windowssecrets.com/comp/090702/") . . . drove me over the edge.  I'm furious over this because it actually happened to me.

I had been toying with the idea of switching to Ubuntu, but my own experience with the 500 pound Gorilla from Redmond pushing out updates when I had selected "Notify only" was the last straw.

So now I'm learning Ubuntu and am reading a lot of the stuff here on this forum.  I already have Ubuntu mounted on a VM within my Windows OS and am climbing that steep learning curve.

One of the issues I have for this transition is Quicken.  I use it for my banking, so there not being a Quicken version for Linux/Ubuntu, I will have to either maintain a Windows OS on a VM, or a Wubi installation of Ubuntu.

So, my question is:  What are the advantages and disadvantages of a Wubi installation versus a Windows VM?

From what I can tell, a Wubi installation would only be a mounting of Ubuntu within Windows and my machine would always boot into Windows first.  Whereas a VM of Windows within Ubuntu would leave Ubuntu as the "real" OS.  I'm leaning toward the VM solution, because I pretty much don't want a Microsoft OS as my main OS.  But I'm not sure yet.

Wubi seems like it might be a better way to make the transition from Windows to Ubuntu though rather then diving right in at the deep end.

I have two different objectives here, but they may be complementary.  On the one hand, I want to make a smooth transition to Ubuntu (Wubi), and on the other I want to maintain the use of Quicken (Windows VM, though Wubi would seem to allow the use of Quicken too).

What would those of you that are expeienced, or who have tried both, recommend?****

---

### Post by dandnsmith on 2009-07-13
I haven't tried it, but understand from what matter is available for reading, and many posts that wubi
a) sets up a filesystem as a Windows file within the Windows partition
b) arranges a dual boot with alternatives your original Windows and the Ubuntu you install.

So you can see, there is no element of the virtual machine here.

If you want to do the Virtual Machine you can do
1) Ubuntu under Windows
2) Windows under Ubuntu
and I would reckon to use VirtualBox for this (either way round)

There are forums at the VirtualBox site which have lots of posts dealing with problems and solutions (if you're lucky).

---

### Post by raymondh on 2009-07-13
Just some thoughts on the matter:

WUBI is meant as a trial for those wishing to try Ubuntu more than a live session.  As you now know, you install WUBI inside windows.  That means that the same limitations you have with windows that causes pooor performance will also be the same limitations you experience in ubuntu (i.e fragmented drive, etc).  

The same could be said for Virtualization... only if your hardware is not strong enough (low RAM, etc), your virtualization experience will be frustrating.

Lastly, if the host OS crashes (whether WUBI or VM installed), so does the guest (Ubuntu).

I use quicken (mac).... and I also Virtualize using both VMWare (mac) and virtualBox (ubuntu).  I leave windows alone and lonely because I only use it for 1 application. 

I would recommend that you keep your windows install *(if you wish, make it minimum in size with just quicken, a browser, anti-virus and the OS) *and then do a straight-up dual-boot.

---

### Post by BobJam on 2009-07-14
> **raymondhenson said:**
> I would recommend that you keep your windows install *(if you wish, make it minimum in size with just quicken, a browser, anti-virus and the OS) *and then do a straight-up dual-boot.So you mean neither Wubi or a VM within Ubuntu, but rather a dual boot?

I've never done a dual boot before, so Ill have to read up on that.  I assume I'd have to make a seperate partition for Ubuntu (I have plenty of disk space for that).  It certainly is an option, and an appealing one at that because I assume all my memory would go the chosen boot OS, and not be split between the OS and a running VM. Plus I wouldn't have the Windows instability issue for running Ubuntu.  But I've heard that dual boot configurations are problematic . . . though maybe that's with Windows OS's . . . like having a dual boot configuration with menu choices to boot into either XP or VISTA.

Curious . . . would the boot menu be a Ubuntu controlled thing or a Windows one?

Is there a discussion group here that addresses that dual boot stuff?

---

### Post by csabo2 on 2009-07-14
I'm not sure if you know but there are alternatives to Quicken, I believe one is called gnucash.  I havent used these or quicken so I dont have a side by side comparison, but i'm sure google does :)

---

### Post by BobJam on 2009-07-14
> **csabo2 said:**
> I'm not sure if you know but there are alternatives to Quicken, I believe one is called gnucash.  I havent used these or quicken so I dont have a side by side comparison, but i'm sure google does :)I have in fact looked at reviews of substitues, but most turn out to be negative.

Here's one (read the responses to the blog article, if you're interested that is):  [http://www.michaeldolan.com/1002](http://www.michaeldolan.com/1002)

And here's another:  [http://www.computer-juice.com/forums/f54/linux-ubuntu-quicken-15246/](http://www.computer-juice.com/forums/f54/linux-ubuntu-quicken-15246/)
It's a discussion thread.

My sense at the moment is that I'll probably want to continue to use Quicken, but I'm still Googling.  Thanks for the suggestion.

---

### Post by unlimitedz on 2009-07-14
> **BobJam said:**
> 
Curious . . . would the boot menu be a Ubuntu controlled thing or a Windows one?


Yes, you would want to install Windows first, then Ubuntu on a separate partition.  Keep in mind that Windows likes to be the first partition on the drive.   When you install Ubuntu, grub is installed as your boot loader, which is used to boot linux and windows.

---

### Post by BobJam on 2009-07-14
I found [this page]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") on how to install Ubuntu (well . . . it's for Ubuntu 8.04, but I assume the 9 release would work the same) as a dual boot on my WinXP machine.  Seems simple enough.  Are there any nuances I should watch out for, or are these instructions complete?****

---

### Post by unlimitedz on 2009-07-14
Before you move forward, do you plan on resizing the windows partition or do you already have separate partitions for ubuntu?  If you're going to re-size the windows partition, I suggest you run a couple of Defrags, and even a chkdisk before you do so.

---

### Post by steveneddy on 2009-07-14
Wubi was designed for Windows users to be able to "try" Ubuntu as an operating system without much knowledge or effort on the part of the end user.

**My suggestion is always to install Ubuntu first, then use VirtualBox to install XP (or your alternate OS of choice) and run XP inside of Ubuntu.**

The machine will operate better and be more secure overall than Ubuntu running on VirtualBox inside of XP.

I used to suggest dual booting, but with the release of VirtualBox and the "[COLOR=Red]**Seamless Mode**[/COLOR]" option it really is easy and fun to run two OS's at the same time.

This is what I do and it works great for my needs.

I would suggest running the VirtualBox from the website (version 3.0) and not the version from the repos.

(I may have just gone over your head, and for that I apologize)

---

### Post by BobJam on 2009-07-14
@unlimitedz,

I have PartitionMagic, and have two partitions.  One for the WindowsXP OS and Apps and the swap file (80GB, NTFS), and another for data (30GB, FAT32).  The OS and Apps only occupies 30GB (50GB free), and the data only occupies 20GB (10 GB free).

Should I use PM to partition for Ubuntu?  From those instructions I read, it looks like Ubuntu will do the partitioning itself on the fly.

How big should I make the Ubuntu partition?

Probably a good idea as you say to run Defrag first regardless of how I do the partitioning.


****

---

### Post by BobJam on 2009-07-14
@steveneddy,

Since I already have Windows XP on my machine, are you suggesting I remove it entirely?

I only have 1GB of RAM, so would running XP in a virtualBox split that memory?  If that's the case, wouldn't a dual boot be a more efficient use of that RAM (that's the max I can have BTW, so I can't add any more . . . had 512 to begin with and added another 512 . . . my machine is an HPze4700 laptop, vintage 2004).

---

### Post by unlimitedz on 2009-07-14
Yes, ubuntu will resize any partition you want to fit ubuntu on (on the fly, during the install).  As for size, this depends but usually 10 to 20GB for ubuntu should be plenty if you have a seperate drive for data.

I suggest doing a disk defrag because it will help move file fragments to the front of the partition that windows is installed on.  This in turn gives ubuntu more room to partition and reduces the chances of windows freaking out.

---

### Post by pythonscript on 2009-07-14
Running XP in a virtualbox would split that RAM, yes. When you make a virtual machine, though, you can choose how much RAM you want to give the virtual XP. I run XP in virtualbox on 256 MB of RAM and it works wonderfully. A dual boot would give you more RAM for XP, but do you really want to be booting back and forth between XP/ubuntu every time you want to use quicken? With a virtualbox, you can use all of your normal apps that run under ubuntu (word processor, browser, etc) and just open the virtualbox when you want to use quicken.

---

### Post by raymondh on 2009-07-14
> **BobJam said:**
> @steveneddy,

Since I already have Windows XP on my machine, are you suggesting I remove it entirely?

I only have 1GB of RAM, so would running XP in a virtualBox split that memory?  If that's the case, wouldn't a dual boot be a more efficient use of that RAM (that's the max I can have BTW, so I can't add any more . . . had 512 to begin with and added another 512 . . . my machine is an HPze4700 laptop, vintage 2004).

Hi BJ,

If I may .... Virtaulization, Wubi or dual-boot will suffice.  How comfortable are you in/with Ubuntu?  I suggest you keep XP until you are ready and comfortable to single-boot ubuntu/linux.

Some references if you decide to dual-boot until you get comfortable with Ubuntu:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

I would start by:

1.  Backing up my files.  There are no guarantees.
2.  Defrag windows.
3.  Download the ubuntu version you wish to try, burn the iso image at a slow speed (to minimize burning errors) and create the liveCD
4.  Boot into the liveCD and check for defects and hash
5.  Try out the liveCD without changes/installing .... this to see how it reacts/works with your system specs' and hardware.
6.  Once ready, decide on your install plan of action.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

-  I would take the space from the windows NTFS partition.  Ubuntu will require between 8-15GB for root (/), depending on how you plan to use your ubuntu.  I, for example, enjoy learning the free apps hence install a bunch of apps.

-  Should you decide to have a separate /home to keep your settings, tweaks, config files, etc. *(nice to retain should you decide to upgrade versions or have to do a ubuntu re-install)*, You would need to create/provide space for that as well

same link but browse at the left for the topic

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

-  Swap is dependent on you and the apps you choose to run as well as your hibernation/suspend practices.  I use 1.5GB but have 4GB RAM.  Some advocate 1X the max RAM possible in your system (as you might add RAM later).  The saying 1-2x RAM is valid for low-RAM situations.

-  Later on, we can just mount the storage partition so that both OS can read into it.

7.  Knowing how much space you want to give, you can either do the partitioning from the liveCD during the actual installation process or, create the partitions beforehand and/thus choosing to manually identify and set the installation.

-  If you decide to do a straight-up-no-separate /home, then when you get to the partitioning part, make sure you choose the right partition, selecting a guided resize and use the slider to set space preferences.

-  If you decide to create the partitions beforehand, let the forum know if you need assistance or a mini how-to.

Some refernces on partitioning:

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

As you'll note from the references, you can use the liveCD and its' partitioning editor (called gparted) by accessing system > administration > partitioning editor.

In gparted, remember to check that all the partitions are unmounted ... swap as well is swapped-off.

Lastly, keep in mind as you make your plan-of-action the 4-max partition rule per HD.  Either 4 primary or 3 primary + 1 extended.  Logical partitions live inside an extended and you can have as much logicals as you, your OS or Bios can take.

Apologies if I am being redundant as you may know all of this already.

Good luck.  back-up first.

---

### Post by unlimitedz on 2009-07-14
+1 raymondhenson, good advice.  ALWAYS have a backup of your important files whenever resizing partitions.

---

### Post by BobJam on 2009-07-14
@unlimitedz,

So can I take it that your recommendation is to let Ubuntu make the partition rather than prepare it with PartitionMagic?

Will 20GB accommodate not only the Ubuntu OS but any mainstream apps (wordprocessing, spreadsheet, database, etc.) that I will want to install for Ubuntu? And, yes, I have a separate partition for data with another 10GB of free space, so I'm assuming that would be enough for data storage (I also have several USB thumb drives for data storage).

BTW, thanks very much for the tips.

@pythonscript,

Same question I had for steveneddy: Are you suggesting I remove Windows entirely and just have Ubuntu as my only OS (with Windows of course in a virtual box)? Your tip about "***do you really want to be booting back and forth between XP/ubuntu every time you want to use quicken?***" does make some sense, but I only load up Quicken about twice a week so I'm not so sure that's much of a consideration. It's not like I'm in it every day. Nevertheless, I do appreciate your tip, and will give it some thought. And worse comes to worse and it gets too tedious, I can always transition to your suggested config, can't I?

@raymondhenson,

Hmmmm . . . you seem to think any alternative will meet my objectives.  Is there one that stands out above the others?

Unless Ubuntu throws me some curves that I can't swing at, I'm about as confident and comfortable as I can be at this stage. With the exception of the command line stuff, which is always intimidating to a noob but which can be dealt with I think, I'm actually very comfortable.

I'm a security freak (was a volunteer moderator on the McAfee forums for a while), so a Linux distro has a definite appeal to me. As I'm sure you know, Windows is like swiss cheese when it comes to security holes/exploits. I know that I will still have to be security conscious with Ubuntu, but I'm looking forward to being much less concerned.

Read that excellent post about "Is Ubuntu for you?" (or something like that . . . can't find it now), and I'm definitely taking a positive view on it. So, all in all, I'm pretty comfortable.

Yes, right now I plan to stay tethered to XP, especially since I'm in the middle of building a website (for my brother-in-law, not me) with Joomla. But I use Firefox, and web site building isn't that dependent on desktop platforms, so other than not wanting to juggle too many balls at the same time, I'm not that afraid to stray from Windows just as soon as I can.

Been putting off this transition for over a year now, and Microsoft finally gave me a push out the door so to speak, so want to use this most recent motivation to get 'er done.

I've got the pocket guide in .pdf, and have been reading it.  Very impressive.

Will check out the other links you gave.

Have been browsing this forum, and I've seen quite a few appealing topics for noobs. Seems like this forum itself is one of the best resources.

Backups and images (Acronis TI) have always been a part of my security approach, so no problem there.

Already have the Ubuntu LiveCD, so I'm ready there. Have run it a few times, and I can connect just fine and have no problems with other hardware, so am pleased with that.

Still haven't decided on my install plan of action.  May just have to draw straws there.

Same question I had for unlimitedz . . . Will 20GB accommodate not only the Ubuntu OS but any mainstream apps (wordprocessing, spreadsheet, database, etc.) that I will want to install for Ubuntu?

What's this thing about "***separate /home to keep your settings, tweaks, config files, etc.***"?  Is that like the FireFox profile?  Can I find out more about that at that psychocats link?

I'm assuming Ubuntu would want it's own swap file, not the one for Windows. Or could I point Ubuntu to the swap file on the Windows partition (assuming I keep Windows rather than remove it and just run it on a VM within Ubuntu)?

Am kind of rusty on partition issues, so may have more questions there later on down the line.

Thanks very much for the tips.

---

### Post by BobJam on 2009-07-14
Here's something someone just pointed out in another forum that favors running the Windows OS within a vurtual box within Ubuntu:  My on line banking sessions would be more secure.

Very pertinent.
****

---

### Post by unlimitedz on 2009-07-14
Yes, the 20GB goes for all your apps, programs, data files, etc.

> **BobJam said:**
> 
What's this thing about "***separate /home to keep your settings, tweaks, config files, etc.***"?  Is that like the FireFox profile?  Can I find out more about that at that psychocats link?

Think of your /home directory kinda like your "C:\Documents and Settings\NAME\" directory.  This is where applications store your profile specific settings, like themes for Firefox, your Desktop background, etc..  This is also where your "My Documents" equiv. would be.  Also a side note, if you have a separate partition for your /home directory, then if you fill up that partition, your system will still be bootable.  If you have the /home in the same partition as / then if you fill it up your system will essentially break (you can still mount the drive from a live CD and move files that way).


As for the Swap question.  Linux uses a special partition, which /swap is mounted to.  you can decide how big you want this, but 1gb is usually enough.  Windows uses a pagefile located on the local harddisk, same thing really except for Linux it has its own partition.  If you decide to do a manual partition then you'll need to create this partition and label it as swap.

For your specific situation, if you're confident and ready to move to Ubuntu, i would just do a full install of Ubuntu and have a windows VM with 256mb RAM allocated for it.  If you really plan on only using it 2 times a week this should be fine, no need to mess with dual booting.  If you're going to be using it more often, or for games and whatnot then i would suggest a dual boot approach.

---

### Post by raymondh on 2009-07-14
20GBs is good. SWAP at 1.5GB reduces that to 18.5 GB less administrative.  Still OK.

> **BobJam said:**
> 

Hmmmm . . . you seem to think any alternative will meet my objectives.  Is there one that stands out above the others?


I virtualize as well as multi-boot.  My home-based MAIN computer is a mac virtualizing XP and ubuntu.  My test machine 3-boots Ubuntu, win7, debian as well as virtualizing some other linux distros (it also uses a /data).  My travel computer is a 3-boot (Ubuntu, XP, OSX).

I set it up this way as it suits my needs and preferences.... also, it gives me various options should one OS or distro give me trouble.  Not for my Mac though hence I go out of my way to protect/shield it and make sure its' data is well backed-up.

Though I believe all those above options I mentioned (in my previous post) are valid, I have chosen to not WUBI anymore.  Again, this is me.

My thoughts:

Virtualization makes computing life easier as you simply click to access another OS.  However, if your host OS crashes and you can't boot into it, neither will you be able to boot into your virtual machine. 

Dual boot ... sure you have to reboot to access the other OS. But, at least it does not rely on any host OS.

If your HD crashes ... well, that's a different story.

Lastly (with regard to security in virtualization) even if ubuntu is the host and XP is the guest ... and you use XP for your banking needs, you still need to run anti-virus/spyware in XP virtualized.

In the end, it really depends on you.  You are pro-active enough to protect your data.... and if anything crashes, a re-installation is only 40 minutes away ... unless it's a windows OS and that takes hours! :)

Good luck.

---

### Post by BobJam on 2009-07-16
> **raymondhenson said:**
> when you get to the partitioning part, make sure you choose the right partition, selecting a guided resize and use the slider to set space preferences.

Duhhhhhh . . . [http://ubuntuforums.org/showthread.php?t=1214631](http://ubuntuforums.org/showthread.php?t=1214631)

---

### Post by raymondh on 2009-07-16
> **BobJam said:**
> Duhhhhhh . . . [http://ubuntuforums.org/showthread.php?t=1214631](http://ubuntuforums.org/showthread.php?t=1214631)

Hello BJ,

I just read your new thread and am sorry you are going through all this trouble.  See link (and browse to no. 8) for a visual of guided resize.  The slider is the 3-dash/hash mark between the 2 partitions.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

P.S.  Let me go back and look at the picture in your new thread. If I see something and if you wish, I will post on that thread.

---

### Post by BobJam on 2009-07-16
Hey Raymond,

Please feel free to comment in my thread about the partitioning problems, especially if you see something in my image that raises an eyebrow.

There's a lot more to my saga . . . for example I ended up installing again from an old 8.10 CD that I had . . . the 9.04 CD crapped out on me in the middle of things . . . errors all over the place . . . hours and hours of blank screens and Grub errors (17 and 22 if that means anything).

Finally got this thing working again, but for a while there I was thinking I'd have to use the OEM XP CD to completely reinstall at least one OS.

In any case, I seem to have finally recovered, am back to a dual boot, and I think I'll catch a few winks now that this thing seems to be functioning again (though as you might expect, the partitions are really screwed up . . . will be asking a lot of questions after I get some sleep).

---

### Post by raymondh on 2009-07-16
> **BobJam said:**
> Hey Raymond,

Please feel free to comment in my thread about the partitioning problems, especially if you see something in my image that raises an eyebrow.

There's a lot more to my saga . . . for example I ended up installing again from an old 8.10 CD that I had . . . the 9.04 CD crapped out on me in the middle of things . . . errors all over the place . . . hours and hours of blank screens and Grub errors (17 and 22 if that means anything).

Finally got this thing working again, but for a while there I was thinking I'd have to use the OEM XP CD to completely reinstall at least one OS.

In any case, I seem to have finally recovered, am back to a dual boot, and I think I'll catch a few winks now that this thing seems to be functioning again (though as you might expect, the partitions are really screwed up . . . will be asking a lot of questions after I get some sleep).

sleep well and deep, BJ.  You deserve it!  Congratulations on the dual-boot set-up.

---

### Post by paynek716 on 2009-07-16
BobJam

Similar situation here - had it with Vista after a recent auto update crashed my machine and I spent FIVE HOURS reinstalling Vista, its 66 updates to the basic OS, and a handful of other apps I use.

I have a similar quandary with dual boot to use certain Windows apps like Quicken. I haven't tried this yet, but [Moneydance]("http://moneydance.com/") is at the top of my list for Quicken replacements. They have separate flavors that run on Apple, Windows, and Linux. All three flavors are compatible with the Quicken QFX file formats.

---

