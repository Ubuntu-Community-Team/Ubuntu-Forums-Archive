---
title: "odd request: Webcam as desktop background?"
date: 2008-08-04
forum: General Help
---

### Post by The Warlock on 2008-08-04
Hey, I've got a shiny new EeePC with a 1.3 MP camera built in. Drivers worked fine after downloading and compiling the newest uvcvideo modules; that's not the problem.

I would like to set it up so that the camera feed is the desktop "wallpaper". Is there any way to do this? Right now I'm using Gnome, but I would readily switch desktop environments if it let me do this.

---

### Post by swarm on 2008-08-05
> **The Warlock said:**
> Hey, I've got a shiny new EeePC with a 1.3 MP camera built in. Drivers worked fine after downloading and compiling the newest uvcvideo modules; that's not the problem.

I would like to set it up so that the camera feed is the desktop "wallpaper". Is there any way to do this? Right now I'm using Gnome, but I would readily switch desktop environments if it let me do this.

Since nobody decided to give this a shot, I'll throw out a suggestion..

To get started, lets try some things. This is NOT tested.

Download and install VLC

Set the webcam to store a video clip to your hard drive.

Set VLC to stream the video to your background. 

Did this work? Is this what you wanted? The video filesize will get pretty large, sadly, and an EEEpc doesn't have a ton of storage space. Maybe someone can chime in on how to cut off the front of the video every once in a while, or a better solution overall?

Also, have you considered how resource intensive this may be?

---

### Post by The Warlock on 2008-08-06
Hey, found something else that works. Good ol' mplayer. 

Sidenote: I kind of miss old-school Linux programs like mplayer. Belligerently user-unfriendly but capable of ***anything*** given the proper command line input.

Which, in this case, is:

mplayer -rootwin -fs -fps 15 tv:// -x 1024 -y 600 -sws 0 -vf crop=640:375

-rootwin sets it as the root window
-fs stretches it to fullscreen
-fps 15 keeps it at fifteen frames per second (to decrease processing time spent on it)
tv:// goes to the default video source (the webcam)
-x 1024 -y 600 stretches it to the exact resolution of my 1024x600 screen
-sws 0 sets the software scaling mode to the least processor-intensive option
-vf crop=640:375 crops the 640x480 camera output to the proper widescreen before stretching it, so the aspect doesn't get screwed up.

This works almost perfectly and takes almost no CPU power.
Some problems:

1) desktop icons won't show up, because I need to turn Nautlius's "show-desktop" option off. 

2) other programs can't use the cam at the same time, unfortunately.

3) the biggie: suspend-to-RAM doesn't work when the camera is in use, or it does work but the camera stops working until a reboot.

unfortunately, #3 there is a dealbreaker. I've filed a bug report; that happens with any program using the camera.

Anyway, maybe anyone on a desktop where you don't need suspend might find this helpful.

---

