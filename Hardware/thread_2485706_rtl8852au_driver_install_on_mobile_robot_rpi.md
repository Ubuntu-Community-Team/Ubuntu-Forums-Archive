---
title: "rtl8852au driver install on mobile robot rpi"
date: 2023-04-06
forum: Hardware
---

### Post by andrewcra on 2023-04-06
Good morning y'all!

Happy Easter to you kind souls!

I'm stuck trying to get my new TP-Link AX1800 - Archer TX20U Plus working on my mobile Robot I'm working on.
The Archer TX20U Plus is based on the RTL8852AU chipset and I'm struggling getting the driver to work on Ubuntu 22.04.
Installation details:

a) raspberry pi 4b 
    ```
cat /proc/cpuinfo
        processor       : 0
        BogoMIPS        : 108.00
        Features        : fp asimd evtstrm crc32 cpuid
        CPU implementer : 0x41
        CPU architecture: 8
        CPU variant     : 0x0
        CPU part        : 0xd08
        CPU revision    : 3

        processor       : 1
        BogoMIPS        : 108.00
        Features        : fp asimd evtstrm crc32 cpuid
        CPU implementer : 0x41
        CPU architecture: 8
        CPU variant     : 0x0
        CPU part        : 0xd08
        CPU revision    : 3

        processor       : 2
        BogoMIPS        : 108.00
        Features        : fp asimd evtstrm crc32 cpuid
        CPU implementer : 0x41
        CPU architecture: 8
        CPU variant     : 0x0
        CPU part        : 0xd08
        CPU revision    : 3

        processor       : 3
        BogoMIPS        : 108.00
        Features        : fp asimd evtstrm crc32 cpuid
        CPU implementer : 0x41
        CPU architecture: 8
        CPU variant     : 0x0
        CPU part        : 0xd08
        CPU revision    : 3

        Hardware        : BCM2835
        Revision        : b03111
        Serial          : 10000000:-)xxx0
        Model           : Raspberry Pi 4 Model B Rev 1.1
```

b) ```
lsb_release -a
    No LSB modules are available.
    Distributor ID: Ubuntu
    Description:    Ubuntu 22.04.2 LTS
    Release:        22.04
    Codename:       jammy
```

c) ```
uname -i
    aarch64
```

d) ```
uname -a
    Linux autobotv2 5.15.0-1026-raspi #28-Ubuntu SMP PREEMPT Fri Mar 10 14:28:52 UTC 2023 aarch64 aarch64 aarch64 GNU/Linux
```

I have found this Github repo and have followed the instructions exactly.
```
https://github.com/lwfinger/rtl8852au
```

Here are the steps I have performed:
1. plugged in the device to USB
2. lsusb shows: Bus 001 Device 007: ID 2357:013f TP-Link 802.11ac WLAN Adapter
3. updated and amde sure all requirements are met / latest
   ```
 sudo apt-get update
    sudo apt-get install make gcc linux-headers-$(uname -r) build-essential git
```
4. created a new directory in my home folder and cloned the git into it:
    ```
mkdir src
    cd src
    git clone [URL="https://github.com/lwfinger/rtl8852au.git"]https://github.com/lwfinger/rtl8852au.git
```[/URL]
5. made sure to update the udev rules matching my device listed in lsusb output
    ```
sudo nano /usr/lib/udev/rules.d/40-usb_modeswitch.rules
    and added the below two lines to the bottom
        # tp-link AX1800 - Archer TX20U Plus (rtl8852au chipset)
        ATTR{idVendor}=="2357", ATTR{idProduct}=="013f", RUN+="usb_modeswitch '/%k'"
```
    -> by the way /lib/udev/rules.d/40-usb_modeswitch.rules contains the same two lines in the bottom. Must be the same file or a symlink!?
