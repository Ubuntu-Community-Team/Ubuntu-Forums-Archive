---
title: "Installing my Logitect MediaPlay Mouse, I don't understand the instructions"
date: 2008-06-02
forum: Hardware
---

### Post by Jordanwb on 2008-06-02
I found this page: [http://daemon.prozone.org/~david/projects/lmpcm_usb/](http://daemon.prozone.org/~david/projects/lmpcm_usb/) for a driver for my Logitech mouse. It's the exact same one in his picture. I'm at the part "Loading Modules"

> Edit /lib/modules/your-kernel-version/misc/modules.dep and remove usbmouse and hid entries. This is required because these modules "steal" any kind of mouse, so we have to load lmpcm_usb first. If usbmouse and/or hid are required for any other device, just load them after lmpcm_usb. But don't forget, lmpcm_usb SHOULD LOAD FIRST that any generic mouse driver.

After a lot of "dir ./" and "dir ../" I found modules.dep (it wasn't in the misc folder)

The part I don't understand (at this point in the how to) is this part:

> and remove usbmouse and hid entries.

I found these:

```

/lib/modules/2.6.24-17-generic/kernel/drivers/hid/usbhid/usbkbd.ko: /lib/modules/2.6.24-17-generic/kernel/drivers/usb/core/usbcore.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/hid/usbhid/usbmouse.ko: /lib/modules/2.6.24-17-generic/kernel/drivers/usb/core/usbcore.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/hid/usbhid/usbhid.ko: /lib/modules/2.6.24-17-generic/kernel/drivers/hid/hid.ko /lib/modules/2.6.24-17-generic/kernel/drivers/usb/core/usbcore.ko
/lib/modules/2.6.24-17-generic/kernel/drivers/hid/hid.ko:

```

So as posted in the code snippet of the modules.dep file some of them are on the same line as another so I don't know what to remove. I attached the modules.dep file as a text file. And since the max I could put for a txt was 19 K I tarballed (tarballed?) it.

Also I don't understand the "# modprobe" part either.

Ah the joys on Linux.

---

