---
title: "Can I install ubuntu this way..."
date: 2009-02-15
forum: Installation &amp; Upgrades
---

### Post by dabomb1022 on 2009-02-15
I was wondering if I can buy a small hard drive that's 10-100gb's and plug it in with USB and install ubuntu on that partition. If that's possible can I then just plug it in and boot from it without changing the bios or anything? Thanks in advance!

---

### Post by sahabcse on 2009-02-15
Yes u can install Ubuntu from the USB.

---

### Post by andrewc6l on 2009-02-15
As long as your computer's BIOS can boot from the USB drive, you should be fine.

---

### Post by dabomb1022 on 2009-02-15
I don't want to mess with changing bios so can I change the windows boot manager like with wubi?

---

### Post by xeth_delta on 2009-02-15
> **dabomb1022 said:**
> I don't want to mess with changing bios so can I change the windows boot manager like with wubi?

I think that what andrewc6l meant is that the BIOS should be able to see the HDD connected at the USB port and can boot from it, like for instance, booting from a CD drive. If that is the case, there should not be big problems.

---

### Post by dabomb1022 on 2009-02-15
Thanks for the help but I just want to know if I can use something to give me a choice at boot up like with wubi.

---

### Post by andrewc6l on 2009-02-15
Set your BIOS to boot first from USB and then from HD. (It may be set to do that already). That way, if the USB drive is plugged in and turned on it will boot from there, but if it's not you'll boot to the hard drive installed in your machine.

---

### Post by xeth_delta on 2009-02-15
> **dabomb1022 said:**
> Thanks for the help but I just want to know if I can use something to give me a choice at boot up like with wubi.

An idea that might work, feel free to correct me if I'm wrong. You could install grub on the USB drive, and one of the entries in the menu being your windows installation.

As has been previously mentioned, make your computer search for operating systems in the USB ports before the fixed HDD. That way, if the USB HDD is connected, you will be prompted with a grub screen to choose what to boot. If the external drive is unplugged, the computer will boot directly to Windows.

This way, you won't be altering your fixed drive at all, either.

---

