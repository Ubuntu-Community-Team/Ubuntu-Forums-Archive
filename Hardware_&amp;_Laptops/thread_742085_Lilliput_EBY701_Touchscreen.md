---
title: "Lilliput EBY701 Touchscreen"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by sigmason on 2008-04-01
I got one of these and decided to hook it up to a Dell Dimension 2400 running Ubuntu 6.06.

From a clean install I was able to install the latest EGalax drivers (not the drivers that came with it):
[http://www.eeti.com.tw/](http://www.eeti.com.tw/)

I used the HID config. so things turned out pretty simple.  Just put the compiled driver in the right folder, tell X11 to use the device hiddev0.  Blacklist touchkitusb and tkusb (if you even bother to put that in as I don't think you need it.)

That got me 640x480 at 60Hz with 16 bit color with a working touch screen which was nice.
I was able to remove the other video modes from the xorg.conf and setup a virtual desktop that was larger as 640x480 isn't large enough for some windows.  Of course, you can use the touch screen to move the windows by holding down ALT and dragging the window with your finger, but the virtual 'panning' could be handy too.  Too bad you can't really 'pan' with the touchscreen (think about it, if you touch the screen it's the equivalent of clicking and dragging, not just moving the cursor.)

I was even able to retain the usage of the onboard PS/2 mouse port and keyboard, which could be handy in a pinch (just keep using the mice event, if you use mouse0 or whatever it will occasionally not recognize events from the on-board PS/2 mouse port.)

I was also able to put the OffTime parameter in and get the display to 'sleep' even though the sleep function in the Power Management doesn't seem to work.

I did notice that despite 'going to sleep' this display does not apparently support DDC.  Which makes things interesting.  Basically the OffTime parameter is turning off the video, which to the display is causing it to eventually time out and 'sleep'.  That's not really how it usually works.

The only problems I have are 2 fold.

This computer has an Intel 845 video chipset, which means any mode it doesn't list I need 915resolution for.   Worse this display is apparently 800x480 and unlike Xenarc they don't give out a modeline to use.  So I tried using PowerStrip to figure it out and it didn't work out.  

Also, since it doesn't support DDC it makes things interesting because X11 tries to query it and ends up defaulting to the CRT display output in 640x480 at 60Hz because it can't figure out what else to do.  I suspect I can override that as I can use 915resolution to change the 'default' mode, but without a modeline, things don't seem to be working out.

Bottom line:

Has anyone got any suggestions for a modeline for this Lilliput EBY701 in 800x480 at 60Hz in 16 bit color?

Sigmason

As an aside, there's a website to use this with an Apple, is there a way to get a modeline from an Apple?

---

### Post by sigmason on 2008-04-04
So while playing with devilspie, I discovered a project called gdevilspie in Python.

Too bad it uses an object for GTK that is not available to Ubuntu 6.06 LTS no matter what you install from Synaptics.

So I decided to try Ubuntu 7.10 on the same Dell Dimension 2400.
(I ended up having to put 256MB of additional RAM in because I found that it pretty much ate all of the existing 256MB of RAM.  With 6.06 it was tight, but it wasn't swapping everything like 7.10 was doing.)

Not only does the version of PyGtk work fine with gdevilspie, but oddly, the display now seems to communicate to the computer!?

Anyway, now that it seems to be talking, it's not talking too well.  Accord to the X11 log this display can handle 1280x768 at 60Hz.  When it did that, the display was there but the vertical sync pushed up the display so that the top of the display was at the bottom.

I quickly lowered the resolution (which I now had options in Screen Resolution because the display is talking) to 800x600 and it actually worked!

I'm not quite sure how it's managing to get 800x600 on a 800x480 display but the display is not clipped at the bottom like I would expect.  Also, after I installed gnome-cups-manager (just to test) I can now run the Add Printer menu and it's not clipped.

I would have to guess that somewhere the modeline that X11 created doesn't work out to 800x600 but instead works out to 800x480 despite it not reading that way.  Very odd.

Sigmason

I'm not complaining, I got more then what I wanted for a simple upgrade install.
Can't get any easier then that.

---

### Post by sigmason on 2008-04-04
In addition in Ubuntu 7.10 the OffTime parameter is not needed in xorg.conf.  The display, as it now communications, does sleep without first turning blue because the OffTime parameter killed the video input and it returns from sleep without turning random solid colors because of the recovery of the video output.

That's another added bonus.

Sigmason

---

### Post by sigmason on 2008-04-05
Turns out not all was really well with 7.10.
The reason the video started working is apparently X11 installed with the Intel experimental mode drivers.
On the plus side, this got the display to do 800x480, on the down side apparently that driver set does not take care of some important incidentals.

1. I lost the video in the TTY screens.
2. I lost the splash screen.
3. I couldn't get the GDM (login screen) to change resolutions.
4. The touchscreen device name changed.
5. 640x480 is the wrong DPI suddenly (turns out this is not because of anything other then more things on the menu, I was tired and didn't notice.  I verified that by installing the same display on another Dell Dimension 2400 Ubuntu 6.06 LTS box and measuring the menus in 640x480.  The extra information on the menu by default in 7.10 makes all the difference.)

1. To fix the TTY screens you need to remove vesafs from the modprobe black list and get it to start with initramfs.

2. To fix the splash screen you need to edit /etc/usplash.conf and put in 640x480.  800x600 does not work here as I discovered latter.  It might work after getting vesafs running but I doubt it so why take the chance and aggravate yourself just stick with the standard 640x480 which the display will scale for you to 800x480 fullscreen.

3. This is actually apparently a known bug.  If you don't have a virtual line in your /etc/X11/xorg.conf the splash screen apparently just goes to the highest detected resolution.  It may be because of the Plug and Play monitor (as 7.10 now reports this display) and a lack of a section in xorg.conf for it or because of the experimental Intel driver.  However, something is odd, because in this case, using another monitor's section I was able to add a line for virtual of:
virtual 800 600
Right below the mode list and the splash screen immediately went to 800x600.
This is somewhat annoying as I suspect in a multiple monitor configuration this could get out of hand.
Worse, this is somewhat annoying as one method of using RandR and Xinerama is to specify a virtual larger then your desktop so you can pan to it.  If the splash screen is using that as a resolution hint it would seem that this otherwise useful function is now crippled.  (By the way as noted above 'panning' doesn't work using the touchscreen, you can't not click and drag the pointer off the screen, you have to click to move the pointer and you can't click off the screen obviously.)

4. After installing 7.10 and finding all of the above I also ran into issues with the touchscreen again.  The egalax driver is still the driver you want to use but for reasons unknown it no longer shows a device of hiddev0 in the /dev when the screen is plugged in without the driver.  Nor does cat /proc/bus/input/devices, not does lsusb.  After annoying myself for some time I tried usbauto in the xorg.conf and it started working and using the hiddev0 event none the less (why I don't know, I suppose the egalax driver has some kind of auto detection it supplements into the system when it runs, I don't have time right now to look at the code.)  That said I also had to make sure to put the parameter file specified in xorg.conf in a location that it could be saved so that my calibration stayed working.

Sigmason

Someone really needs to address that 'virtual' problem.  It find that very annoying.  With it like it is now, I suspect my original trick of just using a mouse plugged into the PS/2 port to pan the display would not work anymore.

As I don't have a mode listed for anything about 800x600 clearly GDM is reading the virtual line and that line was not originally used for that purpose.

---

### Post by sigmason on 2008-04-05
In regards to 7.10:

One other thing, I noticed I can't simply select the i810 driver from 'Screens and Resolutions'.
When you change it and go back in it's ignored.
Also, if you reboot it's still ignored.

Sigmason

---

