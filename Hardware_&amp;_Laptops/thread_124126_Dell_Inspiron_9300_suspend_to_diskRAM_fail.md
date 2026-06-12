---
title: "Dell Inspiron 9300 suspend to disk/RAM fail"
date: 2006-01-31
forum: Hardware &amp; Laptops
---

### Post by jnthornh on 2006-01-31
My Dell Inspiron 9300 will not suspend to disk or RAM.  Well, that's not entirely accurate - it WILL suspend, it just won't ever wake back up.

I have read various reports of functional suspend on this model, but none of the recommendations have helped me.  I've also read several counts of people with suspend failing.

I have noticed that all success stories have been using the ATI video chipset.  It seems possible my NVidia graphics chipset is the culpret.

I've also tried using Dapper, but it behaves exactly the same as Breezy in this regard.

If anybody has any recommendations on how to work around this, I'd be thankful.  Barring a workaround for Ubuntu, I would also appreciate any information about other distributions that might support this feature on the i9300.

---

### Post by sevenseeker on 2007-07-28
This is resurrecting an old post, but with my problems it is still valid.

Suspending to RAM or Disk fails.  The power light stays on and I am forced to do a hard shutdown.

This happens without the official nVidia drivers.  That is because I can not get the official drivers to work with Ubuntu (Kubuntu) Feisty.

Suspend and Hibernate worked with Suse 10.2 with no problems (just slow).

nVidia drivers also worked under Suse 10.2.  Is this a kernel issue?  I don't remember what kernel version Suse 10.2 has  but now I have:
2.6.20-16-generic

One odd thing is that it claims it is a SMP kernel, which my system does not need (single core), the 9400 has dual core.  I wasn't aware of this causing a problem, but who knows?

Trying other methods posted here so far are not working.

---

