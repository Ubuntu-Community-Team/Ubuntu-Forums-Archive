---
title: "Add/Remove ATi Question"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by Newbieuk on 2009-07-05
Hi,
Brand new to linux and ubuntu 9.04 (1 day after 10 years windows frustration) I am beginning to see the light or coffee!! Likely to post many more very simple questions while I find my way around so apologise in advance, am older but not wiser when it comes to computers or forums.

Have desktop (Acer with AMD X2 5000 processor and ATI Radeon 2100 graphics PCI express 2.0 x16 graphics card support). As I understand it the ATI is an onboard chipset/graphics and not a separate card??

On add/remove programmes under Canonical maintained there is an uninstalled/ unticked (ATI binary X.Org driver Video driver for the ATI Radeon and FireGL graphics accelerators this package provides 2D display drivers and hardware accelerated OpenGL).  I am very vary of installing anything that may corrupt or change settings but as the graphics on the desktop are ok since ubuntu installation I am hoping that this will improve desktop/colours/images etc.  Question is A do I install and B will ubuntu do this all on its own without me having to write code, something I have never done before.

Hope someone can help on this.

Regards

Newbieuk

[LEFT][/LEFT]

---

### Post by hellocatfood on 2009-07-05
Hey NewbieUK,

If you go to Administration > Drivers and do a search you can install the drivers there. That's what I used and I didn't have to write any code.

On a separate note, I see that you're from the Midlands. If you want to learn more about computers and Linux I suggest going to your local Linux User Group. [http://lug.org.uk/](http://lug.org.uk/)

There's LUG's in Birmingham, Coventry, Wolverhampton, Nottingham and just about every other major city

---

### Post by wpshooter on 2009-07-05
> **Newbieuk said:**
> Hi,
Brand new to linux and ubuntu 9.04 (1 day after 10 years windows frustration) I am beginning to see the light or coffee!! Likely to post many more very simple questions while I find my way around so apologise in advance, am older but not wiser when it comes to computers or forums.

Have desktop (Acer with AMD X2 5000 processor and ATI Radeon 2100 graphics PCI express 2.0 x16 graphics card support). As I understand it the ATI is an onboard chipset/graphics and not a separate card??

On add/remove programmes under Canonical maintained there is an uninstalled/ unticked (ATI binary X.Org driver Video driver for the ATI Radeon and FireGL graphics accelerators this package provides 2D display drivers and hardware accelerated OpenGL).  I am very vary of installing anything that may corrupt or change settings but as the graphics on the desktop are ok since ubuntu installation I am hoping that this will improve desktop/colours/images etc.  Question is A do I install and B will ubuntu do this all on its own without me having to write code, something I have never done before.

Hope someone can help on this.

Regards

Newbieuk

[LEFT][/LEFT]

Newbieuk:

It has been my experience that if you have the video drivers that were installed by default by the O/S, then you may want to stay with those unless you are having some specific problem.

Again my experience has been that if you attempt to install some driver other that the default they MAY or MAY NOT work.  My experience has been that they generally do NOT work very well.

So if you decide to try some driver other than the default make sure that you have the proper knowledge to straighten out any problems caused by the new driver, or a means to revert back to the old driver or perhaps even having to reinstall the O/S from scratch.

Good luck.

---

### Post by Newbieuk on 2009-07-05
Thanks guys,

I appreciate the advice and will see what I can do, worst case I'll have to reinstall Ubuntu.

Thanks for the added advice on local groups hellocatfood much appreciated.

Regards

Newbieuk

---

### Post by Mark Phelps on 2009-07-05
Newbieuk:

The combination of AMD/ATI dropping support for non-HD video cards/chipsets from their drivers, and Canonical upgrading the Xorg in Ubuntu 9.04 has produced the nasty situation where folks used to upgrading ATI restricted video drivers by default end up all to often with no video or corrupted video -- a problem not helped by the ready availability of utilities that apparently, fail to check to see if the drivers are compatible with the Xorg version before installing them.

I believe that the 2100 was one of the chipsets no longer supported under the AMD/ATI restricted drivers.  If that's the case, do NOT force the installation of those drivers in your machine, unless you have made a backup that you can use to restore it in the event of loss of video or desktop.

---

### Post by Newbieuk on 2009-07-06
Thanks Mark,

I think based on your advice I will not try to add.  The graphics on my pc are ok on most things,  just a few website fonts and display look a bit strange (blurred and washed out) hence the reason for thinking of an update via add/remove listing for the ATI driver.

Thanks again

Regards   

> **Mark Phelps said:**
> Newbieuk:

The combination of AMD/ATI dropping support for non-HD video cards/chipsets from their drivers, and Canonical upgrading the Xorg in Ubuntu 9.04 has produced the nasty situation where folks used to upgrading ATI restricted video drivers by default end up all to often with no video or corrupted video -- a problem not helped by the ready availability of utilities that apparently, fail to check to see if the drivers are compatible with the Xorg version before installing them.

I believe that the 2100 was one of the chipsets no longer supported under the AMD/ATI restricted drivers.  If that's the case, do NOT force the installation of those drivers in your machine, unless you have made a backup that you can use to restore it in the event of loss of video or desktop.

---

