---
title: "Gateway LX6200 won't boot Ubuntu 10.04 LiveCD"
date: 2010-10-31
forum: Hardware
---

### Post by macfreak on 2010-10-31
Hello World,

I have a Gateway LX6200-1 that refuses to load Ubuntu from the LiveCD. It just sits on the black screen with Ubuntu in the middle, pulsing forever. When I switch to the second console (ctrl+alt+cmd+F2) it just shows a blinking _ cursor forever, but when I return to the first console (ctrl+alt+cmd+F1) it reads:

```

udevd[109]: worker [114] unexpectedly returned with status 0x0100

udevd[109]: worker [114] failed while handling '/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/0003:05AC:0304.0002

... [ the above is repeated many times ] ...

udevadm settle -timeout of 180 seconds reached, the event queue contains: /sys/devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/0003:05AC:0304.0002/hidraw/hidraw4 (957)

```

Can anyone help me load Ubuntu? I also have an external HD with Ubuntu 10.1 installed on it, that refuses to boot in the same way. Is this a hardware issue? Obviously there is something malfunctioning on the USB bus... IDK anything about it really.

Please help!

Thanks in advance,
Eliot Simcoe

---

### Post by macfreak84 on 2010-11-12
Bump. Anything?

I've tried different versions of Ubuntu (10.04, 10.10), and unplugging the USB ports from the motherboard. Everything results in the above errors. The CD loads the first screen where you choose the language but when you tell the computer to "Try Ubuntu without installing it", it dies on an unexpected udev result (see above). There are no USB devices other than the keyboard and mouse plugged into the computer.

Can anyone help me or at least confirm that Ubuntu works on a Gateway LX6200?

Thanks for any help!
Eliot Simcoe

---

