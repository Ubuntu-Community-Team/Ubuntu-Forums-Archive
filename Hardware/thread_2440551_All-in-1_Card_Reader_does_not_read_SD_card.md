---
title: "All-in-1 Card Reader does not read SD card"
date: 2020-04-12
forum: Hardware
---

### Post by thosecars822 on 2020-04-12
Hello

An old Fujitsu Scaleo P desktop computer, with Lubuntu 18.04 and an "All-in-1 Card Reader" that came inside of the computer does NOT recognize an SD card I put in this reader. 

You can find the output of several commands such as dmesg, lsusb, lspci and lsblk in the following attachment:
[https://paste.ubuntu.com/p/BqBcSPJ4jv/](https://paste.ubuntu.com/p/BqBcSPJ4jv/)

All this output got done with the SD card inside of the reader.

Does anyone have any suggestion to fix this?


Thanks in advance

---

### Post by CelticWarrior on 2020-04-12
If it still works it supports, at best, the old up to 2GB cards, nothing else.

---

### Post by thosecars822 on 2020-04-12
It seems you are right! I was using a 32 GB micro SD inside of an adapter and it did not get recognized. Nonetheless after reading your message, I looked for an old 2GB SD card and it got recognized at the first try. Thanks
Out of curiosity, how did you get to know this All-in-1 Card reader only recognizes SD cards, the size of which is NOT bigger than 2 GB?

---

### Post by thosecars822 on 2020-04-12
Might there be any firmware/drivers available for download somewhere to make this reader work with SD cards, the capacity of which is bigger than 2 GB?

Thanks in advance

---

### Post by CelticWarrior on 2020-04-12
SD card readers of that vintage supported only the first generation, up to 2GB.
That is the one and only "SD";
From 4G and up to 32GB it's SDHC (SD High Capacity) and the current generation, 64GB and up, is SDXC (SD Extended Capacity).

[https://kb.sandisk.com/app/answers/detail/a_id/2520/~/sd/sdhc/sdxc-specifications-and-compatibility](https://kb.sandisk.com/app/answers/detail/a_id/2520/~/sd/sdhc/sdxc-specifications-and-compatibility)

No, it isn't a matter of firmware/drivers.

---

