---
title: "US-428 Help in Dapper Drake - missing files?"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by W. James MacLean on 2006-07-22
Hi,

I'm trying to get a Tascam US-428 mixer running in Dapper Drake, but having some problems.

I'ved installed alsa-tools and alsa-firmware, but the latter seems to be missing the directory /usr/share/alsa/firmware/usx2yloader and its associated files. Now, I downloaded the firmware package directly from the alsa page, and then ran

```

lsusb
 sudo /sbin/fxload -s /usr/share/alsa/firmware/usx2yloader/tascam_loader.ihx -D /proc/bus/usb/003/005 -I /usr/share/alsa/firmware/usx2yloader/us428fw.ihx
/usr/bin/usx2yloader
/usr/bin/us428control &

```

Everything *seems* to have worked, except for the last step which gives

```

us428control: cannot open hwdep hw:0
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
us428control: seq.c:1044: snd_seq_poll_descriptors_count: Assertion `seq' failed.

```

Any thoughts? I wonder if this might not have been an issue of the firmware files hadn't been missing - does anyone know why this is?

Cheers,

James

---

