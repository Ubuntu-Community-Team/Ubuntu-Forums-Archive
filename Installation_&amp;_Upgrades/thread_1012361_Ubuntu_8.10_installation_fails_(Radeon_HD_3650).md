---
title: "Ubuntu 8.10 installation fails (Radeon HD 3650)"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by trumanhw on 2008-12-15
Radeon HD 3650 doesn't work without advanced installation in 8.04, but I'm honestly surprised that it isn't resolved in 8.10. 

If you have a solution, please, write it in ENGLISH, not coded in a format that would work if I filled in what is obvious only to a person who learns coding for FUN! Its not my concept of fun. I see about 20 different people with the same problem, which means probably 2000 people have the problem - so will some altruistic person more geeky than I please give SIMPLIFIED means of solving this for me, and the rest of us? Preferably, just tell me WHERE to COPY and PASTE a few lines in to a terminal. :-)

Second, if the solution involves "getting" packages, please suggest a means to configure my network in terminal as well, as it didn't autoconfig, and since its in terminal, I can't backspace, delete, nor save in an obvious fashion. If I can download the files to "get" on my laptop, burn them to a disc, then "get" them from the disc, that's perfectly fine. 

I know, I shouldn't let the fact that Im irritated bleed through unto people who haven't irritated me that Im seeking help from, but there seems to be a general preference for being jargon oriented in this community, perhaps for shorthand's sake, but perhaps because someone thinks its actually "cool," which it's certainly no measure of, if not a proof of the opposite.

---

### Post by wpshooter on 2008-12-15
Can you explain what do you mean when you say that it doesn't work without advanced installation in 8.04 ?

Thanks.

---

### Post by trumanhw on 2008-12-15
System boots, shows splash screen, progress bar - then white.

The system isn't 'crashed,' as if I type my username and password I can tell that it starts logging in, and if I type anything but that (username/password) it just accesses the hdd for a nano-second, so Im sure its strictly a video issue, and other people seem to have the same Radeon HD 3650 problem. 

How do I install the Radeon HD 3650 driver/package when I can't access the internet as i have to manually configure after setup, but, I can't get in to the OS to setup the internet as I can't see video. 

thanks.

---

### Post by trumanhw on 2008-12-16
some help would be appreciated.

---

### Post by Herman on 2008-12-16
I have a computer with a Radeon HD3650 video card and I have both Hardy Heron 8.04 and Intrepid Ibex 8.10 running in it alright.

I had some trouble with it at first especially in Intrepid Ibex.
Intrepid bex is extremely slow to boot at first, and then it pauses during boot-up and I get a notice about my computer running in 'low-graphics mode', and urging me to update my configuration file, as '(EE)RADEON(0): Acceleration initialization failed'.
Then I get a choice of three options, if I leave it on the default, 'Run in low-graphics mode for just this session', it works okay.
I have learned the hard way to refrain from optimistically trying the other two choices. When I tried the other two choices it wrecks itself and the easiest way I know so far to fix it is to re-install. I imagine there's a better way, but if there is, it hasn't been made apparent to the user. 

The default driver is actually alright, I'm able to boot up okay, and the picture in the monitor is fine. 
Before I bought the video card Ubuntu would boot up normally but if was just a little slow to use and the video had tiny horizonal flickering  lines in it, but it was usable.
Now that I have the video card I have a nice picture, and my computer is running much faster, even if Intrepid Ibex does complain at every boot-up.
Even if I could just turn off the annoying question at each boot, I'd be happy. I don't really care too much about fancy desktop effects anyway, all I wanted was a clear picture and a fast machine, (well, faster than it used to be), which I have now.

I am optimistic that things like this will be improved with Jaunty Jackalope, and I will be installing the alpha version of that in the machine I'm talking about to see how Jaunty Jackalope progresses.
One of the goals that the developers have set themselves for Jaunty Jackalope is better hardware support. Probably there will be updates for Intrepid Ibex users along the way. It would be nice to have the ability to have the video card working to it's designed potential.

It seems truly amazing to me that Linux, and Ubuntu supports and millions of different hardware items out there as well as it does already. The developers are doing a great job, and I would like to thank them for everything they've done so far. 
I forgot to mention that I got this computer for free from the dump because Windows XP wouldn't boot in it, and Windows couldn't be fixed. 
This computer works great with Ubuntu in it though, (with or without the video card).

Regards, Herman :)

---

### Post by Herman on 2008-12-16
> How do I install the Radeon HD 3650 driver/package when I can't access the internet as i have to manually configure after setup, but, I can't get in to the OS to setup the internet as I can't see video. Probably you can press 'Ctrl+Alt +F1' (or F2 to F6 keys) for a console, but you'll need to know how to do things with the command line for that.
I have fixed my problems that way before, but with all the changes to the x-server, I'm not up to date on what to do anymore.

---

### Post by trumanhw on 2008-12-16
Thanks Herman, and I'll try not to despair. 

So far, I've seen suggestions for 

xforcevesa

to be added to the 'end of a string' of characters, but I'm uncertain as to where, and which selection to choose.

and another one about editing GRUB ?? By entering text such as gdm


something wrong with x.org. When in grub menu, select the line you want to boot and press e for edit the line. at the end add xforcevesa

in this way you'll force X.org to use vesa resolution

