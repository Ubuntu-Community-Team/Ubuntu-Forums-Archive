---
title: "Rotate mouse/cursor axes"
date: 2008-10-10
forum: General Help
---

### Post by Riceboy004 on 2008-10-10
I've just discovered the magic of screen rotation and xrandr.  My laptop (Asus S5n) is small enough that I can hold it like a book, and subsequently i can read pdf's as if i was reading book.  However, it is a little annoying that my touchpad control doesn't change.  Holding in book position, "up" on the touchpad translates to "right" on the screen.  **Is there any way to rotate my touchpad mappings? ** Preferably without needing to restart xorg, so that I can batch together a rotate-screen command with a rotate-cursor command in a script.  Thanks.

---

### Post by Riceboy004 on 2008-10-10
(Bump)

---

### Post by mrpeenut24 on 2008-11-01
I've also been wondering about this.  Anybody know if it's possible?

---

### Post by popperoga on 2008-11-15
Just found a solution to rotate the screen **and** the touchpad simultaneously. Here the procedure.

**1. Enable xrandr**
make sure that xrandr is installed:
[I]sudo apt-get install x11-xserver-utils
[/I]
Add this line to the xorg.conf file
```
Section "Device"
	Identifier	"Configured Video Device"
	...		...
	Option		"RandRRotation" "true"
EndSection
```

then rotate the screen with this command:
*xrandr -o [right,left,inverted,normal]*

**2. Patch the synaptic drives and enable touchpad XY flip**

The following section has been taken from [this website]("http://www.helsinki.fi/~rantalai/synaptics/").

Modify the xorg.conf according to this:
```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "SHMConfig"             "true"
EndSection
```

Install those packages:
*sudo apt-get build-dep xserver-xorg-input-synaptics*

Get official sources:
*apt-get source xserver-xorg-input-synaptics*

