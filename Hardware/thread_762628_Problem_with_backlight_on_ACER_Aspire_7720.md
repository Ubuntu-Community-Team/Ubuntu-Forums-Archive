---
title: "Problem with backlight on ACER Aspire 7720"
date: 2008-04-22
forum: Hardware
---

### Post by Bafflerog Rumplewhisker on 2008-04-22
Does anyone know why I have to adjust my backlight manually (using the function combo keys) each time I reboot my system? It seems to reset to the darkest level upon reboot.

I am running Ubuntu 8.04 RC on an ACER Aspire 7720G. I had the same problem while running the beta, installing proprietary NVIDIA drivers didn't solve the problem (not sure if they're even relevant).

Thank you in advance.

---

### Post by Bafflerog Rumplewhisker on 2008-04-26
I've just confirmed said problem with the LTS release, as well. Any ideas, anyone?

---

### Post by slava1024 on 2008-05-30
Hello

For problem of backlight i have found no fix, but solution.
1. Install xbacklight package using Synaptic
2. Go System->Preferences->Sessions->Startup Programs->Add
3. Write to Command: *xbacklight -set 40*
This command will set backlight brightness to 40%

Regards

---

