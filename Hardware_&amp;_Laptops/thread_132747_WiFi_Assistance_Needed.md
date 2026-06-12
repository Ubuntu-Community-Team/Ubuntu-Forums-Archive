---
title: "WiFi Assistance Needed"
date: 2006-02-18
forum: Hardware &amp; Laptops
---

### Post by PenguinBoy on 2006-02-18
I have an IBM Thinkpad R40, Type 2723-3XU.  I have an Intel Corp PRO/Wireless LAN 2100 3B Mini PCI Adapter.  I have ran the Kubuntu Hedgehog since its release.  It recognized the wifi on installation and I am able to wirelessly compute with no problem whatsoever.  I installed the Kubuntu Badger when it was released and it never recognized my wifi.  I even installed/configured ndswrapper and it still did not permit me to wirlessly compute.  I reinstalled the Hedgehog but would like to use Breezy Badger.  Her is the rersults when I ran the following commands form terminal:

dunefan@laptop:~$ lsmod | grep ipw
ipw2100                78076  0
firmware_class          9728  1 ipw2100
ieee80211              21252  1 ipw2100
dunefan@laptop:~$ lsmod | grep ieee
ieee80211              21252  1 ipw2100
ieee80211_crypt         5832  1 ieee80211
ieee1394              100408  2 ohci1394,sbp2
dunefan@laptop:~$ lwconfig
bash: lwconfig: command not found
dunefan@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11b  ESSID:"default"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:83:82:E3
          Bit Rate=11 Mb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

Any help that you can offer is much appreciated.

---

### Post by Mikecore on 2006-02-18
the driver is already install it looks like all you should need to do is setup your AP in  "System" then "Administration" then "networking" 

setup your wirless card there with the correct essid you want to connect to.

---

### Post by gnutux on 2006-02-19
try starting ndisgtk, it should guide you the rest of the way.

gnutux

---

