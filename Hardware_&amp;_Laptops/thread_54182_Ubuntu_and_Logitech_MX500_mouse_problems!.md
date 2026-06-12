---
title: "Ubuntu and Logitech MX500 mouse problems!"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by Paapaa on 2005-08-03
Hi all!

I just installed Ubuntu. Everything is working fine except my mouse: Logitech MX500.

The left, middle, right, back, forward buttons and the wheel DO work flawlessly in Firefox. The problem is the scroll up/scroll down buttons near the scrolling wheel. They produce too many events when lookin at the output of xev command. If I press the up button and release it I get:

ButtonPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 864197, (172,6), root:(961,121),
    state 0x0, button 6, same_screen YES

ButtonPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 864207, (172,6), root:(961,121),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 864207, (172,6), root:(961,121),
    state 0x800, button 4, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x2e00001,
    root 0x40, subw 0x0, time 864322, (172,6), root:(961,121),
    state 0x0, button 6, same_screen YES

It is actually producing events as if I had pressed two different buttons. The same goes with the down button. Other buttons don't show this odd behaviour. Is there anything I can do to fix this?

---

### Post by autocrosser on 2005-08-04
Well-I've checked Logitech's support out--(see a post of mine this week)--They state that as long as you have "three" buttons working in Linux--they have done their job--- :-? 

Don't give up hope--take a look at Xorg 7.0 (Breezy's Xorg)--will allow more that 12 buttons configured---Might be worth waiting for :grin: 

[http://xorg.freedesktop.org/wiki/ChangesSince68](http://xorg.freedesktop.org/wiki/ChangesSince68)

---

