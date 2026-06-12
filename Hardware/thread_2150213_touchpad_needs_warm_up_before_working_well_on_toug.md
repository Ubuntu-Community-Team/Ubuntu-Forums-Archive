---
title: "touchpad needs warm up before working well on toughbook 52"
date: 2013-05-31
forum: Hardware
---

### Post by sowdust on 2013-05-31
Hello everyone,

I have a Panasonic Toughbook CF-52 that has a strange (to me) problem with its touchpad: while using windows it works well from the beginning, when logging into xubuntu the touchpad is at first very slow and unusable. It take some minutes of use for it to "warm up" and start acting correctly.
Also, sometimes, its sensitivity seems to decrease and I have to put more pressure in order to make the cursor start moving.

I have tried changing max/min speed and acceleration both from console and the gui settings manager but the problem at login remains. 

I thought of a hardware problem but it is highly unprobable since all works fine with win... any ideas?

thanks in advance!

---

### Post by sowdust on 2013-10-04
Hi to everyone, I'm trying to bump this thread since I couldn't find a solution during these months.
I think there is a proportional link between how low the temperature is and how slow the mouse pointer is (also how long it takes it to go back to real time speed).
I also noticed that the pointer becomes slow again after I use keyboard shortcuts to navigate within a window, but in this case it just pauses working for an instant and then resumes its normal speed.

---

### Post by tgalati4 on 2013-10-04
Any touchpad-related error messages?

Open a terminal:

```
dmesg | tail -100
```

Linux tends to use edge sliding where Windows might not, so carefully clean all of the edges of the touchpad with a Q-tip and some alcohol.  Don't saturate, just enough to clean the dirt.

---

### Post by sowdust on 2013-10-04
> **tgalati4 said:**
> Any touchpad-related error messages?

hi tgalati4, thanks for the reply. This is the output I cannot interpret:

