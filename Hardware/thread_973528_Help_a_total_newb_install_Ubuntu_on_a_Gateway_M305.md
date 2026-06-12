---
title: "Help a total newb install Ubuntu on a Gateway M305CRV"
date: 2008-11-06
forum: Hardware
---

### Post by Bailywolf on 2008-11-06
I use an older laptop for my fairly easy going home computing- writing, some minor photo editing, music, and the internet.  

It's a hand-me-down Gateway M305CRV with 512 MB RAM and a P4 1.X Ghz processor.  Currently, it's got XP Home edition on it.  I wanted to bone up on my Linux (I'll be getting a Linux web server to admin at work soon, so I figured I'd better get comfortable with it first), and all my googling indicated Ubuntu is a great place to start.

Anyhow, I tried doing the trial implementation from the CD I burned, but ended up with piles of errors when I tried to boot live from the CD.  A discouraging way to start.  

Now I'm hesitant about just going ahead with the install, and damn the torpedoes- I don't want to hose the laptop, which works fine now.  

I've got the most recent release of Ubuntu (Ibex), and it boots fine from the CD... it just throws endless errors when I try and run the OS from it.  

If I decide to just install it... 

What's the best way to go about it?  What should I have on hand in case something (sound, power management, ect) craps out?

I'm not afraid of the command line (I admin AS400 machines), but my UNIX is RUSTY... I'd hoped UBUNTU would be as easy to get cooking as Windows.

So, help a total newb out?

-B

---

### Post by bonestonne on 2008-11-06
i actually have the same laptop, so does AudioDef.

from what i know, AudioDef has his install working great for him, mine is doing mostly good, i actually just ordered a RAM upgrade that should arrive by next week (going from 2x 256mb to 2x 512mb).

my m305CRV doesn't have audio output right now. that's something i'm just going to keep attacking until it works for me. it could just be my install because AudioDef doesn't have the same problem.

i know a few things you'll want to know though:
1) for me, the boot screen doesn't work with mine. the machine still boots, but with a blank screen. there's a way to fix that, and i'm off to do so soon.
2) the wireless card should work without any extra drivers
3) ubuntu shouldn't have any problem running on 512mb of RAM.

ubuntu will come with all the software you need in order to do everything you want, and it will feel snappier than windows once it's started.

if you still have issues with the the live CD, you might try downloading WUBI, the windows ubuntu installer. that shouldn't have any problems.

---

### Post by Bailywolf on 2008-11-07
Thanks for the quick turnaround bonestonne- but in 11 hours, my post had bumped to the 5th page.  Things move fast hereabouts. 

I played with a few of the suggested tweaks last night, but couldn't get the live CD version of run on my laptop, and was a little gunshy about running ahead with the full install.

The CD image I downloaded (the most current one I assume) came with WUBI as well as some other install methods... start the machine with the CD, and the menu allows the live version w/o making any permanent changes as well as installing it.  

What killed me is when I decided to try the WUBI install from inside Windows, and it started downloading all over again, and was taking forever on my low-end DSL/Wireless network.  Why wouldn't it use the install files right there on the CD?  

Is there any way to get the files I'd need for that WUBI install here on my blazing fast network at work, and bring them home with me?

Or should I just say hell with it, and go for the boot menu install?

-B

---

### Post by bonestonne on 2008-11-09
ubuntu just isn't designed to install through windows, it's for Apt. that's why Apt pops up when you stick a ubuntu install CD in a Ubuntu machine...

as per the installations, i'm not really sure about using the Install Now option. i've never had to use that method before, so i can only assume that it's the same UI as in the live environment.

my ultimate suggestion for trying the Live CD is to burn another copy, but this time burn it at like 8x or something like that. i do that with all my media to prevent errors.

---

