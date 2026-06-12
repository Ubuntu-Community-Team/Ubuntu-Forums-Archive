---
title: "Wifi on Dell XPS 15"
date: 2013-08-04
forum: Hardware
---

### Post by ElfenKiller on 2013-08-04
How can the wifi speed in ubuntu 12.04 be improved on a dell xps 15 laptop?

iwconfig gives:
> wlan0     IEEE 802.11abgn  ESSID:"Hausboot46"            Mode:Managed  Frequency:2.412 GHz  Access Point: 34:08:04:15:E5:44   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:97   Missed beacon:0

/sys/class/net/wlan0/device/driver/module/drivers gives: pci:iwlwifi

The wifi hardware is: Intel Corporation Centrino Advanced-N 6230

---

### Post by TheFu on 2013-08-04
I ahve this laptop. Fastest that I ever connect with 2ft distance between the router (N-300) and the laptop is 72Mbps.  This wifi chip is a cheap N version. I wish I would have paid the extra $10 to get the upgraded wifi miniPCI card.  OTOH, I barely use wifi - always GigE wired connected, so it isn't the end of the world to me.

---

### Post by ElfenKiller on 2013-08-06
Yes, I'm also using a cable now. I'm just wondering because the wifi speed using Win 7 is so much faster ...

---

### Post by varunendra on 2013-08-07
> **ElfenKiller said:**
> iwconfig gives:
/sys/class/net/wlan0/device/driver/module/drivers gives: pci:**iwlwifi**

There are many different parameters available for this driver, most commonly used being "swcrypto=1" and "11n_disable=1". You may try one or both of these to see if they help. The 11n_disable=1 parameter disables N-channel supporting high speeds (more than 54Mbps), but still better than 'unusable' speeds if that is what you are getting at the moment.

Please try -
```
echo "options iwlwifi swcrypto=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

If the second command above gives any errors, just do a reboot and the driver will load with the "swcrypto=1" parameter on the next boot. If it does not help, replace the "swcrypto=1" with "11n_disable=1" in the next attempt. You can also try both at once (like - "11n_disable=1 swcrypto=1"). If none of the above help, you can return to default by deleting the .conf file created by the first command -
```
sudo rm /etc/modprobe.d/iwlwifi.conf
```

If the above two parameters don't seem to help, please follow the "Wireless Script" link in my signature and post back the full diagnostics report as asked in the linked post. Maybe we can find some useful clues in the report to be able to suggest you more options.

---

