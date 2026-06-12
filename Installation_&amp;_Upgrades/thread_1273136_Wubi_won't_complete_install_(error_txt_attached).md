---
title: "Wubi won't complete install (error txt attached)"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by UnderPar on 2009-09-23
Having a run of bad luck on my daughter's Compaq desktop, on which I re-installed Windows XP:

Last week, I used Wubi-installer to download and install Ubuntu.  On repeated reboots, there was no choice of OS - just the normal WinXP startup, so I uninstalled Wubi/Ubuntu.

I then decided to install a partitioned Ubuntu, from disk.  [That was another disaster]("http://ubuntuforums.org/showthread.php?t=1270349").

I removed the partition, and decided to try installing within Windows once again, only this time directly from the Ubuntu 9.04 disk.  It stops with about a minute to go, spitting out an error message that I've attached.  I had to compress it because it's 32kb, over the size limit for this forum.

Does Compaq not like Ubuntu, or does Ubuntu not like Compaq (or me!)?

Thank you for any help you can offer.

---

### Post by UnderPar on 2009-09-23
*bump*

---

### Post by rreese6 on 2009-09-23
Wow! You sure seem to be having a lot grief with this.
I would suggest that you google the answer to remove wubi completely and the files it made for Linux.
Then do a normal install from the Linux CD.
Adjust the partition so you have around 10 gigs on the right side.
the left (or new) is the windows. install that and select put the grun on the MBR. that will give you a full dual boot system.

I read where some people claim that removing the wubi.exe file was all that was needed, but then what about the files that it wrote using up space....dang..ok ok I will google to find something for you in next post.

---

### Post by rreese6 on 2009-09-23
Run the uninstaller. then:
Delete the folder and remove the registry key (using regedit and search)
HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi\

that should get rid of it. check control panel to make sure it is gone.

you can also check your boot.ini file (maybe in Windows/system or system32..too many years away from windows to remember well) and make sure the Ubuntu line is removed...I think you can do it this way to call it up and edit it...Start Button>>RUN>>type "MSCONFIG" then hit enter. that should come up and let you see your startup and your boot.ini file ..

once wubi is gone, reboot the machine with the Linux CD
and chose install. remember to check the partition size "new" means the new size for windows....

once Linux is installed reboot again and you should be able to dual boot.

here is a good link to read up about such things...be sure you are logged in here as this is a secure link.
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

here is one about wubi:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

---

### Post by wilee-nilee on 2009-09-23
> **rreese6 said:**
> Run the uninstaller. then:
Delete the folder and remove the registry key (using regedit and search)
HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi\

that should get rid of it. check control panel to make sure it is gone.

you can also check your boot.ini file (maybe in Windows/system or system32..too many years away from windows to remember well) and make sure the Ubuntu line is removed...I think you can do it this way to call it up and edit it...Start Button>>RUN>>type "MSCONFIG" then hit enter. that should come up and let you see your startup and your boot.ini file ..

once wubi is gone, reboot the machine with the Linux CD
and chose install. remember to check the partition size "new"
 means the new size for windows....

once Linux is installed reboot again and you should be able to dual boot.

Yes you are correct on the msconfig to edit the windows bootloader, I also notice (amd which seems to generally a problem) and 64 and i386 mixed in with that error file, not being a expert it is just a notice. When I had a wubi install that I removed I had the windows ubuntu still there, I just searched with wubi deleted everything and edited the bootloader and it as gone. I assume to that when you are installing gthe ubuntu OS that there is a blank space in the disc, and that you defrag windows after the repartition and then install, and that you have a disc or usb stick that is good. Some thumb drives even if formated with gparted just don't work with the linux boot setup.

---

### Post by rreese6 on 2009-09-23
good points wilee but I think you would want to defrag windows before partitioning.

---

### Post by UnderPar on 2009-09-23
> **rreese6 said:**
> Wow! You sure seem to be having a lot grief with this.
I would suggest that you google the answer to remove wubi completely and the files it made for Linux.
Then do a normal install from the Linux CD.
Adjust the partition so you have around 10 gigs on the right side.
the left (or new) is the windows. install that and select put the grun on the MBR. that will give you a full dual boot system.
 
