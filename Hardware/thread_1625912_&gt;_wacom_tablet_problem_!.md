---
title: "&gt; wacom tablet problem !"
date: 2010-11-19
forum: Hardware
---

### Post by bananartista on 2010-11-19
i need to make my wacom tablet intuos3 ptz930 
work properly on the last version of Ubuntu. 
i want to follow this method:
[https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver)
but i can't find in this list
[http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl)
the driver right for my 9x12 tablet.

what can i do ?



a real thank for your support.

---

### Post by Favux on 2010-11-19
Hi bananartista,

I'm surprised your Intuos3 doesn't work out of the box.  It's not new is it?  It's usb?  I take it you've installed Ubuntu Maverick Meerkat (10.10)?

The linuxwacom project now drops earlier drivers in a series when the next one comes out.  It's up to 0.8.8-10 which is why you can't find 0.8.8-6.

For Maverick you would only use linuxwacom to compile and install the usb kernel driver wacom.ko.  The linuxwacom X driver doesn't work on X servers 1.7 and higer (Lucid and Maverick).  So for the X driver wacom_drv.so you need Xorg's xf86-input-wacom.

So what's happening with your tablet that you need drivers?

---

### Post by bananartista on 2010-11-20
hi Favux, 
the system recognize the tablet.
but
the problem is with the mouse,
it makes me use all the surface and not a little part.
(in this way is very uncomfortable).
and with the pen, the same issue,
i don't know how to regolate the work surface of the tablet.


there is a way to adjust the work area of the tablet for the pen and for the mouse ?

sorry if the question is trivial
but i'm a newbie :)

thanks.


(b)

---

### Post by Favux on 2010-11-20
Hi bananartista,

It sounds like you want to set the Mode to Relative from Absolute for the Wacom tablet mouse and the stylus.  Most people do use Absolute for the stylus, but Relative is fine if that's how you prefer it.  You can do that with xsetwacom commands.

Post the output of:
```
xinput --list
```
in a terminal and we can set you up.

---

### Post by bananartista on 2010-11-20
ok.
this is the output i get.

anan@olo:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 9x12 eraser                   id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 9x12 cursor                   id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 9x12 pad                      id=15    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Intuos3 9x12 stylus                   id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AcerOrbiCam                                 id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]


thanks.


(b)

---

### Post by Favux on 2010-11-20
Sure b.

So what you want is a script with these xsetwacom commands:
```
xsetwacom set "Wacom Intuos3 9x12 stylus" Mode "Relative"
xsetwacom set "Wacom Intuos3 9x12 eraser" Mode "Relative"
xsetwacom set "Wacom Intuos3 9x12 cursor" Mode "Relative"
```
I already have a script for the Intuous3 in post #2 at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").  And instructions to install it in step IV so it applies at startup.  You'd have to modify the script a little with your "Device names" and use of Relative.  Also note my Edit on ClickForce at the bottom of the HOW TO.

---

### Post by bananartista on 2010-11-21
i put this code for changing the cursor  ...

xsetwacom set "Wacom Intuos3 9x12 cursor" Mode "Relative"
but nothing changed ...

---

### Post by Favux on 2010-11-21
The "cursor" is the Wacom tablet mouse.  Did your Intuos3 come with a tablet mouse?  Did the command work on the stylus/eraser?

---

### Post by bananartista on 2010-11-22
yes, i can use the mouse on the tablet,
and i want to change his surface of movements.
the stylus is ok.
it works already right for me.

what'else i can try ?

---

### Post by Favux on 2010-11-22
That should be right.  Did you trying changing Relative to Absolute for the cursor to see what happens?

---

### Post by bananartista on 2010-11-23
yes i did, 
i open the terminal i wrote
xsetwacom
and after i put this line:
xsetwacom set "Wacom Intuos3 9x12 cursor" Mode "Relative
but nothing happened.

did i make something wrong ?

---

### Post by Favux on 2010-11-23
Looks correct, except you don't have the " after Relative.  You don't need the first xsetwacom, just the whole xsetwacom command.  But the just xsetwacom should have only spilled some verbiage.

---