6. Then continued with the build process and install
   ```
 cd rtl8852au
    make
    sudo make install
```
7. I did not get any error output and the install process was flawless. That was yesterday evening. I do not have the terminal trace though.
8. reboot
9. ifconfig shows only loopback and the built-in wifi as wlan0, but not the plugged tp-link :-/
   ```
 lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            inet6 ::1  prefixlen 128  scopeid 0x10<host>
            loop  txqueuelen 1000  (Local Loopback)
            RX packets 102  bytes 8824 (8.8 KB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 102  bytes 8824 (8.8 KB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

    wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            inet 192.168.68.201  netmask 255.255.255.0  broadcast 192.168.68.255
            inet6 fe80::dea6:32ff:fe2a:7e96  prefixlen 64  scopeid 0x20<link>
            ether dc:a6:32:2a:7e:96  txqueuelen 1000  (Ethernet)
            RX packets 495  bytes 66254 (66.2 KB)
            RX errors 0  dropped 41  overruns 0  frame 0
            TX packets 609  bytes 142954 (142.9 KB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
10. lsusb still shows the device listed, same as under step 2. My understand is, that the udev rules should unload it and not list it with lsusb?
        ```
Bus 001 Device 007: ID 2357:013f TP-Link 802.11ac WLAN Adapter
```

Does anyone know what I'm missing, or what else I can try? I bought this adapter specifically because google research before purchase showed compatibility and easy to use in non-windows environments.
The issue with raspberry pi's built-in wifi is, that it performs poorly, since it is tucked away inside the Robot, that's why I need a cable extended USB wifi adapter.

Please help!

---

### Post by #&amp;thj^% on 2023-04-06
Will you also include this from the PI device:
```
dkms status
```
It should show like in mine below:
```
dkms status
8812au/4.2.2, 6.2.0-19-generic, x86_64: installed
nvidia/530.41.03, 6.2.0-19-generic, x86_64: installed

```
I know these dongles are picky on channels as well, I'm on 154 ATM

---

### Post by andrewcra on 2023-04-06
Hi 1Fallen,
thank you very much for your quick reply!

Here is the output of dkms status
```
8812au/5.6.4.2_35491.20191025: added
rtl8821au/5.12.5.2, 5.15.0-1026-raspi, aarch64: installed
rtl8852au/1.15.0.1: added
```

---

### Post by #&amp;thj^% on 2023-04-06
Interesting, I'm not going to rule out a bad driver install.(so many different methods out there, and only a few work currently) 
Lets look at one more thing while I have you:
```
nmcli dev wifi
```
I'm looking for signs of life from your device :):
mine:
```
 BC:A5:11:BA:E1:ED  NETGEAR-AP-5G      Infra  153   35 Mbit/s  64      &#9602;&#9604;&#9606;_  >
```

---

### Post by andrewcra on 2023-04-06
I have taken a screenshot to preserve formatting of terminal output. But couldn't post is.

administrator@autobotv2:~$ ```
nmcli dev wifi
IN-USE  BSSID              SSID                MODE   CHAN  RATE        SIGNAL  BARS  SECURITY
        68:FF:7B:21:??:E3  Home                   Infra  4     270 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2
        6E:FF:7B:21:??:E3  --                  Infra  4     270 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2
        68:FF:7B:21:??:F3  Home                Infra  36    270 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2
        6E:FF:7B:21:??:F3  --                  Infra  36    270 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2
        82:D9:82:30:??:9C  2degrees            Infra  36    270 Mbit/s  39      &#9602;&#9604;__  WPA2 WPA3
        82:D9:82:30:??:98  2degrees            Infra  36    270 Mbit/s  39      &#9602;&#9604;__  WPA2 WPA3
        74:??:28:1F:A0:24  AONET-1             Infra  1     130 Mbit/s  21      &#9602;&#9604;__  WPA1 WPA2
        68:FF:7B:21:??:21  Home                Infra  4     270 Mbit/s  30      &#9602;___  WPA1 WPA2
        68:FF:7B:21:??:A0  Home                Infra  4     270 Mbit/s  30      &#9602;___  WPA1 WPA2
        6E:FF:7B:21:??:A0  --                  Infra  4     270 Mbit/s  30      &#9602;___  WPA2
        6E:FF:7B:21:??:21  --                  Infra  4     270 Mbit/s  29      &#9602;___  WPA2
        88:DC:96:56:94:FE  --                  Infra  6     270 Mbit/s  29      &#9602;___  --
        82:D9:82:30:??:94  2degrees            Infra  6     130 Mbit/s  29      &#9602;___  WPA2 WPA3
        21:80:88:FC:F1:D1  --                  Infra  13    270 Mbit/s  29      &#9602;___  WPA2
        2E:80:88:FC:F1:D1  Lan                 Infra  13    270 Mbit/s  29      &#9602;___  WPA2
        18:FD:74:36:B1:35  AONET-3             Infra  1     130 Mbit/s  27      &#9602;___  WPA1 WPA2
        0A:18:A0:2D:??:85  Mo                  Infra  1     130 Mbit/s  27      &#9602;___  WPA1 WPA2
        88:DC:96:56:95:55  --                  Infra  6     270 Mbit/s  27      &#9602;___  --

