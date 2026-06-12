---
title: "ati x1250 and 8.04 Problems"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by Zw4nzig on 2009-04-11
I am not sure if this qualifies as a bug just yet, so I'm going to put this on here first before filing a bug (Not to mention I haven't filed a bug yet, and don't want to mess up.)

Little backstory incase it helps:

Acer Extensa 4420 with the ati x1250 onboard, and a broadcom wireless chip. I followed the guide for installation of 7.10, and everything (Included proprietary drivers!!)except wireless worked.

Well, I installed 8.04 and I presume it is crashing before or during x starting. Grub loads, select 8.04, I get the ubuntu loading screen, after completion, it dies.. Screen changes shades of black a couple times, then a complete freeze on a black screen (Laptop has power, it's a lit-black.)

Strangely, booting into recovery and choosing "fix x", repairs it.. sort of. It disables the ati driver in restricted manager, and it boots although really, realy slow and compiz works, but too slow to bear.. Like it isn't using the driver.

Any thoughts on how to get it running WITH Compiz working correctly + an ATI driver of some kind?

Would anyone recommend 8.10 for this chipset?

Thanks for the time, guys.

(Edit: Sorry, forgot the ati driver version.. 8.593, I think. the .run is called ati-driver-9-5-x86.x86_64.run )

---

### Post by Zw4nzig on 2009-04-11
Bringing this up really quick, this is rendering my laptop useless.

From what I can tell, it is entirely the fault of the ati driver, because fix-x is getting rid of the driver, and it works..

Edit: Even more info! When booting into single user mode (without using fix-x), it does "Running local boot scripts [ok]", then hangs.

Hope that helps anyone looking into this.

---