Patch and compile the new drivers:
[I]cd xfree86-driver-synaptics-*/
wget [http://www.helsinki.fi/~rantalai/synaptics/axis_patch](http://www.helsinki.fi/~rantalai/synaptics/axis_patch)
patch < axis_patch
make[/I]

Backup the original drivers
[I]mkdir original_drivers
cp -p /usr/lib/xorg/modules/input/synaptics_drv.so original_drivers/
cp -p /usr/bin/synclient original_drivers/[/I]

Install the new drivers:
[I]sudo cp synclient /usr/bin/
sudo cp synaptics_drv.so /usr/lib/xorg/modules/input/[/I]

Usage:
[I]synclient Xrandr=0 
xrandr --orientation normal

synclient Xrandr=1 
xrandr --orientation right

synclient Xrandr=2
xrandr --orientation left

synclient Xrandr=3
xrandr --orientation inverted[/I]

You can also write a simple script that automatically rotate the screen and the mouse/touchpad. Create with your favourite text editor a file named *rotation* and copy&paste this:
```

#!/bin/sh
if   [ $1 = "normal" ] ; then
    synclient Xrandr=0
    xrandr --orientation normal
elif [ $1 = "right" ] ; then
    synclient Xrandr=1
    xrandr --orientation right
elif [ $1 = "left" ] ; then
        synclient Xrandr=2
    xrandr --orientation left
elif [ $1 = "inverted" ] ; then
    synclient Xrandr=3
    xrandr --orientation inverted
else
    echo "rotation [normal,righ,left,inverted]"
fi
```

Then
[I]chmod +x rotation
sudo cp -p rotation /usr/local/bin/[/I]

Hope it works!

---

### Post by dreamessence on 2008-12-15
Hey!
Thanks very much for the post, rotating the cursor is sth i've been meaning to do for a long time, but i didn't have the skills to do it.

I've followed all your steps and yet when i type:
synclient Xrand=1
 I get:
Can't access shared memory area. SHMConfig disabled?

But i did change the xorg.config file to allow for the SHMConfig (i.e. I set it true).

Any idea?

Thanks a lot,

]d[

---

### Post by popperoga on 2008-12-17
Try to use this line in the xorg.conf:
```
Option          "SHMConfig"             "on"
```

---

### Post by dreamessence on 2008-12-17
Cool! You modify the xorg.config with that line, then re-start X (ctrl+alt+supr) and you are good to go!!!

---

### Post by orob on 2009-02-25
Hello,

Does anyone have a copy of the axis patch they can send me?
The url linked above for the axis patch is no longer available.

Thank you.

---

### Post by seymour9 on 2009-03-06
I'd like patch too
do anyone has it?

---

### Post by seymour9 on 2009-03-07
I found patch diff info.
To install it you need to modify the souce of yuour own synaptic driver version according to this:
```
diff -ur old/include/synaptics.h new/include/synaptics.h
--- old/include/synaptics.h	2008-11-26 11:40:08.000000000 +0200
+++ new/include/synaptics.h	2008-11-26 11:42:21.000000000 +0200
@@ -61,6 +61,7 @@
 typedef struct _SynapticsSHM
 {
     int version;			    /* Driver version */
+    int xrandr;
 
     /* Current device state */
     int x, y;				    /* actual x, y coordinates */
diff -ur old/src/eventcomm.c new/src/eventcomm.c
--- old/src/eventcomm.c	2008-11-26 10:49:01.000000000 +0200
+++ new/src/eventcomm.c	2008-11-26 11:58:49.000000000 +0200
@@ -192,6 +192,8 @@
     struct input_event ev;
     Bool v;
     struct SynapticsHwState *hw = &(comm->hwState);
+    SynapticsPrivate *priv = (SynapticsPrivate *) (local->private);
+    SynapticsSHM *para = priv->synpara;
 
     while (SynapticsReadEvent(comm, &ev)) {
 	switch (ev.type) {
@@ -272,10 +274,24 @@
 	case EV_ABS:
 	    switch (ev.code) {
 	    case ABS_X:
-		hw->x = ev.value;
+		if (para->xrandr==0)
+			hw->x = ev.value;
+		if (para->xrandr==1)
+			hw->y = -ev.value;
+		if (para->xrandr==2)
+			hw->y = ev.value;
+		if (para->xrandr==3)
+			hw->x = -ev.value;
 		break;
 	    case ABS_Y:
-		hw->y = ev.value;
+		if (para->xrandr==0)
+			hw->y = ev.value;
+		if (para->xrandr==1)
+			hw->x = ev.value;
+		if (para->xrandr==2)
+			hw->x = -ev.value;
+		if (para->xrandr==3)
+			hw->y = -ev.value;
 		break;
 	    case ABS_PRESSURE:
 		hw->z = ev.value;
diff -ur old/src/synaptics.c new/src/synaptics.c
--- old/src/synaptics.c	2008-11-26 10:49:01.000000000 +0200
+++ new/src/synaptics.c	2008-11-26 11:41:12.000000000 +0200
@@ -384,6 +384,7 @@
     /* read the parameters */
     pars = &priv->synpara_default;
     pars->version = (PACKAGE_VERSION_MAJOR*10000+PACKAGE_VERSION_MINOR*100+PACKAGE_VERSION_PATCHLEVEL);
+    pars->xrandr = xf86SetIntOption(opts, "Xrandr", 0);
 
     /* The synaptics specs specify typical edge widths of 4% on x, and 5.4% on
      * y (page 7) [Synaptics TouchPad Interfacing Guide, 510-000080 - A
diff -ur old/tools/synclient.c new/tools/synclient.c
--- old/tools/synclient.c	2008-11-26 11:01:47.000000000 +0200
+++ new/tools/synclient.c	2008-11-26 11:03:37.000000000 +0200
@@ -60,6 +60,7 @@
 { name, offsetof(SynapticsSHM, memb), (type), (min_val), (max_val) }
 
 static struct Parameter params[] = {
+    DEFINE_PAR("Xrandr",               xrandr,                  PT_INT,    0, 3),
     DEFINE_PAR("LeftEdge",             left_edge,               PT_INT,    0, 10000),
     DEFINE_PAR("RightEdge",            right_edge,              PT_INT,    0, 10000),
     DEFINE_PAR("TopEdge",              top_edge,                PT_INT,    0, 10000),
```

---

### Post by aapo4 on 2009-03-07
Instructions and patches:
[http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/)

---

### Post by elgreengeeto on 2009-08-26
Those instructions worked for me on Ubuntu 9.04! Thanks everyone :) My MSI Wind is now a sweet ebook reader

---

