---
title: "Gateway NV57H backlight brightness won't change"
date: 2011-07-23
forum: Hardware
---

### Post by isaacdl on 2011-07-23
I just got a Gateway NV57H laptop. I installed Natty on it, and everything seems to work except changing the backlight brightness. It's currently set to full brightness. When I use the keys to change it (f11 & f12), the applet shows a change, but the backlight doesn't dim.

I've done a fair bit of Google research, but I can't find anything. How do I go about fixing this?

isaac

---

### Post by isaacdl on 2011-07-23
Anyone?

---

### Post by isaacdl on 2011-07-24
Got it!

The patched kernel and power manager at [COLOR="Blue"][https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight)[/COLOR] worked great.

---

### Post by Jamesi on 2011-07-24
On my acer laptop the Brightness is set at max. and i cant change it. i know how to change it but the brightness stays the same. ;/ i think its a bug. :/even when its on battery mode. when the settings say it goes down to the min setting of brightness. it still set at max. good job i have a good battery which still lasts 2 hours :P

---

### Post by isaacdl on 2011-07-24
> **Jamesi said:**
> On my acer laptop the Brightness is set at max. and i cant change it. i know how to change it but the brightness stays the same. ;/ i think its a bug. :/even when its on battery mode. when the settings say it goes down to the min setting of brightness. it still set at max. good job i have a good battery which still lasts 2 hours :P

Try the link I just posted. It worked great for me. Let me know if you need help installing the patched kernel and power manager. It's not terribly difficult!

isaac

---

