---
title: "HELP!! Intrepid+Laptop = Black Screen of Phun after splash"
date: 2009-03-03
forum: Hardware
---

### Post by VDubCoder on 2009-03-03
Hi all. I'm a n00b to Ubuntu but not to computers.

I currently have an old laptop that I'm working on turning into a media sharing server. I currently have it dual booting with WinXP Home SP3 and Intrepid Ibex 8.10 on a separate partition of an 80GB drive.

The Specs are as follows:
Fujitsu Lifebook N5000? (not sure on the exact model)
Pentium 4 3.0Ghz
80GB HD
512 MB RAM
ATI RADEON Mobility 9600
Aetheros Built in Wireless

I originally installed Intrepid through windows via the ISO file I downloaded and had it running successfully. I had to fudge with the video drivers after I ran some automatic updates but got everything working.

Yesterday I installed a new desktop theme and attempted to install a new splash loading screen as well as a handful of other random things things.

After doing those installations I rebooted. Not only did my new splash screen not show up but Gnome didn't come up either (I have auto login enabled at this point). I first try to change the resolution settings in my /etc/usplash.conf file, save and reboot to no avail. Then I revert back to the old splash via update-alternatives --config and do the update-initramfs -v -c -k all.

After doing this the default splash shows up and then boots to a black screen. No menus. No cursors. Only "static" along the bottom of the screen and something resembling a row of red chinese characters across the top. It slightly resembles looking at a messed up VHS tape. Control+alt+F1 through F0 didn't do anything, except for once. In that instance the screen faded from black to pink to gray and that's it.

I've tried to restart, and boot from a custom line (forget what's it called), removing the quiet, splash, and vga=791 attributes. (The installation of the new usplash theme instructed to add vga=791 to the /boot/grub/menu.lst file.)

Recall that I had this system completely up and functional til I installed the new desktop theme, usplash, and the new usplash theme. I had also updated the kernel to the latest. Although this kernel wouldn't update via the update manager, i had to reboot in recovery mode and choose fix packages. It updated from 2.6.27-11 from 2.6.27-7.

At this point I'm trying to recover the Ubuntu install and avoid reinstalling which would be the easy solution for me. But I'd rather learn something. I'm thinking a problem with video drivers after the update?

I also tried removing compiz and compiz core and rebooted. No luck there either.

Also, I've tried to boot other kernels but they all boot to the same black screen.

When there's a next time, I'm thinking I'll try the Startup Manager.

Any help would be fantastic.

---

### Post by markbuntu on 2009-03-03
Recovery mode
fix x

---

### Post by VDubCoder on 2009-03-03
i tried xfix; no dice. i tried fix packages. it tries to fix the kernel but returns an error code of 1? --or something like that. i tried xfixing both kernels and got the same results:

Screen looked like scrambled cable for a channel that's off the air. blinked with this 3 times at full screen and then had the same image but at a smaller resolution. control+alt+F1 made this small image go to the top of the screen and centered.

I'm confident that this is a video driver issue with the kind-of updated kernel 2.6.27-11. All i have is the command line to work with. How can I roll back the video driver to the default/original out of box?

---

### Post by markbuntu on 2009-03-03
You can edit the /etc/X11/xorg.conf file and replace it with xorg.conf.failsafe. If you do not have a xorg.conf.failsafe these are the sections you need. Remove everything else.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

The autologin is killing you, it is logging you into your last failed session every time and prevents you from logging into gnome-failsafe from which you could easily fix your problem.
Never do that again. It is worth 10 seconds of timed login when something like this happens.

---

### Post by brokentroy on 2009-03-03
I cannot log in at all to change anything.  I booted to recovery mode and went to Root.  I then ran apt-get remove compiz.  I rebooted and when I logged in I now had a white screen, but got logged back out.  I see my wallpaper every time I log in, but then I get either a black wierd screen or a white screen and get logged out.  I will definitely get rid of the auto logon.

I ran sudo dpkg-reconfigure -phigh xserver-xorg and then I went from white screen back to black with colored lines.  I reversed my progress.  Is there a way to run this command and set it to low res.  -plow?

---

### Post by VDubCoder on 2009-03-03
It didn't work :\

---

### Post by markbuntu on 2009-03-04
From the command line you could try 

startx

to get x up and running without going through gdm/

I think there is a way to disable autologin from the command line or at grub boot but I don't know how to do that.

---

### Post by VDubCoder on 2009-03-04
I tried looking into that. I decided to scrap this install and install ubuntu server 8.04. 8.10 server wouldn't install and I've seen that that can mean it's incompatible with my hardware.

I appreciate your help all the same.

---

