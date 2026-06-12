---
title: "Problem with volume knob"
date: 2009-12-28
forum: Hardware
---

### Post by Ram- on 2009-12-28
I am using Karmic Koala (9.10) on a Toshiba Satellite U-305. My volume knob is not working properly. If I try to lower the volume (by rolling the knob a little bit) it will keep lowering the volume forever and cannot be interrupted (the computer will freeze and will keep muting the volume). Same happens when I try to turn the volume up. So I just use my laptop making sure that I do not touch the volume knob :)

The volume control works very well if I control it from the panel inside linux (not from the hardware).

Thanks for all help.

Ram-

---

### Post by vanzippee on 2009-12-28
I would also like help with this.

I have a U300 toshiba satellite with the same issue.

I found some that said there was a evdev fix for intrepid, but then it was said that it wasn't really a fix at all because the problem is in the kernel.

So I would like someone, could tell what is happening, and if there is any chance of a fix. This seems like an old problem.

From what I gather the normal function of a button turns on, then sends an off signal. The wheel does not send an off signal so it just keeps going.
Some have had success with a ctrl-alt-F1/ctrl-alt-F7 to bring things back, but the wheel still does not work.

Here is the bug report, everything is in there:

[Bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706")

As you can see it has been going on for over a year so I hope we are close to a solution.

---

### Post by derekmbarnes on 2009-12-31
> **vanzippee said:**
> 
From what I gather the normal function of a button turns on, then sends an off signal. The wheel does not send an off signal so it just keeps going.

Same problem with my Toshiba Satellite M500; except instead of a wheel, I have a bar of touch-sensitive "media control" buttons. When I tap said buttons, they act as if continuously "on." I wondered if I might have deleted some software that switched these buttons off; the original Toshiba programs were deleted when I wiped the hard drive installing Ubuntu (silly me).

Will be keeping tabs on this thread for future developments.

---

### Post by wafflemelon on 2010-01-01
> **derekmbarnes said:**
> Same problem with my Toshiba Satellite M500; except instead of a wheel, I have a bar of touch-sensitive "media control" buttons. When I tap said buttons, they act as if continuously "on." I wondered if I might have deleted some software that switched these buttons off; the original Toshiba programs were deleted when I wiped the hard drive installing Ubuntu (silly me).

Will be keeping tabs on this thread for future developments.

Oh, I've had this also, but I thought it was just some random glitch.

---

### Post by 61north on 2010-04-30
This problem is still present in 10.4.  8.04 works fine, but in 8.10 this problem appeared.  It's remained a bug through 9.04, 9.10, and 10.4.

I filed a bug on this last year thinking it had something to do with notify-osd which was consuming 100% CPU when this happened.  Now, in 10.4, notify-osd is much better behaved and doesn't lock up the computer.

However, the volume runs away to max or min every time I try to adjust it.  I think I'll file a new bug on this.

Any suggestions which package might be the problem?

---

### Post by 61north on 2010-04-30
Well, I found that this bug has already been discussed at length at Bug #271706.  So no need to submit another.  Doesn't look like any permanent fix is available yet, but there are some temporary fixes if you can add a few lines to the keyboard driver source and recompile it.  

The temporary solution is here:

[http://ubuntuforums.org/showthread.php?t=974723](http://ubuntuforums.org/showthread.php?t=974723)

---

