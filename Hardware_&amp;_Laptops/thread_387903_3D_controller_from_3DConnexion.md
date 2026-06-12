---
title: "3D controller from 3DConnexion?"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by tjod on 2007-03-18
Does anyone use the 3D controller from 3DConnexion? 

[http://www.3dconnexion.com/products/3a1d.php](http://www.3dconnexion.com/products/3a1d.php)

I'd love to figure out how to get it to work in Google Earth under Edgy. The company has Linux drivers but they are apparently set for Maya. 

If you haven't tried one of these gadgets, they are excellent to use with Google Earth (and a friend reports huge success with Maya in Windows...)  and are the final touch that really lets you fly effortlessly - very addictive and productive too. :) 

Tim O

---

### Post by futz on 2007-03-20
I just bought a SpaceNavigator the other day. It's WONDERFUL!!! What a great controller for 3D modelling, Google Earth, CAD, whatever... But for the time being it's a Windows controller only. 

I love using it with Google Earth and SketchUp.

There are Linux drivers, very recently released by 3Dconnexion, but no Linux software so far is able to use the controller (as far as I know). It will come eventually, I guess. If you're a bit of a hacker, you could probably make it work. Just have to somehow connect the driver to the controls you want diddled. :mrgreen:

From what I read at the 3Dconnexion forums, Blender is likely the first program that will get fixed up to work with the SpaceNavigator. Google will have to add some code to make Google Earth work with it (already does with the windows version).

---

### Post by maiatoday on 2007-08-23
I have the sturdy, blue-light-emitting, Space Navigator on my desk connected to UbuntuStudio and it is spinning the demo cube. :D

I installed the driver found at 3dconnexion site as per instructions but I ran the commands using sudo. The steps were copy the 3dxware-linux-v1-2-11.tgz to /tmp and copy/extract the  install-3dxunix.sh file into /tmp as well. Run the install script with sudo.  Then I had to install libmotif because it complained about libXm.so.3. Then I just ran the driver from the command line with sudo /etc/3DxWare/daemon/3dxsrv -d usb.

My next step is to get it going with blender. I downloaded a blender build from [http://www.blenderbuilds.com/](http://www.blenderbuilds.com/)
No joy yet, but working on it.-update- I unzipped the build, copied the 3DxNdofBlender.plugin folder to the plugin directory, double-clicked blender and I am flying, wheee! All as per the docs.

---

### Post by HessiaNerd on 2007-10-22
I was thinking about getting one of these.  Good to see there is some support for it.  

Now if there were only a FOSS Solidworks alternative.

I dont imagine it would be any different with KDE/kubuntu....?

would love to hear from others on their experiences with this.

---

### Post by arigram on 2007-10-31
I got one lately and it has become an important tool in my computer graphics work. Too bad its not very much supported across the system, even though the code is there for all to work with.
Its exactly like having a second mouse, one can even eliminate the keyboard in many cases, or cut down its use to a minimum. Any graphic artist can see the advantage of that.
In general its very much like playing a musical instrument: you use both hands. Imagine trying to play a guitar or piano with just one; possible, but you limit your music. Or for the gamers, like playing an FPS with just one hand...
The Navigator compliments the Mouse and they work at the same time.

I believe that its use could be well defined and embedded in many computer applications and it well become an important tool in one's computer experience, an input device as important as the mouse and the keyboard. Its analog sensitivity, many directions of movement and comfort of use are exactly what one needs to compliment the mouse.

Here's a list of ideas; applications it could have (and not even mentioning 3D apps):

**Desktop**
  Pan around the desktop, move around filenames, zoom in/out, switch viewports, control the cube, move and resize windows, control cursor in CLI/forms

**Word Processor/DTP**
  Move the cursor/object, zoom in/out, pan view/scroll page(s)

**Web Browser**
Pan view, zoom in/out, scroll through forms

**Image Viewer**
  Pan larger that screen/window image, zoom in/out, flip through images

**Photo/Graphics Editor (bitmap, vector)**
  Pan view, zoom in/out, move/scale/transform object, control amount of transformation/filter/etc

**Music/Video Player**
Start/Pause/Stop Buttons, Next/Previous track/video, move position in track/video, control volume

**Video Editor**
Editing controls

**Games **
Control movement of character (instead of AWSD in FPS), control weapons, pan view, zoom in/out (analog movement in FPS, natural control for arcade/puzzle games, view and control at the same time in RTS, move character and aim their weapons in RTS and RPG, etc)

etc, etc...

The possibilities are endless, the code is out there, it is an important input device, so it HAS to be supported.

---

### Post by FractalBrain on 2007-12-03
Hey all,
I just wanted to show my support for wanting more development of the spacenavigator in linux!  I think I am going to get one of these for my CAD work in windows, but like the others, I see this could have great potential for so much more!  Yeah, I really want to see this implemented system-wide (ie. scroll horiz/vert, zoom in/out, and all the rest that was mentioned).  It seems like it could really help speed up mundane tasks and take some of the stress of the other hand.
Thats good motivation for becoming a developer...hmm, perhaps I should graduate first. -Fractal

---

### Post by arigram on 2007-12-05
A new Open Source driver for the devices has been built and is available from:
[http://spacenav.sourceforge.net/](http://spacenav.sourceforge.net/)

Apart from freeing the device from its proprietary device chains, it can now be easily
used in Debian distros such as Ubuntu.

Now, we only need more support for it!

---

### Post by Keith_Beef on 2008-01-07
My SpaceNavigator arrived tonight.

I'm trying to get it working in Gimp, and don't understand well enough how to set up an extra input device. I am getting somewhere, without the need for proprietary drivers or utilities, but I'd like some help.

There is a small problem with permissions on the device file, I think,that means I can only see anything happening if I run Gimp as root... but I'll come back to that another day.

For now, I can start gimp as root in a terminal window.
```
$ sudo gimp
[sudo] password for spacecadet:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Now, I go to File->Preferences and the dialog appears.

I select Input Devices -> Input Controllers and I see two panes.

I select Linux Input in the left pane, and select the right arrow to move this into the list of Active Controllers.

Now, the Configure Input Controller dialog appears.

Here, I check the box Dump events from this controller and in the Device list I select 3Dconnexion SpaceNavigator.

Now, in the terminal I see:

```
linux_input_get_device_info: #keys = 0
linux_input_get_device_info: #ext_keys = 0
linux_input_get_device_info: button 0x100 present
linux_input_get_device_info: button 0x101 present
linux_input_get_device_info: #buttons = 2
linux_input_get_device_info: rel 0x00 present
linux_input_get_device_info: rel 0x01 present
linux_input_get_device_info: rel 0x02 present
linux_input_get_device_info: rel 0x03 present
linux_input_get_device_info: rel 0x04 present
linux_input_get_device_info: rel 0x05 present
linux_input_get_device_info: #rels = 6
linux_input_read_event: EV_REL code = 0x04 (value = -2)
```

This looks promising!

Now, I move the controller while watching the terminal window, and I see plenty of events:

```
linux_input_read_event: EV_REL code = 0x04 (value = -24)
linux_input_read_event: EV_REL code = 0x00 (value = 9)
linux_input_read_event: EV_REL code = 0x03 (value = -5)
linux_input_read_event: EV_REL code = 0x04 (value = -21)
linux_input_read_event: EV_REL code = 0x00 (value = 4)
linux_input_read_event: EV_REL code = 0x03 (value = -3)
linux_input_read_event: EV_REL code = 0x04 (value = -19)
linux_input_read_event: EV_REL code = 0x03 (value = -1)
linux_input_read_event: EV_REL code = 0x04 (value = -11)
linux_input_read_event: EV_REL code = 0x04 (value = -3)
linux_input_read_event: EV_REL code = 0x01 (value = 4)
linux_input_read_event: EV_REL code = 0x00 (value = 1)
linux_input_read_event: EV_REL code = 0x01 (value = 23)
linux_input_read_event: EV_REL code = 0x00 (value = 8)
linux_input_read_event: EV_REL code = 0x01 (value = 32)
linux_input_read_event: EV_REL code = 0x03 (value = 17)
linux_input_read_event: EV_REL code = 0x04 (value = -2)
linux_input_read_event: EV_REL code = 0x00 (value = 10)
linux_input_read_event: EV_REL code = 0x01 (value = 43)
linux_input_read_event: EV_REL code = 0x03 (value = 43)
linux_input_read_event: EV_REL code = 0x04 (value = -4)
linux_input_read_event: EV_REL code = 0x00 (value = 14)
linux_input_read_event: EV_REL code = 0x01 (value = 47)
linux_input_read_event: EV_REL code = 0x02 (value = -6)
linux_input_read_event: EV_REL code = 0x03 (value = 61)
linux_input_read_event: EV_REL code = 0x04 (value = -10)
linux_input_read_event: EV_REL code = 0x00 (value = 5)
linux_input_read_event: EV_REL code = 0x01 (value = 34)
linux_input_read_event: EV_REL code = 0x02 (value = -5)
linux_input_read_event: EV_REL code = 0x03 (value = 54)
linux_input_read_event: EV_REL code = 0x04 (value = -7)
linux_input_read_event: EV_REL code = 0x01 (value = 7)
linux_input_read_event: EV_REL code = 0x03 (value = 11)
linux_input_read_event: EV_REL code = 0x02 (value = 25)
linux_input_read_event: EV_REL code = 0x02 (value = 36)
linux_input_read_event: EV_REL code = 0x03 (value = -22)
linux_input_read_event: EV_REL code = 0x02 (value = 69)
linux_input_read_event: EV_REL code = 0x03 (value = -20)
linux_input_read_event: EV_REL code = 0x04 (value = 8)
linux_input_read_event: EV_REL code = 0x02 (value = 69)
linux_input_read_event: EV_REL code = 0x03 (value = -16)
linux_input_read_event: EV_REL code = 0x04 (value = 5)
linux_input_read_event: EV_REL code = 0x02 (value = 59)
linux_input_read_event: EV_REL code = 0x03 (value = -10)
linux_input_read_event: EV_REL code = 0x04 (value = 5)
linux_input_read_event: EV_REL code = 0x02 (value = 34)
linux_input_read_event: EV_REL code = 0x04 (value = 3)
linux_input_read_event: EV_REL code = 0x02 (value = 4)
```

Ausgezeichnet!

So, I try to map an event to an action in Gimp, but how can I know which event in the gimp window corresponds to the event in the terminal?

For example, when I rotate the controller anticlockwise, I see this:

```
linux_input_read_event: EV_REL code = 0x05 (value = -16)
```

Now by trial and error, I find that I can create these mappings in the Gimp's Configure Input Controller dialog:
Z Axis Turn Left     view-zoom-out
Z Axis Turn Right    view-zoom-in

And the zoom-in and zoom out work! Joy!

Also, I can configure other axes to trigger scroll left or right, and scroll up or down, so I can pan a viewport around within a very large image.

But two problems remain:
[LIST=1]
[*]the sensitivity is too high! I turn a little and the view zooms far too much, or the viewport pans far too fast!
[*]how can I find a list of the events for this controller, with a match to a physical movement?
[/LIST]



Beef.

---

### Post by Keith_Beef on 2008-01-17
> **arigram said:**
> A new Open Source driver for the devices has been built and is available from:
[http://spacenav.sourceforge.net/](http://spacenav.sourceforge.net/)

Apart from freeing the device from its proprietary device chains, it can now be easily
used in Debian distros such as Ubuntu.

Now, we only need more support for it!

Have you succeeded in compiling the two sets of code? Neither spacenavd nor libspnav would compile for me.

I unzipped the archives to /usr/src and followed the instructions (very, very simple!) to the letter.

```
/usr/src/spacenavd-0.1$ sudo make
gcc -pedantic -Wall -g -DUSE_X11   -c -o spnavd.o spnavd.c
spnavd.c:49:22: error: X11/Xlib.h: No such file or directory
spnavd.c:50:23: error: X11/Xutil.h: No such file or directory
spnavd.c:67: error: expected specifier-qualifier-list before ‘Window’
spnavd.c:88: error: expected ‘)’ before ‘*’ token
spnavd.c:89: error: expected ‘)’ before ‘win’
spnavd.c:90: error: expected ‘)’ before ‘win’
spnavd.c:113: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
spnavd.c:114: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘win’
spnavd.c:115: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘event_motion’
spnavd.c: In function ‘main’:
spnavd.c:170: error: ‘struct client’ has no member named ‘next’
spnavd.c: In function ‘select_all’:
spnavd.c:259: error: ‘struct client’ has no member named ‘next’
spnavd.c:269: error: ‘struct client’ has no member named ‘next’
spnavd.c:275: error: ‘dpy’ undeclared (first use in this function)
spnavd.c:275: error: (Each undeclared identifier is reported only once
spnavd.c:275: error: for each function it appears in.)
spnavd.c:276: warning: implicit declaration of function ‘ConnectionNumber’
spnavd.c: In function ‘handle_events’:
spnavd.c:318: error: ‘struct client’ has no member named ‘next’
spnavd.c:319: error: ‘struct client’ has no member named ‘next’
spnavd.c:326: error: ‘struct client’ has no member named ‘sens’
spnavd.c:326: error: ‘struct client’ has no member named ‘sens’
spnavd.c:328: error: ‘struct client’ has no member named ‘next’
spnavd.c:328: error: ‘struct client’ has no member named ‘next’
spnavd.c:336: error: ‘struct client’ has no member named ‘next’
spnavd.c:336: error: ‘struct client’ has no member named ‘next’
spnavd.c:341: error: ‘struct client’ has no member named ‘next’
spnavd.c:346: error: ‘dpy’ undeclared (first use in this function)
spnavd.c:350: warning: implicit declaration of function ‘XPending’
spnavd.c:351: error: ‘XEvent’ undeclared (first use in this function)
spnavd.c:351: error: expected ‘;’ before ‘xev’
spnavd.c:352: warning: implicit declaration of function ‘XNextEvent’
spnavd.c:352: error: ‘xev’ undeclared (first use in this function)
spnavd.c:354: error: ‘ClientMessage’ undeclared (first use in this function)
spnavd.c:354: error: ‘event_cmd’ undeclared (first use in this function)
spnavd.c:362: warning: implicit declaration of function ‘set_client_window’
spnavd.c:362: error: ‘Window’ undeclared (first use in this function)
spnavd.c:362: error: expected ‘)’ before ‘win_id’
spnavd.c: In function ‘add_client’:
spnavd.c:483: error: ‘struct client’ has no member named ‘win’
spnavd.c:483: error: ‘Window’ undeclared (first use in this function)
spnavd.c:483: error: expected expression before ‘)’ token
spnavd.c:487: error: ‘struct client’ has no member named ‘sens’
spnavd.c:488: error: ‘struct client’ has no member named ‘next’
spnavd.c:488: error: ‘struct client’ has no member named ‘next’
spnavd.c:489: error: ‘struct client’ has no member named ‘next’
spnavd.c: In function ‘send_uevent’:
spnavd.c:572: error: ‘struct client’ has no member named ‘next’
spnavd.c:581: error: ‘struct client’ has no member named ‘sens’
spnavd.c:601: error: ‘struct client’ has no member named ‘next’
spnavd.c: In function ‘init_x11’:
spnavd.c:610: error: ‘Window’ undeclared (first use in this function)
spnavd.c:610: error: expected ‘;’ before ‘root’
spnavd.c:611: error: ‘XSetWindowAttributes’ undeclared (first use in this function)
spnavd.c:611: error: expected ‘;’ before ‘xattr’
spnavd.c:612: error: ‘Atom’ undeclared (first use in this function)
spnavd.c:612: error: expected ‘;’ before ‘wm_delete’
spnavd.c:613: error: ‘XTextProperty’ undeclared (first use in this function)
spnavd.c:613: error: expected ‘;’ before ‘tp_wname’
spnavd.c:614: error: ‘XClassHint’ undeclared (first use in this function)
spnavd.c:614: error: expected ‘;’ before ‘class_hint’
spnavd.c:615: warning: ISO C90 forbids mixed declarations and code
spnavd.c:617: error: ‘dpy’ undeclared (first use in this function)
spnavd.c:619: warning: implicit declaration of function ‘XOpenDisplay’
spnavd.c:623: warning: implicit declaration of function ‘ScreenCount’
spnavd.c:624: warning: implicit declaration of function ‘DefaultScreen’
spnavd.c:625: error: ‘root’ undeclared (first use in this function)
spnavd.c:625: warning: implicit declaration of function ‘RootWindow’
spnavd.c:628: error: ‘event_motion’ undeclared (first use in this function)
spnavd.c:628: warning: implicit declaration of function ‘XInternAtom’
spnavd.c:628: error: ‘False’ undeclared (first use in this function)
spnavd.c:629: error: ‘event_bpress’ undeclared (first use in this function)
spnavd.c:630: error: ‘event_brelease’ undeclared (first use in this function)
spnavd.c:631: error: ‘event_cmd’ undeclared (first use in this function)
spnavd.c:636: error: ‘xattr’ undeclared (first use in this function)
spnavd.c:636: warning: implicit declaration of function ‘BlackPixel’
spnavd.c:637: warning: implicit declaration of function ‘DefaultColormap’
spnavd.c:639: error: ‘win’ undeclared (first use in this function)
spnavd.c:639: warning: implicit declaration of function ‘XCreateWindow’
spnavd.c:639: error: ‘CopyFromParent’ undeclared (first use in this function)
spnavd.c:639: error: ‘InputOutput’ undeclared (first use in this function)
spnavd.c:640: warning: implicit declaration of function ‘DefaultVisual’
spnavd.c:640: error: ‘CWColormap’ undeclared (first use in this function)
spnavd.c:640: error: ‘CWBackPixel’ undeclared (first use in this function)
spnavd.c:640: error: ‘CWBorderPixel’ undeclared (first use in this function)
spnavd.c:642: error: ‘wm_delete’ undeclared (first use in this function)
spnavd.c:643: warning: implicit declaration of function ‘XSetWMProtocols’
spnavd.c:645: warning: implicit declaration of function ‘XStringListToTextProperty’
spnavd.c:645: error: ‘tp_wname’ undeclared (first use in this function)
spnavd.c:646: warning: implicit declaration of function ‘XSetWMName’
spnavd.c:647: warning: implicit declaration of function ‘XFree’
spnavd.c:649: error: ‘class_hint’ undeclared (first use in this function)
spnavd.c:651: warning: implicit declaration of function ‘XSetClassHint’
spnavd.c:657: error: ‘cmd_type’ undeclared (first use in this function)
spnavd.c:659: error: expected ‘;’ before ‘root’
spnavd.c:660: warning: implicit declaration of function ‘XChangeProperty’
spnavd.c:660: error: ‘PropModeReplace’ undeclared (first use in this function)
spnavd.c:662: warning: implicit declaration of function ‘XFlush’
spnavd.c: In function ‘close_x11’:
spnavd.c:671: error: ‘dpy’ undeclared (first use in this function)
spnavd.c:676: error: ‘Window’ undeclared (first use in this function)
spnavd.c:676: error: expected ‘;’ before ‘root’
spnavd.c:677: warning: implicit declaration of function ‘XDeleteProperty’
spnavd.c:677: error: ‘root’ undeclared (first use in this function)
spnavd.c:677: error: ‘event_cmd’ undeclared (first use in this function)
spnavd.c:680: warning: implicit declaration of function ‘XDestroyWindow’
spnavd.c:680: error: ‘win’ undeclared (first use in this function)
spnavd.c:681: warning: implicit declaration of function ‘XCloseDisplay’
spnavd.c: In function ‘send_xevent’:
spnavd.c:689: error: expected ‘)’ before ‘*’ token
spnavd.c:691: error: ‘XEvent’ undeclared (first use in this function)
spnavd.c:691: error: expected ‘;’ before ‘xevent’
spnavd.c:692: warning: ISO C90 forbids mixed declarations and code
spnavd.c:694: error: ‘dpy’ undeclared (first use in this function)
spnavd.c:707: error: ‘prev_xerr_handler’ undeclared (first use in this function)
spnavd.c:707: warning: implicit declaration of function ‘XSetErrorHandler’
spnavd.c:707: error: ‘catch_badwin’ undeclared (first use in this function)
spnavd.c:709: error: ‘xevent’ undeclared (first use in this function)
spnavd.c:709: error: ‘ClientMessage’ undeclared (first use in this function)
spnavd.c:710: error: ‘False’ undeclared (first use in this function)
spnavd.c:713: error: ‘struct client’ has no member named ‘next’
spnavd.c:716: error: ‘struct client’ has no member named ‘next’
spnavd.c:720: error: ‘struct client’ has no member named ‘win’
spnavd.c:724: error: ‘event_motion’ undeclared (first use in this function)
spnavd.c:736: error: ‘event_bpress’ undeclared (first use in this function)
spnavd.c:736: error: ‘event_brelease’ undeclared (first use in this function)
spnavd.c:746: warning: implicit declaration of function ‘XSendEvent’
spnavd.c:746: error: ‘struct client’ has no member named ‘win’
spnavd.c:747: error: ‘struct client’ has no member named ‘next’
spnavd.c:750: warning: implicit declaration of function ‘XSync’
spnavd.c: At top level:
spnavd.c:755: error: expected ‘)’ before ‘*’ token
spnavd.c:770: error: expected ‘)’ before ‘win’
spnavd.c:798: error: expected ‘)’ before ‘win’
make: *** [spnavd.o] Error 1
```


So, I suppose I need to install libX11-dev...

Now things work much better!
```
$ sudo make
gcc -pedantic -Wall -g -DUSE_X11   -c -o spnavd.o spnavd.c
gcc -pedantic -Wall -g -DUSE_X11 -o spacenavd spnavd.o -lX11

