---
title: "Change Screen Size for Console Mode/Terminal Mode"
date: 2008-08-28
forum: General Help
---

### Post by Finog on 2008-08-28
I decided to give xubuntu a try without the GUI and so disabled "gmd" on the boot-list (use "startx" in the terminal to get back to the GUI). That worked well, but the resulting console-only/terminal-only mode is using only about half of the available screen real estate (a small rectangle in the middle of the LCD). I'd like to know how to change the screen size/screen resolution for this mode, any suggestions?

---

### Post by Nythain on 2008-08-28
you need to edit your /boot/grub/menu.lst file and make a couple appropriate changes.

first, figure otu what vga=XXX mode you want, thsi will determin resolution, you can find a chart easily enough online anywhere by googling "grub resolution chart" or something similar.

then, you would edit the above mentioned grub file, and look for a line that looks like
#defoptions=quiet splash
though quiet and splash might not be there, who knows... but add right after it, vga=XXX so it looks like
#defoptions=quiet splash vga=XXX

now you could stop here, save the file, and sudo update-grub, wich will create a new menu.lst using the automagic settings, including the vga=XXX that you added.

reboot, and voila, hopefully a much more readable TTY

---

