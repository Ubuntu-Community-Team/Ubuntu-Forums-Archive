---
title: "ATI Radeon x1600pro drivers?"
date: 2009-05-04
forum: Hardware
---

### Post by MadViper on 2009-05-04
With this upgrade to 9.04 i've lost my drivers. Is there any third party drivers out there that would work with Jaunty or should I just stop being cheap and buy a new graphics card

---

### Post by overdrank on 2009-05-04
> **MadViper said:**
> With this upgrade to 9.04 i've lost my drivers. Is there any third party drivers out there that would work with Jaunty or should I just stop being cheap and buy a new graphics card

Hi and welcome, I have seen many users having issues with ATI and Jaunty. If you had a working system before the upgrade why not stick with the previous Ubuntu? :)

---

### Post by khelben1979 on 2009-05-04
Either install the drivers using [EnvyNG]("https://wiki.ubuntu.com/EnvyNG") or go to the ATi website and download the drivers from there.

---

### Post by MadViper on 2009-05-05
Thanks to you both, i think i might just roll back to 8.10. What would be the best way to go about this?

---

### Post by khelben1979 on 2009-05-06
I found [this]("https://help.ubuntu.com/community/DowngradeHowto") Ubuntu document which describes the downgrade process.

---

### Post by mwolfgang on 2009-08-07
I tried to install the drivers using EnvyNG, and learned a lot about using the command line to recover.

In the meantime I've just switched to onboard (Nvidia) video.

Is there an RSS feed I can subscribe to or a page I can monitor that will tell me if these drivers become available?

Thanks,
Matt

---

### Post by khelben1979 on 2009-08-07
> **mwolfgang said:**
> I tried to install the drivers using EnvyNG, and learned a lot about using the command line to recover.

In the meantime I've just switched to onboard (Nvidia) video.

Is there an RSS feed I can subscribe to or a page I can monitor that will tell me if these drivers become available?

Thanks,
Matt

[nVidia developer zone]("http://developer.nvidia.com/forums/index.php") perhaps? It offers rss.

---

### Post by mwolfgang on 2009-08-07
> **khelben1979 said:**
> [nVidia developer zone]("http://developer.nvidia.com/forums/index.php") perhaps? It offers rss.
 
That would be great if the _***ATI***_ Radeon X1600 Pro was an nVidia card.

---

### Post by khelben1979 on 2009-08-08
> **mwolfgang said:**
> That would be great if the _***ATI***_ Radeon X1600 Pro was an nVidia card.

I was a bit tired when reading the post. I'm sure there must be some ATi mailing list out there somewhere.

---

### Post by Yellow Pasque on 2009-08-08
> Is there an RSS feed I can subscribe to or a page I can monitor that will tell me if these drivers become available?

ATI dropped support for X1k cards (and older) in their proprietary drivers after Catalyst 9-3. That limits your options:

1. Just use the open-source radeon driver that comes with Ubuntu
2. Use an older version of Ubuntu (8.10 or older)
3. Install an older version of X Server in Ubuntu 9.04

---

