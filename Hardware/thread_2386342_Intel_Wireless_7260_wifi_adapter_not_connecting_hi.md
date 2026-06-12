---
title: "Intel Wireless 7260 wifi adapter not connecting higher than 54Mbps"
date: 2018-03-04
forum: Hardware
---

### Post by netranger on 2018-03-04
Hi

I have a Dell Latitude E7440 with an Intel Wireless 7260 adapter. I have a TPLINK Archer C5400 Tri-Band router. The wireless adapter only detects bit rates up to 54Mbps. Ethernet speeds go in excess of 200Mbps through the same router which is inline with my ISP connection.

In addition to toggling all of the settings on my router and validating speeds using other devices which achieve much higher bit rates, I have read about every thread I can find on this and nothing is helping. I have WAP2 and AES selected. Here is the output of the commands i've been running:

```
lspci -k -nn | grep -A 3 -i net

...
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
```

```
sudo lshw -C network

  *-network                 
       description: Ethernet interface
       product: Ethernet Connection I218-LM
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 04
       serial: ec:f4:bb:1a:5e:4f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.6-3 ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:f7e00000-f7e1ffff memory:f7e3c000-f7e3cfff ioport:f080(size=32)
  *-network
       description: Wireless interface
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 73
       serial: 80:86:f2:24:57:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.13.0-36-generic firmware=17.608620.0 ip=192.168.1.103 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:49 memory:f7d00000-f7d01fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: virbr0-nic
       serial: 52:54:00:0b:67:a6
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: virbr0
       serial: 52:54:00:0b:67:a6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=no multicast=yes
```


```
sudo iwlist scan

wlp2s0    Scan completed :
          Cell 01 - Address: 50:C7:BF:38:1B:5A
                    Channel:112
                    Frequency:5.56 GHz (Channel 112)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"**********"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000007c9144f
                    Extra: Last beacon: 1964ms ago
                    IE: Unknown: 000D56494C4C415F544F5343414E41
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 073C4445202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E78011E7C011E80011E84011E88011E8C011E
                    IE: Unknown: 200100
                    IE: Unknown: 23021600
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050200060000
                    IE: Unknown: 2D1AEF0117FFFFFFFF00000000000000000000000000000000000000
                    IE: Unknown: 3D16700F1600000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: BF0CB2798B0FAAFF0000AAFF0000
                    IE: Unknown: C005016A000000
                    IE: Unknown: C30402020202
                    IE: Unknown: DD0500904C0417
                    IE: Unknown: DD090010180202001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 02 - Address: 50:C7:BF:38:1B:5C
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"**********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000007a8ade1
                    Extra: Last beacon: 4304ms ago
                    IE: Unknown: 000D56494C4C415F544F5343414E41
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B0509005D0000
                    IE: Unknown: 2D1AEF1117FFFFFFFF01000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F080500080000000040
                    IE: Unknown: DD1F00904C0418BF0CB279830FAAFF0000AAFF0000C0050003000000C303010202
                    IE: Unknown: DD090010180209001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 03 - Address: 56:C7:BF:38:1B:5D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"**********"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000007a820a3
                    Extra: Last beacon: 4340ms ago
                    IE: Unknown: 001356494C4C415F544F5343414E415F4755455354
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B0500005D0000
                    IE: Unknown: 2D1AEF1117FFFFFFFF01000000000000000000000000000000000000
                    IE: Unknown: 3D16010D1600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F03050008
                    IE: Unknown: DD1F00904C0418BF0CB279830FAAFF0000AAFF0000C0050003000000C303010202
                    IE: Unknown: DD090010180200001C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 04 - Address: 50:C7:BF:38:1B:5B
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"**********"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000007b92c44
                    Extra: Last beacon: 3028ms ago
                    IE: Unknown: 000D56494C4C415F544F5343414E41
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 073C4445202401172801172C01173001173401173801173C011740011764011E68011E6C011E70011E74011E78011E7C011E80011E84011E88011E8C011E
                    IE: Unknown: 200100
                    IE: Unknown: 23020F00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 0B050000010000
                    IE: Unknown: 2D1AEF0117FFFFFFFF00000000000000000000000000000000000000
                    IE: Unknown: 3D16340D0000000000000000000000000000000000000000
                    IE: Unknown: 7F080400080000000040
                    IE: Unknown: BF0CB2798B0FAAFF0000AAFF0000
                    IE: Unknown: C005013A000000
                    IE: Unknown: C30402020202
                    IE: Unknown: DD0500904C0417
                    IE: Unknown: DD090010180200001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
```


```
sudo rfkill list

1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: nfc0: NFC
	Soft blocked: yes
	Hard blocked: no
5: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```


