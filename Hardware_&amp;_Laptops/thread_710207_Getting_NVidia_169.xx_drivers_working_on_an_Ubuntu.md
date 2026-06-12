---
title: "Getting NVidia 169.xx drivers working on an Ubuntu laptop"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by enbuyukfener on 2008-02-28
I am trying to get NVidia 169.xx drivers installed on a Vostro 1500 laptop with Ubuntu however I am having problems no matter which option I take.

I try to get a clean slate before doing each.

Installing nvidia-glx-new leads to a garbled X with white noise all over the screen and some purple vertical lines 2/3rds across the screen.

Installing with the binary packages from the NVidia site leads to the same as above.

I also make sure X and processes associated with it are off, make sure xorg.conf is configured properly, I even went and got the custom EDIDs and applied them through xorg.conf as suggested by someone answering a similar problem. I have also looked at several similar questions posted on these forums and elsewhere and tried to combine bits and pieces but nothing has yielded.

Some variations lead to the system reverting to vesa and with that, 640x480, or the screen is rearranged like a jigsaw, I can actually move the mouse and have it come across the other side like playing snake on mobile phones...

I can settle with the old drivers found in nvidia-glx or 10x.xx drivers but I'd prefer to make better use of my hardware considering I often run in dual monitor mode and play the occasional games among other graphic intensive tasks.

Any suggestions?

Maybe I'll try doing it with [envy]("http://albertomilone.com/nvidia_scripts1.html") even though it doesn't officially support hardy yet.

---

### Post by reidkaufmann on 2008-02-28
I've got the Vostro 1500 (with nvidia 8600) too and see the same problem.  I had gutsy and upgraded to a new kernel to fix sound, but couldn't get the latest drivers from Nvidia working (because of this problem).  So I tried upgrading to Hardy Heron, only to find that I'm running into the same problem.  It's so frustrating -- Ubuntu is great on my desktop, but a curse on my notebook.

---

### Post by enbuyukfener on 2008-02-28
If you decide to downgrade, which I am considering, I can refer you to the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449") which I used to solve sound without upgrading the kernel.

At least finding someone else with the same problem has convinced me to try envy (and possibly mess things up further!). Or I could be patient and wait for EnvyNG :D

I'll let you know how it goes.

---

### Post by enbuyukfener on 2008-03-05
EnvyNG was released earlier than I expected so I got this solved a few days ago using it.

---

