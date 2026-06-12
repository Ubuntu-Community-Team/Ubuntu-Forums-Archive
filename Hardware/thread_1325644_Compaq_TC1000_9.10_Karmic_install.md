---
title: "Compaq TC1000 9.10 Karmic install"
date: 2009-11-13
forum: Hardware
---

### Post by lazy-devil on 2009-11-13
Much has been written about Compaq's second tablet model, the TC1100; but many of those instructions and tips don't work well or at all on the previous model, the **TC1000**. With the contribution and wisdom of many talented people I have a fully functioning TC1000 Karmic Tablet.

I use **Xournal** for freehand notes and sketches. Xournal is also great for field annotating PDF documents and saving the results for later printing or review. I use **Cellwriter** for stylus input into many text programs. I use **TangoGPS** for map reading and with a USB GPS unit. My favorite application is **FBReader**, which turns the tablet into a nice, large screen (for my aging eyes), book reader that can handle the .epub books available from libraries and over 30,000 free books from Project Gutenberg.

I've tried Xubuntu 8.10, and Ubuntu 9.04 with LXDE, but 9.10 with Gnome runs very well. Maybe Lubuntu will tempt me, but this six year old Karmic Tablet runs better than it ever did with XP Tablet Edition new out of the box.

For Karmic, I made the following changes and additions after a normal install:

=====WIRELESS OFF AT STARTUP=====
To save battery power and CPU cycles I turn the wireless off at startup. It can always be re-enabled by clicking on the network manager panel applet. Choose SYSTEM > PREFERENCES > STARTUP APPLICATIONS, then add a new Startup Application called "Wireless Off at Startup" and paste this command string:

dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false


=====TOUCHSCREEN DRIVER SETUP=====
The touch screen stylus on the Compaq TC1000 is NOT the Wacom unit of the TC1100. 
It is the Fujitsu Finepoint Stylus and needs the X Server input driver called fpit. 
It can be installed by one two methods. In TERMINAL by typing:

sudo apt-get install xserver-xorg-input-fpit

or more simply by going to SYSTEM > ADMINISTRATION > SYNAPTIC PACKAGE MANAGER, and entering "fpit" in the Quick Search window. I perform this step in Synaptic and add the "Xournal" and "Cellwriter" packages at the same time. I also find that adding "FBReader" and "Tango GPS" complete the Ubuntu Tablet conversion.


=====RIGHT CLICK FOR STYLUS=====
The Finepoint Stylus side button is configured as the middle mouse click at startup.
To change this to the more standard right click do the following:

Create a new panel launcher by right clicking on a blank section of the upper panel. Choose add to panel, click on Custom Application Launcher and click on ADD. In the command box enter the following command:

xmodmap -e "pointer = 1 3 2 4 5 6 7 8 9"

Because this changes the normal keyboard touchpas mouse's right click there must be a way to reverse the change. Performing the same steps, create another new panel launcher with the following command:

xmodmap -e "pointer = 1 2 3 4 5 6 7 8 9"

Now you can change the right click action by choosing either of the two launchers.

I found two icons for these panel launchers that show a keyboard and a stylus, but that is just a cosmetic touch. The JPGs for these icons are attached below.


=====SIDE BUTTONS CONFIGURATION
There are six programable button the edge of the TC1000, 

In Windows they were:    [email]  [Qmenu]  [tab]  [esc]  [jog-up]  [jog-down]   
In Ubuntu they will be:    [pg up]  [pg dn]  [tab]  [esc]  [jog-up]  [jog-down]

To do this the rc.local file needs six lines added to it.

In TERMINAL:
sudo gedit /etc/rc.local

Then paste the following definitions for the side keys:

setkeycodes e002 104
setkeycodes e003 109
setkeycodes e004 015
setkeycodes e005 001
setkeycodes e006 103
setkeycodes e007 108

Then save the file, and exit gedit. Then make the executable with:

sudo chmod +x /etc/rc.local

Then exit TERMINAL.


=====XORG.CONF ADDITION FOR TOUCH SCREEN=====
Add the following text to the xorg.conf file located at /etc/X11. If there is no xorg.conf file, create one and paste the following text into it:

