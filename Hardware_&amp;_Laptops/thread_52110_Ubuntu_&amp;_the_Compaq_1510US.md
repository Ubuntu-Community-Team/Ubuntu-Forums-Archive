---
title: "Ubuntu &amp; the Compaq 1510US"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by lordkyellan on 2005-07-26
All right, here goes.

Before I get into the situation, I 'd just like to say that I fully believe that I have been everywhere on the web trying to sort out this problem. I've dabbled in many linux distros, including (but not limited to) RedHat, Mandrake & Knoppix, but I'm not yet a serious Linux user.

Now I'm into Ubuntu, which works fantastically on my home desktop, and I love it. I'd really like to get this Compaq laptop running with it as well.

The specs are:

Pentium 4 2.2 GhZ
512 MB RAM
Radeon Mobility M7 LW (7500)

The problem seems to be something in the display support. My LCD (which is particularly nice) has a native resolution of 1400x1050. However, whenever I try to boot into X with that resolution, the system hangs.

I have been able to get the computer working through a dpkg-reconfigure and forcing the screen into 1280x1024, but the screen is off-center and I can see a tiny bit of the top bar at the bottom of the screen.

I found on another forum that Ubuntu apparently misdetects my video card as a Radeon 9000 (it's a 7500) and have tried that reconfiguration of xorg.conf -- only to crash the X server entirely. I've since changed the driver in xorg.conf from 'ati' to 'radeon', but that doesn't seem to have helped the situation.

I've also attempted to change the HorizSync and VertRefresh rates in xorg.conf, but I can't find any kind of specs on the monitor for this thing, since it seems to be a mistake (the official specs for this computer state a max monitor resolution of 1280x1024.)

Does anybody have any further ideas?

---

### Post by macgyver2 on 2005-07-26
Is there any further information you can provide?  For instance...when you try to boot into X using your native resolution it hangs.  Is there anything in the Xorg log that looks like it may be related to the problem?

Meanwhile, I'm going to check with a friend of mine.  I think he may have (or have had) a notebook with that native resolution that he put Gentoo on.  I'll see what he has to say about it.  No promises on that front, though.

---

### Post by varunus on 2005-07-26
You may want to try the proprietary ATI drivers instead of the included ones.  Head over to the Hoary Tips and Tricks section of the forum, and look for "ATI Drivers 0.2" or something like that.  (There's an index of howtos there too.)

You should get better control over resolution and OpenGL.

---

### Post by lordkyellan on 2005-07-26
I looked through the Xorg log, and found this entry:

(II) Radeon(0): Not using default mode "1400x1050" (hsync out of range)

Now, this leads me to something else I've looked at.

When I do an xresprobe on my monitor, I get the max resolution, but no values for the HorizSync or the VertRefresh like it gets on a CRT, so I really have no idea what to set those values to.

**UPDATE** : I followed that HowTo and installed the fglrx drivers, but when I updated my xorg.conf and restarted the x server, it crashed and I had to copy back to the working configuration.

I'm now installing Ubuntu on another machine (a desktop, using an LCD monitor) and all of the possible resolutions appeared automatically. I don't know what's wrong with this Compaq, but it's getting frustrating fast. :)

---

### Post by macgyver2 on 2005-07-26
Okay...here's something I came across while reading random things about not-so-ordinary resolutions...

Under the Monitor section you can add

 ```
Option "IgnoreEDID" "True"
```
 
And that should apparently make it so the server doesn't take into account the (non-)information coming from your graphics system.

Now, the disclaimer here is that stuff like that probably has the potential to royally mess up your system. I never had to try something like that when I was dealing with my semi-rare resolution because fortunately I came across a great page that had special modelines when I put Linux on my notebook three years ago (it has a native resolution of 1280x768 which wasn't working "out-of-the-box").

Anyway, just thought I'd put that idea on the table. Maybe someone who knows more about it can weigh in...or you can just try it if you'd like.

---

### Post by lordkyellan on 2005-07-27
Well, first off, I'd like to say that I really appreciate the help.

At this point, we're still a no-go on both the native resolution, and getting the 1280x1024 to work properly. I don't know what the hell's going on, but I suspect it may be something to do with the xorg x server. I loaded up a Knoppix LiveCD (which uses xfree86, naturally) and that worked just fine on every resolution. A SimplyMepis LiveCD also works fine (also running xfree86, I think).

I've not given up yet, but I might be getting there. :) If anybody else has any ideas, feel free to chime in!

---

### Post by macgyver2 on 2005-07-27
When I migrated from xfree to xorg (I forget exactly when that was...sometime last year I guess) I was able to just copy over my old xfree config file.  So...have you tried looking at the knoppix config file once it's up and running?  Maybe you can spot a difference in that file from the one you're trying under Ubuntu (specifically in the hsync range).

Also, in your efforts have you tried this out yet?

[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

I think the guy I originally got my special modelines from used a generator like this originally...  Maybe it's worth looking at.

---

### Post by lordkyellan on 2005-07-27
I've searched all over the laptop booted into Knoppix from the LiveCD, but I can't find the Xfree86.conf file anywhere on it. Can somebody point me to where it might be hiding?

Thanks!

Edit: Oh yeah, and I tried that ModeLine generator. Either it doesn't work, or I don't know exactly how to input it into an Xorg.conf file (the line it generates is for Xfree86). All it does it crash the X server, just like pretty much every other change I've made to that file.

---

### Post by lordkyellan on 2005-07-27
My friends, this is a momentous day!

It finally works! I searched all over, but could not find the xfree86.conf file on Knoppix. As I was shutting it down, however, it gave me the Hsync and Vrefresh rates on my monitor! I put them into my xorg.conf file and restarted. The 1280x1024 still was off-center, but when I then proceeded to put my monitor's native resolution (1400x1050 as stated above) back into the xorg.conf as the primary display mode, it restarted and everything works! The screen is full and it's at its native resolution at last.

Thank you all for your help, and I look forward to much time with Ubuntu!

---

### Post by macgyver2 on 2005-07-27
Hey, congrats!  I'm glad you got it working finally!

---

