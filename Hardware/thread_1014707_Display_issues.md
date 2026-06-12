---
title: "Display issues"
date: 2008-12-18
forum: Hardware
---

### Post by kenjjj on 2008-12-18
test

---

### Post by kenjjj on 2008-12-18
Hi I am new to ubuntu but got 8.10 i386 installed on my old toshiba laptop OK but the display resolution won't go higher than 800 X 600. It seems to be a common problem with this version and.
with the previous version of ubuntu I found a way to make it change the resolution to 1024 X 768 but now either I am doing it wrong or that method no longer works.
 I tried various things I found on the net but none worked so I would like to start again from scratch. 

Does anyone know how I can get a resolution higher than 600 X 800? When I run config it says the display and screen are "configured".

There must be a simple (hope!) way to fix this, anyone? -Ken

---

### Post by kenjjj on 2008-12-18
Hi I am new to ubuntu but got 8.10 i386 installed on my old toshiba laptop OK but the display resolution won't go higher than 800 X 600. It seems to be a common problem with this version and.
with the previous version of ubuntu I found a way to make it change the resolution to 1024 X 768 but now either I am doing it wrong or that method no longer works.
 I tried various things I found on the net but none worked so I would like to start again from scratch. 

Does anyone know how I can get a resolution higher than 600 X 800? When I run config it says the display and screen are "configured".

There must be a simple (hope!) way to fix this, anyone? -Ken

---

### Post by overdrank on 2008-12-18
Hi and welcome, please do not create multiple threads on the same issue, threads merged.

You can try and boot into recovery mode which is usually the second choice from the grub and use the xfix option, then you should be given the option to boot normally.
You may also consider using Hardy 8.04 instead of Intrepid 8.10 but that is my suggestion only. :)

---

### Post by kenjjj on 2008-12-18
Thanks, from the forum web site when I posted it was not clear that the msgs had posted before, I got nothing saying anything had happened.  

I tried your suggestion about recovery mode, no change. I had installed the version you mentioned before 8.1, but although I did get it to display the proper resolution, there were other more serious issues with it that 8.1 has solved.  

So, what would be the next thing to try?-Ken

---

### Post by overdrank on 2008-12-18
> **kenjjj said:**
> Thanks, from the forum web site when I posted it was not clear that the msgs had posted before, I got nothing saying anything had happened.  

I tried your suggestion about recovery mode, no change. I had installed the version you mentioned before 8.1, but although I did get it to display the proper resolution, there were other more serious issues with it that 8.1 has solved.  

So, what would be the next thing to try?-Ken

Hi and you may try this link
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
What is the model of the graphics card?

---

### Post by linux_tech on 2008-12-18
If you type ```
xrandr
```
in the terminal, what does it show for resolutions?

---

### Post by kenjjj on 2008-12-18
Thanks for the suggestions. I tried them out, here is what I found;

When I paste rm ~/.config/monitors.xml into a terminal window and hit enter, it informs me that it cannot remove the file as there is no such file.

When I do the same with xrandr I get a bunch of settings listed, the highest is 800 X 600.

The video card is listed as a Trident CyberALADDIN according to the info that came with the laptop, but from research on the web it seems that it may more accurately be a Trident Microsystems CyberBlade XPAi1.

when I run sudo nano /etc/X11/xorg.conf I get;

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

So I delete that and and replace it with this information that I found online that supposedly is for my hardware;

Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection


But then I see no way to save this in the terminal window! How do I save the new file or whatever it is that has the changes? Maybe that would fix it, using ubunto Hardy I messed with this and managed to save the changes but got them wrong somehow and the display then defaulted to 600 X 480. But at least with Hardy I managed to save the file. How can I save it now? Maybe that would solve the issue with the low resolution setting. 

Or perhaps there is an even better config file set up for this video card? -Ken

---

### Post by kenjjj on 2008-12-18
When I try $ xrandr --output LVDS --mode 1024x768 nothing happens.

---

### Post by pietjanjaap on 2008-12-18
- xfix in recovery mode.
 
  
- gksu displayconfig-gtk

  Choose your videocard or vesa.
  Choose your monitor.
  (If you look in menu, edit menu, the part "other", there you can see this option, this is diabled, so enable it.), or make a icon.
I do not know if your videocard is accepted, I have a sis videcard and I need vesa driver.


Reboot now. and try it.


- sudo dpkg-reconfigure -phigh xserver-xorg, if above is not enough.


In xorg file:
I need to put in:

section:

Section      "Device"
Identifier   "Generic Video Card"
Boardname    "Sis"     (here you need a different name)
Driver       "Vesa"

---

### Post by linux_tech on 2008-12-18
> **kenjjj said:**
> 



But then I see no way to save this in the terminal window! How do I save the new file or whatever it is that has the changes?  



First make a backup of xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

```
sudo nano /etc/X11/xorg.conf
```

Edit file
Save the file and exit nano.

---

### Post by kenjjj on 2008-12-18
Yes, I do make a backup of the file first, but then how do I save it?, I see no options or drop down menues ect to do that.

As for xfix in recovery mode, if this is one of the opptions that comes up when I start ubuntu, it does give me a recovery option but I see no way to enter commands in anywhere, it just loads up a bunch of stuff and I don't ever have an option to do anything....guess I must be missing how to do that, so please, how do i get to enter the xfix in recovery mode?

I tried the commands

xrandr --newmode "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796

then

 xrandr --addmode default 1024x768

and then

xrandr --output 0 --mode 1024x768 

which resulted in the system/preferences/screen resolution showing a 1024x768 setting, but when I highlighted that and hit apply, nothing happened. what's more, this seems to apply for only one session, when I change log ons or ect it reverts back to the lower setting. I could live with that if it did anything, but although it shows a setting of 1024x768 it doesn't make any changes in screen resolution when I select it.

 Please keep the information coming, I will keep trying. Thanks-Ken

---

### Post by linux_tech on 2008-12-18
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by pietjanjaap on 2008-12-18
xfix
You starte this bij, start pc in recovery mode, choose xfix from menu, thats all.
Now ubuntu will try to search for your videocard and monitor.

Reboot

and try:
gksu displayconfig-gtk
(vesa will always work)

---

### Post by kenjjj on 2008-12-19
when I open a terminal and put in xfix, nothing happens, sudo xfix same. It says it doesn't know that command.

If I reboot there is an option to choose recovery mode, and then a window comes up and I can choose xfix, when I do it reloads the xconfig file backup it seems, and the system reverts to where it was with only 800x66 resolution showing.

When I run gksu displayconfig-gtk it says it is starting an admin app but nothing happens.

Running gksudo gedit /etc/X11/xorg.conf brings up the xconfig file showing;

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


I can change that now by making it read;

Section "Screen"
Identifier "Default Screen"
Monitor "Generic Monitor"
Device "Trident Microsystems CyberBlade XPAi1"
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 32
Modes "1024x768"
EndSubSection
EndSection

But that only makes the window that shows the resolution sizes show a 1024x768 option, when I highlight that and exit the resolution does not change.

So I guess I need to change more than the Screen section to impose the changes...what should I change and what should the change be? Thanks,-Ken

---

### Post by camionrouge on 2008-12-19
Hi, can I suggest you take a look at your X log file usually at /var/log/Xorg.O.log to see what's happening. This should have several references to trident spread throughout the file.
It will show what module loaded and what chipset if finds 'cyberbladexxx' etc.
Also what module tries to load the modes and settings. The driver can pick default settings which are not correct for your screen and will get rejected leaving you with default resolutions only.
See [https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution) for some more help.
Correct values can be entered into your xorg.conf to put this right.
Hope this helps

---