$ make install
make: *** No rule to make target `install'.  Stop.


$ cd ../libspnav-0.1/
$ sudo ./configure 
[sudo] password for klrhodes:
configuring spacenav library...
  prefix: /usr/local
  optimize for speed: yes
  include debugging symbols: yes
  x11 communication method: yes

creating makefile ...
creating spnav_config.h ...

Done. You can now type make (or gmake) to compile libspnav.

$ make
gcc -O3 -g -std=c89 -fpic -pedantic -Wall -Wno-strict-aliasing -g -I.   -c -o spnav.o spnav.c
gcc -O3 -g -std=c89 -fpic -pedantic -Wall -Wno-strict-aliasing -g -I.   -c -o spnav_magellan.o spnav_magellan.c
ar rcs libspnav.a spnav.o spnav_magellan.o
gcc -O3 -g -std=c89 -fpic -pedantic -Wall -Wno-strict-aliasing -g -I. -shared -o libspnav.so spnav.o spnav_magellan.o

$ sudo make install
cp libspnav.a /usr/local/lib/libspnav.a
cp libspnav.so /usr/local/lib/libspnav.so
cp spnav.h spnav_magellan.h spnav_config.h /usr/local/include/
```

So good so far... I hope that this will be of some use.

Beef.

---

### Post by gali98 on 2008-02-29
Okay So I also have the great SpaceNavigator. I have a quick question. What can I even do with this open souce driver? I compiled it, butI can't really see what to do. Later, hopefully tomorrow I will post again with some stuff that may help us get it working better, but I'm going to bed now..... :)
Kory

