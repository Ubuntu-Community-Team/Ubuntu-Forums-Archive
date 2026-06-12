---
title: "Genius F610 tablet in 9.10 - which drivers?"
date: 2010-08-19
forum: Hardware
---

### Post by Fubrite on 2010-08-19
Hi,

I'm trying to set up my Genius F610 tablet, but am a little confused...

xinput --list gives the tablet as "WALTOP International Corp. Slim Tablet"

So, do I use wacom, wizardpen or waltop drivers?

And could anyone point me towards a baby-steps how-to of installing them?

This really shouldn't be this complicated!

Thanks!

Stefan

---

### Post by Favux on 2010-08-19
Hi Fubrite,

It should be the wacom driver but because of a kernel problem currently using WizardPen.  See "Attention Waltop tablet in Lucid" near the top of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  That'll link you to several HOW TO's.

---

### Post by Favux on 2010-08-19
Oops.  Sorry, you're in Karmic not Lucid.  So a patched Wacom, see:  [http://ubuntuforums.org/showpost.php?p=8243791&postcount=86](http://ubuntuforums.org/showpost.php?p=8243791&postcount=86)  And a couple pages before and after.

---

### Post by Fubrite on 2010-08-19
Thanks for your help!

I think I started to do it right, but have come a little unstuck...

