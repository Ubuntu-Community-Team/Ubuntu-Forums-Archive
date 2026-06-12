---
title: "Hibernate stops working after Hardy -&gt; Intrepid upgrade"
date: 2008-11-02
forum: Hardware
---

### Post by rts on 2008-11-02
Hibernate has stopped working on my laptop after upgrading to Intrepid.

Unfortunately, there isn't a whole lot in the logs to indicate what the problem might be.

The hibernate seems successful enough:

```

$ cat pm-suspend.log 
Initial commandline parameters: 
Sun Nov  2 00:37:04 GMT 2008: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/00clear hibernate: success.
/usr/lib/pm-utils/sleep.d/05led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager hibernate: success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/50modules hibernate: success.
/usr/lib/pm-utils/sleep.d/90clock hibernate: success.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate: success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate: success.
/usr/lib/pm-utils/sleep.d/95led hibernate: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode hibernate: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video hibernate: success.
/usr/lib/pm-utils/sleep.d/99video hibernate: success.
Sun Nov  2 00:37:06 GMT 2008: performing hibernate

```

But the resume just says "failed":

```

Nov  2 10:24:58 ubuntu kernel: [    5.488884] PM: Starting manual resume from disk
Nov  2 10:24:58 ubuntu kernel: [    5.488889] PM: Resume from partition 254:1
Nov  2 10:24:58 ubuntu kernel: [    5.488891] PM: Checking hibernation image.
Nov  2 10:24:58 ubuntu kernel: [    5.489088] PM: Resume from disk failed.

```

I can't find in any log anything more specific than that.

Any hints appreciated.

---

### Post by Paul S on 2008-11-13
Same problem here.  It  gets just beyond unzipping the resume file and hangs.  You can see this by editing your grub boot line and removing "quiet splash" from the end.

maybe follow bug [https://bugs.launchpad.net/ubuntu/+bug/269490](https://bugs.launchpad.net/ubuntu/+bug/269490)

guess we have to wait for a fix.

regards,

---

### Post by nhooey on 2010-06-17
I don't think this is a bug, per se, since I used to have pm-hibernate working fine on Ubuntu 9.04 and 9.10. It now fails with 10.04 with the same useless message:

"PM: Resume from disk failed."

How do you fix this problem?

Why does stupid pm-hibernate not give any more information about WHY it can't resume?

---

