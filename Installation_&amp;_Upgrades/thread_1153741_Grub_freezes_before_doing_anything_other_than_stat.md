---
title: "Grub freezes before doing anything other than stating GRUB"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Ocat on 2009-05-09
I searched this forum but haven't been able to find anything exactly like it. I re-installed Grub (There are a couple of posts on this forum explaining it) but as far as I can tell that didn't help (It still does the same thing). The installation is from a 9.04 amd64 cd.    As always things start with the first screen where you can push f2 to get into the bios setup. Then a second screen comes up with more information about the computer. On a windows pc this screen clears and windows boots, but here it keeps this screen and adds just &quot;GRUB&quot; at the left bottom. I can't type anything in it, and it does not seem to do anything (I have waited a couple of minutes a couple of times)  I know that Grub has the correct information about which HD to use, and it seems to have the correct other files and info (from what I gathered from the various posts about (re-)instaling Grub) but perhaps there is still a problem there?    Does anyone have any idea?

---

### Post by dandnsmith on 2009-05-09
You get *GRUB*, and then nothing more, when the bootloader first stage has been invoked, but then something is missing (but it cannot get far enough along to issue an error message).

If you are unable to type anything in, then
*either*the keyboard isn't 'detected' (as in usb keyboard)
*or* the boot files aren't properly installed.

what may be helpful is to download and run [this script](https://sourceforge.net/projects/bootinfoscript/) and post the content. It will show some of what is available, and, we hope, what is missing. You may need to use a live CD to get to run this.

---

### Post by Ocat on 2009-05-09
Thank you for the suggestion. However, that script did not work. I do not recall the error exactly, but it complained about a while loop around line 126, it said it didn't recognize j++ (just a part of the while-loop) and it kept saying that error (it was apparently still in this while-loop).

I am however posting from that installation right now. I had no succes with re-installing Grub from the live-cd but I remembered an old linux installation on the same machine. I tried it from that installation, with the grub-install command, with the root directory and install device for the fresh installation and this time it stuck.

So in fact I do not have much of a hint for others with the same problem, considering most won't have an old linux installation on the same pc.

---

### Post by dandnsmith on 2009-05-09
Good to hear it's fixed.
When I had the same problem, I managed to fix it with a re-install of grub - but that was brute force and ignorance, before I became acquainted with ubuntu and these fora.

---

