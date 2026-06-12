---
title: "Gateway M275 with Ubuntu Hardy Heron (8.04.1)"
date: 2008-11-16
forum: Hardware
---

### Post by ScottHW on 2008-11-16
I was recently given a Gateway M275 Tablet PC laptop in a non-functioning state.  This laptop ships with Windows XP Tablet, but a clean format and the Recovery CD failed to bring it back to a working state.  I thought "If I'm going to have to fight with laptop drivers, I might as well fight with Linux drivers".

(I may summarize my Windows results later, but that is basically outside the scope of this forum apart from what it may tell me about *my* hardware specifically)

So, this is a report on the things I've learned, and perhaps more importantly, the issues I am still trying to resolve.

[B]If you read this and find it helpful, please drop a comment saying so.
Or, if you read this and it *doesn't* address some problem (either something else that you have solved, or something that hasn't even yet been solved) a response would be helpful there too.[/B]

Any pointers and or help about outstanding issues would be greatly appreciated.

As a disclaimer: I am certainly not a Linux expert, but I like to think I am a quick leaner.  If I've made mistakes, please help me make corrections for the entire community's benefit.

bonus tags:  Gateway, M275, tablet, linux, ubuntu, hardy, 8.04, gnome, wacom, drivers, graphics

---

### Post by ScottHW on 2008-11-16
I thought it might be possible that this laptop had graphics hardware issues.  During the Windows XP reinstall, the Safe Mode always hangs while/after loading "AGPCPQ.SYS".  A number of other forums across the interweb report similar problems.  Even after a fresh format and new install, the problem persisted.  The computer was able to take an Install from a different Windows XP Pro install CD, and make it all the way to the desktop, graphics and all, so I had some hope.

I started with a new LiveCD, to see if any of the laptop's functions would work.  To my satisfacton, the LiveCD booted, and I was able to cruise around GNOME successfully.

So, let's check the HDD to see if there are any problems there (bad sectors, etc)

Hard drive info:
Hitachi Travelstar
MODEL: HTS548060M9AT00
60GB 5400 RPM

