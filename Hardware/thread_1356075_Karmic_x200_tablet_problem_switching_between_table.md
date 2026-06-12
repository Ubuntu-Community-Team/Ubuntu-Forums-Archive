---
title: "Karmic: x200 tablet problem switching between tablet mode and back kills stylus"
date: 2009-12-15
forum: Hardware
---

### Post by bungjamu on 2009-12-15
Hello,
I'm having problem with the tablet function when switching from normal laptop mode to tablet mode (monitor flipped and folded) and back.  I'm using Karmic on a Lenovo x200 tablet with 'Enhanced multitouch' (Lenovo's term to differentiate "multitouch: pen and one point touch" and "enhanced multitouch: pen and two points touch").

I used the the solution by rec and favux [[link]]("http://ubuntuforums.org/showthread.php?t=1122952&page=2") which was summarized in this blog: [[link]]("http://www.shrapnull.com/v1/node/22").

After doing all the steps, and rebooted, the feature works for a while.  I re-oriented to tablet mode, and the stylus reorients itself to portrait - works great.  But immediately after that, after i re-oriented to normal, the stylus just stopped working altogether.  I had to reboot to get it to work again, but switching to tablet mode and back still kills the stylus.

Also, in the solution it mentioned of three types of input: stylus, touch, and eraser.  I did:
```
$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"ThinkPad Extra Buttons"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"UVC Camera (17ef:480c)"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PnP Device (WACf00c)"	id=7	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26312
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16520
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Video Bus"	id=8	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"PnP Device (WACf00c) eraser"	id=9	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26312
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16520
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"TPPS/2 IBM TrackPoint"	id=10	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Macintosh mouse button emulation"	id=11	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```
and there are only 'stylus' and 'eraser', but no 'touch'.  (Note: I think the "Wacom Stylus" and "Wacom Eraser" entries are from after I implemented rec's script.)

gali98 suggested editing the .fdi file in this solution: [[link]]("http://ubuntuforums.org/showthread.php?t=1038949&page=11") (which is an extension to rec & favux's solution).  I tried the same script gali98 provided, but then the stylus doesn't work altogether.  I had to revert back to the original .fdi file to get it to work back.

I tried to install the newest linuxwacom driver: [[link]]("http://linuxwacom.sourceforge.net/index.php/dl") linuxwacom-0.8.5-6, but it failed in $ make with a bunch of errors:
```
$ make

*** snipped ***

/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../src/include    -Wall -pedantic  -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c -o wacomcfg.lo wacomcfg.c
 gcc -DHAVE_CONFIG_H -I. -I../../src/include -Wall -pedantic -g -O2 -D__amd64__ -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o
In file included from wacomcfg.c:36:
wacomcfg.h:26:22: error: X11/Xlib.h: No such file or directory
wacomcfg.h:27:35: error: X11/extensions/XInput.h: No such file or directory
wacomcfg.h:28:36: error: X11/extensions/XIproto.h: No such file or directory
In file included from wacomcfg.c:36:
wacomcfg.h:58: error: expected specifier-qualifier-list before &#8216;Display&#8217;
wacomcfg.h:62: warning: struct has no members
wacomcfg.h:67: error: expected specifier-qualifier-list before &#8216;XDevice&#8217;
wacomcfg.h:75: error: expected &#8216;)&#8217; before &#8216;*&#8217; token

*** snipped ***

make: *** [all-recursive] Error 1
```

I'm really feeling out of luck and ideas right now.  I'm quite a newbie at Linux.  I hope someone could help me.  The reason I got the x200 is to be able to use the tablet mode to work in Gimp & edit my thesis (I find reading and writing papers are much more convenient in portrait...).

Thanks in advance,
M

---

### Post by Favux on 2009-12-15
Hi bungjamu,

Welcome to Ubuntu Forums!

The good news is that things are changing so fast with linuxwacom, that if we can't get touch working right now, we probably will be able to within a few weeks.

Your X200t is so new that it is not supported by the default linuxwacom (0.8.4-1) in Karmic.  In linuxwacom 0.8.5-5:
> Updated serial ISDv4 support with newer protocol.
and with 0.8.5-6:
> Support new serial Tablet PCs.
Which probably includes yours.

So you were right, for touch (and maybe stylus?) you want linuxwacom 0.8.5-6.  I have to warn you that right now the xsetwacom rotate commands aren't working correctly with it, at least on my system.  That may not be true of yours in Karmic.

Another problem is that there seems to be a bug in 64-bit Karmic for serial tablets, but things seem to work fine with 32-bit installs.  Which do you have?  Some have reported restarting X fixes things for them.  A few have reported the latest updates have fixed it.

Regarding doing the linuxwacom compile and install it looks like you don't have libx11-dev installed. It should place Xlib.h in "/usr/include/X11/Xlib.h".  And several other dependencies.  If you followed this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1"), this command should have installed them:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

```
Attached to the bottom of the same HOW TO are two .fdi's you could use, either the serial tablet one or the new-generic rc1.  Instructions in Section 2 b).  With the serial table pc .fdi you'll need to add 'WACf00c' to the identifiers.  With them you do not need rec's script and should remove it.  Besides from your xinput it doesn't seem to be working anyway.

Yours is a serial tablet pc, which is why gali98's .fdi didn't work for you.

Hope this is helpful.

---

### Post by bungjamu on 2009-12-15
Thanks, Favux, you're a great help!

A little report on my experience with this fix.
- with that X11 components installed, I was able to install the linuxwacom-0.8.5-6 driver.
- the driver detected the touch interface, so now I have touch input! yay!
- I tried the two .fdi, and you're right, it seems to work better with the serial one (Favux_serial-tablet-pc1_10-wacom.fdi.txt).  I used it to replace the 10-linuxwacom.fdi with some modifications.  Your original was (with your note to add 'WACf00c' as an identifier):
```
<?xml version="1.0" encoding="ISO-8859-1"?>

<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf00c;WACf008;WACf009;FUJ02e5">
	<append key="info.capabilities" type="strlist">input</append>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
	<merge key="input.device" type="copy_property">serial.device</merge>
	  <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	  <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf00c;WACf008;WACf009">
	  <!-- Serial tablets with touch capabilities -->
	  <append key="wacom.types" type="strlist">touch</append>
	</match>
        <match key="@info.parent:pnp.id" contains_outof="WACf008">
          <!-- Serial tablets that operate at higher baud rate -->
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
       </match>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="touch">
      <merge key="info.product" type="string">touch</merge>
    </match>
  </device>
</deviceinfo>


```
- It works fine that it keeps the stylus alive after switching to tablet mode and back, but the only recognized devices are only 'touch' and 'eraser'.  So tried to tweak it a bit to:
```
<?xml version="1.0" encoding="ISO-8859-1"?>

<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf00c;WACf008;WACf009;FUJ02e5">
	<append key="info.capabilities" type="strlist">input</append>
	<merge key="input.x11_driver" type="string">wacom</merge>
	<merge key="input.x11_options.Type" type="string">stylus</merge>
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
	<merge key="input.device" type="copy_property">serial.device</merge>
	  <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
	  <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf00c;WACf008;WACf009">
	  <!-- Serial tablets with touch capabilities -->
	  <append key="wacom.types" type="strlist">touch</append>
	</match>
        <match key="@info.parent:pnp.id" contains_outof="WACf00c;WACf008;WACf009">
          <!-- Serial tablets that operate at higher baud rate -->
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
       </match>
      </match>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="stylus">
      <merge key="info.product" type="string">stylus</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="touch">
      <merge key="info.product" type="string">touch</merge>
    </match>
  </device>
</deviceinfo>


```
- And now it registers all three 'stylus', 'touch' and 'eraser'.
- You're right about the warning... xsetwacom set ..rotate didn't work well.  I'm guessing it's just a simple orientation fix in the code?  Two things I noticed:
   1. after the display rotated when in tablet mode, with the stylus or touch, the cursor moves relative to landscape mode.   So the control is not rotated along with my display (my display's rotated clockwise in tablet mode).  Even after doing xsetwacom rotate.  The trackpoint works fine, fyi.  I tried:
```
xsetwacom set stylus rotate cw
xsetwacom set stylus rotate ccw
```
I also tried with replacing 'stylus' with 'touch'
   2. doing the xsetwacom rotate command also displaces the pen tip/fingertip with the cursor by a wide margin.  Recalibrating with '$wacomcpl' works sometimes.

I have to go for now, but I'll let you know if there's any other thing that occurred to me.

Thank you again for your great help!
M

---

### Post by Favux on 2009-12-15
Hi bungjamu,

Great!  Nice work.  You're welcome.

The stylus part is my goof.  I left out a line, I'm not sure how.  :(

I'm not sure from what you posted that your tablet needs the higher baud rate.  Could you please test the attached .fdi and see if it works for you?  I'd appreciate it.  If you need to add your tablet to the higher baud rate let me know.

Unfortunately you're seeing what I'm seeing with rotation.  The rotation problem seems to be a code error in linuxwacom, starting with 0.8.5-4.  Right now they are adding a ton of new devices, trying to get it to work with Xserver 1.7, and syncing with the Xorg xf86-input-wacom driver.  Linuxwacom is the last big input driver to be brought into Xorg.

---

### Post by bungjamu on 2009-12-16
Glad to know it's being worked on :)  Thank goodness for community.

Your new .fdi works great!  In addition - this is something I didn't expect, and if you didn't intend this, you should open up a bottle of good wine and celebrate: two finger gestures are being recognized.  I can scroll this page, resize the fonts using two-finger swipes and pinching, respectively.  I can even use the swipe to scroll in the terminal.  What's weird, though, I was able to scroll the page using the finger gesture in Chrome Beta in Karmic, but not in Chrome in Win 7 (maybe because it's not Beta).

Switching back and forth, to and from tablet mode keeps the touch/stylus functions alive.  In addition, there is no noticable displacements between the finger/stylus tip when switching back to normal (landscape) mode.  While rotated, orientation is still  not working, but multitouch works.  No finger gestures/touch in Gimp, though, although the Edit>Preferences>Extended Input Device is set that 'touch' is enabled to 'screen'.

Quite frankly, when I edited the .fdi file, I didn't know what I was doing...I guess I don't need the high baudrate for the tablet.  What is the current baudrate is for? 

Thanks again, Favux!  Your help is much appreciated!  Now I'm just waiting for the orientation fix, and I'm all set!
M :popcorn:

---

### Post by Favux on 2009-12-16
Hi bungjamu,

Outstanding!  We've also gotten some multi-touch gestures working with the new Bamboo P & T's (those required patches to linuxwacom).  The dev.s have been adding gestures to the 0.8.5 series, esp. the last couple versions.

The default baud rate is 9600.  Glad you confirmed that the WACf00c operates at that rate.  Best of all now I can update the .fdi with some confidence due to your feedback.

I also hope for quick repair of the rotation stuff as I would like to move up to the 0.8.5 series full time.  By the way, what rotation script are you using for rotation?

---

### Post by bungjamu on 2009-12-16
Hi Favux,

For the rotation, I used the script from here:
[http://www.shrapnull.com/v1/node/22]("http://www.shrapnull.com/v1/node/22")

*update: two finger gestures works in viewing images, but: 1) up/down swipes registered like pinching in/out as zoom-out/zoom-in, respectively instead of panning (left-right swipes works as panning) 2) unfortunately no rotating features yet.

M

---

### Post by Favux on 2009-12-16
Hi M,

OK, unless I'm misreading the script he has for acpi you need to add xsetwacom rotate commands for eraser and touch.  See the method 1 scripts on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  By the way method 1 and 3 should work for you.

---

### Post by bungjamu on 2009-12-18
Hi Favux,

Sorry I got busy and couldn't reply to your post sooner.  

I tried the script from method 1, and it works.  When I double-click the .sh file, the screen rotated, each time for 90 degrees - of course still with the same orientation problem of the pointer with respect to the stylus, eraser, and touch as before.  I haven't tried method 3 - frankly, I'm a bit cautious of installing things like that, because if it breaks, i don't really know how to revert back to a working state.

Yes, I have to double check if I added the 'eraser' and 'touch' to acpi script.  Thanks for pointing that out. :)

M

---

### Post by Favux on 2009-12-23
Hi bungjamu and everyone,

**[SIZE="2"]Breaking News:[/SIZE]**  A holiday present from Ping Cheng at the LWP.  :D

Linuxwacom 0.8.5-8 has been released!!!  Rotation is fixed!

There is a little quirk with touch, at least on my tablet.  It's a little misaligned on rotation and the cursor jumps several cm.s when the finger is lifted.  But it hops right back when you touch the tablet again.  It's being looked at.

I'm interested in hearing if it works for you.  See the linuxwacom [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by bungjamu on 2009-12-28
Hi Favux,

Thanks!  The rotation works well after installing linuxwacom-0.8.5-8.  Now the stylus is oriented correctly when the screen is rotated using the .sh script you suggested.
I do have some problem:
1. now i lost the touch / eraser.  Only stylus is detected in 'xinput --list' and 'xsetwacom list'.  I tried adding the WACf### in the .fdi file, but it didn't work.  I followed the HOWTO only for those stuff related to Karmic, and tried the .fdi file for the serial tablet pc, and the generic one.  I must've goofed somewhere along the way.
2. I was using Gimp, and after rotating the screen mutliple times (i.e. > 360 degrees), the pointer on the screen still follows the stylus, but the Gimp brush is way misaligned.  Maybe it's a Gimp issue -- I haven't tested it some more.  After I restarted Gimp, the stylus/Gimp brush are aligned again, though (in any orientation).

Thanks again, and happy holidays!
M

---

### Post by Favux on 2009-12-28
Hi bungjamu,

Great, rotation works for you too.

Either the .fdi on this thread or the two .fdi's at the bottom of the linuxwacom thread should work.  So my guess is you forgot in step 2):
```
sudo apt-get install libhal-dev
```
and so hal-setup-wacom wasn't built.  That means the info.callout in the .fdi's doesn't work so you can't append eraser and touch.  Does this look/sound right/possible?

---

### Post by bungjamu on 2009-12-28
Hmm... still doesn't work.  I tried retracing all the steps again including installing libhal-dev, and touch & eraser are still missing...

Does the ./configure look OK?

```

$ ./configure --enable-wacom --prefix=/usr

***snipped***
----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.27
  module versioning - no 
      kernel source - yes /lib/modules/2.6.31-16-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - hal IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------

```In Step 2 in the HOWTO there's a mention to do the following to clear the previous version:

```
sudo apt-get install wacom-tools xserver-xorg-input-wacom

sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```Does that need to be re-installed too?
Again, i tried using both the serial_tablet&tablet_PC and the generic .fdi's (this time without changing anything). :(

Just in case, this is my 'xinput --list' output:

```
$ xinput --list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"ThinkPad Extra Buttons"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"UVC Camera (17ef:480c)"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"stylus"    id=7    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 26312
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 16520
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Video Bus"    id=8    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"TPPS/2 IBM TrackPoint"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Macintosh mouse button emulation"    id=10    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
```And this is my current 10-linuxwacom.fdi:

```
<?xml version="1.0" encoding="ISO-8859-1"?>

<!-- Wacom Serial tablets and tablet pc's -->
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf;FUJ02e5;FUJ02e7">
    <append key="info.capabilities" type="strlist">input</append>
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
    <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
    <merge key="input.device" type="copy_property">serial.device</merge>
      <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
      <append key="wacom.types" type="strlist">eraser</append>
      <append key="wacom.types" type="strlist">cursor</append>
    <!-- Serial tablets with touch capabilities -->
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009;WACf010;WACf008A;WACf00B;WACf00C;WACf00D;WACf00E;FUJ02e7">
      <append key="wacom.types" type="strlist">touch</append>
    </match>
        <!-- Serial tablets that operate at higher baud rate -->
        <match key="@info.parent:pnp.id" contains_outof="WACf008">
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
        </match>
      </match>
    </match>
  </device>
  <!-- Wacom names "parser" -->
  <device>
    <match key="info.udi" contains_not="subdev_0">
    <match key="info.udi" contains_not="subdev_1">
    <match key="info.udi" contains_not="subdev_2">
      <match key="input.x11_options.Type" contains="stylus">
        <merge key="info.product" type="string">stylus</merge>
      </match>
      <match key="input.x11_options.Type" contains="eraser">
        <merge key="info.product" type="string">eraser</merge>
      </match>
      <match key="input.x11_options.Type" contains="cursor">
        <merge key="info.product" type="string">cursor</merge>
      </match>
      <match key="input.x11_options.Type" contains="touch">
        <merge key="info.product" type="string">touch</merge>
      </match>
    </match>
    </match>
    </match>
  </device>
</deviceinfo>

```M

---

### Post by Favux on 2009-12-28
Hi bungjamu,

Hmmm.  The .fdi looks ok so if you see stylus you should see the rest.

I'm not clear from what you said, did you do?:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom

sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```
Also check in Synaptic Package Manager and see if xserver-xorg-input-all is installed.

Depending on your answers I think we may need to look at your lshal:
```
lshal>bungjamu_lshal.txt
```
and Xorg.0.log in /var/log/.

---

### Post by bungjamu on 2009-12-28
Hi, Favux,

finally i got it to work.  So, you're right, i didn't have xserver-xorg-input-all installed.  Sure enough, not all of my wacom inputs were listed.  And so i installed that, but it didn't work immediately after rebooting.  I had to use the .fdi file you posted in this thread to get touch and eraser registered and working.  For some reason, the serial&tablet_pc and generic .fdi files in the HOWTO didn't work well for me.

And like you said, touch is still a bit quirky: the cursor is in place where the finger touches the screen, and jumps away in the opposite relative position where the finger was last (e.g. if i touch the bottom right of the screen, the cursor will be there.  if i lift my finger off the screen from that position, the cursor jumps to the top left of the screen).  i find it difficult to click using touch, although dragging windows and scrolling using two fingers seem to work fine.  i tried calibrating the touch using:
```
wacomcpl
```At the end of the calibration, i got this warning message:
```
There was something unusual in your calibration step.  
If you are pretty sure that you have clicked on the center of the pink crosshair, you are fine.  
Otherwise, try it again.
```Also, touch is a bit sensitive.  I'm typing this reply in tablet mode, and typed using onboard (the virtual keyboard).  when i use finger, the letters will be typed twice.... so i'm tapping along using the stylus here..

Other than that, everything else seems to work fine.  Can't wait to start doodling in Gimp :)

Thank you so much, again!
M

update: apparently, dragging windows by touch sometimes has the similar 'jumping around' issue with regular click/touch.

---

### Post by bungjamu on 2009-12-28
> **Favux said:**
> 

I'm not clear from what you said, did you do?:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom

sudo apt-get purge wacom-tools xserver-xorg-input-wacom
```Sorry, forgot to respond to your question.  So, yeah, i did both commands in that order. i assumed the second line uninstalled both wacom-tools and xserver-xorg-input-wacom.  That's why i asked if i should install them back after installing the linuxwacom driver since the whole thing didn't work before.

Per your suggestion, i installed xserver-xorg-input-all, which also installed xserver-xorg-input-wacom through Synaptics.  So now it's working, save for those quirks i mentioned in my last post.

M

---

### Post by Favux on 2009-12-28
Hi bungjamu,

Good!  :)

> i didn't have xserver-xorg-input-all installed. Sure enough, not all of my wacom inputs were listed. And so i installed that, but it didn't work immediately after rebooting. I had to use the .fdi file you posted in this thread to get touch and eraser registered and working. For some reason, the serial&tablet_pc and generic .fdi files in the HOWTO didn't work well for me.
Thanks again for looking at this.  I confirms I need to update the HOW TO for Karmic.  In Karmic there seems to be a new dependency with xserver-xorg-input-all.  Apparently what happens is the purge line removes it, which in my opinion it shouldn't.

Probably what is going on with the .fdi's is the new wacom.ko broke the old kernel module dependencies and the reboots rebuilt it.  If you had done:
```
depmod -a
```
to rebuild all of the module dependencies the other .fdi's would have worked, if not right away, sooner.  I'd appreciate it if you tested one and see if it now works for you.

> And like you said, touch is still a bit quirky: the cursor is in place where the finger touches the screen, and jumps away in the opposite relative position where the finger was last (e.g. if i touch the bottom right of the screen, the cursor will be there. if i lift my finger off the screen from that position, the cursor jumps to the top left of the screen).
Same as I am seeing.
> i find it difficult to click using touch
I'll have to check that for me.
> Also, touch is a bit sensitive. I'm typing this reply in tablet mode, and typed using onboard (the virtual keyboard). when i use finger, the letters will be typed twice.... so i'm tapping along using the stylus here..
Oops!  I forgot to check that with my onscreen keyboard.  I use CellWriter which does letter recognition.  Try it, I think you'll like it better than OnBoard.

That's the same warning message I get when trying to calibrate rotated.

Ping's swamped right now and has backed off on his offer to straighted it out right away.  I'm suppose to report the issue on the tracker and they'll get to it when they can.  Hopefully not too long.  So it's helpful that I have your experience too to use in writing the report.  And you've given me a good excuse for procrastinating!  :wink:

Edit:
> Per your suggestion, i installed xserver-xorg-input-all, which also installed xserver-xorg-input-wacom through Synaptics. So now it's working, save for those quirks i mentioned in my last post.
Glad you told me that.  See that could be a problem.  Will it cause version conflict?  How did it manage that without knocking out the 0.8.5-8 that supports your X200t.  The Package Manager somehow recognized the newer version?  I'm back to not understanding what's going on and am stuck again.  Darn.

---

### Post by Favux on 2009-12-28
I wonder if this would serve in Karmic:
```
sudo apt-get install wacom-tools xserver-xorg-input-wacom

sudo apt-get purge wacom-tools

sudo apt-get remove xserver-xorg-input-wacom
```
Would this clear up any of the problems you are seeing?  And not remove xserver-xorg-input-all?

Edit:  Never mind.  Remove results in it wanting to uninstall xserver-xorg-input-all also.

---

### Post by bungjamu on 2010-01-25
Hi Favux,

sorry I haven't been able to respond to your last post in a long time.  It's been a very busy month.  I'll have to check your suggested solutions sometime soon.

Thanks so much for your help, again!

M

---

### Post by han_sol0 on 2010-02-07
Hi Favux, bungjamu,

thanks to your efforts I am able to use the stylus in karmic on x200 tablet.

However, i noticed that there is high latency when drawing with the stylus in gimp (e.g. a growing offset between the actual point I am poking at with the stylus and the line that is being drawn, this increases with the speed the stylus is moved).
In order to fix this I also tried different baudrates which didnt change anything (currently iam back at 9600).
Then i thought there might be a x11_options attribute which controls the latency or similar but couldnt find a fitting switch.

In the end I installed setserial to set /dev/ttyS0 to low_latency, which works.

Hence, i have added
"setserial /dev/ttyS0 low_latency" to /etc/rc.local.
Only drawback is a increased cpu load when using stylus.

Regards..

---

### Post by Favux on 2010-02-07
Hi han_sol0,

Welcome to Ubuntu forums!

Nice work!  Thank you for the tip.  It should help others.

Did you have to install "setserial /dev/ttyS0 low_latency" to "/etc/rc.local" or does it also work in "/etc/serial.conf"?

---

### Post by bungjamu on 2010-02-07
Hi han_sol0,

I also noticed that while Karmic is smart enough to disable finger-touch while the stylus is used (i.e. on or close to the screen), resting my hand on the screen while drawing or writing (on GIMP or Xournal) causes a significant lag like you described.  Just FYI i guess.

Hi Favux,

Sorry I couldn't respond to you sooner.  Has there been a fix for the touch while in rotated/tablet mode?  In normal mode the touch works well.

---

### Post by Favux on 2010-02-07
Hi bungjamu,

Not yet.  I posted a bug report on the tracker like Ping Cheng asked me to.  So far no response.  But they are messing with the touch logic to get the new Bamboo Pen and Touch supported.  Hopefully they'll end up fixing touch for us while they are at it.  We'll just have to see how 0.8.5-10 is.  Due out any day now.

---

### Post by bungjamu on 2010-02-07
Alright.
Thanks a lot, Favux!

---

### Post by SaintDanBert on 2010-02-09
There have been "iss-ues" surrounding anything "tablet" and "anything 3D-desktop" playing nicely together. [highlight] Tablet [/highlight] wants to play games with X-versus-Y during screen orientation changes.
[highlight] 3D-desktop [/highlight] uses X-Y(-Z) and who knows what else to layer and create composite images. [highlight] Tablet [/highlight] plays all sorts of pointer (mouse, finger, stylus) games. [highlight] 3D-desktop [/highlight] has to sift pointer anything through all of the composite X-Y(-Z) to know who touched what ... and so on.

I **try to ** run Ubuntu on a Thinkpad X61-tablet -- the X200's older brother. I found that [highlight] Tablet [/highlight] worked much better in general if I turned off everything 3D-desktop through the gnome control panel.

Is there any chance that you would private message (PM) or otherwise help me discover how to get Karmic working better on my Thinkpad X61-tablet by sharing some of your configuration details or links to whatever you used for guidance?

Thanks,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-02-09
How do I discover which "linux wacom" and related parts (1) that I have installed, and (2) the parts that I need to update and build and install?

My **Thinkpad X61-Tablet** reports the following. I can provide other details if you tell me what is needed.

```

user@host$ sudo xinput list

"Virtual core pointer"	id=0	[XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
	Max_value is -1
	Resolution is 0
    Axis 1 :
        Min_value is -1
	Max_value is -1
	Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"	id=2	[XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Sleep Button"	id=3	[XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"	id=4	[XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer"	id=5	[XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
	Max_value is 24576
	Resolution is 2540
    Axis 1 :
        Min_value is 0
	Max_value is 18432
	Resolution is 2540
    Axis 2 :
        Min_value is 0
	Max_value is 255
	Resolution is 1
    Axis 3 :
        Min_value is -64
	Max_value is 63
	Resolution is 1
    Axis 4 :
	Min_value is -64
	Max_value is 63
	Resolution is 1
    Axis 5 :
	Min_value is 0
    	Max_value is 1023
	Resolution is 1
"AT Translated Set 2 keyboard"	id=6	[XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"	id=7	[XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
	Min_value is 0
	Max_value is 24576
	Resolution is 2540
    Axis 1 :
	Min_value is 0
	Max_value is 18432
	Resolution is 2540
    Axis 2 :
	Min_value is 0
	Max_value is 255
	Resolution is 1
    Axis 3 :
	Min_value is -64
	Max_value is 63
	Resolution is 1
    Axis 4 :
	Min_value is -64
	Max_value is 63
	Resolution is 1
    Axis 5 :
	Min_value is 0
	Max_value is 1023
	Resolution is 1
"ThinkPad Extra Buttons"	id=8	[XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"TPPS/2 IBM TrackPoint"	id=9	[XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
	Min_value is -1
	Max_value is -1
	Resolution is 1
    Axis 1 :
	Min_value is -1
	Max_value is -1
	Resolution is 1
"Macintosh mouse button emulation"	id=10	[XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
	Min_value is -1
	Max_value is -1
	Resolution is 1
    Axis 1 :
	Min_value is -1
	Max_value is -1
	Resolution is 1
user@host$ 

```

```

user@host$ sudo xsetpointer -l

0: "Virtual core pointer"       [XPointer]
1: "Virtual core keyboard"      [XKeyboard]
2: "Wacom Serial Tablet PC Pen Tablet/Digitizer"        [XExtensionKeyboard]
3: "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser" [XExtensionKeyboard]
4: "ThinkPad Extra Buttons"     [XExtensionKeyboard]
5: "AT Translated Set 2 keyboard"       [XExtensionKeyboard]
6: "Sleep Button"       [XExtensionKeyboard]
7: "Video Bus"  [XExtensionKeyboard]
8: "Power Button"       [XExtensionKeyboard]
9: "TPPS/2 IBM TrackPoint"      [XExtensionPointer]
10: "Macintosh mouse button emulation"  [XExtensionPointer]
user@host$ 

```

Please help!? I'm really having a rough time here.
~~~ 8d;-/ Dan

---

### Post by Favux on 2010-02-09
Hi SaintDanBert,

Your xinput shows the default linuxwacom 0.8.4-1 and wacom.fdi in Karmic is recognizing your stylus and eraser.  Do you have touch?

See "Jaunty and Karmic Users" near the top of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  It discusses several options and either of the two attached .fdi's should work for you.  Then you can use wacomcpl as described in Section 3.

The Thinkwiki is always a good source:  [http://www.thinkwiki.org/wiki/Category:X61_Tablet](http://www.thinkwiki.org/wiki/Category:X61_Tablet)

And for Karmic specific info.:  [https://help.ubuntu.com/community/X61T](https://help.ubuntu.com/community/X61T)

Hopefully that will get you set up.

---

### Post by Favux on 2010-02-12
Hi bungjamu,

Linuxwacom 0.8.5-10 is out.

In my testing it hasn't fixed the touch problem when rotated.  I can't see a change.  I'm very interested in your feedback on that.  I'll be testing it a little more.

---

### Post by SaintDanBert on 2010-02-13
> **Favux said:**
> 
...
See "Jaunty and Karmic Users" near the top of this HOWTO [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1).  It discusses several options and either of the two attached .fdi's should work for you.  Then you can use wacomcpl as described in Section 3.
...


When I run [highlight]wacomcpl[/highlight] it does not see any device to select. I read somewhere that the automatic names from *hal* or *udev* don't match what **wacomcpl** expects. Any idea how to sort this out?

Has anyone discovered the Karmic dance that results in whatever it is that X11 needs for configuration?

> 
...
The Thinkwiki is always a good source:  [http://www.thinkwiki.org/wiki/Category:X61_Tablet](http://www.thinkwiki.org/wiki/Category:X61_Tablet)

And for Karmic specific info.:  [https://help.ubuntu.com/community/X61T](https://help.ubuntu.com/community/X61T)
...

Likely it is just me, but I don't find much at ThinkWiki that is useful. I suspect that I don't understand enough ... yet ... to sort the good stuff from the noise.

I always appreciate web links either they are useful or they lead me somewhere that is.

~~~ 0;-Dan

PS/  I'd still like to get the **sysinfo** output for an X200-tablet so that I might compare with my X61-tablet. Anyone?

---

### Post by Favux on 2010-02-13
Hi SaintDanBert,

Sure, that's what the link you quoted is for.  It shows you seveeral ways to fix things so wacomcpl and tablet rotation works including different wacom.fdi's.

.fdi = device information file

See the linuxwacom HOW TO:  [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)

---

### Post by SaintDanBert on 2010-02-13
Sorry to be dense but I'm missing something on the pages we're discussing.

Am I supposed to create the FDI file then restart X11 -- what used to be CTRL-ALT-BACKSPACE?

If that does not work, how do I back out?  Where will I find the error logs to fix what does not work?

Thanks,
~~~ 8d;-/ Dan

---

### Post by Favux on 2010-02-13
Not a problem.  The instructions are in Section 2 b).  You back up your current default 10-linuxwacom.fdi file and replace it with one of the modified ones so wacomcpl works for you.  If you don't like it you can restore from back up.  Or you can use one of the other options like rec's script.

You have to enable ctrl-alt-backspace in Karmic.  It was disabled on purpose upstream (not by Ubuntu) to prevent you from accidentally restarting X.  So just reboot after you change the .fdi.

Xorg.0.log in /var/log is usually a good place to start.

---

### Post by bungjamu on 2010-03-10
Hi Favux,

Sorry for not responding for a long time; it's been a crazy term.

I finally tried the linuxwacom-0.8.5-10, here's my experience with it so far:
- i can only get everything (stylus, eraser, and touch) using the .fdi you provided in this thread (it's in page 1).  I tried the .fdi from the HOWTO page to no avail.

- multitouch works, with some catch.  i like the second-touch-as-right-click feature.  however, scrolling pages with two-finger touch is hit-and-miss; most of the time it'll just go and select (highlight) texts on the page and won't scroll.  i might say it's worse than the previous one - but i have to double-check that ;p

- typing (i'm typing this on Cellwriter) seems to work well even in rotated (portrait) mode.  that said, single and double clicks works well for the most part.  The catch is, the cursor still jumps around after you lift your finger off the screen. [s]Unlike last time where it's somewhat related to the screen orientation, this time it seems rather random.[/s]  It's still related to the screen orientation:
   - when rotated to the right (top of desktop on the right side): tapping on the screen's top side, when the finger is lifted the cursor is on the right side of the screen (although, only near the center of the screen, slightly over to the right), bottom --> left (edge), left --> top, right --> bottom.
   - when rotated upside-down (landscape), everything's the opposite: top-->bottom, bottom-->top, left-->right, right-->left.
   - when rotated to the left: top-->left, left-->bottom, bottom-->right, right-->top
  There's also seem to be some offset issues when rotated to the right/left... the area where the cursor lands after release is smaller than the screen.  However, the touch basic functions like tap (click) and double-tap (double-click) works.

so i guess i pretty much agree with your experience: it's hasn't quite addressed some of the issues in the 0.8.5-8 version ... i think.

- Bungjamu

UPDATE:  I forgot to mention.  I tried to configure Touch using wacomcpl.  After tapping at the two calibration boxes, a message box appears saying: "There's something wrong with the configuration.  But if you think it's working fine, ignore this message, otherwise try again." - or something on that note (I forgot the exact message).  Well, after that, the Touch input goes wonky: the cursor doesn't appear where i tap on the screen, but somewhere else.  Logging out and back in seemed to fix this.

---

