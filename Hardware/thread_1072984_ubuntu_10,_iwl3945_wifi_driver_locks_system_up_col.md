---
title: "ubuntu 10, iwl3945 wifi driver locks system up cold"
date: 2009-02-17
forum: Hardware
---

### Post by bagseed on 2009-02-17
I just upgraded from ubuntu 8.0.4 to 10 and the new iwl3945 driver for my intel pro card locks the system up cold shortly after connecting to my companies WPA/2 Enterprise Network. I have to turn off wireless or it will completely freeze on reboot when it completes the connection. This all worked fine in hardy but now my laptop is useless at work. 

system:ubuntu 10 x64
hardware: hp nx7400
kernel: 2.6.27-11-generic

As far as logs go this is all I have in  messages:

iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 17 13:41:35 Unknown kernel: [   15.293471] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Feb 17 13:41:35 Unknown kernel: [   15.400180] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Feb 17 13:41:35 Unknown kernel: [   15.714370] iwl3945 0000:10:00.0: PCI INT A disabled
Feb 17 13:41:35 Unknown kernel: [   15.766925] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
Feb 17 13:41:35 Unknown kernel: [   15.766941] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 1
6

---

### Post by Vico Vicario on 2009-02-18
Did you install linux-firmware package? Are you sure you don't have old microcode around?

Check dmesg output to see what microcode is being loaded.

[   26.698445] iwl3945 0000:10:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[   26.734605] iwl3945 0000:10:00.0: loaded firmware version 15.28.2.8

V.

---

### Post by bagseed on 2009-02-18
dmesg |grep iwl
[   17.129719] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.129723] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   17.185295] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.185310] iwl3945 0000:10:00.0: setting latency timer to 64
[   17.185327] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   17.251791] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   17.253193] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.438797] iwl3945 0000:10:00.0: PCI INT A disabled
[   36.313176] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   36.313346] iwl3945 0000:10:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   36.313648] firmware: requesting iwlwifi-3945-1.ucode
[   36.446752] Registered led device: iwl-phy0:radio
[   36.447154] Registered led device: iwl-phy0:assoc
[   36.447418] Registered led device: iwl-phy0:RX
[   36.447673] Registered led device: iwl-phy0:TX
[   80.454806] iwl3945: Radio Frequency Kill Switch is On:
[   80.942014] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   80.945043] iwl3945: MAC is in deep sleep!
[   80.991719] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   80.995678] iwl3945: MAC is in deep sleep!
[   81.051293] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   81.055287] iwl3945: MAC is in deep sleep!
[   81.214365] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   81.230740] iwl3945 0000:10:00.0: PCI INT A disabled


I dont remember having issues with wep or wpa but wpa/2 enterprise seems to lock it up quick...there are other reporting problems with the iwl3945 driver locking there systems up. I guess I will have to format and go back to 8.04 because I cant get any work done like this. :(

Have a great day!

---

### Post by bagseed on 2009-02-18
So I am typing this from the house wifi ...which is a dlink AP using WPA just fine. The system has not locked up and it also works fine at my friends house using wep. So the only differences is wpa vs wpa enterprise. Hardy 8.04 worked just fine on the wpa enterprise network at work. Dont know whats going on...also on a side note...since the upgrade from 8.04 to 10 the dam wifi lights blink when transmitting and receiving and its driving me freaking crazy.

---

