---
title: "Asking for advice on purchasing a HD for data storage only"
date: 2017-05-20
forum: Hardware
---

### Post by satimis on 2017-05-20
Hi all,

I'm prepared to purchase a 1T or 2T WD HD, mainly for data storage.  The data may be used once in 2/3 month or in one year or never be used again.

My daily working PC config:

AMD 8-cores
RAM 32G onboard
HD SSD 1TB
OS Ubuntu

In this box I already have a WD Black label 1.2TB HD for storage (old HD having been used for >7 years, IIRC).  They are nearly full.  In front of me there are WD Red/Blue/Purple/Gold/Black label for selection.  I have no pre-set budget.  What I don't expect is to purchase a 10tons track to carry one ton cargo.

Thanks in advance for your suggestion.

Regards
satimis

---

### Post by Tadaen_Sylvermane on 2017-05-20
If you have the money, and space in the case get a pair of 2tb drives. Install snapraid and use one of the 2tb as a parity drive. This will give you a modest "semi backup" of both drives. You can pool them with mhddfs if you want them under a single mount point. That's what I'm working on setting up for my media server. Seems almost bulletproof for data that rarely changes. Another option is lvm to pool them but I don't like that losing one drive means all data in the lvm is gone. (unless i misunderstand how lvm works)

---

### Post by LastDino on 2017-05-20
> **Tadaen_Sylvermane said:**
> If you have the money, and space in the case get a pair of 2tb drives. Install snapraid and use one of the 2tb as a parity drive. This will give you a modest "semi backup" of both drives. You can pool them with mhddfs if you want them under a single mount point. That's what I'm working on setting up for my media server. Seems almost bulletproof for data that rarely changes. Another option is lvm to pool them but I don't like that losing one drive means all data in the lvm is gone. (unless i misunderstand how lvm works)

+ 1
or

Imo 1TB WD passports are fairly cheap and portable too. I have one for backup purpose, like you use it ones in a month to take full backups.

---

### Post by satimis on 2017-05-20
> **LastDino said:**
> + 1
or

Imo 1TB WD passports are fairly cheap and portable too. I have one for backup purpose, like you use it ones in a month to take full backups.
Hi,

The price of

WD Red NAS Hard Drive WD20EFRX 2TB SATA3
vs
WD Red NAS Hard Drive WD10EFRX 1TB SATA3
very small difference

WD Red NAS Hard Drive WD20EFRX 2TB SATA3
vs
WD Blue WD10EZEX 1TB SATA3 6Gb/s /64MB HDD
or
WD Purple WD10PURX 1TB SATA3
almost half price

Regards
satimis

---

### Post by satimis on 2017-05-20
> **Tadaen_Sylvermane said:**
> If you have the money, and space in the case get a pair of 2tb drives. Install snapraid and use one of the 2tb as a parity drive. This will give you a modest "semi backup" of both drives. You can pool them with mhddfs if you want them under a single mount point. That's what I'm working on setting up for my media server. Seems almost bulletproof for data that rarely changes. Another option is lvm to pool them but I don't like that losing one drive means all data in the lvm is gone. (unless i misunderstand how lvm works)
Hi,

Thanks for your advice.

Sorry I don't have space in this box.

Actually I'm considering to build a new box and waiting for 16-core Ryzen in the market.  I have a spare PC with following config:
AMD 8-core
RAM 8G onboard
OS 120G SSD
Storage 1.5T WD Black label HD

The new PC to be built, config;
AMD 16-core Ryzen
RAM 64G onboard
SSD 2TB
Storage - I'll use the old 1.5T WD Black label HD from the spare PC

Maybe I'll waiting because there is no urgency

Regards
satimis

---

### Post by gsahli on 2017-05-20
I treat Hard Drives (rotating) as "commodities" - I buy the best deal I can find that meets my specs - for example, these days I only buy USB 3 externals - otherwise any brand.

---

