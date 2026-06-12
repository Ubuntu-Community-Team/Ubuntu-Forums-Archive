---
title: "Fujitsu Stylistic St5010D"
date: 2009-09-06
forum: Hardware
---

### Post by billklee on 2009-09-06
I just picked up, as mentioned in the title, a Fujitsu tablet PC, a Stylistic ST5010D. My intent was to make an Ubuntu-based e-book reader and web browser and, of course, to play with it.

I installed Kubuntu on it, with the intention to add Ubuntu and Xubuntu later. The biggest reason I went with Kubuntu for the base installation is because I happen to have a Kubuntu 9.04 cd on hand. I knew it might be a bit tricky, having gone through several forum searches for "tablet." However, it might be a bit trickier than I anticipated.

As I said, I installed Kubuntu on it, which took a bit of juggling, right off the bat, but it's installed. It seems to work, for the most part, but the first thing I have trouble with is networking. I'm sitting at a rest area in Texas (I'm a truck driver, and it gives me something to do while I'm waiting for a Tuesday morning pickup), and it does not see the wireless access point. Oddly enough, my other laptop, a Dell Inspiron E1505n, does see it, which is how I'm posting this.

If I have to, I can wait until I get home next weekend and plug in an ethernet cable, but if I can get it working now, I'd certainly like to.

I've got several threads bookmarked that I hope will help with the general setup and configuration. There are a few things I've thought of I want to set up.

