---
title: "Ubuntu crashes when used with KVM switch"
date: 2022-09-20
forum: Hardware
---

### Post by james@finnall.net on 2022-09-20
Hello,

I am using two 1920x1080 displays and four computers with a VGA/DVI KVM switch.  When I switch away from Ubuntu and then switch back I will loose the right LCD panel and all apps move to the left panel and that is followed by being logged out.  The right panel is black.  I can only recover the right panel by restarting the computer.  This can happen several times a week.  It also appears to work OK if the switch is only brief, if longer than say 5 minutes then the problem is more likely to appear.

Any work in progress is lost in addition to the time and effort of restarting everything.  I do play music constantly and it will continue to play while I am switched away to another system.  The music stops when I attempt to switch back.

This is a new system build from about two months ago.  Prior to that I was running Ubuntu 18.04 LTS Desktop and had no issues switching between the computers.

Ubuntu 22.04 LTS Desktop
CPU Intel core i5-10400
   with Intel 630 CPU graphics
16 GByte RAM
Gnome 42.4

KVM switch: Startech 4 port KVM with dual monitor support.  Also includes USB hub and audio.

Screen saver is disabled so should not be causing any problems.  Are there any other settings that could effect monitor detection and/or retention?

Thank you,
James

---

### Post by TheFu on 2022-09-20
I don't have this issue with either of my KVM switches.  I have a VGA+PS2 switch and an 4K@60hz  HDMI+USB3+audio switch.

My KVM switches don't support dual monitors - the second monitor is controlled a 4x2 4K@60hz matrix HDMI switch with separate input-->output controls.  In general, I have the 2nd output from the matrix switch going to an HDMI recording device, not a monitor.  These are all no-name devices.

I do have some issues with the USB keyboard on 1 computer going through the newer KVM switch. It isn't always recognized at boot, but post-boot, it is seen about 3-5 seconds after the KVM changes the computer to be used.  That's a USB thing, I think, since with the PS2 mouse+keyboard, the toggle between computers was instantaneous -ZERO delay before I could type or mouse.  I was warned that cheap USB KVM switches had that issue.  Basically, it is like unplugging the USB connection and plugging it into the other computer, so a delay is expected.

I think $700 KVM switched emulate the USB devices back to the computers, even when the actual mouse and keyboard are not connected.  That's the difference between a cheap KVM and a "professional KVM" switch, I suppose.

My cheap KVM is an "ezcoo" for about $130. So far, so good ... with the delays after switching between systems.  The different physical computers stay up until I reboot them for some reason, usually a new kernel was installed.
```
$ uptime 
 15:54:31 up 4 days, 20:46, 

$ uptime 
 15:55:26 up 10 days,  2:57, 
```
You get the idea.
I rebooted the other boxes today due to some boot storage migrations work that was unrelated.  Moved /boot/ to a larger partition on an NVMe drive - basically added 500MB to allow more kernel lines on that system. This is in prep for a fresh OS install and data migration. Yawn - not really related to this thread.

---

### Post by #&amp;thj^% on 2022-09-20
Along with TheFu's advice, and just a guess but Screen Lock, is that still enabled?

---

### Post by james@finnall.net on 2022-09-21
I think all settings are disabled for screen saver, etc.  I can however, "lock", the station from the menu and enter my password to "unlock".  But I do not switch away while it is in "locked" mode.   I use the station lock mode at night when I leave work.  Also, if not clear from my original post is that it seems to effect the right panel since the left panel continues to work.  However, my processes are all messed up so it logs me off and terminates everything.

---

### Post by TheFu on 2022-09-21
Wayland or X11?  Might try using the other other option, see if that changes the behavior.

Is there a specific model of the KVM switch that someone could look up for the real specs?  I did some searching but couldn't find any that supported 4 computers with dual monitors.

BTW, could you clarify whether the audio is going through the KVM switch too or not?  If you switch to a different computer and the audio keeps playing from the computer you left, that's a bug.   While my KVM supports audio, I have 2 speaker setups and directly connect those to 2 of the computers.  I play music on the 5.1 system using mpd, so it can be controlled remotely by lots of different clients.

---

### Post by james@finnall.net on 2022-09-22
When I run top,  I see a process called Xwayland.  So I suppose it to be wayland.  It is the default on Ubuntu 22.04LTS and I think I am using the default gnome 3 desktop.

I will see if I can find directions on how to switch to X11 and test there.  As I recall I would have been running X11 on my prior systems.

The audio on the secondary computers do play through the KVM switch.  But not the main system since that is what plays all the time.  The other 3 systems are using a set of headphones on the KVM switch.  That is why I mentioned the music continues to play while switched away.  It terminates when I attempt to switch back and everything terminates.

KVM Switch is StarTech.com model [URL="https://www.amazon.com/gp/product/B002ZV6VPA/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1"]SV431DDVDUA 



[/URL]

---

### Post by james@finnall.net on 2022-10-07
I switched the system to X11 about a week ago and so far no problems.  
Only time will tell for sure but at the present time it does appear that the problem may be with Xwayland.
Thank you for all the assistance.
James

---

### Post by james@finnall.net on 2022-10-19
I marked the thread as solved.  I left the machine running last night but the kvm switched to another station for over 19 hours.  I switched back this morning and all is well just like I left it.
So it appears that switching the system back to Xorg resolved the issue.
Thank you once again.

---

