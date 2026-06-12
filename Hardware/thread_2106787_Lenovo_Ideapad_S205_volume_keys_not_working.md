---
title: "Lenovo Ideapad S205 volume keys not working"
date: 2013-01-20
forum: Hardware
---

### Post by d029940 on 2013-01-20
Hello,

I searched and googled a lot, but I did not find anything to my problem.

So, here is my problem:

I installed Xubuntu 32 bit on my Lenovo Ideapad S205. Right from the start almost everything worked.

But now I figured out, when ever I press the function key to control the volume, a pop-up appears at the top right corner of the screen showing me that the volume will change. (I do not know how to refer to this pop-up). So that looks good, but the volume doesn't change. Also the volume indicator of the volume applet in the panel does not change.

(The keys for changing the brightness do work properly).

UPDATE: Just booted with a Linux Mint (Mate) live image. No problem. So, I suppose the problem is related to Xubuntu.  

Any idea?

Thx,
Manfred

By the way, although I am looking at this forum for a long time, this is my first posting. Hope I did not violate any rules. Also, I am guy, sometimes using Windows and sometimes using Linux.

---

### Post by d029940 on 2013-02-02
No one has any idea?

When I run top in a terminal window, I can see that a program "xfce4-notifyd" is called, when ever I press one of the function keys for volume change. So, it seems that xfce4-notifyd cannot "communicate" with the sound applet. Also, I figured out in addition: If I mute/unmute using the sound applet the pop-up (I think it is called indicator) changes the speaker symbol (from mute to unmute and vice versa). But changing the volume bar in the sound applet does not influence the volume bar of the indicator. Changes in the indicator is never reflected in the sound applet.

---

