---
title: "Laptop Hotkeys work in Ubuntu. How to make it work in other distro?"
date: 2007-07-31
forum: Hardware &amp; Laptops
---

### Post by raul_ on 2007-07-31
The title is self explanatory. 

I use Arch, but my brightness and volume keys don't work, so I decided to see if they worked in Kubuntu Live cd, so I could know if it was an hardware issue, or a distro issue.

Turns out they worked out of the box.

Where are these settings tweaked? Is there a driver, a configuration file, ANYTHING? I like ubuntu, but it feels like such a waste using an i386 distribution :(

---

### Post by aysiu on 2007-07-31
These instructions are for Gentoo, but you might find them helpful:
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys)

---

### Post by raul_ on 2007-07-31
Funny. I have the habit of browsing the Gentoo wiki (IMHO the best Linux How-to's resource) and I didn't find it. 

I made a progress with that link though. Check these outputs:

```
[root@apolo raul]# cat /usr/share/X11/XKeysymDB | grep Volume
SunAudioLowerVolume     :1005FF77
SunAudioRaiseVolume     :1005FF79
XF86AudioLowerVolume    :1008FF11
XF86AudioRaiseVolume    :1008FF13
[root@apolo raul]# cat /usr/share/X11/XKeysymDB | grep Brightness
SunVideoLowerBrightness :1005FF7B
SunVideoRaiseBrightness :1005FF7C
XF86BrightnessAdjust    :1008FF3B

```

Now I just have to find the raw Fn+Fx keycode :)


PS: Thanks :)

---

### Post by raul_ on 2007-07-31
Too bad. My Fn+Fx or even Fn don't produce any output with xev :(

---

### Post by raul_ on 2007-07-31
And it seems that the Sun* thing doesn't work either :(

---

