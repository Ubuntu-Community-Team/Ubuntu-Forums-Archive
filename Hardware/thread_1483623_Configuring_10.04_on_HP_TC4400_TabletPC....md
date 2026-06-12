---
title: "Configuring 10.04 on HP TC4400 TabletPC..."
date: 2010-05-14
forum: Hardware
---

### Post by ragtag on 2010-05-14
I've been running dual boot on my TC4400 TabletPC for a while now, and just did a clean install of Ubuntu 10.04, not without some trouble. So this is a mini tutorial for others that might find it usefull.

First of, make a backup of your system. Since the TC4400 (at least mine) only has an 80Gig drive, I like to use dd to copy the whole machine to an usb drive. You can boot into the live cd, open the terminal and type (WARNING, read the manual for dd, and know what you're doing first...dd can destroy your data with one spelling mistake).

```
dd if=/dev/sda of=path_to_your_usb_drive/my_tc4400.dd
```

This makes a complete image of the machine, which you can use to restore the machine completely, in case something goes horribly wrong.

My TC4400 has WinXP TabletPC edidition partition, and one Ubuntu 9.10, but is still legacy grub. For some reason M$ decided to not include WinXP cd-s with all TabletPC's, so you can't re-install easily. So backing up is a good idea.

On thing you need to be aware of before you install grub2, is that it takes up more space in the Master Boot Record (mbr). This is normally not a problem, except that some of the security tools that come installed on the TC4400 from HP, write to this part of the mbr. I'm not exactly sure which one, but what I wound up doing was removing most of them (they're mostly bloat anyway). If they are left in, Ubuntu will install fine with grub2, and boot fine as many times as you like. But once you boot into WindowsXP once, it will write to the last half of the mbr (not used by windows), which will overwrite part of grub2, leaving you with a computer with a completely broken grub. In fact it wont find a system disk at all. :(  If you know some clever way around this, please let me know, but removing all the HP tools does work.

Note. I removed the drive protection thing, that makes the hard drive stop reading if the machine is dropped or moved quickly, as I'm running from a solid state drive, but you might want to leave this in. I doubt this is the one that writes to the mbr, but you can never be sure. So make a backup...again.

For installing Ubuntu, you can basically follow any of the instructions on the net. It will happily install along WinXP, though WinXP will probably request a file system repair on next boot if your resized it.

BASICS

Amazingly the pen works out of the box, with pressure and all (thanks guys). Though you might notice that the touchpad stops working after a short while. This is because it's set to be disabled when you start typing. So go into. System>Preferences>Mouse and select the Touchpad tab. And disable 'Disable Touchpad while typing'. You can change the other Touchpad settings anyway you like, but notice that there is an option to turn on Two-Finger Scrolling...and on the TC4400 this works great.

SCREEN ROTATION & PEN

The next thing to do, would be configure the tablet and screen. It works out of the box, but there are a few modifications you might want to make. For one, the side-button on the pen, is set to middle click by default, and not right click. Add the following to your .profile (it's in your home folder).

```

# Custom wacom settings.
xsetwacom set 'Serial Wacom Tablet' 'Button2' '3'

```

The next time you log in, the side button will be right click. You may want to look up the [Linux Wacom Project]("http://linuxwacom.sourceforge.net/") for different options. Such as adjusting the pressure curve and more. Notice that the last two options are basically the same you would use in xorg.conf in earlier versions of Ubuntu.

That done, we want to get screen rotation working. For this I wrote a simple script.

```

#!/bin/sh
# Toggle the rotation of the screen from normal to right.
rotation=`xrandr -q | grep "LVDS1" | awk '{print $4}'`
if [ "$rotation" = "(normal" ]; then
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet" Rotate CW
    xsetwacom set "Serial Wacom Tablet eraser" Rotate CW
else
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet" Rotate NONE
    xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE
fi

```
You can put this in a file /usr/local/bin/rotatescreen (you need to sudo to write there), and make it executable.
```

chmod a+rx /usr/local/bin/rotatescreen

```
When you run the script, the screen and the tablet will toggle between normal rotation, and rotating to the right (leaving the widest part of the screen under your wrist....assuming you're right handed). To rotate it to the left, simply replace the word "right" with "left" and "CW" with "CCW" in the code above.

One thing that actually tricked me a little up when I was drawing in tablet mode, was that Ubuntu would restart seemingly randomly. I was using GIMP in full screen mode, and what was happening was that I was hitting the Ctrl-Alt-Del button on the side of the screen, when moving the machine around. This, of course, brings up the Shut Down window in Ubuntu, which would show up behind GIMP (probably because I was drawing fast, and thus clicking on GIMP all the time). After 60 seconds, the Shut Down window actually shuts down the computer. :(  So you may want to go into System>Preferences>Keyboard Shortcuts and change the keys for Log out, to something else.

COOL SOFTWARE

Note: To quickly install all the software mentioned below, you can enter this in the terminal:

```
sudo apt-get install easystroke cellwriter xournal gimp inkscape mypaint
```

Let's get on to some handy software. When you flip the screen around on the TC4400, you don't have a keyboard anymore. There are a couple of tools that can be of great help here.

First is **easystroke**. You can find it in the Ubuntu Software Center (or Synaptic or apt-get if you prefer). It's a gesture recognition program, that let's you use simple drawing to issue keyboard shortcuts and commands. It's about as quick as using a keyboard shortcut, and it's dead easy to teach it new commands.

To configure it, simply start it up from Applications>Universal Access>Easystroke.  You'll notice a little green and blue loop shows up in the notification area, in the top Panel. Click on this to open the easystroke window. Begin by click the Preferences tab, from here you'll want to change the following.
Click the Gesture Button, and choose Button 3. This sets the gesture to run when you hold the side button on the pen, and make a gesture.
Check the Autostart easystroke, if you want it to start when you log in...which I find quite handy as I use it all the time.

Move on to the Advanced tab, and check the devices from the list that you want to use gestures. I've only checked off the Serial Wacom Tablet here, as I only use gestures when using the pen. Gestures are kind of hard to do on the Touchpad.

To create your own custom gestures go to the Action tab, and hit "Add Action", enter a name for the action, choose a Type (Key for any key or key combination, and command for starting a program or running a command...like for instance rotatescreen). Then hit "Record Stroke", and using the side button draw the gesture you want to use, without touching the tip to the screen. Make as many gestures as you need. For GIMP I tend to use around 10 or so different gestures; zoom in/out, undo, choose brush, hide tools, save and a couple more. If you want the same functionality in Windows, check out [gMote]("http://www.handform.net/gmote.php").

If you need to enter text, easystroke won't really do the job, but here **cellwriter** steps in to help. In fact, I've set up a gesture in easystroke to open up cellwriter for quick access. It's in the Ubuntu software repositories, so can be installed easily using the Software Center. Cellwriter is a handwriting recognition program, that includes an on-screen keyboard. The first thing you need to do, is to teach it to read your handwriting. Simply hit the "Train" button, and write in each letter 3 to 4 times. You can re-do any letter later, if you find cellwriter keeps messing up a particular letter. Once that's done you can use cellwriter to write in text into pretty much any Ubuntu program. It's not as fast as a keyboard (unless you're a slow typist), but it's great for entering short text, such as names for files you're saving or quick forum searches. :)

**xournal**, is another usefull application for tablet use. It's basically a note book for hand written notes, with an easy to use interface. 

Then there are the graphics programs. First of there is GIMP, which no longer comes pre-installed on Ubuntu, but you can quickly install it from the Ubuntu Software Center. To get pressure working in GIMP, you need to start GIMP, and the go into Edit>Preferences, choose Input Devices on the left side, and hit the "Configure Extended Inpute Devices.." button. This will open up a small window, pick Serial Wacom Tablet eraser from the Device pop-up menu, and choose Screen from the Mode pop-up menu next to it, do the same for the Serial Wacom Tablet. Hit Save and Close. Now you should have working pressure sensitivity in GIMP. You can adjust it in Tool Options under Brush Dynamics for the Paint brush and several other tools. 
As a side note, with the small screen on the TC4400, I like to use just one tool window. If you make the toolbox a bit wide, you can add multiple tabs below the tools, with things like layers, tool options, color picker and more.
Finally, note that the rotatescreen messes up tablet mapping within GIMP. So if you rotate the screen, you'll actually need to actually restart the GIMP to get the mapping right.

Another great graphics tool is **InkScape**. It's a vector drawing program, that like GIMP, also supports pressure. To activate it, start Inkscape, and choose File>Input Devices... You'll get a window that's identical to the one from GIMP, so you can simply follow the instructions above for GIMP. The Calligraphy pen supports pressure. You can make it round under the No-preset pop-up menu, if you don't want an actual calligraphy pen. :)

There are lots more you'll likely want to check out, such as: **MyPaint** - A simple natural media (oils, pencils etc) paint program, and **Krita** - A KDE program, a lot like Photoshop or GIMP, but with 16bit support and more.

I'm sure I forgot something  here, but this post is getting way too long already.  I haven't gotten as far as configuring the scroll wheel on the side of the screen, or the three buttons on the screen (Q, rotate, e), nor have I figured out how to set the screen to rotate when I fold it down, like it does on Windows (I'm not sure I want it to).

Anyway, I hope someone found this at least a bit useful. 

):P

---

### Post by ragtag on 2010-05-16
Just a quick heads up. Someone mentioned in a post here that if you install the proprietary modem drivers in System>Admininstration>Hardware Drivers, it would mess up the sound on your TC4400. I don't know if this is still the case in 10.04, and I'm not too keen to test it...as I really have no need for a modem in this day and age. :)

