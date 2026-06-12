---
title: "[SOLVED] 686 kernel causes GL lag"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by vayde on 2006-08-05
Ok, this is definitely NOT a critical issue, but I recently upgraded to the 686 kernel, and Ive noticed my screensavers are totally lagged up.  They start, and seem to animate somewhere around 1 frame per second (probably faster, but it seems that way).

When I was using the 386 kernel there was no problem at all, if fact if I boot back to it, the screensavers hum along like they should.  It's only when Im in a normal Gnome session with the 386 kernel that I notice the problem.

Running Xgl and Compiz also fixes the problem, but Im not ready to make the permanent switch.  There has got to be a simple solution.

help?

---

### Post by evil_elman on 2006-08-05
Make sure the driver for your graphics card is working fine under 686 as well as 386 kernels...

When I installed the 686 kernel I lost hardware acceleration for some reason and had to re-install the driver.

Try 'fglrxinfo' in a terminal and make sure it doesn't say 'Mesa' anywhere to make sure...

---

### Post by vayde on 2006-08-05
As far as I can tell, it's all set up correctly.  fglrx is kicking some serious tail on nwn.  

```

vayde@Talathar:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5946 (8.27.10)

```

I only notice the problem with the screensaver.

---

### Post by megamads on 2006-08-05
If your graphics are set up properly and you have a Pentium M / Celeron M processor, this could be caused by a bug in the 686 kernel. The 386 kernel does not have this bug, so you can use that until a fix is released or you can try the following workaround:

Enter this as root when booted into the 686 kernel (use su, sudo won't work):

```
echo 1 > /sys/module/processor/parameters/max_cstate
```

More info about the bug is here (the bugfix will also be announced there):
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30557")

Edit: This workaround also helps if you are experiencing problems with cpu scaling.

---

### Post by vayde on 2006-08-06
I thought they fixed that.  I was definitely having trouble with it.  My cpu was idling between 30% and 60%, and everything was very unresponsive.

I just switched back to the 686 kernel because someone told me it was fixed, and at least the problems I was experiencing on that note don't seem to be present.

Just to be sure, I have just recompiled and reinstalled fglrx per instructions, and the problem persists.

```

 echo 1 > /sys/module/processor/parameters/max_cstate

```
The above yields nothing. 
cat /sys/module/processor/parameters/max_cstate yields '8'

I don't know what either of those things mean, but Im thankful for the help.

---

### Post by megamads on 2006-08-06
Hmm. Yeah, you are right. It's supposed to be fixed now! Some people are still reporting problems with it though.

The echo command isnt supposed to give you any feedback, its just sets the max cstate. It will only do so for the current session, mind. After a reboot the cstate will be set back to 8.

But if

```
cat /sys/module/processor/parameters/max_cstate
```

prints out 8 after you have done the echo command, its probably not working for you and i'm out of ideas :-| 

good luck!

Edit: The new kernel works dandy on my HP dv1000 with a celeron m processor!

---

### Post by vayde on 2006-08-06
Aha! I understand.  I was confused.  No, your echo command worked, I just didn't understand the context.  It locked my cpu in that state. It was after a reboot that I catted it.  

Now armed with a better understanding I repeated the experiment, but the screensaver performance was unaffected.  Thanks for the help though, and the lesson.

Ive reinstalled gnome-screensaver and libglut3.  Reinstalling gnome-screensaver made things improve somewhat.  Reinstalling libglut3 did nothing at all as far as I can tell.

It's wierd though, the screensavers positively scream when I login to a xgl/compiz session.

---

### Post by vayde on 2006-08-08
Ok, this has gone beyond annoying.  The screensavers are locking up my box to the point that apps running in the background stall out.  Forget setting something to run and then walking away.  Likewise playing music is out unless Im sitting at the box, or I turn off the screensavers.  I've reinstalled/ reconfigured everything I can think of to no avail.

---

### Post by vayde on 2006-08-09
Ok, final chapter in this pathetic oddessey.  I disabled gnome-screensaver and went back to xscreensaver and lo and behold, all problems disappeared.  

It now runs the most graphics intensive screensavers without even causing the cpu to hiccup.  The fans don't kick in, heat doesn't go up, and most of all, music playback is uninterrupted.  

Since I'm the only one complaining about this problem, I can only suspect that it's my problem somehow.  In any event, the xscreensaver front end is way more user friendly, has more features, and seems to be an all around better solution.

I can only hope that in the future we will be able to choose between gnome-screensaver and xscreensaver without having to resort to so much trouble.

---

### Post by djembe330 on 2006-08-16
You are not the only one with problems concerning gl and gnome-screensaver.  When I first installed ubuntu about a month ago screensaver seemed to be fine (as i can recall).  When I installed the repo fglrx driver (ati x1400 in my notebook) I got the same problems.  I am also running 686 kernel since i have dual core.  After much searching I switched to xscreensaver.  I forget why, but after less than a day I switched back to gnome-screensaver.  After switching it worked!  I don't know if I did any funny business between the switches, but everything was working great with gnome-screensaver.  Now I did a manual install of the newest ati (8.27.10 - installed correctly) and its broken again.  Tried doing the "trick" of switching to xscreensaver and back and no good.

at a loss now...but has something to do with the way it is rendered.  xscreensaver allows you to pick between gl and other methds, and if I pick "truecolor" i get the same problems as with gnome-ss.  when i switch back to gl it works great.

hmmm.....just my 2 cents

---

### Post by vayde on 2006-08-16
Wierd.  I posted it as a gnome-screensaver bug thinking if it was truly just my problem I'd get slapped down pretty quickly.  I haven't heard anything about it.

For the time being, Ill stick with xscreensaver.  I prefer the functionality of the control gui.  I miss out on some of the power management: xine doesn't disable the screensaver automatically, and closing the laptop doesn't lock the screen, but on balance I prefer these problems to gnome-screensavers.

Nice to know Im not the only one.

---

