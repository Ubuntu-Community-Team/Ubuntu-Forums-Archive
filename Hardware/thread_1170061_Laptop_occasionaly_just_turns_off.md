---
title: "Laptop occasionaly just turns off"
date: 2009-05-25
forum: Hardware
---

### Post by Stex on 2009-05-25
Since updating to Jaunty (I have used ubuntu for 3 years and never had this problem) I have, on occasion, had ubuntu decide to shut itself down without warning. It doesn't crash, it calmly goes through the shutdown splash sequence. I've checked the messages log and found the following snipped just before "exiting on signal 15":
> kernel: [35974.270748] ACPI: Critical trip point

As far as I can tell this is some auto-shutoff safety for when processor heat exceeds any sane values. However, last time this happened I checked the heat and this really wasn't the case. My laptop is currently running fine and is noticeably hotter than it was last time it auto-shutdown.

Is there anything that can be done to check/tweak the CPU thermometer to make sure it isn't spewing incorrect temperatures?

Thanks

---

### Post by Dark_Stang on 2009-05-25
You could reflash the Bios if there is an update available. Did you give the computer a thorough cleaning already?

---

