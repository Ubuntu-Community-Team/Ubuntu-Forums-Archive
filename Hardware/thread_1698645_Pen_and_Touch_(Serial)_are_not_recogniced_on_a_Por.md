---
title: "Pen and Touch (Serial) are not recogniced on a Portege M700 anymore"
date: 2011-03-02
forum: Hardware
---

### Post by BackBONE7 on 2011-03-02
Hi,

i was hoping to present a solution at the time i am writing this, but it gone from bad to worse.

I have a Toshiba Portege M700 and had Ubuntu Studio on it but switched later to Ubuntu Lucid. The Problem was Pen Behaviour. (Thread [here )]("http://ubuntuforums.org/showthread.php?t=1533776")

So,  after a couple of updates, things where strange again. Sometimes the  Pen and Touch wasn't working at all, but jumped back to live after a  couple of reboots. A few reboots later they where dead again.
I figured out that, for unknown reasons, my system started to switch the device-id's randomly at start up.
The solution was simple, to use the device name instead of the id number in the script Favux wrote for me. (thanks again for that! )

So far so good. Now i updated xf86-input-wacom witch  converted my nice Tablet PC into an ordinary Laptop. Pen nor Touch is  working. Apparently the devices are not recognized anymore. I guess it  is because they are both serial devices. Probably they are no longer  supported, again. After some googling, i just found rather old threads  from 2008, about compiling a path to make this working again.

Then  i thought , why not just reinstall the older version. So i did, first  0.10.9 then 0.10.8 and so on, i stopped at version 0.10.6. Without any  success.

This makes me believe that the device recognition is not done by xf86-input-wacom, and that another component need to be altered to get rid of this problem. Any hints on that would be great.

Also, is there maybe a up to date patch that could be used?

Thank's in advance.

    BackBONE

---

### Post by Favux on 2011-03-02
Hi BackBONE7,

> i updated xf86-input-wacom witch converted my nice Tablet PC into an ordinary Laptop. Pen nor Touch is working. Apparently the devices are not recognized anymore.
That brings a couple of thoughts to mind.  Maybe the wacom.conf got changed and isn't matching anymore?  Post your wacom.conf.  Are you still in Lucid or now in Maverick?
For Lucid:
```
/usr/lib/X11/xorg.conf.d/10-wacom.conf
```
or Maverick:
```
/usr/share/X11/xorg.conf.d/50-wacom.conf
```
I forget, does the M700 have one or two finger touch?

---

### Post by BackBONE7 on 2011-03-02
Yep, I'm still at Lucid, but i don't have a wacom.conf.
Could this be the Problem?

I think even if the configuration is wrong, the device should show up with xinput list.
But all I get there is:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=10    [slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                      id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard                   id=11    [slave  keyboard (3)]
```So, i guess the problem is on a lower level.

---

### Post by Favux on 2011-03-02
In Lucid you should have a 10-wacom.conf that looks something like this:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7|FUJ02e9"
	Driver "wacom"
EndSection

Section "InputClass"
 	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
	Option "Button2" "3"
EndSection
```
Except I added the FUJ02e9.  Not sure how you lost it.  The Lucid location is non-standard and they updated the number to 50 and so xf86-input-wacom during the compile probably tried to install the 50-wacom.conf in /usr/share/X11/xorg.conf.d.

Anyway that's most likely the problem.  You haven't put any Wacom stuff in the xorg.conf or anywhere have you?

---

### Post by BackBONE7 on 2011-03-02
Yeah, your absolutly right!

I added the 10-wacom.conf, and the Tablet shows up on xinput list again. Touch works, but
has the jumps i had with the pen initaly, just a lot more frequent. The Pen moves the mouse somewhere out of the Screen. I think i need the right Product-Name.

I have no idea how to find it thou. (i bet its easy, if you know how ;))

Thank you for your help, i would be lost without you.

EDIT: 

I just found out that the Pen is actually working, but the mouse-cursor moves instantly to the lower-left-corner.
Example, if i click on the Desktop there is instantly a selection box, from where i clicked to the earlyer mentioned corner.
Right click works, but the contextmenu is always in the lower-left.
Touch does work, but do this weired selection box thing very often.

Any Ideas?

---

### Post by BackBONE7 on 2011-03-04
I did a little more research, and found a hint on a german Ubuntu Blog.

**which xsetwacom** gives you the location of the version used. They wrote there that there are two common locations **/usr/bin/xsetwacom** and** /usr/local/bin**.
The later location can mean that there is a version conflict. I have actually a xsetwacom file in both of these locations. I renamed the one in the local bin directory, simply to disarm it without loosing it. But the strange behaviour remain.

