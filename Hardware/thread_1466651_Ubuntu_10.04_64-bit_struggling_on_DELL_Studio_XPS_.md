---
title: "Ubuntu 10.04 64-bit struggling on DELL Studio XPS 17"
date: 2010-04-30
forum: Hardware
---

### Post by cisforcojo on 2010-04-30
Has anyone else tried Ubuntu 10.04 64-bit on a DELL Studio XPS 17?

First impression is it looks really put together and I like the social networking integration but my wireless card did not work out of the box. (Wireless card is Intel WiFi 5300 AGN) Wireless was simply disabled and I could not enable it. I could physically toggle the WiFi via the WiFi touchbutton on the keypad.

Quad processors (all 8 threads) were detected but it ran really really hot and the battery drained really fast. I estimate a lifespan of about 45 minutes. 

Keyboard backlight did not work.

I couldn't take anymore of the heat, so to speak, so I dropped back into Win7 to evaluate.

Anyone else had similar issues?

EDIT: I was not patient enough. WiFi works, backlight works. Only problem remaining is it's running a little hot.

---

### Post by zgornel on 2010-05-04
The Dell quad-cores run really hot. There are some reviews on [www.notebookcheck.net](www.notebookcheck.net) and other sites where they talk about the problem. Basically the whole cooling system is underpowered ....

---

### Post by mikelsk on 2010-05-10
[cisforcojo]("http://ubuntuforums.org/member.php?u=168901"),

I tried Ubuntu 10.04 (64 bit) on Dell Studio 1457 , it has the same wireless card (Intel 5300 AGN), and I have the same problem - wireless is disabled and yet I cannot enable it. There is a keyboard button for switching it on/off, but it does not do anything. 
Can you, please, tell a bit more details about how you managed to the get wireless to work on that machine? What is the driver that it uses?

---

### Post by cisforcojo on 2010-05-12
Yes, I can really vouch for the Quad-cores running too hot. Where I live now in China, it's about 25 degrees Celcius and if I play a game, it will almost certainly overheat and shutdown within 15 minutes. I just bought a cooling pad but it seems to be entirely infeffective.

As for getting my WiFi to work, honestly, I did nothing. It all worked after a reboot. 

The wireless card is running on device wlan with the driver 'iwlagn'. Just wait until you see the flashing WiFi light to signal traffic ;) You'll be tweaking soon to turn that off as well.

Since I actually didn't do ANYTHING to get it to work, I'm not sure how much more help I can be but if you need any further help, let me know.

