---
title: "Multimedia Keyboard Volume Knob"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by mpgarate on 2007-05-16
I have the dell multimedia keyboard, brand new, and I easily mapped all of the keys to my liking, except I cant get the volume knob to work. How can I do this?

---

### Post by nosami on 2007-05-19
[this]("http://wiki.ejohansson.se/index.php/Software/knob")  worked for me. It's not very precise though.

---

### Post by vigleik on 2007-05-19
I also have a Dell multimedia keyboard. Which version of Ubuntu are you using? On older versions of Ubuntu, and on other Linuxes, I've used xbindkeys. Here's part of my .xindkeysrc file:

#Volume_up
"aumix -v +2"
    m:0x0 + c:176
    NoSymbol

#Volume_down
"aumix -v -2"
    m:0x0 + c:174
    NoSymbol

On 7.04 I didn't have to do this, as the multimedia keys worked on a fresh install.

---

### Post by mpgarate on 2007-05-19
did the all the keys work, including the volume knob? I dont think mine is working (on a fresh install now)

---

### Post by mpgarate on 2007-05-29
vigleik, you say the volume knob worked on a fresh install? are you sure we have the same keyboard? this is mine: [http://support.dell.com/support/edocs/acc/P76379/sk8135.jpg](http://support.dell.com/support/edocs/acc/P76379/sk8135.jpg)

---

### Post by exalted on 2007-07-11
For those of use who've upgrade to feisty from edgy, anyone know how to get the keyboard working with the least headache? most of the buttons work, just not the knob.

---

### Post by mpgarate on 2007-07-11
I messed around with the knob for awhile, with VERY little success. I settled for setting the back/foreward buttons (meant for the browser I think) on the far left to lower and higher. Its just easier. It would be nice if the button worked though.....

im using feisty (fresh install)

---

### Post by nelq on 2007-11-28
The keyboard doesn't use the volume knob as keys but as a joystick returning HID events.
IMHO:
HACK:
[INDENT]To make it work, we need to grab the HID events from the knob and link them to the default Volume up/down XF86AudioUp/XF86AudioDown.[/INDENT]
Possible correct way?:
[INDENT]create a little deamon that takes the HID events and link them to amixer directly (for alsa).[/INDENT]

---