My next step would be to get rid of everything that has to do with wacom drivers, and tools, and attempt a more or less clean install of the latest version. I think just removing it with synaptics won't be good enough.

Any directions what else i have to do to make this happen?

---

### Post by Favux on 2011-03-04
Hi BackBONE7,

The duplicate xsetwacom issue is discussed in Troubleshooting in the Bamboo P&T HOW TO.

Before you remove your wacom stuff let's see what Xorg.0.log in /var/log is telling us.  Compress it by right clicking on it and choosing Create Archive and then attach it to your next post with Manage Attachments below.

The stylus is working after all.

Favux

---

### Post by BackBONE7 on 2011-03-04
O.K. the log file looks fine to me. My knowlege about this is very limited thou.
Maybe you find something else.

---

### Post by Favux on 2011-03-04
You are right, the Xorg.0.log looks good:
```
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.11
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Serial Wacom Tablet: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(II) Serial Wacom Tablet stylus: serial tablet id 0x93.
(--) Serial Wacom Tablet stylus: using pressure threshold of 27 for button 1
(--) Serial Wacom Tablet stylus: Wacom General ISDV4 tablet maxX=26112 maxY=16320 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) Serial Wacom Tablet stylus: hotplugging dependent devices.
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "38400"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet maxX=26112 maxY=16320 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=100000 resol Y=100000
(**) Option "BaudRate" "38400"
(**) Serial Wacom Tablet touch: always reports core events
(**) Option "Device" "/dev/ttyS0"
(**) Option "BaudRate" "38400"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(--) Serial Wacom Tablet touch: Wacom General ISDV4 tablet maxX=26112 maxY=16320 maxZ=127 resX=100000 resY=100000  tilt=disabled
(II) XINPUT: Adding extended input device "Serial Wacom Tablet touch" (type: TOUCH)
(--) Serial Wacom Tablet touch: top X=0 top Y=0 bottom X=4096 bottom Y=4096 resol X=10000 resol Y=10000
(II) Serial Wacom Tablet stylus: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet stylus" (type: STYLUS)
(--) Serial Wacom Tablet stylus: top X=0 top Y=0 bottom X=26112 bottom Y=16320 resol X=100000 resol Y=100000
```
So it looks like it is being placed on the Wacom X driver correctly.  Usually when the X server isn't getting any input from an X driver (wacom in this case) the pointer arrow goes to the left upper corner.

What I'm saying is something may have been broken for serial tablet PCs in xf86-input-wacom recently, i.e. a bug.  I've got another serial tablet PC reporting problems, but I'm not sure they are the same.  You're using 0.10.11 from the Xorg.0.log.  Was that from the tar or did you clone the git repostitory?

Let's see what:
```
xinput list
and
xsetwacom list
```
shows us.

---

