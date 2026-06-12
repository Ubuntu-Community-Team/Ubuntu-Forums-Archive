---
title: "dpkg-reconfigure doesn't recognize that I have an ati card"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by BLTicklemonster on 2007-12-04
Running a Dell Latitude c510 with an ati mobilty card, and I've tried to get the 3d acceleration working like I had before, but I just can't get it now. 

dpkg-reconfigure xserver.xorg doesn't even show ati or radeon as options whether I allow it to auto detect or not.

This worked for me before:

> Originally Posted by Vaan View Post
Many thanks dougfractal! I now have direct rendering working again. Everything is back like it used to be, desktop effects and everything.

This makes me wonder if your solution will help out the others in this thread.


Okay if you have an ATi card below the 9500 series (such as the 9200) then try and follow these steps and let us know your results.

Open up a terminal window and type these commands:
Code:

sudo apt-get remove fglrx*
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

After you've finished running the previous commands type this in your console/terminal window:
Code:

sudo dpkg-reconfigure xserver-xorg

The blue xerver configuration should show up. For the x server driver select ati. Next just continue to follow the directions (when you get to the screen resolution area make sure to select your resolution(s) using the spacebar, when done press enter) and after it's all done press ctrl alt backspace to restart the X11 display.

After you login back to the desktop open up a terminal window again. Type in:
Code:

glxinfo

Near the top you should see something that says:
Code:

direct rendering: YES/NO

It should say Yes. If it says No that means either something went wrong, or this solution did not work for you.

If it is Yes, then your display driver should be configured properly and you can enable Desktop Effects and play your games and such.

But does nothing now.

I keep getting failsafe, and having to use low resolution.

I've tried to go to the ati site to download a driver, but there's like a gazillion mobility drivers there, and I have no idea which one to use.

So how do I get just the plain old every day ati driver back? I don't have to have 3d acceleration that bad!

Ideas anyone?

---

### Post by Yellow Pasque on 2007-12-04
Please run
```
sudo update-pciids
lspci | grep "VGA"
```
for me and give me the output of the lspci

---

### Post by BLTicklemonster on 2007-12-04
bill@bill-laptop:~$ lspci | grep "VGA"
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

Every place I've gone to see anything on this chip, people have different versions, from what I can tell.

I've got back up to full resolution now, but fglrx isn't installed, so I can't get fglrxinfo. BUT, I can do glxgears. 

bill@bill-laptop:~$ glxgears
1952 frames in 5.0 seconds = 390.323 FPS
1967 frames in 5.0 seconds = 393.320 FPS
1967 frames in 5.0 seconds = 393.370 FPS
2004 frames in 5.0 seconds = 400.783 FPS
5817 frames in 5.1 seconds = 1135.700 FPS

nothing major, but still, it's more than before.


Go figger.

Here's the pertinent xorg stuff:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection
```


The last thing I did before I got it back this far was to try to install 

sudo sh ati-driver-installer-8.26.18-x86.run

but it came up with an error and didn't install completely or so I thought... I'm not sure.


*EDIT:

Seeing as how I'm using an attempt to get compiz to work as my end result, I typed compiz in the terminal and here's what I see:

```
bill@bill-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c59 (prog-if 00 [VGA controller])
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (512): Failed.
aborting and using fallback: /usr/bin/metacity 

```

If that's any help. At least my chip's not blacklisted, lol.

But compiz worked at first boot. The upgrade messed it up.

*edit again

but it's still not right. trying glxgears now crashes X.

---

### Post by BLTicklemonster on 2007-12-06
So, any idea how to get this back to normal? I have 3d, but it's nothing like it was before.

---

