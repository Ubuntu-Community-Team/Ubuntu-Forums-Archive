---
title: "Change motherboard, now (K)Unbuntu wont't boot"
date: 2009-02-24
forum: Hardware
---

### Post by oobuntoo on 2009-02-24
I replaced dead motherboard along with CPU (X58 motherboard and Core i7 CPU), now Ubuntu/Kubuntu system won't boot. I'm dual booting with Vista. Vista loaded OK; installed new drivers for chipset, LAN, sound and everything is back to normal.

Short of clean install, is there anyway to do the same under Linux, Ubuntu/Kubuntu in particular? If live-cd can detect hardware and loaded appropriate drivers, why can't an already installed system detect changes in hardware and load correct drivers or at least ask for correct drivers? This seems like a glaring weakness in Linux in general.

Has anyone on this forum experienced a similar problem?

---

### Post by pmlxuser on 2009-02-24
there are several files that have the configuration of the removed MB and thus when the system tries to load it tries to load those setting the Best is to remove them if you know how and replace them with the system files that load during the Live CD session.

I remembered when i changed the video card the same happened all i did was to delete the video card setting file in /etc/X something and the system reconfigured itself to the new hardware.

Regards (i would do a clean install if I were you of course); If there is no risk of loosing alot of data..

---

### Post by oobuntoo on 2009-02-24
> **pmlxuser said:**
> there are several files that have the configuration of the removed MB and thus when the system tries to load it tries to load those setting the Best is to remove them if you know how and replace them with the system files that load during the Live CD session.

I remembered when i changed the video card the same happened all i did was to delete the video card setting file in /etc/X something and the system reconfigured itself to the new hardware.

Regards (i would do a clean install if I were you of course); If there is no risk of loosing alot of data..

I figured I would have to do a clean install. It's probably a lot less painful than messing around with config files. I just wanted to check to see if anyone else knows an easier alternative.

---

