---
title: "another ubuntu suspend hibernate problem"
date: 2008-07-19
forum: Hardware
---

### Post by adamque99 on 2008-07-19
My suspend does not work, it locks the computer then I need to remove battery to restart
When I do sudo hibernate. Screen becomes black then comes back again, as if nothing happened. Here are the messages from /var/log/messages after I did sudo hibernate

^H^H^H^H 67%^H^H^H^H 68%^H^H^H^H 69%^H^H^H^H 70%^H^H^H^H 71%^H^H^H^H 72%^H^H^H^H 73%^H^H^H^H 74%^H^H^H^H 75%^H^H^H^H 76%^H^H^H^H 77%^H^H^H^H 78%^H^H^H^H 79%^H^H^H^H 80%^H^H^H^H 81%^H^H^H^H 8
Jul 19 00:10:55  -laptop kernel: [  501.753626] Wrote 503720 kbytes in 15.83 seconds (31.82 MB/s)
Jul 19 00:10:55  -laptop kernel: [  501.753835] S<3>swsusp: Swap header not found!
Jul 19 00:10:55  -laptop kernel: [  501.754170] |
Jul 19 00:10:55  -laptop kernel: [  501.860626] Restarting tasks ... done.
Jul 19 00:10:55  -laptop kernel: [  501.869698] swsusp: Basic memory bitmaps freed
Jul 19 00:10:56  -laptop kernel: [  501.974303] b43-phy6: Broadcom 4311 WLAN found
Jul 19 00:10:56  -laptop kernel: [  502.073964] input: b43-phy6 as /devices/virtual/input/input29
Jul 19 00:10:56  -laptop kernel: [  502.662025] input: PS/2 Mouse as /devices/virtual/input/input30
Jul 19 00:10:56  -laptop kernel: [  502.704449] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input31
Jul 19 00:10:57  -laptop kernel: [  503.489822] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00171704
Jul 19 00:10:57  -laptop kernel: [  503.750894] Registered led device: b43-phy6:tx
Jul 19 00:10:57  -laptop kernel: [  503.750923] Registered led device: b43-phy6:rx
Jul 19 00:10:57  -laptop kernel: [  503.750944] Registered led device: b43-phy6:radio
Jul 19 00:10:57  -laptop kernel: [  503.753826] ADDRCONF(NETDEV_UP): wlan0: link is not ready


I am using 2.6.24-19-generic kernel on ubuntu 8.04

Thanks
Adam

---

### Post by iva2k on 2009-01-18
Do you have swap file instead of partition?
(if you still have this problem since it was long time)

For anyone with similar problem:

What does swapon -s return?
```
swapon -s
```

See Ubuntu bug #313724 [https://bugs.launchpad.net/bugs/313724]("https://bugs.launchpad.net/bugs/313724")

See Red Hat bug #466408 [https://bugzilla.redhat.com/show_bug.cgi?id=466408]("https://bugzilla.redhat.com/show_bug.cgi?id=466408")

If the problem is due to swapfile, your only solution may be to convert to swap partition. Swap files are too new for Linux and Ubuntu - there seem to be too many unresolved issues still.

--
Ilya

---

