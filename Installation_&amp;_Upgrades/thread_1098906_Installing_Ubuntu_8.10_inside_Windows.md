---
title: "Installing Ubuntu 8.10 inside Windows"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by AnguishedEnd on 2009-03-17
Ok, so I received the Ubuntu 8.10 Desktop Edition in the mail a few days ago and I installed it inside Windows Vista. I followed this guide [WubiGuide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Ubuntu?"), although it was relatively straight forward. The installation was fine and everything but the problem is that once I get to the Windows Boot Manager like in the picture in the guide it only displays Windows Vista, Ubuntu is no where to be seen.

Further below in the guide it says this [Cannot Boot Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu"), so I tried everything it said there but the two files c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot are where their supposed to be and everything.

Also after googleing this problem it seems this occurs more often in Windows 7 Beta but the solutions posted are a tad bit confusing...but my problem is the exact same but instead of Windows 7 Beta, I'm running Windows Vista. Heres the link [Wubi Bug]("https://bugs.launchpad.net/wubi/+bug/318135")

FYI: I'm running on a Dell Studio 15 Laptop with Windows Vista 32bit.

Any help would be appreciated. Thanks!

---

### Post by markosjal on 2009-03-17
Maybe Microsoft is finding new ways to hinder the competition!

---

### Post by AnguishedEnd on 2009-03-17
Well I just did the other option of partitioning the hard drive and everything worked fine...I can boot into Ubuntu without any problems BUT I would really prefer the method of installing it inside Windows. Any ideas why I can't see it in the Windows Boot Manager?

---

### Post by AnguishedEnd on 2009-03-18
Ok after reading some more threads some were suggesting to use EasyBCD 1.7.2 so I downloaded that and it has the option to add things to the boot manager. I selected Linux>>Wubi then clicked add entry...still not working. Now when I click Ubuntu in the Boot Manager it goes to a black screen with "grub >"...WHY MUST IT BE SO DIFFICULT!!! lol...

EDIT- Just read another post about adding C:\ubuntu\winboot\menu.lst to C:\NST and it WORKED!! I managed to finish the installation process and everything. Then it rebooted automatically and brought me back to the Windows Boot Manager. So I clicked on Ubuntu again but then it loads GRUB and I cant select ANYTHING =( It gives me Error 19: Cannot mount selected partition...WTF!

---

### Post by Mark Phelps on 2009-03-19
OK ... so first, you installed Ubuntu inside Windows but Ubuntu wouldn't boot.  So then, you repartitioned your drive and installed Ubuntu (again?), this time, in it's own partition.  Right so far?

And then, you got a disk for Ubuntu, and installed it inside Windows (again?).

So, when you did the dual-boot Ubuntu install, did you remove Ubuntu from inside Windows first?

When you did the second (?) Wubi install, did you remove the Ubuntu from the separate partition?

Without more details, it looks like you have two copies of Ubuntu installed and you're having trouble getting GRUB to point to the correct one.

---

### Post by AnguishedEnd on 2009-03-20
> **Mark Phelps said:**
> OK ... so first, you installed Ubuntu inside Windows but Ubuntu wouldn't boot.  So then, you repartitioned your drive and installed Ubuntu (again?), this time, in it's own partition.  Right so far?

And then, you got a disk for Ubuntu, and installed it inside Windows (again?).

So, when you did the dual-boot Ubuntu install, did you remove Ubuntu from inside Windows first?

When you did the second (?) Wubi install, did you remove the Ubuntu from the separate partition?

Without more details, it looks like you have two copies of Ubuntu installed and you're having trouble getting GRUB to point to the correct one.

Ok here's the steps that I took.


BTW I just did the install inside Windows option on my desktop at home and the Ubuntu option appeared first try!!!!! BUT when I click on it it goes to a black screen and I cannot use the mouse or keyboard. I had to manually shut down my computer!!! 

I received the Ubuntu 8.10 Desktop Edition CD in the mail. I did not download anything (Wubi)

First, I selected the Install inside Windows option (second choice in the menu). The first part of installation was fine but once it rebooted after finishing there was no option to select Ubuntu in the Windows Boot Manager.

Second, after several tries of restarting to see if Ubuntu would appear in the Boot Manager I uninstalled Ubuntu by going to Control Panel>>Uninstall a Program, just like any other program. Once it finished uninstalling I selected the first option on the disc which was to do a full install. I went through the steps and I moved that bar during the partitioning step to make space for Ubuntu. Everything worked fine. After the reboot I was able to select Ubuntu using the GRUB Manager. 

Third, after trying out Ubuntu I decided I would rather use it through the inside Windows option. So I followed what this guy said in another forum 

"If you have your windows setup cd, load it, restart the PC, boot off the CD and start the Recovery console. Here you can use the fixmbr command to commandeer your MBR.

Fixmbr ([http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)) (microsoft.com)"

Then I deleted the partition using the Disk Management program inside Windows Vista. Now it was back to normal I had a two disks (E:) and (C:) like before.

Fourth, I tried the install inside Windows option for I think the sixth time and still Ubuntu doesn't appear inside the Windows Boot Manager. Then I discovered that using EasyBCD and putting the menu.lst file inside the NST folder as I said in a post above the Ubuntu option appeared!!! so I clicked on it and it does the second part of the installation then auto restarted my laptop. I click on Ubuntu again and then it to a black screen with "grub >" and I can type commands but I just turned off my laptop hoping not to screw up further lol.

Anyways, I hope that helps in some way as to finding out what happened.:D

---

### Post by AnguishedEnd on 2009-03-20
> **Mark Phelps said:**
> OK ... so first, you installed Ubuntu inside Windows but Ubuntu wouldn't boot.  So then, you repartitioned your drive and installed Ubuntu (again?), this time, in it's own partition.  Right so far?

And then, you got a disk for Ubuntu, and installed it inside Windows (again?).

So, when you did the dual-boot Ubuntu install, did you remove Ubuntu from inside Windows first?

When you did the second (?) Wubi install, did you remove the Ubuntu from the separate partition?

Without more details, it looks like you have two copies of Ubuntu installed and you're having trouble getting GRUB to point to the correct one.

Ok here's the steps that I took.

I received the Ubuntu 8.10 Desktop Edition CD in the mail. I did not download anything (Wubi)

First, I selected the Install inside Windows option (second choice in the menu). The first part of installation was fine but once it rebooted after finishing there was no option to select Ubuntu in the Windows Boot Manager.

Second, after several tries of restarting to see if Ubuntu would appear in the Boot Manager I uninstalled Ubuntu by going to Control Panel>>Uninstall a Program, just like any other program. Once it finished uninstalling I selected the first option on the disc which was to do a full install. I went through the steps and I moved that bar during the partitioning step to make space for Ubuntu. Everything worked fine. After the reboot I was able to select Ubuntu using the GRUB Manager. 

Third, after trying out Ubuntu I decided I would rather use it through the inside Windows option. So I followed what this guy said in another forum 

"If you have your windows setup cd, load it, restart the PC, boot off the CD and start the Recovery console. Here you can use the fixmbr command to commandeer your MBR.

Fixmbr ([http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)) (microsoft.com)"

Then I deleted the partition using the Disk Management program inside Windows Vista. Now it was back to normal I had a two disks (E:) and (C:) like before.

Fourth, I tried the install inside Windows option for I think the sixth time and still Ubuntu doesn't appear inside the Windows Boot Manager. Then I discovered that using EasyBCD and putting the menu.lst file inside the NST folder as I said in a post above the Ubuntu option appeared!!! so I clicked on it and it does the second part of the installation then auto restarted my laptop. I click on Ubuntu again and then it to a black screen with "grub >" and I can type commands but I just turned off my laptop hoping not to screw up further lol.

Anyways, I hope that helps in some way as to finding out what happened.:D

Edit: I also installed Ubuntu using the inside Windows option on my desktop at home to see if it would work. On the first try Ubuntu appeared inside the Windows Boot Manager!!! BUT when I select it it goes to a black screen and my mouse and keyboard dont work...I was forced to shut down manually...:(

---

### Post by chuottui86 on 2009-06-15
I have just upgrade my os from Windows Vista to Windows 7.
When i using Windows Vista i installed Ubuntu 8.10 inside windows normally. It work!
But when i upgrade to new os (format & install new), i installed Ubuntu inside windows. After that i reboot pc but i don't see choice of os to boot.
It boot Windows 7!:(

---

### Post by Mark Phelps on 2009-06-15
> **chuottui86 said:**
> I have just upgrade my os from Windows Vista to Windows 7.
Don't want to ask why you would replace a working OS with what is essentially still a "beta".
> 
When i using Windows Vista i installed Ubuntu 8.10 inside windows normally. It work! But when i upgrade to new os (format & install new), i installed Ubuntu inside windows. After that i reboot pc but i don't see choice of os to boot. It boot Windows 7!:(

That's because the people who wrote Wubi did it to work with Vista, not with an MS Windows version that has still not been released.

If you search the forum for similar problems, you'll find post after post experiencing the same difficulty.

If you don't have the latest Wubi, you could try downloading and using that; otherwise, you'll have to wait until a Windows-7-compatible version of Wubi is released.

---

