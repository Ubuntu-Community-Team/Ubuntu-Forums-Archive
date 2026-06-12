---
title: "Xubuntu freezes after logo during boot"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by TheFoe92 on 2009-09-01
I installed a fresh copy of Xubuntu just a few days ago. In verbose mode, it appears that it freezes right as it tries to start GNOME Display Manager. Another two lines appear under that (I can't read it because they roll up so fast), and the screen goes black. I have tried many things, none of which have worked. It's an old Toshiba Satellite 1800 laptop that was running XP before I tried installing Xubuntu. It has ~248MB RAM and an 800MHz CPU. Personally, I think it should at least boot into the GUI with those specs. Moving on... I can somewhat boot into non-GUI recovery mode (I can start a shell, but that's about it), so I was able to try a few things like stopping and restarting GDM, using startx, and reconfiguring the xserver. Here is a copy of my current xorg.conf file (I had to type it out by hand on another computer)

```

Secion "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

section "InputDevice"
	Identifier	"ConfiguredMouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/pasux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section	"Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

I don't know what other pieces of info I could provide. If you need anything, I'll respond as soon as I can. Thanks in advance!

---

### Post by sanderd17 on 2009-09-01
Hi, do you have an ati graphical card? And when it freezes do you see colored bars and a deformed ubuntu logo and just before it freezes do you see red ellipses around the ubuntu logo?

in that case i can help you with ease.

---

### Post by sanderd17 on 2009-09-02
> 
The problem is that the ATI restricted drivers do not yet support the new xorg server used in Jaunty. You can return your system to the open source drivers, but wont be able to install the restricted drivers until ATI release an updated version.
This is not restricted to ATI, as Nvidia has similar problems.
The price you pay for having the latest versions of software (xorg in this case), is that sometimes there is a lag between updated drivers...such i think is the case here.

To get your system back to usable try this.

Press ctrl+alt+f2 or ctrl+alt+f1 and login with your user and password, then type:

sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg

sudo aticonfig --initial -f
sudo reboot


This was my solution, I found it in [http://forums.whirlpool.net.au/forum...m/1192180.html ]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/1192180.html"). You know how to get in shell so that isn't a problem and you don't have to type the "sudo"s because the shell is already in root mode. 

I've encountered the problem 3 times, the first time I did a complete reïnstall (I wanted te swich to ext4 anyway), the second time I found this code after a few days and the third time I knew I had written down the code so in a few seconds it was ok.

Just remember, if you do certain system checks or so it could change the settings back and you could have the same problem again so don't lose the code.

---

### Post by TheFoe92 on 2009-09-03
Thanks for the input! I don't remember what kind of video card I have, and no, I do not see colors and shapes. All that happens is that, after a certain point during startup, the screen goes black and freezes. Nothing else happens. In verbose mode, it appears to freeze when it tries to start GNOME Desktop Manager. I tried what you suggested, but unfortunately, it doesn't work. Since I am in a recovery mode shell, I cannot set up my internet connection. The computer is directly connected through Ethernet. Is there any way to get apt-get working? Or are there other ways to fix this?

EDIT: Every time I try using startx or /etc/init.d/gdm start, the computer freezes. I've used all Ubuntus before, but this is way out of my league. Please help!

---

### Post by TheFoe92 on 2009-09-05
Ok, so I got my internet connection working and I did all you told me up there; however, the last command didn't do much at all. It just gave me what seems to be an error message. It reads:

```

Data incomplete in file /etc/X11/xorg.conf
     Device section "Configured Video Device" must have a Driver line. 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Data incomplete in file /etc/X11/xorg.conf
     Device section "Configured Video Device" must have a Driver line.
Segmentation fault

```

---

### Post by Perturbed Penguin on 2009-12-23
@ sanderd17

I am experiencing what you described with the boot logo, it has the green bars of death but no ellipses as far as I can tell. I have an Nvidia 7900gs though so do you have any suggestions for how I might fix my system since mine is not an ATI video card? Thanks in advance.

Here is an image of the boot logo, hopefully I reduced the image size enough this time:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=140951&stc=1&d=1261585226[/IMG]

---

### Post by sanderd17 on 2009-12-23
```

apt-get update
apt-get install xorg-driver-fglrx
dpkg-reconfigure xserver-xorg

aticonfig --initial -f
reboot

```

This was the code I had to type in the terminal mode. Since it uses aticonfig I don't think it would work for your problem. But maybe you can use the first part of the code and search the internet for the other part.

I' haven't encounterred the problem since ubuntu 9.10. So maybe, try ubuntu 9.10 if you don't use that version

grtz sander

---

### Post by Perturbed Penguin on 2009-12-24
I could be mistaken but the problem I am having appears to be a hardware issue. I think this because I booted into the live cd and even using the live cd I was having similar graphical oddities(green boxes everywhere), I have run this live cd in the past on my machine namely for installing and have previously had no such issues. I also tried booting my comp after temporarily replacing my graphics card with my brother's and it booted as usual without any hint of an issue. Please let me know if you think this could be just a driver incompatibility with my specific card but the fact that the live cd was exhibiting the same characteristics leads me to believe that my card is shot.

I am in fact currently running Karmic and my graphics card, if it means anything, is an Nvidia 7900gs - my bro's is an 8800gt.

I am going to go ahead and look into getting a new card, I am pretty convinced that is the issue, but if anyone has any other ideas please do tell. Thanks a bunch for the assistance! ;)

---

