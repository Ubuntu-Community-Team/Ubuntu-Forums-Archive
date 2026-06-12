---
title: "Getting buttons to work with Ubuntu"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by holdie on 2007-02-06
So i'm running Edgy on a Dell Inspiron 6000 (it's been working fine so far) and I was wondering if there was a way I could bind those keys on the outside of the laptop (play, stop, next track, mute, volume, etc) to perform various functions in Amarok or some of the other media players

any ideas?

---

### Post by kidders on 2007-02-06
Hi there,

I haven't done this on Ubuntu before (so there might be a smarter way), but my first step would be to open a little gizmo called "xev". It reports details of various events (including keypresses) as they happen. You could also use it to find ways of making use of extra buttons on a mouse. What you're after is some indication that, when you press "Mute", for instance, that X sees you do it ... preferably a keycode.

Assuming you hit the jackpot, and all the special function keys you want to map have corresponding keycodes, you can use them to create a file called .Xmodmap (in your home directory). It might look something like this...

```
keycode 176 = XF86AudioRaiseVolume
keycode 174 = XF86AudioLowerVolume
keycode 160 = XF86AudioMute
```

Then, restart your X, and see what happens.

**Edit:** Whoops sorry... I forgot the most important step ... you have to run the xmodmap application itself! There are various ways of doing this (GDM, for instance, has its own, if you're using that), but this should work:

Add the line **/usr/bin/xmodmap $HOME/.Xmodmap** to your .xsession script.

---

### Post by eaglesfan17 on 2007-02-09
I'm having the same problem on a Compaq Presario 700 series laptop. I've tried xev and it only detects the volume up/down buttons but not the other ones. What do you do if xev does not detect an action?

---

### Post by kidders on 2007-02-09
Hi there,

Sometimes, changing the keyboard model makes a difference. I've seen suggestions that changing XkbModel to "microsoftpro" in your xorg.conf works nicely on some Compaqs.

---

### Post by Chamith on 2007-02-18
Hey

I've managed to find the keycode from 'xev' - they are the same as your example.  But I'm not sure how to edit / add the line to .xsession - could you expand on how I can edit this file?  I'm using Kubuntu 6.06

thanks

---

### Post by oolunchbox on 2007-02-18
I dont want to jack the thread but my girlfriend has a microsoft keyboard with a calculator buttoin she would like to use, is there a way to use xmodmap to map the key to launch speedcrunch when she pushes it? I know the keycode and Ive tried xbindkeys but it doesnt seem to want to work.

---

### Post by Chamith on 2007-02-19
hey

this post worked for me

[http://www.ubuntuforums.org/showthread.php?t=364006](http://www.ubuntuforums.org/showthread.php?t=364006)

---

