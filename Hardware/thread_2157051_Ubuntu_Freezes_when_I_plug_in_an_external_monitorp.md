---
title: "Ubuntu Freezes when I plug in an external monitor/projector"
date: 2013-06-24
forum: Hardware
---

### Post by alberto666 on 2013-06-24
Everytime I connect an external display Ubuntu just hangs. Everything stops working.

It takes half-a-second or so after I plug the connect. No matter what.
Even if the connector has nothing in the other end.

I am working with Ubuntu 13.04. It started working. But..., after I connected two different external devices, it just stopped working. I had different configurations for them, one of them placed on the left, the other on the right. One of the with mirroring the other just working on the external monitor. 

And now, the only way to make them work is booting with the external monitor plugged, otherwise it just freezes everything.
And by everything I mean everything. 

I tried this solution: [http://blog.shevin.info/2012/05/how-to-fix-dual-monitor-freeze-in.html](http://blog.shevin.info/2012/05/how-to-fix-dual-monitor-freeze-in.html)
But no luck.
ALT+PRINTSCREEN+K not working.
Alt + Ctrl + Supr not working either.

Even Caps. Lock not working (keyboard does not change the indicator left). Everything dead.
Except for one thing. If I un-plug the monitor and plug it again, the same frozen image still appear.

Any clue?
I have seen quite a lot of people have this problem or similar. But I haven't found any solution yet. The only solution is "reboot".

---

### Post by dino99 on 2013-06-24
your best friends are logs, to find usefull warnings/errors
that said, you might pay attention to that hardware how they are plugged: which chipsets used (hdmi, displayport, ...), are they compatible with the cords used and the graphic card
and the bios settings can be tweaked also.

---

### Post by alberto666 on 2013-06-24
They work (currently and perfectly) in Windows.
They used to work in this very same version of Ubuntu/Linux.

They stopped working at same point as aforementioned.

And everything points to a bug from XOrg/Ubuntu.

Any clue to look for a specific log which may help me?

---