Section "InputDevice"
        Identifier "pen"
        Driver "fpit"
        Option "AlwaysCore" "on"
        Option "Device" "/dev/ttyS0"
        Option "BaudRate" "19200"
        Option "MaximumXPosition" "8600" # "6250"
        Option "MaximumYPosition" "6485" # "4950"
        Option "MinimumXPosition" "154"
        Option "MinimumYPosition" "110"
        Option "InvertY"
        Option "TrackRandR"
        Option "SendCoreEvents"
        Option    "Button2"    "3"
    Option "ReportingMode" "Scaled"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    16
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver  "nv"
    Option    "NoLogo"    "True"
    Option  "ConnectedMonitor"    "DFP"
    Option    "RandRRotation"    "on"
    Option     "NvAGP"     "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "pen"
EndSection


I hope this helps some and repays the numerous people on this forum that helped me.

Chuck

---

### Post by EricMattessich on 2009-12-15
I'm going to give all this a try tonight on my TC1000, thanks for the write up, i'll let you know how it goes :D

---

### Post by redzsky on 2009-12-17
which version of karmic is suitable for the tc1000 and how did u install through  usb?

---

### Post by EricMattessich on 2009-12-22
So i finished the install and everything works great!! I ended up using my sony external cd drive to boot a 9.10 disk and it all went smoothly from there (though it did take a very long time) I think the ram upgrade for these machines is a must.  Thanks for the right up :P

---

### Post by angel12 on 2009-12-23
So heres a question for yall interested in ubuntu on the tc1000:
would a custom kernel be of any interest to yall? im sure it would help performance wise, cause my tc1000 is laggy beyond belief, even when running xfce and using the longrun utility.

---

### Post by Blackthorne2 on 2009-12-28
I would be interested in a custom kernel and would help in any way possible.

---

### Post by 9AndS on 2009-12-29
Has anyone managed to install working video drivers? I have been looking through lots of posts about it and it seems i've tried everything to get them working... but still no luck.
ps I had nvidia legacy drivers running on OpenSuse 11.2 via one-click install.

---

### Post by llamallama on 2009-12-30
I figure I should share my experience with this as it is proving to be a fun project.

First, thanks lazy-devil! Your instructions have been most helpful. I'm writing this from my TC1000 because of them. I've been working on getting a faster running installation and would appreciate any adivce on the issues I have left to tackle.

To have something that runs decently fast (faster than XP with Avast Antivirus running) I've decided to not even bother with Gnome, KDE, or XFCE. Instead, I did a command line install of Ubuntu Karmic and am running LXDE. The responsiveness is much better and is featureful enough to keep this laptop useful.

There are a few other features I've had to fill in due to using such a lightweight desktop. The first is the ability to connect to wireless networks. For that I install network-manager-gnome and run nm-applet from my .xsession file. I know that wicd is faster but it doesn't handle well with networks that don't broadcast their essid. Then there's the need for a decent battery monitor. The one in LXDE is too basic IMO and actually doesn't work on the TC1000. For this I install xfce4-power-manager and run that as well from .xsession.

For web browsing, Firefox is just too slow for this thing. I find that epiphany-webkit handles quite nicely. Galeon, or even Google Chrome would be good as well.

There are a couple of other things to add. Since this started from as basic as Ubuntu gets, it's probably a good idea to install laptop-mode-tools as well as longrun. To use longrun be sure to add cpuid and msr to /etc/modules.

One challenge I have left is screen rotation. I'm unsure of how to get this going. Is it just a matter of having the right settings in xorg.conf or will I need to use the nvidia legacy drivers?

Another challenge are the "buttons" to the right of the ports bay. They are normally used for screen rotation, bringing up the writing pad, and the journal in Windows XP. I have no clue on how to make those work. Until I do, I'll just create shortcuts in my taskbar.

I hope this helps someone. If anyone has advice on how to deal with the screen rotation, video drivers, or extra buttons I'd really appreciate it. I'll keep posting as I progress.

Thanks

---

### Post by alex_schmidt on 2010-01-11
I've istalled ubuntu 9.10 and got black screen after installing video diver. Help me, please!
How can I cure it?

---

