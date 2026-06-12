---
title: "Trendnet TEW-424UB (3.0R) USB Wireless"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by brucehohl on 2008-02-06
The Trendnet TEW-424UB (3.0R) is an inexpensive (USD 20) USB wireless adapter. It works with Ubuntu 6.06 (and later?) using the ndiswrapper as follows:

(1) The install CD for my version included the driver inside the Windows setup.exe. I did not find a way to extract the driver from the setup.exe file within Linux so I installed the setup.exe on Windows XP and retrieved the files net8187b.inf and RTL8187B.sys.

(2) Copy those files to Ubuntu.

(3) Here are the command line steps to get connected to an unsecured network.

INSTALL SOFTWARE:
 # aptitude install ndiswrapper-utils

LOAD DRIVER AND MODULE:
 # ndiswrapper -i net8187b.inf
 # modprobe ndiswrapper

FIND INTERFACE AND ACCESS POINT:
 # iwconfig
 # iwlist wlan0 scan (find essid)

STANDARD CONNECTION:
 # iwconfig  wlan0 essid <found essid>
 # dhclient wlan0

(4) To connect to an ENCRYPTED CONNECTION:

INSTALL SOFTWARE:
 # aptitude install ndiswrapper-utils
 # aptitude install wpasupplicant

LOAD DRIVER AND MODULE:
 # ndiswrapper -i net8187b.inf
 # modprobe ndiswrapper

FIND INTERFACE AND ACCESS POINT:
 # iwconfig
 # iwlist wlan0 scan (find essid)

Add following to  /etc/wpa_supplicant.conf 
network=
  {
  ssid="network_name"
  psk="network_password"
  key_mgmt=WPA-PSK
  proto=WPA
  }

Add following to  /etc/default/wpasupplicant 
  ENABLED=1

ENCRYPTED CONNECTION:
# wpa_supplicant -Bw -Dndiswrapper -c/etc/wpa_supplicant.conf -iwlan0
# dhclient wlan0

---

