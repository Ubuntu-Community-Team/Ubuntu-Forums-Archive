---
title: "Can setting POST_VIDEO to false damage my embedded graphics card?"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by Number_6 on 2007-12-14
I think I've finally got the new Radeon driver working properly with standby. The thing is, to do so I had to set "POST_VIDEO=false" in /etc/default/acpi-support. In the file, it says that having POST_VIDEO set to true attempts to warm reboot the graphics card when returning from standby. Am I causing extra wear and tear on my graphics chipset by setting this to false?

Note: This isn't a driver question, just a 'what does this thing do and can it hurt my system' question.

Thanks

---

