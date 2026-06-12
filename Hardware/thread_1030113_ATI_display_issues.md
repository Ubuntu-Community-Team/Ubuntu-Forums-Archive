---
title: "ATI display issues"
date: 2009-01-04
forum: Hardware
---

### Post by TerryArnott on 2009-01-04
Greetings my fellow Ubuntu'ans,

I have recently discovered the joys of linux and am now going through all our household PCs installing Ubuntu 8.10 (intrepid).  due to the fact that each PC's hardware is different to each other one, I am running into issues here and there that the other machines don't share.

The one I'm up against at the moment is a machine with onboard ATI-radion 9100 (onboard version of the 9200) and an AGP slotted ATI-radion 9200.  The pair worked nicely under XP as dual displays and the AGP also ran the TV-out to the big screen TV for watching movies, so all 3 displays were unique and functional at the same time.
Since installing Ubuntu, only one display, the AGP card, works, and even that is pretty dodgy.  The 'monitor resolution settings' window is showing a very limited, list of resolutions.
It starts with the basic 640x480, 800x600, 1024x768, then it gets weird with 1152x864 and 1360x768, neither of which I have seen before.
There are no options for the standard 1280x1024, 1600x1200, etc like it used to have under XP, and the other 2 boxes I have converted to Ubuntu already are showing 1280x1024 and running fine at that res.
I have it hooked up to a LCD with a native res of 1280x1024, so I really want to get it running nice and clean at that res.

I have done a search on here and found a post about installing radion drivers ( [http://ubuntuforums.org/showthread.php?t=1019822]("http://ubuntuforums.org/showthread.php?t=1019822") ), followed the instructions even though it appears that they were already installed (option was to re-install, not just install), and nothing seems to have changed after the reboot.

A smaller problem is that one other machine that is running fine at 1280x1024 is even allowed to go higher, although the monitor can't display it, so I would like to be able to limit the maximum res that can be selected (like you can in windows) by telling it the maximum res the monitor can support, but I have not found any way to do so.

Considering I am very new to linux I don't know what more to try, so I am asking here for some pointers on how to sort out these little problems.

I know this post is rather long winded so here is a summary of what I need to know.
1/ how do i get multiple displays working?
2/ how do i get it to allow the resolutions the card is capable of?
3/ how can I limit the allowed resolutions to what the monitor can handle?

Any help you could give would be greatly appreciated.

TIA
Terry

---

### Post by TerryArnott on 2009-01-08
Anyone? Any ideas?

---

### Post by AKADAP on 2009-01-09
New to this myself, so I won't be much help.

Open the terminal and type:

man xorg.conf

Read the document. I think that is the place to start.

---

### Post by TerryArnott on 2009-01-09
Thanks, I'll take a look.

T

---

### Post by markbuntu on 2009-01-10
If you are using the radeon or radeon hd driver you can use the System/Preferences/Screen Resolution application to set the screens.

---

### Post by TerryArnott on 2009-01-10
I believe (see original post) that i have the radion drivers installed, but the screen rez options only shows one display and there are no options to set up a second.

Thanks
Terry

---

### Post by 00b00nt00 on 2009-01-10
From my own experience, I can tell you that trying to get a dual screen display up and running with Ubuntu is a real pain in the ***. If you are lucky, you will get the video mirrored, but spanning is another issue.

Try:

1) Uninstalling the radeon driver completely. This will force Ubuntu to use the free 'ati' driver instead. Make sure the displays are connected when you re-start.

2) If that doesn't work, install the radeon driver once more. Make sure displays are connected.

3) Give up and use Windows on the computer you want to use for multiple displays. ;)

---

### Post by TerryArnott on 2009-01-11
** GASP **

You don't mean this is something Windoez can do that linux can't?
I would have thought this would have been a pretty high priority item considering the type of geeks (and I mean no offense referring to my fellow geeks as geeks) that put most of this stuff together MUST have multiple displays.... any self respecting geek does!

3 of my machines here have multi-displays, and 1 is a 4 display monster.

oh well... i guess I'm on my own... kinda.

Thanks for the pointers though.

T

---

### Post by 00b00nt00 on 2009-01-11
Terry, I understand your pain. In my case I wanted to get an LCD projector up and running, and while the log files showed that the projector was visible to the computer, including native resolutions, I was damned if Ubuntu would let me pick anything other than the resolutions that the internal panel would support.

However, I heard from The Register that ATI have recently released their drivers as open source. This could mean that the Ubuntu team may be able to pull the rabbit out of the hat for the next version of Ubuntu.

I love using Ubuntu and really appreciate the work that many geeks (often unpaid) put into it; but please, dual displays are important!

---

