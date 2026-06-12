---
title: "Acer Aspire 5810TZ / Ubuntu 9.10 Wifi issue."
date: 2010-02-14
forum: Hardware
---

### Post by 14tjoyce on 2010-02-14
I have Ubuntu 9.10 installed on an Acer Aspire 5810TZ, 3gb ram, 320gb hdd. When i first installed Ubuntu the wifi worked fine but then i went away for the weekend and when i came back the wifi wouldnt connect. The little network indicator just spun for a while then told me i was disconnected. I tried re-installing Ubuntu and it still wont work. Is there anything i can do? Also when i plugg a ethernet cable right into the side it spins and then tells me i am disconnected

---

### Post by ankit singh on 2010-02-14
please post your log files.

---

### Post by 14tjoyce on 2010-02-14
Where would i find these log files?

---

### Post by ankit singh on 2010-02-14
System-adminis..-log file viewer-syslog


While you are viewing this file,click on the network indicator and see what logs are filed in.

---

### Post by 14tjoyce on 2010-02-14
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  dhclient started with pid 2562
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
2010-02-14 14:46:00 Tom-PC dhclient Listening on LPF/wlan0/00:24:2c:59:b8:d1
2010-02-14 14:46:00 Tom-PC dhclient Sending on   LPF/wlan0/00:24:2c:59:b8:d1
2010-02-14 14:46:00 Tom-PC dhclient Sending on   Socket/fallback
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  DHCP: device wlan0 state changed normal exit -> preinit
2010-02-14 14:46:03 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
2010-02-14 14:46:09 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
2010-02-14 14:46:21 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
2010-02-14 14:46:36 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): DHCP transaction took too long, stopping it.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2562
2010-02-14 14:46:46 Tom-PC kernel [ 2028.959911] wlan0: disassociating by local choice (reason=3)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): device state change: 7 -> 9 (reason 5)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) failed for access point (JOYCE)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Marking connection 'JOYCE' invalid.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) failed.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): device state change: 9 -> 3 (reason 0)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): deactivating device (reason: 0).
2010-02-14 14:46:46 Tom-PC wpa_supplicant[1152] CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
2010-02-14 14:46:58 Tom-PC wpa_supplicant[1152] CTRL-EVENT-SCAN-RESULTS

---

### Post by ankit singh on 2010-02-14
> **14tjoyce said:**
> 2010-02-14 14:46:00 Tom-PC NetworkManager <info>  dhclient started with pid 2562
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
2010-02-14 14:46:00 Tom-PC dhclient Listening on LPF/wlan0/00:24:2c:59:b8:d1
2010-02-14 14:46:00 Tom-PC dhclient Sending on   LPF/wlan0/00:24:2c:59:b8:d1
2010-02-14 14:46:00 Tom-PC dhclient Sending on   Socket/fallback
2010-02-14 14:46:00 Tom-PC NetworkManager <info>  DHCP: device wlan0 state changed normal exit -> preinit
2010-02-14 14:46:03 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
2010-02-14 14:46:09 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
2010-02-14 14:46:21 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
2010-02-14 14:46:36 Tom-PC dhclient DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): DHCP transaction took too long, stopping it.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2562
2010-02-14 14:46:46 Tom-PC kernel [ 2028.959911] wlan0: disassociating by local choice (reason=3)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): device state change: 7 -> 9 (reason 5)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) failed for access point (JOYCE)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Marking connection 'JOYCE' invalid.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) failed.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): device state change: 9 -> 3 (reason 0)
2010-02-14 14:46:46 Tom-PC NetworkManager <info>  (wlan0): deactivating device (reason: 0).
2010-02-14 14:46:46 Tom-PC wpa_supplicant[1152] CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
2010-02-14 14:46:58 Tom-PC wpa_supplicant[1152] CTRL-EVENT-SCAN-RESULTS



I think you should reconfigure your network.
IT is clearly stating that it is not getting activated for the given access point

---

### Post by 14tjoyce on 2010-02-14
Thank you for your help

---

### Post by ankit singh on 2010-02-14
If the problem is solved mark this thread as "solved".
You can do this by using the thread tools

---

### Post by 14tjoyce on 2010-02-15
As it turned out all i had to do was reset the router lol

---

