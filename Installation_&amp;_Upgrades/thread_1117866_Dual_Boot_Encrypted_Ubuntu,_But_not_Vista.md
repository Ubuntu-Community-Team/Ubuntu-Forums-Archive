---
title: "Dual Boot: Encrypted Ubuntu, But not Vista?"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by Krovas on 2009-04-06
I realize there are a plethora of tutorials out there on the subject of encrypted dual-booting, but none I have come across deal with my needs precisely. Most assume the user wishes Windows to be encrypted (I do not), and do not adequately cover disk-partitioning within an encrypted volume. Here's a quick synopsis of the partitioning scheme I want:

Windows Vista C: (~60gb, NTFS, Not-Encrypted), /boot(~300mb), [ENCRYPTED VOLUME: {/(~10gb), Swap(1.5gb), /home(whatever's left)}]

 I have a 160 gb drive, the first ~60gb or so to be used with Windows Vista, which is not to be encrypted in any way...I need to have it, but not for anything particularly interesting. /boot will follow from what I gather, and needs to be plaintext...no problem. After that, I want everything encrypted (and, presumably, virtual), beginning with / @ ~10gb, followed by 1.5 gb of swap space, with remainder allocated to /home.


Can this be accomplished, and if so, how? If you have questions, please ask away.

P.S: I should also note that I will be using 8.04(x64), and it is completely necessary that I do so.

---

### Post by miklcct on 2009-04-08
You can create non-encrypted Vista partition, /boot partition and /home partition, and an encrypted LVM containing only the / partition.

---

