---
title: "Ubuntu 6.10 doesn't start in a notebook if is not plugged to AC"
date: 2007-04-06
forum: Hardware &amp; Laptops
---

### Post by geecko555 on 2007-04-06
Hi! I'm a mexican user, I speak spanish and a little english, I posted in other forums and nobody has  help me. I think you can help me, my problem is this:

I have a toshiba a105-s4074 notebook and ubuntu doesn't start when I don't plug the notebook to AC, it freeze in load screen (that has black screen, the ubuntu logo and a load bar). And if i plugged to AC ubuntu starts without problem.

I recently install xgl and beryl, i don't know if the problem is derivated from this.

I hope answers, thanks!!! (P.D. My english sucks)

---

### Post by freewill07 on 2007-04-06
It could be that whenever AC is unplugged there is feature that minimizes the power of a GPU.  For example, I have HP Dv6000z  NVIDIA 7200 GO and if I unplug the AC all games start to run on lower FPS.  It's called powermizer if you have Nvidia based GPU.

NOTE: This is with Windows XP.

Hope this answers to your question.

---

### Post by hardyn on 2007-04-06
thats really bizzare... does windows load correctly?

if i had to guess, i would say that the power supply in the notebook has likely failed, and is producing an unstable or low voltage on the battery... i would see about having the unit inspected, especially if it is still under warranty.

good luck.

---

### Post by IcemanV9 on 2007-04-06
Like hardyn said, it could be the power supply problem. However, you could try to add "acpi=off" at the end of the boot command (press 'e' to edit the command at the boot).

---

### Post by hardyn on 2007-04-06
iceman, good point, i forgot about that... and if i remember correctly acpi has been a problem with toshibas, historically.

---

### Post by marcantonio on 2007-04-06
> **geecko555 said:**
> Hi! I'm a mexican user, I speak spanish and a little english, I posted in other forums and nobody has  help me. I think you can help me, my problem is this:

I have a toshiba a105-s4074 notebook and ubuntu doesn't start when I don't plug the notebook to AC, it freeze in load screen (that has black screen, the ubuntu logo and a load bar). And if i plugged to AC ubuntu starts without problem.

I recently install xgl and beryl, i don't know if the problem is derivated from this.

I hope answers, thanks!!! (P.D. My english sucks)

Did you have the problem before you installed xgl or beryl?

Try booting without the splash screen, at least you'll be able to see some of what's happening.  When grub comes up highlight the entry for Ubuntu and hit 'e' then hit 'e' again for the line that starts with 'kernel'.  Remove the words 'quiet' and 'splash'.  Hit enter then 'b' to boot.  Report back where it stops.

Hope that helps.

---

### Post by nonewmsgs on 2007-04-07
see if unplugging other devices (usb, pcmcia, printer) and put them back in after boot.  power supplies have the biggest pull of power when a computer is turned on, so by not having them in might fix it.

---

