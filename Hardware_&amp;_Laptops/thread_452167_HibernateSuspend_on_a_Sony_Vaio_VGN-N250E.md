---
title: "Hibernate/Suspend on a Sony Vaio VGN-N250E"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by electrifice on 2007-05-23
I've just installed Ubuntu 7.04 Feisty Fawn, and my only complaint is that suspend/hibernate does not work. I really only need one or the other to work (preferably suspend, I think). When I suspend, the machine goes into the desired "comma" but I can't bring it out of it. My only choice is to turn the laptop off and then start over. I would be glad to supply any information needed...
Also, it seems that suspend/hibernate in general aren't very stable yet, so what are some other ways of prolonging battery life, or saving battery while going from one point to another (as with suspend/hibernate)?
--Ubuntu Newb

---

### Post by lord bacon on 2007-05-23
Do you know if it has a dedciated graphics card, if yes do you know what it is,\.

if you cant find out then try the following

type the following into console

sudo gedit  /etc/default/acpi-support

then change the following line

POST_VIDEO=false (should be true at the moment)

save the file then restart and see if that works...

---

### Post by electrifice on 2007-05-23
Here are the specs for my laptop:
[http://www.dealtime.com/xPF-Sony-Sony-VAIO-VGN-N250E-B-15-4-Widescreen-Notebook-PC](http://www.dealtime.com/xPF-Sony-Sony-VAIO-VGN-N250E-B-15-4-Widescreen-Notebook-PC)

It doesn't have a graphic card at all apparently (Intel GMA 900 Graphics Subsystem), but I did try your suggestion and that didn't work. Basically, the laptop falls asleep and only the green power light remains on. Moving the mouse or striking the keyboard has no effect, but pressing the power button lights up the orange battery light until I let go... nothing else happens. I can't hear anything turn on, so I don't think its just a graphic/back light problem.

---

### Post by electrifice on 2007-05-23
I tried something different and got a better response. I downloaded the swsusp (or something like that) package and ran 's2ram -f -a1' The first time I ran this command the computer fell asleep and unlike before the power light turned orange and started to blink... Upon pressing the power button the laptop turned on and everything seemed to be working at first, but the computer was unable to do anything. There was some kind of input/output error and also some problem in being able to communicate with the disks. I am unsuccessful in duplicating this behavior, however. Now, the computer tries to make an effort to suspend and after a few minutes fails with "Input/output" error... any ideas? I really would like to get the suspend feature working... otherwise, the laptop would be rather impractical.

---

