---
title: "Low resolution"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by shang1 on 2009-01-21
I have recently installed ubuntu and I am keen to become a convert. However, when I start the computer I get, "Low screen resolution", when I try to reconfigure or just to run in low screen resolution for this session it will not go any further, it justs loops on this screen.
The graphics card is a gigabyte GV-NX53128D. Am I missing drivers? Whats going on?
Help please :D

---

### Post by Shazaam on 2009-01-21
Go to System>Administration>Hardware Drivers. See if you can enable drivers for the video card there.

---

### Post by shang1 on 2009-01-21
I cant get to the desktop, I only get the low resolution error and can't get past it.

---

### Post by Shazaam on 2009-01-21
Try this...
When the pc boots you will see the "hit your ESC key" prompt, go ahead and do that. You should then see a grub boot screen with the kernel choices. Highlight "Recovery mode" and hit enter. It will then boot to a choice of options, choose "xfix". See if that helps.

---

### Post by sidefx2 on 2009-02-04
> **Shazaam said:**
> Try this...
When the pc boots you will see the "hit your ESC key" prompt, go ahead and do that. You should then see a grub boot screen with the kernel choices. Highlight "Recovery mode" and hit enter. It will then boot to a choice of options, choose "xfix". See if that helps.

I just wanted to let you know this worked for me, thanks a lot it was a huge pain being in 800x600.

---

