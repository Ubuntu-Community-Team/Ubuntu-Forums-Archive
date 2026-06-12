---
title: "Seagate FreeAgent Desk external HD not recognized"
date: 2009-03-22
forum: Hardware
---

### Post by Buzzygirl on 2009-03-22
Hi there.

I'm running Hardy 8.04 and just purchased a Seagate FreeAgent Desk external hard drive, 500 GB. My computer will not recognize it at all. I ran sudo fdisk -l and the device is not detected at all; the only disk seen is my main sda internal disk.

I tried several different USB ports, and the external HD is still not detected.

I would try to mount the drive manually, but I'm not sure what to do next if the drive isn't even showing up. Hmm... I just checked a few other threads here and it seems that Seagate's drives have had some issues with Ubuntu. I can always return it to where I bought it, but I'd like to get it working if I can.

Any help is appreciated. Thanks.

---

### Post by ddrichardson on 2009-03-23
> **Buzzygirl said:**
> Hi there.

I'm running Hardy 8.04 and just purchased a Seagate FreeAgent Desk external hard drive, 500 GB. My computer will not recognize it at all. I ran sudo fdisk -l and the device is not detected at all; the only disk seen is my main sda internal disk.

I tried several different USB ports, and the external HD is still not detected.

I would try to mount the drive manually, but I'm not sure what to do next if the drive isn't even showing up. Hmm... I just checked a few other threads here and it seems that Seagate's drives have had some issues with Ubuntu. I can always return it to where I bought it, but I'd like to get it working if I can.

Any help is appreciated. Thanks.
What's the output of```
dmesg
```After you plug it in?

---

### Post by Buzzygirl on 2009-03-23
> **ddrichardson said:**
> What's the output of```
dmesg
```After you plug it in?

Hello,

I ended up returning the drive to the place I bought it. I thought I should test it on my two spare Windows computers, but the drive was recognized by neither of *them*, so the store took it back; most likely it was a defective product. 

Thanks for your reply though. Cheers.

---

