---
title: "Polar IR-721 USB infrared driver installation"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by kjempe on 2007-07-01
Dear community.

Some time ago I purchased the Polar IR-271 IrDA-dongle to evaluate my training data on my computer but used it only with the Polar software in Windows, as I was unable to get the gadget working. Here's what the README says (and which I cannot comrprehend):

```
These driver files are here to help you get started.  You will at least

need to install the driver into the kernel loadable modules directory

for IrDA (.../kernel/drivers/net/irda) and then insert the module (insmod).



The following modules are incompatible with this driver and on some

versions of Linux, these modules must be removed from the kernel:



   ir-usb

   irda-usb



You might need to insmod the "irda" module before starting.



Before running "make," check the values of LINUX_VERSION,

INLUDEDIR and MODPATH.



Before releasing anything, update the IRDA4210_VERSION string, which

gets embedded in the module.



All devices supported by this driver require a firmware patch to run.

Failing to install a patch into the device (or installing the wrong

patch) can result in a lockup of the USB bus (and the entire system).

For your protection, the driver will not allow you to open the device

unless you first apply the patch.



The "stir42xx" utility in the "tools" directory will install a patchfile.

The patch files are firmware that run in the device and are not available

with this distribution, since they are not covered under the GNU GPL.

Run "stir42xx --help" for more information.



The "sgtlpatch" script attemps to determine the version of the attached

device and will select the appropriate patch file that it finally passes

to the stir42xx utility.

```

The driver's directory contains the following files:

gpl.txt
irda-ioctl.h
irda-usb.c
irda-usb.h
Makefile
README

The subdirectory "tools" contains the following:

getargs.c
Makefile
sgtlpatch
stir42xx.c
stir42xxi.h

A clue anyone how to get this done step-by-step?

Thanks in advance for any guesses.

---

### Post by Gravito on 2007-09-29
Hello,

I just bought the same USB-IR device and I am looking for any information to get the raw data from the Polar 720i watch onto my PC running Ubuntu (6.10 or later).

I tried the famous s710-0.21 program but did not yet succeed to use it :
[LIST]
[*]the USB vendor-ID & product ID needed to be patched
[*]the port is already in use by the irda-usb driver (so I'd need to stop it)
[*]finally I had another error that I did not understand (yet)
[/LIST]
Then I thought that I should attempt to take the benefit of this driver....

If you made any progress since then, could you share your experience ??

Thanks in advance

---

