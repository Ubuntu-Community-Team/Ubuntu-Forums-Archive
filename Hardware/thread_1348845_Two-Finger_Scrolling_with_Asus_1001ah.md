---
title: "Two-Finger Scrolling with Asus 1001ah"
date: 2009-12-07
forum: Hardware
---

### Post by milarepa12 on 2009-12-07
Hello,

I've installed Ubuntu Karmic Netbook Remix on an Asus 1001AH. 

I just have one little problem : I cannot two-fingers scroll. Does anybody know if it's possible with this mouse pad and how to set it if it is possible ?

TIA

Norbert

---

### Post by sleepee on 2009-12-11
yeah, i'd also like to know how to do that on my HP DV7...
i know you have to have synaptics to do it, but for some reason, just enabling "2 finger scrolling" in the mouse preferences doesn't do it..

in another thread (marked "solved")  these instructions were recommended

[http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html](http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html)

maybe it'll work for you...  it definitely didn't work for me..  it actually didn't let me use my mouse after a reboot.  but apparently it worked for somebody..

---

### Post by Zorael on 2009-12-12
I'm not sure what kind of pad you have in that machine, but if it's a Synaptics, you should be able to toggle it. I understand GNOME has some graphical tool for it, but I can't comment on it myself.

The terminal way would be something like;
```
$ xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 **[COLOR="Green"]1[/COLOR] [COLOR="RoyalBlue"]0[/COLOR]**
```
I'm not at my netbook currently so I can't be sure if the last two digits are to be '**[COLOR="Green"]1[/COLOR] [COLOR="RoyalBlue"]0[/COLOR]**' or '**[COLOR="RoyalBlue"]0[/COLOR] [COLOR="Green"]1[/COLOR]**'; try both.

One option should enable vertical two-finger scrolling, and the other horizontal. Setting them to '**[COLOR="Green"]1 1[/COLOR]**' should enable both, if for some reason you want that.

---

### Post by milarepa12 on 2010-01-29
Sorry for the long latency, I've been away for more than one month.

I've applied this morning the solution described in [http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html](http://pages.cpsc.ucalgary.ca/~jnjackin/docs/two_finger_scrolling-linux.html) and it has solved my problem. I can now scroll up and down with two fingers on my touchpad.

Thank you a lot for your help.

Norbert

---

### Post by Jeremy Jackins on 2010-02-03
Could you add [SOLVED] to the beginning of the subject?

---

