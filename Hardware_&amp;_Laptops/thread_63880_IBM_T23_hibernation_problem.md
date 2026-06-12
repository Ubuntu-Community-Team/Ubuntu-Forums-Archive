---
title: "IBM T23 hibernation problem"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by hubidubi on 2005-09-09
Hi,

I have an IBM T23 laptop, and I use it with standard 2.6.10-5-686 kernel. The hibernation is not working stable. Sometimes it works fine, but usually it brings the laptop to sleep, the hdd powers goes down, the lcd switches off, but the laptop remains switched on.

My other problem is, that there's a blanking hotkey (Fn+F3) which worked fine under debian, it completely switched of the lcd, but here it just blank the lcd.



Thanks in advance for any help.


Hubidubi

---

### Post by mlord on 2005-09-09
[QUOTE=hubidubi]Hi,
I have an IBM T23 laptop
[/QUOTE]
Great!  The nice thing about Thinkpads, is that they have an APM bios.  So if you want everything to "just work" on them, you could try uninstalling ACPI support, and installing APM instead.  That's probably what your old Debian install did.

-ml

---

### Post by thin_king on 2005-09-09
I have a T23 also with both Debian and Ubuntu. Hibernation (Fn+F12) works for me but I hardly use it. Suspend (Fn+F4) works fine, never a problem. That's what I use all the time.

Try using APM and suspend, should work

---

