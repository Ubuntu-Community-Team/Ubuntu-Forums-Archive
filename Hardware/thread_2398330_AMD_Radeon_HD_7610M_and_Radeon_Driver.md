---
title: "AMD Radeon HD 7610M and Radeon Driver"
date: 2018-08-10
forum: Hardware
---

### Post by davidbrinkman1999 on 2018-08-10
Hi everyone,

Currently I'm running Ubuntu 14.04 LTS on my Toshiba Satellite C855-255 with AMD Radeon HD 7610M GPU, which uses the fglrx driver if I'm correct. My Ubuntu install has become a bit of a mess over the last few years of using it and I want to reinstall and figured I might as well upgrade as support will stop next year for 14.04. Since the fglrx driver isn't supported anymore I was wondering if the Radeon driver is supported for my GPU? I couldn't find it in the supported list.  If not supported, is there any other driver I could use or is there a Linux (preferably Ubuntu based) that still supports (and will keep supporting) the fglrx driver? 

Thanks!

---

### Post by charles-scoville on 2018-08-10
Hi,

I have had great luck in the past with the AMD Catalyst Proprietary Linux Graphics Driver. These have worked for me from down to an HD 3000 series, up to at least HD 6000 series... Let me get a link for you....

Edit: Here:

[https://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst15-9LINReleaseNotes.aspx]("https://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst15-9LINReleaseNotes.aspx")

Your card is among the supported cards.

---

### Post by deadflowr on 2018-08-10
> **charles-scoville said:**
> Hi,

I have had great luck in the past with the AMD Catalyst Proprietary Linux Graphics Driver. These have worked for me from down to an HD 3000 series, up to at least HD 6000 series... Let me get a link for you....

Edit: Here:

[https://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst15-9LINReleaseNotes.aspx]("https://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst15-9LINReleaseNotes.aspx")

Your card is among the supported cards.

Does not work on any Ubuntu system beyond 14.04.1's xserver version 1.15 and linux kernel 3.13. 
(I think technically it works up to 1.17 and linux kernel 3.18 (or 3.19) but none of that is supported on Ubuntu anymore)

To the op I do not know what the state is in terms of the open source radeon drivers quality on the 7610M card is.
But the driver does support the card. How well is another thing.

---

### Post by Yellow Pasque on 2018-08-12
It should work fine. If you're really concerned, try a LiveUSB of Ubuntu 18.04.1 before you jump.

---

