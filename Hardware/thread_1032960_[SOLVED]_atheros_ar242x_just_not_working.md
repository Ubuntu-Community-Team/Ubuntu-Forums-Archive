---
title: "[SOLVED] atheros ar242x just not working"
date: 2009-01-06
forum: Hardware
---

### Post by sp0nge on 2009-01-06
I've been working to get the Atheros AR242x to work, but apparently I'm just not going to be able to do this on my own :(

Okay, I followed [this guide]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html") to install the updated driver, which was definitely a step in the right direction. At least wireless is an option which it wasn't before. However, after setting up a new wireless connection, it attempts to connect, then nothing! Zip, Zero, Zilch!

Any input would be appreciated. 



```
me@me:~$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```


```
me@me:~$iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

---

### Post by tuxxy on 2009-01-06
Have you tried running a dhclient from terminal also if you can see the network but cant connect it could be an encryption issue so try disable all security aswell.  Also it sounds simple but try pressing the wireless button on your router.

---

### Post by sp0nge on 2009-01-06
I did the dhclient, although I don't like the output. 

```
me@me:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
wmaster0: unknown hardware address type 801
Open a socket for LPF: Operation not permitted
```

With your recommendation about disabling the security, is this necessary? I know the settings are correct, so is there a conflict that  requires it or are you suggesting it to cover all the bases?

---

### Post by sp0nge on 2009-01-07
In continued persuit of my quest, I have continued to work on this issue to no avail! First, I instaled netwok-admin for a gui to "see" what I might be missing:

```
sudo apt-get install gnome-network-admin
```

Unfortunately, I don't think I'm missing anything on that end. The device is recognized but will not connect! I came across the backports option and thought I'd give it a try:

```
sudo aptitude update
sudo aptitude install linux-backports-modules-intrepid
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
```

Still no change. It seems as if the wireless card needs to be "activated" and the wired connection needs "deavtivated", but I don't seem to find such options..

---

### Post by sp0nge on 2009-01-07
I suppose I'll continue posting my progress (or lack thereof) until someone can step in here and show me the light!

I continued to research the issue. I have confirmed that the drivers are installed, and I've even tried the blacklist to no avail. From what I understand about ndiswrapper, it does not support this card, so I'm SOL there and officially out of ideas. I may try madwifi, but I'm wondering if I should uninstall and/or remove all the crap I've added so far in hopes of resolving this mess. 

Thanks in advance for any help.

---

### Post by sp0nge on 2009-01-07
Okay, I don't have any more ideas! I figured since I wasn't able to get this running with anything so far, I would try the madwifi solution:

download the tarball:
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
```

Unpack it:
```
tar zxvf http://snapshots.madwifi.org/madwifi...current.tar.gz
```

Move into the directory:
```
cd madwifi-hal-0.10.5.6-r3861-20080903/
```

Then run:
```
make
sudo make install
sudo modprobe ath_pci
```

Which returns:
```
FATAL: Module ath_pci not found.
```

:confused:  ](*,)  :confused:

---

### Post by sp0nge on 2009-01-09
Works now... Thanks to me.

---

