---
title: "Laptop cannot boot"
date: 2014-08-20
forum: Hardware
---

### Post by paul555 on 2014-08-20
Hi all,

I have a laptop - [model is Acer Aspire E1-531-2697]("http://www.notebookcheck.net/Acer-Aspire-E1-531-2697.82089.0.html") - with Ubuntu which i cannot boot.
Suddenly when i power on the laptop, i see only the Acer splash screen (see attached image) and then nothing happens.
Can you please help me to find out why Ubuntu is not loading?

Thanks in advance.

---

### Post by deb2014 on 2014-08-20
hello,

this could be related to uefi/legacy bios mode, although both are supported by ubuntu.
If this option exists in the bios, try to force legacy at first.

Could you also give more details ? Have you already installed ubuntu ? or just try to boot on the install disk ?

---

### Post by paul555 on 2014-08-20
Thank you for the reply.
The laptop was running fine Ubuntu for a year now, and suddenly for the last three days it cannot boot showing only  the Acer splash screen.

 I will try to check the bios mode.

---

### Post by deb2014 on 2014-08-20
Try to boot on a live CD to see if the problem persists, if you suceed to boot, get a run shell and reinstall grub (see if any error messages).

Is your laptop old ? Check also the bios battery, you probably know that  inside each motherboard lies a small battery like in swatchs,
if this one runs out, boot may become unpredictible.

---

