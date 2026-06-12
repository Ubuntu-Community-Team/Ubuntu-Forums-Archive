---
title: "hp tx2500 series. How on Earth do you get Wacom working?"
date: 2009-04-04
forum: Hardware
---

### Post by maspin on 2009-04-04
**[COLOR="DarkRed"]SOLVED[/COLOR]**


Hello,

I recently bought a hp tx2650 (2500 series) tablet. I have been trying for two weeks not to get the touch screen functions working, and nothing.

I'm still kind of new to Ubuntu, and do not know much about it. I have tried everything I can (crashed xorg.conf a few times). I've followed the instructions on the Ubuntu documents for Wacom, and still nothing.

I was on 8.10, but a friend suggested I try upgrading my kernel to 2.6.28 (from 2.6.27). I couldn't figure that out, so I am trying Jaunty now..

As above, it is a new computer, so not much is on it, I don't mind a complete reinstall of any version to get it working.

I really don't want to go back to Windows, but I don't want a crippled tablet. The reason I bought it is for the touch screen/stylus. So if ANYONE can help, please do! (but keep in mind, I am a bit simple when it comes to this OS)

Thanks,
Matt

---

### Post by Favux on 2009-04-04
Hi Matt,

This is going to be interesting.  I helped a guy with a serial tablet set up in Jaunty.  But so far I haven't heard of a usb tablet pc getting set up.

I think Jaunty has linuxwacom 0.8.1-6 in it's Repository.  Check with Synaptic Package Manager that both linuxwacom drivers and wacom-tools are installed.  Search with "wacom".  Always be sure the linuxwacom driver's version and wacom-tools are the same or badness happens.

Then go here to get a TX2500 xorg.conf at the bottom of the first post.  Be sure to back up your xorg.conf first and compare the two before doing anything.