Also, if you're using the 64bit version and Adobe Flash. You will need to remove the Flash version installed by Ubuntu restricted extras, and download the 64bit version. The 32bit one has problem registering clicks, in Ubuntu 64bit. You can find instructions for how to do this here in the forums. :)

---

### Post by mdhtr on 2010-05-23
Hi!
I love the two-finger scrolling, thanks for mentioning it!

I would be really interested in making the scroll work on the side, because I used to use it a lot, and the last time it worked for me was in Gutsy Gibbon release.

There is [another way]("http://alice-at-ubuntu.blogspot.com/2010/05/setting-pen-button-to-work.html") of fixing the pen button to right click, which is not needed to be put in the profile.
And what I use to rotate the screen now, are [nautilus scripts]("http://alice-at-ubuntu.blogspot.com/2010/05/screen-rotation-through-nautilus.html").
(I linked from [my blog]("http://alice-at-ubuntu.blogspot.com/") where I made notes for myself from the beginning of my usage of Ubuntu on my TC4400. Just in case, anyone is interested.)

---

### Post by dapeco on 2010-05-29
Hi all,

how you have resolved the battery high usage and cpu frequency scale? I'm unable to get a good battery uptime (under 2h with a new battery vs more than 4h with xp). I have a t5600 cpu on the tc4400.