### Post by lacunoso on 2009-11-16
Nice, there is a new patch for Karmic and synaptics-1.1.2.
[http://cc.oulu.fi/~rantalai/synaptics/]("http://cc.oulu.fi/~rantalai/synaptics/")
Thanks for this! :D

---

### Post by aapo4 on 2009-11-17
Yes, patch is up-to-date and in Karmic it is even easier to use (no editing xorg.conf or hdi.policies).  I sent it to upstream, lets see what happens.

Do not hold breath. Because actually this patch doesn't do things right. Yes, it solves problem, but maybe regular mouse should be also affected when screen is rotated. So maybe this screen orientation should be handled much lower level than synaptics.

---

### Post by samguyjones on 2010-02-16
Hello everyone,

I'm trying the patch on UNR.  I compiled the patch and installed it.  /usr/lib/xorg/modules/input/synaptics_drv.so is 232818 bytes.  original_synaptics_drv.so is 50960 bytes.  There was no error during the patch and build process.  If I run "synclient Orientation=2", I get this error:

Unknown parameter Orientation

What should I be looking for?

---

### Post by aapo4 on 2010-02-17
About filesize:
Compiling instructions doesn't contain 'stripping'.

If you check 
file /usr/lib/xorg/modules/input/synaptics_drv.so
and
file $OWN_COMPILED/src/.libs/synaptics_drv.so

you see 'stripped' / 'not stripped'

So just ```
strip $OWN_COMPILED/src/.libs/synaptics_drv.so
```



About synclient:
You must use corresponding synclient and driver.
```
cp $OWN_COMPILED/tools/synclient  /usr/bin/synclient
```
or use full path.

---

### Post by samguyjones on 2010-02-17
> **aapo4 said:**
> About filesize:
Compiling instructions doesn't contain 'stripping'.

If you check 
file /usr/lib/xorg/modules/input/synaptics_drv.so
and
file $OWN_COMPILED/src/.libs/synaptics_drv.so

you see 'stripped' / 'not stripped'

So just ```
strip $OWN_COMPILED/src/.libs/synaptics_drv.so
```

About synclient:
You must use corresponding synclient and driver.
```
cp $OWN_COMPILED/tools/synclient  /usr/bin/synclient
```or use full path.


:biggrin:  It worked!  It freakin' worked!  I just had to copy the client.  If I wasn't at work and didn't have a bad cold, I'd be up and doing a little dance.  This makes a huge difference to me.  I love to use my netbook in portrait for ebooks and reader, but the controls were difficult.

I had to put this into my xorg.conf under the synaptics options
```

"GrabEventDevice"  "Off"

```
X was hitting some kind of conflict.  After I added the line, I had to warning in my X logs, and the Orientation started working.  I lost some synaptics settings in my xorg.conf, but I can set them with synclient, so no biggie.

Also good to know about stripping.  I was just using file size to tell me which was new and which was old and I knew that I copied the file.  The size doesn't bother me, but the stripped synclient is a teeny 20596.

---

### Post by emunrradtvamg on 2010-02-17
[QUOTE=Riceboy004;5939785]I've just discovered the magic of screen rotation and xrandr.  My laptop (Asus S5n) is small enough that I can hold it like a book, and subsequently i can read pdf's as if i was reading book.  However, it is a little annoying that my touchpad control doesn't change.  Holding in book position, "up" on the touchpad translates to "right" on the screen.  **Is there any way to rotate my touchpad mappings? ** Preferably without needing to restart xorg, so that I can batch together a rotate-screen command with a rotate-cursor command in a script.  Thanks.[/Q

---

### Post by aapo4 on 2010-04-09
Hi, I got my PPA working and patched driver can be installed without compiling. (Currently only 9.10 Karmic)

```
sudo add-apt-repository ppa:aapo-rantalainen/ppa-aaporantalainen
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```


[http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/)

---

### Post by cats00eye on 2010-04-15
Just got this to work, and it's wonderful! Thank you so much to all.

Just to point up that there's a typo in the last link. I couldn't get it to work, but worked back from the site [http://ppa.launchpad.net/](http://ppa.launchpad.net/)

I _think_ the last hyphen on the first line needs to be omitted.

---

### Post by aapo4 on 2010-04-15
Thanks, now address is corrected.

---

### Post by clegends on 2010-04-20
Any chance this ppa being made available for Lucid? Looking forward to trying it out, I have a eeepc 901. Cheers.

---

### Post by aapo4 on 2010-04-20
> Any chance this ppa being made available for Lucid?


Anybody is free to do so. I'm planning to do it after Official release, maybe May 2, 2010.

---

### Post by Askrates on 2010-05-03
Hi aapo4,

I found your page and this thread after a lot of digging around. Unfortunately, I am using a newer version of Ubuntu, so I am really looking forward to your patch for 10.04.

Keep up the good work!

---

### Post by aapo4 on 2010-05-03
It has been 22 hours on the builders queue for 10.04.

---

### Post by marranzano on 2010-05-03
> **aapo4 said:**
> It has been 22 hours on the builders queue for 10.04.

just updated with your repo,, thnx!

bu when i run 
$ synclient Xrandr=3
i get:
```
Unknown parameter Xrandr
```

synclient works fine for other options...

any ideas?

EDIT: ok... got it:
the command is synclient orientation=...
got distracted by previous posts...

thanks for the great work!!

---

### Post by Ubuntitude on 2010-05-06
In regards to it being ported to 10.04:

I got it to work perfectly in 10.04. I just followed the instructions on aapo's website. These seemed to not work, so i used the alternate driver installation method he posted here. Then i restarted X, and it worked great!

---

### Post by Drisanna on 2010-05-15
Okay.  I installed this have it working correctly.  What I would like to know now is this:  Is there a way to automate this, so that when I rotate my screen, the touchpad automatically follows?  

Thanks in advance.  

Drisanna

---

### Post by aapo4 on 2010-05-15
There are no yet true automatic way.

You can make scripts or aliases that every time you rotate screen also axis are flipped. Something like:
alias left = 'xrandr -o 1; synclient Orientation=1'

For developers: How this automation should be done? Driver can check orientation of screen. But how driver knows when to check state? Once in every seconds sounds very bad idea.

---

### Post by marranzano on 2010-05-15
there are several scripts that you can find here:
[http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)

including magick-rotation-0.4-beta1 for lucid that can be found here:
[http://ubuntuforums.org/showpost.php?p=8052613&postcount=315](http://ubuntuforums.org/showpost.php?p=8052613&postcount=315)

I have a tx2510us and use this script which checks hp-wmi every second, therefore it's triggered when the screen is rotated and shut in tablet mode:```
#!/bin/bash

# From Red_Lion post #576:  http://ubuntuforums.org/showthread.php?t=845911&page=58

old="0"
while true; do
	if [[ -e /sys/devices/platform/hp-wmi/tablet ]]; then
		new=`cat /sys/devices/platform/hp-wmi/tablet`
		if [[ $new != $old ]]; then
#			-Close and restart Cairo Dock so it resizes on rotation.
#			killall -9 cairo-dock &
#			sleep 2s
			if [[ $new == "0" ]]; then
				echo "Rotate to landscape, hide cellwriter."
				xrandr -o normal 
				xsetwacom set 12 rotate NONE 
				xsetwacom set 11 rotate NONE
				xsetwacom set 13 rotate NONE
				synclient orientation=0

#				cellwriter --hide-window
			elif [[ $new == "1" ]]; then
				echo "Rotate to portrait, show cellwriter."
				xrandr -o right 
				xsetwacom set 12 rotate CW 
				xsetwacom set 11 rotate CW
				xsetwacom set 13 rotate CW 
				synclient orientation=3
				cellwriter --show-window
			fi 
#			cairo-dock -o &
		fi
		old=$new
		sleep 1s
	fi
done
```
although it doesn't make much sense to have the touchpad (synclient) rotate when the laptop is in tablet mode because the touchpad is hidden under the screen...

the other script i use is connected to one of my special keys and rotates everything 90degrees every time i hit the key; to make it work you must first make a file named .screen-orientation in your home dir with the word "normal" in it, or just type this in a terminal:
echo "normal"> .screen-orientation

```
#!/bin/bash
rotate=`cat ~/.screen-orientation`
echo $rotate
	if [ "$rotate" = "normal" ];
	then
	rotate="left"
	wacom="CCW"
	synaptics="1"
	else
		if [ "$rotate" = "left" ];
		then
		rotate="inverted";
		wacom="HALF";
		synaptics="2"
		else
			if [ "$rotate" = "inverted" ];
			then
			rotate="right";
			wacom="CW";
			synaptics="3"
			else
				if [ "$rotate" = "right" ];
				then
				rotate="normal";
				wacom="NONE";
				synaptics="0"
				fi
			fi
		fi
	fi
echo "rotate = "$rotate
echo "wacom = "$wacom
xrandr -o "$rotate";
xsetwacom set "12" Rotate "$wacom";
xsetwacom set "13" Rotate "$wacom";
xsetwacom set "11" Rotate "$wacom";
synclient orientation="$synaptics"
echo $rotate > ~/.screen-orientation;
```


hope this helps
marranzano

---

### Post by pcolamar on 2010-09-07
I have tried to use the ppa solution with my MSi Wind and Lynx 10.04 but it does not work.
It seems lucid is not using the synaptic driver.

*cat /var/log/Xorg.0.log | grep -i "synaptics"*
does not give anything and when I try synclient I get:

[I]palmer@palmer-laptop:~$ synclient Orientation=1
Couldn't find synaptics properties. No synaptics driver loaded?[/I]

I have installed "gpointing-device-settings"(apparently gsynaptic is deprecated) and it recognizes the Sintelic trackpad.
Shell I force (and how?) the use of the synaptic driver ?
Cheers

---

### Post by aapo4 on 2010-09-07
Unfortunately I do not know what to do if Synaptic driver is not used at all.

You have now driver installed?
```
apt-cache policy xserver-xorg-input-synaptics
```

---

### Post by pcolamar on 2010-09-07
that's the result of server-xorg-input-synaptics:

  Installed: 1.2.2-1ubuntu4-b1
  Candidate: 1.2.2-1ubuntu4-b1
  Version table:
 *** 1.2.2-1ubuntu4-b1 0
        500 [http://ppa.launchpad.net/aapo-rantalainen/ppa-aaporantalainen/ubuntu/](http://ppa.launchpad.net/aapo-rantalainen/ppa-aaporantalainen/ubuntu/) lucid/main Packages
        100 /var/lib/dpkg/status
     1.2.2-1ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Packages

---

### Post by aapo4 on 2010-10-23
Maverick Meerkat (10.10) supported. Same PPA.

```
sudo add-apt-repository ppa:aapo-rantalainen/ppa-aaporantalainen
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```


Same usage: (e.g)
```
synclient Orientation=3 && xrandr -o 3
```

Read more:
[http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/)

---

### Post by Nephiel on 2011-01-14
Just tried this from the PPA on my netbook (ASUS eeePC 1001PX) and it worked. The only issue I had with it is, when the touchpad is rotated, the horizontal and vertical speeds of the touchpad no longer match.

So, when rotated, it took 3 whole passes of the finger from left edge to right edge of the touchpad to move the pointer on screen from top to bottom, while moving the pointer from side to side on the screen only required a finger movement of about a third of the touchpad height. I.e., the pointer moves very fast horizontally but very slow vertically.

The solution was to swap horizontal/vertical resolution properties when the touchpad is rotated.

Here's an updated patch:
```
diff -ur xserver-xorg-input-synaptics_1.1.2.orig/src/synapticsstr.h xserver-xorg-input-synaptics_1.1.2/src/synapticsstr.h
--- xserver-xorg-input-synaptics_1.1.2.orig/src/synapticsstr.h	2011-01-14 19:36:17.000000000 +0100
+++ xserver-xorg-input-synaptics_1.1.2/src/synapticsstr.h	2011-01-14 19:36:03.000000000 +0100
@@ -92,6 +92,7 @@
     /* Parameter data */
     int left_edge, right_edge, top_edge, bottom_edge; /* edge coordinates absolute */
     int finger_low, finger_high, finger_press;	      /* finger detection values in Z-values */
+    int orientation;
     int tap_time;
     int tap_move;			    /* max. tapping time and movement in packets and coord. */
     int single_tap_timeout;		    /* timeout to recognize a single tap */
diff -ur xserver-xorg-input-synaptics_1.1.2.orig/include/synaptics-properties.h xserver-xorg-input-synaptics_1.1.2/include/synaptics-properties.h
--- xserver-xorg-input-synaptics_1.1.2.orig/include/synaptics-properties.h	2009-10-20 22:09:01.679710327 +0200
+++ xserver-xorg-input-synaptics_1.1.2/include/synaptics-properties.h	2009-10-22 18:48:47.123708014 +0200
@@ -142,4 +142,7 @@
 /* 8 bit (BOOL) */
 #define SYNAPTICS_PROP_GRAB "Synaptics Grab Event Device"
 
+/* 32 bit */
+#define SYNAPTICS_ORIENTATION "Synaptics Orientation"
+
 #endif /* _SYNAPTICS_PROPERTIES_H_ */
diff -ur xserver-xorg-input-synaptics_1.1.2.orig/src/eventcomm.c xserver-xorg-input-synaptics_1.1.2/src/eventcomm.c
--- xserver-xorg-input-synaptics_1.1.2.orig/src/eventcomm.c	2009-10-20 22:09:01.683709019 +0200
+++ xserver-xorg-input-synaptics_1.1.2/src/eventcomm.c	2009-10-22 21:22:58.224803290 +0200
@@ -352,10 +352,28 @@
 	case EV_ABS:
 	    switch (ev.code) {
 	    case ABS_X:
-		hw->x = ev.value;
+		if (para->orientation==0)
+			hw->x = ev.value;
+		else if (para->orientation==2)
+			hw->x = priv->maxx + priv->minx - ev.value;
+		else if (para->orientation==3)
+			hw->y = (priv->maxx - ev.value) * (priv->maxy - priv->miny) / (priv->maxx - priv->minx) + priv->miny;
+		else if (para->orientation==1)
+			hw->y = (ev.value - priv->minx) * (priv->maxy - priv->miny) / (priv->maxx - priv->minx) + priv->miny;
+		else
+			hw->x = ev.value;
 		break;
 	    case ABS_Y:
-		hw->y = ev.value;
+		if (para->orientation==0)
+			hw->y = ev.value;
+		else if (para->orientation==2)
+			hw->y = priv->maxy + priv->miny - ev.value;
+		else if (para->orientation==3)
+			hw->x = (ev.value - priv->miny) * (priv->maxx - priv->minx) / (priv->maxy - priv->miny) + priv->minx;
+		else if (para->orientation==1)
+			hw->x = (priv->maxy - ev.value) * (priv->maxx - priv->minx) / (priv->maxy - priv->miny) + priv->minx;
+		else
+			hw->y = ev.value;
 		break;
 	    case ABS_PRESSURE:
 		hw->z = ev.value;
diff -ur xserver-xorg-input-synaptics_1.1.2.orig/src/properties.c xserver-xorg-input-synaptics_1.1.2/src/properties.c
--- xserver-xorg-input-synaptics_1.1.2.orig/src/properties.c	2009-10-20 22:09:01.683709019 +0200
+++ xserver-xorg-input-synaptics_1.1.2/src/properties.c	2009-10-22 18:48:47.131703654 +0200
@@ -44,6 +44,7 @@
 static Atom float_type;
 
 Atom prop_edges                 = 0;
 Atom prop_finger                = 0;
+Atom prop_orientation           = 0;
 Atom prop_tap_time              = 0;
 Atom prop_tap_move              = 0;
@@ -251,6 +252,8 @@
     fvalues[0] = para->press_motion_min_factor;
     fvalues[1] = para->press_motion_max_factor;
 
+    prop_orientation = InitAtom(local->dev, SYNAPTICS_ORIENTATION, 32, 1, &para->orientation);
+
     prop_pressuremotion_factor = InitFloatAtom(local->dev, SYNAPTICS_PROP_PRESSURE_MOTION_FACTOR, 2, fvalues);
 
     prop_grab = InitAtom(local->dev, SYNAPTICS_PROP_GRAB, 8, 1, &para->grab_event_device);
@@ -270,7 +273,13 @@
         para = &tmp;
     }
 
-    if (property == prop_edges)
+	if (property == prop_orientation)
+	{
+        if (prop->size != 1 || prop->format != 32 || prop->type != XA_INTEGER)
+            return BadMatch;
+		para->orientation = *(INT32*)prop->data;
+	}
+	else if (property == prop_edges)
     {
         INT32 *edges;
         if (prop->size != 4 || prop->format != 32 || prop->type != XA_INTEGER)
diff -ur xserver-xorg-input-synaptics_1.1.2.orig/src/synaptics.c xserver-xorg-input-synaptics_1.1.2/src/synaptics.c
--- xserver-xorg-input-synaptics_1.1.2.orig/src/synaptics.c	2009-10-20 22:09:01.683709019 +0200
+++ xserver-xorg-input-synaptics_1.1.2/src/synaptics.c	2009-10-22 18:57:34.363700791 +0200
@@ -433,6 +433,7 @@
     horizTwoFingerScroll = FALSE;
 
     /* set the parameters */
+    pars->orientation = xf86SetIntOption(opts, "Orientation", 0);
     pars->left_edge = xf86SetIntOption(opts, "LeftEdge", l);
     pars->right_edge = xf86SetIntOption(opts, "RightEdge", r);
     pars->top_edge = xf86SetIntOption(opts, "TopEdge", t);
@@ -2391,8 +2391,14 @@
     int xCenter = (priv->synpara.left_edge + priv->synpara.right_edge) / 2;
     int yCenter = (priv->synpara.top_edge + priv->synpara.bottom_edge) / 2;
 
-    hw->x = (hw->x - xCenter) * priv->horiz_coeff + xCenter;
-    hw->y = (hw->y - yCenter) * priv->vert_coeff + yCenter;
+    if ((priv->synpara.orientation==1) || (priv->synpara.orientation==3)) {
+        hw->x = (hw->x - xCenter) * priv->vert_coeff + xCenter;
+        hw->y = (hw->y - yCenter) * priv->horiz_coeff + yCenter;
+    } else {
+        hw->x = (hw->x - xCenter) * priv->horiz_coeff + xCenter;
+        hw->y = (hw->y - yCenter) * priv->vert_coeff + yCenter;
+    }
+
 }
 
 void
diff -ur xserver-xorg-input-synaptics_1.1.2.orig/tools/synclient.c xserver-xorg-input-synaptics_1.1.2/tools/synclient.c
--- xserver-xorg-input-synaptics_1.1.2.orig/tools/synclient.c	2011-01-14 19:22:01.000000000 +0100
+++ xserver-xorg-input-synaptics_1.1.2/tools/synclient.c	2011-01-14 19:19:13.000000000 +0100
@@ -78,6 +78,7 @@
     {"RightEdge",             PT_INT,    0, 10000, SYNAPTICS_PROP_EDGES,	32,	1},
     {"TopEdge",               PT_INT,    0, 10000, SYNAPTICS_PROP_EDGES,	32,	2},
     {"BottomEdge",            PT_INT,    0, 10000, SYNAPTICS_PROP_EDGES,	32,	3},
+    {"Orientation",           PT_INT,    0, 3,     SYNAPTICS_ORIENTATION,	32,	0},
     {"FingerLow",             PT_INT,    0, 255,   SYNAPTICS_PROP_FINGER,	32,	0},
     {"FingerHigh",            PT_INT,    0, 255,   SYNAPTICS_PROP_FINGER,	32,	1},
     {"FingerPress",           PT_INT,    0, 256,   SYNAPTICS_PROP_FINGER,	32,	2},

```
So far, this works for me with Maverick 10.10, following aapo4's instructions to get the Ubuntu sources, patch them, compile them, create the package and install it.

---

### Post by Nephiel on 2011-01-14
(duplicate post)

---

### Post by Nephiel on 2011-01-14
(duplicate post)

---

### Post by Nephiel on 2011-01-14
(duplicate post)

---

### Post by Nephiel on 2011-01-14
(duplicate post)

---

### Post by Nephiel on 2011-01-14
(duplicate post)

---

### Post by aapo4 on 2011-01-16
Thanks to Nephiel for this patch. Package on PPA is now updated (current version is 1.2.2-2ubuntu5-b2) for Maverick. I'm not planning to update Lucid or Karmic versions. 


[http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/)

---

### Post by henriquemaia on 2011-04-28
Will the patch be updated to Natty? 

Just in case I need it.

---

### Post by aapo4 on 2011-05-04
Now PPA has also version for Natty.
----
NEWS: patch is committed to the upstream:
[http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/commit/?id=049d5fb6037b34d94b24cb8300849cf4e3b67437](http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/commit/?id=049d5fb6037b34d94b24cb8300849cf4e3b67437)

Unfortunately it is then reverted back:
[http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/commit/?id=4ebde557aee7953f766fcd6b725cbacd47f806ec](http://cgit.freedesktop.org/xorg/driver/xf86-input-synaptics/commit/?id=4ebde557aee7953f766fcd6b725cbacd47f806ec)
and discussed further:
[http://comments.gmane.org/gmane.comp.freedesktop.xorg.devel/20034](http://comments.gmane.org/gmane.comp.freedesktop.xorg.devel/20034)

Currently issue is still open on upstream, but there are hope. Next step needs more Xorg-knowledge than I have...

---

### Post by sdaau on 2011-07-07
Hi all,

Sorry to bump in the thread, but it did come up quite high in my search results, yet my problem wasn't so much related to Synaptics touchpad - I wanted to rotate the axis of touchscreen. 

The thing is, in principle, it seems that one should be able to use `xinput` without changes to any drivers - however, it is not very straightforward, and I've had only limited success with it (mostly because you'd have to think through what sort of a Coordinate Transform Matrix you'd like, and I was just testing values blindly :) ) 

Nonetheless, here's a link dump, maybe it helps someone: 

[LIST]
[*] [How To: rotate screen portrait mode Ubuntu lucid - Micro PC Talk Forums]("http://www.micropctalk.com/forums/showthread.php?t=8933")
[*] [Bug #767315 in xorg-server (Ubuntu): &#8220;xinput 2 "Coordinate Transformation Matrix" not affecting all events&#8221;]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/767315")
[*] [X.Org Wiki - XInputCoordinateTransformationMatrixUsage]("http://www.x.org/wiki/XInputCoordinateTransformationMatrixUsage")
[*] [X/InputCoordinateTransformation - Ubuntu Wiki]("https://wiki.ubuntu.com/X/InputCoordinateTransformation")
[*] [Debian User Forums &#8226; View topic - Configure your trackpad using xinput]("http://www.debianuserforums.org/viewtopic.php?f=9&t=572")
[*] [Dual touchscreen support. NOW: Stuck on xinput configuration - Ars Technica OpenForum]("http://arstechnica.com/civis/viewtopic.php?f=16&t=1146846")
[*] [[PATCH] evdev: add 3x3 transformation matrix xinput property for multi-head handling]("http://lists.x.org/archives/xorg/2010-April/049967.html")
[/LIST]

---

### Post by Jack Brown on 2011-08-18
tried out the patch on natty and it works after reboot.

thing is, command to disable the touchpad no longer works.

```
synclient touchpadoff=1
```how to fix this?



EDIT:

in case you tried the above command and your touchpad stops working.
use
synclient touchpadoff=0
to turn it back on.

and i guess that's good news for you if you applied the patch, since it still works for you.

Edit2:
im using the 1.3.99 patch.
another question: what happens if upstream updates xserver-xorg-input-synaptics?
is it possible that we are using an old version that's why synclient touchpadoff is not working?

---

### Post by Jack Brown on 2011-08-18
also bash script that you can call from Keyboard Shortcuts:

```
#!/bin/bash

# this script changes screen orientation, and also the touchpad orientation. uses xrandr and synclient commands.
# also used xserver-xorg-input-synptics patch from https://launchpad.net/~aapo-rantalainen/+archive/ppa-aaporantalainen

case $1 in
0)
  xrandr -o normal
  synclient Orientation=0 
  ;;
1)
  xrandr -o left
  synclient Orientation=1 
  ;;
2)
  xrandr -o inverted
  synclient Orientation=2 
  ;;
