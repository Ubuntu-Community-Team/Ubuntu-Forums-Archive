---
title: "Installing tommorow, any problems to expect on my laptop ?"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by phantom on 2005-05-20
I've been testing Mandrake 2005LE for the last 2 weeks, and it's nice, but really what I was looking for.

I've heard so much about Ubuntu that I need to give it a try.

Will I need to do specials things to get it working on my lappy, on Mandriva it was a pain btw.

Here are my specs:

Acer Ferrari 3200
AMD64 2800+
ATI Radeon 9700 128Mb
768MB Ram
60GB HD Hitachi 7K60
Broadcom 4306 Wifi Card
Broadcom 1GB Nic 56XX
AC97 Sound card
AC97 Apollo winmodem
Bluetooth
Firewire
Synaptics mouse pad
Matchita 4X DVD-R/DVD+R

External Stuff

Pinnacle PCTV USB
ICE Cage 250GB USB2 HD
Bluetooth MS Mouse + Keyboard
Audigy 2NX + Creative 5.1 Speakers
Creative WebCam Live
Sony Cybershot S70 Digicam
Hp Photosmart 7660 Printer
Hp 2400c USB Scanner
Minolta Magicolor 2300W Color Laser Printer
Sony 17" SDM-R71 TFT Monitor

Apps I'll be running:

Cedega 4.3.2 + Point2Play 1.3.3
Crossover Office
OpenOffice
DivX/DVD/MP3/OGG players + Codecs
DVD Ripper
Gnome 2.10 or KDE 3.4 (prefer GNOME as KDE start to look to much as windows, bugwise)
FireFox
VMWare5 (important for work)
All the bells and whistles I can find  :razz: 


Thanks for the input.

---

### Post by sethmahoney on 2005-05-20
[QUOTE=phantom]
Cedega 4.3.2 + Point2Play 1.3.3
Crossover Office
OpenOffice
DivX/DVD/MP3/OGG players + Codecs
DVD Ripper
Gnome 2.10 or KDE 3.4 (prefer GNOME as KDE start to look to much as windows, bugwise)
FireFox
VMWare5 (important for work)
[/QUOTE]

If it worked with Mandrake, the hardware shouldn't be a problem with Ubuntu, but don't quote me on that.  As far as software goes, installing Cedega will be a pain, but its doable, and I've been using it with Ubuntu for a while now without any problems.  The DivX/DVD/MP3 codecs will require you to enable the universe and multiverse repositories, but that's no big deal.  Gnome 2.10 comes with Ubuntu and KDE (I think its 3.4) comes with Kubuntu.  Firefox and OpenOffice are installed by default.  Not sure about VMWare, though.

---

### Post by ssam on 2005-05-20
check everything is ok with the ubuntu live cd.

sometimes you need to put vga=771 as a boot argument on laptops, if the X server wont start.

---

### Post by kleeman on 2005-05-20
The broadcom wifi probably won't work and you will need to use ndiswrapper. There is a nice howto on this site....

---

### Post by phantom on 2005-05-21
using Ndiswrapper ain't an issue, I have to do it now also but the problem with Cedega is something else.

Gaming is what kept me away from Linux 'till I saw cedega in action on another pc.

And I'm not in for dual booting, imo just a waist of diskspace having 2 os on 1 machine.

Oh well, I'll post back in a minute, gonna pop in the Ubuntu cd, we'll see what happens  :-P

---

### Post by waz on 2005-05-22
I tryed to install the 4.10 version on my ferrari 3200, original specs, and got too much trouble installing the amd64-ubuntu. 
First the screen went black, don't remember exactly, but think linux vga=771 fixed that so I could go through the installation.
After finishing the installation x-server would not start and I never figured out how to fix that.
Also the grub did not leave windows as an option, so had to get some help to fix that.
The result, went back to using windows as I did not have time to hack around too much.

If ubuntu, or linux in general wants to compete with windows, there is still a long way to go about the ease of installation.


Strange thing is that the live-cd seems to work fine except that i cannot change the screen resolution to 1400-1050, the left edge is doubled at 1024 pixels wide.


I might give it another shot this summer so I will be interested in hearing how your installation goes, about problems and how you work around them

---

### Post by Arthemys on 2005-05-22
RE: Synaptics Mouse

I've found problems regarding granular control using mine on my ThinkPad R51. I've so far only found how to control speed and sensitivity, nothing like tap to click and scroll zones yet.

---

### Post by sethmahoney on 2005-05-22
[QUOTE=phantom]using Ndiswrapper ain't an issue, I have to do it now also but the problem with Cedega is something else.[/QUOTE]

Cedega is totally doable.  I've just heard that installing the source is difficult.  The easiest way is to find a deb and install it that way (there's a thread floating around here on doing just that).

---

