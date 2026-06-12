---
title: "Wacom Artpad II serial and Lucid"
date: 2010-10-11
forum: Hardware
---

### Post by JRBASTIEN on 2010-10-11
Hi everyone,

I have a wacom Artpad II serial (KT-0405-R) that I'm trying to setup in Lucid 10.04.  So far, I got it to work with limited success.  Many thanks to Favux for his great How-to ([http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1)) and the community on this one ([http://ubuntuforums.org/showthread.php?t=1480915](http://ubuntuforums.org/showthread.php?t=1480915)).

Basically, I have done the following:

1. Updated the kernel drivers to linuxwacom 1.0.8.8-9
2. Updated Xorg's xf86-input-wacom to 0.10.6 with the serial patch  xf86-input-wacom_git-20100511.patch (I could not find a patch that worked on 0.10.7 or 0.10.8 ).
3. Configured /etc/X11/xorg.conf (I was too confused with the recommended method for Lucid using 10-wacom.conf)
4. Restart the computer and could not see the cursor moving with the stylus.
5. Tested the tablet with the wacdump utility that comes with the kernel driver (wacdump /dev/ttyS0).  To my surprise, it was working fine.  To my greater surprise, the cursor could now be controled by the stylus after that I closed the terminal screen.
6. I finally configured GIMP and inkscape to work with the tablet.

3 problems remain:

  1.  How can I activate the tablet at startup without starting the wacdump utility?
  2.  Pressure sensitivity does not work at all in Inkscape or GIMP even though it is detected fine with Wacdump.
  3.  I have this error if I try to use the command xsetwacom:
      xsetwacom: error while loading shared libraries: libwacomcfg.so.0: cannot open shared object file: No such file or directory

I'm attaching my Xorg.0.log and Xorg.conf for more details.

Thanks in advance to anyone who has a suggestion.

---

### Post by Favux on 2010-10-12
Hi JRBASTIEN,

Really really nice work!  :)

I know there are a lot of serial tablets who can benefit from what you've done so far.  Hopefully we can tweak it some more.

Back up your current xorg.conf and see if this one changes anything.

Does the Artpad II have a Wacom tablet mouse?

---

### Post by JRBASTIEN on 2010-10-12
Hi Favux,

Thank you so much for helping.  No, this tablet does not have a mouse, this is why I had taken out the cursor input.

I just tried your xorg.conf file and the results are the same.  I can't get it to work until I start wacdump.

I'm attaching my Xorg.0.log file.  It is pretty much the same as before...

---

### Post by Favux on 2010-10-12
Hi JRBASTIEN,

> I just tried your xorg.conf file and the results are the same. I can't get it to work until I start wacdump.
Good!  I didn't break anything.  I think it's useful to have a cleaned up xorg.conf for Serial tablets.  I'm not sure how useful the 10-wacom.conf would be anyway, since you don't hot plug a serial tablet.  So using the xorg.conf may make more sense anyway.

You're right, no real changes to the Xorg.0.log that I see.

I know the LWP dev.s want configuration through the wacom.conf but I am not sure how useful/needed that is for Serial tablets, Serial tablet pc's, and USB tablet pc's.  We could go ahead and work up a Serial tablet snippet just for grins and on the off chance it would make a functional difference.  But I don't see any urgency on that.
> 2. Pressure sensitivity does not work at all in Inkscape or GIMP even though it is detected fine with Wacdump.
You're obviously an experienced user but I have to ask anyway.  You did configure the stylus and eraser through Gimp's and Inkscapes extended input devices, correct?  Did you see anything out of the ordinary when you did it?  I believe the other serial tablet users who tried one of the patch sets were reporting working pressure.
> 3. I have this error if I try to use the command xsetwacom:
xsetwacom: error while loading shared libraries: libwacomcfg.so.0: cannot open shared object file: No such file or directory
I'm fairly sure I've seen this error before but I'm drawing a blank on the context or how I fixed it, if I did.
> 1. How can I activate the tablet at startup without starting the wacdump utility?
There's been a long standing bug for Fujitsu serial tablet pc's.  They don't work on boot up and we've discovered if you just restart X with ctrl-alt-backspace they suddenly start working.  Let's see if that applies to your situation.

To enable ctrl-alt-backspace in Lucid:  System > Preferences > Keyboard > Layouts tab > "Key sequence to kill the X server", check the box in front of ctrl-alt-backspace.

---

### Post by JRBASTIEN on 2010-10-12
Favux,

I must confess that I'm not that experienced with Gimp and a graphic tablet.  When I bought this tablet many years ago, I was on Windows and Photoshop.

My mistake, pressure sensitivity is effectively working in GIMP.  With version 2.7, you need to open a separate window called Brush Dynamics to enable size and other parameters to change on pressure.

