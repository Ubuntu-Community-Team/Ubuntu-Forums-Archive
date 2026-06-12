---
title: "Frequent Kernel Panics, perhaps the USB Wireless?"
date: 2011-04-30
forum: Hardware
---

### Post by matthewgreyling on 2011-04-30
I am having frequent kernel panics with my system, at least once an hour, usually more often.  Usually it will go to a screen of text with a bunch of info about the panic, which I do not really understand much of, and just freeze there.  Everything just stops, can't use the keyboard, whatever sound was playing repeats the last second or so constantly until I do a hard restart or shutdown.

I also get a few random freezes (which I can't fix without rebooting) without getting a text screen; not sure if it's related.

From the parts I can understand of the text, it looks to me like my USB wireless card might be the culprit, but I don't know how to find out for sure.

Help?

(I'm running a fresh install of 11.04, dual-booting with Windows 7)

---

### Post by matthewgreyling on 2011-05-11
I'm still getting these kernel panics.

My wireless card is working with the r8712 driver, and I am almost always connecting to my phone's internet connection in Ad-Hoc mode.

(It would seem that after doing some research, this thread may have been miscategorised...)

---

### Post by Ernie07 on 2011-08-08
I have had similar experiences with my ASUS P5Q-E based desktop.  Disabling screen saving did not stop the lockups.  the same symptoms still occur, after a fairly recent 11.04 64bit install that also occurred with the 11.04 32bit install with both upgraded to 2.6.38-11 generic.

The last couple of times the lockup occurred, with caps lock and scroll lock lights flashing, I had just moved or clicked the usb mouse.

The attachment will indicate multiple use of irq:18 (SATA and multiple usb).  I will move the usb mouse to a different port and hope for the best.

---

