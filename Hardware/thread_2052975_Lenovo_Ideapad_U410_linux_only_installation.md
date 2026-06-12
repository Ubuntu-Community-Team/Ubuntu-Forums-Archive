---
title: "Lenovo Ideapad U410 linux only installation"
date: 2012-09-04
forum: Hardware
---

### Post by fetchinson on 2012-09-04
Hi folks, I'm about to buy a lenovo u410 and only need to have linux on it, ready to delete windows completely. I've gone through a couple of threads relating to installation problems and drives not being recognized on this model:

[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?p=9274738#post9274738](http://ubuntuforums.org/showthread.php?p=9274738#post9274738)
[http://ubuntuforums.org/showthread.php?t=2023374](http://ubuntuforums.org/showthread.php?t=2023374)

and it seems to me that problems are only to be expected if one wants to have a dual boot system with both linux and windows. Is this correct? Seems to me that if I deactivate the raid setup in the BIOS and do a completely new install of linux I should be fine. 

I was just not 100% sure that this is the case, can somebody confirm?

Also, those of you who run ubuntu on the u410: wifi, fn keys, volume controls, webcam, etc, all these things work?

---

### Post by ulot on 2012-09-04
I haven't tried Ubuntu yet, but I have successfully installed Fedora 17 with Win7.  I broke the raid array, killed the raid meta data, and labeled the drives gpt.  After that it installed fine and saw all the drives.  Didn't bother trying to use the IRST or RAID, but there are some docs about Intel's Linux support for it.  Bumblebee appears to work with the graphics cards as well.  Had to load the non-free firmware for the Wireless-N 2200, but then it was detected right away.

The only thing that has been an issue is with the Mobile Express SATA RAID controller.  It wants to put the non-SSD drive in UDMA/100.  Just started working on that tonight.  Plan to write a blog post of all the steps taken once I'm done.

All said it isn't the easiest laptop install, but for a new hybrid ultrabook it has been much smoother then I expected.  My Dell XPS 1345 had a rocky start, but things got better over time as the kernel and software updates fixed some of the issues.

---

### Post by phyjcowl on 2012-09-05
A few days ago I got an IdeaPad U410. I made the mistake of installing Kubuntu without doing enough reading on the proper way. Although Kubuntu worked fine, it didn't install properly for dual booting. In your case, I guess that doesn't matter. 

Most everything seems to work fine, including the function keys. The touchpad is flaky though. The right button doesn't function properly and the left button causes it to move as well. There was a way to fix this that I came across in these forums but I haven't tried it yet and don't recall the link.

The main problem I have, is that after installing Ubuntu, the system refuses to let me F2 to get into its BIOS settings. It just totally ignores that. It also doesn't allow me to boot back into the OEM recovery partitions so I cannot figure out how to resolve the F2 problem. 

I've done a lot of searching and I can't find any mention of the F2/BIOS settings problem anywhere. I'm thinking a may return it now. Because while I'd be fine to not have Windows on it, I see it as a potentially big problem not to be able to access the BIOS settings.

---

### Post by fetchinson on 2012-09-05
Thanks a lot for all the details!

> **ulot said:**
> I broke the raid array, killed the raid meta data, and labeled the drives gpt.

Breaking the raid array means you disable it in the BIOS?

> Had to load the non-free firmware for the Wireless-N 2200, but then it was detected right away.

How did you do this exactly? Was there a fedora rpm for it?

> The only thing that has been an issue is with the Mobile Express SATA RAID controller.  It wants to put the non-SSD drive in UDMA/100.

And why is that a problem?

---

### Post by ulot on 2012-09-05
> **phyjcowl said:**
> The main problem I have, is that after installing Ubuntu, the system refuses to let me F2 to get into its BIOS settings. It just totally ignores that. It also doesn't allow me to boot back into the OEM recovery partitions so I cannot figure out how to resolve the F2 problem. 


Hold the Fn key that is between ctrl and alt key while pressing the function keys.  Unlike most laptops, the function keys are meta keys while the feature keys (volume, brightness, and such) are hardware keys.  Normally it is the other way around and you hold down Fn for the feature keys.

---

### Post by ulot on 2012-09-05
> **fetchinson said:**
> 
Breaking the raid array means you disable it in the BIOS?


Set the BIOS to AHCI, delete the raid partitions, and used dmraid to remove the meta data.  Used the install console to do those last two steps before continuing the install.  The dmraid command is:
```

dmraid -r -E /dev/sda
dmraid -r -E /dev/sdb
```

If you plan to run UEFI, you'll need to use gpart to label the disks as 'gpt'.

[QUOTE=fetchinson]
How did you do this exactly? Was there a fedora rpm for it?
[/QUOTE]

Yes.  Redhat does not allow non-free rpms in the distro repos, but you can find it in the rpmfusion repo.  I would imagine Ubuntu has the firmware as well.  Don't know what repo to look in though.

[QUOTE=fetchinson]
And why is that a problem?[/QUOTE]

Normally UDMA/100 doesn't do anything to SATA, but for some reason it is treating it as an IDE drive.  I think it might have to do with the driver for the non-boot drive not being loaded at boot.  Didn't get much chance to look at it.  I found next to nothing about the Intel Mobile Express Chipset SATA AHCI controller that is in the laptop.  Really not even sure if it is supported or not.

Sorry for the lack of Ubuntu specific directions.  Don't normally use it.  I found your post looking for more information on setting up the U410.

---

### Post by phyjcowl on 2012-09-07
Thanks for the tip, unfortunately that wasn't the problem. I never figured out exactly why it stopped letting me access the BIOS, I just returned the system to the store and will get something else.

---

### Post by lakerssuperman on 2012-10-27
Just curious, anyone install 12.10 on this laptop?  If so, how is the experience?  Has it improved over 12.10?

---

### Post by frizi on 2012-11-13
I would be also interested about this answer to know with which difficulties I have to count. 

Except of this I am thinking if the GRUB can be installed while leaving the raid partitions in the initial state like for ex.:

SSD: 1.Windows 32Gb
HDD: 1. Windows Raid copy 32Gb
     2. Linux 64Gb
     3. Storage - rest 400GB
Since the U410 has min 4GB Ram I would not install any swap partition.

Could such partitioning and installing be done. The idea behind it is to leave the Raid and Windows and just add the Linux system to it. If there would be better to have the Storage before the Linux partitions please let me know.

Thank you in advance.

---

### Post by snowz on 2012-11-18
I'm also planing to buy the U410 in short future. I've also asked some questions on askubuntu.com about this ultrabook.

_**Battery**_
The thing that I found out till now is that the battery life on Ubuntu isn't so long than on Windows, because the linux kernel does not support it or something like that.

---

### Post by IQRules on 2013-02-02
So this U410, shipped with Raid on?
And how is the original Win 7 and recovery paritions reside?

Can you post the info from fdisk?

---

### Post by avpatel on 2013-03-08
Hi...I bought Lenovo U410 26 days ago and just within week I disappointed with windows 8..so I decided to install Ubuntu 12.10 along side it.....Actually I want to uninstall windows completely but I am never used linux system and I am afraid what if some program that I am using since last several years wont run on linux.

So you wont believe but I tried for three week.....freaking UEFI wont let me(changed to Legacy mode)........Then finaly I succeeded and I am running now Ubuntu 12.10 along with the Windows 8 on U410.

Its been a week and I must say its much much better than windows.....like the touch pad and scrolling works much better than W8, faster than W8..I mean in opening files and booting.....SO far I haven't experienced any difficulties.....

However.......when I looked 'into the about this computer'>overview.........there its mentions my laptop details.....but in Graphics it says unknown........so may be it doesn't installed the driver for the graphics or I dont know....but i am sure there must be something for that..If someone can help me I will highly appreciate.

Another thing is: I installed wine and I am unable to use it.....I want the "wunderlist and connectify-mee" program on the ubuntu..
Pls help me.....or recommend  me similar program for 'task to do' and 'hotspot' functionality on Linux.....

And now I am considering that I will keep only one operating system..............And that would be definately Ubuntu....

Thanks

---

### Post by avpatel on 2013-03-08
Hi...I bought Lenovo U410 26 days ago and just within week I disappointed with windows 8..so I decided to install Ubuntu 12.10 along side it.....Actually I want to uninstall windows completely but I am never used linux system and I am afraid what if some program that I am using since last several years wont run on linux.

So you wont believe but I tried for three week.....freaking UEFI wont let me(changed to Legacy mode)........Then finaly I succeeded and I am running now Ubuntu 12.10 along with the Windows 8 on U410.

Its been a week and I must say its much much better than windows.....like the touch pad and scrolling works much better than W8, faster than W8..I mean in opening files and booting.....SO far I haven't experienced any difficulties.....

However.......when I looked into the about this computer>overview.........there its mentions my laptop details.....but in Graphics it says unknow........so may doesn't installed the driver for the graphics or I dont know....but i am sure there must be something for that..If someone can help me I will highly appreciate.

Another thing is: I installed wine and I am unable to use it.....I want the "wunderlist and connectify-mee" program on the ubuntu..
Pls help me.....or recommend  me similar program for to do list and hot spot functinality on Linux.....

And now I am considering the I will keep only one operating system..............And that would be definately Ubuntu....

Thanks

---

### Post by fsetiaw on 2013-08-18
Since there are some troublesome post about installing ubuntu on lenovo u410, so I just wanna add success installation story based my experience, so nubee like me have courage todo so; (this is ubuntu only, no dual booting)
good news, I manage install ubuntu 13.04 with only minor glitch, so here the step:
1. go to bios (fn-f2) - change raid to ahcpi (ide controller part - otherwise ubuntu installer wonn't recognoize any hd);
2. dont forget set boot priority - adjust to whatever media u use as ubuntu installer (udb drive,dvd,etc);
3. first try : (glitch #1)
    I do manual partition; 
    1. /boot 500mb
    2. /swap 4096 mb - (put same amount as ur hardware ram u have, mine 4gb)
    3. /root 50 gb
    4. /home (the res GB);
    installation halt, I restart and try again, it works - instalation complete, alas after reboot fail to recognize any available OS (forget what the error shows);
4. so I did step 3 again except, on creating /boot partition i use efi boot partition (option avail just like when u try make /swap file) and make it partition size < 256mb (as I'd tried with 500mb and failed (glitch #2)). the rest partition the same. if it halt, just keep trying,...the installation complete, and reboot and it just works.
it seems everything works, whortcut, wifi, suspend/ hybernate / resume, wifi, bt. my model is the ivy bridge one i5 3317u.

---