---

### Post by Silkesdad on 2008-04-05
The proprietaty driver from 3Dconnexion comes with a testing program called xcube.

It's just a small cube on your screen that you can controle with your 3D mouse.

Those who want is, can e-mail me and I will send it to you

(Or you can compile the driver from 3Dconnection and you can find it in /tmp)

There should be a script that makes the 3D-mouse work in gimp. I'll post it if I've got it working...

---

### Post by nikogawa on 2008-04-05
Hello,

I'm also the owner of a Spacenavigator and I would like to use it to scroll  in firefox, ... And mapping buttons would als be nice.

I think the easiest way is to use the evdev driver. I can get it to work as a mouse with the following code in my xorg.conf.

```

Section "ServerLayout"
...
	InputDevice    "spaceball"   "SendCoreEvents"
EndSection

...

Section "InputDevice"
	Identifier  "spaceball"
	Driver      "evdev"
	Option      "Name" "3Dconnexion SpaceNavigator"
	Option      "Pass" "3"
	Option      "ZRelativeAxisButtons" "Off"
EndSection 

```

Of course it's not very useful as a mouse. When you delete "SendCoreEvents" it actually doesn't do anything. So if somebody would know a way to configure the evdev driver so i could use it to pan (scroll vertical and horizontal), that would be very nice.

