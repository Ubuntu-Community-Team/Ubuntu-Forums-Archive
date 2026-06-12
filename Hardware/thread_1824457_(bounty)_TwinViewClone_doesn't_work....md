---
title: "(bounty) TwinView/Clone doesn't work..."
date: 2011-08-13
forum: Hardware
---

### Post by eyerouge on 2011-08-13
**Problem**
No picture appears on the second monitor connected (external) monitor.

All used to work perfectly until yesterday. I always used nvidia-settings + TwinView/Clone to clone my laptops view, but now nothing happens and Ubuntu freezes, gets garbled and unresponsive. 

**50 USD bounty is promised** to whoever drops the magic words that will fix this for me, granted you accept PayPal. I rely on dual-screen setup on this machine for my work and need it to work.

**Screenshots**
These show some of the settings in nvidia-settings and also how garbled the screen becomes. Notice that the external screen (in this case the Samsung) shows nothing and is just black all the time. It does however detect it has an attached cable to it since the monitor says "No signal" when I disconnect the cable from my laptop to it.

[http://chaosrealm.net/wtactics/files/pics/2011_08_14_01.png](http://chaosrealm.net/wtactics/files/pics/2011_08_14_01.png)
[http://chaosrealm.net/wtactics/files/pics/2011_08_14_02.png](http://chaosrealm.net/wtactics/files/pics/2011_08_14_02.png)


**Hardware**
- MacBook Air 3,2
- GeForce 320M (GPU 0)

**Software**
- NVIDIA Driver Version: 270.41.06
- Ubuntu 11.04 (64)
- [B][xorg log lives here]("http://chaosrealm.net/wtactics/files/Xorg.0.log.txt")
[/B]

**Already tried**

[I]14:th of August 2o11:
[/I]
- Reinstalled the nvidia drivers and using the ones Ubuntu chooses in restricted drivers box.

- Reinstalled xorg.

- Deleted all GNOME2 settings and got a fresh GNOME2.

- Connected the computer to different external monitors, all which used to work, but with same zero result. (This all works in another OS on the same computer, so it's not hardware issues)

- Shut off Compiz - no change.

*28:th of August 2o11*

- Issue is now resolved: The problem was the display port to VGA adaptor. Once I swapped it out for a brand new one it all fixed itself.

---

