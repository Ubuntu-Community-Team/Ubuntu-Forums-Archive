---
title: "Making a hardware RAID 5 server"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by filburt1 on 2007-12-05
My current home server is a cheap Dell refurbished desktop running Xubuntu 7.10. It's mainly used as a file server. For physical space and power capacity reasons, I can't add more hard drives to it without rebuilding the entire system...which is my plan: I'm considering building a new server using RAID 5. It would have three 500 GB SATA hard drives. That means it starts with a 1 TB capacity, and in the future, I could add a fourth 500 GB drive to give it 1.5 TB.

However, every motherboard I've found has "fake" RAID support (offloading processing to the CPU, and more importantly, requiring software to function). So:
[list]
[*]Are there any *motherboards*--not just controller cards--out there that support *hardware* RAID 5 with SATA?
[*]If not, does anybody have recommendations for a SATA controller that supports RAID 5 with up to four devices, and that is known to function properly with Ubuntu 7.10?
[/list]
I've been building the system at Newegg, and I can't rely on all the reviews to determine if a controller is truly supported on Ubuntu or not, or if it's real hardware RAID and not fake RAID. My objective is to come up with a setup such that Ubuntu just sees a giant 1/1.5 TB drive without any extra software overhead.

Thanks for any help.

---

### Post by Yellow Pasque on 2007-12-06
Even the cheaper hardware controllers offload their calculations. It would probably be cheaper to get a fast CPU and use linux software RAID. This has the added advantage of making your array portable between mobo chipsets.

---

### Post by filburt1 on 2007-12-06
If I go with the RAID support provided by the motherboard (an nVidia chipset for this particular motherboard I'm looking at), will I be able to install Ubuntu itself and have it boot off the RAID array? I've read posts from other users that the software RAID can work just fine, except when it comes to trying to boot off the array itself.

If I can only install it to a single drive and instead mount the array somewhere else in the filesystem, that's fine because I can cannibalize my eventually-to-be-old server and install Ubuntu to its current 80 GB IDE system drive. However, I'm not sure whether or not it would actually run faster off the array: RAID 5 can be fast, but the CPU overhead might negate that.

The processor I'm looking at is an [AMD Athlon 64 X2 4000+](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103774) (2.1 GHz dual-core). I'm thinking that should be fast enough to run the array and give decent system performance; I won't exactly be gaming on this thing.

---