### Post by BackBONE7 on 2011-03-04
xinput list
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=10    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch                   id=12    [slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                      id=15    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard                   id=14    [slave  keyboard (3)]

```xsetwacom list
```

Serial Wacom Tablet eraser          id: 11    type: ERASER    
Serial Wacom Tablet touch           id: 12    type: TOUCH     
Serial Wacom Tablet stylus          id: 13    type: STYLUS

```I changed a few parameters, but nothing i did helped in any way.
so... what do you think?

oh... i cloned the git at one time, and used the tar later. Maybe i made a mess with this over-installing.

---

### Post by BackBONE7 on 2011-03-05
Almost there! I digged a little deeper into the system and found out that i had a DKMS Patch installed parallel to the drivers from the tar. After I removed this Patch, both, Stylus and Touch are working as wanted (almost).
However the ButtonMapping changed, and Button2 don't exist any more. The Right click works, so i can work, but i have to hold the button and then tap onto the screen with the Stylus to get a response.
The Wacom-Control-Panel don't find any devices (i guess it only support usb-devices??)
So i have to figure out how to change the Tap-Right-Click to a Hover-Right-Click in a console.

This was the good news.... Now the bad one:

The extra Annoying Jumps of the Pen tip from my first-posts (link [here]("http://ubuntuforums.org/showthread.php?t=1533776")) remain the same.
This puts me back to square one.

I realy, realy ,realy have to get rid of this phenomenon, because i like to draw and do other cg stuff, and most of it is not possible cause i have to hit undo every two seconds.

Any help on this topic is extremly appreciated!

---

### Post by Favux on 2011-03-05
Nice work!

OK, some parameter names changed mainly starting with xf86-input-wacom 0.10.11.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom)

So Button2 is now Button 2, with the space.  So to make it a right click it would be Button 2 3, not Button2 3.  For hover you need the TabletPCButton parameter off.

For the jumps let's try using the RawSample parameter first.  
```
xsetwacom set "Serial Wacom Tablet stylus" RawSample 2
```
Its the data pt.s filtered, default is 2 with a range of 0-100.  Try slowly increasing it and see if the jumps improve.

The other parameter to try is Suppress.  That's the data pt.s trimmed, default is 4 and range 0-20.

You could also try Threshold which is the pressure needed to trigger a Button event, default is 27, range is 0-2047.  Try increasing it.

---

### Post by BackBONE7 on 2011-03-05
Than's for the tip! Hover works great.

The jumps seem to be independet from RawSample, Suppress and Threshold.
I even switched gestures off, and did a reset of the Tablet Area.

If there would be a filter that ignores events that are further away from the last cursor position as, lets say 30 to 80 Pixels, that might help. I downloaded the Source and thought maybe i can do a quick hack to test it, but i don't understand all of it, needles to say i'm not a good programmer.

I am sure there is a solution, i'm still frustraded thou.

---

### Post by Favux on 2011-03-05
Good, at least we've got hover working.

Supposedly ISDV4 devices (serial Tablet PCs) got added to the filter a couple of months ago.

If two things are true its time to post the issue on linuxwacom-discuss or the linux wacom project bug tracker: [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

One it's not a hardware issue because the stylus works fine in Windows.

Two there is no source of unshielded electromagnetic interference that might be causing this.

I suppose we could try running ToolDebugLevel for stylus or TabletDebugLevel and see what shows up in the Xorg.0.log during the jumps.  I think the range is 0-12 for both.

Huh, the irony.  cBusBrewGuy just said the latest xf86-input-wacom fixed the X41t stylus jitters:  [http://ubuntuforums.org/showthread.php?t=1662657](http://ubuntuforums.org/showthread.php?t=1662657)

Edit: fixed debug range.

---

### Post by BackBONE7 on 2011-03-06
Been there bevor with V 0.10.8. There where several reports that this would solve the issue, but didn't worked for me.

O.K. the last time i build the package from the tar-ball, so i thought maybe git will make any difference.
I removed the driver, and fired up git. After Autoconf, i noticed that my xorg-macros where not up to date, so i updated them and continued to compile.
But the juping remains unchanged.

Are there any other components that are involved with xf86-input-wacom that might be out of date?

---

### Post by BackBONE7 on 2011-03-08
O.K. I did some Tests with different debug-level-settings (files Attached) and found this for example:

(WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
(WW) Serial Wacom Tablet stylus: bad data at 7 v=91 l=9
(WW) Serial Wacom Tablet stylus: bad data at 8 v=91 l=9

But what does the last portion mean, is it a Adress or something?

The tar is containing 2 files, one with just ToolDebugLevel turned up, and the Second with both Debug Levels at maximum.

---

### Post by Favux on 2011-03-09
Chris Bagwell just made a patch that may fix things.  Are you interested in testing it?  They're still looking at an issue or two so this probably won't be the final form.  Do you know how to apply a git patch?

---

### Post by BackBONE7 on 2011-03-09
Yes, I'm intrested, but I never applied a git patch befor.

I found a nice tutorial [[link here]("http://www.vogella.de/articles/Git/article.html#firstgit_clone")]( more like a manual acctualy), i have still to read thru it thou.

How do i install this particular patch?

---

### Post by Favux on 2011-03-09
Shoot you caught me at the wrong time, I've got to scoot.  Be back in a few hours.

Don't worry, applying the patch is easy, I'll give you the instructions and the patch when I get back.  Then you just compile xf86-input-wacom and reboot and see if it worked.

---

### Post by Favux on 2011-03-09
Download the patch and copy/move it into the xf86-input-wacom folder.  Remove the *.txt* at the end with rename so the end is just .patch.

Open a terminal and change directory into your xf86-input-wacom folder.  Then update your xf86-input-wacom folder with a pull:
```
git pull
```
Check to see if the patch will apply cleanly:
```
git apply --check remove-per-device-filter-function.patch
```
If it returns to the prompt without error messages it will apply cleanly.  Then to apply the patch:
```
git apply remove-per-device-filter-function.patch
```
Now you can go ahead a compile xf86-input-wacom and reboot.

Don't do another pull or a commit or anything otherwise you'll mess up your local tree and have to resolve conflicts.  I'll tell how to remove the patch after you've tested it a while.

---

### Post by BackBONE7 on 2011-03-10
The Patch makes no difference at all on my system. The jumps occure in exactly the same way as befor.
In the Patch there is a comment: /* skip event if we don't have enough movement */
probably it would be easy to implement, that events are skiped if we have to much movement?
I mean nobody moves the pen like a maniac over the screen nor does anyone bridge long distances in a split second.
Unfortunatly i am not a very good coder, i looked at the patch and the sourcecode but i understand to little about it to make changes.
If anyone create a patch that mutes events that make a to drastic jump, then i am more then happy to test it.
Do you know the right person for the job?

---

### Post by Favux on 2011-03-10
Bummer.  Well Chris is one of the dev.s so he's one of the right persons to ask.

I don't know if I'm seeing jumps on your debug Xorg.0.logs or not.  What I do notice is that it'll often hold the same x & y locations for 2 to 5 times and then go to the next one.  I'm wondering if the filter is holding onto old values too long.  Maybe the serial tablets don't stream in as much data as the usb ones do?  So the filtering window or average is wrong for them?  Or maybe it's just a few serial digitizers like yours.  Here's a sample of what I'm talking about:
```

(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16658 y=10627 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 2
(II) /dev/ttyS0 (10:commonDispatchDevice): device type = 1
(II) /dev/ttyS0 (11:commonDispatchDevice): tool id=1 for Serial Wacom Tablet stylus
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 8 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (7:wcmReadPacket): MOVE 8 bytes
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=8 remaining=248
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 8 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (7:wcmReadPacket): MOVE 8 bytes
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=8 remaining=248
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 8 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (7:wcmReadPacket): MOVE 8 bytes
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=8 remaining=248
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16666 y=10637 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16665 y=10625 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 2
(II) /dev/ttyS0 (10:commonDispatchDevice): device type = 1
(II) /dev/ttyS0 (11:commonDispatchDevice): tool id=1 for Serial Wacom Tablet stylus
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16665 y=10625 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16665 y=10625 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 0
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
(II) /dev/ttyS0 (10:wcmEvent): channel = 0
(II) /dev/ttyS0 (10:wcmEvent): c=0 i=2 t=1 s=0 x=16665 y=10614 b=0 p=0 rz=0 tx=0 ty=0 aw=0 rw=0 t=0 df=0 px=1 st=0 cs=1 
(II) /dev/ttyS0 (10:wcmCheckSuppress): level = 2 return value = 2
(II) /dev/ttyS0 (10:commonDispatchDevice): device type = 1
(II) /dev/ttyS0 (11:commonDispatchDevice): tool id=1 for Serial Wacom Tablet stylus
(II) /dev/ttyS0 (10:wcmReadPacket): fd=17
(II) /dev/ttyS0 (1:wcmReadPacket): pos=0 remaining=256
(II) /dev/ttyS0 (10:wcmReadPacket): buffer has 9 bytes
(II) /dev/ttyS0 (10:isdv4Parse): 
```
Of course I can't correlate it with what you are actually doing with the stylus.

---

### Post by Favux on 2011-03-11
Talked it over with Chris and he has a suggestion to try.

First revert the effects of the patch.  Since it changed multiple files use:
```
git reset --hard HEAD
```
That should restore everything to the pre-patch state.

Next go into the xf86-input-wacom folder, into /src/ and open the wcmISDV4.c file.  At line #182 change:
```
		return n;
```
to
```
		return n-1;
```
and then recompile xf86-input-wacom and reboot.  See if that stops the hangs on the same x,y coordinates.

---

### Post by BackBONE7 on 2011-03-12
Well... that makes no differenc at all.

I started to experiment with the source a little.
In **wcmCommon.c** there is a if statement at line 674:

```

/* don't move the cursor when going out-prox */
    if (!ds->proximity)
    {
        x = priv->oldX;
        y = priv->oldY;
    }

```I thought this would be a good place to test my idea.
So i put another if statement after the existing one, checked if in proximity (because big jumps can occure if you put the pen on the screen, but not while drawing)
Then i callculated the distance between **x** and **priv->oldX** , **y** and **priv->oldY** respectivly, and then assign **priv->oldX** and **priv-oldY** to **x** and **y** if the distance is bigger than a certain threshold level.
The outcome was that everytime i put the cursor on the screen, it went straight to the upper left corner.
Then i thougt maybe **priv-oldX** and **priv-oldY** contain wrong values, and maybe the jumps occure because of the former mentioned if statement.
So i commented the two lines inside the brackets out, and removed my little hack, but that makes, again, no difference.

Thats the current status, i continue to analyze the code and keep you up date.

---

### Post by BackBONE7 on 2011-04-06
Good thinks come to thouse who wait, they say... and it finaly happend.
After the 11th pull till my last post, i am on Version 0.10.99 now.
I scribled around in MyPaint for a few minutes, without lifting the pen from the screen.
This usually gave me at least 2 to 5 jumps a minute. And now nothing.
I dont know what changed since 0.10.8, but it helped.

By the way, since one certain pull (i don't remember to witch version) the Hover-Click only works when Tablett-Buttons are turned on.

---

