---
title: "[SOLVED] Adding Partitions"
date: 2009-01-07
forum: Hardware
---

### Post by vancedus on 2009-01-07
Hi,

I recently removed Windows XP from my hard drive partition in hope of installing it to an external drive (which I found was not possible). Now I need to create a new NTFS partition for Windows.  However, when I try to resize my Ubuntu partition, from right to left, from a live boot I receive an error.  Is there something else that needs to be done? I have included a screen shot of my Gparted.  Thank you.

---

### Post by Elfy on 2009-01-07
If you're trying to make a primary partition - which I recommend, then you need to resize sda5 before you can resize the extended partition. Then you should be able to create a primary.

I would also - resize from the left so that any primary you do make is at the beginning - I've needed to do so in the past.

---

### Post by -kg- on 2009-01-07
> **vancedus said:**
> Hi,

I recently removed Windows XP from my hard drive partition in hope of installing it to an external drive (which I found was not possible). Now I need to create a new NTFS partition for Windows.  However, when I try to resize my Ubuntu partition, from right to left, from a live boot I receive an error.  Is there something else that needs to be done? I have included a screen shot of my Gparted.  Thank you.

Yes.  Seeing your screenshot, I have to assume that you're trying to do it from the Ubuntu installation on your disk.  In order to do any partitioning operations on a partition, it must be unmounted.  If you are doing it from your installation, you cannot unmount your /root partition, since that is the partition which you are operating from.

You will need to boot from your Ubuntu Live CD or a [GPartEd Live CD]("http://gparted.sourceforge.net/livecd.php") and launch GPartEd and do the operations from there, making sure that the partition you are trying to resize is unmounted.

For more information on partitioning see ["How To Partition"]("https://help.ubuntu.com/community/HowtoPartition") from the Community Documentation.

---

### Post by 2hot6ft2 on 2009-01-07
There are actually 3 partitions there sda5 and sda6 are inside sda2 so you have to resize sda5 before you can resize sda2. AND you can't do it from right to left unless after resizing sda5 you move sda6 to the left, then you can resize sda2 to the left.

---

### Post by vancedus on 2009-01-07
Thanks for the help,  It would not resize from the left either and the Gpared error message told me to run a command and this seemed to fix the problem.  the partition is now resizing.  Thanks

---

