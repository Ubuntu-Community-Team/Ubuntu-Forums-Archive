---
title: "AMD Catalyst with 1080p TV"
date: 2017-01-04
forum: Hardware
---

### Post by chellrose on 2017-01-04
I'm using Ubuntu 14.04 with xfce, dual-booted with Windows 7.  I recently swapped my old 720p TV for a larger Sanyo 1080p.  I am also using a small 720p TV as a second monitor.

Setting the Sanyo's resolution to 1920x1080 in amdcccle (Catalyst) causes the desktop to be stretched larger than the screen area.  Desktop icons and the xfce panel go off the edges.  I suspect this is due to the overscan (which I was able to fix in Windows).  In Ubuntu, Catalyst detects my Sanyo as a projector, and thus gives no adjustment/overscan options.  It does detect my smaller 720p as a "Digital Monitor" and has an Adjustments tab for that where I can set overscan.

I've googled this extensively, and most all I can find is "change the display settings in the TV itself".  There is a setting in my TV that fits everything on the screen properly at 1920x1080, but it makes the display generally unpleasant.  Most notably, it makes text look jagged.  Also, the TV's default display setting looks best in Windows and I'd rather not have to change the display every time I switch OS's.

Is there a way to force Catalyst to recognize the TV as a TV (or "digital monitor") so I can set the overscan value?  I have turned on HDMI-CEC in my TV; doesn't help.  I have it set at 1776x1000 currently as a workaround, but would like to take advantage of the full 1080p resolution.

I have tried using the open-source driver too, and it suffers from the same problem.

Thanks!

---

### Post by donbrew on 2017-01-04
I ran > xrandr --output HDMI-0 --set underscan on.  If that works for you, you can add that line to /home/*your name*/.xprofile.

---

### Post by chellrose on 2017-01-05
Thanks.  Upon running that command, I get

```

warning: output HDMI-0 not found; ignoring
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  141 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30


```

Running "xrandr --verbose" indicates that my monitor is called DFP1, so I tried replacing HDMI-0 with DFP1:

```
xrandr --output DFP1 --set underscan on
```

This resulted in an error:

```

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  141 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  31
  Current serial number in output stream:  31

```

and the display is still overstretched.

---

### Post by donbrew on 2017-01-05
You might try sudo.  Other than that, I'm no expert.  I spent hours GoOgling to find that for mine.

Another thing to try is changing the frequency, mine seems to fit better with 720P 30Hz than 1080P 60 Hz.

There is also a setting in setting>displays for scaling to one display or the other.

I have Ubuntu 16.04 with the built in AMD Radeon drivers, that may be the difference.  I never could get Catalyst working right in Ubuntu.

---

### Post by chellrose on 2017-01-05
Ok, thanks for the suggestion.  Sudo didn't help, so I'll do some more digging on xrandr and see if I can sort this out.  At least I have something to explore now.  Thanks again.

---

### Post by deadflowr on 2017-01-05
If you got the catalyst drivers installed try setting things with the command line aticonfig command:
[https://manpages.debian.org/cgi-bin/man.cgi?query=aticonfig&apropos=0&sektion=1&manpath=Debian+7.8+wheezy&format=html&locale=en]("https://manpages.debian.org/cgi-bin/man.cgi?query=aticonfig&apropos=0&sektion=1&manpath=Debian+7.8+wheezy&format=html&locale=en")
man aticonfig or aticonfig -h or --help should bring up the list of options.
(One of those should be it)
I'm sure you can set overscanning options, fwiw.......

---

### Post by efflandt on 2017-01-05
Does your HDTV have any settings in its menus that may help? My 32" 1080p LG HDTV has a setting called "Just Scan" which tries to fill the screen with whatever video signal it is receiving on HDMI, which works better than its "16:9" setting. Samsung calls that "Fill Screen". Not familiar with Sanyo settings.

---

### Post by chellrose on 2017-01-11
> **deadflowr said:**
> If you got the catalyst drivers installed try setting things with the command line aticonfig command:
[https://manpages.debian.org/cgi-bin/man.cgi?query=aticonfig&apropos=0&sektion=1&manpath=Debian+7.8+wheezy&format=html&locale=en](https://manpages.debian.org/cgi-bin/man.cgi?query=aticonfig&apropos=0&sektion=1&manpath=Debian+7.8+wheezy&format=html&locale=en)
man aticonfig or aticonfig -h or --help should bring up the list of options.
(One of those should be it)
I'm sure you can set overscanning options, fwiw.......

Thanks.  aticonfig looks promising.  It has an option to set overscan "on" or "off" but this did not affect my display.  I still suspect that it's because my TV is detected as a projector.  I will have to play with it some more.

---

### Post by chellrose on 2017-01-11
> **efflandt said:**
> Does your HDTV have any settings in its menus that may help? My 32" 1080p LG HDTV has a setting called "Just Scan" which tries to fill the screen with whatever video signal it is receiving on HDMI, which works better than its "16:9" setting. Samsung calls that "Fill Screen". Not familiar with Sanyo settings.

Unfortunately, no.  My Sanyo has a "Full" setting that fits everything in, but it looks pretty bad.

---

