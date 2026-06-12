---
title: "Apple, Inc. Optical USB Mouse [Mitsumi]"
date: 2013-06-01
forum: Hardware
---

### Post by kronus980 on 2013-06-01
I cannot tell if it is a hardware defect or a software issue. The mouse's right click registers as a left click at times using 'xev', and I have to keep left clicking before my right click works. Any way I can pinpoint the problem?

---

### Post by tgalati4 on 2013-06-01
Take the mouse apart and clean it.  Many times, the thin cable used in apple mice and power supplies wears out and causes electrical shorts.  Try wiggling the cable near the rubber grommet coming out of the mouse and see if you get any *xev* events.  If so, then you have a hardware problem.  You can sometimes clip the cable and resolder it--making it slightly shorter, but without the wear spot.  

Try using the mouse in another computer.  If it acts strange, then you probably have a hardware problem.

---

