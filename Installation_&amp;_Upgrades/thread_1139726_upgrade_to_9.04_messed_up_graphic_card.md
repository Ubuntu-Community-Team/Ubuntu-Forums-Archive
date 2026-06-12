---
title: "upgrade to 9.04 messed up graphic card"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by eidam655 on 2009-04-27
hi,

i finally managed to upgrade to 9.04. now i am facing one big and two small problems:

the big problem is that any application needing 3D acceleration acts weird. Compiz renders at constant 24.5 FPS (used to be ~180), Blender's redrawing is buggy (half of the screen just doesn't update), and finally OpenArena gives me very low FPS even at startup, menu etc. All of these used to work flawlessly in 8.10. NO, this is not the case of wrong window manager - i use Metacity by default and the problems persist.

i am on a laptop using Intel GMA950.

what can i do?

second problem is that Nautilus doesn't show desktop icons; they load only after i open any folder in nautilus by hand.

the third is that the soundcard is always muted at the startup and i need to set the volume and unmute it everytime. very annoying this is ;)

thanks for any replies

---

### Post by regala on 2009-04-27
> **eidam655 said:**
> hi,

i finally managed to upgrade to 9.04. now i am facing one big and two small problems:

(...)

i am on a laptop using Intel GMA950.

(...)



until some discrepancies are solved, no user of recent intel graphics should upgrade to 9.04. It shipped with xorg-server 1.6 which turns out to be a "development stage" for graphics chips.

To have correct behaviour with recent intel chips with xorg-server 1.6.x you need the latest intel driver (2.7). I think they are available in a PPA by Bryce Harrington, but I don't know if all regressions were fixed, as it is not really targeted for wide public use (Intel graphics infrastructure and in-kernel graphics infrastructure are in heavy development for a few months).
I won't give any advise about downgrading to xorg-server 1.5.x with a special crafted packet, as it is surely not supported. The safest path would be to downgrade to Intrepid back, but some Jaunty material are really cool...

---

### Post by eidam655 on 2009-04-27
yay, cool. so i wait a month without games... or get Arch Linux working. :P or just switch to Windows... not a convenient option ;)

what about the other two? has anyone found any workaround?

---

### Post by regala on 2009-04-27
> **eidam655 said:**
> yay, cool. so i wait a month without games... or get Arch Linux working. :P or just switch to Windows... not a convenient option ;)

what about the other two? has anyone found any workaround?

here I have a machine with 2D and 3D acceleration running (i.e. with and without compositing, smooth). but I run the latest git tree for a bunch of X stuff (libX11, libdrm, intel driver, xorg-server, mesa, xcb and the associated proto headers), and the last git kernel tree issued on kernel.org. It works, but I would not drag anyone who wants something rock-solid :)

The safest is to use a distro using no more than xorg-server 1.5.x

and the distro would not change anything, the thing is xorg-server 1.6 is not the solution for Intel chips users.

---

### Post by lariosa42 on 2009-04-28
Bump!

It does me no good showing off my new Ubuntu if I can't even show people that it has good 3D support.  

(Also, I am totally going through OpenArena withdrawl.  Does anyone know a face-paced non-3D game that can keep my brain awake while I work late nights?)

---

### Post by shatterblast on 2009-04-28
The safest thing I can think of is finding a .DEB file that has the latest Intel graphics firmware on it, but I'm use to nVidia.  Regala said it correctly with:

> **regala said:**
> 
To have correct behaviour with recent intel chips with xorg-server 1.6.x you need the latest intel driver (2.7). I think they are available in a PPA by Bryce Harrington, but I don't know if all regressions were fixed, as it is not really targeted for wide public use (Intel graphics infrastructure and in-kernel graphics infrastructure are in heavy development for a few months).


Here's a link to follow:

[https://launchpad.net/~bryceharrington/+archive/ppa](https://launchpad.net/~bryceharrington/+archive/ppa)

You can also add the "deb https:" lines under System -> Administration -> Software Sources -> the Third Party Software tab.  If you do so, don't forget to add the key to the Authentication tab as well that the "repository is signed with."

---

### Post by lariosa42 on 2009-04-28
Just found a fix on [here]("http://renesd.blogspot.com/2009/04/ubuntu-jaunty-half-speed-graphics.html").  I had to modify it slightly (my xorg was in a different place).  This is what I did:

Open the file xorg.config (your might be in a different place than mine) with your favorite text editor using sudo.

```

sudo gedit /etc/X11/xorg.conf

```

Next, find the place that reads
```
Section "Device"
Identifier "Configured Video Device"
EndSection
```
and replace it with
```
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
Option "AccelMethod" "UXA"
EndSection
```

restart your computer, and hopefully everything will work.  I'm back to playing OpenArena!  (Still can't get wide-screen, but it runs fast.)

---