1: I want to be able to rotate the display and have it automagically change from landscape to portrait when I do so (when I use KRandRTray, it rotates the display, but the orientation does not change - the display is pushed up into the upper 2/3 of the screen, with the left and right ends pushed off-screen. I need to get it to switch from 1024x768 to 768x1024, obviously.

2: Also, when I rotate the screen, the mouse or pen goes semi-wonky. By that, I mean that even though the display had rotated 90 degrees, the mouse moves at about 10 to 15 degrees off of the original orientation, but does not move evenly. I'm hoping that calibration will fix that.

3: I've got it set up to load a virtual keyboard (kvkbd) before login, but it's not working quite right, either. Just before the login window appears, the keyboard pops up, but disappears when the login comes up. As soon as I log in (with a real keyboard) and it finished loading, kvkbd comes back up. I found a thread a couple of weeks ago that detailed a method of doing so, but neglected to bookmark it, and can't seem to find it now.

4: as I mentioned above, it doesn't see the local wireless access point I'm using with the other laptop. Oddly enough, when I first installed Kubuntu, it wouldn't see the access point, but I remembered that the ST5010 has a switch on the back to turn the WLAN on and off, and I'd turned it off to save battery. When I turned it back on, and rebooted, it saw the access point, but wouldn't connect. I decided to try re-installing Kubuntu with the WLAN switched on, on the feeble hope that if it was on during installation, then maybe whatever drivers it needed would be installed. As it was a new, clean install, I had nothing to lose, so I went ahead with it. Afterward, it won't even see the access point. Bad call on my part, obviously.

5: the stylus works as a single-click mouse only. There's a rocker switch on the barrel, which is supposed to be right-click (push forward) and erase (push backward), but those don't work. However, they didn't work before, either, so in this case, I think I need to get a new stylus.

When I first got it, it had Windows XP installed, and it worked pretty well. It booted up quickly, the WLAN worked (for the most part - it did not work when I first got to the rest area, but then, as I mention above, I had it turned off. Had it been turned on, it might well have see and connected to the access point. As for the stylus, the right-click and erase did not work in Windows, either, so I believe the stylus is defective. However, in Windows, if I held the stylus point against the screen for a few seconds without moving it, it would pop up with the right-click contextual menu. It does not do this in Kubuntu.

Two final questions, before I post this and go to sleep.

First off, is there a particular linux distribution that works better with tablets than K/X/Ubuntu?

Second, software. As far as I can tell, I need to install wacom-tools to get it to work right, or at least better. I've seen mention of cellwriter, xournal, easystroke and basket, and intend to check them out. Are there any others that I should check out?

Almost forgot the specs:
1 GHz Intel Pentium M
1 GB RAM
60 GB HD
Atheros WLAN

---

### Post by Favux on 2009-09-06
Hi billklee,

Sounds like a fun project.  By the way you have a serial Wacom tablet pc.

To get the stylus to change orientation you need a xsetwacom command to go with the rotation.  Since you're in 9.04 we need to check a few things.

Make sure that both 0.8.2-2 linuxwacom packages are installed:  xserver-xorg-input-wacom & wacom-tools.

To use xsetwacom commands and wacomcpl (the calibration and configuration gui) in a terminal:
```
xsetwacom list
```
should return stylus (and eraser if you have one).  If blank to see what HAL's calling things enter:
```
xinput -list
```
There's a couple of ways to go, see Jaunty User's near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Rec's script may be a good option.

Then to look at some rotation scripts see:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)

For wireless you'll need to post on the Wireless & Networking forum.  There's several big threads that should be helpful and I've see the Atheros chipset dealt with.

Since you're in Jaunty the tablet is configured through the 10-wacom.fdi, not the xorg.conf.  It's at /usr/share/hal/fdi/policy/20thirdparty/.  So keep that in mind when looking at these links:

[http://narnia.cs.ttu.edu/drupal/node/165](http://narnia.cs.ttu.edu/drupal/node/165)

[http://ubuntuforums.org/showthread.php?t=514842](http://ubuntuforums.org/showthread.php?t=514842)

[http://en.gentoo-wiki.com/wiki/Gentoo_Fujitsu_Stylistic_ST5010_Manual](http://en.gentoo-wiki.com/wiki/Gentoo_Fujitsu_Stylistic_ST5010_Manual)

Hope this was helpful.

---

### Post by billklee on 2009-09-06
Thanks for the response!

I am taking notes. For what it's worth, I plan to write down *everything* I do, as I do it. That way, I'll know (hopefully) what works and what doesn't, and, if anyone else is interested, I could post it all as a how-to when I'm done.

It looks like I'll have to wait, though, until I get home next weekend. I'll need network access to install stuff, and all I've got here at the rest area is sporadic wifi provided by the state of Texas. Once I leave here, I probably won't have any internet access until I get home, or if I hit a rest area back here in Texas (unlikely) or maybe in Iowa (also unlikely). I've got the week after next off, so I should have time then to get to work on this.

I'd be hitting all these pages and taking extensive notes while I've got the time, but the ubuntu forum pages are very slow to load. Still, I've got nothing better to do, and not much else to read.

So far, I need:
xserver-xorg-input-wacom
wacom-tools

---

### Post by Favux on 2009-09-06
Hi billklee,

Correct, and usually xserver-xorg-input-wacom is installed by default alond with the 10-wacom.fdi.  The one you may have to install is wacom-tools.

---

### Post by billklee on 2009-09-16
I've finally been home and had a few days to work on it. There were four main things I wanted to get working: wireless, rotation, tablet buttons and on-screen keyboard for login. I've had some success, and with a few more hints, I'm pretty sure I can get the rest.

1: wireless. The first thing I did with this tablet when I got home was to plug it into my DSL and run *sudo apt-get update;sudo apt-get upgrade*. After that, the wifi works like a charm. Wish the rest of it was that easy.

2: screen rotation. I'm using your Method 1, right-handed script from the opening post of **How to Rotate the Screen for a TX2000 Tablet PC**. It works 2/3 perfectly. The screen rotates, and maximized windows resize themselves to the new orientation. That's 1/3. The mouse also rotates, so the cursor moves correctly. That's 2/3. Unfortunately, the stylus does not rotate. That's the missing 1/3.

When in portrait mode, which is where I intend to mainly keep it, the stylus is 90 degrees off. If I touch the stylus to the upper right-hand corner of the screen, the cursor is in the lower right-hand screen. As I move the stylus down the edge of the screen, the cursor moves to the left, taking the same time to go from bottom right to bottom left as the stylus does from top right to bottom right. Different distances, same time. As I move the stylus clockwise from corner to corner, the cursor stays ahead.

I'm not sure if it's a calibration problem, or something in the script. When I try to run wacomcpl to calibrate the stylus, I get this:
```

william@buntablu:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1953)
william@buntablu:~$

```

As I get the time, I'm going to have to read the other 28 pages in that thread.

3: the tablet buttons. They don't show up in xev, and I don't know how to make them do so. I tried downloading fjbtndrv, which is supposed to cover that, but when I run *./configure* it fails, telling me that it can't find 'hal'. Now, I had to install four or five other packages it couldn't find, but hal is already installed. I don't know what to do with fjbtndrvpast this point.

4: on-screen login keyboard. So far, I've found 3 ways to get an onscreen login keyboard, and none of them work.

The first one involved kvkbd. It pops up before the login window, then promptly vanishes an instant before the login window appears. It then reappears as soon as login is finished.

The second involved xvkbd. It, too appeared before the login window, but then the system stalled right there. I let it spin for five or ten minutes to no avail.

The third method also involved xvkbd, and kdm. This time, I got the keyboard and most of the login window. I say 'most of' because the window came up, but the username and password fields wouldn't show until I exited xvkbd.

So, I need to work at that some more. gok, sok and onboard all sound like they might work, so I'm going to go ahead and install ubuntu-desktop, since it sounds like they're Gnome products, and the instructions for setup all go through Gnome.

---

### Post by billklee on 2009-09-16
Installed Ubuntu & Kubuntu desktops & tried them. Not much, just wanting to see how rotation & stylus/cursor positioning works. When I rotate in Ubuntu, the display looks like crap (video is bad - can't describe it, I'll have to try to get a screenshot - and the display only covers the top 2/3 of the screen - it's like the rotate script isn't doing anything), the stylus is still un-rotated and the mouse seems to be about an inch to the left of where the cursor is.

In Xubuntu, it rotates just fine, but the stylus is till un-rotated.

My wife wants me to help with a bunch of yard work, so I'll have to wait until this evening/tonight before I can try anything else.

---

### Post by Favux on 2009-09-16
Hi billklee,

I've looked but haven't seen anything saying it has a Wacom digitizer, presumably serial (rather than usb).  But assuming it does make sure in Synaptic Package Manager that both linuxwacom packages are installed:  wacom-tools & xserver-xorg-input-wacom.

The reason the stylus is not rotating is probably due to what name HAL/dBus is returning for it.  For the xsetwacom command to work:
```
xsetwacom list
```
should not be blank.  To see what HAL is calling the stylus enter:
```
xinput --list
```

The Xorg Intel video driver has problems with Jaunty (9.04).  There are some threads that deal with that.  They tell you how to change the Intel driver and/or modify xorg.conf for best performance.  I have some links if you need them.

Since you have a true slate a onscreen keyboard is a good idea.  I have some notes on that from before I realized that it really wasn't useful for a convertible tablet pc.  Let me whip them into shape.  Remember I've only tested parts of it.

---

### Post by Favux on 2009-09-16
**HOW TO Install an On Screen Keyboard for login.**

You can use several different on screen keyboards (OSK's).  CellWriter, onBoard, and xvkbd all  work.  I personally prefer CellWriter.  Check Synaptic Package Manager and if your preference isn't installed, installed it.

In "System->Administration->Login Window" select the 'Local' tab.  In 'Style' choose either  "Plain" or "Plain with face browser" (recommended) option.  Using "Themed" or  "Themed with face browser" from the login windows will not work!  The theme will cover the keyboard.  You must also be sure that the "Show title bar" option is active (checked).

The method is essentially the same for all of them.  You add to the "/etc/gdm/Init/Default" file a line for the one you prefer.  At the end of the file you'll see:
```

  fi
fi

exit 0
```
Edit using:
```
gksudo gedit /etc/gdm/Init/Default
```
And between the last 'fi' and 'exit 0' enter the line.  For CellWriter it would be:
```
cellwriter --keyboard-only --window-y=600 &
```
So it should look like:
```
fi
cellwriter --keyboard-only --window-y=600 &
exit 0

```
Save and close.

For OnBoard use:
```
onboard -s 684x200 -x 170 -y 568 &
```
These values will display the onBoard at about 2/3 the screen width at the bottom.  The -s settings control size and the -x and -y values control location.  You can experiment with them.  For example a smaller keyboard in a different location:  -s 500x130 -x 15 -y 15 &

And for xvkbd use:
```
xvkbd -geometry -300-100 -no-keypad &
```
or
```
xvkbd -geometry 684x200+170+568 -no-keypad 2&>/dev/null &
```
I have no idea what the "2&>/dev/null" is for.

Kubuntu users: In KDE 3.x put either onboard or xvkbd into the "/etc/kde3/kdm/Xsetup"  file.  In KDE 4 is it "/etc/kde4/kdm/Xsetup"?

I'm not sure what the following means but I left it in in case you can figure it out:
> Note:  If you enable automatic login, do NOT amend this file as you will end up with 2 instances of the OSK!

Finally, if you enable autologin in System > Administration > Login Window in Gnome, you still must put the keyboard line in the init script; otherwise you won't be able to log back in if you log out.


**Allowing onscreen keyboards to enter passwords (use GNOME gksudo)**

You can set up CellWriter to supply gksudo passwords.  GNOME's graphical sudo frontend, gksudo, by default grabs the focus, keyboard and mouse to prevent malicious applications from intercepting the password. However, this also prevents onscreen keyboards from entering input at the gksudo prompt. To allow this, Use the gconf-editor program (in Applications > System Tools > Configuration Editor). Find the key "/apps/gksu/disable-grab" and turn it on (check the box).  Or:
1. Press ALT/F2, type 'gconf-editor' and press <ENTER>.
2. Find and click once on 'gksu' under 'apps' in the tree on the left.
3. On the right, check 'disable-grab'.
4. Close gconf-editor
This will prevent gksudo from grabbing focus and all input. You can then input the password the normal way, using CellWriter, OnBoard, Xvkbd, GOK, etc. Be aware though that this is a potential security vulnerability.  You'll notice that the screen no longer dims when passwords are requested.

Another, and simpler, way to do this should be to in System > Preferences > Assitive Technologies to check the "Password dialogs as normal windows" box.

**If in System > Preferences >  Screensaver you've enabled "Lock screen when screensaver is active" deactivate it.**  CellWriter won't show up and you'll have to reboot.  There is a way around this but it involves introducing a keyboard widget for the screensaver.

By frafu post #4:  [http://ubuntuforums.org/showthread.php?p=1792228#post1792228](http://ubuntuforums.org/showthread.php?p=1792228#post1792228)

By phenest post #1:  [http://ubuntuforums.org/showthread.php?t=563736](http://ubuntuforums.org/showthread.php?t=563736)

By Aearenda post #167:  [http://ubuntuforums.org/showpost.php?p=6612730&postcount=167](http://ubuntuforums.org/showpost.php?p=6612730&postcount=167)

From:  [http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons](http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons)

---

### Post by billklee on 2009-09-16
Okay, the on-screen keyboard works now. Boo-yah! It works for login, and when I get everything else working, I'm going to go through those threads you linked and get the screensaver password to work, too.

When I run xsetwacom list, I get a fail for libxcb-xlib.so.0 - no such file or directory. I suspect that might be the problem with the stylus when rotated. wacom-tools and xserver-xorg-input-wacom are both installed.

While I'm thinking of it, running 
    *apt-get install wacom-tools xserver-xorg-input-wacom*
followed immediately by
    *apt-get purge wacom-tools xserver-xorg-input-wacom*
seems incredibly counterproductive, especially since you have to run
    *apt-get install wacom-tools xserver-xorg-input-wacom*
again later. The only thing I can think of is that installing them sets something up that definitely shouldn't be there at some point, and you need to install them so the purge makes sure they're removed, which, somehow, might not work right if they weren't installed. In otherwords, completeness, so you don't miss something.

Yesterday, xinput -list gave me, among other things, these lines:
"Virtual Core Pointer" id=0"
"Virtual Core Keyboard" id=1"
"Wacom Serial Tablet PC Pen Tablet/Digitizer" id=2
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" id=3

Today, it gives me this, instead:
"Virtual core pointer" id=0 [XPointer]
"Virtual core keyboard" id=1 [XKeyboard]
"stylus" id=2 [XExtensionKeyboard]
"eraser" id=3 [XExtensionKeyboard]

IIRC, yesterday's version also had the same entry after the id, i.e. [XPointer], [XKeyboard] etc, but I didn't write that part of it down. I thought the name and id would be the important parts, and I could always run xinput again. I thought I'd made a copy of it (*xinput -list > ~/Documents/xinput.txt*), but if I did, I can't find it now. Oh, well. "stylus" and "eraser" sound a lot more like what I'm reading in all these threads, anyway. Your rotation script I'm using (which, aside from the stylus problem, if that's where the problem is, is great) uses the name "stylus", so I'm fairly confident (halfway confident, anyway) that that's not the problem.

For what it's worth, my xorg.conf looks like this, with all the commented lines removed:
```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor       "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

Of course, it appears that since I'm using 9.04, I need to make changes in /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi. That looks like an XML document to me, and while I know a little about XML, it's just that: a little. I found a post about, basically, boiling down the fdi to the wacom basics, and I'm going to try that later today/tonight.

I'm going to poke around next for the Xorg Intel fix. The rotation works fine in Kubuntu & Xubuntu, except for the stylus problem. If I can fix the video rotation in Ubuntu, that just leaves the bezel buttons and the stylus.

Ah, well, more poking around. Sometimes, I think I get more fun out of fiddling with the system than using it.

---

### Post by Favux on 2009-09-16
Hi billklee,

You shouldn't be:
> While I'm thinking of it, running
apt-get install wacom-tools xserver-xorg-input-wacom
followed immediately by
apt-get purge wacom-tools xserver-xorg-input-wacom
seems incredibly counterproductive, especially since you have to run
apt-get install wacom-tools xserver-xorg-input-wacom
That's only for compiling and installing a new version of linuxwacom.  You want to clear the old version out because different versions confict and can cause weird symptoms.

Did you compile and install a new linuxwacom?  Where from?  You don't need that with Jaunty.  You want the default linuxwacom packages.  Install them through Synaptic Package Manager.  Unless you've compiled and installed a new version.  In which case you need to remove it as in Appendix 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  before installing the default linuxwacom through Synaptic.

I think you want the standard default .fdi because I think you have a serial tablet pc.  What we should be seeing is:
```
"Wacom Serial Tablet PC Pen Tablet/Digitizer" id=2
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" id=3
```
Then in the xsetwacom commands in the rotation script you would substitute "Wacom Serial Tablet PC Pen Tablet/Digitizer" for stylus and the other for eraser.  Although someone said just putting the quotes around them worked, ie "stylus" and "eraser".  See "Jaunty Users" 3) and 3a) near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by billklee on 2009-09-16
Okay, giving that a shot. I'm going to do the Appendix 4 removal, than reinstall via Synaptic.

I *think* I compiled and install from the latest package at linuxwacom - linuxwacom-0.8.4-1.tar.bz2.

When I search Synaptic for wacom, I get wacom-tools and xserver-xorg-wacom-input. The description for xserver-xorg-wacom-input says A: it's from the linuxwacom project and B:"You will also require a kernel module which supports your tablet. Many types are supported by the 'wacom' module supplied with current Linux modules."

This leads me to think that A: xserver-xorg-wacom-input is the linuxwacom I need, and B: I didn't need to download & etc the package from linuxwacom.

We'll see what happens.

---

### Post by billklee on 2009-09-16
Okay, did this:
```

sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom
cd ~/Desktop/linuxwacom/linuxwacom-0.8.4-1/prebuilt
sudo ./uninstall

```

Open Synaptic & install wacom-tools & xserver-xorg-input-wacom
reboot & log into Kubuntu
edit ~.rightflip, change "stylus" and "eraser" to stylus and eraser.
```

./.rightflip

```

It works! The cursor is lined up with the stylus and moves with it perfectly.

If I can get the bezel keys to work now, it's golden. Oh, and right-click, too. And the rotated display problems in Ubuntu.

I don't say this often, but **Favux**, you are ***da Man!***

---

### Post by Favux on 2009-09-16
Hi billklee,

Great, progress!  So putting the quotes around stylus and eraser worked for you too?  Cool.

One stylus button?  With a serial tablet you can get right click two ways, either use rec's script so you can use wacomcpl (or without rec's script in its .xintirc rename everything) or adding a line to the wacom.fdi.

There's several threads where folks try to deal with "fjbtndrv".  I think in one or two of them they figured it out.  I'm not sure if I have any links to them.  I'll look.

---

### Post by billklee on 2009-09-16
Looking better! Before, when I ran xsetwacom list, it would fail, citing libxcb-xlib.so.0 as missing. Now, I get this:
```

stylus        stylus
eraser        eraser

```

And when I ran wacomcpl, I'd get this:
```

william@buntablu:~$ wacomcpl
wacomcpl: using TCLLIBPATH="[list  /usr/local/lib ]"
Error in startup script: xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory
    while executing
"exec xsetwacom list"
    (procedure "createDeviceList" line 4)
    invoked from within
"createDeviceList "
    (procedure "createControls" line 8)
    invoked from within
"createControls"
    (file "/usr/local/bin/wacomcpl-exec" line 1953)
william@buntablu:~$

```

Now it pulls up the gui calibration app.

Still looking for the bezel buttons (maybe via fjbtndrv) and the video on Ubuntu when rotated.

And to think that an hour or two ago, I was seriously thinking about reinstalling and starting fresh. I think I'm done for today, though. I'm not young enough to get by on two hours of sleep in three days like I used to be. Shower & sleep now, more poking and learning tomorrow.

Oh, and for the stylus & buttons: the stylus has the tip button and a 2-position rocker on the barrel. Supposedly, rocker-forward is right-click, and rocker-back is eraser. I think the rocker is broken, though. When I got the tablet, it had WinXP on it, and the rocker didn't do anything then, either. However, there was a nice feature where if I held the stylus to the screen for a few seconds without moving it, it would pull up a right-click/contextual menu automatically. I've also been trying to think of the correct keywords to search the forums for that, as well as everything else.

Or, I could buy a replacement. $42US for 2, from Fujitsu, IIRC. Soon enough, i suppose. Soon enough.

---

### Post by Favux on 2009-09-16
Hi billklee,

Good, wacomcpl working, that's what we want.

Regarding fjbtndrv I found a couple of links:

[https://launchpad.net/~khnz/+archive/ppa/+sourcepub/529485/+listing-archive-extra](https://launchpad.net/~khnz/+archive/ppa/+sourcepub/529485/+listing-archive-extra)

[http://ubuntuforums.org/showthread.php?p=7318554#post7318554](http://ubuntuforums.org/showthread.php?p=7318554#post7318554)

---

### Post by billklee on 2009-09-17
Major progress with the bezel buttons.

added these two lines to software sources:
[i]deb [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) jaunty main[/i]
then ran this in konsole:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E88D7B6F
sudo apt-get install fjbtndrv

```
reboot

The buttons work. I haven't noticed that all of them actually do anything yet, but the ones I'm most interested in do. The alt button puts the word alt on-screen in green letters, the screen rotate button rotates the screen 90 degrees CCVW every time I press it, the page up/down do, indeed, page up and down and the line up/down moved the page up and down one line at a time. In an openoffice doc, it pages up/down & moves one line up/down, moving the cursor, just like using the page up/down and arrow up/down keys on the keyboard.

Hints/leads that got me here:
[This one]("http://ubuntuforums.org/showpost.php?p=7318534&postcount=16"), mostly. In this post, **rarara77** said he/she (sorry, don't know correct gender, and using "they" always strikes me as awkward) added this to their xorg.conf:
```

Section "InputDevice" 
    Identifier     "FSC Tablet Buttons" 
    Driver         "evdev" 
    Option         "Phys"              "fsc/input0" 
    Option         "SendCoreEvents"    "true" 
EndSection

```
I added that to mine, then commented it out, as I wanted to take it a step at a time. On reboot, the buttons worked with it still commented out, so I'm leaving it that way.

---

### Post by Favux on 2009-09-17
Hi billklee,

Outstanding!

If I'm following you, you are basically there.  Just some minor tweaking left to do.

With rarara77's xorg.conf section are you saying you had to use it for only one reboot or restart of X to get the bezel keys to "kick" in?  And thereafter it's not needed?

---

### Post by billklee on 2009-09-17
Nope, never used rarara77's xorg.conf entry at all. I added it to xorg.conf, then commented it out *before* reboot. I thought that if I added fjbtndrv and added that section to xorg.conf, and it worked, I wouldn't know for sure if it needed both to work, or not.

That's why I commented it out. If it worked with fjbtndrv and without the xorg.conf entry, then I wouldn't enable the entry. If it didn't work, I would then enable it, and try again.

Since it did work the first time, I've never enabled it, and I'll remove it from xorg.conf once I get around to doing so.

---

### Post by billklee on 2009-09-17
Been fiddling around a bit more with the bezel keys. Here's what happens with each key, in Ubuntu, Kubuntu and Xubuntu. The page up/down and line up/down keys were tested in Firefox and OpenOffice. If I don't mention a *buntu version, the key does the same thing in all three.

alt: shows "Alt..." on-screen for about 1 second. During that time, none of the other buttons do anything.

email: In Ubuntu, launches Evolution Setup Assistant. Does nothing in Kubuntu/Xubuntu.

screen rotate: In Ubuntu, nothing. In Kubuntu/Xubuntu, rotates display 90 degrees CCW.

esc: functions as an escape key, as per keyboard

ent: functions as an enter key, as per keyboard

Fn: does nothing, does not affect the function of other keys

page up/down: In Ubuntu, nothing. In Kubuntu/Xubuntu, functions as the page up/down keys, as per keyboard.

line up/down: functions as up/down arrows, as per keyboard.

On a different note, I have noticed that if I log out or shut down while in portrait orientation, which is almost every time, that when I log back in or start back up, the windows don't size well. They're usually full height, and wider than the window. Sometimes the stylus and/or mouse don't line up right. However, if I rotate the display, either by the screen rotate button or by using **Favux's** rotation script, everything snaps back to where it should be.

When rotated, display is still off in Ubuntu and cursor appears to be about an inch or so to the left of where it actually is, i.e. if I want to click on a button, I have to place the visible cursor about an inch to the left of the button. Rerotating the display back to landscape fixes everything.

---

### Post by Favux on 2009-09-17
Hi billklee,

Maybe cyberfish's setting's daemon might be of some use to you.  See Section 4 in gali98's Jaunty HOW TO here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

---

### Post by Tom Tiger on 2009-10-01
Hi,

I've been following the tablet threads for a while now (almost a year).
And I like to say thank you for all the great info which helped me a lot.

I have a Fujitsu Stylistic ST5021D, nice but no luck under older versions of Ubuntu.  I had everything working under 8.10, even with compiz :-)
However I upgraded to 9.04, and the problems began. 

Long story short, I got fed up and erased the disk.

- Suse 11, no luck whatsoever, couldn't even get the stylus working let alone the network....(which is odd)
- Fedora latest version, everything works, except for rotating, because your stylus won't work properly no more.
- Knoppix 5.3, not tested yet
- clean install of Ubuntu 9.04, Stylus worked straight out of the box, I added the side buttons with BIG THANKS to the work of Robert Gerlach

[https://launchpad.net/~khnz](https://launchpad.net/~khnz) and [https://launchpad.net/~khnz/+ppa-packages](https://launchpad.net/~khnz/+ppa-packages)

The buttons work after a restart, I also shut down compiz and everything works, the stylus, the side buttons, the rotate through the sidebuttons AND it takes over the stylus.

Since I had no cdrom or dvd on the 5021 I installed Ubuntu on another system and then put the harddisk back in the 5021 :-)

---

### Post by Favux on 2009-10-01
Hi Tom Tiger,

Great!  Glad you're set up in Jaunty.

Your welcome.  And thank you for the links.

---

### Post by Bailywolf on 2009-10-16
This is BRILLIANT.

I'm watching a couple of auctions on eBay right now for this model tablet.  I have exactly the same goal in mind - a stripped down ebook/media tablet and light sketching/photo-manip machine for casual use (and play).  

I so want to use Ubuntu for this instead of getting stuck with an OEM windows install.

Is there any chance of a step-by-step tutorial compiling this thread's revelations into one doc?

-B

---

### Post by Favux on 2009-10-17
Hi Bailywolf,

Not unless billklee or Tom Tiger or someone wants to write one.  I don't feel comfortable trying it without the actual tablet in front of me.  I think the thread is reasonably short and straightforward.  If you have trouble getting Ubuntu to install I'm sure you can get help at the Installation and Upgrade forum.  Maybe when you're done you'd want to try writing a HOW TO?

---

### Post by billklee on 2009-10-17
I just bought a new HD & a 1 GB stick of RAM, with the intention of starting from scratch to see if I can't narrow down exactly what's the minimum needed to get an ST5010D to work right. I then intend to post just that.

However, I ran an update this morning, and when I rebooted this evening, I'm at 800x600 resolution, no screen rotate and no bezel buttons working. The only thing in that last update was something-or-other-display-intel, so I'm pretty sure that's the problem.

I could try to narrow it down, but instead, I'm going to copy my files to the usb drive, install the new HD & RAM, then install 9.10 & see what there is to see. If that works, I'll post those directions. If not, I'll reinstall 9.04 - I know that can be made to work with a modicum of effort, and post those directions.

---

### Post by billklee on 2009-10-18
that was odd. Instead of replacing the old text with the new, it appended my new version as a new message, and right off hand, I don't see a "delete post" option.

---

### Post by billklee on 2009-10-18
**Step 1 - preparing the source:** The Stylistic ST5010D does not have a built-in optical drive, so I used USB Startup Disk Creator and the Ubuntu 9.04 iso. I think there's a Windows app that does the same thing, but I'm entirely unsure of what it is.

Plug in the USB drive and power up. While the initial splash screen is visible, press F2 to enter BIOS, page to Boot and set the USB drive to first boot. It's under hard drive, and in my case, was shown as LEXAR. Save changes and continue boot.

**Step 2 - installation:** Once the system boots from the USB drive, you have the choice of boot & run from it, install, or a couple of other options. Since we're installing, take option 2, install Ubuntu. Once it's done, remove the USB drive and reboot from your shiny new Ubuntu install.

**Step 3- installing necessary packages:** First, get the system current.
```
sudo apt-get update;sudo apt-get upgrade
```

Next, add the software repository for the fjbtndrv package, so the bezel buttons will work. Add these lines in Software Sources:
```
deb http://ppa.launchpad.net/khnz/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/khnz/ppa/ubuntu jaunty main
```

then enter this into your terminal of choice:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E88D7B6F
sudo apt-get update
```

The first line tells the system that khnz'a repository is trustable, and the second line updates the package list on your system.

Next, we add some packages
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom cellwriter xournal fjbtndrv kubuntu-desktop xubuntu-desktop
```

the wacom packages enable the digitizer and various tablet-related apps, fjbtndrv enables the bezel buttons, cellwriter is an on-screen virtual keyboard (which we'll be setting up to use for login), xournal is a stylus-based virtual notepad, and kubuntu-desktop & xubuntu desktop should be obvious.

While the kubuntu-desktop package is installing, a window will pop up and ask if you want to use gdm or kdm. Pick gdm.

**Step 4 - setting up for stylus-based login:** While in Gnome/Ubuntu, go to System --> Administration --> Login Window --> Local tab. Under Style, pick either 'Plain' or 'Plain with face browser.' Also, make sure 'Show Title Bar' is checked.

Back in your terminal, enter one of these two lines (and just one!):
```
sudo nano /etc/gdm/Init/Default
**or**
sudo gedit /etc/gdm/Init/Default
```

Most Ubuntu tips use gedit, but I'm just more used to using nano. Pick your poison here.

Go to the end of the file, and look for these two lines:
```
fi
exit 0
```

edit thusly:
```

fi

# we want to load cellwriter at login, so we don't have to plug in a keyboard
cellwriter --keyboard-only --window-y=600 &

exit 0
```

If, for some reason, cellwriter won't work for you, you could install onboard, instead, and try that. In that case, make this change instead:
```

fi

# we want to load onboard at login, so we don't have to plug in a keyboard
onboard -s 684x200 -x 170 -y 568 &
exit 0
```

**Synopsis:**: Create bootable USB drive, install Ubuntu, update said Ubuntu installation, install necessary packages and make small system tweaks.

Video and screen rotation still aren't up to snuff in Ubuntu, and bluetooth is something of a pain in Kubuntu. My workaround it to log into Ubuntu and get my b/t keyboard & mouse connected, then log out and back into Kubuntu.

Favux has done some standup work pulling all of the various threads on tablets together, and if it weren't for his sterling efforts, I wouldn't have a working *buntu tablet.

Yep, I did forget it add fjbtndrv in the first version. kde and xfce4 appear to be different ways of installing KDE and XFCE, instead of kubuntu-desktop and xubuntu-desktop. Not sure why I included gnome, since that's ubuntu-desktop for our purposes, and that's what we started with.

---

### Post by Bailywolf on 2009-10-19
This is really marvelous - above and beyond, Billklee.  

If eBay is kind, I'll return here and report on my successes - I'd use Ubuntu rather than Kubuntu (personal pref), and so might have a footnote for your procedure if there's any differences there.

Have you had the chance to use it much?  I'm curious how the experience of reading, doodling, and surfing on it hold up and how the pen works with apps like Gimp.

Again, enormous thanks for this breakdown.

-B

---

### Post by HaiAn817 on 2009-10-31
Billklee, thank you so much for the guide.  I have one question.  In the code:
 sudo apt-get install wacom-tools xserver-xorg-input-wacom gnome kde xfce4 cellwriter onboard svkbd

what is the gnome and kde for?  I could not install those to apps but if I leave them out the xfce4, cellwriter, onboard, and svkbd installed.  

I have 9.10 kubuntu on a Stylistic ST5011D by the way

Thanks again.

---

### Post by HaiAn817 on 2009-11-02
NVM, downloaded Kubuntu 9.04 and got everything but the right click button to work.  Billklee, did you ever find out if the rocker switch on your pen was bad or if it was something else?  I read through the posts and could not find anything.

Thanks agian
haian817

P.S. I don't know if it was intentional or not but you forgot to put sudo apt-get install fjbtndrv after getting the key, you replaced it with sudo apt-get update.  The first time around i inputed the latter code and could not get the bezel buttons to work.

---

### Post by Temetka on 2009-11-16
I just wanted to say thanks thanks! This worked great on my think pad x41t with no problems. This post was made using cell writer. :)

---

### Post by billklee on 2009-12-13
**Short form:** Don't.

**Long form:** It works. Sort of.

I wasted two weekends trying to install Ubuntu and Kubuntu via USB drive, to no avail. It would boot, and if I caught it in the first 30 seconds, it'd come up to the options page: Run from disk, install, etc. No matter which option I picked, the screen would go black, and that would be it.

Then, two weekends ago, which would have been the 28th and 29th of November, I decided to work my way through the installations options under F6 at the login options screen. If I checked "acpi=off" it would boot, and I could install. But when I booted from the new install, same thing: black screen and nothing else.

I figured that I had to set acpi=off somewhere on the new installation, and some poking around the forums showed me that I had to edit /boot/grub/grub.cfg.

(For the record, in grub.cfg, find the two lines that start with "linux  /vmlinuz" and add "acpi=off" to the end of those two lines.)

Success, of a sort. The system would boot into Ubuntu, and seemed to work, except that it wouldn't shut down. I had to go back on the road then, and took it as it was, since I didn't have time to do anything else.

Last weekend I spent at a truckstop in New York, where I was able to get internet access, so I took the time to install Kubuntu and some other packages, and play with the new version. Here are my conclusions:

**Pros:**
1: bluetooth works really, really well. In Ubuntu, it connects painlessly and almost instantly, and in Kubuntu it's not too bad. Best of all, it now remembers the keyboard and mouse between sessions, so I don't have to jump through hoops each time.

2: I like the basic access toolbar across the bottom of the screen at login. It provides a native virtual keyboard, so I don't have to hack /etc/gdm/Init/Default to get cellwriter, but that still works, too.

3: the native screen rotation via Settings --> Display works like a champ. Perfect rotation with no screen or cursor distortion.

**Cons:**
1: It is difficult to get it to boot, as I mentioned above.

2: stylus does not work, and bezel key function is limited. The esc and enter keys work, and page up/page down functions as line up/line down. As best I can tell, none of the other keys do anything, even with fjbtndrv installed. I did find out, though, that line up/line down and enter work at the boot menu screen, which was handy.

3: no working battery monitor, probably because I had to use acpi=off to get it to boot.

4: Amarok will not organize mp3s, but then again, Amarok has been iffy in regard for some time.

5: it's unstable. It will lock up solid if I try to shut down. It also instantly throws me out of my session and back to the login screen if I try to run just about any Kubuntu/KDE app, and sometimes just at random, as best I can tell.

**Conclusion:** On this system, at this time, 9.10 is unusable. I will also note that on my other system, a Dell Inspiron E1505, I ran a routine distribution update the first weekend I was home after 9.10's release, and it works fine there.

I have reinstalled 9.04 on the ST5010, since that's my on-the-road system and it has to work. I'm hoping that in 10.04 they fix whatever the problems are, because on the Dell, it looks pretty good.

---

### Post by Favux on 2009-12-13
Hi billklee,

Other serial Wacom tablet's have been reporting problems with the stylus in Karmic, esp. on 64-bit.  After the kernel and other updates on Friday one of them is telling me it fixed everything.  So that's only one system as yet, but...

Edit:  You might also want to try:
```
acpi_osi="Linux"
```
as a boot option rather than "acpi=off" and see if that gets you anywhere.

---

### Post by billklee on 2009-12-27
Having a long weekend at home, I decided to try the upgrade again. I got Karmic to work, sort of. 

First, I tried a distribution upgrade, but the system froze partway through. I have never been able to do a routine upgrade from 9.04 to 9.10, as it always freezes partway through.

However, I was also using the computer at the time, so I decided to give it one more go. This time, I sat it up next to another computer, so I could use that one while the ST5010 was upgrading, then I reinstalled 9.04 for the umpteenth time. I updated that installation, and added the packages necessary to get the tablet functions to run. Then I updated to the originally held-back packages, including, among other things, the 2.6.28-17 kernel and header packages.

Then I ran the upgrade again, reaching over every few minutes to bump the mouse, since it always seemed to freeze after a period of physical inaction on my part.

That actually worked, sort of. In an attempt to avoid the black screen at startup, I went ahead and edited /boot/grub/menu.lst to add acpi_osi="Linux", which didn't work. Neither did replacing it with acpi=off. However, if I hit esc to get into the grub boot menu, I could boot into the 2.6.28-11 kernel, and it'd boot, and the stylus and bezel buttons would work.

Yeah! Happy Dance! etc...

I then edited menu.lst to comment out both of the 2.6.28.17 kernel entries, and it successfully booted repeatedly. However, logging in was problematic. It'd usually boot into Ubuntu, almost never into Kubuntu, and occasionally into Xubuntu. No matter which one I managed to boot into, sooner or later it'd dump me back out to the login screen.

Having installed, reinstalled and upgraded at least four or five times a day for the last four days, with only one partially successful install, I give up from boredom and lack of time. I've reinstalled 9.04, and I'm leaving it there for now. When 10.4 comes out, I'm going to yank the current HD, put in the HD that came with the tablet and try installing it there. If it works, I'll try it on the new HD, and if it doesn't, the only time lost will be the time swapping HDs.

---

### Post by kathleenhenri on 2010-01-03
About a month ago I bought a Fujitsu Stylistic 5011D from ebay with the intent of using it as a reader and to stream Netflix films.  

Before that I had been experimenting with installing Jaunty on a Fujitsu u810. (Still a work in progress btw - everything on that is working well except for the keyboard lights and fingerprint reader). Well, of course, once I had the 5011D Tablet it was only a matter of minutes before I thought about installing Linux. At first I tried OpenSUSE 11.2 live but because I am more familiar with 'buntus I opted to go with Jaunty.  

After the challenges with getting things to work on the u810, I expected a similar road with the 5011D. But I ran ran across this thread and I have to say THANK YOU Billklee for pulling all this together! 

Much works out of the box, wireless, stylus, bluetooth - the only things didn't work were the screen rotation and the row of silver buttons along the bottom right bezel and calling up a keyboard to log-on with. I followed your how-to post #27 and all worked perfectly except for screen rotation. Oh, it would rotate, but then get all wonky and freeze up. But the final clue is in post #21 to disable compiz. Once I did that it runs flawlessly.

I now have a machine that will dual boot Windows (for Netflix and KindlePC) and Ubuntu for everything else.

---

### Post by billklee on 2010-01-03
Thank you, kathleenhenri, for those kind words. However, I have to repeat, all the credit goes to Favux. He's the one who's come up with just about everything I've used. All I did was pull together the stuff for the ST5010D and, it appears, the ST5011D.

Are you using Ubuntu? The reason I ask, is that I run Kubuntu, but always log into Ubuntu first, just to connect my bluetooth keyboard & mouse before logging out and back into Kubuntu. Why? Because getting them to connect in Kubuntu is a royal pain, whereas in Ubuntu it's fairly easy.

The problem I have is that when I log into Ubuntu, the display is in portrait mode, and the video is poor, to say the least. The video only covers the top 2/3 of the display, and the cursor is way, way off of where it appears to be.

If you are using Ubuntu, how does your display/video look?

---

### Post by billklee on 2010-01-03
This is a post I've been meaning to make ever since I got my ST5010D. I'm going to list off the accessories and upgrades I've got, and ask others for their suggestions.

1: more RAM. I got it with 1 GB of RAM (two 512 MB sticks) and I upgraded it to the max it'd take, 2 GB.

2: bigger HD. It came with a 60 GB drive, which I swapped out for a 160 GB drive. Note that 160 GB is too big for the ST5010D, which will give you a GRUB-18 error, if I recall correctly. This is the 'drive is too big' error, and it easily corrected by manually partitioning your drive during installation. Create a 100 MB /boot partition first, at the start of the drive, and it'll work just fine.

3: a slip-case. The ST5010D's proportions are a bit different than a normal laptop, and I thought I was going to have to order a case from Fujitsu. However, I found a [neoprene slip-case](http://www.goincase.com/products/detail/CL57286) at Best Buy from [Incase](http://www.goincase.com/) for the 13" MacBook that fits like a charm. When I bought it, it had a sheet of relatively stiff plastic foam inside, as a stiffener. I had another sheet of thin, stiff plastic left over from another project, which I glued to the foam sheet. This way, I can put this hard on one side/soft on the other side sheet in the case with the ST5010D (soft side toward the display, naturally) as a bit of added protection for the screen.

4: bluetooth. I bought a tiny bluetooth receiver that is small enough that I do not have to unplug it when I zip the slip-case closed. I also have a bluetooth keyboard and mouse that I use, when I can get the bluetooth to work.

5: USB. The ST5010D only has 2 USB ports. Use one for bluetooth or other wireless dongle, and you've got one left. I would suggest either a USB hub, or a USB adapter for the PCMCIA slot.

6: backup mouse. Until such time as you get bluetooth connected, all you've got is the stylus. In my case, the right-click and eraser functions of the stylus don't work. I find it easier to plug in a small wireless mouse and use that to connect the bluetooth, at which point I unplug it.

7: PCMCIA adapters. There is the USB adapter, which I mention above. Another possibility is the PCMCIA laptop fan, to keep the heat down.

Some of the official accessories:

[2 styluses (stylii?) - 2 @ $49.00](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCPN20AP&category=Input%20Devices&title=Replacement%20Stylus%20Set%20(Pack%20of%202)) for ST5010D & ST5011D, among others

[high-capacity battery @ $169.00](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCBP98AP&category=Batteries&title=High-capacity%20Main%20Lithium-ion%20battery) for ST5010D & ST5011D, among others

optionally, [www.batteryrefill.com](http://www.batteryrefill.com/laptops/fujitsu/stylistic5011d.phtml) offers refilled batteries for the ST5010D/5011D for $79.00 (requires sending your old battery in for an exchange) or $109.00 for an outright purchase. They note on their page for the ST5011D refill battery that the original battery is rated at 4500 mAh, that that their refills are 6600 mAh.

Fujitsu also offers the following:

A [hand strap](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCETC13&category=Carrying%20Cases&title=Hand%20Strap), $31.00, that fastens to the back of your ST5xxx tablet for easy handling.

An [easel case](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCCC49&category=Carrying%20Cases&title=Easel%20Case), $39.00, a double-duty carrying case and desktop standing easel for the ST5xxx.

The [Universal Bump Case](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCCC78&category=Carrying%20Cases&title=Universal%20ST5000%20Zipper%20Bump%20Case), to protect your tablet while allowing access to all controls and ports.

The [Executive Leather Portfolio](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCCC45&category=Carrying%20Cases&title=Executive%20Leather%20Portfolio), $75.00.

[Nylon Attache Case](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCCC46&category=Carrying%20Cases&title=Nylon%20Attache%20Case), $85.00

[Universal Harsh Environment Case](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCCC48&category=Carrying%20Cases&title=Universal%20Harsh%20Environment%20Case), $129.00 - does not fit ST5011D, according to that page.

Screen protectors [6-pack](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCSP08AP&category=Screen%20Protectors&title=Screen%20Protectors%20(6%20pack)) $39.00 - ST5011D is not listed as compatible

Screen protectors [12-pack](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCSP04AP&category=Screen%20Protectors&title=Screen%20Protector%20(12%20pack)), $69.00 - the ST5011d **is** listed as compatible with this package, so I'd assume the 6-pack of screen protectors are also compatible.

The [Universal Dock Mount](http://store.shopfujitsu.com/fpc/Ecommerce/SelectAccessoryDetail.jsp?partNumber=FPCPR46&category=Docking%20Options&title=Universal%20Dock%20Mount), $349.00, provides a desktop stand with the following extra ports: 3xUSB ports, external monitor port, LAN (RJ-45) port, aka ethernet, line out port and DC-input port. I find a wire-mesh document stand off of my desk, coupled with a USB hub out of my box of computer stuff works just as well.

[this page](http://store.shopfujitsu.com/fpc/Ecommerce/accstore.jsp) lists all of the official Fujitsu USA accessories.

To other people, what are your suggestions/recommendations/requirements?  What do you have, what do you use, or what do you think would be handy to use along with a tablet PC?

---

### Post by kathleenhenri on 2010-01-03
> **billklee said:**
> Thank you, kathleenhenri, for those kind words. However, I have to repeat, all the credit goes to Favux. He's the one who's come up with just about everything I've used. All I did was pull together the stuff for the ST5010D and, it appears, the ST5011D.

Are you using Ubuntu? The reason I ask, is that I run Kubuntu, but always log into Ubuntu first, just to connect my bluetooth keyboard & mouse before logging out and back into Kubuntu. Why? Because getting them to connect in Kubuntu is a royal pain, whereas in Ubuntu it's fairly easy.

The problem I have is that when I log into Ubuntu, the display is in portrait mode, and the video is poor, to say the least. The video only covers the top 2/3 of the display, and the cursor is way, way off of where it appears to be.

If you are using Ubuntu, how does your display/video look?


Thanks for clarifying. A big thanks to Favux!

I am running Ubuntu and I had a similar problem as in the one you describe above with screen rotation. What solved it is to go to Preferences--Appearance--Visual Effects and click on None. That's it. Screen rotation should now work fine and the display will fill the screen as it should and cursor will work as well. Disabling compiz effects seems to have taken care of it on my model.

---

### Post by billklee on 2010-01-03
One of the reasons I was disappointed by my inability to get 9.10 to reliably work on my tablet was the ease of bluetooth connection. Turn on the tablet, turn on the keyboard and mouse and wait. When the login screen popped up, wait about another 10 seconds and the keyboard and mouse would automatically connect. Of course, the first time I had to manually connect them after logging in, but after that, smooth sailing.

This is how I have to connect now, using 9.04.

Step 1: turn on the tablet, boot up and log in. While the tablet is booting, I turn on my keyboard and mouse. When it gets to the login screen, I use the stylus or my 'backup' wireless mouse to peck out my login information with cellwriter.

Step 2: log into Ubuntu, because it's a whole lot easier to connect bluetooth in Ubuntu. In fact, in Ubuntu, I can do it with my left-click-only stylus. In Kubuntu, I need a right-click, which is why I have the 'backup' wireless mouse.

Step 3: reset bluetooth. In Ubuntu, pull up a terminal and enter 'btr' (without the the quotes, of course. I have a script I created thusly:

```
sudo nano /bin/btr
```

with this as the body of the script:

```
#!/bin/bash
# reset bluetooth

sudo hciconfig hci0 reset
sudo hcitool dev
```

enter my password at the prompt. 

Step 4: connect keyboard and mouse. Go to Preferences --> Bluetooth. The keyboard and mouse should both be shown. Click on the mouse, under the connect icon, then click a mouse button. After a few seconds, the mouse is connected and usable. Do the same with the keyboard, and now they're both connected.

Step 5: Log out of Ubuntu, and into Kubuntu.

I'm having a bit of trouble, at present, Using Ubuntu. The display is poor, and the cursor is not lined up with where it actually clicks. Fortunately, I have a fix. Back when I started playing with this tablet, Favux pointed me at a screen rotation script that might be useful. I stopped using it when I got the bezel buttons to work, but kept it anyway.

This is the script:

```
#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the right 
    xrandr -o right 
# original line. uncomment to restore
    xsetwacom set stylus rotate  CW 
# commentiong out touch, since I don't have a touchscreen
#    xsetwacom set touch rotate CW 
    xsetwacom set eraser rotate CW  
    ;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set stylus rotate NONE 
# commentiong out touch, since I don't have a touchscreen
#    xsetwacom set touch rotate NONE 
    xsetwacom set eraser rotate NONE 
    ;; 
esac
```

I made a desktop launcher to this script, which I can select with the stylus or mouse, and launch by pressing the 'ent' bezel key. Once the display flips over to landscape, the display is good, and the cursor is actually pointing here it looks like it's pointing.

---

### Post by Tom Tiger on 2010-03-13
I haven't posted a for a while in this thread, for which I apologize.

Yesterday I tried to upgrade my 5021D to 9.10, this failed.... and failed big time... I could get it to work with the acpi=off code but no stylus at all.

Which was bad, since I use this system for learning CCNA...I read books on it and comics... it is PERFECT for this...

Fortunatly this time I was smart enough to make a backup. So I'll do a fresh install of 9.04 restore backup and done...  However I now had the possibility to try 10.04 (beta) and it won't work, it doesn't work on my 2100 Satellite, nor on the 5021D.  I will try Mepis next, but Mepis doesn't like it when it's root device is renamed, small problem, yet irritating...

My advice for now, stick to 9,04, everything works (allthough I don't recommend using compiz...) put at least 512 Mb in it (preferably if you got it 1 Gb) and use an extra harddisk for either backup or trying out an new distro.

Problem is I can't afford a new tablet right now...  but... the system runs again on 9.04, just need to restore my backup...

---

### Post by Tom Tiger on 2010-03-13
Update,

Everything works again, allways remember to TURN OFF compiz on 9.04 otherwise your display is very distorted in portrait mode :-)

All data is save, lost my bookmarks but I can export them from another system. 

phew... :-)  

I think I will have to save up for a nice tablet, but I also found another stick of 512 mb... so I can upgrade my tablet to 1 Gb.... can't do no more.

One small problem remaining..... my stylus doesn't do rotate, the screen rotates but the stylus will not... no idea how I fixed that the first time :-) LOL

---

### Post by andrew frank on 2011-01-04
i have a st5010D and installed ubuntu 10.10 and fjbtndrv -- all last updates jan 4, 2011.
bezel buttons work - partially:
[LIST]
[*]- alt  - prints alt on screen
[*]- mail - opens evolution
[*]- rotation : rotates the pointer clockwise a quarter (but not the screen -       pointer and stylus are initially in sync, after rotation only the pointer is moved 
[*]        repeat of button press has no effect. (i need to log off/on to correct)
[/LIST]

- up/down, home/end keys work ok.

before i do much more  - what am i missing? there is much information, but it varies for different versions of ubuntu/kubuntu. do i have to go to System -> Preferences -> Startup Applications. Click Add.
under "Command:", type: "/usr/bin/fujitsu_touchscreen_rotate.py". ?

help is appreciated!
andrew

---

### Post by andrew frank on 2011-01-04
i tried the touchscreen utilities as per instructions from
[http://katastrophos.net/andre/blog/2010/10/14/installing-ubuntu-10-10-maverick-meerkat-on-fujitsu-u820-u2010-u2020/comment-page-1/#comment-24546](http://katastrophos.net/andre/blog/2010/10/14/installing-ubuntu-10-10-maverick-meerkat-on-fujitsu-u820-u2010-u2020/comment-page-1/#comment-24546)

which uses 
Fujitsu usb touchscreen kernel module and utilities v0.3.8
by zmiq2 ,
updated for Ubuntu maverick (10.10) by nerd65536

the make runs ok, but install produces error messages -- i assume because the 5010 has a serial connection to wacom touchscreen (not usb as assumed in the utility). is there a version of the utility for serial connections available? is it difficult to adapt?

here my error message - in case my interpreation of the cause of the problem is wrong:


  * Starting loading fujitsu_usb_touchscreen module fujitsu_touchscreen          /etc/init.d/fujitsu_touchscreen: 102: /usr/bin/lshal: not found
Fujitsu touchscreen driver: ERROR [ERR1] - Device /org/freedesktop/Hal/devices/usb_device_430_530_noserial_if0 not found
                                                                         [fail]
if test ! -f /etc/hal/fdi/policy/fujitsu_usb_touchscreen.fdi; then /usr/bin/fujitsu_touchscreen_helper writecalibrate 124 266 3827 3940 ; fi
fujitsu_usb_touchscreen::error::parameter not available [/sys/module/fujitsu_usb_touchscreen/parameters/touch_minx]
fujitsu_usb_touchscreen::error::parameter not available [/sys/module/fujitsu_usb_touchscreen/parameters/touch_miny]
fujitsu_usb_touchscreen::error::parameter not available [/sys/module/fujitsu_usb_touchscreen/parameters/touch_maxx]
fujitsu_usb_touchscreen::error::parameter not available [/sys/module/fujitsu_usb_touchscreen/parameters/touch_maxy]
fujitsu_usb_touchscreen::error::cannot create file [/etc/hal/fdi/policy/fujitsu_usb_touchscreen.fdi]
ERROR: Module fujitsu_usb_touchscreen does not exist in /proc/modules

---

### Post by andrew frank on 2011-01-05
i uninstalled the fujitsu_usb_touchscreen by removing the file /etc/rc2.d/S99-fujitsu_usb_touchscreen. did produce errors in startup.

then i produced a xorg.conf by
typing X on the recovery terminal and then copying the file
cp /root/xorg.conf/new  /etc/X11/xorg.conf

in the xorg.conf i added a section for 

Section "Device"
	Identifier	"Configured Video Device"
	Option 		"RandRRotation" "On"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

which was in an automatically produced xorg.xonf in 9.04

now rotation works - except when rotated the display is shifted up (the stylus is ok, but not synced to the display). it seems that an origin for up/down in portrait mode is set wrong (left-right is ok).

i also experimented with the drivers from ppa:glasen as instructed here
[http://www.*****************/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html](http://www.*****************/driver/articles/how-to-enable-intel-graphics-driver-for-ubuntu-10-10.html)
but this gave me a display where the cursor acted as big eraser - folders vanished from the screen till it was completely blank. unusable (after rotation it was even worse).

-- 
problem left: how to map the display properly when rotated (it is ok upside down and when rotated back)

---

### Post by andrew frank on 2011-01-05
problem solved - somehow i got compiz activated.
after setting visual effects to NONE it all worked perfect.

seemingly under 10.10 only the activation of RRandR is necessary and the installation of jbtndrv. -- GREAT

---

