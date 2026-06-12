---
title: "Laptop Lid registers wrong state"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by json684 on 2007-01-29
I have been trying to get suspend working on my laptop, an HP dv1315. And I have narrowed it down somewhat. In KDE suspend works every other time I close my lid.  Looking at /proc/acpi/button/lid/LID, I can see that after a working suspend when the computer comes back from suspend the lid is still considered closed. If I push the suspend button once again, the lid is considered open. And then it will suspend. Can anyone point me in a direction to look, or offer a suggestion? I have looked around the forums and haven't been able to find an answer. I am running Edgy, with KDE installed over regular Ubuntu. And using klaptop as the power manager. Thanks.

---

