---
title: "Dead GPU?"
date: 2015-01-17
forum: Hardware
---

### Post by nandodnhd on 2015-01-17
Whatever Distro i use, the pc starts normally and the loading screen looks okay, but after that:

[http://i.imgur.com/DTDI02Mh.jpg](http://i.imgur.com/DTDI02Mh.jpg)
Black and white lines with random colored dots

What could cause this?

---

### Post by Bashing-om on 2015-01-17
nandodnhd; Well ..

What 1st pops to mind is a graphics issue.
Can you boot a liveDVD ?
Have you tried booting with the "nomodeset" boot parameter - IF this is Nvidia/ATI graphics card(s) . Or other means to disable DKMS ?
Speaking of which, is this old hardware or New ? Maybe if newer, hybrid graphics and the system does not know how to cope ?
Maybe we can boot the system to terminal, and have a look-see what the graphics situation is ?

[INDENT][INDENT]look'n to see
[INDENT][INDENT][INDENT][INDENT]what we are going to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nandodnhd on 2015-01-18
It's an intel celeron 3.0ghz (single core) and some old nvidia card. Also, how can i add nomodeset? Using a usb created with UNetBootin

---

### Post by nandodnhd on 2015-01-18
Going to try universal usb installer, to get some other options

---

### Post by nandodnhd on 2015-01-18
nomodeset did the trick, possible to set it as default?

---

### Post by Bashing-om on 2015-01-18
nandodnhd; Well ....

> 
nomodeset did the trick, possible to set it as default?

yeah, it is possible, but NOT the optimum solution. That option disables kernel Mode Setting.
What is the better solution is to load up a graphics driver compatible with your graphics card.

So where are you at presently ... what is your end goal here ? To install ubuntu to the hard drive ? and in what configuration ? Dual booting ?

Depending on your plan to that end-goal is what we do next .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by nandodnhd on 2015-01-18
Just installed it as only operating system, installed the driver and will be disabling the nomodeset with grub editor.

Thank you for the help.

---

### Post by Bashing-om on 2015-01-18
nandodnhd; Great .

> **nandodnhd said:**
> Just installed it as only operating system, installed the driver and will be disabling the nomodeset with grub editor.

Thank you for the help.

Any additional situations OR questions
[INDENT][INDENT][INDENT]help is what we do
[/INDENT][/INDENT][/INDENT]

---

