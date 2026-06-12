---
title: "turn off tap to click"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by stevieb on 2006-07-13
hello,

how can i turn off tap to click?  there is no synaptics entry in my xorg.conf file.

-steve

---

### Post by jstroot on 2006-07-14
I'd love to know how to do this as well! The taps are driving me crazy!!!!!

-jstroot

---

### Post by remusus on 2006-07-14
I did it by installing qsynaptics, and then adding 'qsynaptics -r' to the startup thing in Preferences->Sessions.


I think I had to add a couple entries to xorg.conf... let me see:
In Section Modules, I had to add
Load "synaptics"

And in the Section "InputDevice" for the touchpad, I had to add
Option "SHMConfig" "true"

Then install qsynaptics and add it to startup as described above, then you can use qsynaptics to configure tap-to-click and other stuff and have it autoload on logon.

---