Boot in recovery mode and type

Code:

sudo /etc/init.d/gdm start

or

Code:

gdm start

or

Code:

startx


Obviously, I'm still missing a critical step. Anyone have advice on how to enable force vesa?

---

### Post by Herman on 2008-12-17
> So far, I've seen suggestions for 
xforcevesa
to be added to the 'end of a string' of characters, but I'm uncertain as to where, and which selection to choose.

and another one about editing GRUB ?? By entering text such as gdm
something wrong with x.org. When in grub menu, select the line you want to boot and press e for edit the line. at the end add xforcevesa

in this way you'll force X.org to use vesa resolutionOh, okay, you're talking about adding kernel parameters, yes, that might help, 

Here's a very nice link about how to edit Ubuntu's /boot/grub/menu.lst file with kernel parameters, [grumpymole: Ubuntu - How To Edit Grub Boot Parameters]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")
...but, I don't know what it is exactly you need to type there.

> Obviously, I'm still missing a critical step. Anyone have advice on how to enable force vesa?     I found this link for you, 
**[[ubuntu] [SOLVED] Intrepid: how to *force vesa* driver on boot [B]...**]("http://ubuntuforums.org/showthread.php?p=6096524")[/B]

You could boot into recovery mode and use the text editor nano for editing your /etc/X11/xorg.conf file as described in that link above here, or you could use your Live CD to access the file, [Rescue your Linux system with a Live CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").

I hope something there will help you,
Regards, Herman :)

---

### Post by Herman on 2008-12-17
So, to illustrate, theyre saying you shoudl open up you /etc/X11/xorg.conf file in Hardy Heron and insert the line: [COLOR=Sienna]**Driver "vesa"**[/COLOR], like I have done in the example here, (below),
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    [COLOR=Sienna]**Driver "vesa"**[/COLOR]
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

---

### Post by Herman on 2008-12-17
> If you have a solution, please, write it in ENGLISH, not coded in a format that would work if I filled in what is obvious only to a person who learns coding for FUN! Its not my concept of fun. I see about 20 different people with the same problem, which means probably 2000 people have the problem - so will some altruistic person more geeky than I please give SIMPLIFIED means of solving this for me, and the rest of us? Preferably, just tell me WHERE to COPY and PASTE a few lines in to a terminal. :smile:Oh, okay then.

There are two ways to gain access to your /etc/X11/xorg.conf file for editing it.

If you decide to do it by booting into recovery mode, you'll need to be able to use the text editor called nano, because that's the text editor we can use in command line mode.
Nano is easy to use, but some people find it a bit hard to get used to at first, especially if you don't have someone to show you. (I had to figure it out on my own, but I had a good link for it, which is unfortunately down at the moment).
You would open the file with a command like,
```
sudo nano /etc/X11/xorg.conf
```Then you would use your 'down' arrow key to move the blinking cursor down to the line you want to edit.
Hilight the 'E" for 'Endsection in the line below it and press 'Enter' to make a new line.
Press your 'up' arrow key to move the blinking cursor to the start of your new line and type in 'Driver "vesa" '.
To save the file first press 'Ctrl+o', and 'Enter' to confirm, then to close the file and exit the text editor press 'Ctrl+e'.
(Nano has a bar to remind  you what keys you can press along the bottom of it when the text editor is open. The ^ (caret symbol) is shorthand for 'press your 'Ctrl' key).

The other way, explained in this link, [Rescue your Linux system with a Live CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")[COLOR=#666666][COLOR=#000000] - should be easier for most people, (just read the link and try it, it should work, let me know if you have trouble.
[/COLOR][/COLOR]

---

### Post by Herman on 2008-12-17
:) Hey, that fixed mine! No more slow booting and no more of those nagging warnings about my computer booting in low graphics mode! :)
:lolflag:

I hope you'll be lucky too!

Regards, Herman :)

---

### Post by RJARRRPCGP on 2008-12-17
> **trumanhw said:**
> Radeon HD 3650 doesn't work without advanced installation in 8.04, but I'm honestly surprised that it isn't resolved in 8.10. 

If you have a solution, please, write it in ENGLISH, not coded in a format that would work if I filled in what is obvious only to a person who learns coding for FUN! Its not my concept of fun. I see about 20 different people with the same problem, which means probably 2000 people have the problem - so will some altruistic person more geeky than I please give SIMPLIFIED means of solving this for me, and the rest of us? Preferably, just tell me WHERE to COPY and PASTE a few lines in to a terminal. :-)

Second, if the solution involves "getting" packages, please suggest a means to configure my network in terminal as well, as it didn't autoconfig, and since its in terminal, I can't backspace, delete, nor save in an obvious fashion. If I can download the files to "get" on my laptop, burn them to a disc, then "get" them from the disc, that's perfectly fine. 

I know, I shouldn't let the fact that Im irritated bleed through unto people who haven't irritated me that Im seeking help from, but there seems to be a general preference for being jargon oriented in this community, perhaps for shorthand's sake, but perhaps because someone thinks its actually "cool," which it's certainly no measure of, if not a proof of the opposite.

That doesn't make sense! Because X is fine with my GeForce 9500 GT, which is likely newer than a Radeon HD 3650!

Intrepid Ibex shall have been fine.

---

