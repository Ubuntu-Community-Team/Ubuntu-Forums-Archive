---
title: "Toshiba M750 with Ubuntu 8.10"
date: 2009-01-31
forum: Hardware
---

### Post by Fc1032 on 2009-01-31
Hello all,

I have just put Intrepid onto my toshiba m750 tablet (as far as differences go, the m750 only has a new processor, everything else is the same as the toshiba m700)

After following the instructions here>>
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700")

I managed to get the sound working, but I cannot get the stylus and touchscreen working. 

I followed the prompts,"sudo apt-get install setserial" worked fine, but the next step, i was a little confused. It says add line to the end of "/etc/rc.local" but on this script it says i should put anything before the 'exit o' so i put the line after the installation but before the exit 0.

The next command: 
"sudo apt-get install build-essential
sudo apt-get build-dep wacom-tools
wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.2.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.2.tar.bz2)
tar -xjvf linuxwacom-0.8.2.tar.bz2 
cd linuxwacom-0.8.2
./configure --enable-wacom --prefix=/usr
make
sudo make uninstall
sudo make install" 

Doesn't work for me, it asks me if i want to continue, i choose 'y' (yes) but it aborts...

Can someone give me details/instruction on what i should do to get the stylus and touchscreen working?

P.S you'll have to use really basic terminology... I might not get you the first time :p

---

### Post by Fc1032 on 2009-02-01
Bump??

---

### Post by Favux on 2009-02-01
Hi Fc1032,

I was going to suggest you go to Loic2's wiki and install the 0.8.1-6 debs there.  But then I noticed your HOW TO linked to his Wacom driver wiki.  It also links to the bug report that makes it clear you need at least 0.8.2 to get the patch that enables your touch.

It's not obvious to me why your compiling failed.  The author of  your HOW TO is also instructing you to configure for the kernel driver.  Given all that you might want to try:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

I hope this is helpful.

---

### Post by Fc1032 on 2009-02-10
Thanks! I'll give it a try. I'll report how I go.

---

### Post by tobibas on 2009-03-27
> **Fc1032 said:**
> Thanks! I'll give it a try. I'll report how I go.

I am planning to buy a Multitouchscreen Tablet PC and definitively need the multitouch-feature working for my thesis. Did you succeed with the wacom drivers and get the multitouch working? Anybody else having a multitouchscreen working on linux?

I would appreciate a short but quick answer!

Tobias

---

### Post by Favux on 2009-03-27
Hi tobibas,

Which Multitouchscreen Tablet PC?  If you're talking about one with a N-Trig digitizer you can get it working.  Here's a thread for the HP TX2z:

