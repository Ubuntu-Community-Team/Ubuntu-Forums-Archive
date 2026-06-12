---
title: "Xournal + Ntrig= a big mess"
date: 2010-07-31
forum: Hardware
---

### Post by new newb bie know none on 2010-07-31
Hi,
If anyone can point me in the right direction I would be gr8ful.  Xournal in Ubuntu 10.04 goes crazy when I use the pen and my palm touches the screen.  Tx2z laptop.  I am new to having to think for myself, so please go slow.  The last thing I programed was my Atari 5600 back in 86.  I think it was a lightning bolt.

---

### Post by Favux on 2010-07-31
Hi new newb bie know none,

You want to turn touch off.  See "5) Turning touch on and off" at the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---

### Post by new newb bie know none on 2010-07-31
Thanks for the reply Favux,
Xournal is not getting that message.  Touch is off everywhere but there.  Xournal likes to be touched.  Help me stop it before someone gets hurt.

---

### Post by Favux on 2010-07-31
If you have the default Lucid install touch is probably from evdev.  Did you try in a terminal?:
```
xinput float "N-Trig Touchscreen"
```
Also "N-Trig Touchscreen" is whatever "Device name" for touch 'xinput --list' shows.

---

### Post by new newb bie know none on 2010-07-31
That is the one that I used.  It shut touch off.  Xournal still has touch though.  If I move fast enough I can draw a zig zag. 

Thanks,
Scott

---

### Post by new newb bie know none on 2010-07-31
Also,  I cannot use touch for any menus or toolbar buttons within Xournal.  Touch only works for the actual writing part of the program.

---

### Post by Favux on 2010-07-31
Show me your output of 'xinput --list'.

---

### Post by new newb bie know none on 2010-07-31
netline@netline-laptop:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Touchscreen                          id=13    [slave  pointer  (2)]
&#9116;   &#8627; N-Trig Pen                                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=16    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=17    [slave  pointer  (2)]
&#9116;   &#8627; Kensington Kensington Ci75m Wireless Notebook Mouse    id=18    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]
&#8764; N-Trig Touchscreen                          id=12    [floating slave]
netline@netline-laptop:~$

---

### Post by new newb bie know none on 2010-07-31
that does not look so good

---

### Post by new newb bie know none on 2010-07-31
I tried to float 11, 12, 13, and 14 in various combinations to no avail.   When I float the pen it too still works in the pad portion of Xournal.

---

### Post by Favux on 2010-08-01
Right, there shouldn't be two "N-Trig Pen".  That may be the problem.  You have touch floated.

I gather you just have the Lucid default settings?  You want to use linuxwacom for the stylus.  Check the 10-wacom.conf in /usr/lib/X11/xorg.conf.d/.  You want the n-trig snippet to look like:
```
Section "InputClass"
 	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
 	MatchDevicePath "/dev/input/event*"
 	Driver "wacom"
	Option "Button2" "3"
EndSection
```
You can edit it with:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```

By the way a .txt file from gedit is more useful than an .odt file.

---

