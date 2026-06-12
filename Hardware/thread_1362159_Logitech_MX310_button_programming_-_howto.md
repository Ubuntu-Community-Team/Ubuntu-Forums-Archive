---
title: "Logitech MX310 button programming - howto?"
date: 2009-12-22
forum: Hardware
---

### Post by Objekt on 2009-12-22
Is there some way I can program the buttons on my Logitech MX310 mouse to do various keystrokes in all apps?  The side buttons work as "forward" and "back" in Firefox, but that's not terribly useful, and I haven't found any way to make them do more useful things (e.g. generate an Esc keypress).  In Windows, the Logitech Mouseware software allows one to program arbitrary keystrokes to any of the buttons, and I'd like to do the same thing in Kubuntu 9.10.

I installed an app called "btnx" that claims to allow programming one's mouse buttons to perform desired keystrokes, but in fact it does nothing.  It detects all the buttons, and says it is assigning keystrokes to the buttons, but they don't do anything in applications, such as Urban Terror 4.1.  The side buttons just do "back" and "forward" in Firefox, as before. 

There has got to be some way to assign keystrokes to mouse buttons, hasn't there?

---

### Post by PostWax on 2009-12-28
Same problem here only different mouse.  Sorry I can not help you.

---

### Post by wycito on 2009-12-29
you have to install an app called imwheel which allows you to map the mouse button to any application
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)
Hope it helps

---

### Post by Objekt on 2009-12-29
IMwheel ...umm, I want to program more than just the scroll wheel.  Thanks anyway.

---

### Post by Objekt on 2010-02-01
FWIW, the application "btnx" (available through the Ubuntu Software menu) has solved this issue for me.  I'm not sure why it didn't work the first time; maybe you have to run it as sudo.  I can't remember what I did to make it work.  But it does work now.  Whenever I press the right side button, I get a letter "z" keypress, and the left side button generates "Esc."  That is exactly how I had my MX310 set up in Windows XP.

I am very happy to see I can do button programming without Logitech's Mouseware software, which is Windows-only.

It would be great to have a Windows equivalent of btnx.  It is needed in Windows 7/Vista, as many hardware manufacturers aren't bothering to write Windows 7/Vista drivers for anything but their newest products.  Logitech told me, paraphrasing, "tough cookies, you have to throw away your perfectly good MX310 and buy our latest mouse."  I hate forced obsolescence.

---