### Post by 9AndS on 2010-01-12
> **alex_schmidt said:**
> I've istalled ubuntu 9.10 and got black screen after installing video diver. Help me, please!
How can I cure it?
I get same problem:(. anyone any thoughts?
ps to change driver back you need to start in recovery mode(from grub menu) than type in console mode with root authentication:
> nano /etc/X11/xorg.confand change Driver from "nvidia" to "nv" , save changes and reboot.

---

### Post by maurespo on 2010-02-20
Ciao Lazy-devil,

great article! Thank you so much for your patience!

Only a question: but how many ram have you installed on your TC-1000?

On my TC-1000, i've only the original's 256MB.

I ask to you this, because the installation of the alternate version of the 9.10 Karmic on my tablet, is very very slow, startup is very very slow, and ALL is very very slow.

Can you give me some tips on how i can make a little bit more fast the system?

Thanks for feedback!
Mauro

---

### Post by 9AndS on 2010-02-21
On my TC1000 I have added one 256MB dimm ddr, so it's 512MB in total. I replaced hdd to a larger and faster one and also replaced old wlan adaptor(which didn't support WPA2) to a one from Belkin G+ router. And I think I replaced the stylus battery too.:D

Some time ago I decided to find a lightweight replace for Ubuntu and found #!(Crunchbang), which is great Ubuntu-based distro. But without video drivers no Linux distro could satisfy me. So I simply installed Windows XP Home and I am happy now(I can even watch youtube in low quality). Everything you need is working: nvidia, stylus, all buttons and screen rotation are working without years of studying Linux's 'Wonderland'. Linux is a black hole which consumes your most expensive thing - time, which is way more expensive than a copy of Windows os.

---

### Post by barronmo on 2010-03-23
I tried and got thru the install but the stylus doesn't work.  I replaced battery in stylus.  Any advice?

Thanks in advance.

Mike

---

### Post by lazy-devil on 2010-03-23
barronmo:

Congrats on the install. Bummer about the stylus. First lets eliminate some obvious things:

How long ago did you use the stylus with Tablet XP? I mean, was the TC1000 sitting around unused for month/years?

If it was sitting, did the old battery show any signs that it had leaked?

When I get home this evening, where my tablet is, and my notes; I'll check back.

---

### Post by lazy-devil on 2010-03-23
barronmo:

Let's see your xorg.conf file. That might have a clue.

---

### Post by barronmo on 2010-03-23
It did sit unused for about one year.  However, when I removed the old battery, I didn't see any signs of corrosion.  Is there a way to test the pen?

Mike

---

### Post by barronmo on 2010-03-23
I'm at work until tomorrow night.  When I get home I'll copy the file and post it.  Thanks for your help.

Mike

---

### Post by barronmo on 2010-03-25
Lazy-devil:

Unfortunately things are worse now.  After turning my computer back on today all I can see is a thin grey bar on the left hand side of the screen.  No mouse pointer, no response from the computer to any keys.  Any ideas.  

I did not have a Xorg.conf file so I created one per your instructions by copying the text you provided.

Thanks for any help, 

Mike

---

### Post by lazy-devil on 2010-03-26
Mike:

Sadly, that does sound worse. Does the gray bar show right away, or does it come up as if part of the Ubuntu boot process? I mean when you first power on, do you see BIOS splash screen with the large red "COMPAQ" in the center of the screen and the white bar on the bottom edge with the "Phoenix" logo on the far right? If not, it sounds like it might be more hardware related than operating system.

If you do see the red "Compaq" on startup than the video hardware might be OK. How did you do the install? From an external CD drive or a USB flash drive? Will it boot from a Live CD?

If you copied the xorg.conf file than that is probably not the issue.

This is a link to the service manual:

