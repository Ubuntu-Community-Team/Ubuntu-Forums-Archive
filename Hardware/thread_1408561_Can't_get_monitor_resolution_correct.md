---
title: "Can't get monitor resolution correct"
date: 2010-02-16
forum: Hardware
---

### Post by Borbor on 2010-02-16
Hey, I've been using Ubuntu 9.10 for a few weeks now, liking it.
For a long time now I've been using a 26" LCD TV as a monitor, and when I use a VGA cable, the resolution is okay, meaning everything fits on the screen, but using HDMI I'm forced to either not see about an inch on all sides, or use a resolution not wide enough.
I'm using an Nvidia 9600 GT video card, and the model for the TV is Sanyo dp26648.

On windows, the Nvidia program lets me correct the HDMI resolution, so I know that the resolution I want is 1186x674, or something close to that, though the specs for the tv actually say 1366 x 768, but I doubt that would work. I looked around for a solution, but any guide to a customization I found didn't work, it's possible I'm repeatedly failing at the command line, but I'm not sure, just a minute ago I was sure I'd copied everything down right and got "Configure crtc 0 failed"
The computer reads the monitor (TV) as "SANYO LCD," not sure if that helps at all, but more info is better than none, right?

Also, not sure if this belongs in noob questions or hardware, so move if you wish.
Thanks

---

### Post by MRupe on 2010-02-16
Are you using the NVIDIA driver and display adapter or the ubuntu display set-up?

I am also new to Ubuntu but had this same problem when I hooked my NVIDIA 9400 M up through HDMI. TO resolve the issue I went in and updated hardware drivers [in the administration menu --> Hardware Drivers]. This should allow you to install the proprietary NVIDIA driver set. You can change the resolution from here to the best to fit your TV.

Im running mine 1080p through HDMI to a 55" Samsung, the NVIDIA Xdriver recognizes this immediately and corrected the resolution. The problem I now have (if it can really be called a problem) is that the I have to now resize the picture on my TV rather than leaving it at the natural 16:9 setting to the screen fit setting. However, I do now get a perfect 1080p resolution on my TV.

---

### Post by Borbor on 2010-02-16
Thanks, I tried and this Tv seems all kinds of ghetto, I can change the aspect ratio, put not to anything useful, and can't resize the picture manually. I've been using the "nvidia accelerated graphics driver version 185" since first installing ubuntu, but the resolutions that come with it just don't seem to be what I need, which I think is the real problem, I'm stuck between 1024x768 (so, non widescreen, black bars on both sides of the screen) and 1280x720 (missing ~one inch on all sides)

---

### Post by Borbor on 2010-02-16
sorry to bump, but bump.
I found another thread with a similar problem, [here]("http://ubuntuforums.org/showthread.php?t=970095"), and I've been fiddling with xorg.conf, to no avail, I tried every logical resolution here:
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    SubSection "Display"
        Virtual    1280 800
    EndSubSection
```
where I'm changing the numbers for "Virtual"
1186x674 (what I use in Windows) was frightful, everything was huge and I could see about 30% of the screen, having to guess where all the drop down menus etc were. 
I'm using 1280x800 right now because I can still see everything, although not in widescreen of course.

So, I'm not sure if I'm not the right track to a solution or not, anything would be helpful.

---

### Post by ScarySquirrel on 2010-02-21
Again, this user called jeanseb, and also tm3508, seem to have the same problem.
******* vidcard manufacturers. 
Someone needs to hack 'em and get the specs for these things. 
There's closed source, open source, and "forced" source. 

Related Posts:
[http://ubuntuforums.org/showthread.php?t=1405093&highlight=nvidia+driver+resolution](http://ubuntuforums.org/showthread.php?t=1405093&highlight=nvidia+driver+resolution)

---

### Post by ScarySquirrel on 2010-02-21
This looks similar to these problem posts:
[http://ubuntuforums.org/showthread.php?t=1307848&highlight=nvidia+driver+resolution](http://ubuntuforums.org/showthread.php?t=1307848&highlight=nvidia+driver+resolution)

[NVIDIA Resolution Problem]("http://ubuntuforums.org/showthread.php?p=8858582#post8858582")

[http://ubuntuforums.org/showthread.php?t=1405093&highlight=nvidia+driver+resolution](http://ubuntuforums.org/showthread.php?t=1405093&highlight=nvidia+driver+resolution)

[http://ubuntuforums.org/showthread.php?t=1194965&highlight=nvidia+driver+resolution](http://ubuntuforums.org/showthread.php?t=1194965&highlight=nvidia+driver+resolution)

:KS Whose SOLUTION, hopefully, can be found at this link:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

