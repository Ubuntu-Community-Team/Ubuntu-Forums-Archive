---
title: "USB problem on 13.10"
date: 2014-02-14
forum: Hardware
---

### Post by hyyhyyyy123 on 2014-02-14
[TABLE]
[TR]
[TD="class: votecell"]              
[/TD]
              [TD="class: postcell"] I recently dualbooted Ubuntu 13.10 on top of 12.04 and now  both distros won't recognize USB devices. It recognizes that I have usb  ports but nothing appears in Files when I plug in a device through USB.

[/TD]
[/TR]
[/TABLE]


dmesg | tail
[  854.460876] raid6: sse2x2     747 MB/s
[  854.528879] raid6: sse2x4    1087 MB/s
[  854.528890] raid6: using algorithm sse2x4 (1087 MB/s)
[  854.528898] raid6: using ssse3x2 recovery algorithm
[  854.620728] bio: create slab <bio-1> at 1
[  854.629208] Btrfs loaded
[ 1551.482251] systemd-hostnamed[13047]: Warning: nss-myhostname is not installed.     Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2523.892113] perf samples too long (2519 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2591.888615] psmouse serio2: Touchpad at isa0060/serio2/input0 lost sync at byte 6
[ 2591.909739] psmouse serio2: Touchpad at isa0060/serio2/input0 - driver resynced.  

lsusb  while I have a usb device connected
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:d251 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by mörgæs on 2014-02-15
This is a duplicate of a thread in Askubuntu.

Closed.

---

