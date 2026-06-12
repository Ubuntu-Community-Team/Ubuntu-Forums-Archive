---
title: "Setting up tablet functions on Fujitsu t4215"
date: 2012-01-04
forum: Hardware
---

### Post by jabberwock_11 on 2012-01-04
I am new to Linux, so bear with me if some of my questions seem basic or if I need a bit more help than the average user.

I have a Fujitsu t4215 that, until recently when the SSD failed and the back up disc got messed up, was running Windows Vista.  I currently have Ubuntu 11.10 running on it and am trying to get the tablet functions working.  The pen works as a mouse (but not much else), there is no on screen keyboard for use with the pen, the screen does not rotate, and the function buttons do not work.

I have browsed through several forums and downloaded the input-wacom-0.12.1 file and went through the configure, make, and make install with zero issues.  I downloaded the xf86-input-wacom-0.12.99.1 file, but when I do the configure it gives me these messages: configure: error:

Package requirements (xorg-server >= 1.7.0 xproto xext kbproto inputproto randrproto) were not met:

No package 'xorg-server' found
No package 'xproto' found
No package 'xext' found
No package 'kbproto' found
No package 'inputproto' found
No package 'randrproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I did a search in my file system and found the file source_xorg-server.py in /usr/share/apport/package-hooks so I dunno if I need something else or what.


I also downloaded the fjbtndrv-2.3.2 file for the function buttons, but when I tried to configure the file I got the following messages:
configure: error: Package requirements (x11 xrandr) were not met:

No package 'x11' found
No package 'xrandr' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XRANDR_CFLAGS
and XRANDR_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Any help that you guys can give would be greatly appreciated.  The computer works just fine as a normal laptop, but I really want the tablet set up to work too.

---

### Post by Favux on 2012-01-04
Hi jabberwock_11,

You need some libraries.  See the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or the [Linux Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  They are the lines starting with "sudo apt-get install build-essential libx11-dev...".  I believe the fjbtndrv dependencies would get covered too.  But usually people install Robert Gerlach's PPA:  [https://launchpad.net/~khnz/+archive/ppa?field.series_filter=oneiric](https://launchpad.net/~khnz/+archive/ppa?field.series_filter=oneiric)  Don't know why it now says "Publishing has been disabled for this archive." or what that means.

---

### Post by jabberwock_11 on 2012-01-06
ok, that was very helpful.  I got the files installed to my computer...now I just have to try to get everything configured. 

I have the function buttons working and the screen rotates using those, but I can't seem to get it to auto rotate and the pen also does not rotate with the screen.  I also need to figure out how to automatically pull up either a handwriting program or an onscreen keyboard when I use the pen to input things like web addresses.

---

### Post by Favux on 2012-01-06
Good, progress!

I've been using CellWriter for my scripts and stuff, see the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Give that a try and see if you want to use it too.

Is the stylus in correct orientation in inverted?  Just not in either Portrait orientation?

---

### Post by jabberwock_11 on 2012-01-06
the rotation is pretty minor to me so I'll deal with the auto rotate in time, as long as the buttons work to rotate the screen then I am happy.

The pen however is a big issue.  Right now the pointer icon is oriented the correct way with screen rotation, BUT it goes in the opposite direction when the screen is rotated any other way but normal (i.e. if I move the pen up the pointer goes down).  I dunno how to change the stylus's orientation, I would prefer an automatic reorientation.

I tried CellWriter, but it does not let me lift the pen off of the screen when creating letters (it registers every lift as the start of a new character)...so I don't really like it much, also I see no way to automatically bring it into use when I begin using the pen (maybe I was spoiled by Windows Vista's tablet set up, but it did both of those things).

---

### Post by Favux on 2012-01-06
There is a bug in the default Wacom X drivers (xf86-input-wacom) that causes stylus orientation in Portrait to be reversed, i.e. cw and ccw are swapped, in Natty and Oneiric.  The solution is to update to at least version 0.11.1 which has the fix.  See part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") or section 2 of the [Linux Wacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").
> CellWriter, but it does not let me lift the pen off of the screen when creating letters (it registers every lift as the start of a new character)
That sounds like you didn't train it.  When in training mode it will show you the characters in grey.  You need to keep rewriting until it has enough samples, then the character turns black.
> no way to automatically bring it into use when I begin using the pen
Not that I know of.  That's why I set it up to only show in tablet mode.

---

### Post by jabberwock_11 on 2012-01-06
Ahh, well I will have to retrain the CellWriter then.  I just did a quick set up.  I am sure with a bit of work this program will be exactly what I am looking for.

I have xf86-input-wacom-0.12.99.1, so maybe I did not configure it properly or something, because the stylus as well as the mouse touchpad both try to go in the wrong directions.

---

### Post by Favux on 2012-01-06
I wonder if he could have altered his rotation script to take the bug into account?   But you no longer have one of the buggy xf86-input-wacoms.

Have you tried one of the commands on the Rotation HOW TO to see if it does set the stylus correctly?

---

### Post by jabberwock_11 on 2012-01-08
Well, it is possible.  I have been trying to figure things out using all sorts of different "how to" and forum postings, but I don't know how I would go about checking the files to see if I accidentally over corrected.

