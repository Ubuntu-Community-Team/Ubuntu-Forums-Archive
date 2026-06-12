---
title: "HELP PLEASE NVIDIA driver wrong"
date: 2008-10-24
forum: General Help
---

### Post by mistertee on 2008-10-24
Hi,

For some reason my X server crashed this morning and it said it didn't recognize my video card and monitor.  Unfortunately I was in a rush trying to get out to work so when it came up with a little wizard I selected the wrong NVIDIA driver and now I'm having lots of problems.  Anyone know how to get that wizard back or how I can hardcode the correct driver in?  In my xorg.conf it shows 
Section "device" #  
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:5:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"

My card is a Quadro FX

Thanks!

---

### Post by doas777 on 2008-10-24
try replacing "nv" with "nvidia" . I'm not sure that will work for so old a card, but thats what you do for newer ones.

good luck,
franklin

---

### Post by balaknair on 2008-10-24
Hi.
You could try using the Screens and Graphics option(System Menu>Administration>Screens and Graphics) to get a little wizard like app

 or 

Envy if you want to get the latest proprietary drivers for your card
([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) to enable the relevant drivers.

or use the CLI (sudo dpkg-reconfigure xserver-xorg)
I wouldn't recommend using the CLI if you're not sure about what you're doing. Use it only if nothing else works or you lose the GUI completely(Xserver doesn't start at all)

---

### Post by mistertee on 2008-10-25
OK, so its getting a little better.  I used a tutorial to install the driver from NVIDIA which got me back into the GUI, but I'm still having some weird behavior.  When I use my login my CPUs are heavily tasked for about 5 minutes.  During that time my setup looks ok.  My desktop is setup with Mac4Lin, so I use Emerald for the window borders and the Mac4Lin theme with Compiz effects, and I use Cairo Dock.  After that 5 minute period the window border disappears, Cairo Dock gets really wonky (when it comes up the bottom portion of the screen is black) and I can't type in any window.  I'm using my wife's login for this (she doesn't use any special theme/Emerald/compiz). Any thoughts on what's going on with that?  

Thanks for all the help!

---

