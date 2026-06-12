---
title: "Acer Aspire 5 (Ryzen) not Booting After Update"
date: 2020-03-05
forum: Hardware
---

### Post by linuxguy2 on 2020-03-05
I'm trying to set up an Acer laptop for my mom.
It's an Acer Aspire 5 (Model # A515-43-R19L), with an AMD Ryzen 3 3200u CPU.

I had it running Xubuntu 19.10 just fine and she was very happy with it- until I updated the system. Since then it hasn't been able to boot up properly. So I tried Xubuntu 18.04 LTS and this worked just wonderfully- until I updated the system. Then I got the same kind of error. Here is a picture of a typical error:

[ATTACH=CONFIG]285155[/ATTACH]

I've transcribed it below:

> [ 0.933356] pci 0000:00:00.2: AMD-Vi: Unable to write to IOMMU perf counter.
/dev/nvme0n1p2 contains a file system with errors, check forced.
Inode 4325409 seems to contain garbage.

/dev/nvme0n1p2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
 (i.e., without -a or -p options)
fsck excited with status code 4
The root filesystem on /dev/nvme0n1p2 requires a manual fsck

BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3.2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

The system is UEFI only. I have turned off Fast boot and Secure boot. SATA is in AHCI mode.

I hope someone can help me figure out what is going on here. As always, I'm trying to sell Linux, especially Ubuntu, but its hard to when it can't even boot.

---

### Post by linuxguy2 on 2020-03-05
I've verified that the updates that cause the issues are specifically the Security Updates.

Strangely, now I am getting a loop saying :
"(1 of 1) A start job is running for Hold until boot process finishes off.
(2 of 2) A start job is running for Detect the available GPUs and deal with any system changes."

Then it complains about a soft lockup for CPU #2.

---

### Post by CelticWarrior on 2020-03-05
Updates do not cause "*a file system with errors*". You need to follow the instructions: *root filesystem on /dev/nvme0n1p2 requires a manual fsck*

---

### Post by linuxguy2 on 2020-03-06
> **CelticWarrior said:**
> Updates do not cause "*a file system with errors*". You need to follow the instructions: *root filesystem on /dev/nvme0n1p2 requires a manual fsck*

Apparently this one does, whether directly or indirectly- as this only happens after an update.

If I install either 18.04 or 19.10 without updates, I can use the system and applications, shutdown and restart the system many, many times (and one might conclude indefinitely) without any apparent errors or file system corruption at any point, per my testing. As soon as I install updates on either system, however, this starts to happen.

---

### Post by linuxguy2 on 2020-03-06
I ran fsck, which said the system was "clean". I restarted and again I have the system unable to boot and telling me that all CPU cores are in "soft lockup".

---

### Post by oldfred on 2020-03-22
Have you updated UEFI from Acer?
And if SSD updated firmware?

---

