---
title: "firewire drive won't mount"
date: 2008-06-18
forum: Hardware
---

### Post by wwuster on 2008-06-18
I'm running 8.04 desktop and just noticed that my external firewire drive no longer mounts automatically when I boot. Dmesg shows this error:

[   25.151050] ieee1394: Error parsing configrom for node 0-00:1023
[   25.151157] ieee1394: Host added: ID:BUS[0-01:1023]  GUID[0090270001e4f00b]

lspci shows:

07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


I've done all of the recent updates and I think that the kernel has had a couple of updates recently. This drive was mounting about a week ago but I just noticed that it was no longer doing that.

How can I get this working again?

thanks,
William

---

### Post by wwuster on 2008-06-20
It turned out that the power supply (Acommdata) to the external drive had gone bad. I tried another one and all is ok again.

William

---

