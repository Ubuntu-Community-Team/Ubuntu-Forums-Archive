---
title: "GPU and ACPI Kernel woes."
date: 2011-01-03
forum: Hardware
---

### Post by Black Magix on 2011-01-03
Ok, its been quite a while since I used linux. So I decided to get back into it but Ive got some problems going on that I cant seem to resolve. Let's start from the beginning. 

Got a new toshiba laptop with two video cards in it, one 4230 for low power mode and a 5650 for high power. Awesome. Lets put linux on it.

Get linux installed and get the latest ati drivers from their website and isntall them.

All my opengl rendering on my desktop breaks and any 3D program is running at REALLY low FPS. Ubuntu is using my low power gpu.

aticonfig --lsa

shows me both video cards and sure enough, the 4200 is listed as the default.

So I did some research and apparently i cant switch GPUS in my 2.6.32-27 kernel. Ok lets update the kernel.

Updated Ubuntu 10.04 to the 2.6.35-22-generic kernel.


Now back to the beginning before I tried to install 10.04, I originall tried isntalling 10.10 That didnt work. I got a blinking cursor and it failed.

When I installed the new kernel I got the same issue on loading. by adding acpi=off to the end of the linux statement in grub, it will boot fine now. However, Ive lost all my functionality of a LOT of my devices. my iphone wont tether anymore, my wireless isnt seeing any new networks or connecting and the devices seem to be polling rather slow....so my two questions


1) How do i get ACPI to work in the newer kernel
2) How do I switch gpu's


Also, Catalyst Control Center doesn't load in linux. Period.


Any help guys?

---

### Post by Ceyx on 2011-01-03
I don't use the proprietary drivers on my ATI AMD Toshiba 300D.
It took me quite a while to get ACPI working properly, and the solution was so simple.  A modified Grub did the trick:

GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi= radeon.modeset=0"

That may take care of ACPI for you.  As for the rest, I don't think I could be of much help....

1/2 of an answer ?  

Ciao

---

### Post by Black Magix on 2011-01-03
I appreciate it and I'd love to try it, where do I enter that line?

---

### Post by Yellow Pasque on 2011-01-03
When you boot the computer, press 'Esc' to access the GRUB menu if one does not show up. Then press 'e' and paste that with the other boot arguments.

---

### Post by Ceyx on 2011-01-03
On my 10.10 system, Grub flashes past way too fast to interrupt it.  However, with a delay inserted once into grub you can easily get to the command line.

The grub file to make the changes in my previous post can be found in /etc/default/grub.

About the 8th line down you will see : GRUB_CMDLINE_LINUX_DEFAULT= yada yada

(the yada yada is mine ).  It is here one can insert the "acpi_osi= "

Note the space after the equal sign, it is important.

Note that you must edit grub using the sudo command, ie in a terminal window : sudo gedit /etc/default/grub and enter in your password.  Also when you are done with the edit you must update grub:  sudo update-grub.  Then reboot to see the effect of your edit.

To use the command line option on my system I increased the timeouts in grub near the top of the file.....it can be easier just to play with the command line.  When your system boots just hit escape within the timeout.

If that acpi option doesn't work for you, do a search for acpi options in grub on the net.  There is a ton of stuff on it.

But of course, keep us posted !

Ciao

---