[http://ubuntuforums.org/showthread.php?t=1038949]("http://ubuntuforums.org/showthread.php?t=1038949")

You can probably replace yours with it.  Although the ATI proprietary driver "fglrx" now supports rotation so you don't necessarily need "radeon".  Do you know where xorg.conf lives and how to edit it?  Do you know how to back it up?  It's important to note that some changes (new sections) have to be reflected in "ServerLayout" so look carefully.

Don't try to compile anything or use the links to Loic2's Wacom wiki to download the 0.8.1-6 deb.s.  Let's just use the linuxwacom that comes with Jaunty.  Then you can follow the link to the Rotation HOW TO or go directly, it's here:

[http://ubuntuforums.org/showthread.php?t=996830&page=9]("http://ubuntuforums.org/showthread.php?t=996830&page=9")

If you need more ask.  And we can definitely get you set up in Intrepid.

Edit:  Oh yes, there are suppose to be two new gui's for configuration in Jaunty.  "Xorg.conf Options Editor" was seen and it's called xorg-options-editor-gtk and its version is 0.2 in Synaptics I believe.  It's for video configuring and other things.  Not sure how useful that would be to you now.  Also there was suppose to be "Graphical Configuration Tool for Wacom Tablets & Tablet PCs".  But so far no one has seen it.  The idea is you'd edit xorg.conf through these gui's.  Much less chance of newbies breaking X that way goes their thinking.

---

### Post by Favux on 2009-04-06
Hi again Matt,

Are you still there?  If you still want to install Jaunty (or already have) there may be a new way to get Wacom working.  It should be simpler for you because there is no need to configure xorg.conf.

Let me know.

---

### Post by maspin on 2009-04-06
Hi,
Sorry about the slow reply. It has been a busy weekend.
I will be trying all of this over the next few nights to see if I can get it working. Thank you for the help!

I am using Jaunty at the moment. But I have no issues changing back to 8.10. It is a new computer, so I haven't got much on there that I would miss if I formatted the harddrives a few times.

Matt

---

### Post by Favux on 2009-04-06
Hi Matt,

No problem.  Before you decide on which version of Ubuntu to install please check out post #546 here:

[http://ubuntuforums.org/showthread.php?t=845911&page=55&highlight=tx2*](http://ubuntuforums.org/showthread.php?t=845911&page=55&highlight=tx2*)

Whatever you decide we should be able to get you set up.

---

### Post by maspin on 2009-04-06
Hey,

I tried your xorg.conf.. It kind of crashed.. I got (like I do whenever I edit xorg) a glitch screen instead of a login screen.

I am at a bit of a loss now. There has been so much stuff I've read on this lately, that it has all blurred together.

I have a copy of 8.10 and 9.04 here. Which seems more likely to work? And where do I go from there?

Like I said before, I am kind of new. I know the very (very) basics. I've only been using Ubuntu for about 4 months I believe. So is there a simple step-by-step somewhere I can follow to get this up and working?

:sad:

---

### Post by Favux on 2009-04-06
Hi Matt,

I'd need to see your current xorg.conf.  The one that crashed.  So you know xorg.conf lives in /etc/X11/?  To edit it use:
```
gksudo gedit /etc/X11/xorg.conf
```
Did you download the amd64 deb.'s from Loic2's Wacom wiki and install them?  To back up xorg.conf use:
```
cp /etc/X11/xorg.conf /etc/X11/my_xorg.bak
```
or whatever you want to name it.  To reinstall it reverse it like:
```
cp /etc/X11/my_xorg.bak /etc/X11/xorg.conf
```

Take a breath and break.  Clear your head.  This isn't as hard as it seems.  You just need to be a little patient.

---

### Post by maspin on 2009-04-07
Hey,

My xorg.conf is attached below. It is just the default one, so nothing special.
The one that crashed was the one you suggested.

Thanks for your help!

Matt

---

### Post by maspin on 2009-04-07
Oh, right. I know how to do all the editing and backups for xorg.conf. So you don't have to worry about that ;)

---

### Post by Favux on 2009-04-07
Hi maspin,

OK, that's a bare bones xorg.conf.  If X breaks everytime you try and edit, maybe it is because there is no "ServerLayout" section at the bottom.  It looks more Jaunty than Intrepid.

So we are on the same page.

-You are running Intrepid?
-You want to set up tablet features in Intrepid?
-You have not installed the ATI proprietary driver "fglrx" through System>Administration>Hardware Drivers?  If you haven't don't.
-You are not running Compiz?

If the above is true go to Loic2's Wacom wiki:

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

And install the two amd64 deb.s near the top under the Ubuntu 8.10 header.  The xserver-xorg-input-wacom 0.8.1-6 deb and the wacom-tools 0.8.1-6 deb.  Double click on each and let the Debian installer install them.

---

### Post by maspin on 2009-04-08
Hey!

I followed this ([http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)) to the T.

I got it to actually recognise my touchscreen.. Of course, the calibration was way off. But I can work on that tonight.

My only issue from there, was when I booted again, it went into low graphics mode. Saying that there was no screen detected or something?

It's a bare-bones Jaunty install. I didn't get around to that ATI driver this time around (I reinstalled it yesterday, as one of my xorg.conf attempts froze Ubuntu up, even in recovery mode, and I couldn't edit it.)

I have to work today, but as soon as I am home, I think I can fix it.

Thanks for all your help!

Matt

---

### Post by maspin on 2009-04-08
Okay.. When I follow the steps I mentioned above (before even touching xorg.conf), I have touchscreen, but when I open wacomcpl, there is no device listed, so I cannot calibrate the screen..

When I add those lines to xorg.conf, Ubuntu does not boot anymore.
Attached is my xorg.conf, with the lines added to it. I added in

# This is what I have added

to show where I put the lines in.

Any suggestions?
Thanks!

Matt

---

### Post by Favux on 2009-04-08
Hi maspin,

So we are on the same page.

-You are running Intrepid?  No, Jaunty
-You want to set up tablet features in Intrepid?  No, Jaunty
-You have not installed the ATI proprietary driver "fglrx" through System>Administration>Hardware Drivers? If you haven't don't.  No
-You are not running Compiz?  No

As the HOW TO says it is for installing linuxwacom in Intrepid.  I don't have it ready for Jaunty yet.  Which version did you compile?  0.8.2-2?

It looks like they (Xorg) have made changes to xorg.conf with the new Xserver 1.6.  Intrepid has 1.5.  I don't know or understand the changes they've made to xorg.conf so we are experimenting.

So let's experiment.

At least with Intrepid your "ServerLayout" would be wrong.  Instead of:
```
Section "InputDevice"
      Inputdevice       "stylus"         "SendCoreEvents" 
      Inputdevice       "eraser"         "SendCoreEvents" 
      Inputdevice       "touch"          "SendCoreEvents"
EndSection
```
It should read:
```
Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"touch"		"SendCoreEvents"
EndSection
```
It is possible the usb inputs have changed too I suppose.  Do you have a file &#8220;50-xserver-xorg-input-wacom.rules&#8221;, or something similar, in &#8220;/etc/udev/rules.d/&#8221;?

---

### Post by maspin on 2009-04-11
Okay,

I have 0.8.2-2 here.
I did xorg.conf as you said, and no more booting problems
I do not have the "50-xserver-xorg-input-wacom.rules" file, how important is it?

I still can't see my device listed in wacomcpl, so I cant calibrate it. The touchscreen only moves the mouse around in the top left corner of the screen. :(

Thanks again for your help!

---

### Post by Favux on 2009-04-11
Hi maspin,

I need to know how you got 0.8.2-2.  Did you get it through Synaptic?  Or did you compile it?

If you don't have "50-xserver-xorg-input-wacom.rules" you can't use the wacom symlinks.  So for your input path in xorg.conf for stylus and eraser:
```
	Option		"Device"	"/dev/input/wacom"
```
and touch:
```
	Option		"Device"	"/dev/input/wacom-touch"
```
won't work.  You have to use the pci input path.  Since you have a TX2500 it would be for stylus and eraser:
```
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
```
and for touch:
```
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
```
At least that is what they were for Hardy and Intrepid.

Touchscreen only showing the pointer in a corner usually means X isn't detecting any input.  Is that just for touch (your finger) or also stylus and eraser?

I need to see your current xorg.conf.  At least its not breaking X in Jaunty anymore!

---

### Post by maspin on 2009-04-11
I have the "50-xserver-xorg-input-wacom.rules" file now, followed appendix 3 of your guide.

Everything seems fine and stable, but wacomcpl still shows no devices

It is blank, and only has an exit button available.

I got 0.8.2-2 compiling by your walkthrough before :)

---

### Post by maspin on 2009-04-11
Well for anything, touch, stylus, eraser. Its all limited to about a 3x3 cm square at the top left screen.

So, after following appendix 3, I changed my xorg.conf to have:

	Option		"Device"	"/dev/input/wacom-touch"

The touch and stylus still works, but only in that top left section.

---

### Post by Favux on 2009-04-11
Hi maspin,

Remember its wacom for stylus and eraser and wacom-touch for touch.

We are stuck because you can't calibrate because you don't see any input devices in wacomcpl.  On the left as you know you should see stylus, eraser, and touch.  And when you click on them options should appear including calibration for stylus and touch.

The only time I have seen this is when there is an old version of either the driver or wacom-tools causing a conflict.   We can search through your files trying to find all instances with wacom in them and check the versions.  Of course I'm sure you're wondering like I am if this is a problem being caused by Jaunty.

You could try and insert my .xinitrc file ( a hidden file in the "/home/username/" directory generated by wacomcpl and hope it works.  Keep in mind I have a TX2000 so there may be some differences.

You didn't post your xorg.conf.  There should be crude calibration in it.  If you have it in your xorg.conf try commenting it out.  If not I'll show you examples.  It's the "TopX" to "BottomY" lines.

.xinitrc (see section 3 of the kernel driver HOW TO)
```
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 10 90 100"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set touch bottomy "3969"
xsetwacom set touch bottomx "4028"
xsetwacom set touch topy "215"
xsetwacom set touch topx "140"
xsetwacom set touch Capacity "1"
xsetwacom set eraser bottomy "16630"
xsetwacom set eraser bottomx "26416"
xsetwacom set eraser topy "-101"
xsetwacom set eraser topx "66"
xsetwacom set stylus bottomy "16630"
xsetwacom set stylus bottomx "26416"
xsetwacom set stylus topy "-101"
xsetwacom set stylus topx "66"
# run the primary system script
. /etc/X11/xinit/xinitrc
```
```
Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
	Option		"Type"		"stylus"
	Option		"USB"		"on"
	Option		"Button2"	"3"  # make side-switch a right button
	Option		"TopX"		"225"
	Option		"TopY"		"225"
	Option		"BottomX"	"26300"
	Option		"BottomY"	"16375"
EndSection
```
```
Section "InputDevice"
	Identifier	"touch"
	Driver		"wacom"
	Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
	Option		"Type"		"touch"
	Option		"USB"		"on"
	Option		"TopX"		"200"
	Option		"TopY"		"225"
	Option		"BottomX"	"4000"
	Option		"BottomY"	"3875"
EndSection
```
Since the eraser has the same input path as the stylus it follows its calibration.  You could also try manually playing around with the calibration lines in your xorg.conf if you do have them.  See if you can get more screen coverage.  Maybe the new version of Xserver, 1.6 in Jaunty, interprets the coordinates differently.  That's how things started out, guessing the coordinates and restarting X over and over to zero in on good ones.

---

### Post by Favux on 2009-04-11
Hi maspin,

It looks like there is a way forward in Jaunty.  Both gali98 and cywhale have compiled the new development 0.8.3-2 version of linuxwacom and used xorg.conf and have full Wacom function.

The new method still apparently has problems.  Read this thread:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952)

And also back to the linuxwacom kernel HOW TO:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

And read from post #65 forward:  [http://ubuntuforums.org/showthread.php?t=1038949&page=7](http://ubuntuforums.org/showthread.php?t=1038949&page=7)

Please be sure to read everything before making a decision.

---

### Post by maspin on 2009-04-14
Hey!

Sorry about the slow response. It has been a busy weekend. Best weather in a year so we did some gardening. And my partners family came over for Easter dinner.

BUT, I just tried 0.8.3-2, it works perfectly.
Touch, Stylus, Eraser, Right Click.. All of it!

Thank you a million times Favux! You are a life saver!

---

### Post by Favux on 2009-04-14
Hi maspin,

You're welcome.  Glad to help.

---

