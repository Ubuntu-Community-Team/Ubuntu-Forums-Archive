---
title: "How To Reset BIOS When I Have No Display?"
date: 2014-09-17
forum: Hardware
---

### Post by buzzingrobot on 2014-09-17
How can I trigger a reset of BIOS to default when the display is dark and nothing is displayed?

This is a Lenovo M93p desktop. It has onboard Intel video and a disrete AMD card.  The default video option in the BIOS is 'Auto', which uses a discrete card if one is available and rolls over to the Intel otherwise.

I attached a VGA cable, set the BIOS to use the Intel, and the screen was black on the boot.  The monitor complains that "No cable is connected". 

I removed the AMD card and rebooted, but no change.

So... How do I reset the BIOS' video option when the display isn't showing anything?

---

### Post by maxinstuff2 on 2014-09-18
Depends on your motherboard but most have pins on them that you can short for a few seconds to force a reset. Or just pop the battery out for a few minutes. 

It's your motherboard so be careful, try to find the manual if you can and refer to that.

---

### Post by buzzingrobot on 2014-09-18
Success via moving the jumper to clear CMOS. Yay. Battery trick didn't do it. (Lenovo's manuals are long and detailed. Kudos to them.)

If you try this at home, folks, you will need to enter BIOS setup on the next power up and reset time and date, at a minimum.

Better to avoid the whole problem via If It Ain't Broke, Don't Fix It!

Still curious how to actually use onboard video in this machine, though. The AMD 8570 is a half-height non-retail card made for Lenovo. It's a new machine still with Windows.  Booting up a live 14.04.1 image shows it's using Gallium. Not used to AMD cards; guess I need to find out if this thing can use a proprietary driver.

---

### Post by Bucky Ball on 2014-09-18
Best to post a new thread with a descriptive title regarding using the graphics cards and mark this one as solved. Will improve you chances of a resolution. Good luck. 

* Notice you've marked it solved now. ;)

---