thanks

---

### Post by ragtag on 2010-06-08
The CPU scaling seems to be working ok, at least when looking at the CPU Frequency panel applet. It generally runs at 1Ghz, unless it's doing something heavy.

To be honest, I'm not sure about the battery. I generally get around two hours on a somewhat aging battery, using wifi and the ambient light sensor (so somewhat dim screen). Depends a bit on what I'm duing. Turning up the screen brightness seems to drain the battery quite a bit faster. It's been so long since I used it for any amount of time in Windows, that I'm not sure how it compares to be honest. :)

---

### Post by ragtag on 2010-06-18
After testing Ubuntu Netbook edition on a virtual machine on my main comuter, I found a lot of stuff that looked handy for a small screen, like on the TC4400. Rather than re-install with the netbook edition, I just added the packages I liked. 

The main ones are netbook-launcher, maximus, go-home-applet and window-picker-applet. It save on screen space, and works great on the TC4400. You add netbook-launcher and maximus to System>Preferences>Startup Applications, and the window-picker-applet and the go-home-applet to the top panel. I removed the bottom one to save space. Maximus, maximizes all the windows and removes the title bar, while the window-picker-applet takes over the role of the title bar and a window picker. netbook-launcher covers your desktop, and replaces the normal GNOME menu, so you can remove that from your panel too. The go-home applet hides all windows so you can get at the netbook-launcher. It's pretty a pretty sweet setup. :)

I've made an attempt to activate the remaining keys (the three soft keys on the screen, the scroll wheel and the presentation button) on the TC4400 with little luck. xev returns nothing on any of them, and everything I tried resulted in no feedback whatsoever. If anyone knows how, please post a solution here.

---

