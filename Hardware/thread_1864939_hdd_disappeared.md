---
title: "hdd disappeared?"
date: 2011-10-19
forum: Hardware
---

### Post by prayersfor.rain on 2011-10-19
I have 3 hard drives. 1 runs winxp, the 2nd is (was?) Ubuntu 10.10, the 3rd is storage.
Last night my boyfriend started the computer, it was in sleep mode. I thought it froze because it was taking what I thought was a long time (It wasn't, I didn't realize that he'd JUST "woken it up" a few seconds before) so I figured it froze and I restarted it by pushing the button on my computer. From what I'm guessing, I just didn't wait long enough.
Anyway, now when I try starting up grub says 
[B]error: no such device (uuid of drive)
grub rescue>[/B]
I figured I messed up grub.
I booted live cd of 10.10, ran sudo fdisk -l, and it shows sda (winxp), sdc (storage), but no sdb (ubuntu drive). At all.
I repaired grub.
Nope.
When I go into bios to change the boot order that ubuntu drive doesn't show up AT ALL.

It's like my drive is just gone.
Usually when something weird happens & I can't fix it I repair grub  or reinstall ubuntu.  But the drive has completely disappeared and  I  can't reinstall onto nothing.

I was able to boot into winxp by changing boot order (before I did that grub didn't even give me a chance to choose it) and it shows a "Z" drive with a question mark on the icon.  I am assuming this is my Ubuntu drive as the windows and storage drives show up as regular hdd's.  When I click on this Z drive it it says
**Z:/ refers to a location that is unavailable. It could be a hard drive on this computer, or on a network. Check to make sure that the disk is properly inserted, or that you are connected to the internet or your network, and then try again. If it still cannot be located, the information might have been moved to a different location.**

It's as if I physically removed the drive, but I haven't touched it at all.
I'm not all too sure what to do.  Physically detach the drive, reattach it? 

If I can't get it to work that's 500gigs completely wasted :( sure I can run live cds forever but...500 gigs? and I would rather not use winxp because the boyfriend is great at downloading all sorts of TERRIBLE movies with viruses attached and quite honestly I'm tired of constantly getting rid of them. Especially with live cd because I'd have to get clamAV every time as it doesn't save onto cd. 
Any help would be MUCH appreciated!  TIA!!

---

### Post by prayersfor.rain on 2011-10-19
Ok I unplugged and re plugged in everything.
Grub's kinda crazy though. it gives me winxp option and ubuntu, when I choose ubuntu it says 
**GNU GRUB version 1.98-1ubuntu Minimal BASH-like line editing is supported.**
And whatnot.
I typed reboot and got into live cd again. The drive now shows up. I guess I gotta fix grub? So I'll do that now.

Edited to add: now neither my 2tb nor my winxp drives are showing up in "places" on livecd. When I sudo fdisk -l they show up. But I don't know how to use terminal to do everything, I wanted to move some files to my 2tb and maybe reinstall? if grub repair doesn't work.
Actually I wanna install mint. Preferably zenwalk but the bf is not used to slackware.
Ugh this is all so annoying.


Edited again: Restored grub, everything's fine. Trying to figure out how to mark this solved.

---

