---
title: "Installing a Quadro driver on a GeForce"
date: 2014-09-13
forum: Hardware
---

### Post by lsusb on 2014-09-13
I would like to use quad-buffered stereo but this feature is only available in with the Quadro driver. I have a GeForce GTX680, it's Quadro equivalent in K5000. Both cards are nearly identical, they have the same chip inside. People on Windows can install Quadro drivers on GeForce by unpacking the driver and editing one .inf file then running the setup. They can also do it by choosing an option in RivaTuner to emulate a different card (change it's device ID in the system). How do I do this on linux?

setpci is not working. It's not actually changing the DEVICE_ID.
[COLOR=#444444][FONT=Helvetica Neue]echo "10DE 11BA" > /sys/bus/pci/drivers/nvidia/new_id' doesn't do anything either[/FONT][/COLOR]
I can unpack the linux driver but can't find any information on what to edit in it.

Any suggestions?

---

### Post by lsusb on 2014-09-21
[https://github.com/magestik/glQuadBufferEmu](https://github.com/magestik/glQuadBufferEmu)
This is the only workign solution I found.

---