[http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=307008&targetPage=http%3A%2F%2Fbizsupport2.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc01130934%2Fc01130934.pdf](http://h20000.www2.hp.com/bizsupport/TechSupport/CoreRedirect.jsp?redirectReason=DocIndexPDF&prodSeriesId=307008&targetPage=http%3A%2F%2Fbizsupport2.austin.hp.com%2Fbc%2Fdocs%2Fsupport%2FSupportManual%2Fc01130934%2Fc01130934.pdf)

I'll do some checking and asking around if the gray bar rings a bell with anyone.

Keep the faith, man, where all in this together.

---

### Post by barronmo on 2010-03-29
I see the splash screen and it seems to follow the normal boot timing.  It even makes the Ubuntu drums noise.  However, no display is visible.  I tried booting from the startup disk and removing the contents of the Xorg.conf file.  I also got it to boot in recovery mode and erased the "Wireless Off at Startup" line from the autostart file.  Still no luck.  

Mike

---

### Post by lazy-devil on 2010-03-30
Mike:

That's sounds like good news, since it probably eliminates a hardware problem.

It seems like a driver problem. Make sure the "driver" line in the xorg.conf file is set for "nv" and NOT "nvidia".

I'll do some more checking in my notes as that sounds like something thart happened to me early on. As I recall it involved some splash settings, but I'll check.

---

### Post by cdeist on 2010-04-26
Hey guys. This is my like...official first post I think.
I'm relatively new to the whole Ubuntu thing, and I've successfully built 2 ibm t41's and a desktop, and i recently got ahold of this compaq doohickey. I will attempt to follow your steps and see if I can get my stylus to work as Ubuntu is already installed. One thing I simply must do tho is upgrade the RAM. This is painful to work on right now. Any ideas on how to speed it up/streamline ubuntu until my chip comes in?
Btw, that gray screen i saw when i had a blue tooth mouse adapter plugged into the USB port. Unplugged it, rebooted = everything was aok.
Packrat

---

### Post by lazy-devil on 2010-04-28
Packrat:

Glad to hear that removing the bluetooth adapter got the screen working. It might be a wonky driver. I used to use a wireless (but not bluetooth) mouse with my TC1000. I never tried it with Ubuntu. I'll have to dig it up to see if it would work.

For RAM upgrade there was a helpful thread at Tablet PC Buzz:

[http://www.tabletpcbuzz.com/showthread.php?t=34570](http://www.tabletpcbuzz.com/showthread.php?t=34570)

it referenced a lot of good information. Good luck.

On another front, the fpit driver seems to have been removed from Ubuntu 10.04. I updated to the Beta 2 and then the Release Candidate and both worked for everything except the stylus. Maybe the fix will come with the final version. I keep hoping every update will contain the fix.

---

### Post by hollow5555 on 2010-05-08
Excellent instructions! Thanks a ton. Mine is up and running. The only issue(s) I have are:

1) Screen rotation. It tells me the only acceptable orientation is "normal". Has anyone gotten this working? I'm using the nv drivers.

2) Is there a way to have the cellwriter window up for the login window or do I need to use the keyboard to login (or use autologon)?

Thanks!

---

### Post by hollow5555 on 2010-05-09
Ok, I got rotation working by adding ```
Option "Rotate" "RandR"
``` to the Device section of xorg.conf related to the nv driver. After a reboot I can now rotate the screen and I've made icons on my top bar to do it.

