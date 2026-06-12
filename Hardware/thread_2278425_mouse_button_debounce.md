---
title: "mouse button debounce???"
date: 2015-05-16
forum: Hardware
---

### Post by a-you on 2015-05-16
I'm wondering if anybody has come across any solutions for debouncing mouse buttons. That is, often when I click it registers as a double click or sometimes more even. I see many searches from people having this issue, but seemingly there is no built-in solution in ubuntu as yet. I have read that windoz has debounce though I don't know for sure. It's a drag because if windowz does in fact offer this then some mouse manufacturers might be inclined to skip debouncing the buttons. I have come across some articles about patching evdev but it's a bit beyond my skill level so I thought I'd ask here if anybody knows another way.

[http://lists.x.org/archives/xorg-devel/2012-August/033225.html](http://lists.x.org/archives/xorg-devel/2012-August/033225.html)
[http://blog.guntram.de/?p=16](http://blog.guntram.de/?p=16)

---

### Post by tgalati4 on 2015-05-16
I presume that the "double-click" threshold in Mouse Preferences does not work the way you expect?

Open a terminal and run *xev*.  Put the mouse cursor in the box and click some buttons and keys and look at the behavior.  You should get a press event and a release event for each key.  If only one mouse button is giving double-presses, then perhaps a cleaning or hardware replacement.  If all buttons on the mouse are giving double-presses, then that would be a xinput issue.

---

### Post by a-you on 2015-06-25
Sorry for the long delay. The double-click threshold is for the opposite I would say: to make sure that a double click registers as one. But there's no setting option for filtering out clicks that happen very quickly in a sequence unfortunately. I was wondering if anybody might have come across a solution outside of the regular settings stuff. I guess this is not implemented. It's too bad because there seem to be quite a number of people that have this problem, many of whom have expensive mice that happen to be old where the switches are getting worn out and who'd rather not buy a new mouse. In the end I did just buy a new mouse though because I'd been using a real cheap one (the new one is cheap too, but it doesn't add extra clicks).

Thanks for your comment :-)

---