```

>badblocks -n -v -s -c 10240

Testing with random pattern: done
Pass completed. 0 bad blocks found.

```
Described in more detail here:
**Checking disks for errors using the badblocks command**
credit: *specialj*
[http://ubuntumagnet.com/2008/01/checking-disks-errors-using-badblocks-command](http://ubuntumagnet.com/2008/01/checking-disks-errors-using-badblocks-command)

Well, the HDD appears to be alright.  How about the memory?  I used MEMTEST86 v3.4.  All test Passed, everything was just fine.  Again, very encouraging.

Alright, let's get our Linux on.  Using the Install/LiveCD, I went right ahead.  Partitions were created as follows (shown as "Code" simply for clarity)
```
Partition(s):
/dev/sda1   /       ext3     4096 MB
/dev/sda2  swap              2048 MB
/dev/sda3  /home    ext3    16348 MB
```

Now things are on the right track.  Wireless works no problem, FF runs and browses, once I installed the plugins I could watch YouTube vids easily.  Sound works fine.  Things are looking good.

But, several **symptoms** showed up, related to graphics:

[LIST=1]
[*]Switching screen modes i.e. virtual terminals leads to hangs/crashes
[*]None of the LCD bezel buttons work, so no screen rotation, and no On-Screen Keyboard
[*]Manual screen rotation (System>Preferences>Screen Resolution) fails/hangs/crashes
[*]Displaying a simple .wmv video clip with Totem causes hangs/crashes
[*]ON-Screen Display (OSD) for laptop "Brightness", "Sound", "Status" etc. are garbled or no-show (minor importance, but indicative of problems)
[/LIST]

---

### Post by ScottHW on 2008-11-16
The Gateway M275 Tablet has some nice specs:

[INDENT]Hardware specs
[http://eit.tamu.edu/CostShareArchive/spring05/M275.html](http://eit.tamu.edu/CostShareArchive/spring05/M275.html)

Review:
Low cost Tablet PC convertible with big screen
(by Conrad H. Blickenstorfer)
[http://www.ruggedpcreview.com/3_slates_gateway_m275.html](http://www.ruggedpcreview.com/3_slates_gateway_m275.html)

Here's a good description of the tablet
[http://www.dinarius.com/commentable/article/gateway-tablets-m275-and-m285](http://www.dinarius.com/commentable/article/gateway-tablets-m275-and-m285)[/INDENT]

The factory RAM that was in the laptop was marked as follows:
[INDENT][FONT="Courier New"]hynix                              china 53
PC2700S-25330                    0507
256MB DDR 333MHz CL2.5
HYMD232M646D6-J AA

(200 Pin SoDIMM)[/FONT][/INDENT]

BUT, I figured with only 2x256MB RAM stock, and a max of 2GB, I could do a little upgrading.
I found a good deal, and got down in it twice

[INDENT]**Crucial 1GB PC2700 333Mhz 200-pin DDR SODIMM Laptop Memory $5 AR + s/h**
[http://forums.slickdeals.net/showthread.php?sduid=34717&t=1001949](http://forums.slickdeals.net/showthread.php?sduid=34717&t=1001949)[/INDENT]

Seems to be running great, and Ubuntu recognizes the memory no problem.  I've only got one of them installed so far, made much simpler with the instructions linked from the *dinarius.com* link above
(credit: Bryan A)
[INDENT][http://support.gateway.com/s/Manuals/Mobile/8509557.pdf](http://support.gateway.com/s/Manuals/Mobile/8509557.pdf)[/INDENT]

---

### Post by ScottHW on 2008-11-16
In an attempt to further diagnose the laptop, I figured it might not be a bad idea to see how it responds to WinXP Pro.  If there genuinely are hardware issues, then WinXP would show problems as well, and I would know it's not just Linux driver issues.

Along the way, I made several mistakes.  First, I tried to just boot from WinXP Install CD.  But when I got into the Setup, and tried to Partition/Format for installation, I received the following:
```

Setup cannot create a new partition in the space you selected because
the maximum number of partitions already exists on the disk.
```

Alright; a very fast internet search will remind everyone that a HDD can only accept 4 partitions.  With 3 reserved for *root*, *swap*, and */home*, that only leaves one left.  But WinXP only needs one.  Hmmm....

I assumed perhaps the Gateway Recovery Partition as still hiding somewhere, even though *sudo fdisk -l* in hadn't shown anything else, and neither did *gparted*.

My solution; I used *sudo gparted* to create a new partition in the remaining 36GB of space, formatted as FAT32 (since Linux doesn't yet natively support NTFS writing).  At this point, I figured it wouldn't hurt to have a back-up copy of the MBR, just in case.
```

dd if=/dev/hda of=mbr.save bs=512 count=1

```
[INDENT]source: sidebar of
[http://www.linux.com/feature/57748](http://www.linux.com/feature/57748)
CLI Magic: Salvage lost partitions with gpart
By Mayank Sharma on October 23, 2006 (8:00:00 AM)[/INDENT]

I have used *gpart* in the past, and has success with it.  I tried to read the partitions on the drive, and it appeared to have gone correctly, so I wrote the new partition table.  That was a mistake; now the laptop wouldn't boot :(

Great, I totally fscked that up.  Alright, I went back to the Ubuntu LiveCD, and it still worked fine.  One thing I noticed; now *fdisk -l* gives the warning similar to "partition does not start at end of cylinder".  OK, so *gpart* didn't quite work in this case.  Good thing I had the backup MBR; just turn around the above diskdump (dd) command to restore from mbr.save

Things still weren't quite right, warnings about "no media" during booting.  So I just went ahead and burned a new copy of the Super Grub Disc v0.9766.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
The default options set me back on the right track.

When I ran the WinXP Install CD again, at the Partition screen, I was given the choice to Delete/Reformat the 36GB partition.  Windows XP Pro went in just fine.  Possibly the Gateway Recovery CD containing WinXP Tablet has errors, or there may truly be something wrong with the graphics hardware.

I made a quick modification to /etc/boot/grub/menu.lst to add the WindowsXP boot option, sticking this bit after the Ubuntu-installed MEMTEST86+
```

title		Windows XP
root		(hd0,3)
savedefault
makeactive
chainloader	+1

```

The HDD now has 4 partitions.  I'd have liked to have a FAT32 that I could have used as a "shared" partition that both WinXP and Linux could write, but that's a different issue.

---

### Post by ScottHW on 2008-11-16
From the symptoms listed above, I've thought that I may have graphics driver and/or hardware problems.

A good Specifications page about the M275 will list:
Video: Integrated Intel® Extreme Graphics 2

And more specifically:
Intel integrated Graphics 855GM

This can be confirmed using the command to list PCI hardware connections (use switches for more details)
```

lspci
lspci -vvnn

```
I've attached the results of both from my machine for reference.

Alternatively, a lot can be learned using the package *gnome-device-manager*, currently v0.2.1
credit: davidmaxwaterman
[http://ubuntuforums.org/archive/index.php/t-26800.html](http://ubuntuforums.org/archive/index.php/t-26800.html)

Also, the package *sysinfo* (0.7-0ubuntu3) can tell quite a few things about your hardware.

Either of these will report something similar to
[INDENT]82852/855GM Integrated Graphics Device[/INDENT]
Integrated graphics are fine, but it doesn't leave many options if the hardware itself is actually damaged.

"Intel", they've been around a while, maybe you've heard of them.  So, drivers should be pretty well developed and easy to come by.  Well, sort of.

Recently, 915resolution would have been a necessity for rotating a tablet
[indent][http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)
**915Resolution: Intel Video BIOS Hack**
Steve Tomljenovic [stomljen at yahoo dot com]
Last modified April 26, 2007 
[/indent]


Here's the homepage for Intel Linux graphics
[http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)

[indent] **laptop hangs when switching video mode**
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101)

**[855GM] system hang during suspend/resume**
[https://bugs.freedesktop.org/show_bug.cgi?id=11432](https://bugs.freedesktop.org/show_bug.cgi?id=11432)

**System freeze after pressing ctrl-alt-bs.**
[https://bugs.freedesktop.org/show_bug.cgi?id=10809](https://bugs.freedesktop.org/show_bug.cgi?id=10809)

**xserver crashes when rotating display and compiz enabled**
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/294309](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/294309)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101)
I tried the   Option "ForceEnablePipeA" "true"

[/indent]


X/Bugs/ScreenModeChange
Bugs with screen mode change (startup/shutdown, hibernate, suspend, screensaver, power save, or tty switch)
[https://wiki.ubuntu.com/X/Bugs/ScreenModeChange](https://wiki.ubuntu.com/X/Bugs/ScreenModeChange)


Installed ***xresprobe***, in order to provide ***ddcprobe*** output


Thread asking for specific help
[http://ubuntuforums.org/showthread.php?p=6218154](http://ubuntuforums.org/showthread.php?p=6218154)

Some other forums about the M275 refer to upgrading the BIOS.  I currently have the most recent version ***48.04.01***

---

### Post by ScottHW on 2008-11-16
Don't be misled, some sites/forums incorrectly report that the M275 uses a FinePoint digitizer.  That's incorrect; some tablets do, but the M275 is NOT one of them.  The M285 *does* use FinePoint, find more info [here]("http://ubuntuforums.org/showthread.php?t=429701")

If you happen to be unable to get a Gateway Recovery CD, the Wacom drivers (for Windows) are inconvienently NOT on the Gateway site.  Find them here
[INDENT][http://www.wacom.com/tabletpc/driver.cfm](http://www.wacom.com/tabletpc/driver.cfm)[/INDENT]


A very useful thread:
[indent]**Wacom tablets in Ubuntu guide/howto** - Loïc2
[http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)[/indent]

---

### Post by ScottHW on 2008-11-17
The most major problem I'm still having, after sorting out how to do rotations.

While I suppose I can just use Terminal for most of the simple Linux commands I might like to be issuing, it's quite bothersome that fundamental aspects of Linux aren't working on my system.

Launchpad Bug #127101: laptop hangs when switching video mode
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/127101)

Bugzilla &#8211; Bug 10809  System freeze after pressing ctrl-alt-bs.
[https://bugs.freedesktop.org/show_bug.cgi?id=10809](https://bugs.freedesktop.org/show_bug.cgi?id=10809)

/var/log/bootchart/


As stated above, this is basically worked out.
Only thing, occasionally I still get "Failed to Suspend" upon waking, accompanied with three or four loud beeps.
How do I go about diagnosing that?
I know there's a pretty significant recording in ***dmesg*** when I do a suspend, although I can't quite understand it all yet...


Occurs about 1/3 of the time when I turn the computer back on from Standby, accompanied by 5-6 obnoxious beeps.
[indent]Sleep Problem
Your computer failed to Suspend...[/indent]

**System beeps on return from suspend**
[http://ubuntuforums.org/showthread.php?t=782995](http://ubuntuforums.org/showthread.php?t=782995)
The suggestions here are mostly just how to stop the SOUND, not diagnose the problem...

**Acer Aspire 5100 Suspend Problem on Ubuntu 8.04**
[http://ubuntuforums.org/showthread.php?t=756754](http://ubuntuforums.org/showthread.php?t=756754)
Some useful info (and some webcam nonsense, too)..

**Sleep Problem**
[http://ubuntuforums.org/showthread.php?t=774384](http://ubuntuforums.org/showthread.php?t=774384)

**Suspend/Hibernate in Hardy solved (for me)**
[http://ubuntuforums.org/showthread.php?t=811163](http://ubuntuforums.org/showthread.php?t=811163)
Not actually Solved, but he does suggest how to find the gnome-power-manager...

** Troubleshooting Sleep Problem Message**
[http://ubuntuforums.org/showthread.php?t=828136](http://ubuntuforums.org/showthread.php?t=828136)
Same problem, no suggestions...

** Question  M1530: After successful hibernation, get "your computer failed to hibernate" message**
[http://ubuntuforums.org/showthread.php?t=823081](http://ubuntuforums.org/showthread.php?t=823081)
Gees, this problem is ALL OVER the forums, widely reported, mostly unanswered...

**[SOLVED] suspend and hibernate questions**
[http://ubuntuforums.org/showthread.php?t=811890](http://ubuntuforums.org/showthread.php?t=811890)
OK, here we go; Post #14 at least tells how to log the problems...

As I try to follow this problem across the forums, I realize that the vB implementation won't let you search for "*some string*".  So, one work-around is a google site: serach, (pretty common trick, suggested here: [http://ubuntuforums.org/showthread.php?t=822460](http://ubuntuforums.org/showthread.php?t=822460))

Another question:
** Suspending and Hibernation in hardy -- failed  **
[http://ubuntuforums.org/showthread.php?t=807245](http://ubuntuforums.org/showthread.php?t=807245)
This one linked to the Launchpad bug

Here is the bug on Launchpad (links to similar bug 195095, too)
**{Hardy} Message: "Suspend Problem. Your computer failed to suspend"**
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/199088](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/199088)
TONS of reported incidences, with no answer or even suggestions.  They do tell you how to disable the sound...

Get rid of the beeping by unchecking the box
System->Preferences->Power Management->General
[_] Use sound to notify in event of error

A number of users report that the failure occurs when Suspending for a long time, and not for short Suspend periods...

The very last post says that it stopped happening for one user when she upgraded to Intrepid

---

### Post by ScottHW on 2008-11-17
From some hints on other forums, I've tried to use
```

xev
showkey

```
But I don't get any response from any of the four keys with either of those.

A couple of times, when I had the tablet rotated over 180 deg, the Brightness button actually functioned....

---

### Post by ScottHW on 2008-11-17
Status, Brightness, Volume

During booting, the OSD works fine, but starts to not work right at "Loading hardware drivers..." (I have disabled quiet in GRUB)

I don't quite understand it yet, but apparently after coming back from Suspend, the OSD behaves much better, mostly working

---

### Post by ScottHW on 2008-11-17
XVkbd
[INDENT]on-screen keyboard[/INDENT]

OnBoard
[indent]built in to Ubuntu, works pretty well.
System>Preferences>Universal Access
Maintains "focus" better than XVkbd
(may need to be turned on in System>Preferences>Main Menu>)
haven't yet figured out how to auto-tile windows when on-screen kbd is called up..., or even do it manually

OR how to use on-screen kbd when prompted for Admin password...[/indent]

Xournal
[INDENT]Note-taking, doodling[/INDENT]

**Wacom tablets in Ubuntu guide/howto**
[http://ubuntuforums.org/showthread.php?t=967147](http://ubuntuforums.org/showthread.php?t=967147)

... which links to
** Linux on the Lenovo ThinkPad X60 Tablet**
Last updated: 2008.09.26
[http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/)
Created to be X60-specific, but still has tons of good tips about screen rotation....

Cell Writer
[indent]So, it looks like it works, but could be improved.  For one thing, I would like the recognition to just take place over any window.  Or at least have window docking make other windows  get out of the way. And there are obvious recognition issues/problems with expected things like t and +, c and <, etc.

I guess what I really want is something like No-Cell Writer[/indent]

---

### Post by ScottHW on 2008-11-17
Here's a forum discussing an issue quite similar to mine:
[indent]**Compiz, xournal, gdm and segfault** - s1300045
[http://ubuntuforums.org/showthread.php?t=792035](http://ubuntuforums.org/showthread.php?t=792035)****[/indent]

My crashes have frequently happened while zooming.

I've noticed from System Monitor that both **Xournal** and **gdm** jump around to ~40% CPU usage each, and no amount of waiting has yet let the issue be resolved.


[http://sourceforge.net/forum/forum.php?forum_id=554376](http://sourceforge.net/forum/forum.php?forum_id=554376)

[http://sourceforge.net/forum/forum.php?thread_id=2031444&forum_id=554376](http://sourceforge.net/forum/forum.php?thread_id=2031444&forum_id=554376)

---

### Post by ScottHW on 2008-11-17
reserved for updates

To restart wireless
```

sudo ifconfig eth1 up

```

---

### Post by ScottHW on 2008-11-17
A first trial recording with Applications>Sound & Video>Sound Recorded didn't work.  A right-click and >Edit Menus> to show "Recording Level Monitor" showed me that indeed, there appeared to be no signal on the Mic.

The solution was pretty easy, even though I missed it on my first couple tries.  Using the command
```

alsamixer

```
I just needed to make sure that the *Mic* wasn't muted (*MM*) and that *Mic Sele(ct)* was on *Mic1*.
I suppose it makes sense that the Mic was muted and that Mic Boost was Off by default, but how/why Mic Select was on Mic2 I can't exactly say.

Double-clicking on the Master volume control brings up a GUI for the same settings.  It also shows that the sound device is
[indent]Intel 82801DB-ICH4[/indent]


UPDATE:
AND, I spoke too soon.  I had marked this as solved, but it's not working now..... I've double-checked all the things I listed above...

---

### Post by ScottHW on 2008-11-17
I've read commands to turn off Bluetooth
<links>
Can I actually easily remove Bluetooth (or similar unnecessaries) from the **boot process**, and still get them back with easily (i.e. short script) if/when I need them?

That could save both power, and boot time...
[http://ubuntuforums.org/showthread.php?t=982855&highlight=boot+bluetooth](http://ubuntuforums.org/showthread.php?t=982855&highlight=boot+bluetooth)

Several useful commands for turning Bluetooth off/on, and even a nice short script for the same, can be found here:
**Turn off bluetooth radio**
[http://ubuntuforums.org/showthread.php?t=120403](http://ubuntuforums.org/showthread.php?t=120403)

I wonder what else I could shut off.
So does this guy
[http://ubuntuforums.org/showthread.php?t=985687](http://ubuntuforums.org/showthread.php?t=985687)

---

### Post by ScottHW on 2008-11-18
reserved for updates

---

### Post by MGaddict2000 on 2008-11-22
Thanks a lot for all this info. I got my hands on one of these laptops. I only use it for internet and watching movies. I figured it would be a great system to install Linux on and learn the system. This is extreemly usefull that you had the same system and put up this blog. I would have spent weeks finding all this info especially since I've never really gotten into the linux instilations before. I use Unix at work but we have technitions whenever something doens't work right so I never get to mess with the OS. Thanks again.

---

### Post by ScottHW on 2008-11-23
> **MGaddict2000 said:**
> Thanks a lot for all this info.

I'm glad someone has benefited from what I've put together here.  I was a little worried that maybe some of those on this forum wouldn't like me almost using a thread as a Blog, but this does seem like a really good central location for what I've learned.

Glad to help

---

### Post by ScottHW on 2008-12-02
If I have the tablet folded over, and can't access the keyboard, how do I enter the password...?

None of the on-screen keyboard Apps I've checked so far seem to be able to run during that prompt...

---

### Post by ScottHW on 2008-12-05
Option:   "ForceEnablePipeA"  TRUE

This "quirk" / hack seems to solve several of the problems I was experiencing, but I don't understand it... at all.

Is there a way for for me to do this "manually", once X has started?

What exactly does this do?

How can I know the current status of PipeA?

How is this related to LCD/CRT output?
How can I get the current status of LCD/CRT?

---

### Post by ScottHW on 2008-12-06
I added the packages (to build [WifiScanner]("http://wifiscanner.sourceforge.net/") 1.0.2a, and other future installs)

  build-essentials
  autoconf  2.61-4
  autoconf  2.13-59  
  automake  1.9.6+
  libtool   1.5.26
  libglib2.0-dev 2.16.6-

And I got a little bit of space back on / by searching Synaptic for "linux-image" and removing 2.6.24-19 (I am currently using -21)

So, I scrapped WifiScanner and decided to install Kismet (2007-10-R1-) to learn more about wireless networking

---

### Post by PBrn46 on 2008-12-16
Hi Scott,

I've had problems on my M275 from 8.04 all the way back. There were shutdown issues (won't fully shut down until I press power), startup issues (takes 1 full day to start up), and many more.

I have hit-and-miss chances when it comes to installing Ubuntu (I've tried installing it into this computer for a long time now). At the end, Ubuntu 8.10 (Intrepid Ibex) worked out the best. There were no startup or shutdown issues. The only problem I am facing is the use of video playback while I have Compiz Fusion (Advanced Desktop Effects) running. The video card is fairly old, and didn't work so well in Windows anyways, so every time I want to playback video I just turn off my desktop effects.

For your Windows problems, the laptop actually ships with Windows XP Tablet PC Edition (which I suspect is XP Pro with some extra tablet features). I'm not sure whether that would be the cause of all your tablet issues. I have the original driver CD's that's shipped with my (two) M275's, both for the Tablet PC Edition.

-Bo

---

### Post by MGaddict2000 on 2008-12-23
Are you saying you got 8.10 installed on an M275? From all the threads I've looked at it seems people couldn't get the CD to even boot up, myself included. Did you have to change a setting in the startup?

---

### Post by PBrn46 on 2008-12-23
I didn't have to change any settings for the 8.10 CD to boot. The bios settings were very simple in the machine also, so I don't remember changing anything there. Although, in my experience of installing Ubuntu on any machine, there were some times where I have to change some bios settings to match.

I had troubles partitioning with earlier versions though, it was a little buggy. I usually ended up erasing the entire thing and only having Ubuntu installed.

---

### Post by newfangled on 2009-01-03
Just want to say thanks very much for this thread.  I picked up one of these laptops, and this has been very helpful.

I actually was able to install Intrepid without any problems.  I don't have the newest bios, if that makes a difference.  I think I've got 48.03.01 (but don't feel like restarting to check), just went with the defaults, and I have no way to upgrade it regardless.

This is my first attempt to put ubuntu on a laptop, so I've got a few questions:

For screen rotation using the intel driver, what needs to be done to also rotate the touchpad/stylus?  Is the guide that was posted earlier for the Thinkpad X61 the best place for that?

Has anyone had success with the bezel buttons?  My brightness button does work within ubuntu.  I'm not sure what it's supposed to do, but in ubuntu it cycles through three settings - high, high and low?  None of the others seem to register at all though.  The quicklaunch buttons do register, but that's not much help when it's folded over.

And has anyone tweaked their harddrive powersave/access settings?  I find that the drive clicks on fairly frequently, even when I'm not doing anything.  There's a tonne of information out there about laptop harddrive settings, and I'm currently wading through it.  Just wondering if anyone else has settings they like.

When I shut the laptop down it seems to work fine.  There are no errors, only the battery light is on, it will boot back up with no problems, and everything looks good.  There's still a quiet hum though, which might be from the harddrive?  If I unplug the AC adapter it goes away.  I've never seen a laptop do that before, so is that normal, or is ubuntu confused and this is part of the larger shutdown problems?  I've had ubuntu on desktops before and have had no end of problems with shutdown/hibernate/suspend.  Here, it looks like everything works fine...except for the hum.

I also find that the laptop case gets pretty warm.  My fan is almost never on, and from some playing around Gkrellm it looks like the fan only kicks in when the cpu temp hits 60C.  So presumably it knows what it's doing, and it doesn't look like it's possible to control the M275's fan speed through lm-sensors.  Just wondering if anyone else has done any investigations?

Thanks again.

---

### Post by newfangled on 2009-01-03
Just in response to my own thread, I did get the rotation of the screen and tablet working by following some of the other threads about the thinkpads.  It went so much smoother than I expected.

I also installed [easystroke]("http://easystroke.wiki.sourceforge.net/") for mousegestures when in tablet mode.  I preferred it to brightside or gestikk.

Have played around with laptops-tools, although not enough to really know if it's had an effect on harddrive access.

Anyone else having the heating problem though?  I really am surprised how warm the case gets.  And I'd love to have the ability to manually ramp up the fan.

---

### Post by PBrn46 on 2009-01-03
Don't worry about the heating problems as it isn't a problem. The tablet was originally designed to be that hot, since it was designed close to when the Centrino processors were first released. Under Windows and Linux it is the same. There are no software and bios controls for the system fan, and it is indeed controlled by the hardware only.

It wouldn't harm the processor or most other parts (I believe the processor is rated at over boiling temperatures). The only downside is that the heat will degrade the battery overtime. I have two batteries, one is running at 48% efficiency the other at 55%.

Cooling pads might help. =D

-Bo

---

### Post by newfangled on 2009-01-03
Thanks PBrn46.  That's good to know.

What about the not-quite-shutdown?  Is that normal too?  Other notebooks I've had are dead silent when they're shutdown.  This one's definitely doing something, though.  Is that normal?

(oh, and ubuntu thinks I have 19min of battery, although I haven't done a calibration yet.  Battery is not a huge issue since the machine is mostly going to be an ebook reader, and for websurfing while on the couch)

---

### Post by PBrn46 on 2009-01-03
If the AC adapter isn't plugged in, it shouldn't make any noise at all after shutdown. In my experience with earlier versions of Ubuntu I would not be able to shut down fully (the screen would go black, but I have to force the shut down -- power light was still on though). I haven't had any power issues in 8.10 though.

---

### Post by newfangled on 2009-01-16
I don't know if anyone else has this problem (or which ubuntu versions it affects) but I found that the brightness settings weren't very useful.  I had either low (which was too low for most circumstances) or high (which is brighter than needed, and tends to make the bezel warm).

After some searching I found this:
[http://www.ubuntu1501.com/2007/12/backlight-brightness-fix.html](http://www.ubuntu1501.com/2007/12/backlight-brightness-fix.html)

There are few suggestions in there, but the one I went with was posted by d00d:

> 1. backup /etc/acpi/video_brightnessup.sh
and /etc/acpi/video_brightnessdown.sh

2. sudo gedit the first one

3. replace everything in it with...

And then there's a script.

Under Intrepid this lets the backlight be set from 0 up to 100.  The brightness applet still doesn't work, but the above link also has a replacement that I haven't tried.

---

### Post by newfangled on 2009-01-19
^ after thinking a little bit more about that brightness script above, I'm pretty sure that it doesn't actually do anything.  Maybe I'd only tried Fn+F8, and not actually FN+the arrow keys?  Whoops.  So it can be ignored.

I did write up a script to control the fan speeds though.  Not sure if this will be useful for anyone else, but battery and noise aren't huge concerns for me, and sometimes I'd prefer if the laptop was cool to the touch.  This goes from no fan, to Fan0, to Fan0&1, back to no fan:

> #!/bin/sh

fan0status=$(grep "status:" /proc/acpi/fan/FAN0/state |awk '{print $2}')
fan1status=$(grep "status:" /proc/acpi/fan/FAN1/state |awk '{print $2}')

case "$fan0status" in

	off)
	echo -n 0 > /proc/acpi/fan/FAN0/state
	;;

	on)
		case "$fan1status" in

		on)
		echo -n 3 > /proc/acpi/fan/FAN0/state
		echo -n 3 > /proc/acpi/fan/FAN1/state
		;;

		off)
		echo -n 0 > /proc/acpi/fan/FAN0/state
		echo -n 0 > /proc/acpi/fan/FAN1/state
		;;
	esac
	;;
esac

To make this work without entering a password you do have to edit the sudoers file.  My laptop is pretty secure and unimportant, but ymmv.  There are instruction here: [http://ubuntuforums.org/showthread.php?t=140696](http://ubuntuforums.org/showthread.php?t=140696)

---

### Post by ScottHW on 2009-01-29
Wow, I feel kinda bad not keeping up on my own thread; especially now that there are a couple other posting here!

Here are two new things I just found out:

I had previously mentioned that I was having microphone troubles.  I played around with alsamixer endlessly.  And just today realized that the problem is actually hardware.

When I rotate the screen around about half way, I could hear something going on.  On a whim, I blew on the microphone, and sure enough since I had it on Mic playback, I heard wind noises.

So apparently my Mic problems are largely just the wires that are running down thru the screen-rotating hinge.  Troublesome.

Here's the real kicker; while messing around with alsamixer, I seem to have somehow set my Fn+PgUp / Fn+PgDn  volume controls to control the Mic levels....?!?!  And now, as I don't know how that happened, I don't know how to set it back to Master.

It's been a while since I've updated this thread, mostly because the first posts got me to a functioning Ubuntu status.  I'll go back and clean some stuff up.  Happy Heron, everyone!

---

### Post by newfangled on 2009-02-01
Scott, your first couple of posts got me a functioning ubuntu, so thanks again.

I did just discover a new problem though - I can't read burnt DVD disks.  Commercial disks work fine, and I know that the drive can read burnt disks because that's how I installed ubuntu.  But within ubuntu if I try to open a homemade disk I get "unable to mount location - no media in the drive"

It doesn't seem to work with any of my data DVD: +/-/DL, or whatever.

From searching around a bit, I think it's related to the Vista's UDF formatting, but I'm not sure.

Anyone else have this problem, or know of a fix?

edited to add: actually, looking at them again, most of them are in ISO format instead of UDF, and they were burned under either Vista or XP.  So I have no idea what the issue is.  The drive chugs a bit when the disk is first inserted, but eventually gives up.

---

### Post by ScottHW on 2009-03-27
New attempts

I've discovered Audacity.  It's excellent.  I have it on my WinXP desktop, and now on the M275, too.

I am also increasing my Skype usage of late.

It goes without saying that I would try to record Skype conversations with Audacity.
Nothing doing.

I tried PulseAudio, as described here,
[http://sugree.com/node/286](http://sugree.com/node/286)
But even just launching Audacity and trying to record and playback caused Audacity to crash.

---

### Post by ScottHW on 2009-04-09
Now I'm getting Skype working.

I have Skype for Debian 2.0.0.72

Sadly, Skype for Linux isn't OSS, and is quite far behind in development.  Thus, it doesn't allow common Skype features like SMS.

BUT.....
***megamania*** was looking for the same in this thread
[INDENT]**A way to send sms with skype for linux!**
[http://ubuntuforums.org/showthread.php?t=683129](http://ubuntuforums.org/showthread.php?t=683129)[/INDENT]

Short version:
[LIST=1]
[*]You need python-gtk2
[*]Get Skype4Py 1.0.31.0 from: [https://developer.skype.com/wiki/Skype4Py](https://developer.skype.com/wiki/Skype4Py)
[*]Get Skysentials 1.0.1 from: [http://www.kolmann.at/philipp/linux/skysentials/](http://www.kolmann.at/philipp/linux/skysentials/)
[/LIST]

I just put extracted skysentials into a folder, and made a Launcher for skysentials.py on my top panel.

Also, I spent 90 seconds and put together the attached icon, with the clever name ***skypython*** (a quick GSearch suggests it's actually an original name, w00t!)
I'll whip a better version in a few days.

---

### Post by ScottHW on 2009-05-19
Tonight I decided to check out some webcasting clients, starting with Podracer.  But Synaptic Package Manager only made it part way thru the install.  Turns out my root partition was all filled up.

Here's a helpful command I learned:
```
 df -h 
```
From the manpage
[indent]NAME
df - report filesystem disk space usage
SYNOPSIS
df [OPTION]... [FILE]...
..
-h, --human-readable
print sizes in human readable format (e.g., 1K 234M 2G)
[/indent]
(if you want to spruce up your df a little bit, check out discus)

Apparently the 4GB I thought would be enough for root, wasn't.

There are dozens of references everywhere about this, so I'll just summarize.  To resize partitions, a great way to go is ***gparded***.  But you can't do anything to active partitions.  So, simply use a Live CD (I just grabbed my Ubuntu 8.04 install CD), shutdown and boot to a Live Session.

The only other thing I had to do was ***Swapoff*** on my swap partition, so that I could modify it's position.  There is a key icon next to the swap partition (indicating it's "locked" I guess) so just right-click on the /swap partition and choose the Swapoff option.

I just decreased the size of /home (/dev/sda3), and shifted it along with /swap (/dev/sda2) to the right.  Then used the extra 4GB to expand the size of root / (/dev/sda1).  Worked like a charm.

Last thing, I had to finish up the package installs that got interrupted by the lack of space
```
sudo dpkg --configure -a
```

---

### Post by ScottHW on 2009-05-19
Here's another one that is referenced al lover the interblags, but I found it useful.

To set a keyboard shortcut / hotkey to open a new Terminal console:

[INDENT]System>Preferences>Keyboard Shortcuts[/INDENT]

Scroll down, second section is Desktop, last option is 
[INDENT]
[INDENT]Run a terminal[/INDENT][/INDENT]

Click on the right side, under the Shortcut column, which likely says "Disabled".  Press the keystroke combo you want to use.  I choose Ctrl+Alt+T (for ***T***erminal)

Actually, this may be, or have been, useful for my Volume Keys problem.  Can't remember if I posted about it earlier, but somehow I mapped my Fn+PgUp to control the volume of something else in the mixer, NOT the Playback>Master volume.  But it is fixed now, and I don't remember changing anything... could have been me messing around with the ALSA mixer so much...

---

### Post by ScottHW on 2009-05-19
So as mentioned above I'm looking into some podcasting.  As referred from the Juice page, I thought I'd try IcePodder.

I've had quite some trouble getting it going.  First, there are a bunch of other packages necessary, python-this and python-that.  And not all of them were in the standard Ubuntu repositories.  But I thought I had them all in.

Here's the problem that I came across
```

-@-:/usr/share/icepodder$ ./CastPodder.sh
CastPodderGui.py:48: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from   wxPython.wx import *
Traceback (most recent call last):
  File "CastPodderGui.py", line 48, in <module>
    from   wxPython.wx import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/__init__.py", line 15, in <module>
    import _wx
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_wx.py", line 8, in <module>
    from _misc import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/_misc.py", line 456, in <module>
    wxDateTime_GetNumberOfDaysinYear = wx._misc.DateTime_GetNumberOfDaysinYear
AttributeError: 'module' object has no attribute 'DateTime_GetNumberOfDaysinYear'

```
Yah.  No idea what was going on there.  But some Googling for a couple of those strings led me to this helpful page
[http://ubuntuforums.org/archive/index.php/t-607186.html](http://ubuntuforums.org/archive/index.php/t-607186.html)
Basically, the problem is that I had chosen the newest version, python-wxgtk2.8.  And that's the problem.  Apparently there are some conflicts between IcePodder and wxgtk2.8.  So I downgraded to python-wxgtk2.6
```

sudo apt-get purge python-wxgtk2.8
sudo apt-get install python-wxgtk2.6

```
Note: you may or may not have other things that depend on wxgtk2.8.  I know that one of the forums I read mentioned that possibly Audacity needs 2.8.

Anyway, now it seems to work fine.

Well, aside from this
```

-@-:/usr/share/icepodder$ ./CastPodder.sh
xmms couldn't be imported
Beep-Media-Player couldn't be imported

```

But at least IcePodder GUI starts up.  So I'm not too worried about that player stuff now.

---

### Post by ScottHW on 2009-05-29
This is a follow-up to Post #35 **Gparted**.

Basically, the repartitioning did work.

BUT... I have started to notice a slight change in my boot behavior.  In my /boot/grub/menu.lst I have commented out **#quiet splash** at the end of my kernel line, and the **#quiet** on the last line (of that segment) as well.

I used to get[LIST=1]
[*]BIOS splash
[*]GRUB 1 second delay 
[*]Terminal-looking timestamps and commands (~10 seconds)
[*]Ubuntu logo splash, commands underneath in Orange
[*]Gnome login screen
[/LIST]
But lately, after the Ubuntu splash, it's been going back to Terminal-looking commands, starting with "kjournald starting".
Also, I noticed there has been significant delay at "Waiting for resume device..."
I started trying to think how I could back-track my actions and see what I had done to precipitate the change.  Since I previously installed bootchart, I looked back to see if I could spot a change in the logs (/var/log/bootchart/).  Sure enough, about 8 days ago, I started seeing around a 10 second delay for something listed as "resume".  I also recognized that the 10 seconds on my wristwatch (figuratively, I don't wear a watch) did NOT correspond to the timestamp times during the boot sequence, so the "Waiting..." delay was actually hanging things up pretty seriously.
Fortunately, I didn't have to try very much Ubuntu-forensics, because I don't know what else I would have tried.  I realized from bootchart and my own (highly fragmented) memory that this must have been when I repartitioned.
Here's the first useful thread I found
[INDENT]**Boot time-'waiting for resume device'**
[http://ubuntuforums.org/showthread.php?t=1056474](http://ubuntuforums.org/showthread.php?t=1056474)[/INDENT]
It does have basically the "answer"... but I didn't quite get there from that alone.  Since I had just been messing with partitions, this seemed a likely possibility.

Short version: Check that UUID for swap matches in:
```
sudo blkid                 #gives the UUID of each device, this is the "correct" one
sudo gedit /etc/fstab          # these may be incorrect
sudo gedit /boot/grub/menu.lst    # may be wrong as well
```

So, I backed up fstab, and changed the UUID of /dev/sda2/ my swap partition.
My Grub menu.lst didn't have any references to my swap drive, noting to edit there.
Reboot, but that didn't seem to have fixed it.

Here I got a little side-tracked.  Since this was basically a boot delay, I remembered that I had done "something" a while ago to try to speed up my boot.  What was that...?
[INDENT]**TIP: Improve bootup speed by reprofiling bootup**
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)[/INDENT]

I did try to reprofile again.  One note there, since I have already commented out the end of my kernel line in Grub, I had to make sure to add **profile** *before* **#quiet splash** at the end of the line.  Let it run, but that didn't really do anything for me.

I remembered that I had marked "Swapoff" in Gparted when I was repartitioning, and thought maybe that might have inadvertently done something since I hadn't actually read to do that anywhere.  Of course, you *have* to do that to resize/move the swap partition.
From System Monitor>Resources [tab] I confirmed that I did have 1.9GiB of swap. I used Gparted, did "swapoff" on /dev/sda2 and System Monitor confirmed 0.0 GiB swap.
Reboot, nothing.  Swap just came back on by itself.  This was always a long-shot idea anyway.

Now, we do get to the solution.
[INDENT]**[all variants] System hangs on "waiting for resume device" during boot **
[http://ubuntuforums.org/showthread.php?t=888424](http://ubuntuforums.org/showthread.php?t=888424)[/INDENT]
(IMHO, and no offense meant, but I would *disregard* what fabian.r says in Post #4.)

It's a short discussion, but does link to what is apparently a well-known bug.
[INDENT]**Bug #206358 in initramfs-tools (Ubuntu): “Slow boot process on "waiting for resume device**
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/206358)[/INDENT]
I guess this particular thread doesn't make it as obvious, but I know I saw it in other places [citation needed :]  Frequently when Gparted is used to resize or move a swap partition, the UUID isn't recopied correctly into the necessary locations.  Two are listed above, the third is */etc/initramfs-tools/conf.d/resume*

I made a backup of this file, and changed the UUID to match what **blkid** showed.  Last step, to update the "initial RAM filesystem" 
```
update-initramfs -u
```
Rebooted.  Still nothing.

From the ubuntuforums "system hangs" thread above, Theo148 pointed me to the answer on this one. He had a file called resume-old in his ../resume directory somehow, but I had *intentionally* created a back-up file in this directory.  That was a mistake. Moved the .bak, rebooted...

SUCCESS!!!

"Waiting for resume device..." delay is gone, and boot behavior has gone back to matching what is described in the beginning.


Disclaimer:  I hope that no one minds too terribly that I use this thread as something of a blog.  Particularly since I got *very* wordy in this post.  I know forums are supposed to be for discussion, but if I write all of my experiences, and it helps somebody google and land here to help them solve a problem, it's worth it.

---

### Post by ScottHW on 2009-05-29
updates soon

---

### Post by ScottHW on 2009-05-29
fractals, yah!

---

### Post by ScottHW on 2009-05-29
I sometimes watch The Daily Show on Hulu, and have wondered about my bandwidth usage.  Also, I have been messing around with uTorrent on my WinXP desktop, and learning more about ports and firewalls.  AND, as indicated above, I checked out electricsheep, which uses BitTorrent to get the new sheep.
With my first running of electrisheep, it sat there just saying "Downloading first sheep", but nothing happened, for hours.  So I wanted to figure out if anything actually WAS downloading.

So I started trying to find a way to get some real-time network monitoring.
System Monitor does have Network History, which is alright.  Not much detail, and no options.

I looked around, and found a couple interesting options.

For real-time monitoring, **Speedometer** is a pretty good little program.
I used Synaptic and installed 2.4-1.
After RTFM, here's the command I use
```
speedometer -i .25 -rx eth1 -tx eth1
```
Useful for watching.  I can see Hulu buffering my videos, etc.  But, the main drawback is:
[LIST]
[*]Not giving any information about what program(s) are using bandwidth
[/LIST]
Others include:
[LIST]
[*]Non-intuitive non-linear "y-axis" scale, which can't be modified
[*]Faster "interval" catches more accurate information, but with less "depth of history", i.e. no way to change the scale of the "x-axis"
[/LIST]

So, now to figure out what connections are actually being made, **tcptrack** works alright. Installed 1.2.0-1, again with Synaptic
Again, RTFM to figure out the options
```
sudo tcptrack -f -r 600 -i eth1
```
Advantages:
[LIST]
[*]The destination IP is revealed, so you can try to figure out what kind of network traffic it actually is
[*]With the -r switch, you can set how long to wait before removing a closed connection; essentially sets the history length
[*]Some interactive options; Sort, and Pause
[/LIST]
Possible improvements:
[LIST]
[*]No way to interactively clear the display
[/LIST]

And then, of course, I found the tool actually included with Ubuntu by default, **tcpdump**.
Advantages:
[LIST]
[*]Can give TONS of information, including IPs, and lots more
[*]Captures everything
[/LIST]
I run the program with
```
sudo tcpdump -n -vv -i eth1
```

And this was how I finally got what I wanted.  I re-started electricsheep, and watched packets get sent out, caught the destination IP address, and figured out that electricsheep was indeed contacting its server, as well as checking with random other connections (assumed in a swarm of some sort).  So I let it run all night and the next day, and finally I did end up with my initial sheep, and then on to neat flame fractals.

I figured out which server was being contacted with the useful ```
nslookup
```

The last interesting thing was that on System Monitor, I have seen some occasional small blips, but never known what they are.  Well, tcpdump solved that easily.  **Speedometer** had seen this activity, but couldn't tell me anything about it.  And **tcptrack** didn't record any open connection
I didn't have to wait very long to catch the IP *91.189.94.4.123* which a quick Google search revealed to be the Canonical NTP time server, "Keep Synchronized with internet servers". These guys point that out (in addition to wasting space flaming each other, idiots.
[http://fixunix.com/ubuntu/255352-europium-canonical-com-what.html](http://fixunix.com/ubuntu/255352-europium-canonical-com-what.html)

So now I can sit around semi-obsessively watching my network traffic live, and catching every bit </pun> of it.

---

### Post by ScottHW on 2009-05-29
key bindings, history size,

Modify ALL XTerm sessions (to change terminal size)[indent][http://ubuntuforums.org/showthread.php?t=15471](http://ubuntuforums.org/showthread.php?t=15471)
```
sudo gedit /usr/share/vte/termcap/xterm
.
.
change this line....
:co#80:it#8:li#24:\

```
change the values of co   and   li  to be whatever I want, i went with 120x36
[/indent]

---

### Post by ScottHW on 2009-05-29
don't know how/why, but the conflict with GDM seems to be gone

Upgraded to 0.4.2.1

Now the horz. line display glitches seem to be gone too

---

### Post by ScottHW on 2009-05-31
> **newfangled said:**
> I did write up a script to control the fan speeds though.  Not sure if this will be useful for anyone else, but battery and noise aren't huge concerns for me, and sometimes I'd prefer if the laptop was cool to the touch.  This goes from no fan, to Fan0, to Fan0&1, back to no fan:

I put the script in /usr/local/bin, and made a Launcher on my Desktop.  I expect that'll end up in my top panel before too long.

Fortunately, I just threw sudo on the front of the launcher command line, and I only have to enter the password the first time.  Which is nice.

My concern now is will the automatic fan-speed sensing and control overtake this if it needs to be higher?  I hope so; don't want to cook my processor.
I have a sensor applet up on my panel already, telling me CPU temp.  When I watch movies, the fan kicks on ~65degC.  Just want to make sure his won't override that.
I guess I'll have to watch and see.

Thanks, **newfangled**!

UPDATES:
First, when I bang the fan speed up manually, I can keep CPU at 35degC, which is great.  It keeps the right-bottom side of my laptop icy cool on my lap.
BUT, the center of the thing is still pretty hot.  Hmmm.  Well, that's certainly no this scripts' fault.

As for automatic overriding, I cycled thru back to Fan0, and when things headed up to 65degC, it went right to Fan1.  Now I just have to see if Fan1 goes to Fan2 under higher load....

Next, I don't like the terminal window popping up, even for a sec, as I manually switch fan speeds.  I tried changing my Launcher from "Application in Terminal" to just "Application" but then it didn't work any more.  Actually, I had to just go ahead and make a new launcher, because I couldn't find a way to change the Type of a Launcher.

Maybe this script could be updated so that the interface could be something a little cleaner... three graphical options, for the three fan speed choices?  I certainly don't have the skills to do that... yet.  So for now, I'll stick with just cycling manually with the launcher.

Also, the fan is still on the bottom of this thing, and when it's sitting on a bed, or my pants or whatever, fabric can pretty easily cover the inlet.  There seems to be a little side-port next to the Kensington lock port, looks like if I take the keyboard cover off it might just slide up.  I'll look into that and report back.

UPDATE 2:
Used the linked instructions to change **sudoers** no more password every time
Also created a launcher in my top panel, for easier access than my Desktop
I grabbed a free icon from the Interblags, its attached
Thanks again!

---

### Post by ScottHW on 2009-06-02
to be updated...

Status monitoring
Applets
[http://ubuntuforums.org/showthread.php?t=953132](http://ubuntuforums.org/showthread.php?t=953132)

---

### Post by ScottHW on 2009-06-04
Going to try this...

[http://lifehacker.com/317125/set-up-vnc-on-ubuntu-in-four-steps](http://lifehacker.com/317125/set-up-vnc-on-ubuntu-in-four-steps)

---

### Post by ScottHW on 2009-09-10
I need to learn better how to make disc copies

[http://ubuntuforums.org/showthread.php?t=242251](http://ubuntuforums.org/showthread.php?t=242251)

More updates to follow.

I like the terminal **dd** commands.  Need to know how to figure out the device name / path / mount point for my CD rom

---

### Post by MGaddict2000 on 2009-09-10
Having replaced a laptop fan before, It's a severe pain to get to them. Usually the entire laptop has to be dissasembled. There is typicly onl;y one fan on a laptop, and thats the one covering the CPU. RAM, HD, and Battery will all still get pretty warm when in high use. There isn't anything you can do about that besides makes sure the bottom of the laptop has plenty of ventalation. 

That being said... I would love a copy of this script as it currently rests so I can try it out. Thanks.

---

### Post by MGaddict2000 on 2009-09-10
should be...

> mount /dev/dvd /media/cdrom0

/dev/dvd is the device and /media/cdrom0 is the mount point. Ubuntu doesn't require 9660 on the mount definition, but other distros would. That's what I use to manually mount my CDrom on my M275.

Also note...
> umount /media/cdrom0
to unmount the drive.

---

### Post by ScottHW on 2009-09-30
I've recently been having a weird problem;

With Gmail, through Firefox, when I try to attach a file, my Netgear router has been dropping the internet connection, crashing.  Just a 2MB mp3 file. Have to power-cycle the router/model power strip to get back online.

I don't have anything for it, just a report of the symptoms now.

Tonight, after having a file sitting on my desktop for a month waiting to be sent, I finally got fed up.  I started the commands I'd previously written for speedometer, tcptrack, and tcpdump.

Funnily enough, when I tried to attach the file, it did work.

So not much learning here, particularly since I'm not sure I can reliable reproduce the issue, but I thought maybe somebody else might have similar experiences, or at least some thoughts.

---

### Post by ScottHW on 2009-10-10
I upgraded from 8.04.2 to 8.10 (on my way to 9.10 later in the month)

Issues:
 backed up my menu.lst file
 commented out quite splash and quiet again
 disabled Sounds> Login and Logout

After upgrade
 - had to re-enter wireless password
 - Tablet stylus no longer works
 - xorg.conf was heavily commented for "HAL"
  - Update made a back-up, I just manually reverted to that one
  - stylus is working again EDIT: but NOT when I rotate the screen; still trying to figure it out with xrandr
 - Somehow my CPU temp sensor reading doubled it self
  - I removed it from the panel, and now wish I hadn't, cause I don't remember how to get it back up there....
  - OK, right-click Add to Panel... >Hardware Sensors Monitor
  - To get only one readout; right-click on the sensor, Preferences>Sensors tab, and uncheck one of the two sensors.  I kept acpi and unchecked libsensors, because I like the name CPU better than temp1

Still need to reprofile to speed up the boot time

Used Synaptic to remove linux-image-2.6.24-23, saved 126MB
Manually removed lines from menu.lst

---

### Post by ScottHW on 2009-10-11
I tried to update with Ubuntuzilla
[http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way](http://ubuntumanual.org/posts/193/installing-firefox-3-5-in-ubuntu-the-easy-way)

I didn't like it

Used Ubuntuzilla to take it out

But my shortcut got broken
Fixed it with this
[http://ubuntuforums.org/showpost.php?p=5739904&postcount=10](http://ubuntuforums.org/showpost.php?p=5739904&postcount=10)

---

### Post by ScottHW on 2009-10-12
I don't know if these problems existed while I had 8.10, I wasn't careful enough to check before continuing on to 9.04.  At any rate....

Problems I have now:
 - my stylus does not right-click
 - my rotate scripts do not rotate the stylus input (still rotates the display fine)

Side note: After booting, the hardware direct on-screen displays (OSD) related to volume and brightness in the upper left corner used to be scrambled.  By simply doing one Suspend and wake up, they worked fine.  Now they just stay scrambled.

PM from Newfangled:
> 
I also saw you mention that your rotate scripts weren't working properly anymore? I had a problem when I upgraded to 9.04, and to fix it I had to change the device names in the script

This is straight out of my script:

xrandr -o normal
xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer" rotate NONE
xsetwacom set "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" rotate NONE
#xsetwacom set touch rotate NONE
#xsetwacom set eraser rotate NONE

The commented-out lines are what worked in the older versions. The lines above are what I had to change it to for 9.04.

So basically touch becomes "Wacom Serial Tablet PC Pen Tablet/Digitizer"


---

### Post by ScottHW on 2009-10-16
I decided to upgrade my Skype to the newest version.  I had been running 2.0.0.7, just got the package for 2.1.0.47 Beta.  Seems to work at least as good as before.

Thing is, now Skysentials don't seem to work.  Of course, the new Beta seems to be able to do SMS natively, so maybe it's no problem.

Just for reference, I should learn how I would go about downgrading

---

### Post by ScottHW on 2009-11-06
Fan script stopped working.  Not sure why, but I didn't write the original script so I'm having a hard time diagnosing.

I'm looking around for other options for fan control.  Here's another thread
[http://ubuntuforums.org/showthread.php?t=990580](http://ubuntuforums.org/showthread.php?t=990580)

It was actually already present in Jaunty, but I want to get rid of that On-Screen Display / overlay about connecting to a wireless network.  I don't need that crap, I have NetworkManager Applet that already does a fine job of this.
EDIT: Seems that "Notifications" has been discussed in several places, and quite a while ago...
[http://old.nabble.com/can%27t-disable-notification-bubbles-in-nm-applet,-or-configure-at-all-td20494015.html](http://old.nabble.com/can%27t-disable-notification-bubbles-in-nm-applet,-or-configure-at-all-td20494015.html)

The Bug reports suggest that nm-appler 0.7 had an option added to surpress non-critical notifications, but I don't seem to see that in Jaunty.  So, the current work around is...
EDIT: This doesn't seem to be 100%, I still get some notifications when resuming from Standby...
```

gconf-editor
/apps/nm-applet/
disable-connected-notifications [x]    'mark as TRUE
disable-disconnected-notifications [x]   'mark as TRUE

```
Hmmm... I seem to recall that previously there was a Notification for changing screen brightness, but now that one's gone.  The Volume Notification still displays when I use Fn+PgUp / Fn+PgDn to change Volume.

Decided to remove indicator-applet-0.1 from my Panel.  I don't use Evolution/Empathy/Pidgin anyway, so get outta here.

Sound preferences have changed, a lot.  Mostly it looks more detailed and technical, and I like having options for things.

I do NOT like the fact that double-clicking on the Sound icon on the Panel doesn't bring up the Preferences like it used to before Jaunty.
Also, I can't tell, but for the Gateway M275 I previously had to adjust the headphones output volume independent of speaker volume.  We'll have to see what happens with that.

Clicking on the Shutdown menu seems to do a strange highlight around my fanspeed script Launcher...

---

### Post by ScottHW on 2009-11-07
[http://ubuntu.igameilive.com/2009/10/enable-ctrl-alt-backspace-in-ubuntu-910.html](http://ubuntu.igameilive.com/2009/10/enable-ctrl-alt-backspace-in-ubuntu-910.html)
credit: Panji Nushantara

[INDENT]In Ubuntu/Kubuntu 9.04 I like to have Ctrl-Alt-Backspace enabled to restart X server, which I found a quicker way to log off and log on since I use to hop around from Kubuntu to Ubuntu and back.
And I want it too in my Ubuntu 9.10. Fortunately in Ubuntu 9.10 the method is easier, way easier. No editing necessary like in 9.04. So there's how :
In Ubuntu :

    * System->Preferences->Keyboard
    * go to Layouts tab and click Layout Options button
    * Select "Key sequence to kill the X server" and check "Control + Alt + Backspace"[/INDENT]

FYI, previous method for 9.04 Jaunty et al.
**Xorg Server 1.6.x and Ctrl-Alt-Backspace**
[http://www.nepherte.be/xorg-server-16x-and-ctrl-alt-backspace/](http://www.nepherte.be/xorg-server-16x-and-ctrl-alt-backspace/)
credit: NEPHERTE (DOT) BE  *(actual poster uncertain)*

[INDENT] you can enable it back again by editing the /etc/X11/xorg.conf file. Adding:
```

Section "ServerFlags"
Option "DontZap" "false"
EndSection

```
will make Ctrl-Alt-Backspace work again. If you&#8217;re using xorg server 1.6.1 or later, you&#8217;ll have to do some additional stuff. Either add
```

<merge key="input.xkb.options" type="string">terminate:ctrl_alt_bksp</merge>

```
to your /etc/hal/fdi/policy/10-keymap.fdi file or run
```

setxkbmap -option terminate:ctrl_alt_bksp

```
everytime after you started X.[/INDENT]

---

### Post by ScottHW on 2009-11-07
[http://ubuntuguide.net/disable-60-seconds-delay-notification-in-ubuntu910karmic](http://ubuntuguide.net/disable-60-seconds-delay-notification-in-ubuntu910karmic)
credit: Ubuntu Guide Admin, with editing by ScottHW

[INDENT]This tutorial shows how to disable 60 seconds delay notification for Logout, Restart and Shutdown in Ubuntu 9.10 Karmic Koala.

First, press Alt+F2 to bring up Run Application, and type gconf-editor.  Click Run.

Navigate to apps->indicator-session.  Double click on the only line in right box, suppress_logout_restart_shutdown 
and set its value to TRUE by checking the box.[/INDENT]

---

### Post by ScottHW on 2009-11-07
Don't remember if I had to manually do this before, but I don't like the Tap-to-click "feature".  Just causes too many stray clicks for me.

To Disable:

System>Preferences>Mouse
Touchpad (tab)
[_] Enable mouse clicks with touchpad (uncheck)

---

### Post by ScottHW on 2009-11-07
GRUB 2 - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

GRUB 2 - Ubuntu Wiki
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
(seems to have at least one mistake...)
GRUB_HIDDEN_MENU_QUIET=true 
should likely read
GRUB_HIDDEN_TIMEOUT_QUIET=true 

I installed Startupmanager
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
But it doesn't work completely with GRUB 2 yet...


[http://digitizor.com/2009/10/28/getting-ready-for-karmic-koala-upgrading-to-grub-2/](http://digitizor.com/2009/10/28/getting-ready-for-karmic-koala-upgrading-to-grub-2/)

GRUB 2 settings are in:
```
/boot/grub/grub.cfg
```
BUT.... this file is automatically generated, and should NOT be edited itself.  Instead, you can edit
```
sudo gedit /etc/default/grub
```
I went ahead and changed (added the # to comment out the quite splash)
```
GRUB_CMDLINE_LINUX_DEFAULT="#quiet splash"
```
Because I like to see the startup commands, helps to try to diagnose simple problems.

And afterwards, 
```
sudo update-grub
```

[http://ubuntuforums.org/showthread.php?p=7854520](http://ubuntuforums.org/showthread.php?p=7854520)

---

### Post by ScottHW on 2009-11-08
I was messing around

System>Preferences>Startup Applications

[_] Bluetooth Manager
[_] Evolution Alarm Notifer

Figured I don't need either of these, and I would save a bit of boot time and some system resources.

---

### Post by ScottHW on 2009-11-08
Ubuntu: Revert to traditional boot splash in 9.10
[http://www.dwasifar.com/?p=846](http://www.dwasifar.com/?p=846)
credit: dwasifar

[http://ubuntuforums.org/showthread.php?t=1293350](http://ubuntuforums.org/showthread.php?t=1293350)

---

### Post by ScottHW on 2009-11-13
I wanted to increase my boot time

[Karmic] Boot time has a huge regression (~1.5 min against ~40 sec for Jaunty)  
[https://bugs.launchpad.net/ubuntu/+bug/442132](https://bugs.launchpad.net/ubuntu/+bug/442132)

dupe of...
performs poorly on slow HDD
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/432089](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/432089)


I applied Scott J's method.

[indent]
Scott James Remnant  wrote on 2009-11-09:  	  #20

Please try the following:

  sudo add-apt-repository ppa:ubuntu-boot/ppa
  sudo apt-get update
  sudo apt-get dist-upgrade

This should install an updated kernel package, and replace sreadahead with ureadahead.

The first reboot will reprofile your system, the second reboot should be substantially faster.

Please let me know how you get in (before/after bootcharts always appreciated)
[/indent]


Now I can't tell if I'm actually booting that new modified kernel version with -ureadahead, because I've been toying with GRUB 2.  Also, now the fix for the GRUB 2 hidden menu doesn't seem to be behaving quite the same...

---

### Post by ScottHW on 2010-02-03
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Installing libdvdcss

Ubuntu 9.04 and 9.10 (i386, amd64)
* Install the libdvdread4 package (no need to add third party repositories) via Synaptic or command line: 

[INDENT] sudo apt-get install libdvdread4[/INDENT]

* Then open a terminal window and execute: 

[INDENT] sudo /usr/share/doc/libdvdread4/install-css.sh[/INDENT]

---

### Post by Fenderian_Mayhew on 2012-01-22
Has anyone ever gotten either the screen or media keys working. I could use the keyboard button. I've been using fvwm mostly and need onboard accesable.

---

