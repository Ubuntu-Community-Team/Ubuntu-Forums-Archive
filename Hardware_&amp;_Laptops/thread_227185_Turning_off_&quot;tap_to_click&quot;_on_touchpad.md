---
title: "Turning off &quot;tap to click&quot; on touchpad"
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by RussianVodka on 2006-08-01
I've been searching around for a few days, but I can't find any way of switching of the "tap to click" option off the touchpad.

Anyone know how to do that?

---

### Post by bensexson on 2006-08-01
This will depend on your touchpad.  If it is a synaptics this is how I turned off mine.
Add Option		"MaxTapTime"		"0" to Section "InputDevice" for your touchpad.

---

### Post by kirtfitzpatrick on 2006-08-08
I have found that setting MaxTapTime to 0 does not give me the results I need on it's own.  Also setting MaxTapMove to 0 gets me closer.


    Option         "MaxTapTime" "0"
    Option         "MaxTapMove" "0"

But it's still not quite there.  I need to click twice to follow links in Firefox with that setup.  However if I exclude those two options and instead use the following options I disable the touchpad tap and clicks work as expected in Firefox.

    Option         "TapButton1" "0"
    Option         "TapButton2" "0"
    Option         "TapButton3" "0"

If this still doesn't work for you, read the synaptics man page.

---

### Post by A. J. Rimmer on 2006-09-18
Thanks to the above posts, I was able to dig into the touchpad a bit myself.  After reviewing "man synaptics" and "man xorg.conf", I decided to try setting TouchpadOff to the value of 2.

Unfortunately, this also turns off scrolling, but at least I don't have windows popping open and/or closed any more just because I hit the touchpad a bit too hard!

---

### Post by kaffekopp on 2006-09-18
Have you tried using Syndaemon? With it, you can make the tap function disable automatically for a specific amount of time after each keypress on the keyboard. Great for disabling those random clicks while you're typing!

For more info, check my thread on:
[http://www.ubuntuforums.org/showthread.php?t=212668&highlight=touchpad+syndaemon]("http://www.ubuntuforums.org/showthread.php?t=212668&highlight=touchpad+syndaemon")

---

### Post by A. J. Rimmer on 2006-09-19
> **kaffekopp said:**
> Have you tried using Syndaemon? ...
For more info, check my thread on:
[http://www.ubuntuforums.org/showthread.php?t=212668&highlight=touchpad+syndaemon]("http://www.ubuntuforums.org/showthread.php?t=212668&highlight=touchpad+syndaemon")

Thanks very much for the reference.  I think I did see this earlier, but failed to bookmark it, and wasn't able to get back to it.  I will give this a try!

---

