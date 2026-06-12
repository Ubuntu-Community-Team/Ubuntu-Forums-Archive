---
title: "What is the better driver?  xserver-xorg-video-ati v. fglrx v. fglrx-updates"
date: 2016-01-20
forum: Hardware
---

### Post by ibhollow1975 on 2016-01-20
Out these three drivers xserver-xorg-video-ati, fglrx and fglrx-updates which one is the best? What are the pluses and minuses of each? I am trying to get some feedback on this because I just installed fglrx-updates due to screen tearing with xserver. So, far things look better. I look forward to your feedback.

---

### Post by mastablasta on 2016-01-21
partially depends on the chip.

otherwise:
video ati = opensource = worst
fglrx = closed source = stable, usually a good choice if chip is supported
fglrx-updates = slightly less stable but depending on the chip might have some bugs patched and could for that reason work better than fglrx on some chips.

usually:
closed source driver > opensource

but depends on the chip as for some AMD chips they are almost equal.

---

### Post by Yellow Pasque on 2016-01-21
I don't think there's any hard and fast rule about which one will work better on every card/system. Take it on a card by card basis.
I've always found the open source driver to be more reliable and have better video accel (with mesa-vdpau-drivers package). fglrx generally gives better 3D framerates and is sometimes necessary for the latest GPU's where the open source support has not caught up yet (or has not found its way into stable distro releases).

Just a note: fglrx and fglrx-updates could be the same driver depending on if an updated version of fglrx has been packaged for that version of Ubuntu.

---

