---
title: "Problems suspending with Toshiba Satellite"
date: 2010-05-30
forum: Hardware
---

### Post by fr0otlo0p on 2010-05-30
I've recently installed Ubuntu on an older Toshiba Satellite, and I'm having problems suspending(which is really a must-have for a laptop.)  When I hit suspend or close the lid, the screen goes dark, but the suspend lights never go on.  Whatever I do, I can't bring the screen back on.  If I tap the power button after this, sometimes it will suspend normally, or it will just continue doing nothing.  If it does suspend normally, there is nothing I can do to wake it back up, or at least I can't get the screen to turn back on.  Once, I've gotten it to suspend properly, but this was after I've hibernated and resumed.

Here are the specs I know how to get, if you need more please tell me, I'm new to Linux/Ubuntu:

Toshiba Satellite M45 S169
Ubuntu 10.04 Lucid Lynx LTS Fresh Install

VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200m]
Capabilities: [50] Power Management version 2
Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0
Kernel driver in use: radeon
Kernel modules: radeon

As always, thank you for your help.

---

### Post by efflandt on 2010-05-30
I had a somewhat opposite problem with an old Compaq V2000 with 200M video, although, it lists it somewhat differently.

VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

I don't know if it was the video or something else, but I could not successfully suspend or hibernate in 9.10, but I just tried suspend and it works in 10.04.  However, I notice that you are using the default kernel mode setting (KMS) driver.  I have that disabled to use user space video modules instead, with **nomodeset** kernel boot parameter, since I had issues with KMS on other computers with older ATI chips (X1300 in particular).

I don't know if that will help your issue, but it is something to try.

---

### Post by fr0otlo0p on 2010-05-30
I added the nomodeset boot parameter, but there was no difference.  Were you suggesting that I use space video modules?  Could you please tell me how to do that, I'm new to all of this and don't know how?

---

