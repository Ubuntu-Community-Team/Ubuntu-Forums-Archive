---
title: "ATAPI Microphone under wrong tab in volume control."
date: 2008-12-03
forum: Hardware
---

### Post by PoHandle on 2008-12-03
I am trying to use the ATAPI mic on my HP TX1000 laptop.  (The ones on either side of the built-in webcam)  I know they work, because I unmute the control labeled ATAPI mic in volume control, and hear what I speak being played back through the speakers.  However, I cannot use the mic to record with any apps like audacity because it does not appear under any capture tab, only playback.  Is there anyway that I could make ATAPI Mic appear under a capture tab?

---

### Post by PoHandle on 2008-12-04
Silly me.  The proper recording tab in volume control was disabled because of PulseAudio making my audio system more complicated than it needs to be.  I enabled the proper tab and my ATAPI mic now works with recording programs.

Problem solved.

---

### Post by gobbligook@hotmail.com on 2009-01-26
I had the same problem on the HP tx1420ca and your solution for the microphone was very helpful.  Thanks!

---

### Post by omunozsj on 2010-01-13
On Karmic, you can't access important settings through Volume Control GUI. Instead you need to use alsamixer from a command line terminal:

% alsamixer -V all

Hope it helps...

---

