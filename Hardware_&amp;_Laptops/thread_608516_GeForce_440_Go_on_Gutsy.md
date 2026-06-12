---
title: "GeForce 440 Go on Gutsy"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by bigstoo on 2007-11-10
I've just installed Gutsy on my Dell Latitude C840. It's my first foray into Linux, so bear with me.

When I try to switch on the Restricted Driver (nvidia) for the graphics card, X windows will no longer run. I just get a blank, black screen. Something seems to be running as the sound still works.

If I revert back to the old driver (nv) it works fine.

I have looked at /var/log/Xorg.0.log for both drivers, and I can't see any reason why it doesn't work. There are no error messages in either.

Has anybody else come across this problem?

I will post my full Xorg.0.log and Xorg.conf when I have more time.

---

### Post by biggyfred on 2007-11-10
I can't answer your question, but I can relay that my Geforce 440 Go runs magnificently with Feisty and the restricted driver. I haven't tried Gutsy on that machine. 

Good luck.

---

### Post by bigstoo on 2007-11-11
That's good to know. At least I have something to aim for.

I've looked over the log file again, and I think I've got to the bottom of it.
It is trying to use display "CRT-1", which would be a screen plugged into the VGA port (which, of course doesn't exist). I want it to use DFP-1 - the in-built flat panel.

Any ideas how to force it to use the flat panel? I assume I just have to put something in xorg.conf. Any change someone could post a working one for the Latitude C840 running the nvidia driver?

I've tried pressing the Fn+F8 button, but it doesn't switch displays.

---

### Post by bigstoo on 2007-11-12
Now then,

I've managed to get the display up now. Elsewhere on this forum there is details of an option to add to make it use the flat panel.

Now I have a new problem. There is chunk of screen, about 2 inches wide on the right hand side that is all multi-coloured and garbled. Has anyone else seen this? It doesn't happen with the "nv" open source driver, just the "nvidia" one.

Strangely, I get **exactly** the same problem in Windows XP if I use the latest Nvidia driver there. If I use the one supplied by Dell, I have no problem.

The problem is detailed more clearly [here]("http://www.laptopvideo2go.com/forum/index.php?showtopic=6686")

Does anyone have an older restricted driver? Is the one supplied with Feisty different from the Gutsy one? Would anyone mind sending me it?

---

### Post by LostJot on 2007-11-12
> **bigstoo said:**
> Now then,

I've managed to get the display up now. Elsewhere on this forum there is details of an option to add to make it use the flat panel.

Now I have a new problem. There is chunk of screen, about 2 inches wide on the right hand side that is all multi-coloured and garbled. Has anyone else seen this? It doesn't happen with the "nv" open source driver, just the "nvidia" one.

Strangely, I get **exactly** the same problem in Windows XP if I use the latest Nvidia driver there. If I use the one supplied by Dell, I have no problem.

The problem is detailed more clearly [here]("http://www.laptopvideo2go.com/forum/index.php?showtopic=6686")

Does anyone have an older restricted driver? Is the one supplied with Feisty different from the Gutsy one? Would anyone mind sending me it?

Not sure if this will solve your problem, but it does mention your card. 

[http://albertomilone.com/latest_nvidia_udsf_feisty.html](http://albertomilone.com/latest_nvidia_udsf_feisty.html)

Go to the notes section, and note 7 has specific instructions for that card. 

I know it's feisty but it might still be valid.

---

### Post by bigstoo on 2007-11-12
Aha!

I think you may just have it.
It would seem that the problem is to do with the flat panel incorrectly declaring its settings. By the looks of it there are some optional flags to override it.

I'm quitely confident this will fix it.

I'll give it a go when I get home from work. Cheers

---

### Post by bigstoo on 2007-11-13
Close, but not quite. It made a difference but unfortunately it made the screen *even smaller*.
I'm so close I can taste it.

---

### Post by bigstoo on 2007-11-14
I finally got it working.

The problem my particular Latitude had was that it has the Samsung UXGA screen. Aparently, this screen does not properly (or at all?) sent the correct EDID information to the new nvidia driver. This means that the driver falls back to it's own Nvidia Flat Panel screen settings. I got over it by using the "CustomEDID" option to force it to use an EDID that I wanted.

---

### Post by angeljr on 2007-11-16
I've had the same issue, can you post details on how you resolved it?  I'm am VERY new to Linux and would love to be able to mess around with it!

---

### Post by pkiula on 2008-03-16
Is there any resolution for this--if you resolved it can you please share? I have the same issue now but had to resort to the old "nv" driver. But the performance of windows etc with that default driver is horrid.

---

### Post by fattmox on 2008-03-17
Could you please post your xorg.conf?

---