```
lsmod

Module                  Size  Used by
rfcomm                 77824  2
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
ipt_MASQUERADE         16384  3
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
iptable_nat            16384  1
nf_nat_ipv4            16384  1 iptable_nat
nf_nat                 28672  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
nf_conntrack_ipv4      16384  5
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
xt_conntrack           16384  1
nf_conntrack          131072  6 nf_conntrack_ipv4,ipt_MASQUERADE,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
libcrc32c              16384  2 nf_conntrack,nf_nat
ipt_REJECT             16384  2
nf_reject_ipv4         16384  1 ipt_REJECT
xt_tcpudp              16384  6
bridge                143360  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
ebtable_filter         16384  0
ebtables               32768  1 ebtable_filter
ip6table_filter        16384  0
ip6_tables             28672  1 ip6table_filter
iptable_filter         16384  1
pci_stub               16384  1
vboxpci                24576  0
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               466944  3 vboxnetadp,vboxnetflt,vboxpci
md4                    16384  0
nls_utf8               16384  3
cifs                  716800  6
ccm                    20480  6
fscache                61440  1 cifs
cmac                   16384  4
bnep                   20480  2
hid_generic            16384  0
snd_usb_audio         196608  2
snd_usbmidi_lib        32768  1 snd_usb_audio
arc4                   16384  2
pn544_mei              16384  0
mei_phy                16384  1 pn544_mei
usbhid                 49152  0
pn544                  20480  1 pn544_mei
hci                    49152  2 mei_phy,pn544
nfc                   114688  2 hci,pn544
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
btusb                  45056  0
videobuf2_v4l2         24576  1 uvcvideo
btrtl                  16384  1 btusb
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
btbcm                  16384  1 btusb
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
btintel                16384  1 btusb
bluetooth             544768  31 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           24576  1 bluetooth
media                  40960  2 uvcvideo,videodev
dell_laptop            20480  0
dell_smm_hwmon         16384  0
intel_rapl             20480  0
snd_soc_rt5640        118784  0
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
ghash_clmulni_intel    16384  0
pcbc                   16384  0
snd_soc_core          229376  1 snd_soc_rt5640
iwlmvm                385024  0
snd_compress           20480  1 snd_soc_core
mac80211              782336  1 iwlmvm
ac97_bus               16384  1 snd_soc_core
snd_pcm_dmaengine      16384  1 snd_soc_core
aesni_intel           188416  9
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
intel_cstate           20480  0
snd_seq_midi           16384  0
intel_rapl_perf        16384  0
iwlwifi               253952  1 iwlmvm
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  2 snd_seq_midi,snd_usbmidi_lib
snd_hda_codec_realtek    94208  1
snd_hda_codec_hdmi     49152  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
snd_hda_intel          40960  9
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
input_leds             16384  0
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  2 snd_hda_codec,snd_usb_audio
wmi_bmof               16384  0
dell_wmi               16384  0
serio_raw              16384  0
snd_pcm                98304  8 snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
dell_smbios            16384  2 dell_wmi,dell_laptop
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
dcdbas                 16384  1 dell_smbios
sparse_keymap          16384  1 dell_wmi
cfg80211              614400  3 iwlmvm,iwlwifi,mac80211
lpc_ich                24576  0
mei_me                 40960  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
mei                   102400  4 mei_phy,mei_me,pn544_mei
shpchp                 36864  0
snd_timer              32768  2 snd_seq,snd_pcm
snd_soc_sst_acpi       16384  0
snd                    81920  37 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_usb_audio,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_usbmidi_lib,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
dell_smo8800           16384  0
soundcore              16384  1 snd
snd_soc_sst_match      16384  1 snd_soc_sst_acpi
spi_pxa2xx_platform    24576  0
dw_dmac                16384  0
elan_i2c               36864  0
8250_dw                16384  0
dw_dmac_core           24576  1 dw_dmac
dell_rbtn              16384  1
joydev                 20480  0
kvm_intel             200704  0
mac_hid                16384  0
kvm                   585728  1 kvm_intel
irqbypass              16384  1 kvm
binfmt_misc            20480  1
parport_pc             32768  1
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               40960  11 ipt_REJECT,iptable_mangle,ip_tables,ebtables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_CHECKSUM,ip6table_filter,xt_conntrack,ip6_tables
autofs4                40960  2
i915                 1822720  35
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  5 i915
psmouse               147456  0
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
ahci                   36864  1
fb_sys_fops            16384  1 drm_kms_helper
e1000e                249856  0
libahci                32768  1 ahci
drm                   360448  18 i915,drm_kms_helper
ptp                    20480  1 e1000e
sdhci_pci              28672  0
pps_core               20480  1 ptp
wmi                    24576  2 dell_wmi,wmi_bmof
video                  40960  3 dell_wmi,dell_laptop,i915
i2c_hid                20480  0
hid                   118784  4 i2c_hid,hid_generic,usbhid
sdhci_acpi             16384  0
sdhci                  45056  2 sdhci_pci,sdhci_acpi
```


