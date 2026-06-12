---
title: "Acer Aspire 5633 WLMi wakes but screen remains black"
date: 2008-05-12
forum: Hardware
---

### Post by LucaTNT on 2008-05-12
Hi,
I have an Acer Aspire 5633 WLMi with a nVidia GeForce Go 7300 graphics card and Kubuntu Hardy.
It suspends and resumes with no problems (tried to play an audio file through aplay and it plays), but the screen remains black. I tried to switch to a terminal with Ctrl + Alt + F1 and restarted X but I had no luck.

I have the same behaviour clicking logout/suspend or using pm-suspend.

What can I do?

Thanks in advance for your help!

Luca

---

### Post by LucaTNT on 2008-05-12
I solved it!

Unfortunately I needed Vista to do it, though.
I had to downgrade BIOS from version 3.5 to 3.2 using [this tool]("ftp://ftp.work.acer-euro.com/notebook/aspire_5630/vista/BIOS/BIOS.zip") from Acer.
Then I edited /etc/default/acpi-support and made sure that ACPI_SLEEP and ACPI_HIBERNATE were set to TRUE and uncommented, and I set POST_VIDEO and SAVE_VBE_STATE to FALSE.
That's it!

P.S.: I found this solution [here]("http://ubuntuforums.org/showthread.php?t=614106").

---

