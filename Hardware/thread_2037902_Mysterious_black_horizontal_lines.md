---
title: "Mysterious black horizontal lines"
date: 2012-08-05
forum: Hardware
---

### Post by Blasphemous on 2012-08-05
I'm having problems with my **Radeon 5550 1GB GDDR5** on Ubuntu **12.04 64 bit**: i'm using **proprietary driver **in their *last version*, which I downloaded from AMD website. No difficulties installing them and it seems that they're working fine

**EXCEPT ONE THING**

I keep seeing *black horizontal stripes* on the screen: they appear and disappear randomly in the blink of an eye while using the computer.

Any idea? :(

---

### Post by trundlenut on 2012-08-05
have you tried plugging a different monitor?

---

### Post by Blasphemous on 2012-08-05
Yep. Invane.

---

### Post by trundlenut on 2012-08-05
Maybe try removing and re-seating the graphics card.

Does this happen if you boot from a live CD?

---

### Post by Blasphemous on 2012-08-05
Ok let's clarify some things:

1) It does not happen with open driver
2) It does not happen in Windows 7 (I'm using dual boot)
3) It did not happen with Ubuntu 10.04

So I guess the problem are the proprietary driver and it is not hardware-related.

:confused:

---

### Post by trundlenut on 2012-08-05
> **Blasphemous said:**
> Ok let's clarify some things:

1) It does not happen with open driver
2) It does not happen in Windows 7 (I'm using dual boot)
3) It did not happen with Ubuntu 10.04

So I guess the problem are the proprietary driver and it is not hardware-related.

:confused:

Does sound like it is related to the driver.

---

### Post by Blasphemous on 2012-08-05
and what can I do now?

The new version, the one that can be downloaded from AMD website, does not work and even the Ubuntu-repostory one I instelled using Jockey causes that black lines.

The system is fully usable, no other problems, nothing, but those stripes are very boring...

---

### Post by trundlenut on 2012-08-05
I would have a search around and see if anyone else is suffering from this problem.

Is there anything specific you need the ati driver for or could you live with the open source version?

I suppose it could be a conflict between the driver and the kernel, you could try a newer kernel and see if that helps.

---

### Post by Blasphemous on 2012-08-05
**Solved!**

There was an HDMI cable linked to a turned off television connected to the video card in addiction to the VGA that I usually use with my monitor.
I really don't know why, but, after unplugging it, everything works just fine: no black interferences!

Thanks trundlenut anyway :)

---