[http://ubuntuforums.org/showthread.php?t=1038898]("http://ubuntuforums.org/showthread.php?t=1038898")

So you can get the stylus and touch etc. working.  But specific multitouch gestures?  See post #67 on the above link.

Hope this helps.

---

### Post by tobibas on 2009-03-27
> **Favux said:**
> Hi tobibas,

Which Multitouchscreen Tablet PC?  If you're talking about one with a N-Trig digitizer you can get it working.  Here's a thread for the HP TX2z:

Hope this helps.

Actually I was referring to the Toshiba M750 - is it real multitouch?

---

### Post by Favux on 2009-03-27
Hi tobibas,

I'm not sure.  It at least has touch.  The two multi-touches I'm sure of are the HP TX2z and the Dell latitude XT.  Both of which use the N-trig digitizer.

---

### Post by Fc1032 on 2009-04-23
Hello everyone,

Sorry, i didn't look up the thread... Anyway, the toshiba m750 does not have multi-touch by default. It has been used for multi-touch testing but no offcial m750 has multi-touch. the m750 has touch and active digitizer.

Only tablets with multi-touch are the dell latitude and hp touchsmart tx.

I still haven't got the touch and stylus to work on my tablet... Its so discouraging... I only got the sound to work and noting else. So it only functions as a laptop and not tablet.

Apparently, someone with a m700 has posted a video of the m700 with touch and pen working on Intrepid. I asked how it was done but no response.

---

### Post by Favux on 2009-04-23
Hi Fc1032,

Do you know if it is a Wacom digitizer and touchscreen?  Is it a serial or usb Wacom tablet?  Are you planning on staying with Intrepid for a while?

---

### Post by Fc1032 on 2009-04-23
Hello Favux,

I'm not too sure if it is wacom, but a quick google search lead me to some drivers >> 

[http://www.driversdown.com/drivers/Toshiba-Portege-M750-S7201-Notebook-Wacom-Dual-Touch-Driver-3.0.2.4-Windows-Vista-64_86518.shtml](http://www.driversdown.com/drivers/Toshiba-Portege-M750-S7201-Notebook-Wacom-Dual-Touch-Driver-3.0.2.4-Windows-Vista-64_86518.shtml)

Wacom also doesn't specify if it has drivers for the m750... It just has a general tablet driver for vista.

It came with the drivers built in and has both touch screen and active digitizer. It should be serial tablet?? (since the hardware is all built in...)

I'm waiting for 9.04, i want to give it a try and see if the touch and pen is supported!! I went back to vista a while ago cause i needed the pen for UNI. I'm still very keen in getting ubuntu on the tablet though!!

---

### Post by Favux on 2009-04-23
Hi Fc1032,

So you haven't installed Ubuntu yet?

What I'm trying to tell you is that I can probably help you get Wacom working.  We need to download the linuxwacom drivers from the LWP (linux wacom project) and configure your xorg.conf in Hardy or Intrepid.  If you have a serial tablet pc I'm just not positive I can help you get touch working.  But probably.

Jaunty (which releases tomorrow or actually today since its now the 23rd) relies on the HAL/.fdi method usuing a specially patched linuxwacom 0.8.2-2 driver (patches from Fedora) and the included 10-wacom.fdi file has a section for serial tablets with touch.  Only there is a problem with it and it doesn't work.  We have just figured out a second work around for in the past couple days.  So there should be two ways to get it working.

Those of us with HP TX2000 and TX2500 have had our usb Wacom tablet pc's working with touch since Hardy.

---

### Post by Fc1032 on 2009-04-23
Hello again!

I currently do not have ubuntu installed on my tablet. I did in the past (dual booted 8.10 and vista) but since it did not have tablet functionality, i removed its partition.

I can always make a dual boot now and follow instructions, Ubuntu installs pretty fast, so it shouldn't be a problem to have it up and going within an hour. Thanks for helping out!!! I'm really appreciating the help your giving!! ^^:)

So what would you like me to do now? 



Many thanks!

---

### Post by Favux on 2009-04-23
Hi Fc1032,

Pick the version you want.  It sounds like you're thinking Intrepid, since you've already installed it and probably have the CD.  Let me know which and when you're installed.  And I'm hoping you know serial or usb.  If not I guess we can figure it out.

---

### Post by Fc1032 on 2009-04-23
Hello Favux,

Yea, i'm installing intrepid now. When i have it running, how should/can i find out whether my tablet is serial or usb?

Does it say somewhere in this tut? >> [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700]("https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700")

---

### Post by Favux on 2009-04-23
Hi Fc1032,

Yes, that's a serial tablet pc.  So after you get Intrepid install go here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  Then download to your desktop the two i386 (its Intel right?) 0.8.1-6 linuxwacom deb packages under Download the updated packages under the Intrepid section near the top.  Intrepid comes with 0.8.1-4, so we're updating you.  Just double click on them and the Debian package installer will install them.  Always be sure the linuxwacom drivers and wacom-tool packages are the same version.

Then we need to look at your xorg.conf.  It is in "/etc/X11/".  Use Places (nautilus) on the top menu bar and copy and paste it in between  the code tags you get from clicking on # above.  That boxes it.

---

### Post by Fc1032 on 2009-04-23
Ubuntu is installing now, i think it will take 15~20 minutes from now, when i have new wacom drives updated and the Xorg.conf file for you i'll post them here.

---

### Post by Fc1032 on 2009-04-23
Hi!!

I just finished installing. I got both the packages to install successfully.

the xorg file is this:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

---

### Post by Favux on 2009-04-23
Hi Fc1032,

OK, we want wacom-tools.  Did you update Intrepid?  I'm guessing not since there are probably a lot of packages.  Why don't you go to System>Administration>Update Manager and check.  Depending on what version of Intrepid live CD you used that could take a while.  Then try wacom-tools again.  It was helpful that you caught the error message.  If you get another let me know what it is, because we should be able to fix it.  Meanwhile I'll work on your xorg.conf.

---

### Post by Fc1032 on 2009-04-23
Hahaha, i edited the same time as you posted!

Yea, i found out i needed to update... Thanks for the tip anyway!


So now both packages are installed, what should i do now?

---

### Post by Favux on 2009-04-23
Hi again Fc1032,

Does your stylus have buttons?  How many?

---

### Post by Fc1032 on 2009-04-23
there are 6 in total.

One is the power button, 

one is a joystick type of button (allows left, right, up, down and select all on one button)

the other 4 are normal buttons

---

### Post by Favux on 2009-04-23
Wow!  On the stylus, the writing pen?

---

### Post by Fc1032 on 2009-04-23
pen has only two buttons,

the eraser at the top of the pen 

and a right click button on the side.

---

### Post by Favux on 2009-04-23
Whew!  Ok, that I know how to handle.  Are you comfortable with the command line?  Or do you want instructions?

---

### Post by Fc1032 on 2009-04-23
well i'll give command line a shot :) i'm sure i'll be using the terminal alot down the track

---

### Post by Favux on 2009-04-23
Hi Fc1032,

You have to be careful with xorg.conf.  Doing it wrong can break Xserver and you won't be able to boot into your desktop.  So first back it up with the copy (cp) command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/my_xorg.bak
```
or whatever you want to call it.  sudo makes you root and you get asked for your password and then you're root.  To restore the backup you reverse things:
```
sudo cp /etc/X11/my_xorg.bak /etc/X11/xorg.conf
```
To edit xorg.conf we will use gedit (gnome-edit).  Since this is a graphical editor we will use the graphical version of sudo, gksudo:
```
gksudo gedit /etc/X11/xorg.conf
```
Compare the two and study the changes.  You can probably cut and paste the new one and replace the old one.

Then reboot.  Hopefully it will boot, if it doesn't try recovery.  This should get at least the stylus and eraser to work.

Good luck!

---

### Post by Fc1032 on 2009-04-23
I used the new Xorg file. But when i boot it says its running in low graphics etc etc... I ran the computer in low grapics mode to see what happens.

With the new Xorg, both pen and touch do not work. All it did was make the screen resolution low. I restored original xorg file after that.

Is there another way?

---

### Post by Favux on 2009-04-23
Hi Fc1032,

I wonder why the attached file isn't showing you downloaded it?  I need to see your current xorg.conf to see if and where I goofed.  At least it booted.  It shouldn't go into low graphics unless something happened to the video section.

---

### Post by Favux on 2009-04-23
Sorry, found a mistake.  In the touch section:
```
Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch"
#	Option		"Device"	"/dev/ttyS0"	# SERIAL only
	Option		"Type"		"touch"
	Option		"ForceDevice"	"ISDV4"		# SERIAL Tablet PC only
#EndSection
```
there is a # (comment) I forgot to remove.  Remove the # from:
```
#EndSection
```
to
```
EndSection
```
Color me embaressed.

---

### Post by Fc1032 on 2009-04-23
What should i do now? 

I downloaded about 3 times already. Once on desktop and 2 times on laptop.

P.S the original xorg file is attached

---

### Post by Fc1032 on 2009-04-23
Followed your instructions and got rid of the #

Restarted and all, no touch, pen and eraser don't work. But screen resolution still the same...

---

### Post by Favux on 2009-04-23
Hi Fc1032,

It shows you downloaded now, I guess there's a big lag.  Do you mean screen resolution is back to normal?  Or still low?

The xorg.txt you uploaded as an attachment is your original one that you put in the post.  I need to see what you replaced it with.

Do you know what your video chipset is?

Don't worry, this all seems harder than it is because your new.  Just take a breath and be patient.  We'll get there.

---

### Post by Fc1032 on 2009-04-23
Well, using the "gksudo gedit /etc/X11/xorg.conf" this is what i now use:

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
#	Option		"Device"	"/dev/ttyS0"	# SERIAL only
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# SERIAL Tablet PC ONLY
	Option		"Button2"	"3"  # make stylus button a R mouse button
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
#	Option		"Device"	"/dev/ttyS0"	# SERIAL only
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# SERIAL Tablet PC only
EndSection

Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom-touch"
#	Option		"Device"	"/dev/ttyS0"	# SERIAL only
	Option		"Type"		"touch"
	Option		"ForceDevice"	"ISDV4"		# SERIAL Tablet PC only
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection

Basically its what you gave me with the correction included.

I had to boot into vista (sorry for the late reply!) to check the video chipset. I think it should be called (Vista calls it display adapter??: 'Mobile intel(R) 4 Series express chipset family'

---

### Post by Favux on 2009-04-23
Good.  So no wacom activity.  Did you reboot a couple of times and restart X (ctrl-alt-backspace) a few times?  Is the video normal now or still low resolution?

With no wacom activity it implies that your wacom symlinks aren't in place.  We could go the old-style serial tablet configuration route.  That's what those ttyS0 lines are about.  That can be simple and straightforward or it can get quite involved, depending on how lucky we get.

I'd recommend spending a little more time on the symlinks before giving up.  First when did the Toshib M750 come out?  How new is it in other words?  I'm trying to figure out if the udev wacom.rules that contains the symlinks and comes with linuxwacom 0.8.1-6 is too old to contain your tablet pc.

---

### Post by Fc1032 on 2009-04-23
Well i have restarted a few times both the computer and X.

The toshiba m750 came out around christmas 2008 i think. It is just an upgrade of the m700 (upgrade of the CPU only i think). The m700 was release Dec of 2007. So it is still pretty new.

From the tutorial i mentioned before, they use the 0.8.2>> "Then we can download, compile, and install a working driver (at least 0.8.2 from linuxwacom.sourceforge.net) "

---

### Post by Favux on 2009-04-23
Ah, I hadn't realized it was that new.  The latest wacom.rules came out in 10/08 I think.  So that may explain the mystery.  I knew about the 0.8.1-4 bug, that's why I recommended updating from the default to 0.8.1-6.

Maybe you need 0.8.2, but he doesn't explain why.  Usually serial tablets don't need the latest drivers.  Usb was only introduced in about the 0.8. drivers, but they've had serial from the beginning.  If we assume he is correct and you are feeling adventurous you can go here and compile the 0.8.2-2 linuxwacom:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Notice that appendix 3 at the bottom explains symlinks and how to determine if your model is in them.

---

### Post by Fc1032 on 2009-04-23
So do i have to remove the previously installed packages from synaptic then install the tar.bz2 from linux wacom?

But that is only one package, do i just download it and install like previous package or do i do command prompt?

---

### Post by Favux on 2009-04-23
Hi Fc1032,

No you don't have to remove the previous drivers.  The HOW TO removes them and installs the drivers and wacom-tools.  You have to follow the steps exactly in a terminal.  Copy and paste the commands.  What it has you doing is compiling from the LWP source code rather than downloading and installing a precompiled, pre-packaged debian.  Read it through a couple of times before doing anything.  Since you have a serial tablet the wacom.ko kernel driver probably isn't necessary but it shouldn't hurt.

Between that and the LaptopTestingTeam HOW TO we should get you up and running.  We could keep trying with 0.8.1-6 if you want since we aren't sure it's a dead end.

---

### Post by Fc1032 on 2009-04-23
Oh ok, Thanks! I'll read the how to and follow the steps!
 
One last question, in the previous tutorial i brought up, it says to: "and add line:

/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig

at the end of /etc/rc.local"

Do i have to do this step? If i do iam not sure where i start typing in /etc/rc.local can you perhaps do a screen shot of where i should start typing int he /bin/serial....

---

### Post by Favux on 2009-04-23
Right, we may need to install setserial and do that.  That's sort of the old style setup.  What I've seen recently is that some serial tablets just work using the wacom symlink, the "/dev/input/wacom" line.  Without seeming to need the /dev/ttyS0 port 0x338 irq 4 autoconfiging line.  This doesn't make much sense to me but I thought, hey we might get lucky again.  The 0.8.1-6 you installed may be good enough if we go the setserial route.  That way you wouldn't need to compile anything.

So maybe we ought to take a break and resume later.  You can read up and I obviously need to read the M700 HOW TO again.  It's been too long since I looked at it.

---

### Post by Fc1032 on 2009-04-23
Hello,

Yea, lets call it a day and continue some other time. I need to look at your HOW TO. It seems to be very detailed and seems to hold the answer (somewhere =D)

Thanks for all the help you've given me!! 

See you round!

---

### Post by Fc1032 on 2009-04-24
Hello!

I just finished installing the wacom files by following your instructions here >> [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

I think i have installed it successfully because for the final step (Section1, step 8) it shows i have "USB Wacom Graphire and Wacom Intuos tablet driver"

Now about the xorg file. I tried to just restart the computer because my current xorg file was the one you wrote for me last time. That didn't work so i restarted Xserver (ctrl-alt backspace) but that also didn't work.

So i went to [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700)
the previous tutorial i have been refering to, and took the xorg file from there. The xorg file there did not do anything, ust made my screen resolution smaller.

I then went back to the xorg file you wrote my and this restored my normal screen resolution but still no stylus and touch.

So what is my next step from here? Should i be looking for a xorg file for my computer?

---

### Post by Favux on 2009-04-24
Hi Fc1032,

OK, you've installed linuxwacom 0.8.2-2 using the HOW TO.

See if you have a file called &#8220;50-xserver-xorg-input-wacom.rules&#8221; or something similar in &#8220;/etc/udev/rules.d/&#8221;.  If not follow appendix 3  and install it and reboot.  See if that does anything.

If that doesn't work try:
```
dmesg | grep ttyS
```
This should give you output like:
```
/dev/ttyS0 port 0x338 irq 4
```
like in the M700 wiki.  But it should be a little different.  See what:
```
ls /dev/ttyS*
```
looks like. This should tell you the serial ports available.

Comment out (#) the:
```
Option		"Device"	"/dev/input/wacom"
```
lines and remove the comments from the:
```
#	Option		"Device"	"/dev/ttyS0"
```
lines.  Except I would completely comment out the "touch" section from Section to Endsection and "touch" in "ServerLayout".  Let's concentrate on getting the stylus working first.  And reboot.

To find the active port you can use xxd. The program xxd will exit for devices not listed, otherwise CTRL and C to quit. Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc. Bring the pen to the screen and move it around. You know you have the right ttyS* when you see a reaction with an output of characters. That's the ttyS* you want to use in xorg.conf. In a terminal type:
```
xxd /dev/ttyS0
```
changing to S1, etc.

---

### Post by Fc1032 on 2009-04-24
Hello Favux! :)

I followed your steps, 

i did not "50-xserver-xorg-input-wacom.rules" so i followed your steps and downloaded. Still no tablet functionality, so next step.

"dmesg | grep ttyS" did ot shown any output. Just popped me back into "brian@brian-laptop:~$ ". But "ls /dev/ttyS*" showed me this:

"/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3"

I tried to follow on onto editting the xorg file but i didn't know what comment out and remove comments meant. Does it mean i remove the "#" from that line?

I skipped to the next step about testing. It seemed pretty straight forwards but it didn't seem to work at all for me... Can you see if what i did was right?

First i typed "xxd" into terminal, this made the next line blank. I typed in "ls/dev/ttyS*" and tested the pen. Tried for all ttyS(0-3)

This didn't get any output for me. 

Then i thought i might have been doing it wrong so i typed in xxd /dev/ttyS0 and all the others. but that just made the terminal skip a line to "brian@brian-laptop:~$" (did nothing i guess)

What should i HAVE done? and what needs to be done??



Thanks!!

---

### Post by Favux on 2009-04-24
Hi Fc1032,

Hmmm.  How sure are we that the M750 is a serial Wacom?  After a fresh reboot let's try:
```
sudo dmesg | grep ttyS
```
and see what kind of output we get in usb:
```
lsusb
```
Do you see wacom in this output?  And what is the complete output of:
```
dmesg | grep [Ww]acom
```
Also did you try this command from appendix 3:
```
more /proc/bus/input/devices
```
and see if the output included a section labeled Wacom where you could get the Vendor and Product ID's?  You could then check the table in “50-xserver-xorg-input-wacom.rules” on your desktop and see if it has your tablet pc.

---

### Post by Fc1032 on 2009-04-25
Hello!

'sudo dmesg | grep ttyS' didnt do anything,

'lsusb' produced this output, i don't think wacom is in this output:

'Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 04f2:b096 Chicony Electronics Co., Ltd 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub'

'dmesg | grep [Ww]acom' produced nothing as well

the appendix 3 command gave me a long list>>

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
U: Uniq=
H: Handlers=event4 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=04f2 Product=b096 Version=1024
N: Name="CNA7157"
P: Phys=usb-0000:00:1d.7-3
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb8/8-3/8-3:1.0/input/input7
U: Uniq=
H: Handlers=event7 
B: EV=3
B: KEY=1 0 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="PS/2 Mouse"
P: Phys=isa0060/serio1/input1
S: Sysfs=/devices/platform/i8042/serio1/input/input12
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input13
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

I can't find a wacom section.

:(uh oh...

---

### Post by Favux on 2009-04-25
Hi Fc1032,

No it looks like it is a serial tablet like we thought.  So I've attached a new xorg.conf with the changes I mentioned.  Install it.  Let's go ahead and install setserial also.  Use Synaptic Package Manager.  Search "setserial" and install it.  Reboot.

Then try the:
```
dmesg | grep ttyS
```
command.  If no output try it with sudo in front.

---

### Post by Fc1032 on 2009-04-25
Installed setserial, changed xorg, restarted comp and xserver.

ran 'dmesg | grep ttyS' with and without sudo, both had no output.

:(:(

---

### Post by Favux on 2009-04-25
Not good.  We need to know the equivalent to "/dev/ttyS0 port 0x338 irq 4".  We can guess everything is probably the same except the port.  We should have got the output without setserial.  Darn.  I googled, and can't find anyone reporting the line in any linux much less Ubuntu.  The M700 doesn't have a touch screen correct?

I guess we could start with the M700 line and hope.  If it doesn't work, maybe some guesses?  Not very satisfactory.  You could try a more exhaustive google search, or contact Toshiba.  You could also try running "dmesg | grep ttyS" a few more times, with and without sudo, and after rebooting and restarting X etc.  You could also try a complete uninstall of setserial and do the same thing.

As you can see I'm flailing around.  I've only seen the dmesg ttyS line not work a few times, usually when setserial is installed.

What do you want to try?

---

### Post by Fc1032 on 2009-04-25
Hello.

First off, toshiba m700 has touchscreen.

I'm going to try contacting the maker of the tutorial, since he/she has the tablet, he/she can probably answer the questions more definitively. Maybe he/she can help. Furthermore, will toshiba actually provide us with help installing ubuntu/linux? 

Should i uninstall setserial and try again?

---

### Post by Favux on 2009-04-25
Hi Fc1032,

Well let's try the M700 setting then.  If it doesn't work try dmesg every way you can think of.  I meant see if Toshiba would tell you the serial line details, like Irq=4 etc and most important port=.

The M700 wiki says at the end of /etc/rc.local add:
```
/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig
```
but this isn't the usual method.  So first we need to enter the /dev/ttyS0 (COM0) settings in "/etc/serial.conf". Add this to end of the file "serial.conf":
```
/dev/ttyS0 port 0x338 irq 4 autoconfig
```
and then do:
```
sudo /etc/init.d/setserial reload
```
you may need to reboot and restart X a few times for it to kick in.  Even if this doesn't work if we are very lucky there might be an error message that points us in the right direction.  So watch carefully.

Good luck!

---

### Post by Fc1032 on 2009-04-25
Hello!

In /etc/rc.local i typed the script/prompt two lines down from !bin/sh-e

I wasn't sure what it meant by end, so please check if it is right.

I opened up /etc/serial.conf using 'gksudo gedit /etc/serial.conf' in terminal. But i wanted to let you know that serial.conf was empty, just incase i might have done something wrong

I'll restart Xserver now and see what happens.

---

### Post by Favux on 2009-04-25
You only put "/dev/ttyS0 port 0x338 irq 4 autoconfig" in "/etc/serial.conf" correct?  Not in "/etc/rc.local"?  I was saying try the "standard" serial.conf first before we did what the wiki says.

---

### Post by Fc1032 on 2009-04-25
I have it in both... I'll remove it in the rc.local one then.

I'll give it another shot :)

BTW, the submitter of the youtube video with the ubuntu m700 sent me an email saying he/she is in the process of making a tut for how it was done. His/She's also trying out 9.04 too.

---

### Post by Favux on 2009-04-25
That could be real useful.

---

### Post by Fc1032 on 2009-04-25
Hi!

I got rid of the script in local.rc so that now only serial.conf has the script. I reloaded setserial with provided command.

I restarted x and the computer. but still no outpu from 'sudo dmesg | grep ttyS'

P.S I can't wait for the tut! he/she might also have one for jaunty :D. In the meantime, iam contacting the original tut person for help

---

### Post by Favux on 2009-04-25
Hi Fc1032,

It looks like a no go.  Always try the dmesg command without sudo first.

Good job on figuring out the gksudo gedit serial.conf command.  If it wasn't there from setserial you created it.

No reaction to stylus at all?  You could try it the way the wiki suggests, after removing the line in serial.conf.  I think the wiki line "/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig" goes below the last commented line and above "exit 0".  But maybe after it?  Notice that the line begins with "/bin/setserial" unlike when it is in serial.conf.  But you might want to hold off on that and see what happens through a few more reboots etc.  First you might want to try xxd again.

So too many variables.  The wrong port or irq or ttyS or linuxwacom isn't correctly installed.  Again I suggest we give it a break while you play around with things.  Maybe one of us will come up with a brainstorm.

---

### Post by Fc1032 on 2009-04-25
Hello!

Yea, lets give it a break for now. I won't be able to do much even if i had proper working examples because i have a few tests coming up in UNI.

I'll be fiddling around with the files probably a few days later after the major tests are over.

In the meantime i can wait for the youtuber tutorial and a response from the wiki tutorial maker :) I guess its a win-win?

I'm upgrading my old desktop to jaunty now too! Hope that goes well, desktops seem easier to handle :)

Thanks for all your input Favux! I'll see you round later!

---

### Post by X-Kent on 2009-05-13
Hi everyone.
I have ordered toshiba m750 and I should get it tomorrow. I already see all the road with unseen finish that I will need to pass to get the touch and pen working but anyway. Windows is no option. I will try to go through all the steps you mentioned before and see if I get any clues that could help. Do you have any updates on the issue ?

P.S.
To be more correct I will be installing 9.04 not 8.10.

---

### Post by Favux on 2009-05-13
Hi X-Kent,

I'm working on a serial .fdi for Jaunty, so good timing.  Hopefully that will get us around the need for the serial line.  Just to be clear the 750 has a serial Wacom digitizer that also features touch (finger).  Correct?

I think the two serial tablets with touch in the current 10-wacom.fdi are IBM's.  So we'd need you to type in a terminal:
```
lshal>lshal.txt
```
and then attach it to a post so we can get the identifier.

---

### Post by X-Kent on 2009-05-14
My laptop has arrived and I will install ubuntu on it as get home.
I will post the output of the program as soon as I have jaunty on it.
As far as my order was, it should support both touch and digitizer(pen)

---

### Post by X-Kent on 2009-05-17
here is the output of my lshal

---

### Post by X-Kent on 2009-05-17
ow, it didn't upload it at my first post, had to bzip2 it because it's 147kb txt and the limit is 19kb

---

### Post by Favux on 2009-05-17
Hi X-Kent,

Congratulations on installing Ubuntu Jaunty!  How do you like it so far?  Do you get anything from stylus or touch?  Let's see what, in a terminal, these look like:
```
xsetwacom list
```
and
```
xinput --list
```

---

### Post by Favux on 2009-05-17
Hi X-Kent,

Wow that is a pristine Wacom in HAL.  I don't think the default 10-wacom.fdi is installed.  Here's all there is:
```
udi = '/org/freedesktop/Hal/devices/pnp_WACf009'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (WACf009)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf009'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0c'  (string)
  pnp.id = 'WACf009'  (string)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x338'  (string)
```
And WACf009 is one of the identifiers for a Wacom tablet with touch.  Check Synaptics Package Manager.  Search wacom and make sure the Jaunty default 0.8.2-2 linuxwacom packages xserver-xorg-input-wacom and wacom-tools are installed.  Try rebooting.

Did you finish updating over the internet?

---

### Post by X-Kent on 2009-05-17
Hi, sorry for being not so active, pretty busy week for me :-(.
The output I provided is from jaunty without updates.
Just to confirm, Laptop had both touch and pen input on Vista Business that came preinstalled.
After jaunty installation, no touch/pen for now.
Didn't had time to update the system as I currently still work with my t41 and don't have access to my new laptop during the day. I will update and post outputs of the lshal and two other commands you requested about tomorrow.

---

### Post by Favux on 2009-05-17
Hi X-Kent,

Just be sure to run Update Manager first.  After that finishes try a reboot and see if the tablet is working.  You could then try the commands above.

I have a first pass at a new serial .fdi.  You might want to do:
```
lshal>before_lshal.txt
```
before trying the new .fdi.  The current "10-wacom.fdi" is at "/usr/share/hal/fdi/policy/20thirdparty/". Copy or move it someplace safe. And then rename it, say .fdi to .bak. Then replace it in "/usr/share/hal/fdi/policy/20thirdparty/" with the attached .fdi. After first renaming "10-wacom.fdi", of course. If after you reboot:
```
xsetwacom list
```
now returns linuxwacom names for your input devices like stylus, eraser, and touch you'll know it worked.  If not do:
```
lshal>after_lshal.txt
```
That would give us something to compare.

You can also look at other options in Jaunty Users near the top here: [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) Probably 3a would be the simplest.

Good luck!

---

### Post by X-Kent on 2009-05-17
Hi.
I updated the system (lshal_after_updates)
I figured out that nothing like "wacom" in installed and for some reason GUI package manager returns nothing when I searched for wacom, so I apt-get install wacom-tools and xserver-xorg-input-wacom packages (lshal_after_wacom-tools_install)
Still no touch/pen functionality.
I replaced the .fdi file (backed up original as well) and rebooted, still no touch/pen functionality.(lshal_after_fdi_file_change)
'xsetwacom list' gave no output :-(.
I did 'lsmod|grep wacom' and got no output here(wacom module should be loaded no?), after 'modprobe wacom' I tried 'xsetwacom list' again but still no output.
'xinput --list' is attached as xinput_list

I read the guide you gave me a link to, but it seems I should first get xsetwacom list to give me the names in order to start that guide.

---

### Post by Favux on 2009-05-17
Hi X-Kent,

Well something strange is going on.  Juanty installed the linuxwacom packages and .fdi on my desktop which doesn't have any Wacom.  Try Synaptic Package Manager again.  You should see the linuxwacom packages now.  Reinstall them and reboot.  Also the forum doesn't show you downloaded the modified .fdi yet.

But first see what you get with:
```
dmesg | grep ttyS
```

---

### Post by X-Kent on 2009-05-17
Ok I found this packages in synaptic (I thought add/remove programs is link to synaptic but figured out that it is different programs).
I reinstalled two programs.
wacom-tools and xserver-xorg-input-wacom

Still no touch/pen and all three command give nothing as output:
lsmod|grep wacom
dmesg|grep ttyS
xsetwacom list

currently my .fdi is the original one(reinstallation replaced yours?) I diff the backup copy and the current one and it's identical.

Forum seems to lag alot about downloads.

I attach my current lshal output in case you need it.
I don't get why wacom module doesn't loads itself on boot...

---

### Post by Favux on 2009-05-17
Hi X-Kent,

You might want to go back to the default Jaunty .fdi and see if that gives you anything.  Also check in Synaptics if setserial is installed.  That may be the problem.  I don't know if we need it installed or not.  So don't install it just see if it's there.  I'm doing some stuff on my desktop so it'll be a while before I can boot into Jaunty.  You might also want to look at "lspci" and see if any Wacom stuff shows up.

---

### Post by Favux on 2009-05-17
Hi X-Kent,

Important news.  Arestivo on the other thread confirmed that the setserial line "/dev/ttyS0 port 0x338 irq 4 autoconfig" from the M700 laptoptesting wiki worked for his M750 in Intrepid.  So we know the important parameters now and one way or another should be able to get Ubuntu working on your laptop.

In Jaunty I looked upstream from the "10-wacom.fdi" to the "10-tabletPCs.fdi" in "/usr/share/hal/fdi/policy/10osvendor" and the "20-video-quirk-pm-toshiba.fdi" in "/usr/share/hal/fdi/information/10freedesktop/".  I don't see anything that should concern us there or elsewhere.  So I'll start looking at your stuff.  Have you come up with an explanation as to why wacom wasn't installed?  By the way on my desktop only xserver-xorg-input-wacom was installed, not wacom-tools.

---

### Post by X-Kent on 2009-05-19
Hi.
After re-installation of wacom packages the .fdi file was replaced with the original one, so for now my system uses the original file.
I will try to follow the instructions in the guide with the set serial trick and report if I get anything.
Currently, for some reason 'wacom' module didn't load(and I think it should) at boot so I added it to /etc/modules and now it loads.

---

### Post by X-Kent on 2009-05-19
Hi again Favux.
I have tried to follow the guide for interpid, I skipped the driver upgrade part as I believe jaunty should contain the more recent version of the wacom than interpid.

I have edited rc.local and xorg.conf.
After reboot I get a blue screen with random vertical lines. After a bit of playing I found out that it 'crashes' only if the 'input' lines in 'Server Layout' section are present, so I commented them out for now.
One interesting thing I found out during the time that X was 'crashing'(giving random vertical blue lines):
I ctrl+alt+shift+f1 and logged on in console, checked dmesg and /var/log/messages for any clues and here is the lines that were interesting in dmesg:

[   24.369648] Xorg[3136]: segfault at 10 ip 00007f767e60cc35 sp 00007fff8acd1fc0 error 4 in wacom_drv.so[7f767e5fe000+16000]
[   24.392253] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
[   29.374071] [drm:i915_setparam] *ERROR* unknown parameter 4
[   30.889275] Xorg[3157]: segfault at 10 ip 00007f71d810cc35 sp 00007fffe47d1ac0 error 4 in wacom_drv.so[7f71d80fe000+16000]
[   30.912248] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0

Seems like a segmentation fault in a wacom driver :-(.
I will now try and download the latest version of the wacom package and see if it fixes it but that's it for now.
I am attaching my /var/log/messages, dmesg output, xorg.conf and rc.local files
(messages and dmesg output durring the time X was crashing with segfault)

By the way, I found something that may confuse newbies in that guide, it says to put the line with /usr/bin/setserial at the END of the rc.local file but it already has exit 0 at the end so if you put it after exit it will not get executed...

edit:
my wacom-tools and xserver-xorg-input-wacom packages are both version 1:0.8.2.2-0ubuntu2

---

### Post by Favux on 2009-05-19
Hi X-Kent,

> By the way, I found something that may confuse newbies in that guide, it says to put the line with /usr/bin/setserial at the END of the rc.local file but it already has exit 0 at the end so if you put it after exit it will not get executed...
Right, that's part of the reason I asked Fc1032 on page 6 to do it the way I showed him in post #52.
> After reboot I get a blue screen with random vertical lines. After a bit of playing I found out that it 'crashes' only if the 'input' lines in 'Server Layout' section are present, so I commented them out for now.
I thought the crashing with Xorg was just due to the switch to the HAL/.fdi method.  But it may be a bug.  There's a bug report with a patched xorg-xserver that seems to have fixed the xorg.conf problem for a couple of Jaunty posters.

> I will now try and download the latest version of the wacom package and see if it fixes it but that's it for now.
It sounds like you've decided to blow off the HAL/.fdi method and go with xorg.conf which is totally reasonable if you don't need hotplugging.

You have to download at least linuxwacom 0.8.3-2 because that's the first to support the Xserver 1.6 in Jaunty.  In which case you should be able to use xorg.conf normally, with "ServerLayout" back in.  I assume you've compiled 0.8.3-4 which is the latest.  When you compile be sure libhal1-dev is not installed (it isn't installed by default) otherwise HAL support will be added.

I want you to be aware that Ron updated the “50-xserver-xorg-input-wacom.rules” on 3-29-09.  They contain the Wacom symlinks that are suppose to be in “/etc/udev/rules.d/”.  It is recent enough that I bet it contains the M750's symlinks.  That means instead of the ttyS0 lines in xorg.conf you could use "/dev/input/wacom" and "/dev/input/wacom-touch".

At least with some serial tablets it seemed all they needed was the right symlink in udev.  Then they didn't need to bother with the setserial line.  See Appendix 3 here (from Section 2 above):  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by X-Kent on 2009-05-19
I removed wacom-tools and xserver-xorg-input-wacom packages
I have downloaded and compiled 0.8.3-4
Same result.
Uninstalled 0.8.3-4 and apt-got the packages back.
I have libhal1 but not libhal1-dev installed (now and when I was compiling)

I don't really understand the differences between the HAL/.fdi methods and xorg.conf method, can you explain what do you mean by "crashing with Xorg was just due to the switch to the HAL/.fdi method" as I don't really know how to solve this crash and continue from here or diagnose it further.

If I reached a dead end. I would like to try the method described by the link you provided in your last post. Should I undo all the xorg.conf and rc.local changes before starting ?

---

### Post by X-Kent on 2009-05-19
Humans are humans....

I skipped the /dev/ttyS0 argument in my rc.local.... so the device didn't attach.
I put it there and touch + stylus are working perfectly !!!
Thank you very much.

For future m750 owners:
Follow the tutorial for interpid, skip the compiling, all you need is adjust xorg.conf and rc.local

Don't use rc.local that is inside my last attached file, /dev/ttyS0 argument is skipped there !

If someone needs my help to help with his m750, feel free to write to me: [email]mynick@mynick.com[/email]
replace mynick with my real forum nickname.

Special thanks to Favux !

---

### Post by Favux on 2009-05-20
Hi X-Kent,

Outstanding work!  Really nice job.  That was a tough one to crack.

So to summarize for the Toshiba M750 in Jaunty:
1)  Use the default Jaunty linuxwacom 0.8.2-2 packages.
2)  Follow the M700 Intrepid tutorial here:  [https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaPortegeM700) and:
2a)  Install setserial.
2b)  Add this line at the end of "/etc/rc.local" (but before exit 0):
```
/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig
```
2c)  Add the xorg.conf sections for "stylus", "eraser", and "touch" as shown and add to "ServerLayout":
```
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "touch"        "SendCoreEvents"

```

Do I have it right?  Are you able to calibrate and configure with "wacomcpl"?

---

### Post by X-Kent on 2009-05-20
Clarifications:
it's the default jaunty .fdi
xorg.conf should be exactly as shown in the tutorial

I was commenting out the "input" options inside "server layout" section for debugging purposes.

Working xorg.conf file for M750 is attached

Feedback so far:
Pen button and calibration for both pen and touch is working.
Eraser(the top button of the pen) doesn't seem to respond to anything but I never found what it's for in vista too.

---

### Post by Favux on 2009-05-20
Hi X-Kent,

In Gimp and Inkscape you have to configure their extended input devices options to get the eraser to work.  A little more on it at the bottom of the Wacom wiki or post #8 here:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)  In Xournal the eraser is your stylus button.  And if you haven't already try CellWriter.

---

### Post by Favux on 2009-05-20
Hi X-Kent,

Ha, so my test xorg.conf would have worked for Fc1032!  Well after removing the comments from touch.

By the way I think you can probably remove the:
```
        Option          "Mode"          "absolute"
        Option          "SendCoreEvents"        "true"
```
lines from your xorg.conf wacom sections.  Those should be default now with the "modern" linuxwacom/Xorg xserver.  They were needed back with Gutsy or Feisty.

So the mystery is why did xorg.conf with entries in "ServerLayout" start working for you?  I wonder if there was an update in the last day or so.  Similar to the xorg-xserver patch I mentioned.

---

### Post by X-Kent on 2009-05-24
It started working for me because as I said, a simple human mistake.
I mistakenly omitted the "/dev/ttyS0" parameter when I was editing my rc.local so the /dev/ttyS0 didn't get attached to the interface. When I was trying to use /dev/ttyS0 (by uncommenting the lines inside server layout) X was crashing because my /dev/ttyS0 wasn't attached.

---

### Post by Favux on 2009-05-24
Hi X-Kent,

I'm just glad it's working.  I got the "/dev/ttyS0" part.

What I was saying earlier is the X was crashing in Jaunty if you used xorg.conf with the "default" linuxwacom packages.  Timo's ppa xserver-xorg-core fixed it for at least some folks.  Bug report:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358643](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358643)

---

### Post by X-Kent on 2009-05-27
For now, touch and pen is functioning properly(except some weird lines I sometimes get in xournal), I still have some sound quality problems and can't get mic to work(just no time to figure it out, maybe just volume somewhere) but I thought it will be much more pain to set all this stuff up. Even gprs with PAN to wm6 gateway over bluetooth took only minutes to setup compared to what I had to pass to get debian woody connected to nokia.

Long story short, you can count m750 as one that is supported by ubuntu. I am using Linux since red hat 6.2, it was never as friendly as it is now.

Keep up the good work and many thanks for your support !

---

### Post by Fc1032 on 2009-06-22
Oh! Its that thread i started ages ago =)

I'm sorry i just left it alone... I just recently finished my exams for first semester =)

Nice to see that the m750 is now supported =)

I'll have to update to jaunty to see how things are going, im still on 8.10 =( 

=D Favux you rule!!~ I'll start to fiddle with ubuntu again after my update =)

---

### Post by Yonco on 2009-06-22
Great work guys. 
I followed your instructions and everything worked great. 
I think I found a solution for the mic thingy. check out your post about it. 
another issue I'm struggling with is the intel graphics support. 
I tried following the instructions on 
[http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)
Which improved graphics performance but crushed all the time. 
so I reverted back to the normal kernel and drivers. 
any help on that topic will be welcome.
I'm also stuck with the jumps in Xournal 
and another thing I'm wondering about is if the accelerometer and HD protection are supported. 
all the best.
Yoni

---

### Post by Favux on 2009-06-22
Hi everyone,

A stray thought occurs.  Is it possible that Xournal is just too sensitive to touch?  Why not try turning touch off before starting it to check this out.  In a terminal enter:
```
xsetwacom set touch touch off
```
and then start Xournal.  To restart touch change off to on.

---

### Post by Yonco on 2009-06-25
nope.
didn't work.
its not like we're accidentally pressing with the touch while using the pet. its as if its sending a point in the to corner of the screen. 
my guess is that it has to do with the stylus being pressure sensitive. and the fact its using a serial interface through a usb. 
in windows the stylus on the m750  is not defined as pressure sensitive in the preinstalled system. 
I think I read something about it somewhere.

---

### Post by Favux on 2009-06-25
Hi Yonco,

Too bad.  I'd read somewhere that Xournal could get wonky with touch present.

The last release of Xournal was 3-27-08 4.2.1.  A shame.
[http://xournal.sourceforge.net/](http://xournal.sourceforge.net/)
[https://launchpad.net/ubuntu/+source/xournal](https://launchpad.net/ubuntu/+source/xournal)

I know there was the Gtk+ offset bug.  I guess there are some patches around to "update" it.

---

### Post by Fc1032 on 2009-06-25
Hello everyone!

I finally got the pen and touch working on my tablet!! 

I followed the instructions from page 8.
1) Installed Jaunty
2) Ran update manager, install updates
3) Installed set serial and wacom tools
4) added "/bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig" at the end of /etc/rc.local but before exit 0
5) Used xorg by x-kent on post 80
6) restarted!

7) For others like sound followed [https://wiki.ubuntu.com/LaptopTestin...ibaPortegeM700](https://wiki.ubuntu.com/LaptopTestin...ibaPortegeM700) (post #79)

Done =) so happy ubuntu has touch now! Had so much fun playing with water effect and touch =), I just need to get the screen rotation fixed but all good for now!! 

Special thanks to Favux and X-Kent!!



Many thanks,
FC1032

---

### Post by Favux on 2009-06-25
Hi Fc1032,

And the long and winding road comes to a successful end!  Hurrah!

---

### Post by Fc1032 on 2009-06-25
Hello Favux!

Many thanks to you!!

I couldn't find the "solved" function anymore so i declare this thread solved =)

Thanks again =)

---

### Post by Fc1032 on 2009-07-20
Hello all,

The maker of the youtube video got back to me, he made a video of how he got the sound, pen ,touch to work.

Even thought the steps are written out, i just wanted to share his video with all the tablet pc users out there. Some of us are more visual so here it is:

[http://www.youtube.com/watch?v=8UuxojCf9RU&fmt=22](http://www.youtube.com/watch?v=8UuxojCf9RU&fmt=22)

And here is another video showing how to make the ubuntu better looking on the tablet

[http://www.youtube.com/watch?v=8q79gkMqS5w](http://www.youtube.com/watch?v=8q79gkMqS5w)

Thanks again =)

---

### Post by erik.kugel on 2010-05-05
Hi guys, just wanted to say post 91 pretty much nailed the instructions, and they  worked like a charm (with minimal adaptations) on Slackware 13.

Thanks! ;)

---

