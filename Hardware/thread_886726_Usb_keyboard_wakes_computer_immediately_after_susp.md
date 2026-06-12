---
title: "Usb keyboard wakes computer immediately after suspend"
date: 2008-08-11
forum: Hardware
---

### Post by frenkel on 2008-08-11
My computer suspends fine with a normal ps2 keyboard connect. However, if I connect my Apple aluminum keyboard (with built-in usb hub), it wakes immediately after suspend. I tried disabling usb legacy mode in the bios, but it didn't change a thing.
Anybody know how to fix this?

Thanks.

---

### Post by sdennie on 2008-08-11
I would check to see if you have USB wakeup enabled in the BIOS.  If not, see what the output of this is:

```

cat /proc/acpi/wakeup

```

If you see USB devices listed as enabled, you should be able to disable them with:

```

sudo sh -c "echo USB0 >> /proc/acpi/wakeup"

```

(Substitue USB0 with whatever USB device is enabled for wakeup for each device that is enabled)

If that works, add the following command to /etc/rc.local to make the change persist across reboots:

```

echo USB0 >> /proc/acpi/wakeup

```

(Again, once for each USB device that is enabled)

---

### Post by frenkel on 2008-08-11
Nope, both in BIOS and in the wakeup file the USB devices are disabled.

---

### Post by frenkel on 2008-08-12
Bump :oops:

---

### Post by chrishutt on 2008-11-11
I was experiencing the same problem and I eventually found a solution that works for me here:

[http://www.gossamer-threads.com/lists/mythtv/users/316830](http://www.gossamer-threads.com/lists/mythtv/users/316830)

Basically it was the way my motherboard (ASUS M2N4-Sli) was set-up. Just as described in the link setting the USB power jumpers to +5SB works like a charm. Suspend and hibernate now fully functional and 100% reliable so far.

---

