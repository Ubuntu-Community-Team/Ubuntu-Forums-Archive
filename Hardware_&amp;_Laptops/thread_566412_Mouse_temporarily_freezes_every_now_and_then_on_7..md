---
title: "Mouse temporarily freezes every now and then on 7.4"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by FFred on 2007-10-03
An odd issue recently appeared on my workstation running 32bit 7.04 where the mouse will freeze every now and then for something between 3 to 30 seconds before resuming normal operations. 
The mouse is a wireless Logitech G7 which I've been using with Ubuntu and Gentoo before that without any trouble for quite some time. 

I tried rolling back to kernel 2.6.20-15 in the hope that a recent kernel upgrade might had been the culprit but the symptoms are still there.

Nothing shows up in dmesg or messages. So basically I've no idea what's causing this. I'm starting to suspect a hardware problem (on the mouse side) although the fact that it spontaneously recovers doesn't really seem to point that way. If the mouse failed it would show up as being disconnected in the logs (or at least it should). 

I did poke a bit at my gaming partition (in Windows) to see if the symptoms could be reproduced there but got nothing. Unfortunately I didn't really have time to fully investigate there (gotta work you know).

Needless to say I'm really puzzled and quite annoyed by this, especially since I work with two machines linked by Synergy... difficult without the mouse.

So, suggestions anyone ?

---

### Post by Pablo Pablovski on 2007-10-03
Can't help much (sorry), except to say I've been having this issue too on Fiesty i386 32bit on an AMD 3500+, 2GB RAM with a wireless Logitech Media Mouse currently hung off the PS/2 port (happens when it's attached via USB too).

In my case, the mouse freezes for maybe 3 or 4 seconds, then it's ok again. It seems to have been happening since I upgraded my video card from a 6600GT to an 8800GTS (both nVidia. obv.). I had to reinstall the GPU driver (9755) when I upgraded. 

Xorg.conf contains the changes required to make the new card work - nothing else was changed. 

It doesn't happen in XP.

You're right - it IS annoying! Anyone?

---

### Post by FFred on 2007-10-03
On my side I haven't changed any hardware recently. 
Although I *might* have been poking at corg.conf to play with Beryl more or less at the time when the trouble began (thought of this because you mentioned your video card).
I'm not really sure but I might have added the usual 
  Option "AddARGBGLXVisuals" "True"
  Option "DisableGLXRootClipping" "True"
stuff.

I also found (just now when looking at the xorg.conf file) duplicate device/monitor/screen entries. Which I removed. They listed something with a vesa driver (the video is handled by a GeForce 7950GX2 ?) and there were a bunch of empty entries. I don't know what package edited this.

I' going to poke at the xorg conf file and I'll let you know if anything happens.

The machine is intel dual core2 6700 with 2GB of RAM (not sure it's relevant)
The mouse (or the radio receiver rather) shows up as 0x46d:0x46d on the USB.

---

### Post by FFred on 2007-10-03
Ok, so after some rather heavy editing of the xorg.conf file, this seems to work (only the mouse section) :
```
Section "InputDevice"
  Identifier    "Logitech G7"
  Driver        "evdev"
  option        "CorePointer"
  option        "Phys"          "usb-0000:00:1d.0-2/input0"
  option        "Buttons"       "7"
  option        "ZAxisMapping"  "4 5"
EndSection
```

The trick was to switch to the evdev driver (which was a bit of a hassle since it wasn't easy  pointing at the right device, Finally using the "Phys" syntax above did the trick (it was also nice to have a second machine to do the edits from since the main one was fairly borked at that stage, sometimes with the keyboard gone too, so no access to the consoles).

So far everything seems to be back to normal. It would have been interesting to figure out why it did break in the first place though...

---

### Post by FFred on 2007-10-03
*sigh*

Ok. Things have gotten slightly better with the switch to evdev (slightly better as in it freezes only every 10 minutes instead of every couple minute).

**However**, it let me unearth a completely different can of worms which is exposed on the following page (warning, surrealism ahead) :
[http://www.chromakode.com/blog/2007/09/19/logitech-lx7-in-ubuntu-edgy-ihatekludgers/](http://www.chromakode.com/blog/2007/09/19/logitech-lx7-in-ubuntu-edgy-ihatekludgers/)

The story behind it is exposed here :
[http://zaitcev.livejournal.com/108213.html](http://zaitcev.livejournal.com/108213.html) (something I was scratching my head about as well)
and the coding weirdness is here (although the reason for it remains fuzzy)  :
[http://zaitcev.livejournal.com/108617.html](http://zaitcev.livejournal.com/108617.html)

So apparently the evdev driver is not fit for driving a "core pointer" so X gets to make one up on the spot via a phantom mouse that exists in its schizophrenic little mind. Which leads to various weird things. And explains why getting many-buttonned mice to work was near to impossible.
Whether this is related or not to the freezing issue isn't clear.

Quite amazing at any rate. But supposedly fixed in Xorg 7.3. Whew.

---

### Post by FFred on 2007-10-04
Ok after applying the fixes above, the problem seems to be gone. No freezes in the last hour.

---

### Post by Pablo Pablovski on 2007-10-04
Wow! Quite a tale there. It's cool to see what *actually* goes on with developers!

I'm off to give it a try. If I'm not back in an hour, send me a Wacom tablet for input.

---

### Post by FFred on 2007-10-04
Ok, so to sum things up, the problem is *mostly* gone. I still have the occasional mouse freeze, quite rarely though, but the system is now usable.

I can't find any trace of anything in the logs (I have tail -f running on several files) when the freeze happens which is frustrating. I also looked at ~/.xsession-errors which I had overlooked at first but nothing worthwhile there either.

Well, at least I got to clean up my xorg.conf.

Just in case, added my xorg.conf.

---