IN-USE  BSSID  SSID  MODE  CHAN  RATE  SIGNAL  BARS  SECURITY
```

---

### Post by #&amp;thj^% on 2023-04-06
> **andrewcra said:**
> I have taken a screenshot to preserve formatting of terminal output.


EDIT: Yup thats better, but I don't see your device at all there
[s]Whoops, that did not work out so good,
See if my screenshot helps you attach a screenshot. the paperclip is our tool to upload.[/s]
**I'm going into work for an hour or two, I'll be back to check in.**

---

### Post by jeremy31 on 2023-04-06
What result for ```
modinfo 8852au
```

---

### Post by andrewcra on 2023-04-06
Hi jeremy31,

thanks for your input!

Here the output of  modinfo 8852au
```
filename:       /lib/modules/5.15.0-1026-raspi/kernel/drivers/net/wireless/realtek/rtw89/8852au.ko
version:        v1.15.0.1-0-g487ee886.20210714
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     CA3688458F929C1F84A1DFB
alias:          usb:v2357p0141d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p013Fd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3321d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0411p0312d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p1A62d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p1997d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp885Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp885Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8832d*dc*dsc*dp*icFFiscFFipFFin*
depends:        cfg80211
name:           8852au
vermagic:       5.15.0-1026-raspi SMP preempt mod_unload modversions aarch64
parm:           rtw_wireless_mode:int
parm:           rtw_band_type:int
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           rtw_lps_level:The default LPS level (int)
parm:           rtw_lps_chk_by_tp:int
parm:           rtw_max_bss_cnt:int
parm:           rtw_usb_rxagg_mode:int
parm:           rtw_dynamic_agg_enable:int
parm:           rtw_tx_bw_mode:The max tx bw for 2.4G and 5G. format is the same as rtw_bw_mode (uint)
parm:           rtw_max_amsdu_len:uint
parm:           rtw_rx_ampdu_sz_limit_1ss:RX AMPDU size limit for 1SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_2ss:RX AMPDU size limit for 2SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_3ss:RX AMPDU size limit for 3SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_rx_ampdu_sz_limit_4ss:RX AMPDU size limit for 4SS link of each BW, 0xFF: no limitation (array of uint)
parm:           rtw_vht_enable:int
parm:           rtw_vht_24g_enable:int
parm:           rtw_vht_rx_mcs_map:VHT RX MCS map (uint)
parm:           rtw_he_enable:int
parm:           rtw_rf_path:int
parm:           rtw_tx_nss:int
parm:           rtw_rx_nss:int
parm:           rtw_country_code:The default country code (in alpha2) (charp)
parm:           rtw_channel_plan:The default chplan ID when rtw_alpha2 is not specified or valid (int)
parm:           rtw_excl_chs:exclusive channel array (array of uint)
parm:           rtw_pci_dynamic_aspm_linkctrl:int
parm:           rtw_qos_opt_enable:int
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_vo_edca:uint
parm:           rtw_ap_src_b2u_flags:int
parm:           rtw_ap_fwd_b2u_flags:int
parm:           rtw_wowlan_sta_mix_mode:int
parm:           rtw_pwrtrim_enable:int
parm:           rtw_initmac:charp
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_mp_mode:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_hw_rts_en:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_bw_mode:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_rx_ampdu_amsdu:int
parm:           rtw_tx_ampdu_amsdu:int
parm:           rtw_quick_addba_req:int
parm:           rtw_beamform_cap:int
parm:           rtw_sw_proto_bf_cap_phy0:int
parm:           rtw_sw_proto_bf_cap_phy1:int
parm:           rtw_dyn_txbf:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_full_ch_in_p2p_handshake:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_drv_ant_band_switch:int
parm:           rtw_single_ant_path:int
parm:           rtw_switch_usb_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_check_hw_status:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_hiq_filter:0:allow all, 1:allow special, 2:deny all (uint)
parm:           rtw_adaptivity_en:0:disable, 1:enable (uint)
parm:           rtw_adaptivity_mode:0:normal, 1:carrier sense (uint)
parm:           rtw_adaptivity_th_l2h_ini:th_l2h_ini for Adaptivity (int)
parm:           rtw_adaptivity_th_edcca_hl_diff:th_edcca_hl_diff for Adaptivity (int)
parm:           rtw_dfs_region_domain:0:UNKNOWN, 1:FCC, 2:MKK, 3:ETSI (uint)
parm:           rtw_amsdu_mode:0:non-spp, 1:spp, 2:all drop (uint)
parm:           rtw_amplifier_type_2g:BIT3:2G ext-PA, BIT4:2G ext-LNA (uint)
parm:           rtw_amplifier_type_5g:BIT6:5G ext-PA, BIT7:5G ext-LNA (uint)
parm:           rtw_rfe_type:default init value:64 (uint)
parm:           rtw_dbcc_en:0:Disable, 1:Enable DBCC (int)
parm:           rtw_powertracking_type:default init value:64 (uint)
parm:           rtw_GLNA_type:default init value:0 (uint)
parm:           rtw_TxBBSwing_2G:default init value:0xFF (uint)
parm:           rtw_TxBBSwing_5G:default init value:0xFF (uint)
parm:           rtw_OffEfuseMask:default open Efuse Mask value:0 (uint)
parm:           rtw_FileMaskEfuse:default drv Mask Efuse value:0 (uint)
parm:           rtw_rxgain_offset_2g:default RF Gain 2G Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gl:default RF Gain 5GL Offset value:0 (uint)
parm:           rtw_rxgain_offset_5gh:uint
parm:           rtw_rxgain_offset_5gm:default RF Gain 5GM Offset value:0 (uint)
parm:           rtw_pll_ref_clk_sel:force pll_ref_clk_sel, 0xF:use autoload value (uint)
parm:           rtw_tx_pwr_by_rate:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_tx_pwr_lmt_enable:0:Disable, 1:Enable, 2: Depend on efuse (int)
parm:           rtw_target_tx_pwr_2g_a:2.4G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_b:2.4G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_c:2.4G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_2g_d:2.4G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_a:5G target tx power (unit:dBm) of RF path A for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_b:5G target tx power (unit:dBm) of RF path B for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_c:5G target tx power (unit:dBm) of RF path C for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_target_tx_pwr_5g_d:5G target tx power (unit:dBm) of RF path D for each rate section, should match the real calibrate power, -1: undefined (array of int)
parm:           rtw_phy_file_path:The path of phy parameter (charp)
parm:           rtw_load_phy_file:PHY File Bit Map (int)
parm:           rtw_decrypt_phy_file:Enable Decrypt PHY File (int)
parm:           rtw_phydm_ability:uint
parm:           rtw_halrf_ability:uint
parm:           rtw_en_napi:int
parm:           rtw_en_gro:int
parm:           rtw_iqk_fw_offload:int
parm:           rtw_ch_switch_offload:int
parm:           rtw_en_dyn_rrsr:int
parm:           rtw_rrsr_value:int
parm:           rtw_scan_interval_thr:Threshold used to judge if scan request comes from scan UI, unit is ms. (uint)
parm:           rtw_roch_min_home_dur:uint
parm:           rtw_roch_max_away_dur:uint
parm:           rtw_roch_extend_dur:uint
```

Not sure if that means the driver is properly installed.
Is there a command to list all atatched network interfaces other than ifconfig? Something that goes a bit more in depth? Because afaik ifconfig only shows active interfaces that are "up". I also tried "sudo ifup wlan1" but as you might guess that also didn't work..

---

### Post by jeremy31 on 2023-04-06
Is that module loaded?  Check ```
lsmod | grep 8852
```

Did the device always show as ```
Bus 001 Device 007: ID 2357:013f TP-Link 802.11ac WLAN Adapter
```

---

### Post by andrewcra on 2023-04-06
Hey jeremy31,

I think it is loaded. Here the output of lsmod | grep 8852
```
8852au              13656064  0
cfg80211              966656  2 8852au,brcmfmac
```

and yes, lsusb always showed the following, even before I started the driver install adventure:
```
Bus 001 Device 007: ID 2357:013f TP-Link 802.11ac WLAN Adapter
```

It seems like that is what I would expect.

---

### Post by jeremy31 on 2023-04-06
Try removing the usb-modeswitch entry you added and reboot as it shouldn't be needed for your device, I think it is only needed if it is seen as 1a2b as that is the onboard memory on some Realtek devices that contain Windows drivers

The command ```
iwconfig
``` might show some info

Post results for ```
sudo cat /sys/kernel/debug/usb/devices | awk '/013f/' RS=
```
That should show if the driver binds to the device

---

### Post by #&amp;thj^% on 2023-04-06
@ andrewcra uncle jeremy will have you up going in no time.
jeremy31 Thanks for assist, I need to stop saying work will only take an hour or two, it's automatic whammy.

---

### Post by andrewcra on 2023-04-07
Here is the output of lsmod:
```
administrator@autobotv2:~$ lsmod | grep 8852
8852au              13656064  0
cfg80211              966656  2 8852au,brcmfmac
```


 from dmesg output I noticed some potential driver signing issue!?
I think it did load however, and shows it renamed a device from wlan1 to something else:
```
[   34.797043] usb 1-1.1: USB disconnect, device number 3
[   35.531056] usb 1-1.1: new high-speed USB device number 7 using xhci_hcd
[   35.631647] usb 1-1.1: New USB device found, idVendor=2357, idProduct=013f, bcdDevice= 0.00
[   35.631670] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   35.631677] usb 1-1.1: Product: 802.11ac WLAN Adapter
[   35.631683] usb 1-1.1: Manufacturer: Realtek
[   35.631688] usb 1-1.1: SerialNumber: 00e04c000001
[   35.903595] 8852au: loading out-of-tree module taints kernel.
[   35.924590] 8852au: module verification failed: signature and/or required key missing - tainting kernel
[   36.239926] usbcore: registered new interface driver rtl8852au
[   36.297721] rtl8852au 1-1.1:1.0 wlx9ca2f4fc79dd: renamed from wlan1
```

That coincides with what iwconfig shows:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11  ESSID:"Home Wi-Fi"
          Mode:Managed  Frequency:5.18 GHz  Access Point: 68:FF:7B:32:46:F3
          Bit Rate=260 Mb/s   Tx-Power=31 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=52/70  Signal level=-58 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlx9ca2f4fc79dd  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=5.18 GHz  Access Point: Not-Associated
          Sensitivity:0/0
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


```

