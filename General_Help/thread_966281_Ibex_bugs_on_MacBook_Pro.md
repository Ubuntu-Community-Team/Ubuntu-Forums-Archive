---
title: "Ibex bugs on MacBook Pro"
date: 2008-11-01
forum: General Help
---

### Post by Thedjatclubrock on 2008-11-01
Hey everybody.

I am using a MacBook Pro. I believe it is 2G, but I am not sure. It is a 2.4 Core 2 Duo.

I love Ubuntu on the Mac, it enhances it so much.

There are still a few things I couldn't get working, I googled a bit, tried various solutions, but none seem to work.

[LIST=1]
[*]Keyboard backlight doesn't work.
[*]Brightness can not be adjusted manually, but when unplugged it changes.
[*]Two finger scroll. I tried editing xorg, and no result.
[*]Eject key doesn't work.
[*] Wifi Card seems to be much weaker, I do not have the range I did with OS X
[*]Caps-Lock light stays off, when on CAPS.
[/LIST]

If anyone has a solution, I'd be very thankful :)

---

### Post by Thedjatclubrock on 2008-11-01
Bump :D

---

### Post by parkerhiggins on 2008-11-01
I've had some of the same issues.  No two finger scroll, no caps lock light.  xorg.conf looks to be set up prety differently from in Hardy, so I'm having trouble applying any of the old tips.

---

### Post by Thedjatclubrock on 2008-11-01
I now have two finger scrolling, but it isn't perfected yet :/
All the other problems remain.

---

### Post by aztechclan on 2008-11-03
I put the following snippit into /etc/hal/fdi/policy/appletouch.fdi and the touchpad works much better with two finger scroll etc.  Feel free to tweak to your liking, I believe storing the prefs here is the new way to go.

[http://pastebin.com/f78b2558c](http://pastebin.com/f78b2558c)

---

