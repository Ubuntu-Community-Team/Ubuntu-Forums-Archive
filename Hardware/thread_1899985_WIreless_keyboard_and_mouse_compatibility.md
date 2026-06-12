---
title: "WIreless keyboard and mouse compatibility"
date: 2011-12-25
forum: Hardware
---

### Post by gnomeshelluser on 2011-12-25
I was recently given a wireless keyboard and mouse from a friend.
I tried using wine to install the drivers, but only get errors.

The mouse and keyboard are Sakar international brand, with the model number M/N:62350N.

I was wondering if there was a generic driver or fix for this. I have looked myself for hours with no avail.

Sorry if this seems like a stupid question. I am new to using ubuntu.

---

### Post by hackb0y294 on 2011-12-25
Hi and welcome to the forums!

First of all, installing the drivers with Wine won't work, as Linux doesn't utilise Windows drivers for the most part, and even if it did, the keyboard/mouse would only work under Wine if you installed them via Wine. Do the keyboard and mouse not work automatically when you plug them in?

---

### Post by bobsageek on 2011-12-25
Are you sure it needs an additional driver, most mice and keyboards 'just work' in Linux, often time specialty function keys do as well. Did you try to run without it or just assumed you needed drivers?

---

### Post by hackb0y294 on 2011-12-25
> **bobsageek said:**
> Are you sure it needs an additional driver, most mice and keyboards 'just work' in Linux...

+1 Linux *is* surprisingly compatible with most input devices.

---

### Post by gnomeshelluser on 2011-12-26
Yes :( unfortunately just plugging them in will not work. Also the drivers that came with them on the disc are for windows.

---

### Post by bobsageek on 2011-12-26
These should show up as at least basic HID devices, can you give us the output from "*dmeg | tail -30*" so we can see what's being detected? Thanks.

---

### Post by bootedguy on 2011-12-26
> **bobsageek said:**
> Are you sure it needs an additional driver, most mice and keyboards 'just work' in Linux, often time specialty function keys do as well. Did you try to run without it or just assumed you needed drivers?
Yes, 'just work' in 10.10, but not in 11.10.  Some say it is a bug in the kernel - but whatever it is, it needs fixing.

---

### Post by bobsageek on 2011-12-26
> **bootedguy said:**
> Yes, 'just work' in 10.10, but not in 11.10.  Some say it is a bug in the kernel - but whatever it is, it needs fixing.

Please refer to an actual bug, I've installed 11.10 across quite a few PCs and HID enumeration has not been an issue yet.

---