sudo cat /sys/kernel/debug/usb/devices | awk '/013f/' RS=
T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  7 Spd=480  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=2357 ProdID=013f Rev= 0.00
S:  Manufacturer=Realtek
S:  Product=802.11ac WLAN Adapter
S:  SerialNumber=00e04c000001
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 8 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl8852au
E:  Ad=84(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=06(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=07(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=09(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=0a(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=0b(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=0c(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

```
 
Any ideas what I can try next?

---

### Post by jeremy31 on 2023-04-07
Not really as I see you have filed an issue on github about the driver.  Another person on github warns people against buying anything with the RTL8852AU chipset [https://github.com/morrownr/USB-WiFi/discussions/25](https://github.com/morrownr/USB-WiFi/discussions/25)
I know either of them know more than I do about the driver and if anyone is able to fix it, it would be Larry Finger

---

### Post by andrewcra on 2023-04-07
It seems like it is working now.
However, I'm not sure if adding the module to DKMS has succeeded. Therefore I'm a bit wary I will loose connection next time I update and if there is a kernel upgrade include...

What is the best way to check if the DKMS integration of all modules suceeded?
I tried following the instructions under 
```
https://github.com/lwfinger/rtl8852au/#adding-modules-to-dkms-for-debianubuntu
```

Here is what I have done to get it working. Since the adapter shows up now under ifconfig:
1. I removed the modeswitch rule entry from  ```
/usr/lib/udev/rules.d/40-usb_modeswitch.rules
```

2. modified my /etc/netplan/50-cloud-init.yaml
```
sudo nano /etc/netplan/50-cloud-init.yaml
```

where I simply replaced "wlan0" with "wlx9ca2f4fc79dd"

Anyways, now I'm stuck with the DKMS, and any pointers wil be much appreciated!


Thank you everyone for all of your help so far! This is great! I appreciate y'all

---

### Post by jeremy31 on 2023-04-07
For the dkms support, try ```
sudo dkms install rtl8852au/1.15.0.1
```
Reboot and check ```
dkms status
```
If it works it should change the rtl8852au entry from added to installed

---

### Post by andrewcra on 2023-04-07
Hi Jeremy,

thanks for the suggestion and your continuous relentless help! 
I owe you a great deal mate! Truly appreciate you taking time out of your day!

Here the output for:
```

sudo dkms install rtl8852au/1.15.0.1
[sudo] password for administrator:

Kernel preparation unnecessary for this kernel. Skipping...

Building module:
cleaning build area...
'make' -j4 KVER=5.15.0-1026-raspi...(bad exit status: 2)
ERROR (dkms apport): binary package for rtl8852au: 1.15.0.1 not found
Error! Bad return status for module build on kernel: 5.15.0-1026-raspi (aarch64)
Consult /var/lib/dkms/rtl8852au/1.15.0.1/build/make.log for more information.
```


and of course status:
```

dkms status
8812au/5.6.4.2_35491.20191025: added
rtl8821au/5.12.5.2, 5.15.0-1026-raspi, aarch64: installed
rtl8852au/1.15.0.1: added

```

and the build-log as suggested in the output above
```

cat /var/lib/dkms/rtl8852au/1.15.0.1/build/make.log
DKMS make.log for rtl8852au-1.15.0.1 for kernel 5.15.0-1026-raspi (aarch64)
Sat Apr  8 09:14:46 AM NZST 2023
#rm -f .symvers.8852au
make ARCH=aarch64 CROSS_COMPILE= -C /lib/modules/5.15.0-1026-raspi/build M=/var/lib/dkms/rtl8852au/1.15.0.1/build  modules
make[1]: Entering directory '/usr/src/linux-headers-5.15.0-1026-raspi'
Makefile:712: arch/aarch64/Makefile: No such file or directory
make[1]: *** No rule to make target 'arch/aarch64/Makefile'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-5.15.0-1026-raspi'
make: *** [Makefile:636: modules] Error 2

```

---

### Post by jeremy31 on 2023-04-08
What does it show if you ```
cd rtl8852au
make clean
make
```

---

### Post by #&amp;thj^% on 2023-04-08
@jeremy31 do you think that is a good driver?
4 people have notified me of a successful driver with: [https://community.tp-link.com/en/home/forum/topic/547276](https://community.tp-link.com/en/home/forum/topic/547276)
God I love RealTek>>(Not)
EDIT: And on mine, I *have* to use a USB3 port, @ 5ghz

---

### Post by jeremy31 on 2023-04-08
The poster reported it was working on lwfingers github but there is an issue with the dkms.  I think it has to do with it looking for aarch64 instead or arm64 but I am not sure how the make and sudo make install worked

---