Now I'm just trying to figure out how to get the screen to rotate automatically when I connect/disconnect the keyboard. It seems like the "connect" part isn't so tough (though I haven't done it yet) using udev rules, but the disconnect part could be an issue.

Anyone have any ideas?

---

### Post by Malbeck on 2010-05-09
> **hollow5555 said:**
> Ok, I got rotation working by adding ```
Option "Rotate" "RandR"
``` to the Device section of xorg.conf related to the nv driver. After a reboot I can now rotate the screen and I've made icons on my top bar to do it.

Now I'm just trying to figure out how to get the screen to rotate automatically when I connect/disconnect the keyboard. It seems like the "connect" part isn't so tough (though I haven't done it yet) using udev rules, but the disconnect part could be an issue.

Anyone have any ideas?

Great to see that you got the rotate to work. How did you "I've made icons on my top bar to do it"? I did add the "Rotate" "RandR" to my xorg.conf.
I have 8.10 running on my TC1000, pen and everything works fine. Just want that screen rotation option to work for me.
Thanks

---

### Post by hollow5555 on 2010-05-10
> **Malbeck said:**
> Great to see that you got the rotate to work. How did you "I've made icons on my top bar to do it"? I did add the "Rotate" "RandR" to my xorg.conf.
I have 8.10 running on my TC1000, pen and everything works fine. Just want that screen rotation option to work for me.
Thanks

To make the icons I just added a "launcher" applet to the panel and created 2 buttons on the launcher. One runs the command "/usr/bin/xrandr -o left" and one runs the command "/usr/bin/xrandr -o normal" and then whichever button I push it rotates that way.

I actually had a neat idea on how to do the autorotate that I'm working on and it involves a bit of scripting logic. Basically I can see the keyboard if I do an lsusb so I'm going to write a udev rule to rotate normal when it gets plugged in. Rotating when UNplugged is the tough part because udev doesn't say WHICH device was unplugged, just that it was unplugged. So when the system boots up it will create a text file that is basically a list of devices found with lsusb. Then I'll write a udev rule that whenever ANY device is unplugged it will run a script that looks at the list of devices from lsusb, compares it to my previous listing, and if the keyboard is missing it will rotate the screen. I have no idea if this will all actually work, but I'm going to try!

As for the onscreen keyboard during login I just realized I installed 9.04 instead of 9.10! *facepalm* Time to reinstall... oh well, at least I know it all works! I've run into some other issues in 9.04 that are probably worth upgrading anyway... For example xfce won't run xfdesktop automatically if it's in the "Normal Icon/Launcher" mode, only if I set it for "No Icons" or "Minimized Application Icons". Anyone have any experience with this in 9.10? Does it work right there?

---

### Post by lazy-devil on 2010-05-12
Hollow5555:

This link gives hints for Cellwriter at bootup:

[http://www.krizka.net/2008/01/02/cellwriter-handwritting-recognition-for-gnome/](http://www.krizka.net/2008/01/02/cellwriter-handwritting-recognition-for-gnome/)


ALSO is seems like progress is being made for "fpit" in 10.04

---

### Post by joshlindem on 2010-05-12
Hi all, a little late to this game but now that I found you all talking about a TC1000 I'd like to jump in.
Long time computer tech, after a couple revisions I'm still relatively new to Ubuntu though.

I have a TC1000 and was actually thinking of getting rid of it, until it dawned on my to look at putting Ubuntu on this device as well.

Reading through this post I'm a little confused. Should I be looking at putting the newest version of Ubuntu (10.04) on the device or this "Karmic".  Never heard of that one before, and I seem to be missing it.  Where do I go and download this from? 

Has anyone tried the Ubuntu 10.04 netbook edition?  Would that work on this? Being that they revamped the OS for a more portable system was curious if it would run better on this device.

---

### Post by lazy-devil on 2010-05-12
Josh:

Welcome to the discussion. "Karmic" is Ubuntu version 9.10, known as the Karmic Koala. Version 10.04, is the "Lucid" Lynx. Each version has had an animal name along with the version number. The name is usually just shortened in conversation to the relevant adjective. Hence the "Karmic".

By all means, load up your TC1000 with Ubuntu. Any flavor beats the pants off Tablet Windows.

At this time, there is an issue with the stylus driver, fpit, in 10.04. I am sure it will be resolved shortly. Everything else in 10.04 works great on the TC1000. But just to ensure that your hardware is functioning, in total, with Ubuntu, I would first install 9.10. You can always update to 10.04 when the driver bug is squashed.

As for the netbook version, I have not tried it. My feelings are that since it is optimized for the Atom processor, and the Transmeta Crusoe processor in the TC1000 is quite finicky, I lacked courage.

BUT, I know others have tried it, and I am sure will chime in their feelings.

Best of luck and don't hesitate to post your experiences. I feel the quickly orphaned TC1000 will live again for many with Ubuntu. Mine sits next to my chair in the living room, and is a reference tool while watching TV or to look something up while reading. Be sure to check out "FBReader" in the Ubuntu Software Center. It turns the TC1000 into a 'buntuPad.

---

### Post by joshlindem on 2010-06-02
So far so good.  I installed ver9.10 and it installed just fine.  I followed the instructions and I've gotten my wireless to turn off on boot. (I also have it auto-login too)

I had to go and find how to enable root login since apparently Ubuntu is the only distro that disables it.  Not a bad thing, good security measure, but after I enabled root to log in I was able to go and install the conf file.

Now my pen works.  happy day!

Now, I have a question for you all.  How do I make the OS run a little faster.  I have 256MB in the machine and don't have the funds to go and upgrade the memory.  I turned off a few of the things in the startup that I knew didn't need to be there.  Just wondering what other things can I do to streamline the OS.  It seems sluggish.  Almost, dare I say, a little more (or equal) to what it was when I had WinXP on there.

Suggestions?

---

### Post by hollow5555 on 2010-06-04
Hey guys, more progress made in my attempts to get a fully working tc1000 without manual steps during use (ie: automatic screen rotation when keyboard is unplugged, right mouse click working with pen button 2, etc...)

My latest progress involves getting the pen's second button to function as  the right click on the mouse without the need to run the xmodmap command that affects the touchpad. The solution:

Install xinput and run ```
xinput set-button-map TOUCHSCREEN 1 3 0
```

This maps pen click 1 to mouse button 1, pen click 2 to mouse button 3, and disables pen click 3 (there is no pen click 3 so who cares?)

Put this in a startup script and you should be good to go! Now I can move on to udev rules and scripts to autodetect keyboard removal/addition and rotate the screen accordingly!

:P

---

### Post by hollow5555 on 2010-06-08
Success!!!!! Autorotate works!

I'm attaching the files that make it work. There are 3:

[LIST]
[*]80_tablet.rules - udev rules file. Copy it to /etc/udev/rules.d (or whatever your udev rules directory is)
[*]orientation_normal.sh - Script to rotate screen to normal orientation for active user. Copy it to /usr/bin and set it to executable.
[*]orientation_tablet.sh - Script to rotate screen to tablet orientation for active user. Copy it to /usr/bin and set it to executable.
[/LIST]

When the keyboard is plugged in udev will trigger the orientation_normal.sh script. This is a pretty straightforward script that just gets the current user name and sets the orientation of display :0.0 to normal for that user name.

When a usb device is unplugged udev will trigger the orientation_tablet.sh script. This script will first check lsusb to see if the keyboard's pciid is missing. If it is then it checks the resolution of the screen. If the x resolution is greater then/equal to the y resolution then we're in normal mode and should rotate to tablet (left) orientation. If we're already in tablet mode, do nothing.

Tada! It all works! You may need to verify that the PCIID of the keyboard is the same as mine (not sure why it wouldn't be but mine is actually a pre-release hardware version. It's most likely the same but I can't promise. If my keyboard is a different pciid than yours, just change the udev rules and script files to match your keyboard.

Enjoy!

---

### Post by joshlindem on 2010-06-09
OK, need some HELP and ADVICE!

I have mine working as previously indicated.  But I'm having a few issues that I'm unsure how to fix.

1) Any way to speed this OS up (other than with memory)?

2) When not in full use, I have this sitting on a cheap picture frame stand from an art supply store and use it as a digital photo frame.
My problem here is that the screen keeps turning off after a certain period of time.  I don't know why.  I checked and the screensaver is not turned on.  And I set the power management to never turn off when plugged in.

Any suggestions??
Josh

---

### Post by joshlindem on 2010-06-14
Hey where did everyone go?  I jumped on to this project and everyone else is done and left? drats!

Well, if any of you do venture back I really could use some help.

1) What can I shut off (or uninstall) to help make Ubuntu run faster?  I ran through and got rid of programs I thought would help...and it did... until I rebooted.  and then I couldn't log back in again with anything.

2) Screen kept turning off even though I told Power Management to not do anything and screen saver is not enabled.

