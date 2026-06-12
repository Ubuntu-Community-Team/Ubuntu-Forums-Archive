---
title: "Sony S4XP touchpad sensitivity in Feisty - bug?"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by bbbscarter on 2007-03-19
Hullo!

I'm running Feisty, but I'm pretty sure this has been happening in Dapper and Edgy too.

Basically, my touchpad is far too sensitive to taps, turning the slightest nudge into a 'click'. I've read around, and fiddled endlessly with FingerLow and FingerHigh in my xorg.conf, to no avail. Indeed, anything above '40' in those parameters seems to go out of bounds.

Finally, I discovered synclient and started fiddling around there directly. Using the -m option to monitor my input events, I discovered something odd. If I move my finger around the pad, I get pressure readings going from near zero to 90, moving smoothly up and down according to the pressure I exert. However, if I do a tapping motion, all I get is a pressure of 40 being registered, no matter how hard or softly I tap. This obviously makes it rather hard to configure FingerLow and FingerHigh correctly. :) 

I've made sure my xorg.conf device settings are pointing at the correct device (in my case, event3 rather than the default of psaux), and apart from this problem, it's working fine. I know I can turn off the 'tap' behaviour, but I've become rather attached to it in my other OS...

My machine is a Sony S4XP with an Alps Glidepoint touchpad.

Any help is much appreciated!

Simon.

---

