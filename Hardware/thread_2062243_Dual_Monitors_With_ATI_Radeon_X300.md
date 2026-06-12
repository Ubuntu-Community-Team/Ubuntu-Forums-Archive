---
title: "Dual Monitors With ATI Radeon X300"
date: 2012-09-24
forum: Hardware
---

### Post by AlistairH on 2012-09-24
Until this weekend I was running Ubuntu 10.04 which was happily extending my desktop across two 23" monitors using the built in open-source driver for my ATI Radeon X300.

This weekend I have tried numerous 12.04 based distributions and all have failed miserably to use both monitors, with major screen distortions and system freezes where only a hard reboot would get me going again.

I'm presuming the latest open-source drivers supplied with 12.04 based distros are not compatible with my graphics card (can anyone confirm that?), so I have two questions:

1. Are there ATI 3rd party drivers that would work with this card and on 12.04 distros?
2. Failing that, what nVidia based card would users recommend remembering that I do not need anything fancy other than the ability to extend the desktop across the two monitors.?

Thanks in advance

---

### Post by sacaudill on 2012-12-01
I wish someone had some insight on this issue, as I have had the same problem plague me for a while now and it's the only thing keeping me from switching to Linux completely.

---

### Post by QIII on 2012-12-01
As for 1.:

No.  No ATI driver will work with that card.  The legacy driver for it would, except for the fact that it will not work with X Server versions post 2008.

I'm genuinely surprised, however, that the open source Radeon driver would suddenly not work.

If someone comes along recommending another ATI card, all of them prior to the HD 5xxx series have just been legacied and won't work with the X Server versions starting with Ubuntu 12.10, putting you back to the Radeon driver anyway.

---

