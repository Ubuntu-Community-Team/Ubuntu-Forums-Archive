---
title: "Jaunty UNR on EeePC 900 (Celeron) issues"
date: 2009-04-26
forum: Hardware
---

### Post by dfjkl on 2009-04-26
I'm having a few issues that don't really make Jaunty UNR usable currently on the Eee and am wondering if there are any solutions out there.

The account I created during install, when I login there is no bar on top of the Ubuntu netbook launcher.  To get it back, I have to switch to full desktop and back again.

When I go back to the Netbook Desktop I get an error:

```
An error occurred while loading or saving configuration information for netbook-launcher.  Some of your configuration settings may not work properly.  DETAILS:

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash.  See http://projects.gnome.org/gconf/ for information (Details - 1: Cound not send message to gconf daemon:  Message did not receive a reply (timeout by message bus)). 
```Also, I created another user just to see if that user would give me any issues.  I was able to login successfully with the menu/information bar on top of the netbook-launcher interface with no issues, but I did it as a "switch user" function, then when switching back to my main users...the screen went black, and the disk light went solid for a few minutes before just doing some random activity...the OS never returned though, powered it down.

Also...should the netbook launcher interface be sluggish and jerky moving over the menu items?  My Eee has 1GB RAM....kind of curious.  

Is there any information out there on how to fix all these issues w/ Jaunty UNR?  I can't be the only one experiencing them...I did nothing special except install it and attempt to use it.

---

### Post by dfjkl on 2009-04-27
After installing the linux-image-2.6.28-11-generic_2.6.28-11.43~lp349314apw5_i386 kernel after finding some of the bug reports on Jaunty for the Eee, netbook-launcher is much more responsive and switch-user seems to be working now.

What I'm still having a problem with is the error message above on the user created during install and also on the user created during install I don't have a taskbar available and the application windows don't appear to be "reshaped" as they normally would until I switch to desktop and back to netbook mode.  Here is what I'm greeted with on a standard login:

[IMG]http://www.elitists.org/frank/tmp/Screenshot.png[/IMG]


...and after the desktop switch 2-step to restore the menu bar, it gave back a non-themed one this time it appears:

[IMG]http://www.elitists.org/frank/tmp/Screenshot-1.png[/IMG]

Any ideas about fixing this?  File a bug report?

Thanks!

---

### Post by blackened on 2009-04-27
By the way you describe it, it looks like gnome-panel and gnome-settings-daemon are failing to run properly on startup. When you get the un-themed panel, try using alt+f2 and running gnome-settings-daemon to get the theme settings back.

I'll poke around and see if I can't find a related bug.

---

### Post by dfjkl on 2009-04-27
Hm.  On login again I did not have the task bar but gnome-settings-daemon was running.  Killed and restarted it, no change.  I had to do the 2-step again to get everything proper again, but this time it came back correctly themed.  If I could solve why I have to switch modes everytime after a login it would be great (and also figure out why it is throwing that annoying error).  I had done nothing special w/this install until that kernel change to address the speed issues.

---

### Post by blackened on 2009-04-27
I wonder if you would experience the same issues if you installed the regular x86 desktop version, then added the UNR packages after installation. I'm using the stock install with no issues. Haven't tried UNR though.

That said, I remember reading some discussion on whether or not you absolutely *had* to have an Atom based machine to run it. I think the concensus was that UNR is i386 optimized, not lpia. You might double check my facts though, just to be safe.

---

### Post by francescomm on 2009-04-27
I have the same problem on an Eee 701 4G
UNR is running on an 8GB USB key. System has 4GB RAM.

: : : Description

gnome-panel not starting (or not being viewed) at startup.
Window decorations (title bar) not viewed at startup.

This happens both in the Netbook Desktop and in the traditional Desktop mode
I cannot move and resize windows.


: : : Temporary solutions

I have added a Laucher for gnome-panel on the desktop
I make windows titlebars and resize icons appear going to the Visual Effects control panel, activating "Normal" effects and then reverting to "none".

Doing both things reverts the machine temporarily to a perfectly usable NetbookRemix  install. But at every restart the problem returns.




: : : Possible causes

It was ok at startup, if I remember. I am not sure because of the huge speed problems that were solved installing the new .43 kernel. I did many restarts and changes of desktop kind (regular/netbook) to try to understand the speed problem.

What might have jammed things:

- starting up connecting a secondary monitor

- closed the Eee lid while it had not completely finished a shutdown

- ..

---

### Post by dfjkl on 2009-04-27
I've done none of those things that might complicate the issue.  I have updated the kernel to address the speed issues.  I've not tweaked a single config file on this yet nor have I gone in and messed with any of the system or desktop settings (except to switch back and forth between desktop modes).  Just looking for something for the Eee that "just works."  Had some good experiences briefly w/ Ubu on the desktop...was hoping for a repeat on the Eee.  Guess that's what I get for playing w/ the bleeding edge.  If someone can point me in the direction of resolving issues though...that would be great.