I:
-downloaded linuxwacom-0.8.8-8.tar.bz2
-un-tarred it
-downloaded the alternative wcmUSB.c from [http://ubuntuforums.org/showpost.php?p=8244156&postcount=92](http://ubuntuforums.org/showpost.php?p=8244156&postcount=92) and un-tarred it
-renamed src/xdrv/wcmUSB.c to wcmUSB.c.bak
-replaced wcmUSB.c with the alternative one
-ran ./configure --enable-wacom --prefix=/usr
-ran make

and got:

/wcmUSB.c:545: error: &#8216;struct _WacomCommonRec&#8217; has no member named &#8216;wcmCapacity&#8217;
./wcmUSB.c:546: error: &#8216;struct _WacomCommonRec&#8217; has no member named &#8216;wcmCapacityDefault&#8217;
./wcmUSB.c:550: error: &#8216;struct _WacomCommonRec&#8217; has no member named &#8216;wcmCapacity&#8217;
./wcmUSB.c:551: error: &#8216;struct _WacomCommonRec&#8217; has no member named &#8216;wcmCapacityDefault&#8217;
./wcmUSB.c: In function &#8216;usbParseChannel&#8217;:
./wcmUSB.c:1040: error: &#8216;WacomDeviceState&#8217; has no member named &#8216;capacity&#8217;
./wcmUSB.c:1117: error: &#8216;struct _WacomCommonRec&#8217; has no member named &#8216;wcmCapacityDefault&#8217;

Pleas help!

---

### Post by Favux on 2010-08-19
The 0.8.8-8 linuxwacom is too new for that wcmUSB.c.  You'll either have to manually make the changes to the 0.8.8-8 wcmUSB.c or maybe try linuxwacom 0.8.6-2.  I forgot which version's wcmUSB.c we were working on, maybe 0.8.4-something?

I can help you if needed.

---

### Post by Fubrite on 2010-08-20
Right, I've got it sort of working...

I downloaded linuxwacom-0.8.4-3 from [http://ubuntuforums.org/showpost.php?p=8676926&postcount=120](http://ubuntuforums.org/showpost.php?p=8676926&postcount=120)

and ran ./configure, make and sudo make install on that.

I followed the rest of the instructions on the how-to at [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9740603](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9740603) to replace the .fdi

So now, when I first boot the laptop (HP Pavilion dv3), after I tap the pen on the pad once, hovering the pen on the pad moves the cursor (though not all of the pad is used, but I think that might be down to my resolution, and a minor niggle at the moment) but the buttons on the pen don't work. After tapping the pen again, in order to move the cursor, I have to touch and drag the pen on the pad and the cursor is in "relative" mode (i.e the point I tap on the pad doesn't correspond to the point on the screen - I hope that makes sense... didn't notice if this is the same when hovering, but I don't think so). This persists until I reboot.

When I run wacomcpl or xsetwacom, I get the following error

xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

Any ideas?

Thanks for your help!

---

### Post by Favux on 2010-08-20
Hi Fubrite,

Really nice work!  Looks like you almost have it.

Doesn't look like you installed the dependency libx11-dev.  So before you compile do:
```
sudo apt-get update

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

sudo apt-get upgrade
```
then after you change directory into the unpacked linuxwacom tar, before you do:
```
./configure --enable-wacom --prefix=/usr
```
run:
```
make clean
```

---

### Post by Fubrite on 2010-08-20
Hi,

I did the above, but it's doing the same thing...

When I ran

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

I got:

build-essential is already the newest version.
libx11-dev is already the newest version.
libxi-dev is already the newest version.
x11proto-input-dev is already the newest version.
xserver-xorg-dev is already the newest version.
tk8.4-dev is already the newest version.
tcl8.4-dev is already the newest version.
libncurses5-dev is already the newest version

I'm still getting the error:

xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

when I try xsetwacom list

---

### Post by Favux on 2010-08-20
Hmmm.  Not sure what's going on.  Do you have a 64-bit install?

---

### Post by Fubrite on 2010-08-20
That's a good question! I did have 64-bit installed, but I'm almost positive I did a clean install of 32-bit since then because I was having graphics troubles - is there a way to check?

---

### Post by Favux on 2010-08-20
```
cat /proc/version_signature
```

---

### Post by Fubrite on 2010-08-20
That gives Ubuntu 2.6.31-22.63-generic - is that 32- or 64-bit (and does it shed any light?

Thanks!

---

### Post by Favux on 2010-08-20
My bad.
```
uname -m
```
or
```
uname -a
```

---

### Post by Fubrite on 2010-08-20
Linux HP-laptop 2.6.31-22-generic #63-Ubuntu SMP Wed Aug 18 22:54:26 UTC 2010 i686 GNU/Linux


which is 32-bit?

Just so you know, my laptop's processor is 64-bit, but that shouldn't matter?

---

### Post by Favux on 2010-08-20
Right i686 means 32-bit.  And a 64-bit processor can run either a 32-bit or 64-bit OS.

Darn, 32-bit.  There goes that thought.  Not sure why wacomcpl won't start.  The stylus is working OK?

---

### Post by Fubrite on 2010-08-20
Yes and no - when I boot up the laptop, the stylus isn't recognised until I tap it once, then it acts in relative mode when hovering it over the pad, until I tap it again, at which point I have to drag the stylus on the pad to move the cursor. The side-buttons don't seem to be recognised, and tapping the tip isn't recognised as a left click (or anything else as far as I can tell)

---

### Post by DwalerXIII on 2010-08-23
Yesterday I received my new Genius easypen i405. 
I installed the WizardPen driver (as described on [https://help.ubuntu.com/community/TabletSetupWizardpen)and](https://help.ubuntu.com/community/TabletSetupWizardpen)and) the tablet worked without further configuration.
The Genius G-Pen F610 should also work with this driver.

---

### Post by Fubrite on 2010-08-28
Hi,

I've finally managed to get this 99% working. For future reference, I upgraded to 10.04 (Lucid Lynx) and installed and configured wizardpen.

My conf file is

> Section "InputClass"
   Identifier      "wizardpen"
   MatchIsTablet   "on"
   #MatchProduct	   "*WALTOP*"
   MatchDevicePath "/dev/input/event6"
   	Option		"Device"	"/dev/input/event6"
	Option		"TopX"		"134"
	Option		"TopY"		"98"
	Option		"BottomX"	"20000"
	Option		"BottomY"	"12500"
   Driver          "wizardpen"
EndSection

Now, about the missing 1% - when I run xinput list, I get:

>  Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet  	id=14	[slave  pointer  (2)]


there's no 'stylus' listed. Which on the face of it isn't too bad, but it may be a cause of the next problem.

I'm trying to use Easystroke. When I hold down my pen's side button to make the gesture, and then release it, the button mapping gets messed up - the tip no longer responds, and the two side buttons seem to switch places. The only way to get it back, is to randomly hold down each side button for 5 seconds several times in a row, doesn't seem to matter which order I do it in, and eventually it'll start working again til the next time I want to use a mouse gesture...

I have been able to replicate this with Easystroke turned off, so I don't think it's that, does anybody have any ideas?

---

### Post by Fubrite on 2010-08-30
anyone?

---

