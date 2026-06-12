---
title: "booting from SSD and bogus &quot;degraded raid devices&quot; warnings"
date: 2012-01-27
forum: Hardware
---

### Post by dsevil on 2012-01-27
Hi, I just installed Oneiric on a system that now has a 64GB SSD and a 1TB software RAID-1 of two old-fashioned spinning-platter hard drives (kept from an old Debian install).  I did a netinstall with no desktop or anything, just some basics and some X stuff (I use fvwm).  No gdm or anything, I login at console and type startx to do my stuff.

Result: booting literally takes less than 5 seconds.  That's from "once GRUB is done" to "'login:' prompt".

Problem: I have this feeling it's actually booting *too* fast because about half the times I boot I'll get this warning:

```

** WARNING: There appears to be one or more degraded RAID devices **
<snip>
md1 : inactive sdb1[1](S)
        976759936 blocks

```

When asked if I want to start with the "degraded" RAID I answer yes.  A few seconds later I'll login and run "cat /proc/mdstat" and everything looks fine:

```

md1 : active raid1 sdc1[0] sdb1[1]
      976759936 blocks [2/2] [UU]

```

Any ideas on what I can do maybe to actually slow my boot down?  (lol)

---

### Post by dsevil on 2012-01-27
I was presented with this:

```

echo -e '#!/bin/sh\nsleep 10' >/etc/initramfs-tools/scripts/local-top/easy-there-horsey
update-initramfs -u

```

it works.  you can be smarter about it if you want.

---

