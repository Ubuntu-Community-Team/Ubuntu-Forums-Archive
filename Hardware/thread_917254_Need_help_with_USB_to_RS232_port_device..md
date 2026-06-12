---
title: "Need help with USB to RS232 port device."
date: 2008-09-11
forum: Hardware
---

### Post by MR.UNOWEN on 2008-09-11
Hello,

So I purchased a usb to RS232 port converter. Anyway, I'm having a little trouble with it. I was following a tutorial and by the looks of it Ubuntu recognizes it, but the problem I have is that I need it to appear as if it were a normal RS232 and show up as one of the ttyS#. From the tutorial, it says it shows up as ttyUSB#. How do I fix this problem?

---

### Post by MR.UNOWEN on 2008-09-12
Can some one please help me change ttyUSB0 to ttyS4 or some how direct ttyS4 to ttyUSB0?

---

### Post by IntuitiveNipple on 2008-09-12
Why does it have to be aliased from its original device name? Is there some application that won't accept a user-specified device?

The solution is to create a udev symlink.

Edit the file **/etc/udev/rules.d/60-symlinks.rules** and add a rule similar to the Palm Pilot example, but that matches attributes specific to the USB-to-serial adaptor (such as the vendor and product ID).

However, you'll also need to ensure that the target device name you want to use isn't already taken, which probably means further udev rules (probably in the 20-names.rules) file to ensure the ttyS# target isn't allocated.

For more information on udev read the manula page:
```

man udev

```

To discover unique attributes of the device run this command before plugging the device in. You'll see all the udev messages and attributes that you can use to recognised it in the udev rules:
```

sudo udevmonitor --environment

```

---

