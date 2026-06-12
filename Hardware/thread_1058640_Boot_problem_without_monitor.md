---
title: "Boot problem without monitor"
date: 2009-02-03
forum: Hardware
---

### Post by narusas on 2009-02-03
I install ubuntu minimal 8.10 on AMD Geode( Alix 1)


I work well when monitor attached. 

But I detach monitor(VGA not DVI), and reboot it, it does not boot. 

After grub, 

"""
Boot from (hd0,0) ext3  85c44896...(maybe UUID)
Starting up ...
"""

and halted.  no more actions. 
(I check it to attach monitor after 1 minutes after reboot)


4~5 minutes after attached monitor, it resume boot sequnce. 
(If no monitor attached, no resume)




so I change /boot/grub/menu.lst and append kernel line

vga=0F00  or vga=scan or vga=ask or etc..

but all trial failed.

---

### Post by DefineByte on 2009-03-18
There's now a beta BIOS out on the [PC Engines site](http://www.pcengines.ch/alix1d.htm) that fixes the problem.

If you're not comfortable with the beta tag you can either compile the kernel with 'CONFIG_FIRMWARE_EDID=n' set or insert a paper clip (or some other conductive wire) between pins 6 and 12 on the VGA connector on the board.

---

