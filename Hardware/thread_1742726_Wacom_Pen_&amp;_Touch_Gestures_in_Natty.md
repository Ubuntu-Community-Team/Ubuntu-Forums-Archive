---
title: "Wacom Pen &amp; Touch Gestures in Natty"
date: 2011-04-29
forum: Hardware
---

### Post by marek_online on 2011-04-29
The support for Wacom Pen & Touch out of the box in Natty is great - the touchpad moves much more smoothly for me than it did with Maverick.

I'm trying to get gestures to work nicely though, and failing. Any gesture I try just gets picked up as a "zoom", which for me is utterly useless. All I'm really looking for is scrolling.

I've tried setting ZoomDistance to 1000 with
```
xsetwacom set 13 ZoomDistance "1000"
```

which seems to work:
```
xsetwacom get 13 ZoomDistance
1000
```

Nevertheless, I still just get zooms whenever I try a two-finger scroll.

I'm keeping my fingers off-set while gesturing, just in case.

I'm beginning to wonder whether some other driver than the wacom one has grabbed the touchpad, as no other settings (e.g. RawSample) seem to have much effect on the tablet's behaviour either (the pen and erase work just fine though, and all devices are listed on a "xsetwacom --list").

Any suggestions would be greatly appreciated.

---

### Post by Favux on 2011-04-29
Using the "device name" from *xinput list* in:
```
xinput list-props "device name"
```
should tell which driver it is.  But it should be wacom if touch is showing up in *xsetwacom list*.

I just tried 2FG scrolling in a couple of app.s.  Seems to work fine in gedit and terminal.  However I see what you see in Firefox.  You have to hold the distance between the two fingers absolutely steady to scroll otherwise you get zoom.  And the zoom, after a lag, is hypersensitive.

I'm wondering if something the new utouch stack or utouch libraries is doing this to Firefox.

---

### Post by Favux on 2011-04-29
I can get scrolling to work if I put it on the Synaptic driver.
```
Section "InputClass"
        Identifier "Wacom touch&pad on Synaptics class"
        MatchIsTouchpad "on"
#	MatchProduct	"Wacom Bamboo 2FG 4x5 Finger touch"
	MatchProduct	"Finger"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
EndSection
```
I used 54-bambooPT-on-synaptics.conf in /etc/X11/xorg.conf.d and installed the gpointer settings gui to enable scrolling.  Don't see a setting for zoom, which might just mean it isn't in the gui.  The buttons come along for the ride unfortunately.

---

### Post by marek_online on 2011-04-30
Hi Favux,

Thanks a million for the reply. 

I might go with the synaptics driver I think - I don't use the buttons on the pad much.

But I don't have an /etc/X11/xorg.conf.d directory - do I just create one or should one already exist?

I'll try manually putting in a file with your code there, and see how it goes.

---

### Post by marek_online on 2011-04-30
Wow did I mess that one up.

My computer will now not boot, even into Recovery Mode.

It hangs during boot at:

```
udev[384]: SYSFS{}= will be removed in a future udev version,  please use ATTR{}= to match the event device, in  /etc/udedv/rules.d/custom-concordance.rules
```

This comes after a series of ```
fsck from util-linux-ng 2.17.2
``` messages.

This requires a hard reboot - not even CAPSLOCK is working after it.

I did two things:
- reinstalled plymouth packages in synaptic (to try to fix a blank screen boot sequence)
- manually added a 54-bambooPT-on-synaptics.conf with your content above to a manually created /etc/X11/xorg.conf.d

I suspect the problem isn't to do with X or the touchpad, it happens even if the touchpad is unplugged, and no matter which kernel I boot into (I've tried three, and their recovery modes).

Hoi.

---

### Post by Favux on 2011-04-30
If you can't boot in Recovery Mode you'll have to boot on a live CD and then mount your file system in order to edit the /etc/udev/rules.d file with nano.  It seems to be telling you the affected file:  /etc/udedv/rules.d/custom-concordance.rules  You can either comment out the rules, delete the file, or try changing all occurrences of SYSFS{}= to ATTR{}=.  The switch over happened with Intrepid I think.  I don't know why the error message is calling udev udedv.  Is 'custom-concordance.rules' from plymouth?

---

### Post by marek_online on 2011-05-01
Hi Favux,

As it happened, the machine wouldn't even boot from a live CD (I tried Lucid, Maverick and Natty). All I'll say is: three cheers for a sound backup policy and a partitioning arrangement that meant I didn't really need it.

I nuked the machine (using Windows, which *would* boot) and reinstalled from scratch, which is a bit drastic but has, eventually, worked.

A glutton for punishment, I'm going back to look at that xorg configuration for the touchpad. Should I be creating xorg.conf.d manually? Or should it exist? And will the 54-bambooPT-on-synaptics.conf file with just you suggested code likely be enough?

Thanks,

M

---

### Post by marek_online on 2011-05-01
Excellent.

Manually added the conf file and the directory and the touchpad is now working just as I'd like it.

I had to sacrifice left-handed rotation (which the synaptics driver doesn't seem to do, though [maybe it used to]("http://cc.oulu.fi/%7Erantalai/synaptics/")? ), but the wire's long enough for me to live with that.

Favux, you've been a great help with this thing, both here and over the last couple of years on your other threads. Thanks a million.

---

### Post by Favux on 2011-05-01
Hi marek_online,

Good, you have it working.

I talked to Chris and he showed me how to fix gestures with xf86-input-wacom.
> I think the main change for you here is your now using the MT Wacom [kernel] driver.  It scales resolution up alot to work around some jitter
issues.  But xf86-input-wacom was never modified to account of this.

Can you edit the file wcmTouchFilter.c?  Look for [~ line # 27]:

#define WACOM_INLINE_DISTANCE        40

and change to the following to line up with kernel side resolution change:

#define WACOM_INLINE_DISTANCE        40 << 5

That worked for me.  The stuff in brackets I added.  I just cloned the git and changed the line before doing autogen.sh, make, and install.  It's pretty sensitive but maybe because I'm used to the old version and haven't "learned" the fully MT version.  Anyway I played with it.  Using 40 << 3 may be a little better on my system but if I go to 40 << 2 then the crossover to zoom comes back.

Rotation is broken for evdev in Natty as the old axis swap doesn't work.  It works on other distros but apparently Ubuntu isn't planning on fixing it.  They suggest using CTM instead.  Maybe that will work for you with Synaptics also to get the tablet left-handed.  See Appendix 1 in [HOW TO Setup a Wacom Tablet with Multi-Monitors in Maverick and Natty]("http://ubuntuforums.org/showthread.php?t=1656089").

---

### Post by marek_online on 2011-05-04
Hi Favux,

Tried the revised wcmTouchFilter.c, but it didn't seem to have any effect for me. Not sure why. 

I think I'm going to just go with the synaptics driver for now - it gets things working pretty much just as I'd like. Going to finish with the configuring and get on with the using I think!

Cheers,

M

---

### Post by Favux on 2011-05-04
OK, doesn't sound like you're interested in putting in the time to troubleshoot it, understandable.  But notice Chris should have it fixed in xf86-input-wacom in not too long a while.

By the way I just ran across someone submitting a patch for Synaptic rotation.  That was a while ago.  They turned it down pending further work but someone did suggest the CTM matrix method.  Apparently it works fine in Absolute mode, I'm a little less clear on how it does in Relative axis mode, which is the default.

---

