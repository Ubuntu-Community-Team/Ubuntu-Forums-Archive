---
title: "Is the 96.43.11 Nvidia driver available in Intrepid 8.10?"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by montysan on 2009-02-28
After a lot of trawling, I think I need the 96.43.11 driver to make my Quadro2 MXR (NV11GL) work in Intrepid. My question is, is this version available automatically yet, as I don't fancy the manual install route.

If it is, does anyone have any experience with this card and driver combo?

---

### Post by montysan on 2009-02-28
bump

---

### Post by 4Orbs on 2009-02-28
The manual install is working fine for me and was painless and quick. There is also a method to ensure that new kernel updates don't break the driver at [THIS LINK.]("http://ubuntuforums.org/showpost.php?p=5227704&postcount=1") This driver works better for me on 8.10 than any previous versions have worked on any other versions of Ubuntu.

---

### Post by montysan on 2009-02-28
Cheers for that, but it's a bit more manual than I was hoping for. I guess the fact that you're doing this means it's not generally available yet. Oh well.

Good to know that the new driver seems alright though!

Does anyone have any idea when this driver will be released through the normal channels??

---

### Post by avtolle on 2009-02-28
From reading the release notes for 8.10 about the then-existing nvidia 96 drivers and incompatibility with the xorg used in 8.10, I'd hazard a guess that the newer 96 driver won't likely be available through the 8.10 repositories at all, and your best bet would be to install them manually. As I said, this is my guess, but given the fact that the drivers haven't yet appeared in 8.10 repos, I'd not look for that to happen.

---

