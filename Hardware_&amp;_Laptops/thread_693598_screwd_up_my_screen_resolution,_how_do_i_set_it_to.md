---
title: "screwd up my screen resolution, how do i set it to vesa or so?"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by pedrotuga on 2008-02-11
ok, there´s quita a lot of topics about this. But i didn'd find any with the exact same issue.

My laptop neon tubes broke. The ones that iluminate the LCD. This means I can't see anything as the screen does not irradiate any light. If i lite up the screen with external light i can see a bit but so little that i can't even read a word.

Now... here's the problem:
I connected my laptop to an external LCD, it worked fine but it said something like "cant get screen size.. running on low resolution", so.. i changed the screen settings and basically screw things up.

Now, there is a couple of things i don't understand:
Shouldn't this only affect Xorg? like... when in the login screen I press ctrl+alt+f1 and suposely it should go to text mode but all i can see is a blank screen.

Other thing that is confusing me:
I used booted with a knoppix liveCD i have for emergencies like this one. It booted and KDE works ok execpt for one odd problem: It has a desktop bigger than the screen, like.. I can't see the botom taskbar, but i can click the menus on it if i go with the mouse pointer beyond the visible area. Dunno If i made myself understandable in here.. :s

This looks like something that is not solvable simply by editing xorg.conf as it affected the display settings on a livecd session... dunt know though...

can a nybody give me a few tipos on how to clean up this mess?

thanks

---

### Post by Yellow Pasque on 2008-02-11
Try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This way you can manually select your display type and resolution.

---

### Post by pedrotuga on 2008-02-11
ah.. ok.. sorry.. my fault, i forgot to mention.

How do I get a clear visible text console?

Like... pressing ctrl+alt+f1 when in the login screen results in a blank.

Is there a way to interrupt the boot process and prevent the login screen to show?
In other words.... how do i prevent any graffics to be started?

---

