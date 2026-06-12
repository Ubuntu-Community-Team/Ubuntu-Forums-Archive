---
title: "Ubuntu 12.04 in HP Pavilion dv6 hang on boot after install"
date: 2012-04-28
forum: Hardware
---

### Post by monkiki on 2012-04-28
Hi there,

I have downloaded and installed Ubuntu 12.04 Desktop (32 bits) in my HP Pavilion dv6 lapton. The installation live-cd works pretty well, and all the installation process is fine.

But when it finish and the laptop reboots, it hangs in a black screen with a blinking cursor. :confused:

No GRUB, no error message.

I know these are very little details, but I don't know how to be more verbose.

---

### Post by monkiki on 2012-04-28
Problem solved! I'm not sure why, but GRUB was installed in the pendrive and not in the hardisk. I have ejecuted grub-install /dev/sda and now boot perfectly :)

---

### Post by bedewilson on 2012-04-29
I had the same on my new Toshiba laptop - this solved it.

---

