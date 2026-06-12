---
title: "Atheros AR242x and the ath5k driver"
date: 2009-05-25
forum: Hardware
---

### Post by salemboot on 2009-05-25
* I am posting this so that it will possibly help others.  

The scenario:

Testing Ubuntu 9.04 and couldn't get the ath5k driver to authenticate with a Netgear wireless router.

The specifics:
1. Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
2. Ubuntu 9.04 patched
3. Netgear WGR614 v7 latest patch ? 29
4. The protocol was set to WPA.  

Kubuntu 9.04 had worked fine with the ath5k driver.
Which to me was odd as they should be running the same kernel versions?

I tried various versions of madwifi-hal, trunk and the 0.5.10 compilation.

These all failed.

I'm also fortunate enough to have an Intel graphics chipset for which 2.6.30 r7 fixes.  That said, I moved to 2.6.30 r7 without fixing the problem.

Sure enough it was still a problem after the move.

I have two hypothesis:
1. There is a cache in the router that remembers a hash of the connection settings or some combination with the card's identity
2. The laptops wireless chipset has some cache of the settings.

Solution:
I had to power everything down including the router and mysteriously it started authenticating.  I'm sure I had done this prior and it didn't work.  I also reset the wireless password.

I've since re-compiled the kernel and it still works but with some complaints.

  106.751114] wlan0: associated
[  106.753731] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  112.940991] ath5k phy0: noise floor calibration failed (2412MHz)
[  116.829056] wlan0: no IPv6 routers present
[  143.601128] ath5k phy0: noise floor calibration failed (2412MHz)
[  243.909761] ath5k phy0: noise floor calibration timeout (2412MHz)
[  323.600852] ath5k phy0: noise floor calibration failed (2412MHz)
[  423.909676] ath5k phy0: noise floor calibration timeout (2412MHz)
[  663.604946] ath5k phy0: noise floor calibration failed (2412MHz)

Confucious says, a full log is better than an empty wave

---

