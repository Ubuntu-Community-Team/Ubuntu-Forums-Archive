---
title: "Hp DV1000 laptop backlight brightness keys"
date: 2009-10-22
forum: Hardware
---

### Post by Delvien on 2009-10-22
I am at a loss, in 5 years of linux and ubuntu I have never run into this much trouble trying to get something working. 

Here is the backstory: I have an HP dv1000, and I have installed Hardy, Gutsy, Intrepid, and Karmic, even opensuse, and I have the same issue. The Fuction + f7/f8 keys do not control my LCD backlight brightness.

Tried xev, when I open xev and hit the fn+f7/f8, I get no output, the same goes for when i try the "ubuntu wiki fixing hotkeys" method 

```
 sudo /lib/udev/keymap -i input/event5
``` produced no output (event5 was my keyboard at the time of the test)

Using the LCD brightness applet produced no change.

KDE produced no chance.

Gnome-Power-manager settings, produced no change.

Trying to echo in the value into my /proc/acpi/video/GFX0/DD04/brightness produced no change.

The brightness file in /proc/acpi/video/GFX0/DD04 states only <not supported> yet, no one else that has a dv1000 has experienced this with ubuntu, they are still able to change the backlight brightness in some way.

xgamma is not backlight brightness, only gamma correction. So that's a dead end.

Tried pretty much everything on the internet to fix this....


Anyone have any ideas?

---

### Post by Delvien on 2009-10-22
bump

---

### Post by dnova on 2009-10-31
I haven't tried this yet for Karmic, but in Jaunty, use nvclock.
The command is nvclock -S ## (where ## is the number from 15-100 of the desired backlight brightness.

---

### Post by klap-in on 2009-11-10
in syslog log nonrecognised buttons may appear, with also a scancode mentioned.

Logviewer: System > Administration > Log viewer (or something like this in english..)

---

### Post by Delvien on 2009-11-17
> **klap-in said:**
> in syslog log nonrecognised buttons may appear, with also a scancode mentioned.

Logviewer: System > Administration > Log viewer (or something like this in english..)

Nope, says nothing :(

---

### Post by Delvien on 2009-11-17
> **dnova said:**
> I haven't tried this yet for Karmic, but in Jaunty, use nvclock.
The command is nvclock -S ## (where ## is the number from 15-100 of the desired backlight brightness.


I have an intel card :(

---

### Post by sjalex76 on 2010-02-20
try xbacklight

not an ideal solution, but it's working for me. I've got a lenovo g550 w/intel chipset also. the brightness buttons work fine under centos 5.4 but not in ubuntu; however xbacklight does the job.

I really want a way to make the builtin keys work, but no dice so far.

---

### Post by iTrickU on 2010-06-01
> **Delvien said:**
> I have an intel card :(

Which intel card? is it a core duo version?

---

### Post by punkmexic on 2010-06-27
i have the same computer
same problems
i wonder when someone is gonna save us from this problem 
im starting to hate intel

---

### Post by zemoffm on 2010-08-20
I'm also having this same issue on 10.04.  Hp pavilion dm1z-2000.  Its really frustrating and I have no idea what to do.  Using the ubuntu wiki, I saw the same issue as the original poster, that the FN keys for brightness weren't even registering a keypress, except on my machine they are f3 and f4.

Any help would be greatly appreciated.

---

### Post by punkmexic on 2010-08-20
My monitor sometimes if i moved it... it went black..then i took my laptop to a computer repair place...they offered me to change the monitor but that was expensive and i said no...then they told me that they can grab a piece of other dead laptop...and put it in mine

I IMAGINE they did this 
[http://www.youtube.com/watch?v=UT2GFVem_9U](http://www.youtube.com/watch?v=UT2GFVem_9U)

it cost like 8 dls only..i paid like 40dls
but now i can shift my brightness perfectly in linux or windows, before i changed the piece.....i only could do it in xp with an intel app.

---

### Post by punkmexic on 2010-08-20
My monitor sometimes if i moved it... it went black..then i took my laptop to a computer repair place...they offered me to change the monitor but that was expensive and i said no...then they told me that they can grab a piece of other dead laptop...and put it in mine

I IMAGINE they did this 
[http://www.youtube.com/watch?v=UT2GFVem_9U](http://www.youtube.com/watch?v=UT2GFVem_9U)

it cost like 8 dls only..i paid like 40dls
but now i can shift my brightness perfectly in linux or windows, before i changed the piece.....i only could do it in xp with an intel app.
__________________
Punkmexic 
Linux registered user #429629

---

