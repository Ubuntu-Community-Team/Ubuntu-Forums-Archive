---
title: "Need Help with Fujitsu T4010 wacom digitizer setup in Intrepid"
date: 2009-02-20
forum: Hardware
---

### Post by dciliske on 2009-02-20
So, looking at all other posts and threads pertaining to setting up a tablet's digitizer, it requires some mucking around in xorg.conf. It seems there's a bit of a problem with that now with Intrepid. This is the entirety of noncomments in my xorg.conf:
```
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
```

So, I tried simply adding the various device sections as instructed in other How-To's on Fujitsu digitizers, but that simply killed my graphics.

Most trials were from this thread, 

[http://ubuntuforums.org/showthread.php?t=110050&highlight=fujitsu+tablet](http://ubuntuforums.org/showthread.php?t=110050&highlight=fujitsu+tablet), 

but it seems to have lost updates after Hardy. 

So, I ask, does anyone have experience with setting up an older tablet digitizer under Intrepid, and what do I need to do?

---

### Post by Favux on 2009-02-21
Hi dciliske,

Hopefully the attached xorg.conf will work for you.  You then should be able to follow the rest of the instructions.  In their xorf.conf they were using the "cursor" section which is for the Wacom external tablet hockey puck mouse which you shouldn't need.  I also edited out a couple of lines that should be default in the stylus and eraser sections.

From what they had I'm assuming your stylus has an eraser.  Does it have one or more buttons?

---

### Post by aussiedwarf on 2009-02-22
Well I just got my pen working (again) on my t4010 after a complete wipe of the hard drive. All I did was install wacom tools, add some lines to the xorg and did a restart.

I added these lines to the the xorg after the screen section. Most of it is from [here]("https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D") with a little modification. I added Option "button2" "3" and Option "Button1" "2" just to get the buttons on the stylus to do what I wanted.

```

Section "Module"
	Load		"wacom"
EndSection

# These lines should go after the detected mouse and touchpad
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/ttyS0"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "cursor"
        Option          "Mode"          "absolute"
        Option          "Speed"         "3.0"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/ttyS0"
	Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
	Option		"button2"	"3"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/ttyS0"
	Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
	Option		"Button1"	"2"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"cursor"		"SendCoreEvents"
	InputDevice	"stylus"		"SendCoreEvents"
	InputDevice	"eraser"		"SendCoreEvents"
EndSection

```

I got automatic screen rotation and buttons working by getting the by getting the Distribution Packages for intripid from the [fjbtndrv project]("http://fjbtndrv.wiki.sourceforge.net/") and installing them. I never got auto rotation or the buttons to work so this is a first for me.

I just got it all working then so hopefully it should all go well for you.

---

### Post by Favux on 2009-02-22
Hi aussiedwarf,

Thanks for joining the thread and helping out, I appreciate it.  Like I mentioned to dciliske you don't need the "cursor" section and the "cursor" line in "SeverLayout".  I'm glad your system now seems stable.

So there are two buttons on the stylus?  You have one configured as a middle mouse click and the other as a right click?  The "module" section is interesting.

The link for the buttons, etc. should be very helpful.

---

### Post by Favux on 2009-02-22
Hi,

I found some links that may also be useful.  From the LaptopTestingTeam:

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D]("https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D")

At TuxMobile I found several links (at the bottom), one is the thread you already have and the other to the link above:

