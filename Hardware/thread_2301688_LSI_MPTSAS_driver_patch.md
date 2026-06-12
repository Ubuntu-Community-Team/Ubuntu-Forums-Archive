---
title: "LSI MPTSAS driver patch"
date: 2015-11-04
forum: Hardware
---

### Post by dan201 on 2015-11-04
Hi Guys,

It's my first post on this forum so please bear with me :O)

I'm  using an LSI SAS controller (SAS3041XL (SAS1064 Chipset) within my  servers, to test some SATA and some SAS disk drives. I need a patched  mptsas driver to stop Linux interfering with the device when it's  detected.

Is there someone out there in the big wide world who has low level experience who could patch my driver?

Thanks guys
De

Current O/S 10.04.4 LTS

---

### Post by mörgæs on 2015-11-05
Hi, welcome to the fora.

If you want newer drivers it's best to begin with a fresh install of 15.10. Chances are that all necessary drivers are here by default.
10.04 is out of support and should not be used.

---

### Post by dan201 on 2015-11-05
[COLOR=#000000]Hi [FONT=arial]**[B]Mörgæs**[/B][/FONT][/COLOR], 

I have other specific hardware that has no support for newer versions of the distro, therfore I am stuck with what I have :O(. Still looking for someone to patch source 

Thanks
D

---

### Post by mörgæs on 2015-11-05
You are of course free to look but I doubt that people here care for coding a patch for an unsupported release, especially since it may already be fixed in 15.10.

If you explain about the hardware support problem then maybe someone has a workaround for that.

---

