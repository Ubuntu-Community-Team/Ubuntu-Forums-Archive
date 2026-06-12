---
title: "Failing to find second hard drive?"
date: 2008-05-21
forum: Hardware
---

### Post by Zyndrof on 2008-05-21
Hi!

I have been using Ubuntu for about a week and have tried a few things to access my second hard drive. Since the installation of Ubuntu it is not found in BIOS anymore.

I opened the computer and checked the cables which seemed OK.

When I installed Ubuntu I had troubles for four days before I was able to install after making the following changes in BIOS:

**Onboard PATA/SATA Configuration** was changed from **Enhanced Mode** to **Combined Mode**. This in turn disabled the option to configure **Onboard PATA/SATA Adapters**.

After speaking with some people in the #ubuntuforums channel I tried to configure /boot/grub/menu.lst, adding **pci=nommconf irqpoll** without any difference.

Both hard drives are the exact same brand, and since one works one would think the other one should too.

Do you have any suggestions to how this can be solved or at least what can have happened (with XP installed one week ago both hard drives where running fine)?

Thank you in advance!

---

### Post by digitalvectorz on 2008-05-21
What BIOS are you running?

Not too sure on this, but I know I had problems with the sound device (a little different), but would it make any difference to upgrade the BIOS and and resetting?

Also, what were the troubles you had before making the changes to the BIOS?  Just installation problems or post-install problems?  If they were just install problems, try changing back the settings to the original settings you had and see if that works?

---

### Post by Zyndrof on 2008-05-22
> **digitalvectorz said:**
> What BIOS are you running?

Not too sure on this, but I know I had problems with the sound device (a little different), but would it make any difference to upgrade the BIOS and and resetting?

Also, what were the troubles you had before making the changes to the BIOS?  Just installation problems or post-install problems?  If they were just install problems, try changing back the settings to the original settings you had and see if that works?

The BIOS is HP version 3.04 I think.

The problem was that I couldn't install Ubuntu at all. I just tried changing back to the original settings which made Ubuntu lock at the loading stage of the boot. I passed the grub though so I should be able to make some changes there.

---

### Post by Zyndrof on 2008-05-27
I solved it! :)

This is what I did and never even considered before...

I turned **Onboard PATA/SATA Configuration** to **Enhanced Mode** and then I changed the settings for **Onboard PATA/SATA Adapters** from **Both** to **SATA**. Now I am able to access both hard drives.

---

