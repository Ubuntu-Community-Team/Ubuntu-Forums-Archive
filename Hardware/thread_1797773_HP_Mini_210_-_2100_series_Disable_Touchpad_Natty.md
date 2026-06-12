---
title: "HP Mini 210 - 2100 series Disable Touchpad Natty"
date: 2011-07-05
forum: Hardware
---

### Post by Jack Brown on 2011-07-05
Hi all,

am currently testing Ubuntu 11.04 32 bit on this (thread title) netbook.
with current updates.

still can't figure out how to **disable the touchpad.**

double tapping on the upper right dot (works on windows)  does not work in ubuntu. 

saw another post on the forum from last year, but no solution.

Other touchpad functions workaround that works:

right click - > tap with two fingers
vertical scroll -> right edge finger dragging  (supposed to be 2 finger dragging)


No horizontal scroll, is there?

EDIT: also none of the FN keys are for the touchpd. they each have their own functions drawn on them. tried them one by one, none disabled the touchpad.

good news is all the function keys' work according to what's labelled on them.

thanks lots.


everytime i install an ubuntu there's a funny good feeling.
and we know that things usually get better as time passes.
go developers!

---

### Post by Jack Brown on 2011-07-08
Never mind it's solved.

using the command ```
synclient touchpadoff=1
``` and ```
synclient touchpadoff=0
```, then assigning it to some keyboard shortcuts.

never had a need to go into mouse settings, so pleasantly surprised that MOUSE gui already has other needed feature settings. (like enabling HORIZONTAL scrolling)

Can also install 'Pointing Devices' from repos though found this to be unnecessary.

Now Natty on this is one sleek narwhal. Theres a bit of delay in starting some programs (firefox) as compared to desktop.  But would gladly live with that if it means longer battery life.

Cheers and on to the next problem / need.

---