### Post by Kazarelth on 2010-07-19
Hello there! That was one really awesome tutorial on configuring Ubuntu for the tc4400.
I want to install the Netbook Remix permanently on an SD card. I am currently running it off a 4GB pen drive.
Sadly, when I use the install manager to install Ubuntu onto the (4 GB) SD card, the installation goes till a certain point and then fails saying that the SD card is write protected. I know very well that if it IS write protected, it won't even go through the first ~40% of the installation. I then have to format it back to FAT32 and then try again.
So... any suggestions? 

Now I am primarily an end-user when it comes to Linux (read: n00b) so you must guide me through the basics! :P

---

### Post by timbuktoo on 2010-07-23
is the rotatescreen script suposed to work with the rotate screen button underneath the right side of the screen?

---

### Post by ragtag on 2010-07-27
timbuktoo: No, you need to run it manually, make an icon for it and add it to alacarte. I never figured out how to access that button, and now my TC4400 has a hardware error, so the scroll wheel no longer works, and it keeps pressing Ctrl-Alt-Del, when i move the screen back and forth. :( I tried taking the machine apart, but I think the error is under the screen bevel...and I didn't want to break that apart...as I'll likely damage something if I do. If someone figures how to access those buttons, that would be great though.

Kazarelth: I'm not sure if the TC4400 can boot from and SD card. If you hit F10 when you start it, and go into the BIOS settings, I think the boot options are in the far right menu, there is no SD card listed. Just USB drives, hard drive, cd-rom and so on. It may be possible to do it if the boot sector and grub is on the main drive and the system on the SD card...but I honestly don't know how. I believe the TC4400 needs some kind of firmware update to use SDHC card, if that's what you're using. It could possibly be the reason the install gives up. As a side note, SD cards aren't that fast (see table below). I've tried installing Linux on USB thumb drives...and it was way slower than on a normal laptop hard drive. They also have limited rewrites at around 100.000, so you probably want to avoid having swap on an SD card. Sorry I can't be of more help.

    * Class 2: 16 Mbit/s (2 MB/s)
    * Class 4: 32 Mbit/s (4 MB/s)
    * Class 6: 48 Mbit/s (6 MB/s)
    * Class 10: 80 Mbit/s (10 MB/s)

---

### Post by timbuktoo on 2010-07-27
i tried running the windows drivers for the soft buttons but i got an error about untrusted software. do you know how i could override that. it did the same for android SDK which isnt on the software center.  boy did i love 9.10!

---

### Post by fischtier on 2010-10-19
hi guys,
i've just put ubuntu 10.10 on my (to me new) tc4400. there seems to a problem with either the wireless drivers or the hardware itself. has anyone of you experienced such a thing? would be grateful for help.
(haven't tried any version of windows on it so far, so if you have recommendations... but i guess, wireless should work in ubuntu)

---

### Post by browningj on 2010-11-30
Does anyone have any new info on the Tablet Softbuttons? I have a TC4200 running 10.10 (but I think they are identical when it comes to the buttons) and that is the only thing I can't get to work.  I can get it to work in 9.10, but for some reason my bluetooth isn't recognized.  Now, to figure out whether I should go back to 9.10 for the buttons, or sacrifice them for bluetooth.  Hmm, don't really use bluetooth, so I may be going back.  Let me know if I can help while in 9.10.

---

### Post by crazy ivan on 2011-02-19
Great tutorial, has led me to the purchase and successful configuration of the device. Check out my tutorial [http://ubuntuforums.org/showthread.php?p=10473430]("http://ubuntuforums.org/showthread.php?p=10473430"), maybe you have some Ideas for these questions:

1) cellwriter does not copy to clipboard > hard to use gnome-do
2) somehow 'xrandr --auto' is performed everytime you connect or disconnect a screen, this means one has to run the scripts before connecting the displays, and sometimes afterwards in addition, this should be somehow disabled (for certain screen id's)
3) connecting back to docking-station, just to type a message is too troublesome, any experiences with bluetooth keyboards and this PC?

---

### Post by markonhismobile on 2011-03-21
> **fischtier said:**
> hi guys,
i've just put ubuntu 10.10 on my (to me new) tc4400. there seems to a problem with either the wireless drivers or the hardware itself. has anyone of you experienced such a thing? would be grateful for help.
(haven't tried any version of windows on it so far, so if you have recommendations... but i guess, wireless should work in ubuntu)

I may have had a similar issue on my newly acquired tc4400 earlier. If the issue your getting is the wireless device not activating despite it being "ON" via the hw button and showing in lspci then you need to go into the BIOS and reload defaults. Don't ask me how or why this works but I got my wireless up and going after doing this earlier :-)

---

### Post by markonhismobile on 2011-03-22
OK! Well after reading Ragtags great opening post I've been tinkering with my newly acquired tc4400 for the last couple of nights. 

I started off with 10.10 but couldn't get the stylus to register anything, I had cursor movement but no clicking!
After a bit of looking around I went back to 10.04(.2) and actually got the sytlus registering clicks now but it's rather sensitive.

I'm not sure if it's me using it wrong or an actual misconfiguration but it constantly seems to click so I often end up dragging items around the screen or drawing boxes on the desktop. It's also rather hit and miss when trying to click items on the desktop. I think it's a problem with the proximity as the cursor starts moving when the stylus isn't even touching the screen. Some more googling and I've tried altering the TPCButton option in xwacomset no avail.

My questions are then, is anyone else experiencing this behaviour and has anyone with 10.10 got the stylus working correctly? I don't mind running 10.04 but would rather use 10.10.

---

### Post by Favux on 2011-03-22
Hi markonhismobile,

There isn't any reason I know that you can't get the Compaq working in Maverick.

You seem to be having configuration issues and my guess is your serial Wacom digitizer isn't actually on the Wacom X driver.

To find out enter into a terminal *xinput list*.  In the output should be the stylus device name.  Then enter in a terminal:
```
xinput list-props "device name"
```
and post the outputs of both.  Should tell us a little about what's going on and what driver is being used.

---

### Post by markonhismobile on 2011-03-23
I fired up a liveUSB Maverick this morning before work and had a quick play. I was using the xsetwacom and xinput bits last night to try and work out the weird behaviour in Lucid. All the settings looked the same....

Upgrading to Maverick now so should be able to report back/post output of commands if needed in about 2 hours after it's finished installing and I've eaten. It's times like this I'm glad I use apt-cacher-ng :-D

---

### Post by markonhismobile on 2011-03-23
xinput list output

```
 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=14	[slave  keyboard (3)]
```

xinput list-props "Serial Wacom Tablet stylus" output:

```

Device 'Serial Wacom Tablet stylus':
	Device Enabled (154):	1
	Coordinate Transformation Matrix (156):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (275):	0
	Device Accel Constant Deceleration (276):	1.000000
	Device Accel Adaptive Deceleration (277):	1.000000
	Device Accel Velocity Scaling (278):	10.000000
	Wacom Tablet Area (339):	0, 0, 24780, 18630
	Wacom Rotation (340):	0
	Wacom Pressurecurve (341):	0, 0, 100, 100
	Wacom Serial IDs (342):	144, 0, 2, 0
	Wacom TwinView Resolution (343):	0, 0, 0, 0
	Wacom Display Options (344):	-1, 0, 1
	Wacom Screen Area (345):	0, 0, 1024, 768
	Wacom Proximity Threshold (346):	0
	Wacom Capacity (347):	-1
	Wacom Pressure Threshold (348):	27
	Wacom Sample and Suppress (349):	2, 4
	Wacom Enable Touch (350):	0
	Wacom Hover Click (351):	1
	Wacom Enable Touch Gesture (352):	0
	Wacom Touch Gesture Parameters (353):	50, 20, 250
	Wacom Tool Type (354):	"STYLUS" (356)
	Wacom Button Actions (355):	"None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0), "None" (0)
```

The eraser end of the pen appears to work fine. The cursor moves and I can click on items when I depress that end.

I have configured the side button to be the right click and initially it wasn't working. I tried toggling the TPCButton setting (seems to effect the "Hover Click" setting) from off to on and when it's set to on I can use the right click.

On the plus side as I'm now back on Maverick I have the hp_wmi module back so Magick Rotation now works again :-)

---

### Post by Favux on 2011-03-23
Actually TPCButton (now TabletPCButton) was only enabled recently.  So maybe that's why the right click problem.

Xinput list shows both devices and list-props shows it's on the wacom X driver, so all looks good.

I gather the stylus tip isn't working?  What do you see with?:
```
xsetwacom list
```
Why don't you try running in a terminal:
```
xsetwacom set "Serial Wacom Tablet stylus" Button1 1
```
and see if that changes anything?

Glad to hear Magick is working for you.  :)

---

### Post by markonhismobile on 2011-03-24
xsetwacom list:
```

Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet stylus STYLUS
```

Would the fact that xinput and xsetwacom have them named slightly differently have an effect? I'm sure when I was on Lucid they where both named exactly the same. I did read a thread somewhere else yesterday for 9.10 that talked about ensuring the naming was the same between the two but the comments implied it wasn't needed in 10.04+.

I tried the other command but that didn't have any effect, still not picking up the click for the stylus.

---

### Post by Favux on 2011-03-24
That shouldn't matter.  The name is more dependent on the xinput version and xsetwacom version than anything else.  The key is xsetwacom is recognizing the stylus so it should be on the wacom X driver.

It's possible to have a bad stylus tip.  To rule out a hardware problem do you happen to know if the stylus tip worked in Windows?  It seemed to in Lucid, but do you know if that was on the Wacom driver?

The only other reason for it not to be registering is if you have the ClickForce set very high.  So are you saying not only does it not click the pointer arrow doesn't track the cursor tip?

---

### Post by markonhismobile on 2011-03-25
OK, I tried setting ClickForce to a lower value and that didn't seem to have any effect.

The cursor tracks the stylus tip fine, it picks it up about 10mm from the screen and when I was in Lucid that was enough to register a "click" so for example I'd start writing in Xournal or drawing in MyPaint without physically touching the screen.

I didn't test the stylus in Windows however I do have a spare SATA disk so could swap over and do a test install. At the moment I am thinking it could be a dodgy stylus as I noticed similar issues on another tc4400 with this stylus and a fresh Maverick install. I did have some spare tips and I've swapped them over but it's made no difference atm.

---

### Post by Favux on 2011-03-25
> The cursor tracks the stylus tip fine, it picks it up about 10mm from the screen and when I was in Lucid that was enough to register a "click" so for example I'd start writing in Xournal or drawing in MyPaint without physically touching the screen.
That was the non-normal behavior.  It should not start writing until the tip is in contact with the screen.  In other words a *Button 1 1* event should not be generated until there is physical contact.  ClickForce/Threshold sets the minimum pressure necessary to generate a Button 1 event to avoid spurious left clicks.  There was some kind of bug in your Lucid set up, with proximity maybe.  You are able to use the stylus side buttons (Button 2 and Button 3) without the tip in contact.  That's called "hover" mode (TabletPCButton off) which is the default for non-tabletPC tablets.  Are you sure you were using the Wacom X driver in Lucid?

---

### Post by markonhismobile on 2011-03-25
I believe I was using the Wacom X driver in Lucid however as I've replaced it now with Maverick I'm not certain. As Ubuntu is so quick to install I'll probably whack the spare SATA disk in and then test with a fresh Maverick install (unless a Live environment will do for diags?)

Would I just need to try adjusting the ClickFore/Threshold Value?
I think I did spot the Proximity value when I was trying to diag this originally but could never find a valid value to set it to.

As far as I can remember I think I can use Button2 (I don't appear to have a Button3 ?) whilst hovering but will need to double check this evening when I'm back with the computer.

Thanks for your help on this, I do quite enjoy a challenge and investigating this has taught me a few more commands :-)

---

### Post by Favux on 2011-03-25
Don't know how valid a live Lucid CD would be for testing.
> Would I just need to try adjusting the ClickForce/Threshold Value?
I don't think even setting Threshold to 0 will do it.
> I did spot the Proximity value when I was trying to diag this originally but could never find a valid value to set it to.
I think it is only user modifiable for the cursor (the Wacom tablet mouse).
> I don't appear to have a Button3?
Right, a lot of tabletPC styli only have one side button, so Button 2.

---

### Post by crazy ivan on 2011-03-28
Hi Mark,
I would guess your stylus is somewhat incompatible. In this thread [http://ubuntuforums.org/showthread.php?p=10473430]("http://ubuntuforums.org/showthread.php?p=10473430") I describe how I set up a tc4400 with ubuntu 10.10. The original HP stylus was working out of the box on Maverick Live-USB.

---

### Post by crazy ivan on 2011-04-22
Hi guys: Some news on the scrolling wheel, the thumbprint scanner and other stuff from [http://www.youtube.com/watch?v=6Fcc1428abo]("http://www.youtube.com/watch?v=6Fcc1428abo"). It seems to be possible to get quite a lot more things going.

---

### Post by Brancaleone on 2011-04-28
So now I got everything working.  

Biggest problem were the soft buttons. It's quite easy, there's a patch released on linux-wacom. Though it is written for the tc1100 (which is an antecessor of tc4400), seems that hardware is similiar. So grab the patch, apply it to [xf86-input-wacom-0.10.10.tar.bz2                         ]("http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.10.tar.bz2/download") - driver and replace xorg-input driver with the patched version. Restart x11 and you get the 3 Buttons recongnized as button 17, 18 and 19. Now use xbindkeys to assign whatever you want - in my case a rotate-script, cellwriter and iceweasel.   


Patch Link
[http://sourceforge.net/tracker/?func=detail&aid=3165586&group_id=69596&atid=525126](http://sourceforge.net/tracker/?func=detail&aid=3165586&group_id=69596&atid=525126)

Driver Link
[http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.10.tar.bz2/download](http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.10.tar.bz2/download)

---

### Post by gabetz08 on 2011-08-15
Brancaleone, I am a newbie here. Can you give me some help on how to patch the wacom driver. 

I have two other issues that I want to fix. Screen rotation and the jog dial on the side of the screen. I know in the video The guy wrote a script to get the jog dial working but from my best efforts I was unable to get that to work. Is there a command I can run to see what button presses the computer is seeing. I have tried goggling this but I am unable to to find what I am looking for. 

Any help with getting the wacom buttons, screen rotation, or jog dial buttons working would be greatly appreciated

---

### Post by Favux on 2011-08-15
Hi gabetz08,

Magick Rotation should give you rotation;  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  For your model remember to check the box in front of "BIOS hinge switch values reversed?" in Setup.

To patch you need the xf86-input-wacom source code.  The [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") or the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") will show you download the source code for patching.

---

### Post by Brancaleone on 2011-08-26
Hi gabetz, 

I use a slightly modified rotate-bash-script I found around the net. I  put it on my Desktop an linked it to /usr/bin, so I can start it easily  from a terminal or in "Tablet Mode". 

I uploaded you the already patched Wacom-Driver. Just extract and compile 
(tar -xjvf xf86-input-wacom-0.11.1.patched.for.tc4400.tar.bz2
 cd xf86-input-wacom-0.11.1
 ./configure
 make)

sudo make install doesn't work, so we have to copy the driver manually 
cp -v /your/directory/xf86-input-wacom-0.11.1/src/.libs/wacom_drv.so /usr/lib/xorg/modules/input

Restart X and the soft buttons should work as described above.

Edit: 

So now I am home and have time so let's continue: 

The Jogdial isn't recognized with xev, because it's no standard key. All you have to do is to assign a keycode to the recognized scancode. The scancode is e006 and e007 (you can get this code if you run showkey -s OUTSIDE X, so shut it down or use a virtual console). To assign PageUp / PageDown just enter:   

sudo setkeycodes e006 104 && sudo setkeycodes e007 109

Of course you can assign another key if you want to, Cursor Up & Down (103 / 108 ) e.g.
Or you can map it to another (unused) keycode and assign that to an action, just be careful because setkeycodes keycodes ARE DIFFERENT than xev-keycodes. Also some of the setkeycodes - keys are already in use for the additional buttons like volume up/down.   

To make this permanent, you have to edit rc.local:

gksudo gedit /etc/rc.local

and put 

setkeycodes e006 104
setkeycodes e007 109

just before the exit 0.

---

### Post by usu0101 on 2012-12-29
Hi,
there is any solution for tc4400 with 12.10? 
the "xev" command doesn't recognize the buttons :(

---

### Post by Favux on 2012-12-29
Hi usu0101,

Welcome to Ubuntu forums!


Looks like you may be able to get them working.  See this linuxwacom-devel thread:  [http://sourceforge.net/mailarchive/forum.php?thread_name=20110724222710.GA27391%40barra.bne.redhat.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20110724222710.GA27391%40barra.bne.redhat.com&forum_name=linuxwacom-devel)

---

