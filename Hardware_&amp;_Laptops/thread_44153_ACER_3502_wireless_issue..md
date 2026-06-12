---
title: "ACER 3502 wireless issue."
date: 2005-06-24
forum: Hardware &amp; Laptops
---

### Post by Mark_logan on 2005-06-24
Okay, I have the built in card working and showing  in the Networking window as active... but what now? I can't seem to get any use of it. I imagine I need something to find the networks... any ideas?

---

### Post by thechitowncubs on 2005-06-24
sudo iwlist eth1 scan

---

### Post by Mark_logan on 2005-06-24
# sudo iwlist wlan0 scan
wlan0     No scan results
----------------------------------------
 # ndiswrapper -l
Installed ndis drivers:
net5211 driver present, hardware present
----------------------------------------
lspci
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
----------------------------------------
 # ndiswrapper -d 0000:00:0b.0 net5211.inf
'0000:00:0B.0' is not a valid PCIID

-------------------------------------------
shows up fine as wlan0 in the Network settings window though..
Any other ideas?

---

### Post by ssck on 2005-06-25
[QUOTE=Mark_logan]# sudo iwlist wlan0 scan
wlan0     No scan results
----------------------------------------
 # ndiswrapper -l
Installed ndis drivers:
net5211 driver present, hardware present
----------------------------------------
lspci
0000:00:0b.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 001a (rev 01)
----------------------------------------
 # ndiswrapper -d 0000:00:0b.0 net5211.inf
'0000:00:0B.0' is not a valid PCIID

-------------------------------------------
shows up fine as wlan0 in the Network settings window though..
Any other ideas?[/QUOTE]


do you have eth0 up ? if so, sudo ifdown eth0 and then try iwlist wlan0 scan again

---

### Post by Mark_logan on 2005-06-25
Okay, I got it working and  I can scan for networks... thanks!
Now... how does one connect to these networks?

Ps. It turns out that the light that denote the card as being on should be sowly flashing if it is indeed working. The light is also the on/off button.

---

### Post by phantom on 2005-06-25
[QUOTE=Mark_logan]
Now... how does one connect to these networks?
[/QUOTE]

iwconfig wlan0 essid "name of network"

---

### Post by Mark_logan on 2005-06-25
Okay... now I am getting the following:

#iwconfig
wlan0     IEEE 802.11b  ESSID:"waypoint"
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:00:B2:B3:54:DB
          Bit Rate:11 Mb/s
          Encryption key:off
          Power Management:off
          Link Quality:63/100  Signal level:-30 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Still no connection, I am sure this network is working, becuase I use it from my other laptop no problem. However, I cannot ping the 192.168.0.1, nor can I access anything on the internet.

---

### Post by ssck on 2005-06-26
[QUOTE=Mark_logan]Okay... now I am getting the following:

#iwconfig
wlan0     IEEE 802.11b  ESSID:"waypoint"
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:00:B2:B3:54:DB
          Bit Rate:11 Mb/s
          Encryption key:off
          Power Management:off
          Link Quality:63/100  Signal level:-30 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Still no connection, I am sure this network is working, becuase I use it from my other laptop no problem. However, I cannot ping the 192.168.0.1, nor can I access anything on the internet.[/QUOTE]

what is your ifconfig and the /etc/network/interface file info ? can you paste the results here ? you have to be absolutely sure the wireless card is on.for my acer travelmate 2300, even if it is not on, when the wlan0 is up, it will be light up but it will be blinking instead.if the wireless card is switched on and wlan0 is up, it will be lighted all the time.you could also use gtkwifi software which you can install.it will detect the ap's for you and get you connected

---

### Post by Mark_logan on 2005-06-27
Okay, I actually have everything figured out, it was just my process was off.
modprobe ndiswrapper
iwlist (get the info for the connection)
iwconfig wlan0 essid "name" mode Managed channel 6
dhclient wlan0

And I am ON! :) Everything is all fixed, and thank you everyone for helping out.
Now... on to my sound issue... :)

---

