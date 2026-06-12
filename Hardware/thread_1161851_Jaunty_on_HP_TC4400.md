---
title: "Jaunty on HP TC4400"
date: 2009-05-17
forum: Hardware
---

### Post by alawson on 2009-05-17
Hi all,

I've been trying to setup Jaunty on a TC4400. Mostly smooth, but I've got a few problems left.

Things that don't work;
Pointer rotate.
Touchpad buttons.
Weird wireless problems.

Well done getting the tablet to start! Out of the box Jaunty recognised most of the hardware. Pointer movement on the tablet works really well straight off, but I'm unable to rotate the pointer.

When I rotate the screen from System/Preferences/Display/Rotation, the pointer does not rotate with it. This is the showstopper at the moment. I really want to use this platform as a book reader, and I'd like to view it in portrait mode.

Oh yeah - a word about the other troubles....
I haven't a clue how to get the touchpad buttons to work. It'd be cool if they would, one of them is the screen rotate button....
On startup the wireless reckons it's connected to my home network, but has a bogus IP and no comms. Clicking on the wireless icon and selecting the home network from the list fixes it. I'll check this out a bit more before whinging properly tho....

Any help much appreciated!

---

### Post by Favux on 2009-05-17
Hi alawson,

Your first post.  Are you new to linux?

Right now there is a problem with the 10-wacom.fdi file so it isn't parsing the names HAL is returning into linuxwacom names.  We've figured out how to do it with usb wacom tablets and I'm trying to do the same with serial tablets.  You can see the problem by typing in a terminal:
```
xsetwacom list
```
that should return you wacom input devices like stylus and eraser.  It will probably be blank.  This means xsetwacom commands (rotation of stylus etc) and wacomcpl (calibration and configuration gui) don't work.  To see the names HAL/D-BUS is seeing type:
```
xinput --list
```

I hope this was helpful.

---

### Post by alawson on 2009-05-17
Hi Favux,

That was mostly my first post 'cos my other issues had already been fixed & documented :)

I'm newish to Ubuntu. I've worked with multiple unices over the years, but wouldn't call myself an expert on any of 'em. I've been using Ubuntu seriously since 8.04. I read several of your posts on the TC1100s whilst researching this - thanks for that!

I typed the commands you suggested. The wacom commands don't reference the tablet at all, but the xinput one certainly did.

You say you're working on the issue - do you have an ETA on the a resolution?

Thanks for your help!

---

### Post by Favux on 2009-05-17
Hi alawson,

Well right now there are several options.  You could use 2 or 3 in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Probably 3a would be the simplest.

Or you could try the .fdi.  The current 10-wacom.fdi is at "/usr/share/hal/fdi/policy/20thirdparty/".  Copy or move it someplace safe.  And then rename it, say .fdi to .bak.  Then replace it in "/usr/share/hal/fdi/policy/20thirdparty/" with the attached .fdi.  After first renaming 10-wacom.fdi, of course.  If after you reboot:
```
xsetwacom list
```
now returns linuxwacom names like stylus and eraser you'll know it worked.

You might want to do:
```
lshal>before_lshal.txt
```
before installing the new .fdi and:
```
lshal>after_lshal.txt
```
after installing it.  That would give us something to compare.

In terms of your bezel buttons try "xev".  Type it in a terminal and and a gui will pop up.  Press the buttons.  You are looking for a keycode.  For example "keycode=176" buried in the output.  You might only want to press one button with each instance of xev so you don't get lost in too much output.

---

### Post by alawson on 2009-05-24
Thanks Favux!

I haven't had  a chance to play with this yet... Hopefully I'll get some time over the coming weeks....

---

