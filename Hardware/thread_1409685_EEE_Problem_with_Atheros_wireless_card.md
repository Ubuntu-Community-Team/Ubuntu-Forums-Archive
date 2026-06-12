---
title: "EEE Problem with Atheros wireless card"
date: 2010-02-17
forum: Hardware
---

### Post by Nalroff on 2010-02-17
I have a problem with wpa_supplicant. The atheros AR9285 adapter in my EEE does not seem to work with wpa_supplicant, but it worked fine when I had KDE working with Kubuntu using network-manager. I wanted to un-bork my KDM settings by uninstalling and reinstalling, but after the uninstall, I can't get connected to the internet, and hence, can't download the package files to install GNOME.

I run:

```

wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf

```

and my wpa_supplicant.conf file has this:

```

network={
  ssid="MySSID"
  scan_ssid=1
  key_mgmt=WPA-PSK
  psk="14M1337"
}

```

and the output where wpa_supplicant poops on itself is here:

```

Wireless event: new AP: 00:1a:70:d8:b6:01
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:00:00:00:00:00
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request

```

And then there's a whole bunch of RTM_NEWLINK stuff, but looking at it I think that's ifdown/ifup-esque stuff. Any help is much appreciated. The sooner the better. Need this for work tomorrow :-P

---

