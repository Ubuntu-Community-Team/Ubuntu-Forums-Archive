---
title: "logitech mx1000, pls help."
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by saldie on 2005-12-25
Can someone help me configure my mouse so that the side, forward and back buttons work.
I tryed following this  thread,
[http://ubuntuforums.org/showthread.php?t=65471&highlight=Logitech](http://ubuntuforums.org/showthread.php?t=65471&highlight=Logitech)
with no luck.

---

### Post by AmboyGuy on 2005-12-25
clicking search and entering " Logitech mx1000 " turned up about a page and a half of threads that could help. Good luck in your search.

---

### Post by saldie on 2005-12-25
Thay is the one I posted.
Believe me I have searched here and googled the net to no avail.

---

### Post by AmboyGuy on 2005-12-25
Found this one: [http://ubuntuforums.org/showthread.php?t=28374]("http://ubuntuforums.org/showthread.php?t=28374")

Kinda glad I've got the old stupid mouse on my system.

---

### Post by audax321 on 2005-12-25
Well here are the steps to get your mouse buttons working (for side-scrolling in Firefox, you will need to follow the directions at [http://www.hopstudios.com/nep/unvarnished/item/scrolling_horizontally_with_firefox/](http://www.hopstudios.com/nep/unvarnished/item/scrolling_horizontally_with_firefox/) after you have it working ... but side scrolling in any other program should work).

Now, to get the buttons recognized you need to use evdev and will not need an xmodmap file. 

1. Open a terminal and type: cat /proc/bus/input/devices

  Keep this window handy, because you'll need it later.

2. Edit xorg.conf by opening another terminal: sudo nano /etc/X11/xorg.conf

3. Find the section marked as Section "InputDevice" that specifies your current mouse configuration and comment it out by placing the # symbol at the beginning of each line, so it looks something like this:

```

#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

```

4. Now, copy this section and paste it under the section you commented (I believe in the Terminal that comes with Gnome, paste is SHIFT+CNTRL+V)

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Dev Name"		"Logitech USB RECEIVER"
	Option		"Dev Phys"		"usb-0000:00:1d.0-1/input0"
	Option		"Device"		"/dev/input/mice"
	Option		"Buttons"		"12"
	Option		"Name"			"Logitech MX1000"
	Option		"Protocol"		"evdev"
	Option		"ZAxisMapping"		"4 5 7 6"
	Option		"Resolution"		"800"
EndSection

```

5. Now go back to the first terminal you opened and find the output that says something about Logitech USB RECEIVER and has some kind of mouse under the Handler listing (e.g. mouse0).

6. Make sure the Dev Phys and Dev Name here, exactly match the ones in xorg.conf, if not edit them. THEY MUST BE EXACT!!!

7. To save xorg.conf ... CNTRL+X and then press Y and enter to save.

8. Log out and then restart X by doing CNTRL+ALT+BACKSPACE... if X doesn't start again, the device information is wrong and you will have to edit xorg.conf again and uncomment the old input section and comment the new one you just wrote and try again (which is why I told you to use nano above instead of gedit :) )

Good luck.. btw, your side buttons will probably not do anything since they haven't been mapped to anything. To map them you will need to use xbindkeys (and possibly xvkbd) which is available in one of the repositories... might have been universe or multiverse (not sure).

Also, if you move your mouse receiver to a different USB port, X probably won't start because it is looking for your receiver at a different port (indicated by Dev Phys)... so plug it in a port you want to keep it at.

---

### Post by saldie on 2005-12-25
Thanks audax321, for the help, I entered the info and X restarted just fine.
Is there anyone who can tell me what to install and how to configure it so that my side buttons work.
Thanks again.

---

### Post by audax321 on 2005-12-25
To get the mouse buttons to work you need one or two things.

1. If you want to just assign commands to the buttons, then just use xbindkeys.

2. If you want to use the buttons for back/forward commands on a web browser, then install both xbindkeys and xvkbd (xvkbd just sends key presses to the currently active window, instead of running a command).

Both of these are available in either the universe or multiverse repositories.

To set it up, make a file called .xbindkeysrc in your home folder and add the following to it:

```

# INSTALL xvkbd AND THEN USE xbindkeys TO UTILIZE THIS FILE

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
   m:0x10 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]"" 
  m:0x10 + b:9
"firefox"
  m:0x10 + b:10

```

I don't have my MX1000 with me right now, but I think button 8 is back, button 9 is forward, and button 10 is circular button between them (you can verify this by running xev in a terminal and pushing them). Also "left" and "right" above should be "Left" and "Right", for some reason it is making the L and R lowercase.

Anyway the format of the file is basically:

```

"<command>"
  m:0x10 + b:<button number>

```

Finally, the path I have to xvkbd in the file above is: "/usr/X11R6/bin/xvkbd" but in the past this program could have just been added as "xvkbd", but for some reason it decided to install it in /usr/X11R6/bin. So try both if it doesn't work.

After the file is setup, open a terminal and type: xbindkeys

This will start the daemon... to start this when Gnome starts: System > Preferences > Sessions > Startup Programs > add xbindkeys in there.

---

### Post by saldie on 2005-12-26
Audax321, thank you sooo much for this.
Everything is working great in firefox and nautilus.
Thanks again.
:p

---

### Post by brj on 2005-12-27
audax321,

it looks like you are the specialist for logitech mouse issues :)

i'd like to simulate a double-click whenever i click the thumb-button or the scroll wheel (just the way i have it in winxp using the logitech-driver).

so far i was not able to successfully 'program' a double-click. may be you know some tricks ?

jakob

---

### Post by audax321 on 2005-12-27
It appears you need a program called mvmouse, but I can't get it to compile. Make exits with a lot of errors. There are some more details here:

[http://forums.suselinuxsupport.de/index.php?showtopic=23440&pid=133530&st=0&#entry133530](http://forums.suselinuxsupport.de/index.php?showtopic=23440&pid=133530&st=0&#entry133530)

EDIT: Anybody else know what could be wrong? This is the output I get from make:

```

gcc -c -Wall mvmouse.c -o mvmouse.o
mvmouse.c:19:22: error: X11/Xlib.h: No such file or directory
mvmouse.c:20:34: error: X11/extensions/XTest.h: No such file or directory
mvmouse.c: In function &#8216;main&#8217;:
mvmouse.c:32: error: &#8216;Display&#8217; undeclared (first use in this function)
mvmouse.c:32: error: (Each undeclared identifier is reported only once
mvmouse.c:32: error: for each function it appears in.)
mvmouse.c:32: error: &#8216;dpy&#8217; undeclared (first use in this function)
mvmouse.c:33: error: &#8216;Window&#8217; undeclared (first use in this function)
mvmouse.c:33: error: syntax error before &#8216;root&#8217;
mvmouse.c:43: warning: implicit declaration of function &#8216;strcmp&#8217;
mvmouse.c:69: warning: implicit declaration of function &#8216;XOpenDisplay&#8217;
mvmouse.c:73: error: &#8216;root&#8217; undeclared (first use in this function)
mvmouse.c:73: warning: implicit declaration of function &#8216;DefaultRootWindow&#8217;
mvmouse.c:78: warning: implicit declaration of function &#8216;strlen&#8217;
mvmouse.c:78: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
mvmouse.c:81: warning: implicit declaration of function &#8216;XWarpPointer&#8217;
mvmouse.c:81: error: &#8216;None&#8217; undeclared (first use in this function)
mvmouse.c:84: warning: implicit declaration of function &#8216;XTestFakeButtonEvent&#8217;
mvmouse.c:84: error: &#8216;True&#8217; undeclared (first use in this function)
mvmouse.c:85: error: &#8216;False&#8217; undeclared (first use in this function)
mvmouse.c:87: warning: implicit declaration of function &#8216;XCloseDisplay&#8217;
make: *** [mvmouse.o] Error 1

```

I can't find anything in Google with people having problems compiling this...

---

### Post by brj on 2005-12-27
thanks for your answer.

it's funny that such a simple thing is so complicated under linux :) :(

jakob

---

### Post by audax321 on 2005-12-27
I got it to compile!! Just needed some headers. Here are the packages to install to compile it:

libx11-dev
libxtst-dev


I'm going to try to use it now... I'll post back if it works... Never thought about setting up a mouse button for double clicking, but could be useful. :)

---

### Post by audax321 on 2005-12-27
Okay, its working great. Just when you create the double-click script you only need to put the mvmouse command in twice, not four times like he is in the forum link I gave you. So the script should look like this:

```

#!/bin/sh

# Script to emulate double-click using mvmouse

mvmouse +0 +0 1 && mvmouse +0 +0 1


```

And to uninstall mvmouse, all you have to do is remove /usr/bin/mvmouse

After you compile mvmouse to remove the headers you installed remove these packages:

```

libx11-dev
libxau-dev
libxext-dev
libxi-dev
libxtst-dev
x11proto-core-dev
x11proto-input-dev
x11proto-kb-dev
x11proto-record-dev
x11proto-xext-dev

```

Then just setup the xbindkeys file as I said before except the command would be the path to the script in quotes followed by the button your assigning to (you can get the button number using xev).

---

### Post by audax321 on 2006-01-09
I got a PM requesting that I upload the binary I compiled, so here it is. :)

mvmouse compiled on Ubuntu Breezy Badger:[ATTACH]5244[/ATTACH]

---

### Post by hanover.fiste on 2006-02-27
Compiles for me. Do you have the x-window-system-dev installed? That's needed to compile most X stuff.

---

