---
title: "HP Compaq nw8440 &amp; Intel PRO/Wireless 3945ABG in latest Ubuntu"
date: 2011-07-20
forum: Hardware
---

### Post by biggie_ on 2011-07-20
Hello,

I've got this laptop in my new job. I installed Ubuntu 11.04 and then I realized there is no wireless in network manager.

# lspci |grep -i wirel
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

There was no iwl3945 module however. So I installed package linux-backports-modules-cw-2.6.39-natty-generic and it appeared.

Then I rebooted machine and this appeared in dmesg:

```

[    8.752063] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[    8.752067] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[    8.752238] iwl3945 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.752253] iwl3945 0000:10:00.0: setting latency timer to 64
[    8.760328] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[    8.761706] Registered led device: hp::hddprotect
[    8.762091] hp_accel: driver loaded
[    8.808310] iwl3945 0000:10:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[    8.808314] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    8.808625] iwl3945 0000:10:00.0: irq 45 for MSI/MSI-X
[    8.808865] Registered led device: phy0-led
[    8.808897] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    9.136569] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xcc000-0xcffff 0xe0000-0xfffff
[    9.136637] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[    9.136697] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[    9.472222] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[    9.707746] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    9.707751] cfg80211: World regulatory domain updated:
[    9.707754] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.707757] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.707760] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.707763] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.707774] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.707777] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```However wireless is still not available in network manager. What should I do?

Thanks in advance.


EDIT:

Linux finds the wireless card:

# ip a
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 00:1c:bf:0a:92:9b brd ff:ff:ff:ff:ff:ff

---

### Post by mikewhatever on 2011-07-20
I have an HP laptop with this very card, and it worked out of the box in Natty. 2.6.39 is not the default kernel, have you installed it from backports or something? The module it uses is **iwl**, have you tried loading it manually?

---

### Post by biggie_ on 2011-07-20
> **mikewhatever said:**
> I have an HP laptop with this very card, and it worked out of the box in Natty. 2.6.39 is not the default kernel, have you installed it from backports or something? The module it uses is **iwl**, have you tried loading it manually?

Hi.

The module (iwl3945) is loaded and there is an interface for wireless card. Only network manager doesn't want to "Enable wireless" (like there was no wireless card).

The package I mentioned above is somewhere from official Ubuntu repositories (I installed Ubuntu few hours ago a I didn't add new package sources).

# dpkg -L linux-backports-modules-cw-2.6.39-2.6.38-10-generic|grep iwl
/lib/modules/2.6.38-10-generic/updates/cw-2.6.39/iwl3945.ko

Seems fine to me.


EDIT:

Now I tried running kismet and got error :(

```
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (wifi): Enabling monitor mode for iwl3945 source interface wlan0 channel 6...
FATAL: channel get ioctl failed 22:Invalid argument
Done.

```

---

### Post by biggie_ on 2011-07-20
F*ck me sideways!

When I tried:

ip link set wlan0 up

It said:

RTNETLINK answers: Operation not possible due to RF-kill

So I started looking for physical button on laptop and find the one which controls wifi xD.

Also I realized there already is iwl3945 module:

# dpkg -S /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
linux-image-2.6.38-10-generic: /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko

Problem solved. Sorry for bothering.

---

