---
title: "Samsung N140 - WPA authentication problems"
date: 2009-10-19
forum: Hardware
---

### Post by Dr_Bobby on 2009-10-19
Hi,

I have a delicious new N140 and have proceeded to install CrunchBang on it.  CrunchBang is a lightweight distro built on Ubuntu, hence asking here for advice.

Wireless was made to work using ndiswrapper with the RTL819xp.inf driver from the Samsung website.  No probelms connecting to unencrypted and WEP secured connections using the network-admin GUI.

WPA and WPA2 is posing a bigger problem.  I have done the following:

Checked I have wpa_supplicant installed
Edited /etc/network/interfaces
Added the following:[INDENT]```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid "My Network Name"
wpa-ap-scan 1
wpa-proto WPA RSN
wpa-pairwise TKIP CCMP
wpa-group TKIP CCMP
wpa-key-mgmt WPA-PSK
wpa-psk "HEX KEY FROM WPA_PASSPHRASE"

```[/INDENT]Generated my passkey using:

```
wpa_passphrase "My Network Name" myasscipassword
```Restarted networking:

```
sudo /etc/init.d/networking restart
```At this point it runs through to DHCPDISCOVER and pings away until timing out.

Alternatively, if I place the same information in wpa_supplicant.conf and run:

```
sudo wpa_supplicant -B -d -iwlan0 -Dwext -c/etc/wpa_supplicant.conf
```It tends to run through a few authentication attempts before giving me the "WPA key negotiation complete" message.  At which point I don't know what to do...

So, my questions are:[INDENT]1.  Is this the correct way to go about setting up WPA?  I have several home and work WPA-networks I want to move between.  Does editing wpa_supplicant.conf have the advantage over editing /etc/networking/interfaces in that case?

2.  Should I attempt using network-manager or network-admin to set up WPA?  I have read they can interfere so removed network-manager from my installation.

3.  Is generating the passphrase using wpa_passphrase the best way?  My network name contains spaces (which I cannot change as it is a work network) and I have heard this can complicate key generation.

[/INDENT]I piped the outputs of all of the above to txt files but cannot find a way to access them from my windows installation (which has wireless working :-(  ) so cannot post them.

Thanks in advance!

---

### Post by Dr_Bobby on 2009-10-20
OK, in time honoured fashion I fixed this myself by reinstalling, updating kernel to latest, THEN installing wireless drivers using ndiswrapper and everything worked through nm-applet/networkmanager after that.

---

### Post by bobbyuser on 2009-12-30
> **Dr_Bobby said:**
> OK, in time honoured fashion I fixed this myself by reinstalling, updating kernel to latest, THEN installing wireless drivers using ndiswrapper and everything worked through nm-applet/networkmanager after that.

Dr_Bobby,

I'm also looking to run crunchbang on my N140... What kernel did you upgrade to/are you running? Can you post your kernel .config?

What is your wpa_supplicant version as well?

I've been scratching my head for a bit on this as I am having the same wpa wifi related connectivity issues... any incite / help you could provide would be greatly appreciated! Thanks!

---

