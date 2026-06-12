---
title: "MX5000 zoom slider, how do I figure out what the &quot;keys&quot; are to set up xbindkeys?"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by Mysticle31 on 2007-12-17
I've been trying to make my zoom slider work to zoom in compiz-fusion.

The interesting thing is that when I run xbindkeys-config and hit "get button" or something of the sort, the slider doesn't generate any results.  

I've tried xev in the terminal and I don't get any results there either.

The volume slider and media buttons (mute, play/pause, stop, back, and forward) all work by default in Ubuntu.  I tied using the volume slider and media buttons in xev, and they don't give any results, but they work.  

The media button (on top) generates results in xev, but doesn't work.  I had planed to use xbindkeys to bind it to my media player.

I tried the function buttons, none of them work or generate results in xev except for e-mail, which generates results in xev, and starts evolution. I never use them anyway, so I don't care.

Soo..

The media button is an exception in that it generates a command in xev, which means it's bindable, but doesn't work by default.

The volume sliders and media buttons (play pause..etc) are an exception in that they do not generate xev events and do work by default. 

The zoom slider is an exception in that it does not generate xev events and does not work by default.

How do I make it generate xev events so I can bind it to zoom in compiz? 


[IMG]http://www.extremeoctech.com/reviews/logitech/mx5000/keyboard2.jpg[/IMG]
I am not from this company, I am not advertising from them.  They had good picture of the sliders.  If this is an issue, I will remove it and replace it with a picture I take promptly.

---

### Post by pingpongboss on 2008-01-05
Hey I'm running into the same question you are! If you managed to fix this or at least gathered a few clues, could you reply back please.

---

### Post by Mysticle31 on 2008-01-05
I have not come up with a good solution as of yet.  

I'm still working on it and other, more pertinent, problems.

I did find this, you may want to give it a shot.  Let me know how it goes.

mx5000-tools

[http://home.gna.org/mx5000tools/](http://home.gna.org/mx5000tools/)

---

### Post by pingpongboss on 2008-01-06
Look interesting, but currently I can't find any uses for it. mx5000d exits with ```
** ERROR **: Can't open input device: No such file or directory (2)
aborting...
Aborted (core dumped)

```
The most i've done with mx5000-tool is draw a horizontal line :mad:

---

### Post by Skerit on 2008-05-12
Ah yes, the mx5000-tools ... Still running in to the same problems:

skerit@KIP-DU-SKER:~$ sudo mx5000d -d /dev/hiddev0
Could not create uinput device: Cannot allocate memory
Could not create uinput device: Cannot allocate memory

** ERROR **: Could not open uinput

aborting...
Afgebroken
skerit@KIP-DU-SKER:~$ mx5000-tool --device /dev/hiddev0 --n dfs
skerit@KIP-DU-SKER:~$ mx5000-tool --device /dev/hiddev0 -b
skerit@KIP-DU-SKER:~$

---

