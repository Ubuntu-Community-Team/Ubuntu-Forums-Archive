---
title: "[SOLVED] ACPI -t help"
date: 2008-07-01
forum: Hardware
---

### Post by Akash Singhal on 2008-07-01
Can anyone please tell me that what does ACPI temperature mean.
I typed acpi -t in the terminal which then showed me my battery status and a temperature...which temp is this..I have core 2 Duo processor. Is this the temperature any one of the 2 processors or something else..moreover can I know my processor's temperature

NB: lm-sensors don;t work for me cause there is a bug which makes it unable to detect temperature with coretemp sensors
X sensors also dont work for me...please help
Thanks in advance.

---

### Post by sdennie on 2008-07-01
If you have a Core 2 Duo, you only have a single processor with 2 cores.  The temperature reported from "acpi -t" comes from the BIOS and you can consider it to be the temperature of your processor.

---

