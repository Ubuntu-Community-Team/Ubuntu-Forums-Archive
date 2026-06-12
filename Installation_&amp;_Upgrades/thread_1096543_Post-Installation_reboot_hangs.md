---
title: "Post-Installation reboot hangs"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Martel791 on 2009-03-15
Hey,
I have an old Dell Dimension L433c desktop that I am trying to install Xubuntu 8.10 on. The basic system specs are: Intel Celeron processor @ 433 Mhz, 320 Mb RAM. I have tried installing the system 2 ways: from inside a live cd session via the "install" icon, and from the menu that comes up when the computer first boots into the Xubuntu menu. Both ways I have had the same problem. The install will do its thing and finish, and ask to reboot. Now, the splash/loading screen for *buntu has 2 parts, first a small bar that bounces back and forth, then a bar that remains stationary and "grows" until the login screen appears. When I restart after the install, the loading screen will do the first part, but when it should start the second part, instead it shows a wall of text as follows:

```
Boot from (hd0,0) ext3   *bunch of letters\numbers*
starting up ...
Loading , please wait...
usplash: Setting mode 1024x768 failed
usplash: Using mode 800x600
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Mising modules (cat /proc/modules: ls /dev)
ALERT! /dev/disk/by-uuid/*bunch of letters\numbers equal to set above^^* does not exist Dr
opping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.
```

Following this are a bunch of entries filled with lots of stuff I don't understand, a picture of a sample of which is attached.

Things like that scroll by and after a while the system just stops doing anything, although it can't be technically frozen, because it goes into a blank "screensaver" mode after some time, which goes away when a key is pushed. That pic shows the end of the scrolling text.
The only other times I have installed Ubuntu the installer worked perfectly, so I am at a loss as to what to do. How can I get the system to correctly reboot into Xubuntu as opposed to this mess? (read: HELP!!)

I am still somewhat of a newbie to Linux so please try to keep things simple for me ;). Thanks for any/all assistance!

---

### Post by Martel791 on 2009-03-15
Solved this one myself! :cool:

Typing 'exit' a few minutes into the scrolling code got me back into a normal boot (albeit without the loading screen).
Then all it took was adding:
```
rootdelay=90
```
to the end of the kernel line in menu.lst for everything to work right!

---

