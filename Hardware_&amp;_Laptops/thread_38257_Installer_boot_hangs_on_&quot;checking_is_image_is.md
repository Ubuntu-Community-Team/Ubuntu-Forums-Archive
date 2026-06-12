---
title: "Installer boot hangs on &quot;checking is image is initramfs...&quot;"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by BaLdMoNkEy on 2005-05-30
I am trying to install Ubuntu on a very old PII 400Mhz computer with 256Mb of ram, 9gb Maxtor HDD.

All hardware components are fully working, I have checked CD media, tried LiveCD and InstallCD, Used different CD media, used different drives, changed partitions on drives, used different combinations of drives etc, and have put my memory through memtest86 and most importantly managed to boot into a previous installation of Fedora from a while back on the exact same hardware with no errors.

During the first boot sequence on the cd rom (I have tried server and default install modes AND have tried some of the advanced boot options) it gets to "checking if image is initramfs..." and hangs. I have also tried leaving it for longer than 10minutes, with no avail.

I am guessing it has something to do with a ram disk not being able to be initialised due to the age of the hardware I am trying to use but I have absolutely NO idea really, its all guesswork :p.

Does anyone have any suggestions?

Any help is greatly appreciated :)

---

### Post by BaLdMoNkEy on 2005-05-31
bump?

---

### Post by Sandu on 2005-07-18
[QUOTE=BaLdMoNkEy]bump?[/QUOTE]
 I have the same problem. System hags up on "checking if image is initramfs...". LiveCD also hangs up on this string. Can anyone help? Is there a hardware problem?

---

### Post by gstanley on 2008-02-24
> **Sandu said:**
> I have the same problem. System hags up on "checking if image is initramfs...". LiveCD also hangs up on this string. Can anyone help? Is there a hardware problem?

I resolved my issue by removing my attached thumb drive and the hard disk as well as live cd work perfectly. I have 2 other USB drives attached with no problems.

---

