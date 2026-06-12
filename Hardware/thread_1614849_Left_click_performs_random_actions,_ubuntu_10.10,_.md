---
title: "Left click performs random actions, ubuntu 10.10, hp pavillion tx1000 tablet"
date: 2010-11-06
forum: Hardware
---

### Post by bee.carlo on 2010-11-06
Hi there,

I've installed Ubuntu 10.10 Maverick from a few weeks (upgrading from the great Lucid) and a strange thing happened:

When I tap the touchpad, or when I click with the touchpad left-click, the OS replies doing 70% of the times the right action (clicking) and the other times it performs actions like: "open in a new tab" or "close this tab" or "close window" or "copy" or "paste" or other astonishing things... :confused:

If I try to use an usb external mouse it works fine, so I thing the problem is only concerned with the touchpad...

I tried to deselect system>preferences>mouse>touchpad>"Enable mouse clicks with touchpad" but anything changed...

I hope there is someone who knows something about it
Thanks in advance :guitar:
Carlo

---

### Post by samcompton on 2010-11-09
I am experiencing the same issue with a fresh install of 10.10 on my HP Pavilion dv6000 laptop.  I have been searching all over for someone with the same problem who has solved it.  The closest thing I have found is a bug report that has not been solved.  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/636720](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/636720)

Maybe someone out there knows how to fix this.

---

### Post by _aar0n_ on 2010-11-14
I have the same problems on my hp pavilion dv6000. maybe it's our laptops that do that

---

### Post by samcompton on 2010-11-17
A user has come up with a fix or workaround that seems to be working fine.  User kruffwuff posted a fix on the bug report site. It worked for me.

[COLOR="Blue"]I had the same problems after fresh Install of 10.10.

I found a solution for the problem in the opensuse forums:
[http://forums.opensuse.org/english/get-help-here/hardware/442426-synaptic-touchpad-11-3-strange-behaviour-dragging-middle-click-2.html](http://forums.opensuse.org/english/get-help-here/hardware/442426-synaptic-touchpad-11-3-strange-behaviour-dragging-middle-click-2.html)

I solved the problem temporarily by typing in terminal:

sudo synclient ClickFinger3=1

and for persistence over reboot added

 Option "ClickFinger3" "1"

to the InputClass in

 /usr/share/X11/xorg.conf.d/50-synaptics.conf[/COLOR]

Thank you kruffwuff.

---

### Post by squizzi on 2010-11-18
Just wanted to add something, after dealing with this problem for over a couple weeks and going absolutely nuts (good thing I only use my laptop when on campus), I've replicated the issue.  

It seems to occur when the left mouse button is pressed and held, except it's incredibly touchy.  Sometimes it takes 1 second of holding sometimes less.  

To replicate I went into chrome, long clicked on links which opened tabs, closed tabs by long clicking etc.  Glad someone figured out a fix for it, I was honestly thinking about moving distros if it was a bug that wasn't resolved, it was driving me that crazy!

Edit: I'm running an hp dv2000 laptop.

---

### Post by bushpilot on 2010-11-19
> **samcompton said:**
> [COLOR=Blue]
I solved the problem temporarily by typing in terminal:
   sudo synclient ClickFinger3=1

and for persistence over reboot added
   Option "ClickFinger3" "1"

to the InputClass in
/usr/share/X11/xorg.conf.d/50-synaptics.conf[/COLOR]


This worked like a charm for me, solving a problem that was driving me a little around the bend.  Thanks!

---

### Post by bee.carlo on 2010-11-21
it worked fine for me....
Thanks kruffwuff

I will put [Solved] to this issue

;)

---

### Post by valmorel on 2011-04-28
> **samcompton said:**
> A user has come up with a fix or workaround that seems to be working fine.  User kruffwuff posted a fix on the bug report site. It worked for me.

[COLOR="Blue"]I had the same problems after fresh Install of 10.10.

I found a solution for the problem in the opensuse forums:
[http://forums.opensuse.org/english/get-help-here/hardware/442426-synaptic-touchpad-11-3-strange-behaviour-dragging-middle-click-2.html](http://forums.opensuse.org/english/get-help-here/hardware/442426-synaptic-touchpad-11-3-strange-behaviour-dragging-middle-click-2.html)

I solved the problem temporarily by typing in terminal:

sudo synclient ClickFinger3=1

and for persistence over reboot added

 Option "ClickFinger3" "1"

to the InputClass in

 /usr/share/X11/xorg.conf.d/50-synaptics.conf[/COLOR]

Thank you kruffwuff.

Worked for me too, saved me buying a new laptop :). Actually, I had solved this problem before with Puppy Linux, so knew it was the clickfinger3 option that was required, I just did not know where to insert it. A google search for clickfinger3 led me here. thanks a million.

---

