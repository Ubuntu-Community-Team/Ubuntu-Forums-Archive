---
title: "How do I listen directly to a USB bus?"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by RichardBronosky on 2007-03-16
I have a keyboard that does not seem to deliver Ctrl+Alt+RightArrow.  It does deliver Ctrl+Alt+LeftArrow.  I have inspected with "xev" and found that each of the key up and key downs are detected for the first key combination, but the RightArrow up and down actions show no event when both the Ctrl and Alt keys are down.  (events are shown when only one of the modifier keys are used.)

I need to start with the lowest level of trouble shooting.   I don't care about pretty scan codes.  I want to see nasty binary gook come off the bus for every key I press.  This way I can see if the keyboard is the problem.

Is there a way that I can get a stream of the data on which the driver is making its decisions?  I have to rule out the driver as an point of failure.

Please advise.

---

