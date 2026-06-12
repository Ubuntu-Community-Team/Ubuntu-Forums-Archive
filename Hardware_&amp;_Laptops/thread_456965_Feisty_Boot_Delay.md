---
title: "Feisty Boot Delay"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by cabbage on 2007-05-28
Dear all,

I've just performed an upgrade from edgy to feisty on my Dell Inspiron 8200. Now when it boots there is a 20 second delay once usplash starts before anything happens. See the attached bootchart.

I've read about the problems with the network config causing delays whilst booting, but this is before it gets that far.

Can anyone shed any light on this please.


Thanks,

Cabbage.

P.S. Needless to say, this didn't happen in edgy. I'm wondering if its anything to do with the drives now being treated as sd? devices rather than hd?...

---

### Post by cabbage on 2007-06-01
Having looked in /var/log/dmesg there are two instances of ata "device error" during each boot. I'm guessing the new libata does not work well with my IDE cdrom.

To work around this I modified /etc/initramfs-tools/modules and included the ide ones, and blacklisted the ata ones.

Now I've got /dev/hda devices again and the system boots in 39 seconds rather than 110!


Regards,

Cabbage.

---

### Post by maubp on 2007-06-01
How easy was it to get that bootchart?

I'm still on Dapper Drake, but I've noticed there is a LONG pause if I have my USB card reader plugged in at boot time (its usually empty - with no cards present).

---

### Post by cabbage on 2007-06-01
Its real easy - just "sudo apt-get install bootchart" and reboot. The picture will then be in /var/log/bootchart.

:-)

---