### Post by easybake on 2008-08-06
You can do it using xwinwrap. [[IMG]http://img511.imageshack.us/img511/7571/screenshotvi2.th.png[/IMG]](http://img511.imageshack.us/img511/7571/screenshotvi2.png)EDIT: New[[IMG]http://img210.imageshack.us/img210/5060/screenshotir7.th.png[/IMG]](http://img210.imageshack.us/img210/5060/screenshotir7.png)

It boxes my conkys when i click on them. You can keep your icons and docks too.
```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid WID -quiet -fps 15 tv://
```
For those who don't know how to install xwinwrap.
in terminal
```
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
``````
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
```
```
cd xwinwrap
``````
make
```Optional ```
sudo cp xwinwrap /usr/bin
```

---

### Post by The Warlock on 2008-08-07
That's an excellent solution to problem 1 up there; now just to figure out 2 and 3.

---

### Post by easybake on 2008-08-07
> **The Warlock said:**
> That's an excellent solution to problem 1 up there; now just to figure out 2 and 3.

Would a toggle script solve those problems? That way you could just create a custom launcher that turns it off/on when you want.
In terminal```
gedit blahblah
```
Paste this in text editor```
#!/bin/sh

# click to start, click to stop
if pidof xwinwrap ; then
 killall xwinwrap
 else
 exec xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv://
fi
```Save and close.
In terminal```
sudo chmod a+x blahblah
```
Create a launcher with any name with the Command```
./blahblah
```

---

### Post by The Warlock on 2008-08-07
Hey, how did you get transparency to work right with mplayer? If I use the xv output driver, there are big black borders wherever something should be transparent. (And if I use the x11 driver, it takes like a third of my CPU power so that's right out.)

---

### Post by easybake on 2008-08-07
> **The Warlock said:**
> Hey, how did you get transparency to work right with mplayer? If I use the xv output driver, there are big black borders wherever something should be transparent. (And if I use the x11 driver, it takes like a third of my CPU power so that's right out.)

My bad, it might only work if you're running compiz as your window manager. If you try to use metacity or something else i don't think it will work.

Edit: I wrote a Howto on how i accomplished it, but it hasn't been approved yet.

---

### Post by The Warlock on 2008-08-07
No, I'm using compiz. xwinwrap doesn't work at all under metacity. But the transparent parts of compiz (i.e. the whole damn point of compiz) don't do a proper transparent overlay over the video background, instead they just show solid blue or solid black or whatever.

Unless I change mplayer's output driver to x11 software rendering, but that's pretty CPU-heavy. If it's what's needed, though, I guess it's what I have to do. I'll just give it a high "nice" value.

---

### Post by loell on 2008-08-07
this is the best hack i've seen for awhile now. :)
thanks easybake :KS

---

### Post by gaminggeek on 2008-08-08
> **The Warlock said:**
> 
Unless I change mplayer's output driver to x11 software rendering, but that's pretty CPU-heavy. If it's what's needed, though, I guess it's what I have to do. I'll just give it a high "nice" value.

that is because indirect rendering is not supported on some intel cards like the one in the EEE and in my dell laptop, you can ether wait till it is supported or try the opengl mplayer plugin

---

### Post by easybake on 2008-08-08
> **loell said:**
> this is the best hack i've seen for awhile now. :)
thanks easybake :KS

Thanks. I was psyched when it worked.

---

### Post by andybleaden on 2008-08-08
> **The Warlock said:**
> Hey, I've got a shiny new EeePC with a 1.3 MP camera built in. Drivers worked fine after downloading and compiling the newest uvcvideo modules; that's not the problem.

I would like to set it up so that the camera feed is the desktop "wallpaper". Is there any way to do this? Right now I'm using Gnome, but I would readily switch desktop environments if it let me do this.



That was a fantastic hack I must admit

Now then The Warlock...was looking at these eeepc things...are they any good...for moderate home use as a backup for my desktop...ie for the kids to use ...running (k)ubuntu

Was it easy to set up etc?

---

### Post by The Warlock on 2008-08-09
> **andybleaden said:**
> Was it easy to set up etc?

As the kids these days say, "lol no".

Neither the wired nor wireless network drivers are included in good ol' Hardly Heroin. It was also missing proper drivers for the webcam, sound, and ACPI. They might be in the next version, I dunno. I compiled them from source, but someone at array.org later made custom kernels that help everything work right. The system works perfectly *now*, but setting it up was a bit of an ordeal.

Great laptop, though. It's *so tiny.*


Hey, I'm trying to set this up to stop on sleep and start on wake, but I can't seem to get my scripts in /etc/pm/sleep.d to work. What's the deal? I chmodded them +x and everything.

---

### Post by easybake on 2008-08-09
> **The Warlock said:**
> That's an excellent solution to problem 1 up there; now just to figure out 2 and 3.

Hey I didn't figure it out but someone else did.

[http://ubuntuforums.org/showpost.php?p=5554249&postcount=3]("http://ubuntuforums.org/showpost.php?p=5554249&postcount=3")

---

### Post by joss24 on 2008-10-15
Wow thats what i have been looking 4 a long time.
Any similar solution in xp?

PS. Glue webcam behind ur lcd and enjoy simulated transparency ;D

---

### Post by easybake on 2008-10-15
> **joss24 said:**
> Wow thats what i have been looking 4 a long time.
Any similar solution in xp?

PS. Glue webcam behind ur lcd and enjoy simulated transparency ;D

jdong actually noted that idea in the tutorial I made for this. You should post a picture of your result. 

My tutorial [http://ubuntuforums.org/showthread.php?t=883176]("http://ubuntuforums.org/showthread.php?t=883176")

---

### Post by scruffpup on 2008-11-30
your info about using mplayer was a huge help for me, but it didnt work right off the bat.  after a bunch of googling, this is the command line i ended up using, im posting it in case it might help anybody else


mplayer -rootwin -fs -x 1600 -y 1200 -sws 0 -fps 15 -tv driver=v4l2:device=/dev/video0:input=0:outfmt=rgb24 tv://

---

### Post by warrenis1234 on 2009-02-19
> **easybake said:**
> You can do it using xwinwrap. [[IMG]http://img511.imageshack.us/img511/7571/screenshotvi2.th.png[/IMG]](http://img511.imageshack.us/img511/7571/screenshotvi2.png)EDIT: New[[IMG]http://img210.imageshack.us/img210/5060/screenshotir7.th.png[/IMG]](http://img210.imageshack.us/img210/5060/screenshotir7.png)

It boxes my conkys when i click on them. You can keep your icons and docks too.
```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid WID -quiet -fps 15 tv://
```
For those who don't know how to install xwinwrap.
in terminal
```
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
``````
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
```
```
cd xwinwrap
``````
make
```Optional ```
sudo cp xwinwrap /usr/bin
```



how would i go about reversing the output so i can get it to look like a mirror

---

### Post by easybake on 2009-02-19
> **warrenis1234 said:**
> how would i go about reversing the output so i can get it to look like a mirror

All you have to do is add "-vf mirror" to the end of the command. like this 
```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv:// -vf mirror
```

---

### Post by warrenis1234 on 2009-02-20
perfect, thanks

---

### Post by zefry on 2010-07-09
I can't access...
haelp me please....

I got..
```
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: USB20 Camera    
 Capabilites:  video capture  read/write  streaming
 supported norms:
 inputs: 0 = sn9c20x;
 Current input: 0
 Current format: unknown (0x30323953)
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: Cannot get fps
v4l2: ioctl set mute failed: Invalid argument
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
Opening video filter: [mirror]
==========================================================================
Cannot find codec matching selected -vo and video format 0x30323953.
Read DOCS/HTML/en/codecs.html!
==========================================================================

v4l2: ioctl set mute failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.

Exiting... (End of file)
mplayer died, exit status 0

```

what should I do..??

please help me...

---

### Post by Jose Catre-Vandis on 2010-10-21
Tried the mplayer command with dvb (but happens with trying to play an avi too) - I get sound but no video, getting X11 errors?

```
mplayer dvb://BBC1 -rootwin -fs -x 1920 -y 1080
```

```
X11 error: BadAccess during XSelectInput Call
X11 error: The 'ButtonPressMask' mask of specified window has probably already used by another appication (see man XSelectInput)
X11 error: MPlayer discards mouse control (reconfiguring)
```

---

