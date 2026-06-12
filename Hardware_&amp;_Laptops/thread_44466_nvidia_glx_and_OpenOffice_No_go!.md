---
title: "nvidia glx and OpenOffice: No go!"
date: 2005-06-26
forum: Hardware &amp; Laptops
---

### Post by lptr on 2005-06-26
When I enable glx section in xorg.conf with nvidia's latest drivers 7667 then OpenOffice does not start

Is it possible to solve this issue anyhow?

rob*

---

### Post by intangible on 2005-06-27
If you start oowriter inside a terminal, does it give you any error messages?

---

### Post by skoal on 2005-06-27
a loooong time ago in a distro galaxy far far away, I had a problem using "RenderAccel" with an older Nvidia card.  Everytime I loaded up OO, it puked up chunks of "seg faults" on my lovely X desktop, sometimes killing or freezing it.  Set that option in 'xorg.conf' to:

Option          "RenderAccel" "off"

in Section "Device", and see if you still get barfed on.

\\//_

---

