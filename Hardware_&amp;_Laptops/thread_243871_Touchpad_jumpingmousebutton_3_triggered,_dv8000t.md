---
title: "Touchpad jumping/mousebutton 3 triggered, dv8000t"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by KrakensDen on 2006-08-25
I have an hp dv8000t laptop, and every once-in-a-while, the cursor jumps, and mousebutton 3 gets triggered. I can't reliably reproduce this behavior, but it happens often enough that if I just use the laptop for 45 minutes it will happen a few times.

It [seems to] produce the following output in /var/log/messages:
> 
Aug 25 13:17:05 localhost kernel: [17180830.564000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Aug 25 13:17:05 localhost kernel: [17180830.568000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug 25 13:17:05 localhost kernel: [17180830].576000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
Aug 25 13:43:02 localhost -- MARK --


While not exactly a showstopper, it's incredibly annoying to get things randomly pasted into things you are writing, especially if the selection was rather long. In fact, it happened while I was writing this post. Here are the new lines:
> 
Aug 25 13:47:52 localhost kernel: [17182677.780000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug 25 13:47:52 localhost kernel: [17182677.780000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug 25 13:47:52 localhost kernel: [17182677.784000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Aug 25 13:47:52 localhost kernel: [17182677.796000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.


ideas?

---

### Post by christhemonkey on 2006-08-25
My brothers laptop does this as well,

although it also exhibited this behaviour back when he had *shudder* windows on it.

We assumed it was just his touchpad going.

If anyone knows any different let us know!

---

### Post by KrakensDen on 2006-08-25
What kind of laptop was it? If I can send the thing back to HP, I'd like to know. I've never had Windows on mine, so I have no idea if it works there or not.

---

### Post by christhemonkey on 2006-08-26
He has about a 4 year old Compaq Armada.

I'd email/call them about it and see what they say.

---

### Post by zzanzare on 2007-12-11
Hi, I had the same problem on my Acer Aspire 5710 with ALPS Glide point

the touchpad was loosing sync and randomly jumping and clicking. sometimes when i started my system, it was jumping, sometimes not. but when it was the "bad start" it made a jump about every 3 seconds.

i finally found something that worked for me in another thread (i may find the exact link later).

after adding 
```
i8042.reset i8042.nomux
```
to my kernel options in /boot/grub/menu.lst i had NO JUMP what so ever, and it's been 4 days already..

hope it helps for you, i know how annoying this can get

[edit:] i have found this solution here: [http://www.ubuntu-forum.net/showthread.php?t=571498](http://www.ubuntu-forum.net/showthread.php?t=571498) but maybe this thread: [http://ubuntuforums.org/showthread.php?t=417492&page=5](http://ubuntuforums.org/showthread.php?t=417492&page=5) can help you better, as it has more information about this problem

---

