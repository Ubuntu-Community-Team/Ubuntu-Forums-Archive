---
title: "Ubuntu for the HP dv6t Quad Edition"
date: 2011-09-12
forum: Hardware
---

### Post by CountryGuy on 2011-09-12
Hello!

I have an HP dv6t Quad Edition laptop with the Optimus switchable graphics (IBM graphics plus a Radeon 6770M card), and I'd like to set this up to run with Ubunutu.  My big question right now is around drivers, as HP isn't providing any for Linux OS'es.  Hoping the folks here can help me out.  I should point out I am most definitely a Linux noob, so bear with me!

1) First, at this point is there a graphics driver option that will support the switchable graphics?  If not, is there a way to have Ubuntu use the IBM onboard (low power) GPU, but still make the Radeon available as-needed for Virtual Machines?

2) Is there a driver (and also application) that can be used to enable the fingerprint-identification device on the laptop?

3) Does Ubuntu support the Sandy Bridge architecture and USB 3.0 ports out of the box?  Or do I need to download something additional for that?

Very excited to give this a shot, but hoped to make sure I'm going to the right places for drivers if this is at all possible.

Thanks in advance!

---

### Post by SeijiSensei on 2011-09-12
So far I've only been able to force the machine to use the ATI card, and only then after installing a BIOS upgrade.  I installed F1.A, but it appears that F2.0 is a bit more recent.  You can find these [here](http://forum.notebookreview.com/hp-pavilion-notebooks/595505-updated-hp-pavilion-bios-releases.html).

That will enable you to enter the BIOS at boot and switch the graphics card to "fixed" mode. That has benefits for both [Windows]("http://forum.notebookreview.com/hp-pavilion-notebooks/583203-dv6t-61xx-dv7t-61xx-switchable-graphics-discussion.html") and Linux.  I found I could then install the proprietary driver for the ATI card (using the Additional Drivers application in Ubuntu).  

There's a lot of [work going on]("http://linux-hybrid-graphics.blogspot.com/") to make switchable graphics in Linux a reality on these types of machines even if the manufacturers don't make an effort to support it.  I hope to see if any of these developments work with my daughter's dv6tse when she returns from college for winter break.

I'd browse forum.notebookreview.com for updates on the fingerprint reader.  Last I saw it wasn't supported in Linux, but things may have changed on that front as well.

---

### Post by CountryGuy on 2011-09-12
Awesome, thank you very much for the prompt reply!  The fingerprint reader isn't that big of a deal to me, but a solution for the graphics would be great.

---

