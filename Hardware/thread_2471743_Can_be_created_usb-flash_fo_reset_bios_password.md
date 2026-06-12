---
title: "Can be created usb-flash fo reset bios password?"
date: 2022-02-08
forum: Hardware
---

### Post by aleksandrposs on 2022-02-08
For up high-security of BIOS, need setup password for BIOS...And if user of laptop of personal computer will forget BIOS's password, then he or she need pay money for "password reset for BIOS" on other computer companies in him or her country/town..Can be created usb-flash from "ubuntu" for reset bios password?

---

### Post by DuckHook on 2022-02-08
Ubuntu has no special abilities to reset a BIOS password. The BIOS finishes its work long before Ubuntu gets loaded.

You need to read your owners' manual to find the proper way to reset a hardware BIOS password. On my motherboard, it can be done by taking out the CMOS battery then shorting two pins on the motherboard. This is potentially dangerous: short the wrong pins and you can brick your motherboard. Every manufacturer is different, so you need to read your manual or ask technical support from your manufacturer. I've never done this on a laptop, so have no guidance for you there.

Flashing firmware can be done by downloading a firmware image, then writing that image to a USB stick. The firmware usually boots a simple DOS environment and then does its thing. Any operating system can write such an image&#8212;nothing special about Ubuntu&#8212;but such a procedure is for upgrading BIOS firmware, not for resetting your password. If you have lost your password, then the system will not allow a firmware upgrade because that is the whole point in setting a BIOS password.

---

### Post by DuckHook on 2022-02-08
*Thread moved to **Hardware** forum to better fit the inquiry.*

---

