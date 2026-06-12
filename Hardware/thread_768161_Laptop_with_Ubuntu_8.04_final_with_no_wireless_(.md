---
title: "Laptop with Ubuntu 8.04 final with no wireless :("
date: 2008-04-26
forum: Hardware
---

### Post by rootk1t on 2008-04-26
What can I do?

> root@john:/# lspci | grep -i broadcom
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

I have a HP dv9645ed notebook.

Thanks!

---

### Post by bodgetastic on 2008-04-26
Have you tried ndiswrapper?  At work I have an HP laptop with a broadcom card that this worked with.  You'll need the Windoze driver for the card, I think that I downloaded it for mine but you should be able to use the driver CD.

You should be able to install ndiswrapper through Synaptic.

Next you need to unzip the windows driver package if it's zipped - you need the .inf file and the .sys file.

ndiswrapper should make a menu entry under System->Administration, something like 'Windows Wireless Drivers' (apologies, I'm going from memory on Gutsy here...).  This should ask for your password, then give you a window with some options.  One of these should be 'Install...'.  Point this at the .inf file from your driver package.

This should do it all automatically.... If you randomly lose the driver try 'modprobe ndiswrapper' as root.

If you can't find the GUI then try this from a terminal...
sudo ndiswrapper -i {path-to-inf-file}
sudo ndiswrapper -l
sudo ndiswrapper -m

The first command installs the driver.  Look out for any errors on this.
The second command tells it to list drivers available.  You should see something like this:
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)
(that's for my RealTek card on Slackware)

If you see that kinda think then all should be well (I think that the Broadcom driver is  something like bcmlw...) and you should run the third command, which writes the config info to the system and causes it to load every time.

---

### Post by JosephInEgypt on 2008-04-26
Hi,

     I have an HP Pavilion dv5139us laptop that I have been trying to get the wireless to work for quite some time.  My problem is that I am a noobie when it comes to Linux.  I am very much excited about switching to Linux because I believe in the movement, and I absolutely thin Microsoft and Apple both need to get off their high horses.  Anyways, I have tried to find a good step by step guide for beginners for the nsdiwrapper thing, but have never succeeded in installing it right because I need like step by step for "Dummies" guide.  I would greatly appreciate it if someone could guide me in this because I have tried just about every Linux distro out and I am convinced that Ubuntu is the best,...if I could just get my wireless to work I would switch over completely for ever.  Thank you in advance to anyone who decides to try and help me with this,...I have been trying to get this to work for quite some time.

Here are my basic Specs:

HP Pavilion dv5139us
AMD Turion 64
2048MB RAM
120GB HDD
ATI Mobility Radeon Xpress 200
Bluetooth Integrated 10/100 Network Card
WLAN 802.11a/b/g

If any other info is needed to help me out with this please let me know.  Many thanks. :-)

---

### Post by rootk1t on 2008-04-26
> **bodgetastic said:**
> Have you tried ndiswrapper?  At work I have an HP laptop with a broadcom card that this worked with.  You'll need the Windoze driver for the card, I think that I downloaded it for mine but you should be able to use the driver CD.

You should be able to install ndiswrapper through Synaptic.

Next you need to unzip the windows driver package if it's zipped - you need the .inf file and the .sys file.

ndiswrapper should make a menu entry under System->Administration, something like 'Windows Wireless Drivers' (apologies, I'm going from memory on Gutsy here...).  This should ask for your password, then give you a window with some options.  One of these should be 'Install...'.  Point this at the .inf file from your driver package.

This should do it all automatically.... If you randomly lose the driver try 'modprobe ndiswrapper' as root.

If you can't find the GUI then try this from a terminal...
sudo ndiswrapper -i {path-to-inf-file}
sudo ndiswrapper -l
sudo ndiswrapper -m

The first command installs the driver.  Look out for any errors on this.
The second command tells it to list drivers available.  You should see something like this:
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)
(that's for my RealTek card on Slackware)

If you see that kinda think then all should be well (I think that the Broadcom driver is  something like bcmlw...) and you should run the third command, which writes the config info to the system and causes it to load every time.

Thanks a lot for your reply,

BUT:

I downloaded my driver, and it's a EXE! Exracted that exe and found another EXE and a MSI file. How can I get those files?

[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/) found this, but I can't extract the needed files :(

---

### Post by rootk1t on 2008-04-26
So where can I find the appropriate .inf file for my device? :(

---

### Post by jfhillmann on 2008-04-26
The *.exe from dell is a self extracting file. On a windows machine, run the exe which will build a directory structure on the PC which contains the *.inf & *.sys. The move the files to the unbuntu machine.

---

### Post by rootk1t on 2008-04-27
> **jfhillmann said:**
> The *.exe from dell is a self extracting file. On a windows machine, run the exe which will build a directory structure on the PC which contains the *.inf & *.sys. The move the files to the unbuntu machine.

Did that, the problem is that on the HP website I only find drivers for Vista, that are not supported by ndiswrapper.

Do you know any sys and inf files for BCM4312 for Win XP?

---

### Post by QuaintRealist on 2008-04-27
I've been getting my BCM43k card to work with ubuntu since 6-10 unsing ndiswrapper, and gotten pretty good at it, I thought.  Could not get it to work at all with Hardy Heron.  So I tried the fwcutter route - get an ethernet connection, use Synaptic (or whatever) to download "b43-fwcutter".  During the install, when it asks you if you want to install drivers pick Yes.  After installation completes restart - you should have wireless.  Worked for me just that easily - hope it works for you

---

### Post by rjmoerland on 2008-04-27
> **QuaintRealist said:**
> So I tried the fwcutter route - get an ethernet connection, use Synaptic (or whatever) to download "b43-fwcutter".  During the install, when it asks you if you want to install drivers pick Yes.  After installation completes restart - you should have wireless.  Worked for me just that easily - hope it works for you

Or, other route, same result:

use the Hardware Drivers item from the System menu. In my case, my Broadcom B43xx card showed up there. Check the box 'Enabled', let ubuntu do its thing, and you also should have a working connection.

HTH

---

### Post by QuaintRealist on 2008-04-27
My Broadcom4306 did not show up in the hardware drivers menu, unfortunately.  But you're right - if yours does you're home free.  Sometimes it's hard to remember the intermediate steps you tried that didn't work.  And dont get me started on the time I wasted fiddling with my modprobe blacklist!

---

### Post by rootk1t on 2008-04-27
> **QuaintRealist said:**
> I've been getting my BCM43k card to work with ubuntu since 6-10 unsing ndiswrapper, and gotten pretty good at it, I thought.  Could not get it to work at all with Hardy Heron.  So I tried the fwcutter route - get an ethernet connection, use Synaptic (or whatever) to download "b43-fwcutter".  During the install, when it asks you if you want to install drivers pick Yes.  After installation completes restart - you should have wireless.  Worked for me just that easily - hope it works for you

I used Synaptic, installed b43-fwcutter, he asked me if I want to extract the firmware -said yes, rebooted, and no sign of wireless.

Nothing in /var/log/messages or dmesg. Absolutley nothing. :(

---

### Post by bodgetastic on 2008-04-27
Hi there - I couldn't remember where I got it from either, so I did a bit of googling and turned up this excellent post:

[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)

It goes right through installing ndiswrapper from source, but you shouldn't have to do that.  It does go through where to find a driver and how to get at it.

So, with all credit to the author of that post, you should be able to open a terminal window and type in:

sudo aptitude install wget cabextract
[and type in your password, it won't be echoed back to you]
mkdir broadcom-driver-install
cd broadcom-driver-install
wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
cabextract sp33008.exe

The first command tells the system to install the programs 'wget' and 'cabextract'.  If either is there it won't over-write (I think).  Wget is a commandline network downloader (and very handy!) while cabextract lets you get the files out of that pesky .exe.

The fourth command tells wget to download the driver from hp - if you've already got one then ignore this line!

The fifth is the crux of the matter - use cabextract to get all of the bits out.  Tried the above on my system and it gave me a couple of .cabs, Setup.exe with associated bitsnbobs, and the bcmwl5 inf and sys files.

Once you've installed the driver in ndiswrapper, you shouldn't need to reboot - a simple 'sudo modprobe ndiswrapper' in a Terminal should suffice.  I don't know  if there's a GUI way of doing that or not...

Hope that's of some help!  Btw, what was the url you found your .exe on?

---

### Post by rootk1t on 2008-04-28
Well, that's the exe for bcm4306 and I've got bcm4312, is that OK?

---

### Post by rootk1t on 2008-05-04
> **rootk1t said:**
> Well, that's the exe for bcm4306 and I've got bcm4312, is that OK?

Anyway it's not working :confused:

No sign of wireless...

---

### Post by rootk1t on 2008-05-16
Someone, please?

---

### Post by rootk1t on 2008-05-17
So nobody can help me?

---

### Post by Ayuthia on 2008-05-17
> **rootk1t said:**
> So nobody can help me?
The 4312 rev 02 card is currently not very happy with the b43 drivers in Ubuntu.  You will need to go the NDISwrapper route.  The guide that was provided to you was a good guide, but does not cover 8.04.  There are new drivers introduced in the kernel and now creates extra steps for NDISwrapper.

Here is a [link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") that might help.  It gives you some driver options and tells you how to extract them (.exe files need cabextract from the repositories).  It will also tell you how to disable the ssb driver that is currently causing your problem. 

If you are still having problems, please come back to this thread and tell us where you are stuck.

The HP laptops seem to be happy with using similar drivers so for NDISwrapper, the driver that is used for a 4306 could also work for other models too.

---