here is the output for "xidump spaceball-usb-0000:00:1d.7-4.1/input0", maybe this is useful. The ouput for the axes seem to be relative and incremental. The two buttons are 17-UP and 18-DOWN.
```

InputDevice: spaceball-usb-0000:00:1d.7-4.1/input0
Valuators: Relative   ID:     65535  Serial Number:       -65536

             x-axis    y-axis   pressure  rotation  throttle    wheel
     data:  -06475    -35011    +13564    -08738    -00376    +00555
      min:  +00000    +00000    +00000    +00000    +00000    +00000
      max:  +01279    +00799    -00001    -00001    -00001    -00001
      res:  +00000    +00000    +00000    +00000    +00000    +00000

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
    Focus:
  Buttons:                                                    17-UP  
     Keys:

```

And here is the output for "cat /proc/bus/input/devices".
```

I: Bus=0003 Vendor=046d Product=c626 Version=0110
N: Name="3Dconnexion SpaceNavigator"
P: Phys=usb-0000:00:1d.7-4.1/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=20007
B: KEY=3 0 0 0 0 0 0 0 0
B: REL=3f
B: LED=100

```


BTW
[LIST]
[*]In the Gimp it works without any driver through this guide: [http://www.3dconnexion.com/forum/viewtopic.php?t=1917]("http://www.3dconnexion.com/forum/viewtopic.php?t=1917")
[*]The opensource driver seems to work for the xcube demo, and it doesn't interfere with Gimp. But this driver doesn't work in Pro/Engineer. So I always have to start the proprietary driver for that.
[/LIST]

---

### Post by Silkesdad on 2008-04-06
> **nikogawa said:**
> ...
I think the easiest way is to use the evdev driver. I can get it to work as a mouse with the following code in my xorg.conf.

```

Section "ServerLayout"
...
	InputDevice    "spaceball"   "SendCoreEvents"
EndSection

...

Section "InputDevice"
	Identifier  "spaceball"
	Driver      "evdev"
	Option      "Name" "3Dconnexion SpaceNavigator"
	Option      "Pass" "3"
	Option      "ZRelativeAxisButtons" "Off"
EndSection 

```
...
[*]In the Gimp it works without any driver through this guide: [http://www.3dconnexion.com/forum/viewtopic.php?t=1917]("http://www.3dconnexion.com/forum/viewtopic.php?t=1917")
[*]The opensource driver seems to work for the xcube demo, and it doesn't interfere with Gimp. But this driver doesn't work in Pro/Engineer. So I always have to start the proprietary driver for that.
[/LIST]

Strange, it seems that for everybody the evdev driver works but not for me :( I can't figure out why. I use the same lines in the xorg.conf...

---

### Post by tomjennings on 2008-04-09
I have one, like an idiot I bought it hoping for later linux support for googleearth (my only interest for this controller) but that ain't happening.

BUT! if spacenavigator could merely be mapped as a HIB device (keyboard) then if it generated the keyboard nav codes, googleearth would work without explicit support. 

I don't know where to start here. I'd do the grunt work of making spacenavigator->keyboardkeys if someone knows how to coerce the USB system to plug spacenavigator in as a "keyboard".

Beats no support at all.

---

### Post by not_surt on 2008-05-09
I've just got me a SpaceNavigator PE, and it's working fine with the proprietary driver if I manually launch it as super user, but the autostart (which I would find infinitely more desirable) as setup by the install script isn't working.

The line in /etc/inittab is the following:
```
3d:2345:respawn:/etc/3DxWare/daemon/3dxsrv -d usb </dev/null >/dev/null 2>&1
```

Any ideas how to get it working as intended?

---

### Post by Keith_Beef on 2008-05-09
I've had no time to spend on this lately. :( But with what little time I could get for myself, I found mention of other people using evdev and btnx to send events from other input devices, like the Logitech G7 mouse with lots of extra buttons.

[http://ubuntuforums.org/showpost.php?p=1413357&postcount=17](http://ubuntuforums.org/showpost.php?p=1413357&postcount=17)
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

Maybe these could be used to turn a physical movement of the SpaceNavigator into an X event, then map this to a control for, e.g., GIMP.

K

---

### Post by not_surt on 2008-05-10
Found the solution to my startup problem here: [http://www.3dconnexion.com/forum/viewtopic.php?p=7108#7108]("http://www.3dconnexion.com/forum/viewtopic.php?p=7108#7108")

---

### Post by arigram on 2008-07-05
Christian from 3Dconnexion has a proposal to get the Navigator working as a buttonless mouse:

> Hi,

you can control the mouse cursor with our 3D mice, but you'll lack the mouse buttons. This seems to be a limitation of the evdev driver (regarding to its documentation), which just processes buttons that are declared as mouse buttons (via the device firmware). The buttons of our 3D mice aren't declared this way.

For those who still want to try controlling the mouse cursor, please open the xorg.conf and add the following lines in
Section "ServerLayout":
Code:

InputDevice  "3DMouse" "CorePointer"


and create a new InputDevice section for "3DMouse:
Code:

Section "InputDevice"
    Identifier    "3DMouse"
    Driver    "evdev"
    Option    "Name" "3Dconnexion *"
    Option    "Pass" "3"
    Option    "Mode" "Relative"
EndSection


Now kill and/or restart your XServer with <CTRL><ALT><BACKSPACE> or init 4/init 5 (e.g. Fedora). If you have your SpaceNavigator connected you can now control the mouse cursor.


Regards,

Christian
3Dconnexion

Now, the million dollar questions:
- How can one access the buttons to be able to use them in Compiz and Nautilus?
- Can we get Navigator working with Compiz as a separate controller (to rotate the cube for example)?

---

### Post by jaygo on 2008-07-08
Using the stock driver and GUI config, I was able to map the buttons to keys listed in the drop-down lists under button mapping -- I tested "esc" & "control + alt" successfully. However, the config kept returning the binds to default. I was able to set & save key combos and assign them to the buttons *but* they wouldn't work. Neither would the built-in combos listed as "Custom #". Anyway, it's a start.

What I'm hoping is to find some practical method of button or axis-mapping so that I can make this paperweight useful in Wine/Sketchup.

For what it's worth, I took a long-shot and installed the win driver in wine. Sketchup picked up the plugin but can't see it at all. There's probably an advanced way of hacking your USB devices into Wine accessibility, but that's a ways off for me.

The spacenav & lib6dof projects look very promising but they'll probably be a while yet. Looks like best bets are to simply avoid it unless you use Maya, Blender, or want to wait for something else.

---

### Post by arigram on 2008-07-09
The new hack in Compiz to include the multiple controller support of X (XI2) might just be the ticket for real support of the Navigator.

From Phoronix:
> In May we shared that Multi-Pointer X (or MPX for short) was entering the mainline X server. While it was merged to master that month, X Server 1.5 was already branched out and therefore it won't appear in X.Org 7.4, but it will appear in X Server 1.6 (X.Org 7.5) until next year.

While it's now in the mainline branch, Peter Hutterer, the chief developer of MPX, hasn't stopped there. One of his most recent accomplishments was modifying Compiz to support Multi-Point X. In his personal git repository, he now has a custom version that does support multiple inputs and multiple events occurring simultaneously while still enjoying the wobbly windows and other desktop effects presented by this window manager. To do this, Peter had to rewrite portions of the Compiz Core to support XI2 (X Input 2) by replacing some functions and listening to X Input events instead of internal Compiz core events. Additional work was then also required to support the Compiz plug-ins on MPX.

In a blog post by Peter explaining this Compiz+MPX work, he mentions that many details are left in an unfinished state. Unfortunately, due to time commitments, he won't be continuing this work with an MPX-aware XI2-supportive version of Compiz. Perhaps someone will step up to the plate and finish it off and down the road be able to merge it into the mainline Compiz.

In:
[http://smspillaz.wordpress.com/2008/07/09/compiz-fusion-community-news-for-july-9-2008-the-usual-shipment-of-eye-candy-and-functionality/](http://smspillaz.wordpress.com/2008/07/09/compiz-fusion-community-news-for-july-9-2008-the-usual-shipment-of-eye-candy-and-functionality/)
Scroll down to "Experimental tests with INPUT REDIRECTION in Freewins."
and watch the video.

---

### Post by jaygo on 2008-07-12
that would be nice. One more excuse to run compiz >8]

---

### Post by galland on 2008-07-22
Hello,

I'm responsible of a unofficial package for the official 3DxWare driver.
You could get it from [www.arakhne.org](www.arakhne.org).

Features:
a) A specific daemon which launch the 3DxWare daemon on demand; from a gnome applet or application menu.
b) A C++ library that permits to simplify the use of the Space Mouses.
c) A Java Native Wrapper for Java applications (only for Linux).

Feedbacks are welcome :)

Stéphane

---

### Post by secundar on 2008-07-23
> **galland said:**
> Hello,

I'm responsible of a unofficial package for the official 3DxWare driver.
You could get it from [www.arakhne.org](www.arakhne.org).

Features:
a) A specific daemon which launch the 3DxWare daemon on demand; from a gnome applet or application menu.
b) A C++ library that permits to simplify the use of the Space Mouses.
c) A Java Native Wrapper for Java applications (only for Linux).

Feedbacks are welcome :)

Stéphane

Thank you! I tried adding the repo but got an error when reloading: 
```
Failed to fetch http://download.tuxfamily.org/arakhne/ubuntu/dists/hardy-arakhne/Release  Unable to find expected entry  universe/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

But I downloaded the debs from the package pool and all is well... so far. Now to config for my apps.

---

