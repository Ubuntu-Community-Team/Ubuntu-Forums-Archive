---
title: "Login Screen freezing  Ubuntu Studio 22.04 Mouse is moving"
date: 2022-10-13
forum: Hardware
---

### Post by wavesound on 2022-10-13
Hi All
Had the screen freeze on logging in, Mouse can move but not select anything.
Have to hard reboot the box.

It seems tied to the TPM error I get when booting no Idea what TPM is on my Dell workstation.
I found a thread that told me to  change Grub and add this line:

******************************
GRUB_CMDLINE_LINUX_DEFAULT="quiet loglevel=0 splash"
***************************************

Don't forget to run update grub

This has stopped the errors and now I don't seem to get the Freezing login screen

Was becoming a real problem.

Cheers all

---

### Post by tetobear on 2023-02-04
Thank you so much had same problem with Dell Optiplex 7020

> **wavesound said:**
> Hi All
Had the screen freeze on logging in, Mouse can move but not select anything.
Have to hard reboot the box.

It seems tied to the TPM error I get when booting no Idea what TPM is on my Dell workstation.
I found a thread that told me to  change Grub and add this line:

******************************
GRUB_CMDLINE_LINUX_DEFAULT="quiet loglevel=0 splash"
***************************************

Don't forget to run update grub

This has stopped the errors and now I don't seem to get the Freezing login screen

Was becoming a real problem.

Cheers all

---

