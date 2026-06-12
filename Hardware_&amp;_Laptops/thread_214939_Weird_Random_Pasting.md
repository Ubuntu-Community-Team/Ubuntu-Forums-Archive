---
title: "Weird Random Pasting"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by tonyr1988 on 2006-07-13
I installed Ubuntu on my girlfriend's hp pavilion ze4900 last night (she loves it!). The only problem (so far): when typing ANYTHING (in gedit, in the Firefox URL bar, *right now*!), it will do two things:

1) randomly "paste" the stuff currently on clipboard (is it called "clipboard like Windows"?), or
2) randomly type stuff, like "d" or move back in the web browser.

This post alone has taken me forever to type (having to constantly hit Backspace and go forward when it navigates me to the previous page). It has caused problems in Terminal.

HELP!

---

### Post by rbalfour on 2006-07-13
do you have an external keyboard? if so, try it with that before you start messing with the xcong.conf

---

### Post by tonyr1988 on 2006-07-13
No, I don't have one. But someone I'll bring one down to try on her laptop. In case it doesn't work, what would I change in xorg.conf?

---

### Post by rbalfour on 2006-07-13
Most HP laptops have hotkeys, you will need to add those keys to the xorg.conf
I am not sure what the scancodes are, but a google search should turn up the correct codes.

---