To be perfectly honest I didn't notice any changes or differences when I installed the input-wacom-0.12.1 and xf86-input-wacom-0.12.99.1 files.  My pen already worked as a pointer device before that and the screen still didn't rotate.  The only thing that seemed to actually do anything was the fjbtndrv-2.3.2 file, which allowed me to use the function buttons to rotate the screen manually.  I am not even entirely certain what the first two files are supposed to accomplish beyond automatic screen rotation.

I don't know about any other functions that may be provided, but really all I want to do is to be able to rotate the screen and to use the pen as a mouse and to input characters (for web browsing addresses and text).

I tried working with CellWriter, but every time I raise the pen when training the letters (such as to dot an i or cross a t) it takes the first stroke as a single sample and the dot or cross or whatever as a different sample...I am trying to figure out how to better work with the program using the help guide and forums.

Sigh, I really am trying to get this all worked out, but it seems like so much work for so little benefit.  It is a bit frustrating, but maybe if I get this worked out I can help other folks in similar situations.

---

### Post by Favux on 2012-01-08
Tablet PCs are pretty simple compared to some of the Wacom tablets and unless it is a new model pretty much any recent xf86-input-wacom will work.  Well except for the cw/ccw swap bug which wasn't fixed until 0.11.1.

What the fjbtndrv does is install a new kernel driver/module called fujitsu-tablet.ko.  There should already be one called fujitsu-laptop.ko.  The fujitsu-tablet.ko is similar to say the thinkpad_acpi.ko.  Just like it, it is what is detecting the bezel buttons and automatic rotation.  As part of the package it installs scripts, some of them for rotation.  In /usr/lib/fjbtndrv I think.  If you look in the packages at Robert Gerlach's sites you'll see all that.

I'm not sure what is wrong with CellWriter.  I only see that if it is untrained and it "gets it" when I execute separate strokes in training mode.  Not sure what could do that.  Maybe you should reinstall CellWriter?

---

### Post by jabberwock_11 on 2012-01-08
I still don't know how to change the files so that my stylus will rotate with the screen rotation.  The screen rotates ccw using fjbtndrv-2.3.2 and when the screen is right side up or upside down the pen works correctly, but when it is turned to the left or right the pen and pointer go in the opposite direction.

Every posting that I have found (other than the few you have directed me to) all involve earlier versions of the Ubuntu OS, so I keep running into issues there when looking for help.  This site gave me some scripts that work the same way the button driver does, but also have the same issue.   [http://agacho.blogspot.com/2010/10/ubuntu-1010-on-tablet-pc-hp-2730p.html](http://agacho.blogspot.com/2010/10/ubuntu-1010-on-tablet-pc-hp-2730p.html) 

I really just need to know how to find and alter the files so that the pen will rotate with the screen.

---

### Post by Favux on 2012-01-09
Sorry, I should have been clearer.  You want to find the rotate-wacom.sh file.  I think it is in /usr/lib/fjbtndrv.  Then edit it using:
```
gksudo gedit /usr/lib/fjbtndrv/rotate-wacom.sh
```
and change it from:
```
#!/bin/sh

test "$ACTION" = "rotated" || exit 0

case "$ORIENTATION" in
	n*) val=0 ;;
	r*) val=1 ;;
	l*) val=2 ;;
	i*) val=3 ;;
	*)  exit 1 ;;
esac

# xinput installed?
xinput --version || exit 0

export LC_ALL=C

xinput list --short \
| sed 's/^[^[:alnum:]]* \(.*\) *id=.*/\1/p; d' \
| grep -vi 'virtual' \
| while read dev; do
	if xinput list-props "$dev" | grep -q 'Wacom Rotation'; then
		xinput set-prop "$dev" 'Wacom Rotation' $val
	fi
done

exit 0
```
to
```
#!/bin/sh

test "$ACTION" = "rotated" || exit 0

case "$ORIENTATION" in
	n*) val=0 ;;
	r*) val=2 ;;
	l*) val=1 ;;
	i*) val=3 ;;
	*)  exit 1 ;;
esac

# xinput installed?
xinput --version || exit 0

export LC_ALL=C

xinput list --short \
| sed 's/^[^[:alnum:]]* \(.*\) *id=.*/\1/p; d' \
| grep -vi 'virtual' \
| while read dev; do
	if xinput list-props "$dev" | grep -q 'Wacom Rotation'; then
		xinput set-prop "$dev" 'Wacom Rotation' $val
	fi
done

exit 0
```
See where I swapped the 2 and the 1 under $ORIENTATION?  The other way to do it is to update to a xf86-input-wacom version that doesn't have the bug.  So at least 0.11.1, see part II. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

---

### Post by jabberwock_11 on 2012-01-09
HOLY CRAP IT WORKED!  After DAYS of trying to find something to allow me to alter the set up so that the stylus would rotate with the screen rotation, that little minor alteration worked!

Now all I have to do is work with CellWriter to get that the way I want it and I will be in business and using an OS that works better than the Windows Vista set up that I initially had on here.  There are things that did not work with Vista that have no issues on Ubuntu.

I was even considering moving to Linux Mint, which seems to have wacom stuff right in their repositories.  Thanks for the help so far.

Oh, I also found a thread about handwriting recognition software for tablet PCs that you may be interested in checking out.  [http://ubuntuforums.org/showthread.php?t=1147022](http://ubuntuforums.org/showthread.php?t=1147022)

---

