---
title: "Screen Blanks During Startup"
date: 2008-07-28
forum: Hardware
---

### Post by stephen.ward on 2008-07-28
I’m a complete novice to Linux.

I thought I’d give Ubuntu a try, by installing it on my old Compaq Presario laptop, which previously had Windows XP installed.

I used the alternate Ubuntu 8.04.01 CD to install the system sucessfully. ( The screen blanked when I tried to use the normal CD ).

During startup, the Ubuntu logo appears, followed by the orange ‘loading bar’, which goes to full orange. A blinking cursor then appears for a few seconds, followed by a blank screen!

Any ideas?

(The installation CD Help Menu mentions ‘Special Boot Parameters – Laptops with Screen Display Problems – vga=771.
I tried booting with this parameter, but to no avail.

My laptop has:
1100Mz Intel Celeron Processor
40 Gb Hard Drive
312 Mb RAM
Integrated Trident CyberBlade graphics (8Mb memory allocated to graphics)


Thanks.

---

### Post by SZorg on 2008-07-28
A few things to try off the top of my head:

Hit Ctrl+Alt+Backspace to restart the X server (the GUI backend)

Hit Ctrl+Alt+F2 to change virtual terminals, see if you get to a terminal screen that asks you to login (this will be a black screen with white lettering.)

---

### Post by rahmath on 2008-07-28
Same problem for me... No, Ctrl+Alt+bkspc, etc... Bcoz system is totally freezed.

Any suggestions.....

---

### Post by stephen.ward on 2008-07-30
Thanks for the advice, but nothing seems to work.

I think I'll have to revert back to Bill in Redmond :(

---

### Post by rahmath on 2008-07-31
There is one suggestion for you. I am not sure whether it will work with you(but there is a 90% of chance). You can try the older version of ubuntu, that is Gutsy (7.x). I hope that should work with you fine.

This hardy seems to have so many problems related to display drivers...


Hope this will help you out, eager to know the status...

---

### Post by stephen.ward on 2008-08-01
rahmath

I was just about to ditch Linux for good, but thought I would just check first for any other suggestions before I did so.

Your latest idea worked! Gutsy Gibbon installed and booted perfectly. Thanks for your help.

---

### Post by rahmath on 2008-08-02
Welcome, Always!!!

---

