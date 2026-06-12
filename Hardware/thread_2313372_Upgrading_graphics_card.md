---
title: "Upgrading graphics card"
date: 2016-02-11
forum: Hardware
---

### Post by Edward_Diener on 2016-02-11
I am planning on upgrading my graphics card for an existing installation. The upgrade will retain the card type, AMD Radeon, but will upgrade from a no longer supported HD series to a supported one. Will Ubuntu 15.04 automatically pick up the new graphics card in an existing system, or do I have to re-install the OS again ?

---

### Post by monkeybrain20122 on 2016-02-11
As long as the new card is supported and you are not using a proprietary driver it should work automatically. if you are using a proprietary driver you may have to reinstall the driver.

---

### Post by deadflowr on 2016-02-11
It'll see it and use it, if the BIOS is set to see the card.
No re-install needed, at all.
All the better if you were only using the open-source drivers to begin with.

**If you had been using the close-source drivers, you might have wanted to remove those first.
(And also remove any xorg.conf files you may have made for the closed-source card.)

---

### Post by Bucky Ball on 2016-02-11
> **deadflowr said:**
> 
All the better if you were only using the open-source drivers to begin with.



And better still if you were using a supported release. 15.04 is EOL (end-of-life). Upgrade to a supported release, 15.10 is probably your best option from here, especially if you are going to install very recently released hardware.

Upgrade now and avoid what will possibly become a steadily growing list of issues in future as your EOL release becomes more obsolete.

---

### Post by P-I H on 2016-02-12
There are some articles on the Phoronix site about Radeon graphic cards. This is an example
[http://www.phoronix.com/scan.php?page=article&item=linux-45-amdgpurad&num=2](http://www.phoronix.com/scan.php?page=article&item=linux-45-amdgpurad&num=2)

I am using a Radeon R9 380 on Ubuntu 15.10 with the fglrx driver, installed by use of the Ubuntu installation method **System settings/ Software & Updates/ Additional Drivers**.

On the same computer with the development version of Ubuntu 16.04, I'm using the open driver. To get the best performance, you have to do some work and install a Linux 4.5 kernel with support of AMDGPU.
Both installations are working OK.

---

### Post by Yellow Pasque on 2016-02-12
See this table if you don't know what core/architecture your GPU is based on: [https://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units](https://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units)
The answer to your question depends on exactly which graphics card you're putting in. If you're putting in a card with a Tonga/Antigua or Fiji/Fury core (i.e. a GCN 1.2 - based card), the open source driver isn't going to work out of the box on Ubuntu 15.04. It may work on 15.10, but the performance isn't going to be great because you'll need a patched kernel (or a 4.5-rc kernel) to support Powerplay/reclocking.

If you're using a card based on GCN 1.1 or older, it should be okay using the open source driver without modification, although as others have noted, using an EOL release is not good. Later versions should bring better performance and fix bugs. 

If you really hate upgrading Ubuntu versions and you have a GCN 1.2 card, it's my opinion that you'd actually be better off doing a fresh install of 16.04 LTS even though it's still prerelease (I know someone will jump in and say prereleases are unstable/bad, but Ubuntu 16.04 is getting closer to release, and I think it's best for people with really new hardware that don't like distro upgrading every 9 months).

---

### Post by Edward_Diener on 2016-02-23
Everything worked without problems with my upgraded graphics adapter. I am using the stock Ubuntu AMD driver rather than a proprietary AMD driver. Thanks for everyone's suggestions.

---

### Post by Bucky Ball on 2016-02-23
Great news. If you're happy, please see the first link in my signature and mark thread as solved to help others.

Good luck with it. ;)

---

