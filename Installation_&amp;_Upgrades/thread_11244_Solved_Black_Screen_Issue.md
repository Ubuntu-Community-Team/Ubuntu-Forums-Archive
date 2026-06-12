---
title: "Solved Black Screen Issue"
date: 2005-01-15
forum: Installation &amp; Upgrades
---

### Post by Andy Owen on 2005-01-15
A couple of months ago, I tried installing ubuntu and when it was finished installing, I was greeted with a black screen instead of a login screen after rebooting. I didn't know what to do, so I tried other distributions and that was all good. The other day, I decided to try again, and I had the same problem, but I fixed it, and I also have a theory (totally unproven) as to why it is:

**My Theory**
My computer is a laptop with a widescreen display (1680x1050 native) and a Geforce4 mobile card in it. I don't think Ubuntu realised that the resolution I wanted was 1680x1050, so it was attempting to go at 1440x1050 or something like that. The drivers which were originally installed didn't like that resolution so they just displayed a black screen.
As I said, this is just a theory and I have nothing to back it up, just my single anecdotal experience.

**The Fix - Short Version**
Install the nvidia drivers. Restart X and all should be fine.

**The Fix - Long Version**
You will need an internet connection.
1) When greeted by the black screen, press Ctrl+Alt+F1, and log in.
2) Type **sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup**
3) Type **sudo nano /etc/apt/sources.list**
4) Look through the file and read what it says, in particular find the 2 lines you need to uncomment (remove the "#" from) to enable the "universe" repository.
5) Remove those two "#" signs
6) Type **sudo apt-get update**
7) Wait a little bit
8 ) Type **sudo apt-get install nvidia-glx**
9) Press Ctrl+Alt+Backspace
10) Press Ctrl+Alt+F7

This is all from my memory, so hopefully I haven't forgotten some of the steps I took. I can imagine that it would be very similar if you have an ati card, if this is you then try the instructions here (point number 2):

[http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713)

Hopefully this will help some people.

Andy

---

### Post by daniels on 2005-01-15
The (nVidia-provided, opaque to all except nVIdia) 'open source' nv driver does not support panels with resolutions like that; nothing we can do.

---

