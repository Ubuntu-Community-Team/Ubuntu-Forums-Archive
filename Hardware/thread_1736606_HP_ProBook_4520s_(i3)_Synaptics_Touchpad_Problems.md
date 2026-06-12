---
title: "HP ProBook 4520s (i3) Synaptics Touchpad Problems"
date: 2011-04-22
forum: Hardware
---

### Post by joel.markshalayenka on 2011-04-22
Hi Everyone,

Got a lovely new laptop, following my long term plan to migrate to linux. Of course there are hiccups, but this one is a little difficult to live with:

HP ProBook 4520s

Touchpad by Synaptics

Ubuntu 10.10 64bit

[B]Problem1: RIGHT CLICK not registering.
Problem2: Cannot turn off touchpad using top left double click. (There is an associated 'off lamp' in that location to indicate off state).
[/B]
These are both important issues for me, first because the right click is bound to GUI context menus and secondly because I like to have manual control over turning off the touchpad rather than automatic palm detection.

Please, does anyone have any ideas? I installed GSYNAPTIC but its configuration options do not seem to include anything useful to this problem.
The double click top left corner has been around on HP laptops for a while - the entire G62 range uses it too.

Here is a picture I ripped of the net of the offending touchpad. Note the spot in the top left is also an LED.
[http://www.marks-goloenko.com/ebay/5420s_touchpad.jpg](http://www.marks-goloenko.com/ebay/5420s_touchpad.jpg)

thanks in advance

---

### Post by NBFruit on 2011-05-07
> **joel.markshalayenka said:**
> Hi Everyone,

Got a lovely new laptop, following my long term plan to migrate to linux. Of course there are hiccups, but this one is a little difficult to live with:

HP ProBook 4520s

Touchpad by Synaptics

Ubuntu 10.10 64bit

[B]Problem1: RIGHT CLICK not registering.
Problem2: Cannot turn off touchpad using top left double click. (There is an associated 'off lamp' in that location to indicate off state).
[/B]
These are both important issues for me, first because the right click is bound to GUI context menus and secondly because I like to have manual control over turning off the touchpad rather than automatic palm detection.

Please, does anyone have any ideas? I installed GSYNAPTIC but its configuration options do not seem to include anything useful to this problem.
The double click top left corner has been around on HP laptops for a while - the entire G62 range uses it too.

Here is a picture I ripped of the net of the offending touchpad. Note the spot in the top left is also an LED.
[http://www.marks-goloenko.com/ebay/5420s_touchpad.jpg](http://www.marks-goloenko.com/ebay/5420s_touchpad.jpg)

thanks in advance

I've been trying to get the Synaptics Touchpad on my 4520s to work correctly for nearly a year. I ended up using a usb mouse most of the time.

I can get right-click to work by editing /usr/share/X11/xorg.conf.d/50-synaptics.conf, but the main problem is that the Touchpad interferes with my keyboard, which cause all sorts of erratic cursor movements when typing.

This will help you get right-click working

[http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/](http://bigbrovar.aoizora.org/index.php/2011/01/12/enable-multitouch-support-for-clickpad-on-ubuntu-10-10/)

Basically, you right click by tapping with 2 fingers.

Will be very reluctant to buy HP again after this.

---

### Post by NBFruit on 2011-05-24
> **joel.markshalayenka said:**
> Hi Everyone,

Got a lovely new laptop, following my long term plan to migrate to linux. Of course there are hiccups, but this one is a little difficult to live with:

HP ProBook 4520s

Touchpad by Synaptics

Ubuntu 10.10 64bit

[B]Problem1: RIGHT CLICK not registering.
Problem2: Cannot turn off touchpad using top left double click. (There is an associated 'off lamp' in that location to indicate off state).
[/B]
These are both important issues for me, first because the right click is bound to GUI context menus and secondly because I like to have manual control over turning off the touchpad rather than automatic palm detection.

Please, does anyone have any ideas? I installed GSYNAPTIC but its configuration options do not seem to include anything useful to this problem.
The double click top left corner has been around on HP laptops for a while - the entire G62 range uses it too.

Here is a picture I ripped of the net of the offending touchpad. Note the spot in the top left is also an LED.
[http://www.marks-goloenko.com/ebay/5420s_touchpad.jpg](http://www.marks-goloenko.com/ebay/5420s_touchpad.jpg)

thanks in advance

This is a related thread, and has a couple of solutions.

[http://ubuntuforums.org/showthread.php?t=1739152](http://ubuntuforums.org/showthread.php?t=1739152)

I'm testing the syndaemon solution at the moment, and the hardware store one...

---

### Post by dougk7 on 2011-11-03
I started having this problem after upgrading to Kernel 2.6.32-34 but when I revert back to 2.6.32-30 the Touchpad works perfectly.

---

