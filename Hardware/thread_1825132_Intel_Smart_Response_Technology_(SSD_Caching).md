---
title: "Intel Smart Response Technology (SSD Caching)"
date: 2011-08-14
forum: Hardware
---

### Post by brendan-nz on 2011-08-14
Does anyone have experience with ubuntu and [Intel Smart Response Technology]("http://www.hardocp.com/article/2011/05/11/intel_smart_response_technology_srt/") (SRT) that is available on the z68 chipset?  Does it work at all? Was there a significant performance improvement?  Were there any special things to be aware of?

I'm evaluating the following 3 options when upgrading my hardware:
[LIST]
[*]Using Intel SRT on a 64GB SSD (maximum size supported).
[*]Install everything except /home on 128GB SSD
[*]Using bcache with 128GB SSD
[/LIST]

---

### Post by JLGreen on 2011-08-16
I have read about the Intel SRT and it sounds awesome, I think its currently only available to Microsoft users.  I believe its mostly software based so there is no reason there couldn't be something like this for Linux users in the future.  Here is a good article that describes how it works...

[http://www.anandtech.com/show/4329/intel-z68-chipset-smart-response-technology-ssd-caching-review/2](http://www.anandtech.com/show/4329/intel-z68-chipset-smart-response-technology-ssd-caching-review/2)

---

### Post by xanderp123 on 2012-02-08
> 
Were there any special things to be aware of?


Yes - I discovered the hard way (several hours of researching and experimenting) that once you use a SSD with Intel's Smart Response Technology (SRT) the SSD will be unavailable to other operating systems. This is because you will have to use Intel's Rapid Storage Technology (RST) driver that is only available for Windows to access the drive.

I was hoping to use a single SSD for my Ubuntu root partition and the SRT cache (in a dual boot configuration) but sadly it seems this is not possible. After creating the SRT cache, the remaining space on the SSD is available to Windows only (you still have to format it).

It seems it is possible to do what I was trying to achieve with Windows (install Windows to the SSD and have a cache on the SSD to speed up access to other drives, see [http://www.tomshardware.com/forum/270288-32-cache-boot-volume-single-disk-full-success](http://www.tomshardware.com/forum/270288-32-cache-boot-volume-single-disk-full-success)) but it can't be done with Ubuntu :-(

---

