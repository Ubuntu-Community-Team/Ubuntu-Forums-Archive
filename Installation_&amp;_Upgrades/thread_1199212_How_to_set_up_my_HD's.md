---
title: "How to set up my HD's?"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by will190780 on 2009-06-28
Hello,

I have been curious about Linux for a good 5 years and finally decided to take the plunge a few weeks ago. I accidentaly set a dual boot with Vista but have quite quickly found myself leaning more towards Ubu.

I decided to tidy up my set up and was hoping for a bit of advice. I have a 160GB ATA and a 300GB Sata. What I was planning on was splitting the 160GB into three. The primary for Ubuntu the next with Vista (Just in case) and a spare for trying out other Linux versions (I hear Mint is worth a look). This would leave my 300Gb for personal files, music etc.

Turns out this isn't quite as simple as I had hoped. I think I've managed to get Ubuntu into the first. Windows won't even look at the other partition and I can't seem to find a simple explanations as to all the different formatting options or for that matter see what is going on in the Ubuntu explorer.

Hope someone can help. I have attached a screenshot of Gparted looking at the Frankenstein HD mess I have created in case anyone takes pity on me! :-)

Thanks in advance

A confused W.Smith

---

### Post by merlinus on 2009-06-28
You cannot install windows into a logical partition, which is sdb6 in your screenshot.  It must go in a primary.  Linux does not care.

And why 50G for /boot?

I would format that one (sdb1) as ntfs, and install windows there.  You can then use sdb6 for data sharing between both oses.

---

### Post by WRDN on 2009-06-28
Windows will not recognise the partition because you may have created a logical partition, and Windows requires a primary partition.
On the other hand, you can install any Linux distro on a primary or logical partition.
I would recommend the following partition scheme:

- Partition 1 (Primary) = NTFS (for Windows)
- Partition 2 (Extended)
- Partition 3 (Swap)
- Partition 4 in Extended (Ext3 or preferred filesystem)- this is where the system files will be placed for Ubuntu
- Partition 5 in extended (Ext3 or preferred filesystem)- this is for other distro's system files
- Partition 6 (Ext3 or preferred filesystem)- this is where /home can be mounted. It is recommended to seperate /home from the / (root i.e. rest of system files) so you can reinstall Ubuntu/other distro without losing personal data/ settings

The rest of the space can be used for whatever else you want (personal files?) and can be on a primary or logical partition.

---