```
iw phy

Wiphy phy0
	max # scan SSIDs: 20
	max scan IEs length: 425 bytes
	max # sched scan SSIDs: 20
	max # match sets: 11
	max # scan plans: 2
	max scan plan interval: 65535
	max scan plan iterations: 254
	Retry short limit: 7
	Retry long limit: 4
	Coverage class: 0 (up to 0m)
	Device supports RSN-IBSS.
	Device supports AP-side u-APSD.
	Supported Ciphers:
		* WEP40 (00-0f-ac:1)
		* WEP104 (00-0f-ac:5)
		* TKIP (00-0f-ac:2)
		* CCMP-128 (00-0f-ac:4)
	Available Antennas: TX 0 RX 0
	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * monitor
		 * P2P-client
		 * P2P-GO
		 * P2P-device
	Band 1:
		Capabilities: 0x11ee
			HT20/HT40
			SM Power Save disabled
			RX HT20 SGI
			RX HT40 SGI
			TX STBC
			RX STBC 1-stream
			Max AMSDU length: 3839 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 4 usec (0x05)
		HT Max RX data rate: 300 Mbps
		HT TX/RX MCS rate indexes supported: 0-15
		Bitrates (non-HT):
			* 1.0 Mbps
			* 2.0 Mbps (short preamble supported)
			* 5.5 Mbps (short preamble supported)
			* 11.0 Mbps (short preamble supported)
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
		Frequencies:
			* 2412 MHz [1] (20.0 dBm)
			* 2417 MHz [2] (20.0 dBm)
			* 2422 MHz [3] (20.0 dBm)
			* 2427 MHz [4] (20.0 dBm)
			* 2432 MHz [5] (20.0 dBm)
			* 2437 MHz [6] (20.0 dBm)
			* 2442 MHz [7] (20.0 dBm)
			* 2447 MHz [8] (20.0 dBm)
			* 2452 MHz [9] (20.0 dBm)
			* 2457 MHz [10] (20.0 dBm)
			* 2462 MHz [11] (20.0 dBm)
			* 2467 MHz [12] (20.0 dBm) (no IR)
			* 2472 MHz [13] (20.0 dBm) (no IR)
	Band 2:
		Capabilities: 0x11ee
			HT20/HT40
			SM Power Save disabled
			RX HT20 SGI
			RX HT40 SGI
			TX STBC
			RX STBC 1-stream
			Max AMSDU length: 3839 bytes
			DSSS/CCK HT40
		Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
		Minimum RX AMPDU time spacing: 4 usec (0x05)
		HT Max RX data rate: 300 Mbps
		HT TX/RX MCS rate indexes supported: 0-15
		VHT Capabilities (0x038071a0):
			Max MPDU length: 3895
			Supported Channel Width: neither 160 nor 80+80
			short GI (80 MHz)
			TX STBC
			SU Beamformee
		VHT RX MCS set:
			1 streams: MCS 0-9
			2 streams: MCS 0-9
			3 streams: not supported
			4 streams: not supported
			5 streams: not supported
			6 streams: not supported
			7 streams: not supported
			8 streams: not supported
		VHT RX highest supported: 0 Mbps
		VHT TX MCS set:
			1 streams: MCS 0-9
			2 streams: MCS 0-9
			3 streams: not supported
			4 streams: not supported
			5 streams: not supported
			6 streams: not supported
			7 streams: not supported
			8 streams: not supported
		VHT TX highest supported: 0 Mbps
		Bitrates (non-HT):
			* 6.0 Mbps
			* 9.0 Mbps
			* 12.0 Mbps
			* 18.0 Mbps
			* 24.0 Mbps
			* 36.0 Mbps
			* 48.0 Mbps
			* 54.0 Mbps
		Frequencies:
			* 5180 MHz [36] (20.0 dBm) (no IR)
			* 5200 MHz [40] (20.0 dBm) (no IR)
			* 5220 MHz [44] (20.0 dBm) (no IR)
			* 5240 MHz [48] (20.0 dBm) (no IR)
			* 5260 MHz [52] (20.0 dBm) (no IR, radar detection)
			* 5280 MHz [56] (20.0 dBm) (no IR, radar detection)
			* 5300 MHz [60] (20.0 dBm) (no IR, radar detection)
			* 5320 MHz [64] (20.0 dBm) (no IR, radar detection)
			* 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
			* 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
			* 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
			* 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
			* 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
			* 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
			* 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
			* 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
			* 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
			* 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
			* 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
			* 5720 MHz [144] (disabled)
			* 5745 MHz [149] (13.0 dBm) (no IR)
			* 5765 MHz [153] (13.0 dBm) (no IR)
			* 5785 MHz [157] (13.0 dBm) (no IR)
			* 5805 MHz [161] (13.0 dBm) (no IR)
			* 5825 MHz [165] (13.0 dBm) (no IR)
	Supported commands:
		 * new_interface
		 * set_interface
		 * new_key
		 * start_ap
		 * new_station
		 * new_mpath
		 * set_mesh_config
		 * set_bss
		 * authenticate
		 * associate
		 * deauthenticate
		 * disassociate
		 * join_ibss
		 * join_mesh
		 * remain_on_channel
		 * set_tx_bitrate_mask
		 * frame
		 * frame_wait_cancel
		 * set_wiphy_netns
		 * set_channel
		 * set_wds_peer
		 * start_sched_scan
		 * probe_client
		 * set_noack_map
		 * register_beacons
		 * start_p2p_device
		 * set_mcast_rate
		 * connect
		 * disconnect
		 * channel_switch
		 * set_qos_map
		 * add_tx_ts
		 * Unknown command (121)
	Supported TX frame types:
		 * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
		 * P2P-device: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
	Supported RX frame types:
		 * IBSS: 0x40 0xb0 0xc0 0xd0
		 * managed: 0x40 0xd0
		 * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * mesh point: 0xb0 0xc0 0xd0
		 * P2P-client: 0x40 0xd0
		 * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
		 * P2P-device: 0x40 0xd0
	WoWLAN support:
		 * wake up on disconnect
		 * wake up on magic packet
		 * wake up on pattern match, up to 20 patterns of 16-128 bytes,
		   maximum packet offset 0 bytes
		 * wake up on EAP identity request
		 * wake up on rfkill release
		 * wake up on network detection, up to 11 match sets
		 * wake up on TCP connection
	software interface modes (can always be added):
		 * AP/VLAN
		 * monitor
	valid interface combinations:
		 * #{ managed } <= 1, #{ AP, P2P-client, P2P-GO } <= 1, #{ P2P-device } <= 1,
		   total <= 3, #channels <= 2
	HT Capability overrides:
		 * MCS: ff ff ff ff ff ff ff ff ff ff
		 * maximum A-MSDU length
		 * supported channel width
		 * short GI for 40 MHz
		 * max A-MPDU length exponent
		 * min MPDU start spacing
	Device supports TX status socket option.
	Device supports HT-IBSS.
	Device supports SAE with AUTHENTICATE command
	Device supports low priority scan.
	Device supports scan flush.
	Device supports per-vif TX power setting
	P2P GO supports CT window setting
	P2P GO supports opportunistic powersave setting
	Driver supports full state transitions for AP/GO clients
	Driver supports a userspace MPM
	Driver/device bandwidth changes during BSS lifetime (AP/GO mode)
	Device supports static SMPS
	Device supports dynamic SMPS
	Device supports WMM-AC admission (TSPECs)
	Device supports configuring vdev MAC-addr on create.
```