```
[   13.691357]  excluding 0xc0000-0xd3fff 0xe4000-0xfffff[   13.691381] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   13.691390]  excluding 0xa0000000-0xa0ffffff
[   13.691407] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   13.691416]  excluding 0x60000000-0x60ffffff
[   13.711325] kvm: disabled by bios
[   13.730467] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   13.730471] Copyright(c) 2003-2012 Intel Corporation
[   13.730627] iwlwifi 0000:0b:00.0: irq 46 for MSI/MSI-X
[   13.924136] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   14.021648] iwlwifi 0000:0b:00.0: loaded firmware version 8.83.5.1 build 33692
[   14.057228] [drm] Initialized drm 1.1.0 20060810
[   14.210952] iwlwifi 0000:0b:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   14.210957] iwlwifi 0000:0b:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   14.210959] iwlwifi 0000:0b:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   14.210961] iwlwifi 0000:0b:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   14.210963] iwlwifi 0000:0b:00.0: CONFIG_IWLWIFI_P2P disabled
[   14.210966] iwlwifi 0000:0b:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   14.211032] iwlwifi 0000:0b:00.0: L1 Disabled; Enabling L0S
[   14.211412] iwlwifi 0000:0b:00.0: RF_KILL bit toggled to enable radio.
[   14.351461] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.362622] psmouse serio2: synaptics: Touchpad model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04711/0x200000/0x0, board id: 3655, fw id: 496518
[   14.402592] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input5
[   14.517137] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.536818] i915 0000:00:02.0: setting latency timer to 64
[   14.591759] i915 0000:00:02.0: irq 48 for MSI/MSI-X
[   14.591772] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.591773] [drm] Driver supports precise vblank timestamp query.
[   14.591813] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.600493] type=1400 audit(1380913105.441:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=774 comm="apparmor_parser"
[   14.600668] type=1400 audit(1380913105.441:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=718 comm="apparmor_parser"
[   14.600893] type=1400 audit(1380913105.441:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=774 comm="apparmor_parser"
[   14.601064] type=1400 audit(1380913105.441:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=718 comm="apparmor_parser"
[   14.601115] type=1400 audit(1380913105.441:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=774 comm="apparmor_parser"
[   14.601287] type=1400 audit(1380913105.441:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=718 comm="apparmor_parser"
[   14.601721] type=1400 audit(1380913105.441:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=707 comm="apparmor_parser"
[   14.602117] type=1400 audit(1380913105.441:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=707 comm="apparmor_parser"
[   14.602339] type=1400 audit(1380913105.441:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=707 comm="apparmor_parser"
[   14.708052] [drm] GMBUS [i915 gmbus dpc] timed out, falling back to bit banging on pin 4
[   14.725976] cfg80211: World regulatory domain updated:
[   14.725988] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.725991] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.725993] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.725995] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.725997] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.725999] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.729205] fbcon: inteldrmfb (fb0) is primary device
[   15.448131] Console: switching to colour frame buffer device 160x50
[   15.451084] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   15.451087] i915 0000:00:02.0: registered panic notifier
[   15.459520] acpi device:01: registered as cooling_device2
[   15.459652] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.460342] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   15.461270] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.005638] EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
[   16.006232] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   16.722085] EXT4-fs (sda8): warning: maximal mount count reached, running e2fsck is recommended
[   16.725931] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   17.345648] init: failsafe main process (872) killed by TERM signal
[   18.007099] type=1400 audit(1380913108.845:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=940 comm="apparmor_parser"
[   22.648990] Bluetooth: RFCOMM TTY layer initialized
[   22.649006] Bluetooth: RFCOMM socket layer initialized
[   22.649008] Bluetooth: RFCOMM ver 1.11
[   22.791262] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.791266] Bluetooth: BNEP filters: protocol multicast
[   22.791276] Bluetooth: BNEP socket layer initialized
[   23.065019] ppdev: user-space parallel port driver
[   23.083021] init: avahi-cups-reload main process (1290) terminated with status 1
[   23.210619] audit_printk_skb: 48 callbacks suppressed
[   23.210624] type=1400 audit(1380913114.049:28): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1365 comm="apparmor_parser"
[   23.211114] type=1400 audit(1380913114.049:29): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1365 comm="apparmor_parser"
[   28.332423] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   28.436114] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
[   28.436259] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.436611] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.600008] iwlwifi 0000:0b:00.0: L1 Disabled; Enabling L0S
[   28.600409] iwlwifi 0000:0b:00.0: Radio type=0x1-0x2-0x0
[   28.800289] iwlwifi 0000:0b:00.0: L1 Disabled; Enabling L0S
[   28.800671] iwlwifi 0000:0b:00.0: Radio type=0x1-0x2-0x0
[   28.933642] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.934075] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.763868] postgres (1938): /proc/1938/oom_adj is deprecated, please use /proc/1938/oom_score_adj instead.
[   35.469301] wlan0: authenticate with 00:90:a2:54:5a:8b
[   35.483323] wlan0: send auth to 00:90:a2:54:5a:8b (try 1/3)
[   35.486558] wlan0: authenticated
[   35.486695] iwlwifi 0000:0b:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   35.486699] wlan0: waiting for beacon from 00:90:a2:54:5a:8b
[   35.656024] wlan0: associate with 00:90:a2:54:5a:8b (try 1/3)
[   35.660031] wlan0: RX AssocResp from 00:90:a2:54:5a:8b (capab=0x431 status=0 aid=1)
[   35.683326] wlan0: associated
[   35.683366] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   35.683449] cfg80211: Calling CRDA for country: IT
[   35.687846] cfg80211: Regulatory domain changed to country: IT
[   35.687850] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   35.687852] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   35.687854] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   35.687856] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   35.687858] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   36.064248] wlan0: Limiting TX power to 20 (20 - 0) dBm as advertised by 00:90:a2:54:5a:8b
[   46.749764] init: plymouth-stop pre-start process (2440) terminated with status 1



```

---

### Post by sowdust on 2013-11-27
any idea why this might be happening? 
I still haven't been able to solve it. I have notice however that it happens the most whenever I somehow switch from "mouse mode" to "keyboard mode":
for instance if I am browsing the web and typing text in a form as I'm doing now, when I decide to move my mouse pointer it takes it two-three second to follow my fingers' movements on the touchpad. Same happens when typing the URL of a website, or writing emails... and it is not even restricted to the browser, it is the same in all of this kind of situations, also in regular applications such as a login prompt or a gnumeric spreadsheet.

Apart from being an annoying behaviour, I am a little concerned about the cause that could show this kind of symptoms. Maybe I should mention that I bought my laptop second (or at least I hope so) hand from ebay and I have not checked the hardware.

---

### Post by mogsareus on 2014-03-24
I have a similar problem.

CF-29 Pentium 1.3, 768MB ram 40GB hard drive.

Windows XP professional installed - strokes of touch pad needed to cross the screen diagonally.  XP - 3.  Lubuntu, running in demo mode 13-16.

Is there a way of increasing the amount of output relative to the touch pad input?

Regards

Simon DENHAM

---

