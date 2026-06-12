---
title: "Get sysfs info on USB-RS232 adapter"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by steve0921 on 2007-06-20
I'm using an embedded Ubuntu machine with several USB-RS232 adapters to control various peripherals (motors, cameras, etc.), and want to make udev rules to consistently name each device based either on the particular converter unit it has (ideal) or on the physical USB port it is plugged into.

To accomplish my ideal plan, I've discovered that I need to find information in sysfs that distinguishes the adapters (like serial numbers), but have been unable to find this. My searching so far has lead me to try:```
udevinfo -q path -n /dev/ttyUSB0
```
but that tells me there is no record in the database for it. The device node definitely exists though and I can communicate with it.

Is there something I'm doing wrong? Is there a better way to find this information?

I also welcome input on how to name based on USB port, which would be almost as good a solution.

Thanks,
-Steve

---

### Post by IntuitiveNipple on 2007-06-20
Will this help?
```
$ sudo lshal
```

---

### Post by steve0921 on 2007-06-20
Just tried that out on a home computer. Looks like it may be useful. Will know more when I get to really try it.

---

### Post by steve0921 on 2007-06-25
Just a wrap-up in case anybody comes across this thread in the future:

The best command to use for this is ```
udevinfo -a -p <sysfs top level device path>
```

The command in to original post is supposed to find the sysfs path for this device, but doesn't work (for an unknown reason). Instead I just looked for a dev file (which every top level path will have) and used grep to sort it out.```
find /sys -name dev | grep USB
```.

---

