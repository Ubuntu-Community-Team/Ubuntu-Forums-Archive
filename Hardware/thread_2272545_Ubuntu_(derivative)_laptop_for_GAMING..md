---
title: "Ubuntu (derivative) laptop for GAMING."
date: 2015-04-07
forum: Hardware
---

### Post by adam136 on 2015-04-07
All,

My current laptop has finally died on me. So time to go for a new one...

The last laptop I had was Windows 7. I had previously installed various Linux editions on it but had to return to windows to run World of Warcraft at an acceptable framerate. Drivers were just much better, not to mention there is no official port of WoW onto Debian systems and I had to hack it together using PoL.

Anyway - now that it's dead I'll be buying a replacement and going 100% Linux.

Here's a nice one: [http://www.pcspecialist.co.uk/notebooks/defiance-15/](http://www.pcspecialist.co.uk/notebooks/defiance-15/)

I'll be upgrading the standard GPU to to the 2nd option in the dropdown: GTX 970M plus a few other things like extra RAM and I have a 1Tb WD SSHD lying around "spare" now my old laptop is dead - so I'll use that as the main partition.

Iv scanned through the compatible laptop list and couldnt see any mention of the one specified there. 

So my question is do more experienced eyes see anything there that is incompatible - or known to cause issues? Im also considering upgrading the WiFi to the highest spec available in the dropdown. Id really like dual channel but that doesnt seem available. Im specifically asking about that as Iv had nightmares with wlan0 in the past.

The distro I'll be using is LXLE 64 bit: [http://www.lxle.net/](http://www.lxle.net/)

Ignore all that "Ageing PC" nonsense. It's just optimized the way I like it, and it is Ubuntu. There are a whole load of VM's in our company using that OS now... everyone seems to like the Unity free experience.


Anyway - if someone with more "non server" / recreational knowledge of 14.04 and modern hardware could cast their eye over it Id appreciate it. 

Issues with Nvidea drivers ... things like that... Id like to know about before spending the money. I never want to go the MS route again so it's important to get it right.


Thanks in advance.

---

### Post by efflandt on 2015-04-07
Nothing jumps out at me as being incompatible. With hybrid Intel/Nvidia graphics I heard that you should NOT use nomodeset boot parameter (nomodeset might typically be used during install for a desktop with only Nvidia). And not using any boot parameters worked for my laptop with hybrid Intel HD 4600/Nvidia GTX 765m. Although, that laptop had Win7 that defaulted to legacy BIOS (instead of UEFI) and msdos partitions, so I am not up on exactly what is required cooperate with Windows Secure Boot and UEFI. On that laptop I installed 64-bit 14.04.1 on 512 GB mSATA SSD for use with Linux Steam games when traveling. For some SSD optimizations (TRIM, etc.) see [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

You could try **nvidia-331-updates** for video drivers, but if you want/need something newer like **nvidia-346** or **nvidia-349** packages you can add the xorg-edgers ppa. Note that X did not work with default nouveau driver or nvidia-current package on my desktop that has GTX 750 Ti with that new Maxwell chip. But nvidia-331-updates worked and I am now using nvidia-349 package.

---

