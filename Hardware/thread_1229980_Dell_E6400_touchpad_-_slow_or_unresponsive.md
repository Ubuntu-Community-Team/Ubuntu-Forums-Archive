---
title: "Dell E6400 touchpad - slow or unresponsive"
date: 2009-08-02
forum: Hardware
---

### Post by washirv on 2009-08-02
There are a ton of posted issues re: Dell's Alps touchpads, but most seem to center around features like scrolling or tapping.  Mine fails completely on a regular basis.

I've tried Ubuntu, Arch, and Redhat, all with same result.  (Windows is generally fine, except for the odd period of several seconds where the touchpad doesn't respond.)  Each time I boot, the touchpad exhibits one of the following behaviors:
- Perfectly fine
- Very slow, about 1/4-1/3 speed
- Completely unresponsive

Sometimes the trackpoint behaves the same way, sometimes it is fine, sometimes it's also dead.  USB mouse always works.

I'm about to send it back and hope this is the typical case where a bad component slips through QC.  Kind of overkill, but I would hate to get stuck with a piece of hardware which doesn't work under Linux.

Have tried configuring xorg.conf specifically, using hal with default settings, and using hal with overrides to treat this Alps touchpad as Synaptics.  No improvement.

Anyone have an answer for this?  You may save UPS and Dell some trouble!

---

### Post by yotam on 2009-10-17
You may consider trying my Alps driver in
   [http://www.medini.org/software/alps/alps.html]("www.medini.org/software/alps/alps.html")
-- yotam

---

