---
title: "Trackpoint in EnduraPro External USB Keyboard Doesn't Work"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by ajkessel on 2007-04-24
I just got an EnduraPro 104 USB keyboard <http://www.pckeyboard.com/ep104.html>. The keyboard has a built-in trackpoint. I can't for the life of me get it to work properly in Feisty X (or in console, for that matter). I can go down, but not left, right, up, etc..

The website claims no special drivers or configurations are required.

I've tried a variety of drivers, including PS/2, IMPS/2, ExplorerPS/2, Auto, intellimouse, etc.. I've tried accessing the mouse from /dev/psaux and /dev/input/mice.

xev can see all the events of the mouse moving up and down, but xserver only allows the mouse to move down.

An external mouse plugged in separately to another USB port works fine. Adding or removing that mouse makes no difference on the built-in trackpoint.

dmesg sees it is:

[    5.898000] input: Unicomp  Endura Keyboard  as /class/input/input2
[    5.898000] input: USB HID v1.10 Keyboard [Unicomp  Endura Keyboard ] on usb-0000:00:1d.7-1.1

mdetect goes back and forth between thinking it is a 'psaux' mouse and an 'intellimouse'.

Any ideas how to troubleshoot? It's driving me crazy.

---

