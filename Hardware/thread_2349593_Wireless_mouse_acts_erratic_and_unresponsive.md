---
title: "Wireless mouse acts erratic and unresponsive"
date: 2017-01-16
forum: Hardware
---

### Post by cybrsaylr on 2017-01-16
Running Ubuntu 14.04.5 LTS (x86_64; Unity) and using a Logitech M185 wireless mouse. The white cursor arrow starting freezing, stalling  and just not responding and moving around as normal. At times the white cursor arrow  turns into a hand, then goes back to becoming an arrow! Thought it was just this mouse getting old. Got a new wireless Mobile Microsoft 3500 wireless mouse last week. It installs easily and seems to work fine but  now this new mouse is starting to act in the same erratic way as the old Logitech mouse!

Any ideas as to what is causing this?
Battery levels are normal in both mice.

---

### Post by efflandt on 2017-01-16
Is that happening on the desktop or laptop or both? I have never had any Ubuntu related Logitech mouse issue in any Ubuntu version. I have been running 14.04 on an XPS 8100 w/i5 650 3.2 GHz since Jan 2014, earlier with Logitech Anywhere MX mouse that worked great on any surface, but would eat batteries rather quickly gaming. So I used Ni-Mh rechargeable batteries until its M1 button started failing (a mechanical issue fixed with disassembly and spray contact cleaner). But in the meantime I got a Logitech MX Master mouse which has Li-Ion battery rechargeable with USB cable and the repaired Anywhere MX has been put to less stressful laptop duty. I think I have an M185 mouse somewhere, but it is with my 10.1" tablet PC which I cannot locate at the moment (it boots Ubuntu or Lubuntu from SD card with common /home).

There is a package you can install called **solaar** that can associate Logitech keyboards and mice with a Unifying receiver and in some cases tell battery status, but I don't know if that would help troubleshooting your issue. Do you have any other Unifying receiver or have you tried it in different USB port?

I did have an issue at one point where (wired) keyboard and wireless mouse buttons would stop responding (in 12.04), but strangely the mouse cursor would usually still move. That was apparently the result of a failing video card that also stopped responding at times in the rare times I booted Win7, and eventually resulted in scrambled graphics and boot errors from the Linux driver that the graphics card was not responding. Haven't had that problem since replacing that graphics card.

---

### Post by cybrsaylr on 2017-01-16
This is happening with the i7 Dell desktop in my signature line with both Logitech and Microsoft wireless mice. Just switched the wireless receiver to another USB port to see if that helps any.

---

### Post by cybrsaylr on 2017-01-18
Well so far after using another USB port, mouse is acting normal.
Hope that was the problem but will keep monitoring it.

---

### Post by cybrsaylr on 2017-01-20
Well it has been a couple more days and mouse is still performing normally so will assume the USB port was the cause and mark this as 'solved'.

---

