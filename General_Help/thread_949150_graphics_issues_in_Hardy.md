---
title: "graphics issues in Hardy"
date: 2008-10-15
forum: General Help
---

### Post by lkb3 on 2008-10-15
I've just installed Hardy in the last few weeks.  

My graphics don't seem right - colors are off, there is a blank bar on the edge of the monitor where no display appears (meaning - if I use the controls on the monitor to expand the picture across the whole glass, it just resets next time I boot up), and I can't do anything with the resolution - if I try, the display starts to run past, like the wheels on a slot machine, and the only way to stop is is by rebooting. 

Is it possible I've got a graphics driver issue? Should I try a new driver? if so, how?
I have a 4 or 5 year old gateway with an intel motherboard with integrated graphics, if that matters.

---

### Post by Spaceman9 on 2008-10-15
Hold down the Alt and F2 keys. That will bring up the run Application window. Type or copy and paste this code into that window and hit Enter
 
gksu displayconfig-gtk

A window will open. Type in your user password and hit Enter. The Screen and Graphics Preferences window will open. you should be able to find your video card and monitor there and set up everything.

If you don't know what graphics chip you have in your motherboard run this code in a terminal

sudo lshw -C display

---

### Post by lkb3 on 2008-10-15
Thanks, Spaceman.  That helped me get it fixed.

---

### Post by Spaceman9 on 2008-10-16
Excellent! Glad I could help.

---

### Post by LyleCanada on 2008-10-18
Thanks so much Spaceman9. Have been fiddling trying to figure this out since going to ubuntu a week ago. I now have plenty of screen resolution options that work. Good job.

---

### Post by LyleCanada on 2008-10-18
Well, except that now when I log off, then the "log in" screen is not centered correctly.The Ubuntu logo is mostly off the screen, the "Options" choice is missing, and depending on the resolution I use, the user name box is not visible. I have to then reboot to get in again.

---

### Post by Spaceman9 on 2008-10-19
Because you're new to Ubuntu you should install StartUp-Manager from Synaptic. With StartUp-Manager you can set up boot options for timeout, Default operating system(the kernel you boot by default) Display Resolution and Color Depth, Bootloarder menu colors, Bootloader themes,
Usplash themes, Bootloader password and make a GRUB floppy disk.

In StartUp-Manager goto Display>Resolution:. Make sure the Resolution is 640x480 and 8 bit color depth. That should take care of it if you have a CRT monitor. If you have a digital monitor you'll need to look at the manual to find controls to adjust the screen.

It's a good idea to makes a GRUB floopy disk right after you install and update Ubuntu. That way if you can't boot Ubuntu from your hard drive you can boot it from the GRUB floppy disk.

Also install OGRUBEditor. That lets you edit the menu.lst file from a GUI so you don't have to muck about with doing it by hand.

Also, if you need to change file or folder permissions you can hold down the Alt and F2 keys. That will bring up the run Application window. Type or copy and paste this code into that window and hit Enter

gksudo nautilus

That will give you the Nautilus file browser in root mode. You can change permissions with it by right clicking on a file or folder and click Properties.

---

