---
title: "Hardware in Sun VirtualBox running Ubuntu 9.04 as guest?"
date: 2009-09-19
forum: Hardware
---

### Post by Ironfrunk on 2009-09-19
I have an XFX GeForce 9600 GSO and the drivers for it on the host OS, but the guest OS is running the default "virtual" drivers.

I'm running Linux Mint 7 as the Host OS and Ubuntu 9.04 as the guest OS via VirtualBox.
I was wondering if there was any way to enable my host hardware drivers under the guest OS?

Thank you in advance :)

---

### Post by SoftwareExplorer on 2009-09-19
Let me get this clear: you want to have 3D compiz etc in virtualbox. I'm pretty sure you can't use the drivers for you graphics card in virtual box. I think however, that virtualbox emulates a graphics card if you have it set right, but (correct me if I'm wrong, I haven't checked in awhile) ubuntu doesn't have the driver for that hardware (yet).

---

### Post by earthpigg on 2009-09-19
video hardware acceleration in VBox *proprietary* 3.0.6 r52128 works fine for me with guest additions installed in an ubuntu 9.04 guest using the "Virtual Guest Additions For Linux Module" in the guest machine's system -> administration -> hardware drivers...

is that not working for you at all?

or do you just want the native hardware drivers to work within VBox...? i am pretty sure that would not be stable, if possible at all.

---

### Post by SoftwareExplorer on 2009-09-19
By the way, Welcome to the ubuntu forums :P

---

### Post by talsemgeest on 2009-09-19
Since the guest isn't actually using the guest hardware (as it is being used by the host os), you would get no more benefit from using the host drivers than if you were to use a competely different set of drivers.

---

