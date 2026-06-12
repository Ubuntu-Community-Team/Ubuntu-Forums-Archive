---
title: "sbp2 (ipod) issues"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by craigmaloney on 2005-04-17
Hi all.

Just installed Hoary... coming from sarge... many things seem very nice and I didn't want to futz with sarge for weeks to get things cherry.  Kudos to the ubuntu people.

Here's my problem...  I have an sbp2 device (my hfs+ ipod... but I'm not sure if that matters at all) and also an external DELL firewire CDRW for my laptop.  The ipod works if its plugged in at boot.  I get the "do not disconnect message".  I can r/w to the drive which is mounted properly:

----------
Apr 17 02:26:24 localhost kernel: scsi0 : SCSI emulation for IEEE-1394 SBP-2 Dev
ices
Apr 17 02:26:24 localhost kernel: NET: Registered protocol family 17
Apr 17 02:26:24 localhost kernel: ieee1394: sbp2: Logged into SBP-2 device
Apr 17 02:26:24 localhost kernel:   Vendor: Apple     Model: iPod              R
ev: 1.40
Apr 17 02:26:24 localhost kernel:   Type:   Direct-Access                      A
NSI SCSI revision: 02
Apr 17 02:26:24 localhost kernel: SCSI device sda: 19531260 512-byte hdwr sector
s (10000 MB)
Apr 17 02:26:24 localhost kernel: sda: test WP failed, assume Write Enabled
Apr 17 02:26:24 localhost kernel: SCSI device sda: 19531260 512-byte hdwr sector
s (10000 MB)
----------------------------------

OK. So I unmount the thing and the "do not disconnect" message goes off.  I do this part graphically via the kubuntu konqueror window "safely remove ipod".  The icons go away, but the strange thing is that the sbp2 is still in use (refcount is 2).

After this I am unable to use either my CDRW or the ipod.  The 1394 bus doesn't even seem to notice any sort of bus activity (nothing in the logs... no icons in the konqueror window).

If the CD is plugged in first, then it works with no problems.  I haven't thouroughly explored getting the same kind of effects with just the CD, but it seems strange to me that the ref count on sbp2 seems wrong.

Does anyone know what might be the issue?  I'd be more than happy to provide more relevant details, but I'm a bit of a newbie, and I'm not sure which details are relevant.

Thanks in advance.

Cheers,
Craig

---

