---
title: "Can I use a floppy disk image with out a disk?"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by Infinitas on 2007-07-17
I have been having trouble with my Promise Fasttrack SX4000. I was given a workstation that had the RAID card in it. It worked fine in Windows. This workstation is now my web server and I want to get the RAID card working again. I have searched the forums and the web, and finally found a floppy disk image that supposedly has a Linux driver on it. However, I don't have a floppy drive. I was wondering if there is a way to use files on the image without a floppy drive.

Thanks for your time.

Infinitas

---

### Post by reclusivemonkey on 2007-07-19
> **Infinitas said:**
> I have been having trouble with my Promise Fasttrack SX4000. I was given a workstation that had the RAID card in it. It worked fine in Windows. This workstation is now my web server and I want to get the RAID card working again. I have searched the forums and the web, and finally found a floppy disk image that supposedly has a Linux driver on it. However, I don't have a floppy drive. I was wondering if there is a way to use files on the image without a floppy drive.

Thanks for your time.

Infinitas

Try 

```

mount /path/to/image -o loop /media/floppy

```

You may have to create /media/floppy if it doesn't exist.

---

### Post by Infinitas on 2007-08-29
Thank you for your response. That worked perfectly. However it appears the driver that I found only works for the Linux Kernel 2.4.20-8 UP/SMP.

---

