---
title: "Ubuntu isn't recognizing my video card"
date: 2008-11-11
forum: Hardware
---

### Post by kira. on 2008-11-11
I went to turn on my computer, and a prompt came up telling me that Ubuntu was going to run in "low graphics mode", because it couldn't seem to recognize my nvidia video card. When I tried to check my nvidia-settings, it gave me a box with the following:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

When I wrote "nvidia-xconfig" into the terminal, it told me:

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

I'm guessing that for some reason I'm missing the drivers, but I'm not really sure..

Any ideas?

---

### Post by IceBadger on 2008-11-11
My guess is that you do not have the correct permissions as a non-super user.  Did you try "**sudo nvidia-xconfig**"?  Was this the result of an update, an upgrade to a newer version of Ubuntu, or a clean install?

What type of Nvidia card is this?

---

### Post by kira. on 2008-11-13
Yeah, I used sudo, but it still doesn't work

I'm pretty sure it has to do with an update. The other day, I updated using the package manager, and when I restarted in ubuntu the next day, it was like this. 

I'm using an Nvidia GeForce 8800<-(not sure about the number) video card

---

### Post by MeURi on 2008-11-13
Well, I have an nVIDIA GeForce 6800GT, and my /etc/X11/xorg.conf is the following:
```

Section "Monitor"
	Identifier    "Configured Monitor"
	Option        "DPMS"    "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load    "glx"
EndSection

Section "Device"
    Identifier	"Configured Video Device"
    Driver      "nvidia"
    Option	"NoLogo" "True"
    Option      "FlatPanelProperties" "Scaling=Centered"
    Option      "RenderAccel" "True"
    Option      "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option    "Composite" "Enable"
EndSection

```

I have the latest nVIDIA driver shipped with Ubuntu, check if they are correctly installed via synaptic

If you don't have any special hardware configuration, my xorg.conf should be ok also for you (mainly the "Device" section)

I'm sorry not to be more precise than this about the drivers in use, but I'm in Windows now.

Let us know if you solve the problem

PS: I usually don't use nvidia-xconfig, I prefer reading the driver's options on the nVIDIA website and modify my xorg.conf by hand

---

### Post by kira. on 2008-11-13
where is my xorg. file? and should i just use a text editor to change it?

---

### Post by MeURi on 2008-11-13
Here I am again :-)

The *xorg.conf* file is located in the */etc/X11/* folder. Any text editor is capable of handling it, since it's plain text.

And well... I suggest you to choose an editor which does syntax highlighting (so you can easily discover typos in keywords, and so on... it helps also in understanding the structure of a configuration file)

---

### Post by Mardoct909 on 2008-11-13
Are you running Gnome?

```
sudo apt-get install envyng-gtk
```

Or KDE? 

```
sudo apt-get install envyng-qt
```

Ok, now you have a utility for managing ATI and Nvidia drivers. 

I believe it is found in Applications->Utlities under Gnome, but look around the menus if not. When it's open, it's simple to install the Nvidia drivers. After clicking the "Install Nvidia" button, it automatically gets the one you need, install it and configures it and your Xorg.conf as needed.

---

### Post by Grashopper on 2008-11-26
What do I do if envyng isn't working?  I typed 

sudo apt-get install envyng-gtk 

into the terminal and it said:  E: Couldn't find package envyng-gtk

Newbie to Linux and Ubuntu.  Please help, thanks!

---

### Post by Grashopper on 2008-11-26
I should also mention I downloaded the package from:

[http://packages.ubuntu.com/source/intrepid/envyng-gtk](http://packages.ubuntu.com/source/intrepid/envyng-gtk)

but I'm not sure what do to do with it at this point...

---

### Post by MeURi on 2008-11-26
The page you linked says that envyng-gtk is in the multiverse repository, so maybe it's just a matter of having all the repositories enabled in your *sources.list* file.

If you don't know how to enable extra repositories, go [here](https://help.ubuntu.com/community/Repositories/Ubuntu).

Anyway, you downloaded the package sources, so it means you have to compile it, install it, and only after you can use it.

Enable the repositories and install it through synaptic or from the console like you already tried to do. It's the simplest way ;-)

PS: the package *envyng-gtk* stays in the *universe* repository; its source is in the *multiverse* repo.

---