```

$ dmesg | grep -e iwl -e wlan
\[   13.698981] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.698984] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.699059] iwlagn 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.699090] iwlagn 0000:05:00.0: setting latency timer to 64
[   13.699185] iwlagn 0000:05:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   13.754224] iwlagn 0000:05:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.754314] iwlagn 0000:05:00.0: irq 36 for MSI/MSI-X
[   13.763277] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.411412] iwlagn 0000:05:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   14.520748] iwlagn 0000:05:00.0: loaded firmware version 8.24.2.12
[   14.713708] Registered led device: iwl-phy0::radio
[   14.713728] Registered led device: iwl-phy0::assoc
[   14.713743] Registered led device: iwl-phy0::RX
[   14.713758] Registered led device: iwl-phy0::TX
[   14.965004] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.503833] wlan0: deauthenticating from 00:15:e9:05:c4:e2 by local choice (reason=3)
[   38.503973] wlan0: direct probe to AP 00:15:e9:05:c4:e2 (try 1)
[   38.507536] wlan0: direct probe responded
[   38.507543] wlan0: authenticate with AP 00:15:e9:05:c4:e2 (try 1)
[   38.509407] wlan0: authenticated
[   38.509439] wlan0: associate with AP 00:15:e9:05:c4:e2 (try 1)
[   38.511774] wlan0: RX AssocResp from 00:15:e9:05:c4:e2 (capab=0x431 status=0 aid=1)
[   38.511778] wlan0: associated
[   38.516447] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.475726] wlan0: no IPv6 routers present
[10839.732942] bridge-wlan0: is a Wireless Adapter
[10839.732944] bridge-wlan0: up
[10839.732947] bridge-wlan0: attached
[10889.664021] bridge-wlan0: disabling the bridge
[10889.687738] bridge-wlan0: down
[10889.687752] bridge-wlan0: detached
[10922.176307] bridge-wlan0: is a Wireless Adapter
[10922.176313] bridge-wlan0: up
[10922.176318] bridge-wlan0: attached
[13221.521074]  [<ffffffffa0424953>] ? iwl_led_brightness_set+0x63/0x80 [iwlcore]
[13221.668942]  [<ffffffffa0424969>] ? iwl_led_brightness_set+0x79/0x80 [iwlcore]
[13272.153584]  [<ffffffffa041bc97>] ? iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13272.153597]  [<ffffffffa041bc97>] iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13272.153605]  [<ffffffffa041cffb>] iwl_rx_replenish_now+0x1b/0x30 [iwlcore]
[13272.153612]  [<ffffffffa0450378>] iwl_rx_handle+0x288/0x2f0 [iwlagn]
[13272.153618]  [<ffffffffa04509d0>] iwl_irq_tasklet+0x140/0x4f0 [iwlagn]
[13272.172266] iwlagn 0000:05:00.0: Failed to allocate SKB buffer with GFP_ATOMIC. Only 0 free buffers remaining.
[13272.623975]  [<ffffffffa041bc97>] ? iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13272.623984]  [<ffffffffa041bc97>] iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13272.623989]  [<ffffffffa041cffb>] iwl_rx_replenish_now+0x1b/0x30 [iwlcore]
[13272.623994]  [<ffffffffa0450378>] iwl_rx_handle+0x288/0x2f0 [iwlagn]
[13272.623997]  [<ffffffffa04509d0>] iwl_irq_tasklet+0x140/0x4f0 [iwlagn]
[13272.640448] iwlagn 0000:05:00.0: Failed to allocate SKB buffer with GFP_ATOMIC. Only 0 free buffers remaining.
[13275.844198]  [<ffffffffa041bc97>] ? iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13275.844218]  [<ffffffffa041bc97>] iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13275.844232]  [<ffffffffa041cffb>] iwl_rx_replenish_now+0x1b/0x30 [iwlcore]
[13275.844242]  [<ffffffffa0450378>] iwl_rx_handle+0x288/0x2f0 [iwlagn]
[13275.844252]  [<ffffffffa04509d0>] iwl_irq_tasklet+0x140/0x4f0 [iwlagn]
[13277.427042]  [<ffffffffa041bc97>] ? iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13277.427060]  [<ffffffffa041bc97>] iwl_rx_allocate+0x197/0x2f0 [iwlcore]
[13277.427068]  [<ffffffffa041cffb>] iwl_rx_replenish_now+0x1b/0x30 [iwlcore]
[13277.427075]  [<ffffffffa0450378>] iwl_rx_handle+0x288/0x2f0 [iwlagn]
[13277.427081]  [<ffffffffa04509d0>] iwl_irq_tasklet+0x140/0x4f0 [iwlagn]
[13277.455285] iwlagn 0000:05:00.0: Failed to allocate SKB buffer with GFP_ATOMIC. Only 0 free buffers remaining.
[13277.455728]  [<ffffffffa0424969>] ? iwl_led_brightness_set+0x79/0x80 [iwlcore]

```

---

### Post by cisforcojo on 2010-05-14
Spoke too soon. A recent update broke my wireless. I'll let you know if I come across anything to fix it.

EDIT: I believe this is the bug posted:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553572?comments=all](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553572?comments=all)

EDIT 2: I was receiving this error:
```

$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

```

rfkill showed this (and I still have no idea what is blocking it):
```

$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

Solution:
```

sudo rfkill block all
sudo rfkill unblock all
sudo modprobe -r iwlagn
sudo modprobe iwlagn
sudo ifconfig wlan0 up

```

Done.

---

