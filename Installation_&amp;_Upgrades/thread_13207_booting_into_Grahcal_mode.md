---
title: "booting into Grahcal mode"
date: 2005-01-29
forum: Installation &amp; Upgrades
---

### Post by googlinggoogler on 2005-01-29
Hiya,

Gotta say first off kudos to who ever made the installer for ubuntu, it took me about 25minutes, was amazing - I remember when I first installed mandrake in the 90's it took me 5 or 6hrs.

anyway heres my problem, I boot ubuntu and it boots into text mode. I obviously arent a diehard user as I want to boot into a graphical mode (gnome).

Ive tried startx, but this doesnt work - indeed it doesnt even appear to be in /usr/X11R6, so i tried to edit /etc/inittab. I wasnt really sure what changes to make so I decided not to make any and ask here what the solution is. obviously I want to boot into state 5, but im not sure how to achieve this.

anyone help??

Cheers

dave

---

### Post by DJ_Max on 2005-01-29
When you run startx, what errors do you get?

---

### Post by googlinggoogler on 2005-01-29
Thats the thing, I dont get any errors - i get the usual "startx: command not found" , errors I can deal with, they just need logical thinking, when theres nothing there to investigate then I get confused!

So I was woundering whether X hadnt installed, but then theres the /X11R6 folder so i assume it must of to some extent, although there wasnt much in that folder, like i seem to remember the being on my last system.

and the inittab file just looks screwed up, and talks about the serial and modem I think, although I cant confirm that at the moment

cheers

---

### Post by az on 2005-01-29
Did you by chance install with the custom option?

That sure takes a lot less time than a full install!


try 
dpkg -l |grep xserver

if you have one, try

sudo dpkg-reconfigure xserver-xfree86

---

### Post by googlinggoogler on 2005-01-30
umm well i didnt do anything special although On inserting the CD and booting the system hung on the bit where it initialises the framebuffer.

so I tried the changing the boot parameters -

linux debian-installer/framebuffer=false

but this doesnt allow me to move forward in the install, 

so I tried the floppy=thinkpad option seen as im running a IBM thinkpad r40e,  which doesnt work.

So the final and best solution that allows me to install a system is -

linux acpi=off vga=normal

and that works, although not everytime...

any suggestions in how to get an install working smoothly?

cheers

Dave

---

