---
title: "what hardware should i generally avoid if i'm getting a computer to run linux?"
date: 2023-05-18
forum: Hardware
---

### Post by m3ideh on 2023-05-18
Wanting to build a pc or get a laptop solely to run ubuntu on, but not sure what kinds of compenents/ brands of hardware to avoid that are known for having compatibility issues

i've heard Nvidia generally has less support and laptops with a dedicated+standard gpu may have issues?

---

### Post by TheFu on 2023-05-18
This question is asking for opinions.  Almost any computer can work with Linux, eventually.  Stick with the major, known, parts manufacturers and use versions of their stuff that are 1+ yrs old. Avoid the bleeding edge stuff.

For laptops, Lenovo and Dell seem to have the best Linux support, assuming you don't get something "odd". I've had Dell, Toshiba, Acer, HP, Asus laptops running Linux.  They all worked and if not all of the hardware worked, it was something like the fingerprint reader that didn't.  Some just needed a little custom help, unfortunately, that custom help is often needed just after install for the first non-install boot just to get the system booting.  On the Toshiba, seems the UEFI BIOS at the time didn't follow the standards.  I understand that HP has this issue still.  After fixing the issue once, whenever boot files related to UEFI booting were modified, I'd have to manually make the fix again ... btw, the fix isn't hard, just a hassle.  It was copying a shim file from 1 directory into another inside the UEFI partition.  With that laptop, I always brought an install ISO on a cheap 8GB USB thumb drive to address boot issues. Not a big deal and I had more problems with ChromeOS updates (they are forced) than I had with the Toshiba booting.  The boot error wasn't really clear, but a quick search found the issue.  Just something to be aware.

I suspect with dual boot systems, there will be more problems and more complexities with those issues. I stopped dual booting about 15 yrs ago, preferring to run other OSes as virtual machines instead.

When building a desktop, certain well-known motherboard vendors are linux-hostile, but even those motherboards can work.  Watch out for odd, non-standard, network and audio devices.  Stick with boring, known, brands and models to avoid the most issues.

If you are considering printers/scanners, get those from the "openprinting" and "openscanning" websites.  Effectively they use **driverless** printing/scanning, so the OS doesn't matter.  Searching for "driverless" is a good idea.  My next scanner will work without any computer connected.  It will scan to a USB flash drive or SDHC card to avoid dumb OS problems.  That will work with my scanning workflows.  I completely understand that others may need computer controlled scanning.

Of course, we all have our specific vendors that we like or dislike based on our experiences.  I prefer Asus motherboards with Intel NICs (not realtek). Be certain to read the motherboard manual BEFORE buying, to see if there are any odd configuration limitations.  

For example, some motherboards have 2 m.2 slots which can be used as NVMe or SATA storage.  However, if the 2nd m.2 slot is set to be used for SATA m.2 SSD storage, then 2 of the standard SATA ports on the motherboard become unavailable.  Also, if both m.2 slots are set to NVMe, then they both lose performance, since the bus bandwidth has to be shared.  1 NVMe storage device can't full the bus, so that isn't an issue, but with 2 NVMe, the bus can be flooded just with storage data.  This can impact the x16 GPU bandwidth and effectively drop an x16 PCIe GPU to x8.  

Gotchas.  Gotta read the motherboard manual.  Of course, the box and advertising imply that all these slots and devices can be used concurrently at the highest possible speeds, but reality is different from the advertising.

---

### Post by mIk3_08 on 2023-05-19
> **m3ideh said:**
> i've heard Nvidia generally has less support and laptops with a dedicated+standard gpu may have issues?
Yes. I agree as I heard it before that Linus Torvalds the lead developer of the Linux kernel said "<expletive deleted> Nvidia". Not too bad but its just that, it really happen due to Nvidia personal intentions.
And I totally support Linus Torvalds decisions about this. Regards and cheers.

---

### Post by ian-weisser on 2023-05-19
Depends upon your budget and needs.

The only universal advice is to:

1) Avoid bleeding edge hardware. Hardware released 6 months to one year before an Ubuntu release should be safe to use with that release. Newer hardware might not be in the kernel yet.
2) Purchase from a vendor with a generous return policy. It's worthwhile.
3) Upon receipt: Test, test, test. Slap that LiveUSB in there and find a way to test ALL the hardware before installing. Stream movies, play games, load it up...in the "Try Ubuntu" environment. Make sure all hardware is compatible and you don't need to return it before you touch the hard drive.

---

### Post by yorakal on 2023-05-24
There are some Linux laptops vendors out there like kfocus who ship with kubuntu and are designed for compatibility with ubuntu even with Nvidia GPU's present.

But as a general rule Intel/AMD are the safe option.

---

### Post by mIk3_08 on 2023-05-24
I prefer AMD than Intel. AMD are the closes friend of Linux.

---

### Post by Tadaen_Sylvermane on 2023-05-26
> **m3ideh said:**
> i've heard Nvidia generally has less support

This is only true if one tries to be an open and free software purist. The closed drivers are very good. Closed being the operative word.

---

