---
title: "Network Manager"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by Wermut on 2006-06-29
I installed the Gnome network manager. Just, how does it work?

Clicking it does not show any wireless networks.

The manpages are not very verbose and neither is the official website.

Do I have to do some configuration or something similar?

---

### Post by FuturePast on 2006-06-29
I tried this as well yesterday with the same results.
Apparently it should "just work" :-)

---

### Post by PvSinNL on 2006-06-29
AFAIK, you need to comment out the entries for your "physical" network cards (interfaces) in **/etc/network/interfaces**, otherwise Network Manager won't be able to control them.
In other words, the only "active" lines (i.e., lines not starting with a #) in /etc/network/interfaces should be:
```
auto lo
iface lo inet loopback
```
Oh, and you need to have the "Notification Area" active in one of your panels, otherwise the NM applet won't be visible...

---

### Post by m.m.shahabi on 2006-06-29
Thanx. I had this problem but it shure helps.

---

### Post by Wermut on 2006-07-03
So far I got wireless network working and I also installed the plugin for VPN support.

Again, how does it work???

I enter the information for the vpn network... and then... nothing happens.

Is there a way I can tell it to simply start vpnc after connecting to certain networks?

(This tool does not adhere to the "It justs works" philosophy very strongly")

---

### Post by dureyes on 2006-07-23
> **PvSinNL said:**
> AFAIK, you need to comment out the entries for your "physical" network cards (interfaces) in **/etc/network/interfaces**, otherwise Network Manager won't be able to control them.
In other words, the only "active" lines (i.e., lines not starting with a #) in /etc/network/interfaces should be:
```
auto lo
iface lo inet loopback
```
Oh, and you need to have the "Notification Area" active in one of your panels, otherwise the NM applet won't be visible...

Thank you this solved my problem completely !!  I can now choose what ever network shows up on network manager.

---

### Post by boobytrapped on 2006-07-23
> **Wermut said:**
> So far I got wireless network working and I also installed the plugin for VPN support.


I haven't been able to figure out how to enable the VPN support with NetworkManager.  Which plugin are you talking about here?

---

### Post by BIGtrouble77 on 2006-07-24
Does anyone know how to set a static ipaddress?  I want my wired address to be static and my wireless dynamic.

---

### Post by NeoChaosX on 2006-07-25
> **BIGtrouble77 said:**
> Does anyone know how to set a static ipaddress?  I want my wired address to be static and my wireless dynamic.

You can't with NetworkManager. If you want your wired to be static, you have to configure it with GNOME's network settings and can't use it with NM.

---

### Post by michaeljustman on 2006-12-30
I'm having continuous issues with network-manager.

I've done a fresh install of Ubuntu twice now in order to get my wifi working again. When I install extract the firmware from the window's driver on a fresh install I am able to modprobe bcm43xx to enable the light on my laptop and wireless works fine with network-manager.

After about four or five days my wireless just stops working. One day I can connect and then, all of a suddon it just stops connecting.

The network manager keeps timing out when I try to connect to my wireless, even when I turn off encryption. This is so frustrating. I don't know what to do.

Any ideas on what I should check or do would be very appreciated.

---

