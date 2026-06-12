---
title: "dell inspiron e1705 HELP!"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by ry4n on 2007-08-15
I have a Dell inspiron e1705 (9400) and i can't even get the live cd of Ubuntu to work? what do i do? why is this so?

---

### Post by rickdmer on 2007-08-18
I am a total ubuntu newb (just installed ubuntu on my E1705 with a x1400 a couple weeks ago) but I figured you have the same exact laptop as me, and I would have loved some help installing mine. Here are a few links to installing ubuntu with Beryl and then upgrading to Compiz Fusion (runs great with our setup, by the way).

This link is for the 6400 but has the same hardware as us, even the x1400 video:
[http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913)

At one point in that tutorial it tells you to log in from the command prompt but doesnt tell you how (again, Im a windows guy) so if you just restart your laptop at that point (ctrl, alt, backspace) it will ask you to log in when you start up.

This one will upgrade you to Compiz Fusion if you would like (you would!):
[http://forum.compiz-fusion.org/showthread.php?mode=hybrid&t=3157](http://forum.compiz-fusion.org/showthread.php?mode=hybrid&t=3157)

Hope I was some help! If you have any other questions don't be afraid to ask 
aim: rickdmer

---

### Post by phenest on 2007-08-18
Ok guys, I'll save the day. I have one of those machines and it's only the ATI video card that is the problem. You are obviously face to face with a command prompt. Type:
```
sudo /etc/init.d/gdm stop
sudo apt-get install xorg-driver-fglrx
```
Once it,s installed, press Ctrl-Alt-Backspace and type:
```
sudo /etc/init.d/gdm start
```
If it fails, type it again. After a few seconds you should get a graphical login screen.

When you have installed Ubuntu, you may need to do the above again.

---

### Post by Sorenfrey on 2007-11-23
I used the WUBI installation thing that came on the cd. Also tried to install directly from cd. Ubuntu starts up with a nice splash screen at start of installation. But at some point it is trying something with the graphics and it just flickers weirdly. at the end I can type stuff, but typing that sudo whatnot doesn't seem to do anything
matter of fact, nothing I type does anything except for ctrl-alt-del (not ctrl-alt-enter, that doesn't do anything either).

---

