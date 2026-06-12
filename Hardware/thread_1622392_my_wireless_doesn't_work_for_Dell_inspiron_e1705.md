---
title: "my wireless doesn't work for Dell inspiron e1705"
date: 2010-11-15
forum: Hardware
---

### Post by Mock Force on 2010-11-15
Hey there,

I'm new this community and very new to linux and Ubuntu in particular. This is actually my first post ever, So advice on better formatting my queries would be appreciated.

My problem is that my wireless interface for on my Inspiron e1705 is not working on the Ubuntu Partition I have. I'm dual booting with Windows and Ubuntu ver. 8.04.01 with kernel 2.6.22.19. So I know it's not a hardware problem because the wireless works fine with the Windows partition.

My wireless network controller is Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I can't see any wireless networks and under network settings there is no connection showing that I even have a wireless connection option.

So far I've been tentative to try most solutions I've found on the forums because they don't address my computer model and some of them don't address the version of Ubuntu I'm running.

Thanks for your help,

---

### Post by Enigmapond on 2010-11-15
With Dell Inspiron...and I have one too, you have to enable the Broadcom proprietary driver...with a wired connection, go to System/Administration/Hardware Drivers (or additional drivers) and enable this. Also make sure that the wireless is enabled after doing this. Also if you are new to Linux, why did you install 8.04? The end of life for this distro is in April...just curious.

---

### Post by Mock Force on 2010-11-15
there is no proprietary driver in the location that you've described, there are only two boxes unchecked to be enabled.

Framebuffer driver for Intel(R) 830M/845G/825GM/855GM/.../945GM chipsets
I801 SMBus driver

is one of these what you're refering to?

> **Enigmapond said:**
> Also if you are new to Linux, why did you install 8.04? The end of life for this distro is in April...just curious.

I installed 8.04 because it's required for the research I'm doing, I actually initially installed 10.something but then had to downgrade. 8.04 works fine as far as I can tell, except for the whole wireless connection problem I'm having.

---

