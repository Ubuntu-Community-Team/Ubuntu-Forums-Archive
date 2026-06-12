---
title: "Am I using hardware acceleration?"
date: 2013-09-29
forum: Hardware
---

### Post by mma8x on 2013-09-29
Running Kubuntu 13.04,  AMD Athlon(tm) II X2 245 Processor, Radeon HD 3200 GPU.  I'm running XBMC with a separate mythtv backend.  I get choppy HD playback on this machine.  My CPU use shows 50-60%, though I always question how accurate that is.  I have a much older laptop that plays back the same content without a problem, as does my raspberry pi.  So this hardware should be plenty capable.  I'm using the radeon driver.  How can I tell if I'm getting hardware acceleration? I'm guessing that's my problem here...

---

### Post by Yellow Pasque on 2013-09-29
You're not going to get video decode accel from an HD3200 (at least right now). AMD finally released UVD support for the open-source radeon driver, but it only works on cards with UVD 2.2 or later (i.e. RadeonHD >= 4250).

---

### Post by mma8x on 2013-09-30
Thanks.  For some reason I thought that the radeon driver supported everything except some 3d functions.  I feel like this just started recently.  I wonder if I was using the fglrx driver before and somehow switched to radeon after an upgrade...

---

### Post by mma8x on 2013-09-30
Well, I'm guessing that what happened is that I had the fglrx driver, upgraded to 13.04, and now I'm SOL.  More reading shows that it doesn't look like the new ATI drivers support the HD 3200, and the legacy drivers aren't supported by ubuntu.  So I can either downgrade my system (which I'm guessing will be a huge PITA) or live with the poor performance.  Not good choices.  I mean, this hardware isn't THAT old to run into these problems...

---

### Post by Yellow Pasque on 2013-09-30
"Look before you leap."

---

### Post by QIII on 2013-09-30
> **mma8x said:**
> I mean, this hardware isn't THAT old to run into these problems...

Agreed.  However, since the decision not to continue Linux support was AMD/ATI's there is not much anyone in the Linux community can do about it.  The best anyone can do now is use the open source driver.  That driver has really gotten very good over the last several years, but the developers can only see so far back into a black box and they make do as best they can.

This has done little to endear AMD/ATI to the Linux community.

---

### Post by mma8x on 2013-09-30
Yeah, I know.  However, it's frustrating to upgrade and have a fairly fundamental breakage.  As much as I try to use them, the open source drivers are often just not as good--running into the same problem with realtek wifi chips.  Oftentimes the hardware is listed as "supported", but really it's only kinda-sorta supported.  Ubuntu (and linux in general) has gotten MUCH better at not ending up at a console with no internet after an upgrade, but it would be nice to know about this kind of thing before the upgrade.  Or come up with an official work-around for the legacy drivers.  I've read about rolling back to an earlier X version, but that seems like trouble as well.

---

### Post by Yellow Pasque on 2013-09-30
The other thing I would look at is what video output method the mythtv backend is using. If you had it set to use xvba or va-api (to work better with the proprietary driver), perhaps setting it to use Xv output would help.

---

### Post by mma8x on 2013-10-11
Couldn't find that setting on the backend for some reason.  In XBMC, I disabled the hardware acceleration options.  It seems to have started playing better on its own before that though.  Anyway, the playback at this point is smooth, so I'm sorta happy enough.  Thanks.

---

