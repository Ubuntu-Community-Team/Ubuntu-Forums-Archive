---
title: "Screen resolution on Advent KN1 Laptop"
date: 2007-08-17
forum: Hardware &amp; Laptops
---

### Post by frankos44 on 2007-08-17
I have a Advent Laptop model KN1. 
Chipset Intel 915GM

I believe the graphics is NVIDIA but not sure about that because there is apparently there is more than one version of the KN1.

The screen looks like a 16:10 aspect ratio (wide) and I assume it has a native resolution would be 1280x800

How do i change the resolution from 1024x768 to 1280x800 on Feisty?

---

### Post by dougfractal on 2007-08-17
lspci -nn

this is probably a refresh issue
sudo gedit /etc/X11/xorg.conf
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	31.5-80
	Vertrefresh	56-85
EndSection


and just add "1280 x 800" to the other resolution choices in xorg.conf

---

### Post by frankos44 on 2007-08-17
Thanks for responding.
I did the changes, saved the file and did a crtl-alt-backspace.
When i try to change the screen resolution only the standard 640x480, 800x600 and 1024x768 modes are available as before. Is there some other command i need to issue first?
Frankos

---

### Post by frankos44 on 2007-08-17
I have fixed it by installing a patch as follows:

sudo apt-get install 915resolution

I typed crtl-alt-backspace.

After logging in, I selected 1280x800 and off it went.

Needless to say I installed some nice fonts:

sudo apt-get install msttcorefonts
wget [http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz](http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz)
sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

Looks cool now!!!

---

