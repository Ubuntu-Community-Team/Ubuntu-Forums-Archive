---
title: "Acer 1681 - No Battery Support?"
date: 2004-12-27
forum: Hardware &amp; Laptops
---

### Post by kudlatygosc on 2004-12-27
Hi all.

I've got Acer 1681 WLCI. Few days ago I installed Ubuntu and almost everything works fine - sound was detected, xfree with WXGA support works, powernowd is up and running, im closid lid it goes to sleep, opening it and laptop wakes up - all that from start with no configuration at all. The thing which is not detected by system is battery. I know that acpid is running, I can check the temperature of processor, but I can't check how much battery power is left. When I change directory to "/proc/acpi/battery" - it's empty. Still, I know that Acer 1681 WLMi works fine ( I know that from Ubuntu Wiki's "HardwareSupport/Machines/Laptops".
Someone had similar problem?

Appreciate any help.
&
Thanks in advance.

---

### Post by snop on 2004-12-29
Hi,

I own an Acer Travelmate 4001 Wlmi. It uses a "smart battery" which is not *yet* supported by Linux. Check this:

[http://sourceforge.net/mailarchive/message.php?msg_id=10126159](http://sourceforge.net/mailarchive/message.php?msg_id=10126159)

They seem to be working on this but are not having any support from Acer...

My battery directory is empty too so it may be the same issue. 

Bye

SnOp

---

### Post by claude.p on 2005-01-02
Hi,

Same problem with an Acer 1682.

---

### Post by LB06 on 2005-01-02
Same here.

Acer Travelmate 4501LCi (basically same laptop as the 4000WLMi, but without widescreen and 9700 pro) running Warty.

---

