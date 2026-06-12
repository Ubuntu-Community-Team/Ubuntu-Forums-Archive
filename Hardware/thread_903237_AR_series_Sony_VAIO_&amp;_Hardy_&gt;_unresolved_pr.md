---
title: "AR series Sony VAIO &amp; Hardy &gt; unresolved problems"
date: 2008-08-28
forum: Hardware
---

### Post by devill on 2008-08-28
As I have not managed to find a thread for AR series VAIO users I decided to open one, and sum up my experiences.

I have Sony VAIO VGN-AR550U laptop, and Hardy Heron installed about 2 weeks ago... 

Most of the things are working fine right out of the box, except for:

* Sound card needed a fix (see solution below)
* WebCam is not recognized, nor did it appear in lspci or lsusb 
* FN keys won't work except for volume controls 
* I did not manage to change back light settings, not even with xbacklight (returns: No outputs have backlight property)

*If any one could help me on the remaining problems, it would be appreciated!*

**Soundcard fix:**

```

sudo gedit /etc/modprobe.d/alsa-base

```

and add the lines below to the end

```
options snd-hda-intel model=vaio
options snd-hda-intel model=3stack probe_mask=1
```

Reboot, and hope for the best :-)

---

### Post by Nepherte on 2008-08-28
Related to the brightness problem: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/173652)

Try running these commands in the terminal:
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
sudo /etc/init.d/acpid restart
```
And try xbacklight again.

---

### Post by a3qp on 2008-09-09
Nepherte,
I have the same backlight problem than devill, although I have a Sony Vaio SR129E/B, with a Radeon HD 3470 graphic card. (and a amd64 Ubuntu Hardy version)

When I tried xbacklight, I got: "No outputs have backlight property"

I tried then what you said:

```

xrandr --output LVDS --set BACKLIGHT_CONTROL native

``` 

But I got:
```

a3qp@a3qp-laptop:~$ xrandr --output LVDS --set BACKLIGHT_CONTROL native
X Error of failed request:  173
  Major opcode of failed request:  159 (RANDR)
  Minor opcode of failed request:  15 ()
  Serial number of failed request:  14
  Current serial number in output stream:  14

``` 

So I couldn't try the next code instruction you said. 

I appreciate any help, since my screen is really dark now.
(not in windows).

Thanks,

---

