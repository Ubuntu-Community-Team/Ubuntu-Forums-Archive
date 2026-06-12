---
title: "ATI Mobility Radeon 7500 driver"
date: 2008-12-18
forum: Hardware
---

### Post by widggman on 2008-12-18
Hi,

  I'm looking for a driver for my old video card on my laptop, an ATI Mobility Radeon 7500 64mb.

  I checked on the ATI web site, but the driver doesn't seem to be there. On this site:
   [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

  I have a list of potential driver called: Mobility Radeon X600/X700/X800. Is one of these driver okay for my video card ?? And if it's the case, which one should I get ??

  Thanks in advance!

JUST another thing, all the drivers looks like they're for x86_64... and I have a 32bits system...

---

### Post by jocko on 2008-12-19
ATI have never made any linux driver for cards below the radeon 8500, and the past few years they dont support anything below radeon 9500 . The only driver which works for a radeon 7500 is the open source driver (named radeon) which is installed and enabled by default in ubuntu.


and:
> JUST another thing, all the drivers looks like they're for x86_64... and I have a 32bits system...
Actually ati's driver installers have "x86.x86_64" in their file names, which mean they are both for x86(32bit) and x86_64(64bit).

---

### Post by widggman on 2008-12-19
I tried everything I've found and nothing work...

But the default driver doesn't seam like working well... I cannot even test glxgears

Anyway, it's an old laptop, so I'm not totally surprised.

Thank for your reply

---

### Post by overdrank on 2008-12-19
> **widggman said:**
> I tried everything I've found and nothing work...

But the default driver doesn't seam like working well... I cannot even test glxgears

Anyway, it's an old laptop, so I'm not totally surprised.

Thank for your reply

Hi and Hardy works well for me on a ATI 7000 32mb, If you are will to try. :)

---

### Post by widggman on 2008-12-19
I have an old Live CD of Ubuntu 7.XX. Tomorrow, I will try it to see if the OpenGl works on the video card

And if it is... is it possible to use that old driver to overwrite the new one ???

---

### Post by widggman on 2008-12-21
Like I said, I tried an older livecd version and effectively, the video card is recognized. In the xorg.conf file, it's written that the driver is called "ati".

Is there a way to get that driver from the live CD and make it work on the current version of Ubuntu ??

On the livecd, I was able to run "glxgears". I got a poor FPS, but at least, it something.

So, I'd like to have your opinion and/or solution about that driver!

Thanks

---

