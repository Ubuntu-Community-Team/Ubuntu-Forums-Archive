---
title: "Ubuntu 22.04 work on NUC13?"
date: 2023-06-29
forum: Hardware
---

### Post by naoqmon on 2023-06-29
Hello!

I would like to make Ubutnu22.04 work on Intel NUC 13 pro.
Are there any OS and hardware compatibility issues?

thanks.

---

### Post by oldfred on 2023-06-29
Historically users with NUC seem to have more issues than other systems.

Make sure UEFI firmware and if SSD it firmware is up to date.

Download latest Ubuntu live installer and test it. Normally I suggest latest LTS, but since very new system you need latest version to have updated kernel & drivers. And you may need even newer than default 23.04. You can experiment with 23.10, but it still is in development and will have many changes until released in Oct.

This user seemed to have issues.
[https://ubuntuforums.org/showthread.php?t=2486197](https://ubuntuforums.org/showthread.php?t=2486197)

---

### Post by guiverc on 2023-06-30
I'll add little sorry.

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)

That tutorial is geared at Ubuntu Desktop, but applies to all *live* systems including all *flavors* of Ubuntu* (excluding Ubuntu Core I believe*[I]; so desktop flavors anyway). 

[/I]Ubuntu 23.04 is available with the 6.2 kernel, Ubuntu *mantic* (23.10) has the 6.3 kernel, and Ubuntu 22.04 LTS is available with either 5.15 (GA) or 5.19 (HWE) kernel stacks by selecting the ISO/media used (*Lubuntu 22.04 & 22.04.1 media has the 5.15, 22.04.2 & later media uses the HWE kernel stack*)

Whilst the 6.2 kernel (`6.2.0.23.23~22.04.4` in *proposed*) is available for download/install, no ISO/media exists with it yet to try if you have issues with the older stacks (ie. 5.15 or 5.19). But ISO/media exists using the 5.15 & 5.19 kernel stacks, with 6.2 progressing forward (*but can be tested via 23.04 media currently*) thus you could test rather well using on *live* systems.  Use *mantic* media to test the 6.3 kernel.

---

### Post by naoqmon on 2023-06-30
I apologize for my lack of understanding.
I am going to use 22.04 LTS instead of Ubuntu 23.xx.
Should I ask Canonical?

thanks.

---

### Post by guiverc on 2023-06-30
> **naoqmon said:**
> I apologize for my lack of understanding.
I am going to use 22.04 LTS instead of Ubuntu 23.xx.
Should I ask Canonical?

thanks.

Lubuntu 22.04 has released various media currently (*your question was placed in the official flavors section of this forum, specifically Lubuntu*) which includes

- [Lubuntu 22.04 LTS]("https://lubuntu.me/jammy-released/")
- [Lubuntu 22.04.1 LTS]("https://lubuntu.me/jammy-1-released/")
- [Lubuntu 22.04.2 LTS]("https://lubuntu.me/jammy-2-released/")

with 22.04 & 22.04.1 installing with a different kernel stack as default (ie. 5.15) than later media such as Lubuntu 22.04.2.  If you have newer hardware, you'll generally do better with the newer HWE stack found on the .2 media (ie. 5.19 kernel).

The different kernel stack choices allow you to use a different set of kernel modules (*commonly called drivers*), thus my comment was an attempt to point you to ISOs that allow you to test *four* stacks on your device without installing anything (ie. 5.15, 5.19, 6.2 & 6.3)... ie. letting you test it on your device without changing anything on your actual device.

The testing being just various ISOs downloaded, then written/burnt to USB thumb-drive, then booted & tried on your device giving you 

- 22.04 using the GA kernel stack 5.15 available now
- 22.04 using the HWE kernels tack as it stands currently (5.19), another option that is available now
- [I]what the next 22.04.3 media will possibly look like; testing via 23.04 (6.2)
- [/I][I]the mantic ISO just gives you another 'newer' stack to try which maybe better for newer hardware, alas its not available for 22.04 & likely won't ever be supported there (22.04.4 will likely have 6.4 or 6.5)

ie. I was providing information useful with 22.04; attempting to give you ways to test a 22.04 easily, without any install to your actual device; thus no changes

[/I]Canonical support Ubuntu, with Lubuntu being a *community* supported *flavor*. If you want to use paid Canonical support though you can try, but I'm not sure you'll gain more (*though maybe they'll word it more easily than I do*)

FYI:  The various kernels I mention are also available for Ubuntu's main products, though I've kept details specific to Lubuntu media your initial question *flagged*, with Ubuntu 22.04 Desktop  for example defaulting to HWE, and Ubuntu 22.04 Server media defaulting to GA kernel stack..

---

### Post by tea for one on 2023-06-30
> **naoqmon said:**
> 
I would like to make Ubutnu22.04 work on Intel NUC 13 pro.
More info here [https://www.intel.co.uk/content/www/uk/en/support/articles/000005628/intel-nuc.html](https://www.intel.co.uk/content/www/uk/en/support/articles/000005628/intel-nuc.html)

---

### Post by naoqmon on 2023-07-04
Thank you very much.
I see that different versions of Ubuntu have different kernel types.
I couldn't open the tutorial URL so I wasn't sure.

---

### Post by naoqmon on 2023-07-04
Thanks.

This page is very helpful.

---