3) Screen Brightness. Where can I go to brighten this up.  I turn it on and it just seems to be dim\dark.  I'm pretty sure it has the ability to get brighter, but that was within the Windows functionality.  Do we have that ability in Ubuntu?

---

### Post by Tolan on 2010-06-28
Hi joshlindem,
 
I have a TC1000 but will change to a TC1100 soon, as they come quite cheap here.
 
Ubuntu is quite slow on the TC1000, I use crunchbang currently (with an addition called Adesk-launcher, a python script that gives a Netbook-interface) which is faster (but still slow with programs starting). 
 
I am currently trying to get the NVIDIA-Driver to work to see if they speed up things a bit. Else I will try VESA / XVESA.
 
As soon as I find out more, I'll post it here.
 
Tolan

---

### Post by cdeist on 2010-07-21
hey guys: 
New chip came in. 768mb ram now :-D. installed xfce and it is much more usable now. (Last night something happened and i had to redo the whole install...don't ask). I'm going to research making an image of this thing so i dont have to do that again...
I dropped Galeon, and I am about to add that rotate and randr thing too...
Def go with XFCE boys...it makes it much easier to use.
Btw...i also got debian 4.0 etch running on the wii this past week.
Rat

---

### Post by brotherlouie on 2010-08-13
no wonder the tips in the tc1100 thread wasn't working for me,
i just found out that i have the TC1000 instead. so here i am. 
installing 9.10 right now. will try the tips posted by lazy-devil.

i found this on the net tho, was wondering what the experts here think of this.
[http://www.techeye.net/software/patch-turns-transmeta-crusoe-into-a-full-i686](http://www.techeye.net/software/patch-turns-transmeta-crusoe-into-a-full-i686)
i think its a patch to make the processor on the TC1000 run a little better.
but i don't know how to use it, or if it is safe to use.
hoping somebody here can enlighten us.

tnx!

---

### Post by GaiusJuliusCaesar on 2010-08-13
I've got a TC1000 too and will follow these tips to get 9.10 installed, thanks lazy-devil.  Does this work on 10.04?

---

### Post by brotherlouie on 2010-08-13
got the pen working finally! 
just had to say thanks for this thread, it helped me alot.
im updating everything now.
will try to tackle rotation and wifi next.

---

### Post by charon79m on 2010-09-18
Hey, everyone!  So glad to see renewed interest in this platform again.  Honestly, I've not used my TC1000 in a year or so, since I got a HP 2730P tablet.

I dug my old tablet out when I ran across a new Ubuntu based distro called Node0, and I though it would be fun to toss it on this old hardware and play around.  I googled for my old post on the fpit driver and found this thread instead.  I'm SO GLAD I DID!

I'm now up and running with my tablet.  Stilus is working great and I'll be looking over all the other posts with suggestions.

My personal favorite apps are Xournal for taking notes, cellwriter for the onscreen keyboard, and TuxPaint for my daughters to play.

I'm really interested in getting the NVidia drivers working on this.  At one point a few years back, compiz worked on this little gem.

I don't really have anything to add at the moment other than the encouragement another successful install can provide.  Hope to see more fun posts in this thread over the next months!

---

### Post by shaolin77 on 2010-10-01
Hey Everyone....Can I join this party too?  :P


I also have a TC1000 and want to install Ubuntu 9.10.   I downloaded the iso for installation via USB however I'm running into an error:


**(initramfs) unable to find medium containing a live file system**



My First thoughts were maybe the iso was corrupt so I figured I download it again...and recreate on USB drive....but I'm still running into the same error message...any help would be greatly appreciated.   

By the way did any of you have to change the boot order in the bios so that USB drive kicks off first?

Please help!!!  Thanks!!!!

---

### Post by shaolin77 on 2010-10-01
Looks like I have resolved the issue....with not being able to install Ubuntu 9.10 on the TC1000.  

Not sure exactly what resolved the issue at this point...I reformatted my USB thumb drive and prepared it for the iso....same as I did last night.

The only thing I did different this time was to not connect the power supply.  Its currently running the install on battery power...and it actually started the installation..so far so good.....

---

### Post by shaolin77 on 2010-10-04
Just another quick update...the installation went fine and thanks to those who have taken the time to work on getting the tc1000 up and running...all your hardware work is greatly appreciated.


My tc1000 only has 512mb of ram...and while this are not blazing fast..I would like to find out if anything can be done to speed it up a bit.   I'm contemplating buying a 512mb memory module to bump up the tc1000 to a total of 768mb...not really sure if that will even make a difference in performance though.

Have any of you tried lighter distros or even attempted to max the tc1000 to 1GB per the links provided earlier in this thread?


Hopefully you guys still find interest in getting the tc1000 working optimally.


Thanks again!!!

---

### Post by cdeist on 2011-01-09
Well, sorry bout the lag, been a little busy with other projects. Remember my tc1000 is at 786MB ram. well it was still a bit laggy, and i got frustrated with it, even with XFCE. I had conducted an experiment and dropped Xubuntu on a p3 650, and then Lubuntu on another. Lubuntu ran better. Sooooo i tried that on the tc. Seemed to fair a little better, but still not good enough. (my xorg.conf didnt work), and i also realized my aaaa battery was dead. Now I have no idea where in the heck to buy one of those so I ordered it online, and am now waiting for it to come in. So as of now I have reverted back to 9.10 + xorg here and all should be back to normal except now I will install LXDE instead of the full 10.10 Lubuntu set up, will post my findings once the install is finished.
Cdeist

---

### Post by cdeist on 2011-01-09
Ok so it seems the best combo so far is 9.10 with LXDE. Very usable. However, still having trouble with AutoRotate....
Cdeist

---

### Post by jasonofx on 2011-03-19
Dead thread revival! I recently got a TC1000 and a TC1100 given to me. Was able to torrent the HP/Compaq recovery disks for both, etc. I am a HUGE Ubuntu enthusiast, and have been using it alongside Windows for many years now. I am actually probably gonna keep Windows on the faster TC1100, and am currently experimenting with different flavors and versions of Linux on the TC1000 to see what I like as far as functionality and speed. Mine has 768 mb of ram, so it's maxed out. I tried 9.04 with LXDE, but I didn't like it. Currently installing 9.10 netbook remix, might have to switch to the plain desktop install if it doesn't work right. This one I plan to use as a carputer. The TC1100 I'll leave laying around the house for my wife to use for LogMeIn at work, and for guests to use, and just to use while laying around on the couch or in bed. I want to keep this thread active, because I've been searching for forums regarding Linux on these tablets, and there's not much out there. Thanks to all who have contributed, and I'll re-post if anything interesting comes up.

---

### Post by jasonofx on 2011-03-20
Anybody get WPA working with the wireless card in Ubuntu? In Windows I was able to download the latest driver to get WPA working. Do you think I could use ndiswrapper with that Windows driver or should I just Ebay a different card?

---

### Post by DesertEagle on 2011-03-24
10.04 and later got most of the hardware down: xrandr rotates the screen, fpit drivers are functioning -albeit after editing xorg.conf- and the wireless card works out of the box

---

### Post by personoperson on 2011-04-02
After installing Ubuntu 10.10, I entered the terminal and tried to install fpit using apt-get but it gave an error about xorg and xserver.  Then I tried to install fpit through synaptic package manager.  It listed what packages needed to be remove for fpit to be installed and it was every package installed on the computer, and there were no other package to be installed replacing them!  I'm not sure what I did wrong or if it is a glitch and all those packages don't actually need to be uninstalled.
   Thanks for any help!

---

### Post by James1975 on 2011-04-05
ok so the the smash is this pardus2007 runs smooth on tc1000, however I've never seen anyone do any research for that flavor as far as getting the tablet functions working.:lolflag:

i know that doesn't help much but at least  i found a distro that runs smoothly on the unit!

---

### Post by jasonofx on 2011-04-21
> **DesertEagle said:**
> 10.04 and later got most of the hardware down: xrandr rotates the screen, fpit drivers are functioning -albeit after editing xorg.conf- and the wireless card works out of the box

Does it run slow? I got 9.10 netbook remix up and running, but it was just so slow. I am using separate hard drives for the Windows and Linux installs I am doing, mostly for comparison. So far, there's no linux install that runs as quickly as XP tablet with all of the functions working. I REALLY like the netbook interface, but am just about to give up. This tablet is slow by today's standards, anyway, but I thought for sure that Ubuntu would be quicker on these than XP.

---

### Post by linuxlover42 on 2011-05-05
I know this is an old topic but I've been experimenting with 11.4 on one of these things and the closest I've gotten to getting the pen working is a spectacular crash of x when I touch the screen with it.
[LEFT] I had some problems with the video drivers but I got nv driver working pretty well (might try to upgrade to noveau after I get the pen up.
The two closest attempts at getting the pen up used the xorg.conf file in this thread and an auto-configured xorg.conf file to which I added the code which works the pen from the one in this thread.
Anyone have any Ideas?
[/LEFT]

---

### Post by OpenSorce on 2012-11-09
I've tried many different configurations and distros since I found this thread without success. against my better judgement and the constant protests of the guys in #unbuntu on IRC, I hunted down an ISO for 9.10 and used it via netboot to load onto my TC1000.

Using the excellent guide in the original post here, everything works...

This little machine has never run this good or been this useful before.

---

### Post by wildmanne39 on 2012-11-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

