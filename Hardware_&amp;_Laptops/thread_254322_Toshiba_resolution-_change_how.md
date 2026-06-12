---
title: "Toshiba resolution- change how???"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by RKelly5327 on 2006-09-09
Folks, I did mention this in a previous post but it was involving other issues too. I have a 2100CDS Toshiba. It has an S3 ViRGE MX video adapter. It's capable of 64 million colors and 800x600 resolution. I am presently using a different hard drive with both Windows 2000 and XP Pro on it. I can get that resolution with both systems. 
The Xubuntu system won't let me get anything but about 640x480 and looks terrible. Someone here told me to check the system file located at filesystems/etc/x11/xorg.conf which I finally found- had no idea where to look. When I checked the Screen section I found what looked like options in the file which should let me choose a better resolution, but they simply are not available from the desktop. I only have two options, the crappy one now being used or an even worse one at 320x280 or some such thing. If this Linux system is so much better than Windows why isn't it capable of doing the same thing? And this wireless internet hookup! Unbelievable! It works fine with the Live CD but as soon as I installed it (Xubuntu) away went the internet connection. The weird thing about that is that the signal indicator on the wireless card has a steady light, as if it's receiving the signal fine. When it can't establish a connection it blinks. Even so, I can't get on the web now that I've installed Xu. 
I almost said Phooey on the whole thing and reformatted the drive and set it back up with Windows again, but thought I'd wait a while and see if anyone can help get this beast working.
Thanks to all.
RK in PAh

---

### Post by mssever on 2006-09-10
Does the xorg.conf have decent options already present? If not, you can make a backup of xorg.conf and add them.

In Ubuntu, you can change screen resolutions by going to System > Preferences > Screen Resolution. I don't know if this works in Xubuntu. The brute force method would be to delete all the resolutions you don't want from xorg.conf--after a backup, of course--and log out and kill X (Ctrl+Alt+Backspace).

Wireless setup is probably the most difficult aspect of Linux setup these days, thanks to wireless card manufactuers who are very uncooperative with Linux developers. You should probably post a separate thread with the make and model of your card, and sombody can probably help you.

---

### Post by RKelly5327 on 2006-09-10
Yes, the xorg.conf does have decent options, even some that are a lot better than the 800x600 that my laptop can do. That's what is so puzzling to me. They are there in the xorg.conf file but they are not available in the Display options from the desktop. The 800x600 is there in the file, but not from the desktop. One thing- I see in the file that it has Default with a number after it which I think is 1. I wondered if changing that number to coincide with the number that represents the 800x600 option would give me the desired resolution. What do you think? Two other things- I don't know how to back up the file before messing with it.  The other is I don't know what you mean by logging out and killing X. Sorry...
Thanks for the info. Hope we can make a go of this.
Ron

---

