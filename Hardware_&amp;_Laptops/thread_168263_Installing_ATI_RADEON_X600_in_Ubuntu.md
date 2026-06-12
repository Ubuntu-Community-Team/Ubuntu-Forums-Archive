---
title: "Installing ATI RADEON X600 in Ubuntu"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by metjoo on 2006-04-30
First of all, I think this "tutorial" will work for almost every RADEON card, but anyway, trust me, it's worth to try it.

It's been a few days since I've finally managed myself to have the graphic card working..

So after browsing the net for hours and wasting a lot of time I've got plenty annotations (surely form just one site, but you know it ends up mixed a lot). So I don't know exactly who I must give the credits for.

But, anyway, here are the steps I followed to have this *** card to work:

**(STEP 1)** Once the OS is installed you will see the Graphic Card crash. You will be forced to work in the command line. Don't panic, just type your username and password and follow these steps.

First of all, I would login as root, that's very simple in Ubuntu, just type:

```
sudo -s
```

And then retype the same password you did in the user login.

Now type the follow sentences:

```
cd /etc/X11
vim xorg.conf
```

That will open the VIM editor, its use is far more simple than it seems.
The Insert key will allow you to enter the edit mode, you can exit this mode by pressing Esc.
To exit VIM saving the changes you must type (out of the Edit mode)
```
:x
```
To exit VIM without saving the changes just type
```
:q
```

Now in the xorg.conf file we should change just one thing. Find the Device Section, it will look something like this:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

Ok, add a line at the end to have it as:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "noaccel"
EndSection
```

Exit the edit mode (Esc) and exit VIM saving the changes.

Now type

```
reboot
```

in the command line to reboot the system.

We have managed to have the card almost working, at least you will enter the graphic mode in ubuntu and you will be able to install and set the proper drivers.

**(STEP 2)** Once the system loads, you will access the graphical environment of Ubuntu. Just type your username and pasword in the login window and enter Ubuntu.
Open a Terminal window (Applications -> Accesories -> Terminal), and login as root again:

```
sudo -s
```

Now write the following lines:

```
sudo apt-get update
sudo apt-cache search fglrx
sudo apt-get install xorg-driver-fglrx
```

This will install the new downloaded driver.
Now let's edit again the xorg.conf, type:

```
vim /etc/X11/xorg.conf
```

Change the Device section that now reads:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "noaccel"
EndSection
```

to

```

Section "Device"
	Identifier	 "ATI Technologies, Inc. Radeon Mobility X600 (M24)"
	Driver		 "fglr"   #"radeon"   #"ati"
	BusID		"PCI:1:0:0"
	#Option	      "VideoOverlay"		      "on"
	#Option	      "OpenGLOverlay"               "off"
	#Option	      "UseInternalAGPGART"	"no"
	#Option	      "DynamicClocks"		    "on"
EndSection

```

Reboot the system, and you're done!
Ufff!


Hope it works for the rest of us.
Enjoy and Share!

---

### Post by jazzmuzik on 2006-04-30
What is the rpm for?

---

### Post by metjoo on 2006-04-30
Sorry, it was a mistake. I have edited the post.

I mixed my annotations in paper :-# 

Thanks!

---

### Post by chicken101 on 2006-04-30
Of course, you could always just install the frglx drivers- they seem to work fine.

---

