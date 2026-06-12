---
title: "Lenovo Ideapad 5: Touchpad stopped working after a suspend fix."
date: 2023-03-11
forum: Hardware
---

### Post by zandbye on 2023-03-11
So, i had a suspend problem where my screen would go black and not turn on (only if i force shut down the pc)
For some reason my touchpad stopped working in Ubuntu. It works in BIOS and on my Windows boot.
I have tried modifying grub, which didn't work so thats why i am typing here.

My laptop is a -> Lenovo IdeadPad 5 Pro 16ACH-6
When first installing ubuntu the touchpad worked fine, and after i fixed my suspending bug it doesn't work anymore.
I'm pretty sure that this is not the case for the problem. But i have used about 2-3 hours now and im not sure where the error is.

I think that the problem is the fact that Ubuntu doesn't seem to recognize my touchpad driver. It is not present in System Profiler.
I have the latest version of Ubuntu installed.

My current edit in grub:
GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash acpi=off i8042.nopnp=1 pci=nocrs"

Anyone who can help?
Thank you

---