[http://tuxmobil.org/fujitsu.html]("http://tuxmobil.org/fujitsu.html")

But the last one is to a T4220 wiki:

[https://help.ubuntu.com/community/T4220]("https://help.ubuntu.com/community/T4220")

---

### Post by M@s on 2009-03-08
[Continued from here: [http://ubuntuforums.org/showthread.php?p=6856438#post6856438](http://ubuntuforums.org/showthread.php?p=6856438#post6856438)]

[QUOTE=Favux]Does your stylus have an eraser? Does the stylus have buttons on it? If so how many?[/QUOTE]
No erasor, but two buttons (which both worked with [this config, edited for Tablet PC](https://help.ubuntu.com/community/WacomTroubleshooting)).

[QUOTE=Favux]Is a Fujitsu Lifebook 4010D the same model?[/QUOTE]
I've been searching but can't find any other difference but the WLAN card. So I think they are equal in this case.

Thanks for taking your time! :)

---

### Post by Favux on 2009-03-08
Hi again M@s,

No eraser, important to know.  As you can see from above aussiedwarf seems to have one.  Attached to the bottom of this post is a test xorg.conf.  I've removed the pad and cursor sections since they don't apply to a tablet pc.  I've removed the eraser section since you don't have one.  I added a second button to stylus but since I don't know how they work I've left only one button "on", it should give you a right mouse click.  If that's how you want that button we can then experiment with the other button.  Be sure to describe where the buttons are on your stylus.

I've commented out:
```
#	Option		"UseFBDev"		"true"
```
because we don't know what it is for.

With Intrepid Ubuntu started moving to HAL (hardware abstraction layer).  It is running your keyboard and mouse.  Do you have a "Synaptics TouchPad"?  All three sections in that order should appear above your stylus section if you were using Hardy or earlier.  So if you find examples of them around you could/should place them in your xorg.conf commented out (and their "ServerLayout" entry, if any) and in your backup.

Be sure to backup your xorg.conf and compare the test one to your current one.  Check to see what I did and whether I made any errors.

Edit:  I've looked through the link you gave and can't find anything relating to stylus buttons.  If the xorg.conf isn't working correctly and X is not getting any input HAL might be running your stylus through its .fdi file.  I haven't seen HAL support stylus buttons before.  But if the .fdi file in your system is giving button support then HAL may be all you need.  You don't have an eraser or touch after all.

---

### Post by M@s on 2009-03-09
It works! Excellent! :D

Now both buttons perform a right click. On Windows I had one button configured to act as eraser, is this possible to achieve?

[quote=Favux]Be sure to describe where the buttons are on your stylus.[/quote]
They are located on the side of the stylus, accessible through a single switch (as you can't press both at the same time).

[quote=Favux]With Intrepid Ubuntu started moving to HAL (hardware abstraction layer). It is running your keyboard and mouse. Do you have a "Synaptics TouchPad"? All three sections in that order should appear above your stylus section if you were using Hardy or earlier. So if you find examples of them around you could/should place them in your xorg.conf commented out (and their "ServerLayout" entry, if any) and in your backup.[/quote]
I'm not sure what you mean. I don't know if I have a "Synaptics TouchPad", how do I find out? Or do you mean if I have it in my xorg.conf?

[quote=Favux]I've looked through the link you gave and can't find anything relating to stylus buttons. If the xorg.conf isn't working correctly and X is not getting any input HAL might be running your stylus through its .fdi file. I haven't seen HAL support stylus buttons before. But if the .fdi file in your system is giving button support then HAL may be all you need. You don't have an eraser or touch after all. [/quote]
Hmm, OK. Well, both buttons worked with that config, and they acted as right click vs scroll click.

---

### Post by Favux on 2009-03-09
Hi M@s,

Great!  Progress.  Did it clear up your video issue on booting?

First a link to the Wacom wiki:  [https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")
That link has a link to the Wacom.fdi wiki:  [https://help.ubuntu.com/community/Wacom.fdi]("https://help.ubuntu.com/community/Wacom.fdi")
Which will help explain what I'm talking about with HAL and .fdi files.  If you look at the default wacom.fdi file there aren't any button entries in it.  I'm not sure if they are allowed because only one "input" is allowed, as I understand it.

We may have to experiment with the buttons to get what you want.  But I'm interested in trying if you are.  First try changing in xorg.conf:
```
#	Option		"Button1"	"2"
	Option		"Button2"	"3"  # make side-switch a R button
```
to
```
	Option		"Button2"	"2"  # make first button a middle button
	Option		"Button3"	"3"  # make second button a R button
```
This would be test 2 of your xorg.conf.

Let me know how they behave.  The second button should act as an eraser in Xournal.  That is because Xournal uses the right mouse button as the eraser.  What other programs do you need an eraser in?

The Synaptic Touchpad would be the "mouse" built into your laptop.  The little pad at the front that tracks your finger movements and has "mouse" buttons.  Your "mouse" pad may not be a Synaptics one.  Synaptics is just a common manufacturer.

Edit:  By the way I want to be sure you noticed the link by aussiedwarf to get bezel buttons and screen rotation at:  [http://fjbtndrv.wiki.sourceforge.net/]("http://fjbtndrv.wiki.sourceforge.net/").  He should be able to help if you have questions.

---

### Post by M@s on 2009-03-09
Hi Favux!

Yes, it now works like a charm. I edited those lines you gave me, and that works too. It seems like Xournal uses both middle and right click as eraser, so erasing works with both buttons.

I mostly use Gimp for painting, but it don't use right/middle as eraser and I don't find an option to change it. Is Gimp only able to use a real eraser on the stylus for erasing? Is it possible to set a button to act as an eraser instead of mouse click?

Oh, you mean the touch pad. I thought you meant something about the Synaptic Package Manager. I do have a touch pad, but I don't know if Synaptic is the manufacturer.

Thanks for the notice, I did install fjbtndrv before this Ubuntu installation, and it worked without problems!

---

### Post by Favux on 2009-03-09
Hi M@s,

Good deal.  Since my stylus has only one button I didn't know the middle button was also eraser in Xournal.

Getting eraser in Gimp looks tougher.  If you've noticed when you go to Edit>Preferences>Input Devices>Configure Extended Input Devices and pick say stylus there is a Keys tab.  If we can get a keycode from your buttons maybe we can map a key to eraser?  Also above the Input Devices there is Interface.  It also has keyboard shortcuts.

My stylus button does not seem to be returning a useful keycode.  What I am getting is:
```
ButtonPress event, serial 34, synthetic NO, window 0x4a00001,
    root 0x1a6, subw 0x4a00002, time 122905116, (31,14), root:(836,72),
    state 0x0, button 4, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x4a00001,
    root 0x1a6, subw 0x0, time 122905116, (31,14), root:(836,72),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2048

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967206 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 34, synthetic NO, window 0x4a00001,
    root 0x1a6, subw 0x4a00002, time 122905116, (31,14), root:(836,72),
    state 0x800, button 4, same_screen YES

LeaveNotify event, serial 34, synthetic NO, window 0x4a00001,
    root 0x1a6, subw 0x0, time 122905116, (31,14), root:(836,72),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

```
Why it's called button 4 I do not know.  But I am not getting eg. "keycode=26" buried in there.

But maybe you'll get lucky.  Type "xev" in a terminal and then press your buttons.  You'll also get a lot of output due to stylus motion so try to hold still.

Also xorg.conf is suppose to allow buttons to map to other events, not just mouse buttons.  I'll take a look at that, but I think we'll need a lot of luck to get that working.

Also this quote:
> You will experience this when you try to use your eraser for the first time. Rather than selecting the eraser tool, you get the rectangle selection tool instead. This is by design, believe it or not. Gimp does not care that its an eraser, just that it's not the pen you were just using. If you choose the eraser tool now, it will remember that for the next time you try to use it.
almost makes me think if we were clever enough, we might be able to make the rectangular selection tool accept a button as eraser.  The link is here:  [http://linuxwacom.sourceforge.net/index.php/howto/gimp]("http://linuxwacom.sourceforge.net/index.php/howto/gimp")

---

### Post by Favux on 2009-03-09
Hi again M@s,

I may have just figured it out.  In Gimp the keyboard shortcut for eraser is "shift e".  So you may be able to do:
```
xsetwacom set stylus button2 "key core shift e"
```
Run this in a terminal before launching Gimp and see what happens.  You could get a launcher to run it as a shell script.  Then you could run another to set it back.  Or if you wanted it permanent you could place it in your ./xinitrc.  In xorg.conf I think it would look like:
```
Option		"Button2"	"key core shift e"  # make first button eraser in Gimp
```

If you try it let me know how it works.

---

### Post by M@s on 2009-03-10
Hi Favux!

Interesting! The Shift-E option works fine for switching to eraser tool, but not for changing back again. Is this even possible this way, with the same button? One way could be assigning the other tools shortcut to the other button, but I don't know if that's a good idea because I want at least one button to work in other programs too (with right clicking, for example).

I don't get a keycode from xev neither. I'm getting this for button 2 and similar for button 3:
```
EnterNotify event, serial 34, synthetic NO, window 0x3a00001,
    root 0x79, subw 0x0, time 795608, (23,48), root:(694,99),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 512

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  121 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ConfigureNotify event, serial 34, synthetic NO, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, (669,49), width 178, height 178,
    border_width 2, above 0x380000a, override NO

LeaveNotify event, serial 34, synthetic NO, window 0x3a00001,
    root 0x79, subw 0x0, time 795624, (23,48), root:(694,99),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 512

ButtonPress event, serial 34, synthetic NO, window 0x3a00001,
    root 0x79, subw 0x3a00002, time 795608, (23,48), root:(694,99),
    state 0x0, button 2, same_screen YES

EnterNotify event, serial 34, synthetic NO, window 0x3a00001,
    root 0x79, subw 0x0, time 795624, (23,48), root:(694,99),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 512

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  121 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ConfigureNotify event, serial 34, synthetic YES, window 0x3a00001,
    event 0x3a00001, window 0x3a00001, (669,49), width 178, height 178,
    border_width 2, above 0x100103d, override NO
```

Thanks again! :)

---

### Post by Favux on 2009-03-10
Hi M@s,

I ran into the same problem.  It seems it is due to how Gimp handles tool selection.  In other words it doesn't let you "grab" the tool with a button press signal and then release the tool with a button release signal.  It just changes the tool selection.  If there is a way to change it's behaviour I don't know what it is.  Actually I think this would be fairly simple to code (the change in handling button press and release signals), but then we would have to get one of the Gimp dev.s interested and the rest to agree.  I don't see a way to do it through X.  Gimp got very angry with me when I tried to use xsetwacom commands when it was running.

Just like my button output I don't see a convienent way to use your xev output to use your buttons.

You are also right that you would have to use your other button.  I can't do that of course, but then I have an eraser.  We could assign it say paintbrush (P) or whatever tool you most commonly use.  We would have to do a script that does that before you run Gimp (starting Gimp could be in the script) and then another script to change the buttons back to normal after you're done with Gimp.

I know that some other folks have described doing something similar for their setups.

---

### Post by M@s on 2009-03-14
Hi Favux!

I've now run into another problem... the tablet isn't working anymore! I have no idea why, I haven't been changing any settings since last time. The xorg.conf is correct, and I've unprosperously tried to reinstall xserver-xorg-input-wacom and wacom-tools.
Perhaps it stopped working after a hibernate (not sure), but a reboot didn't solve the problem.

Due to the eraser problem, I've been looking for a Gimp alternative that supports right click as eraser, just like Xournal but for pixel based graphics. Do you if there is such a program?
If I don't find any, maybe it would be easier for me just to press the eraser tool button in Gimp instead of creating and executing bash files. ;)

---

### Post by Favux on 2009-03-14
Hi M@s,

I don't think there is anything comparable to Gimp.  But there are a few Gimp modifications around.  Maybe these handle tools differently?
[http://www.gimpshop.com/]("http://www.gimpshop.com/")
[http://www.gimphoto.com/2007/08/about.html]("http://www.gimphoto.com/2007/08/about.html")
> maybe it would be easier for me just to press the eraser tool button in Gimp instead of creating and executing bash files.
Probably, it depends on your work flow I suppose.

Loss of stylus.  Which version of linuxwacom did you have installed when things were working?  0.8.1-6?  I need to know more about what you did to install the drivers.  Since it sounds like you installed multiple versions that is probably complicated.  If you had remnants of a different version around that could have led to a problem.  You would have to be sure the previous version was purged.  According to the LWP if you have different versions of the linuxwacom driver and linuxwacom tools bad things can happen, including crashes.  Another thing to try is to change the dev/input/wacom line to the dev/ttySO line in xorg.conf and see if that gives you a signal.

---

### Post by M@s on 2009-03-14
Hi Favux,

Thanks, I will take a look at those mods. I guess there is a lot of Wine compatible painting programs too that maybe could solve this problem. I read that Photoshop will run through Wine.

The working installation was 0.8.1.6-1. The procedure was:
1. Configure serial ports according to [this guide](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuT4010D).
2. Installing [these](https://help.ubuntu.com/community/Wacom?action=AttachFile&do=view&target=wacom-tools_0.8.1.6-1ubuntu2_i386.deb) [two](https://help.ubuntu.com/community/Wacom?action=AttachFile&do=view&target=xserver-xorg-input-wacom_0.8.1.6-1ubuntu2_i386.deb) files.
3. Changing xorg.conf with the one you put together.
4. Reboot

But this was working well with several reboots, I can't understand why it suddenly just wasn't working.

My re-installation was the following:
1. apt-get remove setserial xserver-xorg-input-wacom wacom-tools
2. Reboot
3. Install again as seen above.

Have I screwed things up now?

Changing the /dev/input/wacom line made no difference.

---

### Post by Favux on 2009-03-14
Hi M@s,

I can't see why you would have lost wacom.  What else did you install if anything?

Try rebooting several times.  Also try restarting X several times:  <ctrl><alt><backspace>.  Sometimes the drivers (at least the kernel driver) doesn't load correctly.  See if that brings wacom up with the wacom input line.

You must have had symlinks somewhere for the input/wacom line to work.  Presumably installed with the 0.8.1-6 Wacom deb.s.  Try in a terminal:
```
more /proc/bus/input/devices
```
And see if you get any entries like:
```
I: Bus=0003 Vendor=056a Product=0093 Version=0330
N: Name="Wacom ISDv4 93"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input10
U: Uniq=
H: Handlers=mouse2 event10 
B: EV=b
B: KEY=3c03 0 0 0 0 0
B: ABS=1000100001b

```
If you do see if you have a file at etc/udev/rules.d/50-xserver-xorg-input-wacom.rules (this is the file that establishes symlinks, at least for usb, maybe serial is different?).  In it see if there is in there an entry that matches your Vendor and Product ID's.

---

### Post by M@s on 2009-03-15
Hi Favux,

Hmm. As far as I remember I installed Wine (and then ArtRage 2 with it), VLC, KeePassX, Inkscape, StarDict. Nothing that should be able to cause this problem I guess?

The X restarting and rebooting didn't bring wacom up, nothing happened.

I tried executing that command in a terminal but doesn't give me any "wacom" entries at all...

---

### Post by Favux on 2009-03-15
Hi M@s,

I have no idea why you've lost Wacom.

Let's summarize:
-You checked in Synaptic Package Manager that setserial, linuxwacom and linuxwacom-tools are present?
-You checked that your /dev/ttyS0 line was present in /etc/serial.conf?
-You installed linuxwacom 0.8.1-6 using the deb.s at Loic2's Wacom wiki.  You then reinstalled them.
  Did you try going to Synaptics Package Manager and completely uninstall them?  Then reinstall them (maybe from a fresh download)?
-No wacom entry with the more /proc etc. command.
-Did you update to a new kernel?  That shouldn't make a difference.
-You've dead ended on figuring out where your wacom symlink is located.
Try:
```
dmesg | grep [Ww]acom
```
Also try:
```
dmesg | grep ttyS
```
This should give you output like:
```
/dev/ttyS0 port 0x220 irq 4
```
and see what:
```
ls /dev/ttyS*
```
looks like.  This should tell you the serial ports available.  I don't see how the active serial port could have changed.  Unless you deliberately changed it with setserial.  To find the active port you can use xxd. The program xxd will exit for devices not listed, otherwise CTRL and C to quit. Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc. Bring the pen to the screen an move it around. You know you have the right ttyS* when you see a reaction with an output of characters. That's the ttyS* you want to use in xorg.conf. In a terminal type:
```
xxd /dev/ttyS0
```
changing to S1, etc.

That's about all I can think of.  Unless your /dev/ttyS0 line needs baudrate too?  But why did it work without it?

---

### Post by M@s on 2009-03-16
Hi Favux!

*-You checked in Synaptic Package Manager that setserial, linuxwacom and linuxwacom-tools are present?*
Yes they are.

*-You checked that your /dev/ttyS0 line was present in /etc/serial.conf?*
Yes it is:
/dev/ttyS0 port 0x220 irq 4 autoconfig

*-You installed linuxwacom 0.8.1-6 using the deb.s at Loic2's Wacom wiki. You then reinstalled them.*
Yes.

*Did you try going to Synaptics Package Manager and completely uninstall them? Then reinstall them (maybe from a fresh download)?*
No, I uninstalled them with "apt-get remove" and then reinstalled them. But now I tried to completely uninstall them and reinstall them from a fresh download, but it still doesn't work.

*-No wacom entry with the more /proc etc. command.*
No, I've triple-checked it.

*-Did you update to a new kernel? That shouldn't make a difference.*
Not that I know of. Maybe I ran the update manager, does it update the kernel? My version is 2.6.27-11.

And the commands:
*dmesg | grep [Ww]acom* gives me nothing.

*dmesg | grep ttyS* gives me:
```
[    1.986420] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
[    1.987077] 00:08: ttyS0 at I/O 0x220 (irq = 4) is a 16550A
```Not exactly like the output you suggested...


The available serial ports are ttyS0-ttyS3. With xxd I found out that ttyS0 is the active port, so it hasn't changed.

> Unless your /dev/ttyS0 line needs baudrate too? But why did it work without it?Sorry, but I've checked in all my dictionaries and can't find out what "baudrate" means, unless you mean "baud rate" wich is translated into something like "transfer speed". If that's correct, then I still don't know what you mean... :)

Which /dev/ttyS0 line by the way, the one in the serial.conf or xorg.conf? Hasn't it been there all the time?

Thanks again for all help.

---

### Post by Favux on 2009-03-16
Hi again M@s,

Update manager will update the kernel.  But you have the latest.  Kernel 2.6.27-13 is in pre-release, but that doesn't mean we will get it.

Do you have a windows partition?  Does the stylus work in Windows?

I meant the ttyS0 in setserial.  The output from dmesg | grep ttyS and the results from xxd are good news.  They mean everything is in place and we should be able to get it working (if we're smart enough-lol).

Try:
```
sudo /etc/init.d/setserial reload
```
before we do anything else.

And let me see your xorg.conf (attach to next post).

---

### Post by M@s on 2009-03-17
It's alive! :D

The setserial reload seems to have solved the problem. But it's very unpredictable... this was my procedure:

1. Reload setserial.
2. Restart X, tablet's still not working.
3. Restart X again, now it works!
4. System reboot, now it's not working again.
5. Restart X once, it works!
6. Reboot, now it works immediately!
7. Reboot again, it keeps working.

I've been hibernating and rebooting about 5 times now, and it seems to work all the time. Now let's hope this continues. My xorg.conf is now exactly the one you gave me, since I tried reinstalling wacom from scratch the last time.

I think I will configure the buttons back to normal (right and middle mouse) and search for other painting programs that is able to handle mouse buttons as eraser.

---

### Post by Favux on 2009-03-17
Hi M@s,

Outstanding!  Nice job.  Clever the way you persisted after the setserial reload.  Thanks for posting your procedure.  I have my fingers crossed.

To answer your question about baud rate (sorry, I meant baud base).  Some serial tablets would want a line something like:
```
/dev/ttyS0 uart 16550A port 0x220 irq 4 baud_base 34800
```
The baud_base can be different.  Notice no autoconfig.  I don't know if that doesn't work for them or they're inadvertently using an old type of configuration that they don't need anymore (if they use setserial's autoconfig).

If you find a paint program you like please let me know about it.

---

### Post by M@s on 2009-03-17
Hi Favux!

Thank you. Now i'm a bit more clever about baud base.

If I find a program I'll post it here, but no luck so far. I've tested Photoshop CS2, ArtRage 2, Sketchbook Pro and Gimpshop.

Once again, thanks for all help. Really appreciate it.

By the way, I'm trying to get fjbtndrv working but can't remember how I succeeded last time. But that's a topic for a new thread I suppose.

---

### Post by amador.duran on 2009-05-14
Hi all,

I've been trying to install and configure Jaunty on my T4010 and I've been reading this and other threads for the last week. I've finally got it, so I want to share my experience with the rest of the Ubuntu community.

This is the process for installing Jaunty on a T4010 (debugged after many attempts):

[LIST=1]
[*]Install Jaunty from the LiveCD (I installed it directly, without testing the LiveCD).
[*]The touchpad works but the stylus doesn't.
[*]The var/log/Xorg.0.log detects FUJ02e5 device and says:
   Wacom ISDV4 control data (0) error in * query
   (II) UnloadModule: "wacom"
[*]Go to System->Preferences->Mouse and ... at this point, X chrashes and restarts and then the stylus works!
[/LIST]
 I have to repeat step 4 every time I start my computer.

After that, I have installed the already compiled fjbtdrv from [https://launchpad.net/~khnz/+archive/ppa]("https://launchpad.net/%7Ekhnz/+archive/ppa") and everything works OK if you turn off visual efects (i.e. Compiz) in Preferences->Appearance.

No serial configuration, no fdi file rewriting, everything works like a charm except I have to go System->Preferences->Mouse every time I start Jaunty and wait for X to crash and restart.

Thanks to all the guys whose posts have helped me before.

---

### Post by gideon793 on 2009-10-06
> Hi all,

I've been trying to install and configure Jaunty on my T4010 and I've been reading this and other threads for the last week. I've finally got it, so I want to share my experience with the rest of the Ubuntu community.

This is the process for installing Jaunty on a T4010 (debugged after many attempts):

   1. Install Jaunty from the LiveCD (I installed it directly, without testing the LiveCD).
   2. The touchpad works but the stylus doesn't.
   3. The var/log/Xorg.0.log detects FUJ02e5 device and says:
      Wacom ISDV4 control data (0) error in * query
      (II) UnloadModule: "wacom"
   4. Go to System->Preferences->Mouse and ... at this point, X chrashes and restarts and then the stylus works!

I have to repeat step 4 every time I start my computer.

After that, I have installed the already compiled fjbtdrv from [https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa) and everything works OK if you turn off visual efects (i.e. Compiz) in Preferences->Appearance.

No serial configuration, no fdi file rewriting, everything works like a charm except I have to go System->Preferences->Mouse every time I start Jaunty and wait for X to crash and restart.

Thanks to all the guys whose posts have helped me before. 

Thanks for the post.. This worked for me as well but I can't use the buttons on the pen. How do i turn them on?

---

