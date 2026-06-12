---
title: "Windows Re install on Toshiba Satellite C55-A"
date: 2015-02-16
forum: Hardware
---

### Post by brianarmstrong210 on 2015-02-16
Trying to get Windows back on my laptop, I hope that isn't heresy here. Basically a Linux noob, I haven't been able to boot from my Windows install CD. Also tried to boot from boot-repair-disk on a USB drive to fix the problem, no luck there either. Any help would be very much appreciated!

Thanks.

---

### Post by Mark Phelps on 2015-02-16
What version of Windows is it?  Windows hasn't fit on a CD since the XP days.

---

### Post by brianarmstrong210 on 2015-02-17
Sorry, it's on a DVD. It's Windows 7. My laptop actually came with 8 but I wasn't a huge fan of it.

---

### Post by Mark Phelps on 2015-02-18
> **brianarmstrong210 said:**
> Sorry, it's on a DVD. It's Windows 7. My laptop actually came with 8 but I wasn't a huge fan of it.

You are likely facing some problems, then.  Win8 machines are typically UEFI and I don't think Win7 can be installed in UEFI -- but I don't know.

Also, unless this is a new version of an older laptop, it's likely that the manufacturer will not have Win7 drivers for it.

You should first go to the laptop manufacturer's site to see if they have Win7 drivers and if they do, download those for use during Win7 installation.

Also, you would do better going to a Windows 7 forum with Win7 issues -- recommend [www.sevenforums.com](www.sevenforums.com).

---

### Post by brianarmstrong210 on 2015-02-18
Thank you for the feedback! Well, just tried a Windows 8 install DVD, same issue. I set it to boot from the DVD drive and I get: 
                                                                                                                                                                                                             "Checking media [Failed]
                                                                                                                                                                                                              Checking media [Failed]"

Any ideas?

---

### Post by brianarmstrong210 on 2015-02-18
I feel like maybe the hard drive isn't formatted correctly after having Ubuntu installed on it, maybe?

---

### Post by oldfred on 2015-02-18
Probably drive is still gpt partitioned. 
All Windows 8 pre-installed systems are UEFI with gpt partitioning. Ubuntu can then install in UEFI or BIOS boot mode to a gpt partitioned drive.
But Windows only will boot in UEFI mode from gpt drive and only in BIOS mode from a MBR(msdos) partitioned drive. 
So partitioning of drive has to match how you plan to install, or you have to have a blank drive.
And how you boot installer UEFI or BIOS is how it installs.

It was my understanding that the Windows 7 DVD is BIOS only, but it can be copied to a flash drive and with minor updates be a UEFI installer. You must have a 64 bit version for UEFI.

---

