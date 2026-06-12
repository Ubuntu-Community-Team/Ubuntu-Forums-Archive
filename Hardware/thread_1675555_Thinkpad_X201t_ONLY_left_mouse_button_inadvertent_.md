---
title: "Thinkpad X201t ONLY left mouse button inadvertent double click"
date: 2011-01-25
forum: Hardware
---

### Post by KVirtanen on 2011-01-25
Hi guys!

I just finished installing Ubuntu 10.10 64-bit on my Thinkpad X201t (tablet) through WUBI and I'm faced with a strange problem. I had 10.10 installed earlier and didn't have the problem. So maybe this bug came with the system updates.. don't know ... :/

Basically, the left mouse button, the one right under the red trackpoint button AND ONLY THAT ONE is randomly double clicking instead of single clicking. The right and middle buttons work fine as do all the normal gestures done on the trackpad and the additional two buttons below the trackpad. Only this one button is misbehaving.

**EDIT: I'll add that I even tried changing the mouse handedness, but the problem with the same physical button remained, it just made random right-doubleclicks. It must have something to do with the signal coming from the physical button.** 

I also have Windows 7 Professional 64-bit installed and this doesn't happen there at all. Nor has it ever happened during the two months I've owned this brand new computer - and as I mentioned, it didn't happen when I previously had 10.10 64-bit installed.

Now that xorg.conf is gone, what could I do to debug this?

Here's what xev outputs for a single left-click:

```
ButtonPress event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x4400002, time 752174, (41,38), root:(42,443),
    state 0x0, button 1, same_screen YES

EnterNotify event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x0, time 752174, (41,38), root:(42,443),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967212 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x4400002, time 752252, (41,38), root:(42,443),
    state 0x100, button 1, same_screen YES

LeaveNotify event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x0, time 752252, (41,38), root:(42,443),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0
```Here's for the right-click:

```
ButtonPress event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x4400002, time 937381, (42,37), root:(43,442),
    state 0x0, button 3, same_screen YES

EnterNotify event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x0, time 937381, (42,37), root:(43,442),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1024

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967212 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x4400002, time 937415, (42,37), root:(43,442),
    state 0x400, button 3, same_screen YES

LeaveNotify event, serial 33, synthetic NO, window 0x4400001,
    root 0xac, subw 0x0, time 937415, (42,37), root:(43,442),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0
```I'm clicking inside the square in xev. When clicking outside there are no KeymapNotify, EnterNotify or LeaveNotify events. The values for all hardware mouse buttons and taps on the trackpad are the same for respective keys (I have 3 ways for left-clicking and the values match).

What I'm gathering is that xev doesn't seem to show double input events even if I KNOW they're happening (I'm closing dialogs and Firefox tabs by accident all the time.....). I made dozens of clicks to come to this conclusion.

Any clues guys? :)

---

### Post by miobrad on 2011-02-04
i have just installed 10.10 on an x201i and can confirm the problem! any solutions yet?

---

### Post by miobrad on 2011-02-04
i think i found the solution - it seem to work for me:
go to: System/Preferences/Mouse/Touchpad and disable: mouse clicks with touchpad.. i suppose the finger just kept touching he touchpad..

---

### Post by Favux on 2011-02-04
Hi,

You might be interested in Magick Rotation.  It gives you automatic screen rotation along with the ability to toggle touch on and off, among other things.  On Launchpad:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

### Post by KVirtanen on 2011-02-05
> **miobrad said:**
> i think i found the solution - it seem to work for me:
go to: System/Preferences/Mouse/Touchpad and disable: mouse clicks with touchpad.. i suppose the finger just kept touching he touchpad..

Sigh... Occam's razor to the rescue :)

For the time being I'll try (hard) to restrain myself from banging my head against my desk - I simply can't believe that was the reason :) I must admit that now that I pay attention to the trackpad I haven't had any erroneous doubleclicks... I feel so stupid :D

But to my defense I also must add that I have NEVER clicked the trackpad by mistake in Windows. Must be a different click threshold there I guess.

Thanks for the help guys ;)

---

### Post by miobrad on 2011-02-05
Favux - you are great! thank you so much. i installed magick rotation and it works great!

may i ask you - can you point me to up to date how to so i can enable the tablet buttons (screen rotation)?

thanks so much!

---

### Post by Favux on 2011-02-05
Hi miobrad,

Excellent!

Sure, see linduxd00's post [http://ubuntuforums.org/showthread.php?t=1656632](http://ubuntuforums.org/showthread.php?t=1656632).  By the way linuxd00 was one of the testers who helped us add the ThinkPads to Magick a week or two ago.  :)

---

### Post by mikio on 2011-02-05
ooops - i had a bad crash today. i accidentally held the power button while in tablet mode. when i tried to boot the next time i had the error descibed here:

[http://ubuntuforums.org/archive/index.php/t-1244466.html](http://ubuntuforums.org/archive/index.php/t-1244466.html)

i loaded the livecd and tried to fix it (gparted/diskutility and manually using "sudo e2fsck -fyv /dev/sda1") but all methods give me the same error: device busy :(

i think it is due to the crash. i think the file system is corrupted. i wonder - is this due to ext4? i never had this problem before - ext3.. 

hmmmmm i think i will reinstall (i did not like leaving windows on there anyways). a fresh install on a ext3 partition.

any thoughts much appreciated!

thanks again!

---

### Post by Favux on 2011-02-05
Leave Windows on.  You'll find its much easier to update the bios and firmware with Windows.  Just shrink the Windows partition.

---

