---
title: "Set up a LG C1 tablet in Karmic"
date: 2010-01-02
forum: Hardware
---

### Post by vespagts on 2010-01-02
Please help me!

I can't get my LG C1 touchscreen to work under Karmic! I've tried to set it up as a wacom tablet as in this thread
[http://ubuntuforums.org/showthread.php?p=6546012&mode=linear#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012&mode=linear#post6546012")

and then as a Fujitsu touch screen, recompiling kernel with 8250 and 8250_pnp as modules, installing fujitouch driver and editing xorg.conf to add touchscreen on /dev/ttyS4 with sendcorevent option... nothing to do...

now I've zapped it all and made a fresh re-installation of Karmic (netbook remix); in the attached zip there are dmesg, hwlist, lshal, lsmod, syslog and xinput of the new installed Karmic

help me please!

---

### Post by Favux on 2010-01-03
Hi vespagts,

I found your old thread:  [http://ubuntuforums.org/showthread.php?t=441723](http://ubuntuforums.org/showthread.php?t=441723)

From your lshal I believe these are your tablet sections:
```
udi = '/org/freedesktop/Hal/devices/pnp_LTS0001'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (LTS0001)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_LTS0001'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02'  (string)
  pnp.id = 'LTS0001'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_LTS0001_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_LTS0001'  (string)
  info.product = 'PnP Device (LTS0001)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_LTS0001_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:02/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_LTS0001'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
```
Interestingly the touchscreen might be supported by linuxwacom as the "FUJ02E6" because:  [http://gitorious.org/opensuse/kernel-source/commit/1dc8ec9ec0c341b5c5b4209799abf9a83ac5391f](http://gitorious.org/opensuse/kernel-source/commit/1dc8ec9ec0c341b5c5b4209799abf9a83ac5391f)  shows and says:
```
 /* Fujitsu P-series tablet PC device */
			{ "FUJ02E6", 0 },
			+ /* Fujitsu Wacom Tablet PC device */
			+ { "FUJ02E7", 0 },
			/*
			* LG C1 EXPRESS DUAL (C1-PB11A3) touch screen (actually a FUJ02E6 in
			* disguise)
```
I don't know if it is possible to "rename" 'LTS0001' to "FUJ02E6" in HAL.  But something to keep in mind.

So I think you need a fujitouch driver like before.  The question is whether the fujitouch driver was incorporated into the evtouch driver (in Synaptic Package Manager).  It looks like the usb version was, but maybe not the serial version.

So look in Synaptic for the fujitouch driver, probably named xorg-xserver-input-fujitouch.  If it isn't there then the choice is to try the evtouch driver in Synaptic or try a ppa with what looks like a fujitouch driver updated for Karmic.

evtouch site:  [http://freshmeat.net/projects/evtouch/](http://freshmeat.net/projects/evtouch/)

fujitouch ppa:  [https://launchpad.net/~fujitouch/+archive/ppa](https://launchpad.net/~fujitouch/+archive/ppa)
and parent site:  [https://launchpad.net/~fujitouch](https://launchpad.net/~fujitouch)
source site for the update?:  [http://www.t2-project.org/packages/7.0/xf86-input-fujitouch.html](http://www.t2-project.org/packages/7.0/xf86-input-fujitouch.html)

The best LG C1 wiki/HOW TO I've seen (I think you've seen it before):  [http://www.gentoo-wiki.info/LG_C1](http://www.gentoo-wiki.info/LG_C1)

What I don't know is if you'll need to configure through xorg.conf or will the driver (Karmic fujitouch or evtouch) come with a .fdi?  If it does what will it be named (fujitouch.fdi?) and where will it be installed?  If it is in Synaptic check in the package list and see if it tells you.

Hope this helps.  Good luck!

---

### Post by vespagts on 2010-01-03
IT (quite) WORKS!!!!! THANKS FAVUX

I got the stylus working by the fpit driver installed through synaptic and the attached xorg.conf

the trick was to identify the device as Mouse0 with SendCoreEvents and leave Mouse0 as CorePointer under ServerLayout

...maybe there are better values for X and Y max & min but these work fine!

don't look at the commented lines in xorg.conf: they were from a previous attempt of using the fujitsu driver downloaded from conan.de (not working for me)

there is also another way to get it work, but calibration is not easy, u can find it here:

[http://doitfast4u.blogspot.com/2008/07/howto-get-touchscreen-working-on.html]("http://doitfast4u.blogspot.com/2008/07/howto-get-touchscreen-working-on.html")

it's been two years since my LG C1's touchscreen is not working, but I'm quite sure it could be used also with fingers on vista... after I figure out how to rotate screen that will be the real challenge... any idea?

Thank again Favux, I was quite giving it up on it!

bye for now!!!

---

### Post by Favux on 2010-01-03
Hi vespagts,

Outstanding!  Nice work!  So the fpit driver works for the LG C1.

Usually for rotation Fujitsu tablets use the fjbtndrv (Fujitsu Button driver).  I don't know if that will work for your tablet.  The ppa that updates it for Karmic is linked in [this post]("http://ubuntuforums.org/showpost.php?p=8478326&postcount=709").

---

### Post by redxine on 2010-01-03
Screen rotation would usually happen in System > Administration > Display (perhaps with the exception of NVidia cards; use the nvida configuration instead). If you want a hot key for rotation take a look at xrandr. 

```
xrandr -q
```
[http://www.cyberciti.biz/tips/linux-resize-screen-size-quickly.html]("http://www.cyberciti.biz/tips/linux-resize-screen-size-quickly.html")

---

### Post by vespagts on 2010-01-10
Hallo!

as for now it's ok with rotation:

```
xrandr -o left
```

or "right", "normal", "inverted" works fine for me, but I'd like to get the screen bezel keys to work... 

I've tried to install fjbtndrv, but it seems not to work... the keys aren't recognized either with xev nor acpi_listen...

where do Ihave to start to deal with it?



any way to get the keys recognized?


Thanks!

---

### Post by Favux on 2010-01-10
Hi vespagts,

If "the keys aren't recognized either with xev nor acpi_listen" you may not have anything to keybind with.  Two of my bezel keys look like they are suppose to go through wmi and then pass through hp-wmi but it isn't set up for them.  So they don't work either.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  There's a link there to [posts #273 & 274]("http://ubuntuforums.org/showthread.php?t=996830&page=28") where I discuss what we know about it.

So it's possible a launcher is the best you can do.

---

### Post by japglish on 2010-02-13
Both of you are stars.  Thanks for this solution, has been bugging me for months.  Also found the solution to the audio problem here [http://hatzimihailm.blogspot.com/2010/01/speaker-sound-on-lg-p1-express.html](http://hatzimihailm.blogspot.com/2010/01/speaker-sound-on-lg-p1-express.html) so doubly made my day.  Thx guys.

---

### Post by redxine on 2010-02-13
For the buttons, I have noticed that of my 4 buttons and the d-pad (Rotate screen, Taskmanager, Tablet software hotkey, and enable projector) if I hold down the projector button and press up or down on the dpad it will adjust the display brightness (although this might be a BIOS function). So the keys aren't completely useless, they just don't behave like they are expected to. I read on a thread somewhere when I first installed ubuntu on my laptop that the keys work through the same serial port that the tablet uses.

For now a panel button will work just fine. Perhaps a 'select case' function in bash to rotate the screen 90° clockwise every time the script is run.

---

### Post by pmsoft1 on 2010-03-12
Thanks to you guys I solved 2 out of 3 problems with my new karmic install.
My last problem concerns the touchpad.
If I click, this click is actually 3 clicks and a scroll (up if left click, down if right click) as described in [Arch Linux Wiki]("http://wiki.archlinux-br.org/Touchpad_Synaptics#Scrolling_and_multiple_actions_with_synaptics_on_LG_Laptops").
Back in hardy, the solution was to compile my own driver from this wiki (which is now removed, but I attached it).
This old driver fails to compile because of missing xf86_ansic.h and the new one doesn't solve the problem.
So here is my output
```
philipp@philipp-desktop:~/synaptics-0.14.6$ make
make: /bin/arch: Command not found
make: /bin/arch: Command not found
rm -f synaptics.o
gcc -c -O2 -pedantic -Wall -Wpointer-arith -fno-merge-constants -fPIC -I. -I/usr/include/X11 -I/usr/include/X11/extensions -I/usr/include/xorg -Dlinux -D_POSIX_C_SOURCE=199309L -D_POSIX_SOURCE -D_XOPEN_SOURCE -D_BSD_SOURCE -D_SVID_SOURCE  -D_GNU_SOURCE  -DSHAPE -DXINPUT -DXKB -DLBX -DXAPPGROUP -DXCSECURITY -DTOGCUP   -DDPMSExtension  -DPIXPRIV -DPANORAMIX  -DRENDER -DGCCUSESGAS -DAVOID_GLYPHBLT -DPIXPRIV -DSINGLEDEPTH -DXFreeXDGA -DXvExtension -DXFree86LOADER  -DXFree86Server -DXF86VIDMODE  -DSMART_SCHEDULE -DBUILDDEBUG -DX_BYTE_ORDER=X_LITTLE_ENDIAN -DNDEBUG -D__i386__ -DFUNCPROTO=15 -DNARROWPROTO -DIN_MODULE -DXFree86Module -DVERSION="\"0.14.6\"" -DVERSION_ID="(0*10000+14*100+6)"  synaptics.c
In file included from /usr/include/xorg/misc.h:113,
                 from synaptics.c:64:
/usr/include/xorg/os.h:519:16: warning: anonymous variadic macros were introduced in C99
In file included from /usr/include/xorg/xf86.h:47,
                 from synaptics.c:65:
/usr/include/xorg/xf86str.h:1098: warning: comma at end of enumerator list
synaptics.c:67:24: error: xf86_ansic.h: No such file or directory
synaptics.c:149: error: ‘XF86_VERSION_CURRENT’ undeclared here (not in a function)
synaptics.c: In function ‘SetDeviceAndProtocol’:
synaptics.c:183: warning: implicit declaration of function ‘strcmp’
synaptics.c: In function ‘alloc_param_data’:
synaptics.c:227: warning: implicit declaration of function ‘xf86shmget’
synaptics.c:228: warning: implicit declaration of function ‘xf86shmctl’
synaptics.c:228: error: ‘XF86IPC_RMID’ undeclared (first use in this function)
synaptics.c:228: error: (Each undeclared identifier is reported only once
synaptics.c:228: error: for each function it appears in.)
synaptics.c:230: error: ‘XF86IPC_CREAT’ undeclared (first use in this function)
synaptics.c:234: warning: implicit declaration of function ‘xf86shmat’
synaptics.c: In function ‘free_param_data’:
synaptics.c:261: error: ‘XF86IPC_RMID’ undeclared (first use in this function)
synaptics.c: In function ‘synSetFloatOption’:
synaptics.c:275: warning: implicit declaration of function ‘xf86sscanf’
synaptics.c: In function ‘SynapticsPreInit’:
synaptics.c:324: error: ‘struct _LocalDeviceRec’ has no member named ‘motion_history_proc’
synaptics.c:435: warning: implicit declaration of function ‘DBG’
synaptics.c:435: error: invalid use of void expression
synaptics.c:440: warning: implicit declaration of function ‘xf86mknod’
synaptics.c:440: error: ‘XF86_S_IFIFO’ undeclared (first use in this function)
synaptics.c:441: error: ‘xf86errno’ undeclared (first use in this function)
synaptics.c:441: error: ‘xf86_EEXIST’ undeclared (first use in this function)
synaptics.c:450: warning: implicit declaration of function ‘xf86free’
synaptics.c: In function ‘SynapticsCtrl’:
synaptics.c:495: error: invalid use of void expression
synaptics.c: In function ‘DeviceOn’:
synaptics.c:537: error: invalid use of void expression
synaptics.c: In function ‘DeviceOff’:
synaptics.c:571: error: invalid use of void expression
synaptics.c: In function ‘DeviceInit’:
synaptics.c:607: error: invalid use of void expression
synaptics.c:617: warning: implicit declaration of function ‘miPointerGetMotionBufferSize’
synaptics.c:617: warning: passing argument 4 of ‘InitPointerDeviceStruct’ from incompatible pointer type
/usr/include/xorg/input.h:357: note: expected ‘PtrCtrlProcPtr’ but argument is of type ‘int (*)(struct _DeviceIntRec *, struct xTimecoord *, long unsigned int,  long unsigned int,  struct _Screen *)’
synaptics.c:617: warning: passing argument 5 of ‘InitPointerDeviceStruct’ makes integer from pointer without a cast
/usr/include/xorg/input.h:357: note: expected ‘int’ but argument is of type ‘void (*)(struct _DeviceIntRec *, struct PtrCtrl *)’
synaptics.c: In function ‘move_distance’:
synaptics.c:637: warning: implicit declaration of function ‘xf86sqrt’
synaptics.c: In function ‘angle’:
synaptics.c:672: warning: implicit declaration of function ‘xf86atan2’
synaptics.c: In function ‘diffa’:
synaptics.c:679: warning: implicit declaration of function ‘xf86fmod’
synaptics.c: In function ‘SynapticsGetHwState’:
synaptics.c:787: warning: implicit declaration of function ‘xf86write’
synaptics.c: In function ‘SelectTapButton’:
synaptics.c:955: error: invalid use of void expression
synaptics.c:959: error: invalid use of void expression
synaptics.c:963: error: invalid use of void expression
synaptics.c:967: error: invalid use of void expression
synaptics.c:971: error: invalid use of void expression
synaptics.c:977: error: invalid use of void expression
synaptics.c:981: error: invalid use of void expression
synaptics.c: In function ‘SetTapState’:
synaptics.c:994: error: invalid use of void expression
synaptics.c: In function ‘ComputeDeltas’:
synaptics.c:1283: warning: implicit declaration of function ‘xf86modf’
synaptics.c: In function ‘HandleScrolling’:
synaptics.c:1388: error: invalid use of void expression
synaptics.c:1396: error: invalid use of void expression
synaptics.c:1401: error: invalid use of void expression
synaptics.c:1409: error: invalid use of void expression
synaptics.c:1415: error: invalid use of void expression
synaptics.c:1425: error: invalid use of void expression
synaptics.c:1431: error: invalid use of void expression
synaptics.c:1435: error: invalid use of void expression
synaptics.c:1441: error: invalid use of void expression
synaptics.c:1445: error: invalid use of void expression
synaptics.c:1464: error: invalid use of void expression
synaptics.c:1475: error: invalid use of void expression
synaptics.c: In function ‘ControlProc’:
synaptics.c:1782: error: invalid use of void expression
synaptics.c: In function ‘CloseProc’:
synaptics.c:1790: error: invalid use of void expression
make: *** [synaptics.o] Error 1
philipp@philipp-desktop:~/synaptics-0.14.6$

```

Can anyone help?

Thanks in advance.

---

### Post by pmsoft1 on 2010-03-17
Nobody?

My temporary solution is to deactivate scrolling:
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "UpDownScrolling" "0"
    Option         "ZAxisMapping" "4 5"
EndSection
```

But the triple click is still annoying.

---

### Post by zeronius on 2010-11-23
Hi,

i have the same problem here with maverick, 3 clicks and a roll down on left button, 3 clicks and a roll up on the right button.
my solution ist not nice, i use my bluetooth mouse, but anyone out there now managed to find a correct driver or know where i can find?

thanks all :cool:

---

