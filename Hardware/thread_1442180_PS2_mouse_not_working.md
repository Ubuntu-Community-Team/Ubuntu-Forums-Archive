---
title: "PS/2 mouse not working"
date: 2010-03-29
forum: Hardware
---

### Post by bapatons on 2010-03-29
Hi folks,

A little background:

I have several Dell PC's which I was intending to place Ubuntu on to compliment another set of similar old systems. This particular model seems to be experiencing some difficulties so I'm assuming, as all of the same model exhibit the problem, that it's hardware/driver related. I *think* the model is a Dimension 2300, will clarify this tomorrow.

Specification for the Dimension 2300 - [http://support.euro.dell.com/support/edocs/systems/dim2300/specs.htm#1101572](http://support.euro.dell.com/support/edocs/systems/dim2300/specs.htm#1101572)

The problem is even during the Ubuntu installation process, the mouse cursor appears but does not respond to any input. The mice I've tried work perfectly on other PC's, and several different mice react the same on these Dells, so I am ruling out the possibility of it being a faulty mouse at the moment.

I have ran through a full install on two separate PC's of the same model with the same results; the mouse is again non-responsive even after installation.

What to do?

I see there have been a few threads here about mice freezing or initially working then failing for various reasons. I don't see anything directly related to my specific situation. I have tried to compare this system with another older Dell to see if I can find any differences. Unfortunately, I do not have the dmesg output here but will post it tomorrow if some kind folk would mind taking a look.

What I did notice was the dmesg output contained one entry saying "PNP: No PS/2 controller found", which seemed odd to me as this is a PS/2 mouse port. Is this likely to be an issue?

Also, would it be beneficial to include the Xorg log? I've had a look at it but am unsure what it is I'm looking for to be perfectly honest. Any other steps folk could recommend to narrow this problem down, or preferably resolve it, would be very much appreciated. 

I am also noticing that a number of resolutions for similar problems seem to be related to the graphics driver; should I consider this as a possible problem also?

Thanks for any suggestions,

Baps.

---

### Post by mörgæs on 2010-03-30
Which Ubuntu versions have you used?

---

### Post by bapatons on 2010-03-30
Hi mörgæs,

Apologies I forgot to mention that. It's Ubuntu 9.1 (32bit). I didn't have time today to look at the systems, but they are actually Dimension 2400's.

[http://support.euro.dell.com/support/edocs/systems/dim2400/en/sm_en/specs.htm](http://support.euro.dell.com/support/edocs/systems/dim2400/en/sm_en/specs.htm)

Possibly worth noting, I have to use the virtual terminal and it is extremely slow on all of these boxes. Also, periodically they black screen after the splash screen so if it is a possible graphics card issue that's looking more likely.

Any suggestions as to how to move forward with the problem would be greatly appreciated. I should get time to attach some logs/details tomorrow.

Many thanks,

Baps.

---

### Post by mörgæs on 2010-03-31
According to 
[http://www.ubuntuhcl.org/browse/search?keywords=dell+dimension](http://www.ubuntuhcl.org/browse/search?keywords=dell+dimension)
the Dimensions (also the 2400) should work well with Ubuntu. 

Please post the output from ```
hwinfo --gfx
``` and ```
hwinfo --mem
```

---

### Post by bapatons on 2010-03-31
Thanks for the help, it's very much appreciated.
I've attached the requested details as well as the dmesg output and Xorg log.

Baps.

---

### Post by bapatons on 2010-03-31
Hey folks,

I tried a USB mouse of my own on the system and it works perfectly. Although it is an option to go out and buy 20 x USB mice, it would be nice to use the 20 perfectly fine mice we have here. 

It's no longer a major issue as this is a possible workaround, but it would be nice to know what the cause is, if only for my own sanity.

Baps.

---

### Post by mörgæs on 2010-03-31
hwinfo --mem indicates that you have only 256 MB memory. This explains why your system in general is slow. Before going any further: Are you sure that you will stay with Ubuntu? Puppy Linux might be a good alternative.

[http://www.puppylinux.org/](http://www.puppylinux.org/)

---

### Post by bapatons on 2010-03-31
Hi mörgæs,

Yes, there is indeed only 256Mb in these boxes, although low it is sufficient for our purposes at present. It may be upgraded if they are deemed suitable after a review period. 

When I say the virtual terminal is slow though, I mean it responds to about 1 keystroke per second. With a regular terminal in the environment (now that there is a working mouse) typing speed is perfectly normal. I can check if this has been affected with a working mouse attached if you think this would shed some light on the matter?

Baps.

---

### Post by mörgæs on 2010-03-31
Hi Baps.

Yes, please. Would be good to know how it behaves with a USB mouse.

Another test is booting a 10.04 live CD and see if it works with the PS/2 mouse (which it does on my machine)
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is in beta, but surprisingly stable.

---

### Post by bapatons on 2010-04-01
Just tested the virtual terminal, it works just fine with a USB mouse attached, it's only dead slow with a PS/2 mouse.

I'll try the beta release shortly and see how it reacts with the PS/2 mouse.

Regards,

Baps.

---

### Post by bapatons on 2010-04-10
Mouse aside, I've run into more pressing issues.

The majority of the time these systems will not boot correctly. I've made some changes which I should outline.

The systems start with 3 possible outcomes.

1) Splash starts, fschk runs and throws no problems but then the system blackscreens and is not responsive in any way.
2) Splash starts, system throws an error "General error mounting filesystems" and attempts to enter an emergency shell, which sometimes works, sometimes fails.
3) System boots normally.

Having spent hours trawling forums for this I have changed the grub2 config to disable the UUID references and updated grub which now uses /dev/sda1 for the / fs and /dev/sda5 for the swap fs instead of the UUID's. I've also updated fstab to do the same and this information matches what I have in fdisk -l.

If I choose to boot into a recovery console from the grub menu, then login and startx, everything starts normally every time.

Any suggestions as to what to try next? I have to say this is getting to the point of considering another distribution entirely, which would be a shame.

Thanks in advance,

Baps.

---

### Post by mörgæs on 2010-04-11
> **bapatons said:**
> I have to say this is getting to the point of considering another distribution entirely, which would be a shame.


I think it would be wise, if not for anything else then just for comparison. You could try Puppy and see how that goes. 

The 10.04 Beta has had problems the latest days (isn't it always like that - when you recommend something, it breaks?) 
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)
I don't think it is worthwhile following that road for the next couple of days. 

Another option is reinstalling 9.10 and post again all your experience in Absolute Beginners Talk, where there is a lot more activity.  Sorry, I am running out of ideas besides that :-(

---

### Post by bapatons on 2010-04-11
That's no problem mörgæs, I appreciate the help you have already given me.

I think I'll try a reinstall once more and see how that goes.

Baps.

---

### Post by bapatons on 2010-04-11
Quick update; seem to have the black screen issue sorted, doing some testing to be sure but I changed the grub2 config to use nosplash noquiet on boot and so far 10/10 successful boots.

I have no clue why this would be a problem, but so far looking good. Here's the thread I found this suggestion on for anyone who might be interested.

[http://ubuntuforums.org/archive/index.php/t-386920.html](http://ubuntuforums.org/archive/index.php/t-386920.html)

Baps.

---

### Post by mörgæs on 2010-04-11
Good!

By the way, if you want to run Ubuntu on a machine with only 256 MB memory, a minimal install might be interesting:

[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

The thread is long, but worth (speed)reading.

---

