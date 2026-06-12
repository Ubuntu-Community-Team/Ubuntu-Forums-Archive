---
title: "Wacom"
date: 2011-01-15
forum: Hardware
---

### Post by bartekklimczak on 2011-01-15
hi all

am running ubuntu 10.04 on  hp 6730b laptop
had bamboo installed was working fine yeseteday

suddenly today it stopped working
is this because of updates
the light is on but nothing seems to be getting through
have uninstalled and reinstalled wacom insoftware centre followed the instrutions on the ubuntu site

still nothing
its very frustrating took forever to get it working in the first place and now it seems its not working agian for no reason

nothign has changed

the support from linux is crap

how can you very simply check to see if it is plugged in and working
really there should be a hardware configuration something like deice manager inwindows so you can see if installedand working properly

i even tried forcing updated back to no avail

grrrrr

all help much appreciated

---

### Post by Favux on 2011-01-15
Hi bartekklimczak,

Welcome to Ubuntu forums!

Is it one of the new Bamboo's with touch?

If so to get it working you must have compiled a new wacom.ko (the usb kernel driver) to get it working, because the default wacom.ko with Lucid doesn't have the new Bamboos in it.

If the updates included a kernel update that's the problem.  The new kernel came with a new modules directory that has the default non-working Lucid wacom.ko in it.  You need to recompile a working wacom.ko.  See the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

Hope this helps.

---

### Post by bartekklimczak on 2011-01-15
nope its almost 2years old, was working with laptop for the last 8 months no issues except of course getting it working in the first place

---

### Post by bartekklimczak on 2011-01-15
followed steps
got stuck here
after first command it says no such directory???


cd xf86-input-wacom

./autogen.sh --prefix=/usr

make

sudo make install

(Now reboot.)

---

### Post by Favux on 2011-01-15
Hi bartekklimczak,

If you have one of the older Bamboo's like a MTE you shouldn't need to update xsetwacom with Lucid, except maybe to get your pad (tablet buttons) to work.

What was the problem you had installing it originally?

Let's see if X sees your tablet.  Enter in a terminal:
```
xinput --list
```
and post the output.  To check your model/product ID:
```
lsusb
```
and post the line with Wacom in it.  Also let's see if the usb kernel driver wacom.ko is autoloading:
```
dmesg | grep [Ww]acom
```

---

