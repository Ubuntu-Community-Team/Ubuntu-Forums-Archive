---
title: "Ubuntu did not ask where to write boot record"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by Piscium on 2009-08-11
A few weeks ago I installed Kubuntu on my second hard disk. I have been playing with it since. Today I reformatted the Kubuntu partition on the second hard disk and installed Ubuntu. 

I was expecting that Ubuntu installation would be just the same as Kubuntu’s, and it was, but with one difference: during the Kubuntu installation process I had the possibility of choosing where to write the boot record. No such luck with Ubuntu. The result is that the boot record on my *first* drive was written to, which is what I did not want, because on my first drive I have Windows and wanted to leave it alone.

My question is: why does Ubuntu installation differ from Kubuntu on this detail, which for me is important?

Any ideas? If I want to have control of where the boot record is written can I use the alternate CD?

Thanks,
António

---

### Post by doas777 on 2009-08-11
> **Piscium said:**
> A few weeks ago I installed Kubuntu on my second hard disk. I have been playing with it since. Today I reformatted the Kubuntu partition on the second hard disk and installed Ubuntu. 

I was expecting that Ubuntu installation would be just the same as Kubuntu’s, and it was, but with one difference: during the Kubuntu installation process I had the possibility of choosing where to write the boot record. No such luck with Ubuntu. The result is that the boot record on my *first* drive was written to, which is what I did not want, because on my first drive I have Windows and wanted to leave it alone.

My question is: why does Ubuntu installation differ from Kubuntu on this detail, which for me is important?

Any ideas? If I want to have control of where the boot record is written can I use the alternate CD?

Thanks,
António

on the last page of the install dialog, click the Advanced button, and select your MBR disk fromt he dropdown

---

### Post by Piscium on 2009-08-11
> **doas777 said:**
> on the last page of the install dialog, click the Advanced button, and select your MBR disk fromt he dropdown

Yes, you are right, the button was there but I missed it.

In fairness, that button is easy to miss in its present location. It would not be a bad idea to make it more prominent, perhaps moving it to the left side of the screen (for left to right languages).

In any case, I have fixed the boot record with the Windows command fixmbr, so all is well.

Thanks,
António

---

