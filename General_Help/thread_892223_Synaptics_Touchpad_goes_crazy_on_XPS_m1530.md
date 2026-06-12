---
title: "Synaptics Touchpad goes crazy on XPS m1530"
date: 2008-08-16
forum: General Help
---

### Post by screamthenrun on 2008-08-16
So, after much searching I know that there is a fix for the touchpad for the m1530, but only w/ the GRUB bootloader.

I'm not exactly new to linux; you could say that I'm returning after a hiatus, and Wubi seemed like a great way to do it.

It would be amazing if only my touchpad worked correctly and didn't jump all around the screen. [Originally it was just really slow, and then I messed with the xorg.conf file and screwed something up.]

:confused: Anyone know how to fix this for Wubi?
[It's my first post so feel free to yell at me if this question has been answered... I truly could not find the answer.]

---

### Post by chrishj82 on 2008-08-17
Hi!

Having the exaxt same problem on the same pc (dell xps 1530. To get rid of the jumping problem just turn SHM config to "on" instead of "true". Then it gets back to the slow mode. Still working on finding a solution to the slow problem. Let me know if you find a solution.

Regards 

Chris

---

### Post by chrishj82 on 2008-08-17
Hi

I finaly found out how to fix this problem. Im new to linux so ill explain this the "idiot" way so other newbies can get it to work..

First i unistalled all the the gsynapicts stuff.. Diddnt to anything to me:)

Then i whent to the terminal

you edit the menu lst file with this:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **i8042.nomux=1**

Then you type this in the terminal
sudo update-grub

then reboot and its all buisness.. 
Thanks to smazero for the solution. Check out [http://ubuntuforums.org/showthread.php?t=737060&page=2](http://ubuntuforums.org/showthread.php?t=737060&page=2) for more info

Thanks

Chris

---

### Post by screamthenrun on 2008-08-17
Thanks a bunch!
I'll go do that right now.

---

