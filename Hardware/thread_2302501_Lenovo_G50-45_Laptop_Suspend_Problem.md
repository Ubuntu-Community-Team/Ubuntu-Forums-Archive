---
title: "Lenovo G50-45 Laptop Suspend Problem"
date: 2015-11-10
forum: Hardware
---

### Post by jlcapps on 2015-11-10
Hi,

I have a new Lenovo G50-45, and it works well, with one exception: suspend/resume will work only once per boot. That is, I can suspend the laptop however I wish (using the menu, closing the laptop lid, typing ```
pm-suspend
``` at the CLI) and resume once. If I suspend again, the laptop will reboot rather than suspend. I see nothing amiss in ```
/var/log/pm-suspend
```. Has anyone run into this? How would I go about debugging it?

As a work-around, I've enabled hibernation, but actual suspend would be *really nice*.

EDIT: Should have mentioned of course that I'm running 15.10, but I've found exactly the same behavior in 15.04, and 14.04.

Thanks!

---

