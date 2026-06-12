---
title: "BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by baal666 on 2009-01-05
Hi,

I am new to Ubuntu.  Downloaded the latest version to put on my new hard drive on my Dell Latitude D600 laptop.  

Here is the message I get when trying to install:



BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


I don't understand what is the problem.  I checked on Google but found no solution so far that would work for me.  If anyone can help me, that would be great. 

Thanks

---

### Post by baal666 on 2009-01-05
Anyone?

I read a lot of people were having this problem... but were not finding how to arrange it.

---

### Post by baal666 on 2009-01-05
For the record, I got a blue screen while trying to install Windows as well...  Said something about been shutted down to avoid some kind of risk...

---

### Post by h2o4444 on 2009-01-16
I've been using Ubuntu 8.10 on a HP Compaq tc4200 tablet laptop for about 2 weeks and recently I've been experiencing the same thing when I boot into Ubuntu from the boot loader (I dual boot Windows XP Pro Tablet Edition and Ubuntu 8.10). I see something that begins with "mount: cannot setup loop device:..." then something about Busybox v1.10.2, then (initramfs). I have this problem about 2/3 of the time when I start up my computer.

When this problem occurs, I restart the computer by pressing down the power button for 3-5 seconds and then choose Ubuntu again. It will most likely start up correctly. I would say the success rate is 3/4. I only have one time when I restarted twice for the computer to boot into Ubuntu.

I tried to search for answers online but can't find any. I'm wondering if it's something I did in Ubuntu that caused this problem. The major things I did were: [http://ubuntuforums.org/showthread.php?p=6544578#post6544578]("http://ubuntuforums.org/showthread.php?p=6544578#post6544578"), [http://ubuntuforums.org/showthread.php?p=6542275#post6542275]("http://ubuntuforums.org/showthread.php?p=6542275#post6542275"), and installed KDE, VLC, Amarok, Songbird, Skype, Gshutdown, Wine, Picasa, and Amazon MP3 Downloader (this one was installed after I noticed the start up problem).

I have also successfully boot into Windows since I've been using Ubuntu so I don't think there is anything wrong with Windows.

---

### Post by gehentogo on 2009-01-19
I get the exact same message.  I get it while trying to load the live CD with both Ubuntu and Kubuntu and can not get it to boot.  Anyone know what this is?

---

### Post by Yixi_CZ on 2009-01-24
I've got same laptop and same problem... But Hardy Heron works fine on it... Now im running Windows 7 Beta and i wish to have stable system under it on my second partition but it stuck after trying to install or run Live.

---

### Post by jamiestr on 2009-05-26
[COLOR=black][FONT=Verdana]Folks I had this exact problem (asus eeepc 901) and one, or both, of the following two options solved it. I was trying to install Ubuntu Netbook Remix without much luck, I got this exact same message and nothing more. I actually managed to do both of the below between an unsuccessful and a successful install so I'm not sure which one fixed it, although I suspect number two. Anyway:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]1. Reset BIOS settings[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Turn computer on and hit F2 to enter BIOS. Go to the 'save and exit' settings page (far right of BIOS menu at top of screen). The bottom option on this page should allow the BIOS settings to be reset to default. Select this option confirm, save and exit.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]There does appear to be a BIOS default reset switch under the eeepc as well >.< but I didn’t need to go anywhere need that.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]2. Bootable USB Drive[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I produced the bootable USB drive on a windows machine.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I had originally downloaded the .img file from ubuntu.com for the netbook remix and converted it using the UNetbootin to produce a bootable USB drive. I think it was the UNetbootin program that caused this problem, although I might be wrong, so I downloaded a different prog from:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][http://webupd8.blogspot.com/2009/04/4-ways-to-create-bootable-live-usb.html](http://webupd8.blogspot.com/2009/04/4-ways-to-create-bootable-live-usb.html)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Following the link in Option 2 and downloading the top app.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Once I'd wiped the old UNetbootin stuff on the USB stick and made a new one using the win32 image writer. Turn the computer on, press escape, select USB boot and take it from there.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]As above once I'd done all of the above the upload worked like a dream.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I also got some great advice from:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][http://mesanna.com/2009/05/10/how-to-install-ubuntu-netbook-remix-on-an-eee-pc/](http://mesanna.com/2009/05/10/how-to-install-ubuntu-netbook-remix-on-an-eee-pc/)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]On what to expect and particularly how to partition the hard drives (I am no expert), clear and concise advice, once this problem had been solved.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]What I did find out is that if it can go wrong it will go wrong but then I guess that’s why these things are so helpful.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Anyway hope that helps, Jamie[/FONT][/COLOR]

---

