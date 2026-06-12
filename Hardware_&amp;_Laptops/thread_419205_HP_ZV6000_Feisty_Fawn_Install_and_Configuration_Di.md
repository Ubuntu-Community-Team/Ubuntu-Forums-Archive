---
title: "HP ZV6000 Feisty Fawn Install and Configuration Diary"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by OneSeventeen on 2007-04-22
I am starting this thread to document from start to finish every single step I take (even if I take the wrong steps) so others can get Ubuntu 7.04 working on their zv6000, and it will also help me with my troubleshooting.

All of my posts with official steps I've taken will simply begin with a big bold title of what step I've taken, followed by any details and experiences because of that step.

I'll be lame and start at the VERY beginning.

[size=4]**Step 1: Download Ubuntu 7.04**[/size]
I first downloaded Azureus for Windows onto my desktop machine, and started downloading the bittorrent of Ubuntu Feisty Fawn 7.04 - desktop for i386 (even though this is an AMD 64... it is hard enough getting 32 bit stuff working on laptops much less 64)

I downloaded the bittorrent by:[list=1][*]Going to [ubuntu.com](http://www.ubuntu.com)
[*]Clicking on [download](http://www.ubuntu.com/getubuntu/download) on the top right of the page
[*]Clicking on [complete list of download locations](http://www.ubuntu.com/getubuntu/downloadmirrors) at the very bottom of the page
[*]Scrolling down until I got to the bittorent details, and clicked on [6.10 Release Page](http://releases.ubuntu.com/6.10/)
[*]Changed the end of the URL from 6.10 to 7.04 so I could go to the non-referenced [7.04 Release Page](http://releases.ubuntu.com/7.04)
[*]Scrolled down and clicked on [ubuntu-7.04-desktop-i386.iso.torrent ](http://releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso.torrent)
[*]Told Firefox to open with Azureus, and it is now downloading at about 700kB/s from 7 peers.[/list]
I know that's lame to document that much, but I want to be *that* detailed in this.  I'll write a summary when I'm done and link to it in this post.

I strongly feel that "For Advanced Users: Torrent Downloads for 7.04" (or something similar) would be **awesome** to see on the download page, to make this a 2 step process... or at least add the 7.04 release page to the complete list of download locations page.  (For now I'll just settle with the fact that you've thrown together an easy-to-use distribution that runs smoothly on every desktop I've tried it on so far... but just know you're getting off easy!)

And yes, I'm being sarcastic, the developers are overworked and underpaid, just like the corporate world, but at least the corporate guys get health insurance, so I'm definitely appreciative, just picky like every other end user that thinks everyone should cater to their every desire. :)

More to come...

---

### Post by OneSeventeen on 2007-04-22
[size=4]**Step 2: Boot and Install**[/size][list=1][*]Burn CD using ISO Recorder v 2 for Windows and half the speed the CD and Drive can actually do... just for reliability's sake.
[*]Put the CD in the laptop and power it on.
[*]Set the VGA mode to the highest setting just so the monitor will work (1024x768)  [size=1]*I don't think this step was necessary.[/size]
[*]Choose the first option, to start or install Ubuntu
[*]Wait as it boots up and immediately switches to 1280x800 and fills the screen very nicely :)
[*]plug in the network to my router and watch as it obtains an IP
[*]Double-click the Install icon
[*]Keep it on "English" and click "Forward"
[*]Choose my timezone and click "Forward"
[*]Choose my keyboard layout and click "Forward"
[*]Manually edit my partition table to put a 1024MB swap and 30GB ex3 partition in the free space in the middle of my hard drive and click "Forward" when I'm done with that.
[*]Choose to recover Firefox settings and "My Documents" to my new accounts for each user from the old system (one for myself and one for my wife)
[*]Click "Forward" and review the settings, clicking on whatever button is on that screen so I can tell it I want to participate in some ranking system for the packages.
[*]click "finish"
[*]watch as it installs
[*]click "restart now" when it asks me after it finishes installing
[*]take out the CD after it pops the tray out and hit "Enter"
[*]Wait
[*]Hit "Enter" again
[*]Wait
[*]Hit the power-button
[*]Wait
[*]Hold down the power-button and do a hard shut-down (same thing I did when installing it on a desktop a few days ago)
[*]hit the power-button again, and wait as it boots up
[*]Leave it on the default boot setting in GRUB
[*]log in as the default user.
[*]Notice that it only grabbed the first folder from the "my documents" folder and not so much as a single preference or bookmark from Firefox... oh well, can't win 'em all.
[*]Also notice that the sound card works perfectly and the video card is displaying at full resolution.
[*]Remember I should be documenting this and go back and make the post, hoping I remembered everything I did.[/list]
Because of the last step I may have put a few of the steps out of order, but you get the idea.

Just a basic vanilla install, and everything but my wifi card works wonderfully so far.  I'll try and get the wifi working tomorrow after much research.  (knowing that in Windows I may have updated the firmware on the wifi card, so I need to find out exactly which drivers to use.  Any pointers on this would be appreciated.)

---

### Post by OneSeventeen on 2007-04-22
[size=4]**Step 3: Install Extra Applications**[/size]
I simply used the Add Programs tool to install the first set of apps I could think of.
In no particular order:[list][*]GnomeSword 2
[*]Lyricue
[*]Font Forge
[*]glade python interface developer
[*]Audacity
[*]Those Gnome advanced config GUI's
[*]Inkscape
[*]Blender
[*]Project Manager
[*]And I'm sure tons more I am forgetting[/list]

I don't think I added any extra system tools other than what is listed, primarily just some bible study software, development software, and things of that nature.  I also added a few education games for gnome to see if it would be worth installing this on a PC for my wife's classroom.

Only a few apps (like Audacity) were not Ubuntu supported.  I try to stay away from anything slightly experimental as I will hopefully be using Ubuntu more and more over the next month as I try to migrate our home fileserver to linux.
**Edit:** Also installed the vista-grey theme, very clean but a little oddly contrasting in places.  Overall not too bad.

---

### Post by OneSeventeen on 2007-04-23
[size=3]Research: Wireless Card[/size]
I typed in lspci -v | less in the command line and found out I have a **Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)**

Subsytem: HP Unknown device 12f8.
Flags: bus master, fast devsel, latency 64, IRQ 21
Memory at c8204000 (32-bit, non-prefetchable [size=8K].

On the [Hardware Support Components/Wireless Network Cards/Broadcom Wiki page](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) someone claims ndiswrapper did not work with rev 03, and fwcutter is the way to go.

I remember using fwcutter on Ubuntu 6.10, but I had to run dhclient and a couple of other commands for about 30 minutes (repeatedly) to either get wireless to work, or just to give up and reboot into Windows.

I'll keep researching to make sure I get the proper drivers before I try anything.  (I may even image the partition first as well, just to be sure.)

---

### Post by scotty64 on 2007-04-23
Hi 117!

I am having a ZV6000 as well and experiencing a strange thing with the CD drive under Dapper:
DVDs (both Video and Data) and Audio CDs are automatically mounted and/or played without any problems. But when I insert a DATA CD into the drive it starts spinning up and down and I get the following IRQ hickups:
[17182619.364000] hdc: irq timeout: status=0xd0 { Busy }
[17182619.364000] ide: failed opcode was: unknown
[17182619.508000] hdc: ATAPI reset complete
When I disable HAL - automount by removing the group "cdrom" from the haldaemon user, I can mount the drive manually without these problems - but I have to wait with the mounting until the drive has come to a complete halt.
I know this is a bit OT here, but have you experienced any probs with your CD/DVD drive ?

---

### Post by OneSeventeen on 2007-04-23
[size=4]**Step 4: Get Wireless Working**[/size]
I found [DarkNoob's thread on how to install Broadcom 43xx based wireless cards](http://ubuntuforums.org/showthread.php?t=405990) using a simple script that just installs the firmware that was pulled from a windows driver using fwcutter.  (This way I didn't have to use fwcutter because he already did it for me.)

I downloaded the script, extracted it to a folder, then in a command line ran the shell script to copy the drivers over.

It works perfectly on unsecured networks, and not at all on WPA protected networks.  :(

I may look for a linux native-supported brand of wifi cards for my laptop in the future, but as long as it can deal with the WEP I have going on at home, I'll be happy.

I download at roughly 2.3 Mb/s, which is the same as on my wired connections here at work.  (We are a little bit slower because we have a corporate fiber line that keeps us consistent, which is apparently crazy expensive but well worth it in the long run.)

I will post more as I go along.  (3d window effects do not work yet, but that pales in comparison to being able to connect to wifi networks!)

---

### Post by OneSeventeen on 2007-04-23
[size=4]**Unofficial Step: Make some graphics**[/size]
Just to test out the ability to make 3d graphics as well as 2d graphics, I made a quick and shiny 3d image, and manipulated it in Inkscape to give it rounded corners and a drop-shadow.
[img]http://bin.woventhorns.com/117_test.png[/img]

Interestingly enough Blender runs much faster on Ubuntu than XP on this laptop.

---

### Post by xxrealmsxx on 2007-04-24
> **OneSeventeen said:**
> [size=4]**Step 4: Get Wireless Working**[/size]
I found [DarkNoob's thread on how to install Broadcom 43xx based wireless cards](http://ubuntuforums.org/showthread.php?t=405990) using a simple script that just installs the firmware that was pulled from a windows driver using fwcutter.  (This way I didn't have to use fwcutter because he already did it for me.)

I downloaded the script, extracted it to a folder, then in a command line ran the shell script to copy the drivers over.

It works perfectly on unsecured networks, and not at all on WPA protected networks.  :(

I may look for a linux native-supported brand of wifi cards for my laptop in the future, but as long as it can deal with the WEP I have going on at home, I'll be happy.

I download at roughly 2.3 Mb/s, which is the same as on my wired connections here at work.  (We are a little bit slower because we have a corporate fiber line that keeps us consistent, which is apparently crazy expensive but well worth it in the long run.)

I will post more as I go along.  (3d window effects do not work yet, but that pales in comparison to being able to connect to wifi networks!)

I picked up an Aetheros card and it works right out of the box.

I love my zv6000 in Vista/Xp but god if it hasn't stopped me from going 100% linux I don't know what else has :(.

Good luck! I'll be watching the thread.

---

### Post by arfink on 2007-04-24
I love my zv6000 too, but there is one hitch with the video- they come with the ATI Xpress 200m chipset, which if you look closely, is supported on the open source video acceleration drivers, but only for 2d aceleration. The proprietary ATI drivers don't even include the Xpress 200m. I found that the drivers for the closes match, the Xpress 200, don't work right and tend to hang up the system. :( I really have no idea when they will fix that. It ticks me off, because in Windows my machine is a beast for gaming, but it feels like a wussy machine in Linux, especially when I can't even run basic 3d software. 

Oh yeah, got those wireless drivers working really well. I downloaded them in Windoze and then moved the package from the NTFS partition to the Linux one, because I can't seem to find my ethernet cable around- turned my dorm upside down, but now I don't need to worry 'cuz my wireless works!! :popcorn:

Edit: I will be re-doing my install and going from 64-bit to 32-bit because I am too lazy to figure out how to make everything work 64 bit on my own. Tell you how that works, it should actually be easier than before.

---

### Post by Jeff Gavett on 2007-04-29
Would you all suggest sticking with an earlier version or is it worth it? My friend whose zv6000 I set up is currently running dapper because edgy just wouldn't work with the wireless card.

---

### Post by arfink on 2007-04-30
My Fiesty works OK with the onboard wireless chipset, not the fastest beast on the block, but that's because I used the firmware rip instead of doing it with NDISWrapper.

---

### Post by fain on 2007-06-05
i am using ubuntustudio and have the zv6000 with 
03:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

i used
 ```
sudo apt-get install bcm43xx-fwcutter
```
now i have a wep encrypted connection.
i was really hopeing for wpa tho :(
o well this will do for now.
i have used ndiswrapper with this card in SuSe 10.1 and had instability problems.
i hope this driver works better.

---

