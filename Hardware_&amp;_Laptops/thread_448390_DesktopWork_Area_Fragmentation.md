---
title: "Desktop/Work Area Fragmentation"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by kpfuser on 2007-05-19
After starting the Ubuntu 7.04 CD in a Compaq Presario 1500, the work surface (screen) became fragmented as follows: First a horizontal line appeared near the bottom leaving about 75% of the total screen area above it. Then the window that appeared covered about 75% (from the left edge) of the area above the horizontal line (leaving the area near the right edge of the screen black) and replicated itself (as space availability allows) below the line . The reduced work area works ok and all activity (mouse movements, etc.) that takes place in the upper (fully visible) panel are replicated in the lower (partially visible, due to space limitations) panel. Any ideas as to how can this be corrected?

---

### Post by uconvert on 2007-06-06
I almost abandoned 7.04 in favor of 6.06LTS (I have several machines running different versions) for that very reason, but needed to show my Dell only cousin that my Compaq could do anything his Dell could do.
Here's the basic fix:
Do the install --you'll have a split screen, but you can still enter the terminal from the top section.
in terminal mode type:
sudo dpkg-reconfigure xserver-xorg

a screen pops asking to autodetect video card (y), then its basically a prompt style reconfiguration. Your video card has 32MB memory dedicated, I have left the entry blank and it works fine, autodetect the monitor (generic) and set resolution to 1024x768 in the medium mode. That should do it, I have tried to use the ati-glx drivers to no avail, but I have good 3D and a cubed desktop - way cool:)

---

### Post by kpfuser on 2007-06-07
Thank you very much indeed! It is good to know that there is a resolution to the 'split windows' problem. But how did you discover this thread that by now must have been relegated far too deep under the heap of more recent ones? Amazing! Btw, are there supposed to be empty spaces before -reconfigure and -xorg in the command you mentioned?

---

### Post by uconvert on 2007-06-08
Hours of Googling -- I have a Desktop PC with an invidia video card and needed to get the most out of it, then tried the ati method and killed the installation, so I reinstalled & backed my way into this work-around.

The command is sudo (space) dpkg-xserver (space) xserver-xorg

Hope that helps!

---

