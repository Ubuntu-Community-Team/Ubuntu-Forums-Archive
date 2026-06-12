---
title: "HP Pavilion ZE4805US issues"
date: 2008-08-16
forum: Hardware
---

### Post by wizardfait on 2008-08-16
I have an HP Pavilion ZE4805US, and out of the box, everything works in Ubuntu except for the wireless card. (The infamous Broadcom 4306).

I have gotten the wireless card to work by plugging the laptop into a router using a CAT5 cable, and downloading b43-fwcutter, however it is highly unstable, and likes to just not connect.

I remember reading somewhere that the 4306 should use the b43-legacy, or something like that... How do I use it instead of b43? And are they correct?

Another thing, I've tried NDISwrapper, and only one time did I ever get it to work with reporting 54Mbit, however, I only seemed to get 1Mbit down, and 1.5Mbit up, so I tried wiping Ubuntu and starting over (I had tried many fixes, and thought they were somehow overlapping/interfering). Only to find, now I can't get NDISwrapper to report 54Mbit anymore, and I'm still not sure how exactly to go about using this. The guide I used will be attached, and I (of course) used the RIGHT version of bmcwl5.inf as opposed to the one described in the tutorial.

Is this tutorial correct? 

And if not, how should I correctly install NDISwrapper?

And lastly, am I supposed to install b43-fwcutter first, for the firmware for the chip, and THEN install NDISwrapper? Or are the two supposed to be totally separate?

One more issue, on this laptop, the side buttons for the sound control work perfectly fine, however, the mute button is supposed to light up when muted, however it doesn't. Does anyone know the fix for this? I do know that during boot, there are a few messages that say something about some errors with alsa, and one that may be unrelated saying to fix something about memory addresses to update my BIOS (Which is currently the newest version), or to manually set it.

I don't know how to get back to these messages, and be able to copy and paste them for analysis if required, so some help with that would also be appreciated.

One last problem, related to the wireless card: This laptop also has a button for turning the wireless card on/off, however, this is a software-driven button. Even in Windows, a special program needs to be installed in order for it to work. Do you know of a fix for this as well?

I believe that's all my issues for now. Any help at all would be greatly appreciated. However, the most important issue in my opinion is at least getting my wireless to work to the best of its ability (Which I know is hard being as Broadcom hasn't released their card's specs, making the act of making a driver for it very difficult, however, I've heard of people getting theirs to work perfectly).

However, even if it's not possible to get it working "Perfectly" to at least get better than 1Mbit speeds, and have it able to actually connect, when I tell it to connect, not just when ever it chooses to feel like working.

---

### Post by Ayuthia on 2008-08-16
> **wizardfait said:**
> 
I remember reading somewhere that the 4306 should use the b43-legacy, or something like that... How do I use it instead of b43? And are they correct?
If you installed b43-fwcutter from the ubuntu repositories, the system will select the correct one automatically.  If I recall, I think that it was the 4306 rev 02 that has shown up as b43legacy, but I could be wrong.

> Is this tutorial correct? That tutorial is correct and has worked for quite a few people.

> And lastly, am I supposed to install b43-fwcutter first, for the firmware for the chip, and THEN install NDISwrapper? Or are the two supposed to be totally separate?They are totally separate.  The b43-fwcutter is the application that cuts out the necessary information from the firmware that is used for the b43 driver (not NDISwrapper).  If you are using NDISwrapper, you don't need to install b43-fwcutter.  NDISwrapper uses the Windows wireless drivers instead.

> One more issue, on this laptop, the side buttons for the sound control work perfectly fine, however, the mute button is supposed to light up when muted, however it doesn't. Does anyone know the fix for this? I do know that during boot, there are a few messages that say something about some errors with alsa, and one that may be unrelated saying to fix something about memory addresses to update my BIOS (Which is currently the newest version), or to manually set it.I am not too sure about this one, sorry.

> I don't know how to get back to these messages, and be able to copy and paste them for analysis if required, so some help with that would also be appreciated.You should be able to retrieve those messages through dmesg.  You can just type dmesg in the Terminal and it will list it all out for you.  You can also go into /var/log/dmesg and get it from there also.

> One last problem, related to the wireless card: This laptop also has a button for turning the wireless card on/off, however, this is a software-driven button. Even in Windows, a special program needs to be installed in order for it to work. Do you know of a fix for this as well?I don't have any experience in this at all, sorry.

> I believe that's all my issues for now. Any help at all would be greatly appreciated. However, the most important issue in my opinion is at least getting my wireless to work to the best of its ability (Which I know is hard being as Broadcom hasn't released their card's specs, making the act of making a driver for it very difficult, however, I've heard of people getting theirs to work perfectly).The 4306 cards have been hit and miss for many people.  I have a 4306 rev 03 card on my Dell and it works well.  However, I have seen a lot of other ones where it will not connect well and have also seen some that have the same issue as yours.  As for Broadcom, they are now doing development for linux.  They have made a linux Broadcom driver for the 4311, 4312, 4321, and 4322 cards.  I have a 4311 rev 01 on my HP and it works really well with the new Broadcom driver (I did try it with my 4306 card and it did not work).  Hopefully they will be expanding the support for their other cards also.

---

### Post by wizardfait on 2008-08-17
Thank you very much for all of your help.

Do you know anyone/anywhere I can find to get answers for the other issues, such as the wireless button, and the light-up mute button?

Also, have you known of an issue with one install of Ubuntu, fully updated, the card works flawlessly, but the next install, same machine, it doesn't?  I had it working once, but I mudded-up the system, and reinstalled Ubuntu and did exactly what I did before, but without all the "Dirty" stuff (Writing to files, and not being able to reverse it, and applying things I don't know how to un-apply... (Still a little new to Linux, so I'm not as experienced with this stuff as I would like to be)) and the wireless card was horrible once again... Could there maybe be some information in that? Such as maybe the driver only likes certain things, even if hardware isn't changed? Idk if that helps, or even is relevant... Just kind of randomness.

---

### Post by wizardfait on 2008-08-19
Update: I got my wireless working, perfectly. My method is as follows:
1. Install Ubuntu (Obviously)
2. Pop CD back in, and install NDISwrapper and NDISgtk from the CD.
3. Use NDISgtk to install the driver.
4. Made script like in first post's tutorial, but modified it to be:
[INDENT]modprobe -r b43legacy
[/INDENT][INDENT]modprobe -r ssb
[/INDENT][INDENT]modprobe ndiswrapper
[/INDENT] 5. Done!

:D

Doing Ubuntu-Updates now, and once I reboot, I'll see if the settings stick, or if I need that script to auto-remove and auto-probe those modules at startup.

Anyone have any answers as to the wireless button, and the mute button problems?

---

