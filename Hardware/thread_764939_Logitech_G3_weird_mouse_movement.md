---
title: "Logitech G3 weird mouse movement"
date: 2008-04-24
forum: Hardware
---

### Post by melat0nin on 2008-04-24
Hi all

Just installed Hardy this afternoon, everything seems to be going swimmingly, except my mouse (USB Logitech G3).

When I first booted it didn't work, so I booted into Recovery Mode and ran xfix, which got the mouse working.  There's something weird with the resolution/smoothness of it though.  When moving slowly to do something precise, it would only move in 'stepped' lines, as though following the lines of a grid.  I changed the settings in Mouse Preferences to low Acceleration and high Sensitivity and that helped a bit, but it's still not right - movement isn't smooth and the speed isn't constant (which is the way I like it).

Any thoughts?

---

### Post by bludo on 2008-04-24
I'm having the same problem on with a Logitech MX310.

I've tried switching it from usb to ps2 but it behaves the same.

I've attached a screenshot with a test.

Any help please?

---

### Post by melat0nin on 2008-04-25
> **bludo said:**
> I'm having the same problem on with a Logitech MX310.

I've tried switching it from usb to ps2 but it behaves the same.

I've attached a screenshot with a test.

Any help please?

Very novel way to demonstrate it!

I 'solved' the problem by tweaking the mouse preferences.  I've got Sensitivity at 0% and Acceleration at about 40% and that has calmed my mouse down completely. Something's still not right because other settings bring back that dodgy behaviour, but since I don't every change the settings it doesn't bother me.

HTH

---

### Post by bludo on 2008-04-25
Sadly I still got the problem :( no matter what settings I use. There is no way I could do any graphics with this mouse movement and the overall experience is choppy :( This is the only thing that I couldn't solve in my ubuntu installation, the rest is working great.

---

### Post by ballso on 2008-07-04
Is there a solution for the crappy mouse movement? I also got this problem after upgrading from Feisty to Hardy Heron. I have never ever before experienced this in earlier versions of Ubuntu. 

I have tried solving this with some humble configuration in the xorg.conf and with a "dpkg-reconfigure xserver-xorg", but with no luck. Hardy Heron made my already messed up life even worse. 

Im pretty pissed off right now :)

Mouse in use: Razer Copperhead

---

### Post by ballso on 2008-07-10
Now I have tried with other mice too, and the problem persists. Anyone who is capable of solving this horrible mouse movement problem in Hardy Heron?

---

### Post by melat0nin on 2008-07-10
> **ballso said:**
> Now I have tried with other mice too, and the problem persists. Anyone who is capable of solving this horrible mouse movement problem in Hardy Heron?

Have you experimented with the mouse settings (acceleration and sensitivity)?  I found that after a bit of tweaking I was able to calm the mouse down and get smooth movement.

Not ideal by any means, but once you've done it you can forget about it.

---

### Post by ballso on 2008-07-11
> **melat0nin said:**
> Have you experimented with the mouse settings (acceleration and sensitivity)?  I found that after a bit of tweaking I was able to calm the mouse down and get smooth movement.

Not ideal by any means, but once you've done it you can forget about it.

Yes, I read in the forums that someone (maybe it was you) calmed the mouse by setting the correct values in sensitivity and acceleration. For instance 0 in sensitivity and 40 in acceleration, this doesn't work for me though :(.

If I switch from my lazer mouse to my optical mouse, then I can get a smoother feeling by executing xset m 1 1. Movement is still very crappy and imprecise. This ruins Hardy Heron totally, it feels rotten. Soon I must downgrade to Feisty Fawn.

---

### Post by ykram on 2008-10-01
I've had this SAME EXACT PROBLEM in Heron using a Logitech G5. I play Quake 3 Arena on Dapper (reinstalled Dapper after Heron failed on me completely, mouse movement wise) and its perfect. The only thing keeping me back from using Heron is the way the mouse moves, as somebody else put it, in straight lines, almost as if its on a grid. Just as important, I'd LIKE to keep my mouse movement the exact same way it is in Dapper, that is, no acceleration and the same sensitivity.

PLEASE FIX THIS.

---