Considering that pressure works and that I have a way to activate the tablet, I can almost call it a success.

As for the xsetwacom error, I will try recompiling the xf86-input-wacom 0.10.6.  Does this utility comes with this code?  I may not have used the right prefix option (./configure --prefix=/usr).  Not sure if it is the problem.

Restarting X did not help. Thanks for the suggestion.

I'm stubborn.  If I fix everything, I will post a message with the detailed procedure.

---

### Post by Favux on 2010-10-12
> pressure sensitivity is effectively working in GIMP
That is good news.
> Does this utility comes with this code?
No.  The Xorg developer Peter Hutterer, responsible for xf86-input-wacom, dropped wacdump, xidump, and wacomcpl.  He feels they are client side (user programs) that don't belong in a driver.  He's technically correct.  And besides we should be able to use Xorg equivalents.  Ping Cheng, the Wacom developer, has been more concerned with user experience over the years.  Apparently there was a long discussion and the upshot is we're lucky we still have xsetwacom.  Peter rewrote it for xf86-input-wacom.

I'm sorry restarting X didn't do it.  Trying a repeat of the patches and recompiling xf86-input-wacom makes sense.  If we're lucky that will fix the problem.  What we need to do is figure out the system state before wacdump and after to see what's initializing the tablet.  Through Xorg.0.log or something.  Is it flowcontrol or what?
> If I fix everything, I will post a message with the detailed procedure. 
That would be great!  In fact it would very useful for you to do a detailed HOW TO now, even given where you are.  You can always update it as you learn things.  And someone else might come along and figure something out.  So consider a new thread with your HOW TO in the first post.

---

### Post by JRBASTIEN on 2010-10-13
Hi Favux,

With your great help, I'm starting to understand better what is going on and I'm making progresses.

I resolved the XSetWacom problem by recompiling xf86-input-wacom.

Because X sever is version 1.7 and higher starting with Lucid, Xsetwacom is no longer provided with the linux wacom driver but with xf86-input-wacom.  Like I said, I could not find a "Serial" patched code for a version higher than 0.10.6 so I used the code that I found here: [http://sourceforge.net/projects/linuxwacom/files/](http://sourceforge.net/projects/linuxwacom/files/)

I'm also attaching the patch for those interested here because it is hard to find.

```

cd Desktop/cd xf86-input-wacom-0.10.6 (or where you have downloaded the 0.10.6 source code)
patch -p1 < xf86-input-wacom_git-20100511.patch
./configure (don't change the prefix here)
make
make install (or checkinstall if you prefer keeping a trace in Sypnatic).
```

Voila!  The only problem left is to initialize the tablet at startup.  For further troubleshooting, I added these options in the Xorg.conf file in the Section "InputDevice" of the stylus:

	Option "DebugLevel" "12"  # 1 providing the less info, 12 the most.
	Option "CommonDBG" "12"

I have attached the new Xorg.0.log trace but you can see that it did not add much to it.  When I initialize the tablet through wacdump, I get that strange log:

xf86WcmSerialValidate: bad magic at 2 v=e0 l=7


That's all for tonight!

---

### Post by Favux on 2010-10-13
Hi JRBASTIEN,

Outstanding!  Great work again.

So:
Pressure:  check
xsetwacom:  check   (it's a shame the patches don't work on any xf86-input-wacom later than 0.10.6.  There were a lot of bug fixes and additions to xsetwacom after that.)

I think the reason the debug lines aren't showing much in the Xorg.0.log is because the patches actually work well and there aren't any bugs to report.

I think it is possible that the error from wacdump is from running it on the wrong kernel or a Xserver => than 1.7.  There are a couple of bug reports that may be related.  This one is interesting:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/259659](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/259659)  Claus' script in post #14 might be useful.  You could put something similar into a launcher if all else fails.  By the way where did you get the wacdump you're using and how did you get it working in Maverick?

---

### Post by JRBASTIEN on 2010-10-14
Nice script by Claus.  I confirm that it can be used to activate the tablet in silent mode.  So far, the bad magic errors do not seem to affect the performance of the tablet.

Personnaly, I prefer to just create a launcher with wacdump /dev/ttyS0 and a nice icon from here: /usr/share/icons/gnome/scalable/devices/input-tablet.svg.

That allows me to test the tablet when I start it and this way it remains off until I need it.

Given it is very acceptable workaround (perhaps even better than having the tablet ON all the time and that I have spent a lot of time already on this, I will mark this thread as "Solved"

As for where I got wacdump, I'm puzzled.  It looks like I have compiled it last sunday!

Favux, a VERY BIG THANKS to you.  Guys like you make this incredible operating system more and more popular and accessible.

---

