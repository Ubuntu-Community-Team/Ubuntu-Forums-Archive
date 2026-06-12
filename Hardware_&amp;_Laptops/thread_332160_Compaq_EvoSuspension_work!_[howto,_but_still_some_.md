---
title: "Compaq Evo:Suspension work! [howto, but still some little problems]"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by Skumpic on 2007-01-05
Hi all.
I'm an italian ubuntu edgy user, and i'm a real noob (as you can see it's my first post here :D ).Anyway after long tweaking i was able to make suspend to ram working on my compaq evo N610C, so now i'm here to share this mini howto, hoping someone else will help me to resolve last few questions.I hope you can understand my poor english :D

**PREAMBLE**
Using ACPI on my Compaq evo N610C i wasn't able to make suspension work.I tweaked hard for many weeks but i never have been able to "wake up" my screen after suspension (notebook seems to suspend well, but when i wake it up fan, cd-rom,hd start working again while screen remain black).
**Gnome Power Manager** is able to discover when i close/open the lid and is able to manage dmps on/off.Hibernation works out of the box.

One day using Gparted live cd i just discovered that suspension partially worked on my notebook (screen wake up but then freeze).Gparted Live cd used APM to handle power management.So i decided to find out the right configuration for my evo.

**MAKE IT WORKING**
**FIRST STEP: USE APM**
Just modify your grub starting menu:
> sudo gedit /boot/grub/menu.lst
Now find the string **defoptions** and add here: ** noacpi acpi=off apm=on**
Now update your grub with:
> sudo update-grub 
So finally your grub starting menu should be something like this:
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash noacpi acpi=off apm=on

Now add one module:
> sudo gedit /etc/modules 
and add this module at the end: **apm power_off=1**

**STEP TWO:Configure ati card** (otherwise when trying to suspend screen will show funny color)
Edit xorg.conf:
> sudo gedit /etc/X11/xorg.conf
Edit your video card section and make it look similar:
> Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Driver		"radeon"
	VendorName   	"ATI"  	
	BoardName    	"ATI Radeon Mobility 7500"
	BusID		"PCI:1:0:0"  	
        Option          "RenderAccel"           "true"
        Option          "AGPMode"               "4"
        Option          "AGPFastWrite"          "true"
        Option          "EnablePageFlip"        "True"
        Option          "UseInternalAGPGART"    "no"
        Option          "backingstore"          "true"
        Option          "AllowGLXWithComposite" "true"

**STEP THREE: Configure starting service**
Install sysv-rc-conf
> sudo apt-get install sysv-rc-conf
Now lauch it:
> sudo sysv-rc-conf
Deactive (is it a right word in english??) every X in this 2 string:
acpi-supp
acpid
So now they are deactivated.
Now check that apmd is active ( X on runlevel 2,3,4,5)
Press **q** to exit.

**STEP FOUR: Hibernate**
Install hibernate script:
> sudo apt-get install hibernate

Reboot.
Now if you press the power button on your notebook it should suspend, pressing again the same button it should wake up perfectly.
In alternative try:
> sudo apm -s
If you wish to hibernate try:
> sudo hibernate

PROBLEMS:
**1)lm_sensors No longer manage fan.**This doen't mean that fan doesn't work, but simply that lm_sensors doesn't find them.
In fact fan starts and also change their speed based on cpu temperature (quite at the beginning and then, after 20min of work, faster).
So they work (at least for me). Maybe this happens because now all is managed by bios????
**2)gnome power manager** no longer discover when i close/open lid.When i close the lid screen goes off.When i open the lid screen starts again.If i try to suspend or hibernate thru gnome-power-manager or thru **system menu--->pressing quit and then suspend** suspension and hibernation fails.

It seems that they run acpi scripts.
"Googling" i find out this:
[http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-gpm-apm](http://cvs.gnome.org/viewcvs/*checkout*/gnome-power-manager/docs/faq.html#faq-gpm-apm)
> Where do I put my custom suspend/shutdown/hibernate script?

Because gnome-power-manager uses HAL to toggle bits in the hardware, you need to put your custom instructions in /prefix/share/hal/scripts/system/hal-system-power-*
Anyone want to help me to customize suspend and hibernation script????? (i'm a noob, dont' forget) :D
**3)STANDBY FREEZE SYSTEM** If you try **apm -S** to put the system in standby (this is not suspension) very often the system freeze (monitor came back, mouse start again to work but the system is freezed).
That's all folks.
Hope to get good feedback and help for the scripts

Skumpic

---

### Post by James Goode on 2008-03-20
Brilliant, brilliant, brilliant!  Your instructions worked perfectly, thank you very much :-)

---

### Post by Redsandro on 2008-04-26
Thanks for this tutorial! I have exactly the same video card as you. How did you install the radeon driver? My *xorg.conf* has ati and *restricted hardware manager* sais I don't need the *restricted driver *and won't offer me one.

---

