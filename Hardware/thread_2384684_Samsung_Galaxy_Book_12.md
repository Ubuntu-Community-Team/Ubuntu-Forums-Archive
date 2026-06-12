---
title: "Samsung Galaxy Book 12"
date: 2018-02-10
forum: Hardware
---

### Post by makem2 on 2018-02-10
description: Detachable
    product: Galaxy Book 12 (GALAXY A5A5-A5A5-A5A5-A5A5-A5A5-PHAC)
version: P02HAC


Fn keys, Sound and Brightness now working with xubuntu 17.01.

Does anyone have this machine?

Is there any help with where to start to enable these?

---

### Post by makem2 on 2018-02-10
There is a typo in the above.

It should read, "[COLOR=#000000]Fn keys, Sound and Brightness NOT working with xubuntu 17.01".

I find these entries relating to brightness:

[/COLOR]```
makem@galaxy-book:~$ cd /sys/class/backlight/intel_backlight
makem@galaxy-book:/sys/class/backlight/intel_backlight$ ls -la
total 0
drwxr-xr-x 3 root root    0 Feb 10 16:59 .
drwxr-xr-x 6 root root    0 Feb 10 16:59 ..
-r--r--r-- 1 root root 4096 Feb 10 17:12 actual_brightness
-rw-r--r-- 1 root root 4096 Feb 10 17:12 bl_power
-rw-r--r-- 1 root root 4096 Feb 10 16:59 brightness
lrwxrwxrwx 1 root root    0 Feb 10 17:12 device -> ../../card0-eDP-1
-r--r--r-- 1 root root 4096 Feb 10 16:59 max_brightness
drwxr-xr-x 2 root root    0 Feb 10 17:12 power
lrwxrwxrwx 1 root root    0 Feb 10 16:59 subsystem -> ../../../../../../../class/backlight
-r--r--r-- 1 root root 4096 Feb 10 16:59 type
-rw-r--r-- 1 root root 4096 Feb 10 16:59 uevent
makem@galaxy-book:/sys/class/backlight/intel_backlight$

```

[COLOR=#000000]When I nano the above I find these entries:

[/COLOR]actual_brightness - 5000
bl_power - 0
max_brightness - 5000
[COLOR=#000000]power - 0

I even as root cannot amend these from nano, "[/COLOR][ File 'max_brightness' is unwritable ]"

[COLOR=#000000]Tee'ing a value does change it but has no effect on the actual brightness.

I do not understand this entry from above:

[/COLOR]lrwxrwxrwx 1 root root    0 Feb 10 16:59 subsystem -> ../../../../../../../class/backlight

Although I know it is a symlink.

[COLOR=#000000]Am I on the right track to adjust the brightness?
[/COLOR]

---

### Post by makem2 on 2018-02-10
Workaround from here:

[https://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/469040](https://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/469040)

Post #126

In my case:

```

makem@galaxy-book:~$ xrandr -q | grep "connected"
eDP-1 connected primary 2160x1440+0+0 (normal left inverted right x axis y axis) 252mm x 168mm
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
makem@galaxy-book:~$ xrandr --output eDP-1 --brightness 0.5
makem@galaxy-book:~$ 

```

Now my eyes and the battery can rest.

Next.......................sound!

---

### Post by mörgæs on 2018-02-11
> **makem2 said:**
> There is a typo in the above.

Then it's better to edit the post than writing a new one.

Your hardware is new. Have you tried if a live boot of 18.04 works better?

---

### Post by Nattydread69 on 2018-04-26
I have a samsung galaxy book 12 running ubuntu 18.04. 
Unfortunately changing the screen brightness with xranrd as discussed is broken with wayland on gnome 3. So I installed unity and it works again.

I have never got the sound working though :(

---

