---
title: "Ubuntu 9.10 on Toshiba m750 - Screen Calibration"
date: 2009-10-29
forum: Hardware
---

### Post by X-Kent on 2009-10-29
Hi.
I just installed new 9.10 on my toshiba m750, everything works OTB but I can't figure out how to calibrate the touch screen. The screen is calibrated OTB but when I rotate the screen the touch/pen input is not rotated. I once configured the this (on jaunty) with wacomcpl but now wacomcpl doesn't see any devices
"xsetwacom list" returns nothing

I downloaded a program named "Calibrate Touch screen" it now sits in system->administration but when I launch it complains about "evtouch" not found, not sure what that means.

Script that I used once:

# Toshiba M700 rotate script for bezel button

if [ -f /tmp/rotated ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate none
        xsetwacom set "cursor" Rotate none
        xsetwacom set "eraser" Rotate none
        rm -f /tmp/rotated && exit 0
else
        xrandr -o right
        xsetwacom set "stylus" Rotate CW
        xsetwacom set "cursor" Rotate CW
        xsetwacom set "eraser" Rotate CW
        echo 1 > /tmp/rotated && exit 0
fi
/usr/local/bin/rotate (END) 

But now, part of the script fails:
x-kent@slider:~$ xsetwacom set "stylus" Rotate CW
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'
x-kent@slider:~$ 

The screen (view) rotates but the touch/pen input is messed after the rotation. (xsetwacom doesn't work)
I tried configuring the "old way" with the xorg.conf method but I get this:

root@slider:/home/x-kent/Backup/Configuration/Slider# /bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig
Cannot autoconfigure port: Device or resource busy
root@slider:/home/x-kent/Backup/Configuration/Slider# 

Favux, seems I need you again buddy :-)

Just a note. I see a difference in the way it works now:
1: (pro) The bug in xournal that caused random lines([http://ubuntuforums.org/showthread.php?t=1183109](http://ubuntuforums.org/showthread.php?t=1183109)) disappeared (at least seems so)

2: (con) Interface is slower, when I write something with a pen, it responds slower.

---

### Post by X-Kent on 2009-10-31
still can't find a solution/

---

### Post by X-Kent on 2009-11-01
Ok, I managed to rotate.
I apt-get purge xserver-xorg-input-wacom xserver-xorg-input-all
Touch stopped working at all.
I used the old xorg.conf file from this thread [http://ubuntuforums.org/showthread.php?t=1055845&page=8](http://ubuntuforums.org/showthread.php?t=1055845&page=8)
and apt-get install (the same packages back)
and put the line to rc.local that binds the serial interface.
now xsetwacom list gives the output and everything seems to work (I can rotate)
I just copied that file to /etc/X11/xorg.conf, there was no xorg.conf by default, I created one.

I used my laptop today at uni for writing an realised that it is much much slower than it was once ! I am not sure how it currently works (.fdi or .xorg method, I think it's .fdi for now) but I want it to be as it was once.
How do I disable the .fdi so it will work the same way it was in jaunty ?

---

### Post by Favux on 2009-11-01
Hi X-Kent,

In Karmic they renamed the 10-wacom.fdi to 10-linuxwacom.fdi and it lives here:
```
/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi
```
You could just rename it 10-linuxwacom.bak or move it.  You could also comment out the serial section in the .fdi.  For a .fdi the comments look like:
```
<!--  -->
```
and you bracket what you want commented out with them like:
```
<!--  whatever you want commented out  -->
```

---

### Post by X-Kent on 2009-11-01
Hi Favux.
Thanks for a quick reply.
I found that .fdi file and renamed it to filename.fdi.bak
Rebooted - nothing chaged.
Touch/pen is working but very slowly (when I write, there is about 0.5-1 sec delay between me writing the text and it's appearing on the screen, it's very confusing to write this way)
I tried to setserial, but the device sill used by something.

root@slider:/# /bin/setserial /dev/ttyS0 port 0x338 irq 4 autoconfig
Cannot autoconfigure port: Device or resource busy
root@slider:/# 

root@slider:/# lsof /dev/ttyS0
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/x-kent/.gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
Xorg    1276 root    9u   CHR   4,64      0t0 1578 /dev/ttyS0
root@slider:/# 

Xorg still uses the device, should I disable something else so the wacom will start working as it worked in jaunty ? Is there anything I can read to see what was added and disable it ?

Thanks alot.

---

### Post by Favux on 2009-11-01
Hi X-Kent,

We can look at your "xinput --list" and Xorg.0.log and see if linuxwacom is attaching to your tablet, but I don't think that's the problem.  Unfortunately.

There seems to be a bug in Karmic regarding serial tablets.

Sanette with a m750 is having problems to.  See, starting with post #597, [here]("http://ubuntuforums.org/showthread.php?t=1038949&page=60").  You might want to contact him.  He posts on LWP too.

Some folks don't even see their stylus.  See posts [#350]("http://ubuntuforums.org/showpost.php?p=8145455&postcount=350") and [#352]("http://ubuntuforums.org/showpost.php?p=8150194&postcount=352").

The original Karmic forum thread:  [http://ubuntuforums.org/showthread.php?t=1280564](http://ubuntuforums.org/showthread.php?t=1280564)

And now two bug reports:

[https://bugs.edge.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181](https://bugs.edge.launchpad.net/ubuntu/+source/wacom-tools/+bug/383181)

[https://bugs.edge.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997](https://bugs.edge.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997)

Don't know if it's a linuxwacom bug or something else.  Join in the bug reports, start your own, make some noise.

---

