---
title: "My mouse does not work/not recognized"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by dlaneir_loire on 2005-09-13
--------------------------------------------------------------------------------

I've installed Ubuntu in my laptop. Yes, I've installed and the interface is nice.

But WHEN I MOVED MY MOUSE POINTER (the mouse, which is built-in in my laptop of course), NOTHING HAPPENS. It does not move and it remains in its place, the center of the screen. It does not work as hard as I could and all that I can do is to use the keyboard.

Why such happens? PLEASE HELP ME. I need to move it. Thank you....

---

### Post by P_Squiddy on 2005-09-26
I have this same problem with my Toshiba A40 Satellite. Not sure the actual cause, but the fix I use is to remove the psmouse and mousedev modules, then install tsdev and psmouse again. This "toggles" something that makes the mouse work. I've got a script that seems to do the trick adequately. I put it in my system /etc/init.d/fixmouse, and linked it in /etc/rc2.d/S15fixmouse to make it do it's thing automagically at boot.

[FONT=Courier New]#! /bin/sh
#
# fixmouse    executed by init upon initializing X.
#

PATH="/sbin:/bin:/usr/sbin:/usr/bin"
rmmod psmouse
rmmod mousedev
sleep 2
modprobe tsdev
modprobe psmouse
[/FONT]

---

