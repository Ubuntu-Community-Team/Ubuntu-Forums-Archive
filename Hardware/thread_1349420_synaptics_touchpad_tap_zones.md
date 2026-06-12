---
title: "synaptics touchpad tap zones"
date: 2009-12-08
forum: Hardware
---

### Post by cjnrac on 2009-12-08
hello,

After much research, I've finally edited my /etc/hal/fdi/policy/11-x11-synaptics.fdi file and have gotten my touchpad to work like it used to in windows. Specifically getting the lower left corner of the touch pad to browse back one webpage by setting input.x11_options.LBCornerButton to 8.

Everything that I've read shows button events 4 and 5 used for vertical scrolling, events 6 and 7 for horizontal scrolling, and 8 for browse back one web page and 9 for browse forward one web page.  My question is how would I map the right corner tap zone to send keystrokes such as ctl+w or ctl+home? Are there numbers that are related to keystroke combinations, and if there are how would I find them.

I have an Acer travelmate 4010 and am using Ubuntu 9.04.

Thank you,

cjnrac

---