### Post by mssever on 2006-09-10
> **RKelly5327 said:**
> Yes, the xorg.conf does have decent options, even some that are a lot better than the 800x600 that my laptop can do. That's what is so puzzling to me. They are there in the xorg.conf file but they are not available in the Display options from the desktop. The 800x600 is there in the file, but not from the desktop. One thing- I see in the file that it has Default with a number after it which I think is 1. I wondered if changing that number to coincide with the number that represents the 800x600 option would give me the desired resolution. What do you think? Two other things- I don't know how to back up the file before messing with it.  The other is I don't know what you mean by logging out and killing X. Sorry...
Thanks for the info. Hope we can make a go of this.
Ron
There are many ways to backup a file. One way is this:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.backup
```
Once you have a backup, try different ideas you have until you hit on something that works. Kill X between tries. And if you break something, that's why you have a backup.

To kill X, hit Ctrl+Alt+Backspace. I would recommend that you log out before doing this (so that the login screen is showing), or that you at least close all programs first.

---

### Post by RKelly5327 on 2006-09-10
I'm sorry for my ignorance, but I don't know what you mean by Kill X. Do you mean that deletes the file?
Thanks,
Ron

---

### Post by mssever on 2006-09-11
No. X is short for the X Windowing System (Ubuntu's flavor is known as Xorg). X is also sometimes called X11. X is what provides the graphical interface--as opposed to a prely text-based interface.

Killing a program means making it exit through some means external to the program (known as sending it a signal). There are varying degrees of "niceness" when it comes to killing a program. For example, sending SIGHUP or SIGTERM (signals 1 and 15, respectively) generally causes programs to save their state and clean up after themselves before exiting. Sending SIGKILL (signal 9) forces a program to exit immediately without saving or cleaning up.

I'm not sure which signal Ctrl+Alt+Backspace sends, but it's the way to kill X.

For more info, read ```
man kill
man killall
```

---

### Post by RKelly5327 on 2006-09-11
As Ricky Ricardo would say, "I yi yi yi yi!!!" A whole new world of terminology! Oh my! Well, guess I'd better dig in. Glad I asked!
Thanks,
Ron

---

### Post by halw on 2006-09-11
Having the same problem as Rkelly. The system at issue here is a Toshiba 2545xcdt. Thus far have change video setting at boot to live cd. No joy.


Hopefully a resoution can be found.

---

### Post by RKelly5327 on 2006-09-11
The resolution on mine was the same with the Live CD, Xubuntu, that is. Regular Ubuntu wouldn't even load on my Toshiba. Not enough RAM, I guess. The only thing different with mine on the Live CD and having loaded it is that my wireless card worked fine with the Live CD but won't work with the installation.
Ron

---

### Post by halw on 2006-09-11
Haven't tried loading Xubuntu onto hard disk yet. Currently have Mepis 3.4-3 loaded. No problems with resolution or wireless with it.

The reason I was looking at Xubuntu is that my machines memory is maxed out at 192 KB and was trying to find distro that played nice with that amount of memory.

FYI, have tried DSL, Puppy, Knoppix and a couple others and they all choke with my pcmcia wireless card on startup.

---

### Post by mssever on 2006-09-11
> **RKelly5327 said:**
> The resolution on mine was the same with the Live CD, Xubuntu, that is. Regular Ubuntu wouldn't even load on my Toshiba. Not enough RAM, I guess. The only thing different with mine on the Live CD and having loaded it is that my wireless card worked fine with the Live CD but won't work with the installation.
Ron
Have you had any success with xorg.conf yet?
> **halw said:**
> Having the same problem as Rkelly. The system at issue here is a Toshiba 2545xcdt. Thus far have change video setting at boot to live cd. No joy.

You might find different/better results once you do an actual install. The live CD isn't identical to an install. Also, given your limited system resources, you might find that the alternate install CD plays nicer with your system.

---

### Post by RKelly5327 on 2006-09-11
My laptop says it has 160 MBs of RAM so it's even less than yours. I've never heard of Mepis. I guess that must be another install of Linux. I wonder if that would work on my Toshiba. I've given up trying to make anything of the Xubuntu. I tried editing the xorg.conf file and after I went to save it, I got a popup telling me it wasn't able to do that. I'll have to check into this Mepis.
Ron K

---

### Post by mssever on 2006-09-11
It's possible that Mepis might work better for you. Different distros work better with different hardware.

However, the reason that you couldn't save xorg.conf--and this issue will likely crop up with most distros--is that system files require superuser (aka root) privileges to edit. In Ubuntu, you could open up a terminal and type ```
gksudo gedit /etc/X11/xorg.conf
```
note the gksudo part. gksudo is for graphical apps, and sudo is for text-based apps.

I don't know whether Mepis uses gksudo/sudo or su (the other common way of gaining root privileges), but you'll need to do something along those lines in pretty much any distro.

---

### Post by RKelly5327 on 2006-09-11
I downloaded the version you have and am giving it a whirl. It booted up but I didn't get to log in because of the password. I'll reboot and try to catch the clue to get in. Have to pay attention, I guess. 8-) 
RK

---

### Post by RKelly5327 on 2006-09-11
Whaddayaknow! It works! The resolution is much better and the Wireless card (PCMCIA) even works. It's a bit slow because of my CPU (400GHz) but it is working. I'm having a bit of trouble getting the screen just right so I can see everything. I saw in the setup it said something about setting up a shortcut to view the wireless signal strength, but it went by before I saw what to do. ha.
Thanks for the Mepis tip.
RK

---

### Post by halw on 2006-12-11
RKelly, 

Are you still using Mepis or did you find a fix for your resolution problem in Ubuntu?

Just thought I would ask as I would like to try Xubuntu but unable to crack the screen resolution issue.

---

### Post by RKelly5327 on 2006-12-11
I gave up on Ubuntu. It didn't work at all. I haven't done anything with Mepis either. Just haven't had time, but it did work whereas Ubuntu wouldn't work at all.
Ron

---

