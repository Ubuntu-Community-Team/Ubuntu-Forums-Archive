---
title: "no sound emachine w4620 w/ Ubuntu 9.10"
date: 2010-02-01
forum: Hardware
---

### Post by Qassis on 2010-02-01
RESOLVED!  Fixed!
Issue:  No sound!  Sound wouldn't work on a W4620 emachine with an
ATI Technologies Inc IXP SB400 AC'97 Audio Controller after upgrading to Ubuntu 9.10.

Very simple solution:  Go to application" pulse audio volume control" tab to OUTPUT DEVICES : and turn OFF amplifier.  Sound came back for most formats immediately, youtube sound returned only after reboot.  100% fixed.

Note: I previously had sound fixed with version 9.04 and only lost sound upgrading to 9.10.
If you have no sound with a new install of 9.10, not an upgrade, I don't know if this will work for you.

respectfully, qassis

---

