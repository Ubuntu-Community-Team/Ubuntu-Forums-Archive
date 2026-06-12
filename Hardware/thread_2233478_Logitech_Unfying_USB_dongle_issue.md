---
title: "Logitech Unfying USB dongle issue"
date: 2014-07-08
forum: Hardware
---

### Post by kurt18947 on 2014-07-08
This is more of a heads-up though if anyone has any thoughts I'd welcome them.  I've had a Logitech keyboard (K320) that uses the USB receiver that is supposed to support up to 6 devices.  I recently purchased a Logitech M570 wireless trackball.  Pairing the devices is pretty simple; start with both devices switched off and turn one on at a time, pausing a few seconds between.  Both devices worked on one receiver but periodically I'd have about 8 seconds where keystrokes didn't register but would be buffered and would eventually registered.  I look at dmesg and saw this:
```
[11115.017631] PM: Finishing wakeup.
[11115.017632] Restarting tasks ... done.
[11115.381792] r8169 0000:02:00.0 eth0: link down
[11115.381801] r8169 0000:02:00.0 eth0: link down
[11115.381830] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[11117.041775] r8169 0000:02:00.0 eth0: link up
[11117.041796] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[12307.264248] type=1400 audit(1403950780.599:71): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=11322 comm="apparmor_parser"
[12307.264257] type=1400 audit(1403950780.599:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=11322 comm="apparmor_parser"
[12307.264692] type=1400 audit(1403950780.599:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=11322 comm="apparmor_parser"
[13649.020375] nvidia 0000:01:00.0: irq 43 for MSI/MSI-X
[13652.163976] type=1400 audit(1403952125.727:74): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/etc/dconf/profile/gdm" pid=11954 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=115 ouid=0

```

I saw apparmor and wondered if I had some sort of keystroke logger or other malware.  I decided to start Windows and download Logitech's unifying utility.  I paired keyboard & trackball to one receiver and restarted Ubuntu-gnome.  The delay was better - perhaps one second instead of 8 but still present and the above dmesg entries were still present.  I finally used 2 receivers, one for each device paired using the Windows/Logitech utility.  It appears both pieces are working as intended and no questionable dmesg entries.  

Any thoughts about what caused this except "works best with Windows"?  It's possible that my motherboard is at issue.  It's a Gigabyte MA785GM-US2H on which I've noticed some USB devices do not function 100% correctly.  Anyone else using the Logitech Unifying receiver on Ubuntu with multiple peripherals attached to one receiver?

---

