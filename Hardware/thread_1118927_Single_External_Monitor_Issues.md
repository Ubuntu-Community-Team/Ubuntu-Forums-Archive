---
title: "Single External Monitor Issues"
date: 2009-04-07
forum: Hardware
---

### Post by Scuddlefish on 2009-04-07
Hello ubuntu community!

After wiping my hard drive and reinstalling windows alongside ubuntu (dual boot), I'm having troubles getting my external monitor (plugged into my laptop) to work. I've had ubuntu previously, and I remember altering the xorg.conf file, but from what I've searched for just now indicates that I do not need to for such a simple configuration. I also don't remember exactly how I altered the file, and I cannot find the sources from which I found out how to do it.

When I boot up I can see GRUB and the ubuntu loading up screen on both my laptop screen and my external monitor screen, but only my laptop screen displays anything after that point.

Thank you for reading this, and thank you in advance for any help.

Regards,
Scuddlefish...Brett :)

---

### Post by Scuddlefish on 2009-04-07
bump, looks like there is a lot of traffic. Already on page 4 :(.
Any help would be kindly appreciated.

---

### Post by Scuddlefish on 2009-04-08
bump, I feel like I'm being a nuisance by having to bump several times, but I'm afraid my thread will just get lost :-O.

Please read above. 
Thank you.

---

### Post by lparsons42 on 2009-04-08
I can tell you that I had the same problem in Kubuntu 8.10, and apparently this problem is not of any value.  Actually, if you can boot while connected to the external monitor, then you are getting further than I can.  I found that attempting to boot while my laptop is connected to an external monitor or projector ends in complete and miserable failure.  If I connect it after booting "normally", it fails less miserably, in the fact that at least my laptop is usable through the main screen (though the connected external display *never* works).

I can also tell you that this is not a problem in FreeBSD on my thinkpad, so next week I will wipe out my Linux partition and go back to FreeBSD.  I would suggest looking into the same option if you haven't already.  The biggest caveat however is that FreeBSD doesn't do recent version of flash or wine anywhere nearly as well as Linux.  If those are not of significance to you, then you may find FreeBSD to be a better option as well.

---

### Post by phil11 on 2009-04-08
> **lparsons42 said:**
> I can tell you that I had the same problem in Kubuntu 8.10, and apparently this problem is not of any value.  Actually, if you can boot while connected to the external monitor, then you are getting further than I can.  I found that attempting to boot while my laptop is connected to an external monitor or projector ends in complete and miserable failure.  If I connect it after booting "normally", it fails less miserably, in the fact that at least my laptop is usable through the main screen (though the connected external display *never* works).

I can also tell you that this is not a problem in FreeBSD on my thinkpad, so next week I will wipe out my Linux partition and go back to FreeBSD.  I would suggest looking into the same option if you haven't already.  The biggest caveat however is that FreeBSD doesn't do recent version of flash or wine anywhere nearly as well as Linux.  If those are not of significance to you, then you may find FreeBSD to be a better option as well.

I have the same problem with 8.04. I've tried other live Linux distros and while the external monitor might work I never could figure out how to get the printer working. How is the FreeBSD with printing (Brother Laser)? The Ubuntu works fine with it (well, mostly fine). But it is really slow in accessing a USB external secondary drive. I have it dual booted with WindowsXP, using the Ubuntu for the Internet and the WindowsXP for the rest (writing, CD writing).

---

### Post by lparsons42 on 2009-04-08
> **phil11 said:**
> How is the FreeBSD with printing (Brother Laser)? The Ubuntu works fine with it (well, mostly fine).
How do you print to your printer?  I can tell you that my experience setting up an old HP (laserjet 4) in CUPS was that FreeBSD for some reason ran with it much easier than did Kubuntu.  This was setting it up over the network; I haven't tried setting up a locally-connected printer in CUPS under either system yet (I don't see a reason to connect a laptop directly to a printer when I have a home network).


>  But it is really slow in accessing a USB external secondary drive. I have it dual booted with WindowsXP, using the Ubuntu for the Internet and the WindowsXP for the rest (writing, CD writing).
I have burned CDs from my laptop in FreeBSD no problem.  Have not tried the same in Kubuntu yet. This is using the DVD-ROM/CDRW combo drive in my laptop; have not tried a USB optical drive.  I have used my USB flash drive in both FreeBSD and Kubuntu and found the experience was adequate and more or less equivalent in each.

---

### Post by Scuddlefish on 2009-04-08
Thanks for the reply, but please keep topics related to the original post. 

Actually, as I described in the original post, I've had it working perfectly before. So I at least know that there is quite an easy fix. I had edited the xorg.conf file, but I don't remember exactly what I should add (and I don't remember having to put any exact numbers for any value). Also, what I've been reading suggests that for my simple set up (just one external monitor) I probably don't need to edit it.

Any help would be greatly appreciated!
Thanks!

---

### Post by lparsons42 on 2009-04-08
> **Scuddlefish said:**
> Thanks for the reply, but please keep topics related to the original post. 
Sorry, I promise I am not trying to hijack your thread.


> Actually, as I described in the original post, I've had it working perfectly before. So I at least know that there is quite an easy fix. I had edited the xorg.conf file, but I don't remember exactly what I should add (and I don't remember having to put any exact numbers for any value). Also, what I've been reading suggests that for my simple set up (just one external monitor) I probably don't need to edit it.

Any help would be greatly appreciated!
Thanks!
Though I can tell you I posted almost the identical problem last week and never had a response.  The best solution I have found to this problem is to not run Ubuntu.

As far as the xorg.conf file goes, it seems that the application of that file has changed dramatically in recent versions - as in, I'm not sure if it is used at all anymore.  So I'm not sure that you'll solve your problem by editing it, though I could be wrong.

---

### Post by Scuddlefish on 2009-04-09
Hi all,

For anyone still interested in this, I now have everything working properly, though I didn't really "fix" the problem.
I was running version 8.04 and decided to do a clean reinstall to version 8.10. I'm sure I could have fixed it in 8.04, but I don't have a lot of time to mess around with something like trying to get my monitor working with school and work.

:)

Regards,
Scuddlefish

---

### Post by digitalramble on 2009-04-10
Well I have a similar type of issue here.  I have 8.10 on an older laptop (a 2004 gateway laptop) and a widescreen flat monitor attached to it -- this works just fine and it clones the laptop screen and I use xrandr to resize it for the larger monitor (I haven't yet tried making it a dual monitor setup where the available "screen" tracks across both).

So now I have a new laptop (hp dv4tse) on 9.04 rc1, but when I plug the monitor into this I get nothing (and it doesn't help to logout, reboot, whatever).  (On the other laptop, before using xrandr, it would clone it fine with no tweaking, just look like hell b/c the aspect ratio was too far off.)  I've tried some of the similar things I did on the other laptop to set it up there, but nothing here. 

Any thoughts about what I can look at?  I pored over dmesg ,but am not sure what I'd be looking for.  Clearly the monitor itself is fine (since it still works a charm with my old laptop) and clearly ubuntu can deal with it (as recently as 8.10 anyway) so I'm not sure what steps to take to zero in on the possible source of the problem?

Any tips or suggestions would be greatly appreciated...

---

