---
title: "Jumpy mouse - low speed USB device"
date: 2011-08-27
forum: Hardware
---

### Post by sleepingdragon on 2011-08-27
I recently purchased a Cerulion blue-dot mouse. Sad thing is it seems jumpy. Every now and again the pointer will stick on the screen when I move the mouse, but then the pointer catches up to where it should be.

The only thing I can see is a reference in my logs to the mouse being reset:

> [  622.984025] usb 5-2: reset low speed USB device using uhci_hcd and address 3


I get quite a few of those.  It's as though the mouse is "forgotten" if it's not being used and takes a moment to catch up when it's used again.

Any ideas?

---

### Post by sleepingdragon on 2011-09-18
I think it's solved. Nothing to do with the mouse itself, but rather another bug that's [solved here]("http://ubuntuforums.org/showthread.php?t=1234983"). It was just the sheer number of error messages causing my machine to be jumpy and slow. 

Problem solved!

---

