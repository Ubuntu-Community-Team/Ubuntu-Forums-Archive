---
title: "dualboot linux + vista on t61 = rescue and recovery"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by ubiwankanubi on 2007-10-22
I have installed 7.10 on a t61 laptop, I used the live CD to resize the windows partition and made some partitions for linux. After the install, ubuntu works great, but, every time I try to boot into windows vista, I get the rescue and recovery screen!

I've taken a look in parted and vista is installed in sda2, however picking any choice to boot windows results in the recovery screen

here's my menu.lst concerning windows vista:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Any help on how I can get vista working again without deleting ubuntu is what I'm hoping for!!

---

### Post by El Zoido on 2007-10-22
As far as I know, you HAVE to shrink the partition in Vista, because of some changes in the NTFS filesystem. If you want both you probably have to use the recovery and maybe reinstall Ubuntu again...

A friend of mine had the same problem, but fortunately the recovery didn't touch Ubuntu, so afterwards everything seems fine (till now, at least).
I can't promise that it will work for you as well though...

---

