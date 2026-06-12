---
title: "USB devices grab all user i/o on boot + wacom questions"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by larpon on 2007-02-12
Hey there...

I'm having a hard time setting up this wacom tablet (USB - Graphire (ET))...

And while trying to fix it.. I ran across this problem:

If I have the tablet plugged into the usb port on my computer (no matter which port)
On power up the kernel boots fine, and start X with the wacom tablet working (apart from a few things I'm trying to figure out.. got pressure and active area working)

.. but.. my keyboard and mouse aren't working..
Unplugging the tablet doesn't solve it.. if I unplug it and then plug it back in.. Nothing is working.. 
While I first thought this was an X issue I found out that the kernel still does this with certain types of usb devices..
e.g. If I plug in an iPod or my digital camera.. same thing happens..
It's a bit annoying because it makes the wacom tablet testing harder this way (have to restart X, while I could've had 'plug'n'play)..
This annoys me that I can't have the usb devices plugged in at boot time..

I can though.. plug the devices in after boot.. and everything works like a charm (apart from the wacom I'm fiddling with atm.)

Can anyone help out here?
Both keyboard and mouse are ps/2..

System is edgy running on 2.6.17-11 kernel w/KDE (Kubuntu.. upgraded from dapper via apt-get packages)

Regarding the wacom questions..
Does anyone know why Gimp some times displace the active cursor by some weird offset coordinates?
I'm running the lastest stable wacom drivers 0.7.6-4 and everything else works like a charm beside those weird displacements..

Thanks in advance for any help on this :)

---

### Post by larpon on 2007-02-13
Now that's a damn shame that nobody are having the same problems as I on this subject :( (this is a bump comment btw) :)

---

### Post by larpon on 2007-02-15
3rd bump :(

---

### Post by jaquio on 2007-02-15
the same thing happened to me
adding this to the kernel line of the grub config fix the problem (i see this somewhere in the kde page)

usb-handoff

sadly now the gimp don't recognize the extended peripherals, but the stylus eraser cursor works (stylus with absolute position, cursor with relative position)

im using kubuntu and beryl

---

### Post by larpon on 2007-02-19
Thank you _very_ much for this answer... It works!

Though it eats my ps/2 mouse control.. but that's not important right now :)

I'll see if the Gimp has changed behaviour

-edit-

Unfortunately not :(

It still ha a weird offset...
But your usb-handoff solution made testing easier now..

---

### Post by larpon on 2007-02-22
Yup... It's solved...

For the first problem I encountered the solution was to add the lines
```
usb-handoff
```

in my grub menu.lst in the kernel arguments..

examples:
```

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,3)
kernel          /vmlinuz-2.6.17-11-generic root=UUID=537411d6-c72c-484a-b46e-e18d830ae8fa ro **usb-handoff** quiet splash
initrd          /initrd.img-2.6.17-11-generic
savedefault
boot

```

That fixed my problems...
with the current wacom drivers I could change the previous:
```

       Option          "Device"                "/dev/input/mouse1"

```

fix as the wacom documentation describes back to:

```

       Option          "Device"                "/dev/input/mice"

```

as the x-server wouldn't see my PS/2 mouse anyhow...
But I changed it back to -mice- and it worked like a charm along side the
wacom tablet.

Now the second problem with The Gimp...

Is only partially solved.. but it's working in some cases...

I have somehow completely overlooked that the driver and tablet I have
don't like the
```

  Option        "TopX"
  Option        "TopY"
  Option        "BottomX"
  Option        "BottomY"

```
options IF you **don't** keep the correct aspect ratio to the pad.
It works in Xorg if it doesn't have the the correct aspect ratio but
gtk/gimp confusses and give the weird cursor offset..
(this isn't a Gimp problem.. I think it's GTK who displaces the coords)
So to get the Gimp work correctly I had to calculate the correct aspect ratio
from the pad to the active area on the pad.. and to the screen resolution.

Starting with this:
```

cat /var/log/Xorg.0.log

```
I found the lines:
```

(**) Option "Device" "/dev/input/wacom"
stylus Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Graphire tablet speed=9600 maxX=10206 maxY=7422 maxZ=511 resX=2032 resY=2032 suppress=2 tilt=enabled

```

where
```

(==) Wacom USB Graphire tablet speed=9600 maxX=10206 maxY=7422 maxZ=511 resX=2032 resY=2032 suppress=2 tilt=enabled

```

is the line we need.

the aspect ratio of the pad is thus:

ar = width/height (maxX and maxY)
ar = 10206/7422 = ~1.375

and my screen resolution is 1600x1200...

ar = 1600/1200 = 1.33333 etc.
luckily for me all normal non-widescreen resolutions have an aspect ratio of 1.3

which means that they fit the pad's (almost)..
so...

I wanted an active area that's smaller than the pad default size..

I wanted it approx. 2000px into the pad (from the top) which gives me a more sensitive pen.
```

  Option        "TopY" "2000"

```
Now as I am a complete dumbass at math...
a friend of mine cleared it out for me:

TopX = 2000px * 1.375 (the aspect ratio of the pad) = 2750px

thus getting:
```

  Option        "TopX" "2750"
  Option        "TopY" "2000"

```

for the BottomX and BottomY we have:

BottomX = PadmaxX - TopX, and
BottomY = PadmaxY - TopY
getting:
BottomX = 10206 - 2750 = 7456, and
BottomY = 7422 - 2000 = 5422

giving me:
```

  Option        "TopX" "2750"
  Option        "TopY" "2000"
  Option        "BottomX" "7456"
  Option        "BottomY" "5422"

```
to insert into my xorg.conf wacom device sections..
Restarted X... and Gimp finally had it right :)

Anyway I don't know if it's just me who had these problems so..

The only thing that I haven't been able to get to work in the gimp is
if you have a TwinView setup with different resolutions...

Hope this helps others than me...

Tablet and pen is:
Graphire ET (ET-0405-U)

Over and out

---

