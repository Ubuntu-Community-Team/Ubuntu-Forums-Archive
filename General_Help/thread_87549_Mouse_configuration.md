---
title: "Mouse configuration"
date: 2005-11-08
forum: General Help
---

### Post by Optiker on 2005-11-08
I posated this to the Kubuntu forum with no replies, so thought I'd try here as well.

Just installed 5.10. My mouse is an MS 5-button Optical Intellimouse. I'd like to disable the two buttons on the sides of the mouse since I have a tendency to inadvertently press them - especially the one on the left - and that alters or disables the action I intended.

How do I configure my mouse to act as a simple 3-button mouse?

Thanks!
Optiker

---

### Post by Who on 2005-11-08
You may find the option you need if you reconfigure your xserver using
sudo dpkg-reconfigure xserver-xorg
(by typing it in a terminal)
Beware that this is a powerful script, and unless you know what you are doing you should stick to the default values (except of course when it comes to the mouse settings :P)

Also, I would reccomend doing the following FIRST
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_BACKUP

and then if all goes horribly wrong when using the dpkg-reconfigure command you can do:
sudo cp /etc/X11/xorg.conf_BACKUP /etc/X11/xorg.conf

(cp means copy, the first item is the source file and the second the file to copy to. If the Xserver doesn't start then push CTRL+ALT+F1 or F2 to get to a terminal where you can login in text mode)

I hope that helps. Alternatiively, you could manually edit your /etc/X11/xorg.conf using something like gedit.

Hope that helps

Who

---

### Post by Optiker on 2005-11-08
Who...I was afraid it might be that kind of process. I'm not real experienced at Linux yet. I've already done one sudo dpkg-reconfigure xserver-xorg with regard to display resolution since I didn't know how to select resolutions beyond the defaults when I installud Kubuntu and needed higher than teh highest default. I survived, but who knows what I may have inadvertently changed. I'm reluctant to go through it again unless I have no other choice.

I feel more comfortable manually editing xorg.conf. Here's what it currently reads...can you tell me what to change and what, if any, packages I'd need to install to provide a driver. Or, am I really biting off more than I should try to chew? It's the MS 5-button optical Intellimouse with scroll wheel.

-----------
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
-------------

Thanks!
Optiker

---

### Post by tonysathre on 2005-11-08
there is a mouse configuration applet in kcontrol, but not sure if that is what u need, try that before messing with your xserver configuration files

---

### Post by Optiker on 2005-11-08
Tony...thanks! Much more to my style. Thanks! Looked for something like that but must have missed it.

Optiker

---

### Post by Optiker on 2005-11-08
kcontrol is appraently installed, but I don't find anythink in the start list to launch it.

However, I did find something to run to change settings and the mouse aplet doesn't have anything in it to configure mouse buttons.

Other suggestions?

I'm still willing to try to manually edit xorg.conf if somebody will tell me what to change.

Thanks!
Optiker

---

### Post by Who on 2005-11-08
Optiker - If you don't have any success with using kcontrol or another GUI app you could backup your /etc/X11/xorg.conf and then run dpkg-reconfiguer etc... then, after running it copy the NEW xorg.cong to a different file (say, xorg_MOUSE) and put the backup of the one that works BACK to being xorg.conf. Now reboot, and use Gedit (as a superuser) to copy JUST the mouse section from xorg.conf from the corg_MOUSE file to the current xorg (keeping a backup of it, of course)..

Like I said, this is a more friendly way of doing stuff if you find no app - cos it ensures  all the settings except the mouse ones stay the same

The section you want to edit/copy will probably start like 
"Section "InputDevice"
	Identifier	"Configured Mouse""

Good luck!
Remember, as long as you make a copy of the file, all will be well! I find that you can almost invariably take the default vaules for everything in the xserver configuration script, and considering in the above approach all the settings except those for the mouse are irrelevant, so that the process is acually quite quick (if not ideal!)

Hope you don't need to find this helpful :P

Who

---

