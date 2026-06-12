---
title: "Rezise HFS+ partition on GPT partition table"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by emil.s on 2007-04-17
Hi!
I have Ubuntu installed on my Macbook Pro. I have triple boot with OS X, Ubuntu and Win XP.
No problem so far..

But now i need more space on my Windows partition!

The disk have 4 partitions.
P1 = EFI partition!? ~200 MiB, I don't know what it's used for
P2 = OS X, HFS+, ~70GiB
P3 = Ubuntu, ReiserFS, ~18GiB
P4 = Windows, NTFS, ~22GiB

Now i want to "take" ~6-7GiB from P2 to P4.
I have rezised NTFS, ReiserFS and Ext2/3 partitions before, but never on a disk with a GPT partition table.
And can parted, (gparted) rezise HFS file systems?

I can remove P3 if it make it easier. I will reinstall Ubuntu when Feisty is released anyway.

Can it be any problem whit this?
I will preferably not reinstall the complete system... ;-)

---

