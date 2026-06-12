---
title: "Wacom Bamboo mte-450"
date: 2010-07-24
forum: Hardware
---

### Post by stay gold! on 2010-07-24
Before I get started I think I got some help from Favux in the past.

I'm on Ubuntu 10.04, and I have a Wacom Bamboo mte-450. What exactly would I have to do, in order to get it working with pen pressure and everything in gimp? I've read it works out of the box (almost?)

Any help would greatly be appreciated, thanks! :D

---

### Post by Favux on 2010-07-25
Hi stay gold!,

Is anything working?  Stylus etc.?  In Synaptic Package Manager is xserver-xorg-input-wacom installed?  Does the wacom.ko show up in lsmod?:
```
lsmod | grep wacom
```

---

### Post by stay gold! on 2010-07-25
I just installed Ubuntu, and I haven't had the chance to even test it. But I have used Ubuntu before and had a heck of a time getting pen pressure or anything to work. Let me try that first.

---

### Post by stay gold! on 2010-07-25
Ok, lsmod | grep wacom shows wacom in red.

In gimp I have no pen pressure, and the eraser thinks it's a pen as well. So I guess nothing works as planned.

---

### Post by Favux on 2010-07-25
It sounds like the stylus/tablet is working.  OK, try configuring your extended input devices.  That's near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").  Then for eraser point it to the eraser icon and once it assigns hit save at the bottom of the tool/icon panel.

Do the tablet buttons work?

---

### Post by stay gold! on 2010-07-25
Ok, I configured it like in the wiki, and i'm still not getting any pressure. Also "stylus" doesn't show up just bamboo, bamboo pad, bamboo eraser and bamboo cursor. But it does work otherwise.

---

### Post by Favux on 2010-07-25
They renamed everything.  I can show you how to figure it out.  Just enter in a terminal:
```
xinput --list
```

Good so everything seems to be working but pressure.  May need to update xf86-input-wacom.

---

### Post by stay gold! on 2010-07-25
with xinput --list i get
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo eraser                     	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo cursor                     	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo pad                        	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo                            	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=9	[slave  keyboard (3)]

```

---

### Post by Favux on 2010-07-25
So you can see:

stylus = Wacom Bamboo

and the others are obvious.

Any pressure in Inkscape, or Xournal, or anything?  If not you probably need to do II. from the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  You may want to do I. to update the wacom.ko also.

---

### Post by stay gold! on 2010-07-25
Ok, so after updating I still have no pressure sensitivity in anything. But it does recognize my stylus as a stylus now, instead of just plain Wacom.

But still no sensitivity.

---

### Post by stay gold! on 2010-09-17
I know it's 2 months later and sorry for bumping this thread, but I ended up back on Windows after trying to deal with this for too long. I thought my Wacom was supposed to work without issues, I'll be back Ubuntu when things run a bit more smoothly.

---

