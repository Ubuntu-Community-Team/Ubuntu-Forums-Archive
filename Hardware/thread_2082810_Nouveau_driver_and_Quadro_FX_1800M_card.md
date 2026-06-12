---
title: "Nouveau driver and Quadro FX 1800M card"
date: 2012-11-10
forum: Hardware
---

### Post by Titibandit on 2012-11-10
Hello everybody !
I'm now using Ubuntu on my HP Workstation 8540W laptop, with a nvidia Quadro FX 1800M graphic card.
The first time I installed Ubuntu on this machine, I booted on a USB key, and each time, after the loading ubuntu logo, the computer freezes with some nice glitches.
After some research, it quickly came to me that it was the nouveau nvidia driver that didn't work. The fix was to disable KMS, and to install nvidia's drivers.

I'm running like this since, but now I really want to get rid of these proprietary nvidia drivers (mainly because managing two screens with these drivers is a pain).
I decided to wait until the release of 12.10, to see what happened with this nouveau driver, and nothing changed ... same freezes when trying to boot with KMS enabled ...
The only difference is that now, I can get an error message. Here it is :

```

[70.208725] [drm] nouveau 0000:01:00.0: Failed to idle channel 2.
[74.208678] [drm] nouveau 0000:01:00.0: PGRAPH TLB flush idle timeout fail : 0x011fde03 0x00145b4d 0x0000002d 0x0034db40
[76.203997] [drm] nouveau 0000:01:00.0: PGRAPH TLB flush idle timeout fail : 0x011fde03 0x00145b4d 0x0000002d 0x0034db40

```Googling these messages was unsuccessful ...

any kind of help would be much appreciated !
of course, if you need more information than I gave ... tell me !

Thanks a lot !

---

