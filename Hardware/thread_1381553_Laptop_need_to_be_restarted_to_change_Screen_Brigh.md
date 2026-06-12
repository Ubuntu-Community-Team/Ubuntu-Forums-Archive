---
title: "Laptop need to be restarted to change Screen Brightness."
date: 2010-01-14
forum: Hardware
---

### Post by pramtung on 2010-01-14
Hi guys. I know it's kinda strange, but I've found this strange problem in my ACER Aspire 4732Z, Everytime I try to adjust the screen brightness, the brightness won't be changed. Unless I restart the computer and the brightness change will take effect. Please help me out with this problem..

---

### Post by pramtung on 2010-01-18
Oh come on, noOne help..

---

### Post by dyslexia on 2010-01-18
su root -c 'echo 0 > /proc/acpi/video/VGA/LCD/brightness'

---

### Post by pramtung on 2010-01-19
Yeah, I've done that, the brightness meter is really changed but the monitor is barely changed at all. Help..

---

### Post by t4thfavor on 2010-01-21
Do you have a key on your kepboard labeled fn? if so hold that, and press the one that looks similar to bright sun, that is the left arrow for my aspire 5100. It seems backwards, but it does work. Keep in mind that the screen may not change all that much.

I have an intel that I can turn it all the way off, and still see the non-backlit images if I try hard, while this ATI still looks very bright when all the way dimmed at night.

---

