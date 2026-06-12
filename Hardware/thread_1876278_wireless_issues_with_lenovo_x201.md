---
title: "wireless issues with lenovo x201"
date: 2011-11-05
forum: Hardware
---

### Post by thenav on 2011-11-05
Hi, I have a Lenovo X201 tablet, and the wireless connection seems to be pretty flaky with ubuntu. The wireless card is Intel Centrino Advanced-N 6200. I have a dual boot, and while Windows 7 detects close to 100% signal, in Ubuntu it never gets above 70% or so, and the signal strenth varies with time, getting disconnected every now and then. I'm running 11.10 now, but the same problem was there in 11.04.

Here's the result of lspci etc. Any help would be appreciated.

lspci | grep -i net

00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

sudo iwconfig wlan0

wlan0     IEEE 802.11abgn  ESSID:"MIT"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:70:93:6C:A1   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:192   Missed beacon:0

dmesg | grep iwlagn

[    4.225323] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.225333] iwlagn 0000:02:00.0: setting latency timer to 64
[    4.225361] iwlagn 0000:02:00.0: pci_resource_len = 0x00002000
[    4.225368] iwlagn 0000:02:00.0: pci_resource_base = f842c000
[    4.225370] iwlagn 0000:02:00.0: HW Revision ID = 0x35
[    4.225453] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
[    4.225493] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[    4.225559] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[    4.235079] iwlagn 0000:02:00.0: device EEPROM VER=0x436, CALIB=0x6
[    4.235083] iwlagn 0000:02:00.0: Device SKU: 0X1f0
[    4.236233] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    4.366451] iwlagn 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[    4.978184] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[    4.978314] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[    5.213215] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[    5.213349] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[   16.392951] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.393119] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[   17.131060] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[   17.131190] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1945.190633] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1945.190768] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1945.985102] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1945.985237] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1946.150737] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1946.150872] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1949.351839] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.
[ 1950.243237] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1950.243364] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1958.339190] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1958.339322] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1968.394419] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1968.394550] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1969.260369] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 1969.260511] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 6066.553266] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 6066.553400] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 6067.369545] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 6067.369679] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 6070.564248] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100106, writing 0x100506)
[ 6071.081912] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 6071.082041] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 6076.400018] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 6076.400155] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 6077.116983] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[ 6077.117125] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10004.757420] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10004.757551] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10030.373588] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10030.373720] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10031.104004] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10031.104134] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10073.686204] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10073.686335] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10182.731863] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10182.732004] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10182.897968] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10182.898098] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10183.631565] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10183.631710] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10496.117085] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10496.117221] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10511.812992] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10511.813134] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[10512.533648] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[10512.533778] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[19177.266742] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[19177.266873] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[19209.545837] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[19209.545980] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[19210.329084] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[19210.329226] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[19283.988108] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[19283.988239] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1
[19284.659328] iwlagn 0000:02:00.0: L1 Disabled; Enabling L0S
[19284.659459] iwlagn 0000:02:00.0: Radio type=0x1-0x3-0x1

---

### Post by bluexrider on 2011-11-05
[B]The Lenovo x201 is a certified Ubuntu laptop

Check this out [http://www.ubuntu.com/certification/hardware/201102-7305](http://www.ubuntu.com/certification/hardware/201102-7305)


[/B]

---

### Post by thenav on 2011-11-05
bluexrider, thanks for your reply. However, I did quite a bit of searching online before I posted. It appears I'm not the only one to have issues with the 6200 wireless card.

---

### Post by bluexrider on 2011-11-06
Have you considered support at Lenovo? [http://support.lenovo.com/en_US/research/default.page?](http://support.lenovo.com/en_US/research/default.page?)


May be a better source

---

### Post by thenav on 2011-11-06
Lenovo doesn't seem to offer support for Ubuntu. Anyway, maybe I posted in the wrong category. I will try networking and wireless; perhaps that'll me more helpful.

---