3)
  xrandr -o right
  synclient Orientation=3 
  ;;
*)
  echo "pass parameter 0-3"
  ;;
esac
```

save as a file (e.g. orientscreen.sh) somewhere in your home folder.

give it executable privileges from terminal
chmod +x orientscreen.sh

then in Keyboard Shortcuts
add custom shortcut
'normal orientation'
with 
command:
/home/...[other folders]/orientscreen.sh 0

set keyboard shortcut to something like     SUPER key + UpArrow

and so on for other orientations.

---

### Post by aapo4 on 2011-08-18
I'm using package from my PPA (for Natty) and synclient touchpadoff=1 is working as expected.

Did you compiled patched driver for yourself? Try then compile same version (with same configuration) WITHOUT patch and check is touchpadoff=1 is working or not.

Just looking patch doesn't give any hints why touchpadoff is not working.

---

### Post by Jack Brown on 2011-08-19
Hi aapo, 

thanks for replying.

used the xserver-xorg-input-synaptics_1.3.99+git20110116.0e27ce3a-0ubuntu12-b1_amd64.deb
from the ppa.   64bit.

wonder why it doesnt work.  it used to work before i applied the patch.


are you supposed to modify anything else after applying the above patch? 
the rotate for both screen and mouse works already though...

when i run synclient touchpadoff=1 on the terminal, there is no error message.

How do you go back to original version for testing? just apt-get purge and reinstall xserver-xorg-input-synaptics (from ubuntu and not from ppa)?

---

### Post by aapo4 on 2011-11-01
> **Jack Brown said:**
> 
How do you go back to original version for testing? 


Check what is version on Ubuntu's repository:
```
apt-cache policy xserver-xorg-input-synaptics

