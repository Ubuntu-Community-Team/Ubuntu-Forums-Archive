---
title: "phy0: not handling 0x02 type control frame"
date: 2008-05-19
forum: Hardware
---

### Post by maxino on 2008-05-19
Hi all,
I recently installed Hardy Heron on a Fujitsu-Siemens Amilo A7640 laptop.
It seems to be working satisfactorily (just the video chip -SIS M760- is not fully supported in Linux) and the laptop's user, my father, is not complaining much :)
One thing bothers me, though: I keep receiving *a lot* of the following error/warning every time I do dmesg:

```
phy0: not handling 0x02 type control frame
```

I get this message literally every second or even more frequently and therefore I cannot see the other messages from dmesg (since the last hundreds -or thousands- lines are all as above).
I'd really like to understand what's happening, googling around I haven't found much.
Can anyone advice?

Thanks in advance,

---

### Post by maxino on 2008-05-20
Hello guys,
Google is not turning any reference for my error message and in the meantime my kernel keeps on spitting out the same line over and over:

```
phy0: not handling 0x02 type control frame
```

I have no idea whatsoever where this comes from.
Can anyone point me in the right direction?

Thanks,

---

### Post by Pondussi on 2009-08-29
Same problem here, about 169 times per minute those messages float /var/log/syslog.0, kernel.log.0 and debug.0, letting those files grow about 1 MB per minute.

There's a launchpad report* which is marked as fixed in 2008 for Intrepid. But as it seems it does still exist in Jaunty!

*) [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/248455](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/248455)

---