I read where some people claim that removing the wubi.exe file was all that was needed, but then what about the files that it wrote using up space....dang..ok ok I will google to find something for you in next post.
 
 
Thank you for taking the time to reply, rreese6!
 
Yeah, this Compaq hasn't wanted to play nice with Ubuntu.  On my homemade desktop and my Acer Vista laptop, Ubuntu installed first time, no problem, using Wubi.
 
I may end up trying another partitioned install from the Ubuntu 9.04 disk, but as I said this is my 13 year old daughter's desktop, and the reason I was able to convince her to even put Ubuntu on was she liked the OS choice menu that loaded XP if she didn't do anything.  The partitioned Ubuntu makes you choose WinXP, if I'm not mistaken.

---

### Post by rreese6 on 2009-09-23
yes it does make you choose Windows in the boot menu after you do the install, but Like most things in Linux this can be configured.

once you do the install edit the menu.lst to make Windows the default boot OS. I list two methods here.
In a terminal.....be calm, be happy and begin typing (or cut and paste, if you have too :) )

```
cd /boot/grub
sudo cp menu.lst menu_backup.lst
sudo gedit menu.lst

```
look for blocks of information that has the first line as "TITLE"
count how many of those you have (don't count anything with " # " in front of it.
IE
here is what one block would look like:
```
title		Ubuntu, kernel 2.6.18-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-15-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.18-15.gz
boot

```
find the one that show windows (usually about 3)
Then find this text:
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0 
```

change the "default" from 0 to 3.
save the file and reboot. windows will be booted if no key is pressed.

that is basically the ubuntu way of doing it. I like to move my block that has the other OS (windows in this case) to a position above the other blocks.Like this:
```

title Windows XP Professional (not really)
rootnoverify (hd0,0)
makeactive
chainloader +1

title		Ubuntu, kernel 2.6.18-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.18-15-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.18-15.gz
boot
```

it isn't that big a deal and if you make a nice cup of coffee or tea, sit back relax and hum a nice tune while you do it, you will become a zen master of Linux....enjoy

---

### Post by wilee-nilee on 2009-09-23
> **rreese6 said:**
> good points wilee but I think you would want to defrag windows before partitioning.

you are so right, I keep mine defragged quite often. I have seen advice to do a post repartition as well so I generally advise it, in that at the least you get to see if windows opens again after the repartition, thanks for the comment.

---

### Post by rreese6 on 2009-09-23
> **wilee-nilee said:**
> you are so right, I keep mine defragged quite often. I have seen advice to do a post repartition as well so I generally advise it, in that at the least you get to see if windows opens again after the repartition, thanks for the comment.

A second defrag would probably be a good idea too...It has been many years since I got to watch defrag working...I miss it is a funny sort of way...made me feel like windows was "healing"..Maybe I should go see if I can find and old install disk of win98SE....have a very nice evening and thanks for helping.. (sorry for the minor hyjack here)

---

### Post by UnderPar on 2009-09-23
> **rreese6 said:**
> Run the uninstaller. then:
Delete the folder and remove the registry key (using regedit and search)
HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi\

that should get rid of it. check control panel to make sure it is gone.

you can also check your boot.ini file (maybe in Windows/system or system32..too many years away from windows to remember well) and make sure the Ubuntu line is removed...I think you can do it this way to call it up and edit it...Start Button>>RUN>>type "MSCONFIG" then hit enter. that should come up and let you see your startup and your boot.ini file ..

OK, I've done this, and Wubi was nowhere to be found.  I think every remnant was removed when I did a [CCleaner]("http://www.ccleaner.com/") cleanup of the hard drive and registry.

> once wubi is gone, reboot the machine with the Linux CD
and chose install. remember to check the partition size "new" means the new size for windows....

once Linux is installed reboot again and you should be able to dual boot.I am going to assume that you are talking about a partitioned install rather than an install within Windows.  I am fine with that, since I see that you have included instructions in another post to change the boot order.

Since the last Wubi attempt picked 17 gigs to devote to Ubuntu, I will assume this is sufficient.  The C: drive currently has 93 gigs free, so I see no problems down the road.  Is there a chance of Ubuntu eventually needing more than 17 gigs?

Thanks to all who have responded so far!

---

### Post by rreese6 on 2009-09-24
You asked if it need more than 17 gigs..not really, but then it would depend on how much you use it :)
I have a 120 gig on my laptop and only have 17 gigs left (after 4 years)
but this one I am using now only has 5.5 gigs and I use it for surfing and such).. 17 should be good to get you going..
look on the bright side. if it gets filled up, you can go get another drive and we will teach you how to dual boot using 2 hard drives :)
Sounds scary, but it is actually quite simple to do and fun too...
Grab your cup of java or tea, relax and have fun!
I am here for a while more tonight...

---

### Post by UnderPar on 2009-09-24
> **rreese6 said:**
> You asked if it need more than 17 gigs..not really, but then it would depend on how much you use it :)
I have a 120 gig on my laptop and only have 17 gigs left (after 4 years)
but this one I am using now only has 5.5 gigs and I use it for surfing and such).. 17 should be good to get you going..
look on the bright side. if it gets filled up, you can go get another drive and we will teach you how to dual boot using 2 hard drives :)
Sounds scary, but it is actually quite simple to do and fun too...
Grab your cup of java or tea, relax and have fun!
I am here for a while more tonight...
I am posting this from my other desktop.
 
I just finished the install, devoting 17 gigs, leaving 84 gigs for WinXP.  I launched Update Manager, and it is currently downloading 231 updates (154.5 megs worth).  Everything looks fine so far.  I will mess with it for a bit before going to bed.  I may have a further question tomorrow, so if you would be kind enough to check back when you get a moment, I would be very grateful.
 
Thank you, and everyone else who participated in this thread!

---

### Post by UnderPar on 2009-09-24
Oh - I do have a quick question for anyone listening:  how do you turn off the request for the password for everything you do in Ubuntu.  It drives me crazy on my machine, and I know that it will be such a turn-off for my daughter, she'll never boot Ubuntu!

---

### Post by rreese6 on 2009-09-24
I will try to be around tomorrow all day, from time to time.
About the password question. that is just to make changes.
it is dangerous to defeat it, especially when new users (and some old ones) are concerned. She really shouldn't need to use the password for anything. 
Although if you want it to log in automatically we can do that tomorrow
I am too tired to think right now...good night . see you tomorrow

---

### Post by UnderPar on 2009-09-24
A few things: on startup, I get this boot screen:
[INDENT]Ubuntu 9.04, kernel 2.6.28-15-generic
Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
Ubuntu 9.04, kernel 2.6.28-11-generic
Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+
Other operating systems:
Microsoft Windows XP Home Edition
Windows NT/2000/XP
[/INDENT]That last one is the recovery partition for XP. Does everything look right? I don't know why I have the two '11-generic' entries.
 
Also, the display is not centered, with a lot of black space on the right, and half of the 'hide all windows' button missing on the left. I took a screengrab of the 'Display' properties, but it doesn't include the black space.
 
 
[IMG]http://i35.tinypic.com/2wox9cl.png[/IMG]
 
 
Since the display is centered when using XP, I am assuming that if I use the controls on the monitor itself to fix the Ubuntu display, then the XP display will be off. Can this be corrected within Ubuntu? I can't seem to be able to 'drag' anything, as the Display properties instruct.
 
 
Edit to add:  I also cannot change the display to anything larger than 800x600, which is too small, forcing me to scroll left and right.
 
.

---

### Post by rreese6 on 2009-09-24
I thought your original quest was about installation...LOL
Glad to see you have it installed. the different Ubuntu's is the new (updated) kernel and old kernel(installed from CD). good to keep at least one old kernel in case you have trouble with an upgrade you can boot in the old kernel to fix the issues.
Ok about the Screen. that means we need to know your video configuration.
post here the contents of /etc/11/xorg.conf
also do a lspci |grep vga  or lspci |grep VGA and post here
what we want to do is fix the the video first.

---

### Post by UnderPar on 2009-09-24
> **rreese6 said:**
> I thought your original quest was about installation...LOL
Glad to see you have it installed. the different Ubuntu's is the new (updated) kernel and old kernel(installed from CD). good to keep at least one old kernel in case you have trouble with an upgrade you can boot in the old kernel to fix the issues.
Ok about the Screen. that means we need to know your video configuration.
post here the contents of /etc/11/xorg.conf
also do a lspci |grep vga or lspci |grep VGA and post here
what we want to do is fix the the video first.
 
I'm sorry - should I abandon this thread now that I'm up and running, and start new ones for further questions?  I'm not really sure of the protocols on ubuntuforums.org and I don't want to be a pest.
 
I think I just fixed the video resolution.  I went to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS and downloaded and installed the (recommended) NVidia driver.  On reboot, all looks well!

---

### Post by UnderPar on 2009-09-24
I think the only thing left for me to do is see if her NetGear wireless G USB dongle is recognized, since there isn't hard-wire in her bedroom.  I've had her machine in my office while doing all the installs.
 
One further question:  When downloading add-ons like Flash Players, etc. they always give you options like .YUM, .deb, etc. but never explain which is for what, so I never know which is the proper format.

---

### Post by rreese6 on 2009-09-24
+1 Underpar

Great!
I was going in that direction, but you beat me there...good job.

Ok so let continue the "installation" by fixing you boot up.
if you like I will edit your Menu.lst file for you and you can compare them to see what i did. or you can try it yourself..but be careful.

if you want me to do it, go to /boot/grub amd post menu.lst here.
And you are not a pest, I was just poking some fun at you.

edit: Additional info.. you can install flashplugin-nonfree from your package manager. easiest way to do it.

---

### Post by UnderPar on 2009-09-24
> **rreese6 said:**
> +1 Underpar
 
Great!
I was going in that direction, but you beat me there...good job.
 
Ok so let continue the "installation" by fixing you boot up.
if you like I will edit your Menu.lst file for you and you can compare them to see what i did. or you can try it yourself..but be careful.
 
if you want me to do it, go to /boot/grub amd post menu.lst here.
And you are not a pest, I was just poking some fun at you.
 
edit: Additional info.. you can install flashplugin-nonfree from your package manager. easiest way to do it.
 
 
I'm glad I'm not being a pest!
 
I am embarrassed to say that I do not know how to go to /boot/grub or even to find the terminal.

ETA:  I was talking about a drop-down choice like on here:

[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

They give you 4 choices, with no explanation.

---

### Post by rreese6 on 2009-09-24
I will explain the 4 choices :
those are different Packages for different "flavors" (distributions) of Linux.
Yum is related to redhat Linux
RPM is redhat, Suse, mandriva,Centos...etc
DEB is debian, Ubuntu, Kubuntu, XUbuntu, etc
tar.gz is normally the source file that can be installed by compiling.

---

### Post by rreese6 on 2009-09-24
(this post intentionally left blank)

---

### Post by UnderPar on 2009-09-24
> **rreese6 said:**
> Lets connect using live chat. AOL AIM (windows) or Pidgin(Linux)
My user name is reeserh2
it will be faster.and I will be able to help you better.

if you don't have an account you can make a free on on AOL.com
then just run Pidgin in Linux or you can use AIM in Windows.
I will explain the 4 choices :
those are different Packages for different "flavors" (distributions) of Linux.
Yum is related to redhat Linux
RPM is redhat, Suse, mandriva,Centos...etc
DEB is debian, Ubuntu, Kubuntu, XUbuntu, etc
tar.gz is normally the source file that can be installed by compiling.
I just signed up on AOL AIM, using the username *private*

---

### Post by UnderPar on 2009-09-24
Thank you to everyone for their help!

---

