---
title: "Odd display issue... hardware problem?"
date: 2010-10-09
forum: Hardware
---

### Post by Astnya on 2010-10-09
I've got this old _[Compaq  Presario SR1610NX]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00472088&dlc=en")_ (though with enough RAM added to put it up to 1  GB) that's been running 32-bit Ubuntu 10.04. One day, out of nowhere,  it developed a strange display problem. The best way to describe it is  the display shifts over to the right, overlapping around to the left  side of the screen, and constantly shakes and vibrates with a steady  oscillating motion. I've got a small (1 MB) video of the screen that I  recorded that I can share; [get it from here](http://img819.imageshack.us/img819/7259/wtf.mp4).

The display doesn't do this all the time: the BIOS screen, part of the  Ubuntu loading screen, and virtual terminals are all displayed without  any problems. The issue only occurs under the GUI. I've swapped out  monitors to make sure that the problem isn't with the monitor, and I  loaded an Ubuntu live environment from a flash drive, still experiencing  the same display problem.

From the above I've gathered that the problem is with the hardware. I  know little about computer hardware, though I've opened the case and  don't see any obvious signs of damage. Does anyone have any advice on  what I can do to diagnose and hopefully solve this?

---

### Post by 23dornot23d on 2010-10-09
You can upload it to Imageshack and then post the direct link on here

[http://imageshack.us/](http://imageshack.us/)

Sounds like it may be the xorg.conf file that might have got changed or removed .....

There may be a backup in the directory

etc/X11/

But if you can upload the video it may help .... just to see what is happening ......

---

### Post by Astnya on 2010-10-09
> **23dornot23d said:**
> You can upload it to Imageshack and then post the direct link on here

[http://imageshack.us/](http://imageshack.us/)
Thanks, I'll update the original post in a sec =)

> Sounds like it may be the xorg.conf file that might have got changed or removed .....

There may be a backup in the directory

etc/X11/

But if you can upload the video it may help .... just to see what is happening ......Are you sure it would be xorg.conf considering that a live environment has the same issue?

---

### Post by 23dornot23d on 2010-10-10
From what I can see ..... its very close to when you adjust a screen wrongly and move the display over to the right .........

Is there any adjustment on the monitor ......

Why its shifted position so far to the right is another question ....... have you used twinview before at all on this computer ......

Almost looks like the horizontal positioning is way out ......... it could be a hardware problem ....

Do you have another computer you can connect to the monitor ...... to see if it does the same thing with that.

Do you have more than one operating system ..... does it do the same with other OS's

Just things you could try to see if it is the monitor at fault ........

Process of elimination ..... I have no quick fix for this .......


But if it looks ok at the start screen ....
> 
The display doesn't do this all the time: the BIOS screen, part of the   Ubuntu loading screen, and virtual terminals are all displayed without   any problems.
Its a graphics driver problem ..... its doing it when it switches from Lower to Higher resolution .... 

so it might be that the **xorg.conf **has been removed or replaced with a different one ..... are there any backup files in

etc/X11/xorg.conf.backup

and does the contents of it look the same as the xorg.conf that is presently there ?



Someone else might be able to help now you have[ this short video]("http://img819.imageshack.us/img819/7259/wtf.mp4") showing what is happening.

---

### Post by Astnya on 2010-10-10
> **23dornot23d said:**
> its doing it when it switches from Lower to Higher resolution .... 
This gave me an idea.

While I was running from a live CD, preparing to partition the drive to install Windows and see if it has the same problem, I changed the resolution to 800x600... and the display went back to normal. When I put it back on 1024x760, it stayed normal.

I booted off the hard drive and switched the resolution, and indeed it worked. I then noticed that the refresh rate was set at the highest level, at 85 Hz... I changed it to 75, set it on 1024x760, and the problem disappeared. Changing it back to 85 Hz caused the screen to screw up again, just like before.

Okay, so it looks like I've found a (potentially temporary) workaround, but I'd still like to know what caused this and whether a different permanent solution is necessary.

For the record, there is no xorg.conf file on that machine, and I have no particular reason to believe there ever was.

---

### Post by 23dornot23d on 2010-10-11
I hope you have the problem sorted now .....  

First place to look is here

[B]System Preference Monitors
[/B]
Sometimes its better to have a xorg.conf ....which can be created ..... it can keep all the unusual user scrren and monitor settings and seems to override the automatic ones.

It always used to take priority ..... I am not 100% sure if this is still true as a lot of work
has been going on with Graphics and Drivers over the past 6 months.

A good starting place for the [xorg.conf]("http://en.wikipedia.org/wiki/Xorg.conf") I used to use this a lot before, but it seems less and less needed nowadays except it is useful for some problems.

---

