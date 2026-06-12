---
title: "Problems abound!"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by wrongOne on 2007-10-25
Hey guys, first off i dont know too much about linux at this stage, just freshly made the move so hope it isnt hard to help me :P i will try to do my best to facilitate:

Ok first a workup of what is being used:

Acer Aspire 5600
Intel 945PM Express board (Graphics media accelerator 950)
Ubuntu 7.10

Problem:

This is happening RIGHT after install. I completed install and logged into the system, i noticed the same graphics problem i had with 7.04 (prompting my fresh install), that is that my maximum resolution is listed as 1024x768. I fixed this last time by installing the 915resolution through synaptic packet manager, so i figured it would work again. It did, at first...when i attempted to restart the little bit of text you see in the shutdown process hung and blinked in and out a couple times, then it proceeded to restart. When i booted it back up, as the gui was loading and i was about to be presented with the login screen, multi colored lines distorted a portion of the screen for a moment and then i get a message that ubuntu has been relegated to reduced graphics mode, prompting me to work in that mode or change options.

My "screen and graphics preferences" window shows 3 screens, Screen1(greyed out), Screen2(active and set as default), and Screen2(greyed out)...this is how it came

If i change screen1(default one), to plugnplay generic lcd 1280x800 and press ok it seems as though it works fine, until i restart/log out.....

My graphics card tab displays the following:

Graphics Card (Intel 945)
Driver: i810 - Intel integrated graphics chipsets, in...(cant see the rest? weird)
Video memory: greyed out, but showing "automatic"

Graphics Card (VESA Driver (generic))
Driver: vesa - Generic VESA-compliant video cards
VIdeo memory: greyed out, but showing "automatic"

I dont know if its related, but with compiz and emerald themes installed when i try to enable any level of desktop effects through the system->preferences->appearance, it simply says "cant enable desktop effects"
---

As i said i dont know too much about linux at this stage i simply made the move to 7.10 presuming elimination of some of the problems i was experiencing there, should i simply move back to fiesty if it functioned a little better? Is it just a driver problem? monitor or graphics card driver?

---

### Post by scrooge_74 on 2007-10-25
Probably a driver problem, did you do a sudo dpkg-reconfigure-phigh  xserver-xorg on a terminal?

I have the same graffic card but my laptop only goes as far as 1024x768 (hardware specs)

My advice is that if your were more or less happy in 7.04 stick to it until they iron out a few more issues.  I myself went even further down (Debian Etch), but it just works for me this way.

---

### Post by wrongOne on 2007-10-25
Hrm:

wrongone@wrongbook:~$ sudo dpkg-reconfigure-phigh xserver-xorg
sudo: dpkg-reconfigure-phigh: command not found
wrongone@wrongbook:~$ 

---

I think it might be the command, should be a space before the - in phigh?

wrongone@wrongbook:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071025214433
wrongone@wrongbook:~$ 

but thats how it turns out even with that command

?

And i did a sudo apt-get install xserver-xorg-video-intel, but it said it was up to date

and i downloaded 915resolution and edited via: sudo gedit /etc/default/915resolution

to show:

mode=3c
XRESO=1280
YRESO=800
BIT=32

(got this from [http://www.linlap.com/wiki/Configuring+the+Intel+Graphics+Media+Accelerator+900-950+for+Linux#UbuntuKUbuntuXUbuntuLinux704](http://www.linlap.com/wiki/Configuring+the+Intel+Graphics+Media+Accelerator+900-950+for+Linux#UbuntuKUbuntuXUbuntuLinux704))

but even tho the 915 resolution allows me to set my res to 1280x800, it still claims the computer needs to run in reduced graphics mode after a restart.....so is it the monitor? or driver? or ....?

---

### Post by scrooge_74 on 2007-10-25
I just copy the line from inside my xorg.conf file

 sudo dpkg-reconfigure -phigh xserver-xorg

you can also take out the -phigh part

---

### Post by wrongOne on 2007-10-25
I ran that and let it auto detect, i then set everything to default, but now its as if i have no graphics card or its super slow, even moving windows is chopy, but it did allow me to enable desktop effects and start up without issue :D

---

### Post by wrongOne on 2007-10-25
also everything seems to be working now, i have a totally diff vid driver now and screen, all the desktop effects work, but its just super slow......i set the memory for the vid card to 256000k that cool? i have 1gig of ram.....?

---

### Post by scrooge_74 on 2007-10-26
If you take the desktop effects how fast it is running? I think you are getting close, there is probably some tweak yo need to do to your xorg.conf file

---

### Post by wrongOne on 2007-10-26
It isnt running slowly with just desktop effects enabled, just opening up windows, or moving a scroll bar down in on a web pages causes broken "jumps" down the page....its all chopy, moving windows around is really slow, if i grab the top of a window in ubuntu and pull it down (to 'peek' behind it) it takes about 20sec for the graphic to catch up to the mouse movement.......its like when you are in windows before loading any video drivers;....... what should my xorg file look like?

---

### Post by scrooge_74 on 2007-10-26
Sorry ran out of fresh ideas here, I am not using 7.10 at present time and we so many problems around I think I will stick to my current configs

---

