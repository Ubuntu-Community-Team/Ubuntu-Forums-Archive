---
title: "ati driver! error: Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.c"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by Amendment44 on 2008-03-05
Im running a saphire x1550 512meg ati radeon card. 
ubuntu 7.10 gutsy 


I installed the radeon drivers from the ubuntu repository.

when i'm in the terminal I get the following. 

sudo aticonfig

...... menu options come up like its installed it right.

then anytime i try an option like 

matt@matt-desktop:~$ sudo aticonfig --initial=dual-head --screen-layout=above

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

and when I go directly to the restricted driver tab. it shows the ati driver as there. and surprisingly in use.... however the box isn't check and when i try to

I get a pop up with the following error. 

"Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist."

I know the file is there, and is not invalid

---

### Post by arashiko28 on 2008-03-05
why didn't you tried envy first?
restart, if you have double boot choose the recovery mode, if not, press esc before the GRUB counting gets to 0, choose restore or recovery mode (you'll only see one) and type:> dpkg-reconfigure xserver-xorg
go to devices and search for the ATI drivers and change the word "ati" for "Vesa", save it and get out. This will give you time to install what you need.

In terminal: sudo nano /etc/X11/xorg.conf

Try envy, I installed gutsy for a friend with ati and envy worked great, also on my family computer worked, I have never had that kind of problems.

---

