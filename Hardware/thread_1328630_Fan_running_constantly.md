---
title: "Fan running constantly"
date: 2009-11-16
forum: Hardware
---

### Post by piusvelte on 2009-11-16
*UPDATE:
Despite numerous reboots at work, since booting up at home, using both boot options described below, my fan appears to be working normally. It starts around 44 degrees and stops at 39.

Hi,
I've a pretty bad headache now from my laptop fan that will not stop running. I've done a lot of searching and reading before posting. I'm using a Gateway laptop with an intel mb. It's the only OS installed. Jaunty would occasionally stop the fan, but not often. Then I upgraded to Karmic and the fan never stops.

I installed grub2 and have tried the boot options acpi_osi=\\\"Linux\\\" and acpi_enforce_resources=lax, editing the /etc/default/grub, and then running update-grub. Neither makes a difference, either separately or in combination.

I installed lm-sensors and ran sensors-detect, but the result was "Sorry, no sensors were detected."

My cpu temp ranges from 39 to 56 mostly.

I ran pwmconfig, which reports "No sensors found!"

My bios doesn't have an option to turn the plug and play off, and is set to the recommended "Other".

Any help trying to fix this would be really appreciated. I really do not want to have to downgrade. Thank you!

---