---

### Post by davidryderuk on 2009-04-27
Hi i believe this is your problem. Hopefully it should be fixed with an update to desktop-switcher soon. For the time being it seems to be best to avoid using the desktop switcher. 

> **njpatel said:**
> This a bug in the desktop-switcher package ([https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519)), which I'm trying to fix and get uploaded to Jaunty before release.

To fix the issue you have currently (gnome-panel and/or windowmanager not starting), please run the following command depending on which mode your currently running in:

If in Netbook-mode, should execute:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

If in Classic mode:

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]

I have updated desktop-switcher .debs available in that bug for which I am looking for testers (I would appreciate feedback on that bug). Once you've run the above commands, you can install the latest deb from that bug and hopefully further switches will work without issue.

Thanks and sorry for desktop-switcher screwing up :)

-- Neil

---

### Post by dfjkl on 2009-04-28
That seems to have fixed it.  All good now.  Thanks!!  I didn't actually run any of those commands.  I installed the latest deb offered and it just fixed up most everything.  I still had to run another command to restore all the default settings to eliminate the error, but now I'm all up and running.  I updated the bug with details.

---

### Post by francescomm on 2009-04-28
I have performed a clean install, installed the kernel debs to speed up the netbook-launcher, installed the deb in this tread. Attached a second monitor in NetBook Desktop, played with the display panel, arrange monitors,..etc was asked to logout. Switched to full desktop. After restart same problem again

---

### Post by davidryderuk on 2009-04-28
Great thanks dfjkl, I could only avoid the problem before I saw your post on the bug report and here, but now it seems to actually be fixed. 

You might want to check the bug report again francescomm, the package that solved my problem was only posted yesterday so you may have missed it.

---

### Post by Orbital_sFear on 2009-05-06
I'm having the same issue with my eee 1000he, but found a solid work around.

[https://bugs.launchpad.net/ubuntu/+bug/366109/](https://bugs.launchpad.net/ubuntu/+bug/366109/) is the bug we are talking about.

               [VladIonescu]("https://bugs.launchpad.net/%7Evladimir-ionescu")          wrote     on 2009-04-27:     [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+bug/366109/comments/4")   
                   A better workaround for me was this: First I created a launcher on the desktop with the command gnome-panel. Executing it restores the menu bars. Then I opened System->Preferences->Startup Applications and added gnome-panel and gnome-wm. After restarting the machine everything seemed normal.


Here are the steps I took.


Goto preferences - switch desktop
toggle to classic then back to unr
Now the task bar exists
Then open system - preferences - startup application
add gnome-panel
add gnome-wm
reboot and things should start normally now.

---

### Post by salttalk on 2009-09-18
I don't understand much about the terminology used in these threads, but enough to fumble my way around. In other words, I need real simple instructions guys.

On my Eee PC 900, I recently installed Jaunty (Ubuntu 9.04 netbook remix). I run it in Classic mode, because I could not get the other mode (UNR) to run properly.

Originally, the netbook ran on the full version of Xandros linux. But I prefer Ubuntu since Xandros never gets updates and cannot do a lot of the things Ubuntu does. (I knew this because I use Ubuntu on my desktop and have used it on other computers as well.)

So I finally got around to installing Ubuntu on my netbook through a thumb-drive. By the way, my netbook now has a broken screen (I think someone sat on it), so I use an external monitor all the time now. To get the resolution up on the external monitor, I deselected "Mirror" on Preferences>>Display option, then clicked on the separated external display icon and reset the resolution. I turned off the netbook screen. It works very well!

I really like this netbook running on Ubuntu. Ubuntu with Open Office and Firefox is ideal because I work for hours on the computer every day, writing and doing research. However, there are a couple of problems.

This netbook has two storage devices, a hard drive with about 4 Gigs of space (which has the operating system loaded on it), and another storage device with about 16 Gigs of storage space. The 1st device now has only about 600 Megs of remaining space, but the second bigger 16 Gig device is almost empty (I store Open Office files and data there). Also, Ubuntu does not mount this 16 Gig device at startup, so I have to mount it manually every time.

Now I wanted to ask, **how do I get Ubuntu to mount the 16 Gig device every time the netbook boots up?** The other 16 Gig device is called /dev/sdb1 or /media/disk in the System Monitor. I would like Ubuntu to mount it and store as many data files there as possible, because I'm already running out of room on the 1st storage device.

Another noteworthy problem is that the wireless device still is not running as well as it was on Xandros linux. I tried most of what was suggested on the forums, but ended up using the default. At least it works sometimes. I guess I can live without a consistent wireless connection, because I can use a cable and wired network. But it would be nice to see the wireless run a little better, and not need to pull out the cable so often to surf the net.

Thanks.

---

