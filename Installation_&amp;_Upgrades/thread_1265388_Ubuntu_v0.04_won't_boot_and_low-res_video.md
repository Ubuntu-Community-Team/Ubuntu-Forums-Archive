---
title: "Ubuntu v0.04 won't boot and low-res video"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by cooltouch on 2009-09-13
Howdy folks.  My first post here on the forums.  Glad to have found this place, and glad to be here.

Okay, first off -- I am NOT a Linux weenie.  Several years ago, I installed a copy of Suze Linux on an old machine, played with it for a while, was easily bewildered, and gave up.  So, before you choose to offer to help out here, please be aware you are writing to a Linux noob, 'kay?

I just installed v9.04 last night.  Copied the .iso from ubuntu.com and burned the CD.  I installed it on an older machine.  It's running an AMD 1.2ghz processor, has 768mb ram, four smaller hard drives (two 20gb, two 30gb), and an Nvida GX440 (I think?  Something 440) video card.  I used to have SCSI installed in the machine, but its current OS (7100 build of the RC of Windows 7) doesn't support SCSI anymore, so I just removed the SCSI devices.  I haven't used them in years anyway.

I installed Ubuntu onto an emptly 30gb drive.  I figured that way each OS could have its own dedicated hard drive, and there would be less chance of conflicts.

Installation went relatively smoothly except the video resolution defaulted to some very low level, probably 800x600, and the mousable buttons needed to advance through the screens were not visible.  I was able to complete the installation using the Enter and Tab keys.  Back to this in a moment.

After installing Ubuntu, I shut down the machine, then restarted it, expecting to get some sort of boot manager menu.  Nothing appeared.  Instead the machine booted to Win7.  I tried it again, just to be sure, and again it booted to Win7.

I have a copy of System Commander v9 here, and I suppose I can install it to handle the boot chores, but I kinda thought that Ubuntu would come with a boot manager.  What do you folks use for boot management chores?

About my video issues -- I'm running the old Nvidia GX440 card with a relatively new AOC flatscreen.  As I'm sure you're aware, flatscreens work best when run at max resolution.  Max res for this screen is 1680 x 1024, which is just barely supported by the Nvidia card.  I'm keeping my fingers crossed that this card's max res capabilities is supported by a driver out there somewhere.  But more to the moment, I'm wondering how I go about changing resolution.  When I took the test drive from the CD, I found a menu item called Display (I think), but wasn't able to find any resolution selection.  What's the solution for this?  I have a Linux solutions disk that boots from the disk, and offers a number of higher-res modes that work with my system.  I kinda figured I'd find something similar to this with Ubuntu.

Thanks for any help you may be able to provide.

---

### Post by running_rabbit07 on 2009-09-13
Looks like everything mentioned has a simple fix. 

First you need to get grub(Ubuntu's boot loader) installed to your MBR, which can be done following the steps on this [thread]("http://ubuntuforums.org/showthread.php?t=224351").

Once you get the Grub loader installed then you can fix your graphics driver by going to your menu and going to System>Administration>Hardware Drivers and selecting whichever driver is at the top of the list.

Let us know if you need more help.

---

### Post by cooltouch on 2009-09-13
Thanks for the link, running rabbit.  If I may follow up -- as I mentioned in my previous post, I own a copy of System Commander v9, which claims to be able to boot all sorts of OSes.  I am planning to set up a small DOS partition on this machine, and perhaps another OS or two at some later date.  Given this, will I be better off setting up SC9 as my boot manager, or will Grub offer me the flexibility to accomplish this too?

---

### Post by running_rabbit07 on 2009-09-13
I am not sure about grub working with the other installs, but it will work with Windows 7 and Ubuntu.

I have both installed.

---