```

Answer will be something like:
```
xserver-xorg-input-synaptics:
  Installed: 1.4.1-1ubuntu2-b2
  Candidate: 1.4.1-1ubuntu2-b2
  Version table:
 *** 1.4.1-1ubuntu2-b2 0
        500 http://ppa.launchpad.net/aapo-rantalainen/ppa-aaporantalainen/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     1.4.1-1ubuntu2 0
        500 http://fi.archive.ubuntu.com/ubuntu/ oneiric/main amd64 Packages
```

Which means: Currently installed version is **1.4.1-1ubuntu2-b2**, it is also the newest version and it comes from [http://ppa.launchpad.net/aapo-rantalainen/](http://ppa.launchpad.net/aapo-rantalainen/). 
And there are version **1.4.1-1ubuntu2** from ubuntu.com.

Then install (downgrade) to that version
```
sudo apt-get install xserver-xorg-input-synaptics=1.4.1-1ubuntu2
```

(This can be done also with GUI tools: look for '*select version manually*').

---

### Post by aapo4 on 2011-11-01
Oneiric (11.10) version released:

[http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/)

---

### Post by wolneykien on 2012-02-15
Hi!

I've written a small utility  that dynamically rotates the coordinate system of an XInput device  monitoring the screen (output) orientation: 

  [http://github.com/wolneykien/xrandr-align]("https://github.com/wolneykien/xrandr-align") 

May be you will find it interesting. If so, advertise it a little. Thanks.

---

### Post by aapo4 on 2012-02-17
> **wolneykien said:**
> Hi!
utility  that dynamically rotates the coordinate system of an XInput device  monitoring the screen (output) orientation: 

Sounds good. How it is used? 

I can see that ALT Linux is already packed it:
[http://sisyphus.ru/en/srpm/Sisyphus/xrandr-align](http://sisyphus.ru/en/srpm/Sisyphus/xrandr-align)

I get it compiled on Ubuntu:
git clone [https://github.com/wolneykien/xrandr-align.git](https://github.com/wolneykien/xrandr-align.git)
apt-get install xutils-dev
./autogen.sh
./configure
make

When compiled, it produces 'xrandr-align' -binary. Then what?

Does upstream (xrandr) know about it? Seems to me that xrandr-align contains code from xrandr, but is not replacing it, but they are used together?

---

### Post by wolneykien on 2012-02-22
> **aapo4 said:**
> 
Sounds good. How it is used? 


  Run

  *xrandr-align monitor --input="My touchpad device"*

  and your touchpad will be rotated follow after screen rotations. It stays in the foreground listening for RandR events. To see the proper name of the input device use

  [I]xrandr-align list-input
[/I] 
  New version supports the complement procedure too: it can rotate the screen follow the device rotations reported by a gravisensor (accelerometer) input device (can be found in some modern tablets).

  In the new version there are scripts and desktop files to start the tools automatically. See the README file and manual pages for more information.

> **aapo4 said:**
> 
I can see that ALT Linux is already packed it:
[http://sisyphus.ru/en/srpm/Sisyphus/xrandr-align](http://sisyphus.ru/en/srpm/Sisyphus/xrandr-align)


Yep, I'm working on it there.

> **aapo4 said:**
> 
I get it compiled on Ubuntu:
git clone [https://github.com/wolneykien/xrandr-align.git](https://github.com/wolneykien/xrandr-align.git)
apt-get install xutils-dev
./autogen.sh
./configure
make


Good to hear that it builds fine. :)

> **aapo4 said:**
> 
When compiled, it produces 'xrandr-align' -binary. Then what?


Use it! :)

> **aapo4 said:**
> 
Does upstream (xrandr) know about it? Seems to me that xrandr-align contains code from xrandr, but is not replacing it, but they are used together?


I've post a message to the xorg-devel list: [http://lists.x.org/archives/xorg-devel/2012-February/029321.html](http://lists.x.org/archives/xorg-devel/2012-February/029321.html) . No answer yet. Shouldn't I mail some people directly?

Yes, it uses some code from xinput and xrandr as mentioned in the copyright and authorship messages.

---

### Post by aapo4 on 2012-02-24
> **wolneykien said:**
> 
Yes, it uses some code from xinput and xrandr

Could functionality of xrandr-align be merged to the xrandr? Then monitoring step can be skipped.

So it would be used something like this:
xrandr list-input
xrandr add --input="My touchpad device" #this writes to config file
xrandr -o left #rotates screen and check devices for config file

And then there can be permanent config files and files which are cleaned on boot.

---

### Post by wolneykien on 2012-02-24
> **aapo4 said:**
> Could functionality of xrandr-align be merged to the xrandr? Then monitoring step can be skipped.

So it would be used something like this:
xrandr list-input
xrandr add --input="My touchpad device" #this writes to config file
xrandr -o left #rotates screen and check devices for config file

And then there can be permanent config files and files which are cleaned on boot.

  Is the `xrandr' the only program that can be used to interfacing with the RandR extension? Potentially, there may be various desktop applets for that purpose. Moreover, the touchscreen devices (aka tablet PCs) would have other means to automatically rotate the screen when the device itself is rotated. Thus, I see the "third-party monitoring" approach as relatively universal.

  Support for configuration files is already added in version 0.3.2. ;)

---

### Post by aapo4 on 2012-05-15
Precise (12.04) version released:

[http://cc.oulu.fi/~rantalai/synaptics/](http://cc.oulu.fi/~rantalai/synaptics/)

---