```
dmesg | grep iwl

[    2.894722] iwlwifi: unknown parameter 'auto_agg' ignored
[    2.907208] iwlwifi 0000:02:00.0: loaded firmware version 17.608620.0 op_mode iwlmvm
[    2.948849] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.968772] iwlwifi 0000:02:00.0: base HW address: 80:86:f2:24:57:e3
[    3.195967] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.263279] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0

```


```
sudo cat /etc/modprobe.d/iwlwifi.conf

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=0 bt_coex_active=0 power_save=0 auto_agg=0 swcrypto=1
```

I should add that i've tried 11n_disable being set to 0, 1 and 8 as i've read in other threads and none makes a difference.

Also worth adding my speed test results:

```
speedtest

Retrieving speedtest.net configuration...
Testing from ********** (*.*.*.*)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by *********** (*********) [***** km]: 43.381 ms
Testing download speed................................................................................
Download: 48.01 Mbit/s
Testing upload speed................................................................................................
Upload: 8.12 Mbit/s
```

---

### Post by netranger on 2018-03-04
While I was pulling this data together I noticed **TKIP** was being used even though I had toggled that a number of times and tested. I set that before running the speedtest above and got the desired results. 

I've since re-run speedtest a number of times both the CLI tool and via a browser and i'm getting over **200Mbps** I'm meant to via my ISP. So the solution was to **force selection of WPA2 and AES instead of "Auto" ** on the router. 

I had done this but it looks like something needed time to update between the change and the speedtest. Worth also noting that bit rates from 

```
sudo iwlist scan
```

haven't changed. Checking the network manager applet however now shows **866Mbps**.

---

