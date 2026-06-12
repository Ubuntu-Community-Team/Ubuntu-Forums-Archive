---
title: "How do I do a complete reinstall?"
date: 2008-07-22
forum: General Help
---

### Post by mczonie on 2008-07-22
I recently installed Ubuntu on my Dell Pentium, but for some reason, it's glitchy and buggy as hell. I want to do a complete reinstall and see if that fixes the problem. How do I do that?

TIA.

---

### Post by Ryadt on 2008-07-22
Just boot from the Livecd and let it guide you through the installation process.

---

### Post by WRDN on 2008-07-22
Put the LiveCD in, and click System > Administration > Partition Editor (or words to that affect). Now, delete the partition you installed Ubuntu on then close GParted.
Run the installer, and select "Use Largest Free Contiguous Space". Ubuntu will then install in the space where you deleted the partition. You could also do manual partitioning, and create a swap partition, a root (/) partition and a /home partition, so that, you can install it in the future without losing your files/ settings.

---

### Post by Elfy on 2008-07-22
Use the manual partitioner - you can reuse your old / - just edit the partition and choose a mountpoint of / the swap partition will get recognised.

You could as wrdn has pointed out make a /home - depends on how much space your installation is taking up.

---

### Post by binukavumkal on 2008-07-22
Hi,

Adding to this, the text mode installation went very well with me using Live CD. It's faster and easy. And everything installed very well.

My Machine hanged when I tried GUI mode installation.

---

### Post by jras20 on 2008-07-22
I guess I did the long way, I went into windows Vista and did the un install there, then re-installed it clean.  Mine mest up the other day.  Ubuntu is easy to install thats for sure!

---

### Post by mczonie on 2008-07-24
> **Ryadt said:**
> Just boot from the Livecd and let it guide you through the installation process.

OK, how do I boot from the CD?

---

### Post by Elfy on 2008-07-24
AS long as your pc is set to boot from cd first just put it in and start pc, should boot livecd first.

USe manual partition method and reuse old partitions

---

### Post by mczonie on 2008-07-29
> **WRDN said:**
> Put the LiveCD in, and click System > Administration > Partition Editor (or words to that affect). Now, delete the partition you installed Ubuntu on then close GParted.
Run the installer, and select "Use Largest Free Contiguous Space". Ubuntu will then install in the space where you deleted the partition. You could also do manual partitioning, and create a swap partition, a root (/) partition and a /home partition, so that, you can install it in the future without losing your files/ settings.

I went to system > administration. There's no option called "partition editor."

---

### Post by mczonie on 2008-07-29
> **forestpixie said:**
> AS long as your pc is set to boot from cd first just put it in and start pc, should boot livecd first.

USe manual partition method and reuse old partitions

I just restarted the computer with the CD in the drive. It didn't work.

---

