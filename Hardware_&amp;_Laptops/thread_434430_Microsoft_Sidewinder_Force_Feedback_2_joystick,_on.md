---
title: "Microsoft Sidewinder Force Feedback 2 joystick, ongoing chagrin"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by pifactorial on 2007-05-05
Heh, I was a bit of a Linux guru back in the day, but laziness after my hard drives died drove me back to Windows for the last couple years.  I decided to give Ubuntu a try, and I must say it is absolute <3.

The issue I'm having is with my Microsoft Sidewinder Force Feedback 2 joystick.  With previous versions of Linux I've used, it worked more-or-less fine as a joystick, though no amount of kernel tinkering has ever allowed me to enable force feedback on it.  (Although the kernel has theoretically supported this for some time.)

The joystick did work just fine (sans force feedback) when I installed vanilla Ubuntu.  When I later compiled a custom kernel for myself, I was sure to enable all of the following:
- USD support
- HID support
- Joystick support
- Force Feedback support
- PID device support ("Say Y here if you have a PID-compliant device and wish to enable force feedback for it. Microsoft Sidewinder Force Feedback 2 is one of such devices.")

Anyway, when I booted into my kernel, the joystick still worked mostly normally (still without force feedback, though).  The odd problem is that the tension of the joystick is now dead on the X-axis.  Since the tension is applied by default by the hardware when no force feedback instructions are being sent, I'm guessing that the kernel is trying contact the joystick, but is sending corrupt force feedback information which is causing it to get confused.

Does anybody have experience with this sort of problem?  Is there any output I could post here that would help in debugging this issue?  Any clue what specific kernel option might have triggered this behavior?

Thanks for the help.

---

### Post by madluther on 2007-06-03
I've experienced the same issue. The fix was simple enough. Disable force feedback and PID device support, then recompile. I also had to powercycle the joystick and the PC to clear what ever the PID driver was sending to the joystick that initially caused the problem.

HTH

Mad.

---

