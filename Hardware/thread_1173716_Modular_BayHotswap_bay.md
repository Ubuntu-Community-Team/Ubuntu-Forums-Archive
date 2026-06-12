---
title: "Modular Bay/Hotswap bay"
date: 2009-05-30
forum: Hardware
---

### Post by Saxie on 2009-05-30
Hello all :)

First time user of Ubuntu, very green when it comes to Linux.  After searching through the various threads about this none have actually corrected my issue.  So I throw my hands at the feet of the community lol.  I have managed to get everything running, wireless card etc.

This isn't a HUGE issue as I do dual boot between this and xp but it would be nice if I could get this to work.

Problem:  Removal of the CD/Dvd Rom drive locks Ubuntu up
Objective:  I want to be able to remove that drive in place of an extra battery if need be w/o having the system lock up.
What I've Tried:  The tool called 'Hotswap'.   However with the tool I am getting the following message:

[B][I]**I/O warning : failed to load external entity "/etc/hotswaprc"
hotswap 0.4.0
Copyright 2001 Tim Stadelmann
This program is free software, licensed under the conditions of the
GNU General Public License version 2, or (at your option), any later
version.

There is currently no IDE device configured.  (Floppy disk drives,
batteries, and 'travel modules' are not managed by this utility.  If
you want to swap such a module, you should remove it now.)

Would you like to insert an IDE device into the module bay? y
Please insert the new device into the module bay and press RETURN.

hotswap: opening IDE device failed: No such file or directory**[/B][/I]

Now I have found that using this utility I can remove the drive without it locking up on me (when I am at the "please insert the new device...").  Upon popping the drive back in, the drive is unresponsive. 

The System:  Lshw info in attachment

Sorry about the long post just wanted to make sure I have provided as much info as possible.
If anyone has any ideas please post them, I am eager to hear them.  Remember... I've been using Linux for...about a week, so forgive me if my reply is less than...informed :)

Other than this issue, I have very much enjoyed Ubuntu.  Using Windows since Win95, its a huge learning process.

---

### Post by erdelyi on 2013-03-13
The accident can happen like the following, also for the root device:

1. Connecting a SATA disk to an E-SATA port, and booting from the external drive.
2. Sending the computer (actually a laptop) to sleep, removing the external drive
3. failing to connect the drive correctly (inserting the cable loosely)

I would appreciate a kind of "mount verification" (about a decade ago I was working as an OpenVMS operator during my university studies, in OpenVMS terms mount verification is when some device seems to be unavailable, the system keeps polling if it became available.
Thanks to journaling file system there is less risk of damage on the file system due to such an accident, but if Linux (I actually use Xubuntu) could deal with the situation it would be a great help :idea: 8-)

---

### Post by varunendra on 2013-03-13
Old thread, Closed.

From Forum's Code of Conduct -
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

Feel free to start a new thread in a relevant section of the forums asking your question.

Thanks!

---

