---
title: "Trackpad gestures problems"
date: 2014-03-25
forum: Hardware
---

### Post by priestnot on 2014-03-25
I have a Clevo P150SM with a synaptics trackpad and I wish to have multi-touch gestures for expo, scale, show desktop, change view port, etc...

I am using Ubuntu 13.10 with mate as a desktop environment and have synclient.

I searched the web and found touchegg and I installed it from the repos and it did not work, then I tried to install it by the source and it did not work.

Touchegg runs on terminal and displays the information of the gestures but then if I make a gesture it does not do anything.

An example I created a gesture for "all" to make a mouse click (button 1) with 4 fingers I rebooted the PC logged in but it did nothing.

(I have the touchegg in the startup applications).

Does any one has touchegg working in ubuntu 13.10?

---

### Post by wheatley2 on 2014-05-11
I have the same problem as you. I have an ASUS F200CA with a multitouch TouchPad, and I cant use it. Ubuntu provides 2-fingers horizontal and vertical scroll and 3-4 fingers tap gestures, but I want to scale, zoom, etc... I've found this:

[http://http://ubuntuforums.org/showthread.php?t=2160095](http://http://ubuntuforums.org/showthread.php?t=2160095)

But It didnt work for me. I typed "synclient ClickFinger2=0 TapButton2=0 VertTwoFingerScroll=0 HorizTwoFingerScroll=0" and TouchEgg doesnt recognize any gesture...

Please help!!

---

### Post by tar0n on 2014-05-14
I have the same problem with my Vaio Pro 13.
I can set two-finger scrolls and 3-finger-taps in KDE settings, but not more. And I really want to use some 3-finger-drag and 2-finger-pich gestures.

So I tried the KDE "gesture and shortkey settings" (<- don't know if that's the exact name in English), but I was unable to implement any new touchpad gestures. First of all, it seemed to only recognize 1 (!) finger, and second, even those gestures did not work afterwards.

So then I installed touchegg and its GUI. Still, whatever I configure, it doesn't work. THIS IS EVEN TRUE FOR 2-FINGER-GESTURES, given that the 2-finger-scrolls are disabled in KDE in order to not intervene with touchegg. When I start touchegg in the terminal and use gestures on my touchpad, it only shows a reaction for 2 fingers. Still, 3 fingers should work, as I was able to define this as a middle click in KDE, right? I'm really confused.

If no one knows a solution: is there at least a way to set (in KDE) two-finger-drags to left/right as ALT+left/right? I would rather have this than horizontal scrolling.

---

### Post by tar0n on 2014-05-15
Okay, what made it a little better for me:
In Firefox, you can set mousewheel.default.action.override_x = 2. This means scrolling horizontally (done by two fingers, that works out of the box) is interpreted as Back/Forward by Firefox. Of course, it can't be used in Nautilus/Dolphin or other browsers, but still a big step forward :)
I will now set the screen edges for exposé functions or show all desktops, and just use Ctrl + touchpad edge for scrolling (instead of pinching with 2 fingers)

---

