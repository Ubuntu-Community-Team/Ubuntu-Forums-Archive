---
title: "[SOLVED] Second Hard Drive question"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by JawsThemeSwimming428 on 2007-07-25
I am currently running Feisty on a machine I built about a year or two ago. It only has a 40GB SATA HDD and I am running out of space for storage. I found a Seagate Barracuda 7200.9 160GB 8MB SATA II/3Gb NCQ on Provantage for $52.96([http://www.provantage.com/seagate-st3160811as~7SEGB02F.htm](http://www.provantage.com/seagate-st3160811as~7SEGB02F.htm)). If I purchase this drive, how do I format it so that it will be seen as another drive in Feisty? What do I need to do?

---

### Post by Depressed Man on 2007-07-25
You can format it as ext3, or if you want Windows to use it too you can format it as NTFS and get the NTFS-3g driver so Linux can read and write to it.

---

### Post by JawsThemeSwimming428 on 2007-07-26
How do I do that? I am new sorry.

---

### Post by logos34 on 2007-07-26
The easiest way is to use gnome partition editor

**sudo gparted**

---

### Post by JawsThemeSwimming428 on 2007-07-26
So when I buy this drive and install it, I go into gparted and it will see the new drive?

---

### Post by LaRoza on 2007-07-26
> **JawsThemeSwimming428 said:**
> So when I buy this drive and install it, I go into gparted and it will see the new drive?

Yes. Or you can use the GParted Live Cd, in my sig.

---

