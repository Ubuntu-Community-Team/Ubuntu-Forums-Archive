---
title: "Beginner Help xserver-xorg"
date: 2008-02-14
forum: Hardware &amp; Laptops
---

### Post by franco81 on 2008-02-14
I need a little absolute beginner help here please. 

Hardware:
Toshiba Satellite P200-1EE
Intel Core 2 Duo 1.50GHz
2048MB RAM
ATI Mobility Radeon HD2600

Currently I have a dual boot system with Vista loaded too and about 20 gigs partioned to Ubuntu. 

All I really want from Ubuntu is a working desktop environment to develop websites etc. 
The problem I was having was poor resolution and occassionally the viewable portion of the screen was squeezed into a box in the middle of the actual screen.

I have had difficulties getting the graphics card to work properly, I followed a bunch of tutorials for getting fancy desktop environments working etc. but none really worked, in the process I installed a bunch of xserver stuff and changed the xorg.conf file.

Now when I boot up I get a black screen which starts resolving into a bit of a cloud like the tan background is starting to come through. I have booted into safe mode and taken xorg.conf back to a failsafe backup but no luck. I have also tried recreating the xorg.conf with 
dpkg-reconfigure -phigh xserver-xorg
But after the resolution screen it just dies and although it looks like xorg has been updated (although no resolution in there) I still get the cloudy screen.

Any help appreciated. At this point I would like to roll back to how my ubuntu was installed in the first place and then start afresh on this problem.

Cheers,
Frank.

---

### Post by erginemr on 2008-02-14
To begin with:

1- I didn't quite understand this "cloudy screen". Are the Compiz desktop effects currently enabled? Does disabling it make any difference?

2- What is the natural resolution of your laptop? (say, the one in Windows)

3- Can you please also try: "sudo dpkg-rexonfigure xserver-xorg"? It will ask you several questions to configure your graphics card, and also the resolutions you would like to have?

4- You may try booting form a Live CD and if everything works as you desired, copy its /etc/X11/xorg.conf file to a USB drve for a partial / full replacement with our original config file.

5- If none of the above works, then can you please post your "/etc/X11/xorg.conf" file here?

Take Care,

Emrah

---

### Post by franco81 on 2008-02-14
A few other details before I get home and try what you suggest - thanks for the help.

I was playing around with compiz yes, they are probably enabled but I would like to disable them to debug so if anyone knows how to do that the command would be much appreciated.

sudo dpkg-reconfigure xserver-xorg
I did a version of this command from memory it was:
sudo dpkg-rexonfigure -phigh xserver-xorg

This started going through the graphical interface for setting up the details, but on the resolution screen, no matter which resolution I picked it seemed to crash out about there and return me to the command line. Sometimes it gave the error that it was worried about overwriting my xorg.conf file.

Cheers,
Frank.

---

### Post by erginemr on 2008-02-14
The command to disable compiz temporarily (for that session) is Alt+F2, then "metacity --replace".

Without the "-phigh" parameter, you are at the captain's seat, because the script will ask you which driver and resolutions to use.

---

### Post by franco81 on 2008-02-14
Great, thanks, will let you know how I get on.

Cheers,
Frank.

---

