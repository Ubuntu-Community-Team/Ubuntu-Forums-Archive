---
title: "How to get a Dexcom CGM receiver to work with Ubuntu"
date: 2018-03-28
forum: Hardware
---

### Post by michael330 on 2018-03-28
I am trying ti get a Dexcom CGM to work with Ubuntu. It works with Windows 10 with the Tide Pool windows driver [https://github.com/tidepool-org/windows-driver](https://github.com/tidepool-org/windows-driver). Windows device manager shows it as a Virtual com port device. I also have a Tandem-t slim insulin pump that works with Ubuntu and it shows up as a virtual com port device from lsusb and dmesg commands.
info for Tandem T-slim connected.
michael@michael-HP-15-Notebook-PC:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f3:228e Elan Microelectronics Corp. 
Bus 001 Device 006: ID 04f2:b52d Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 009: ID 0483:5740 STMicroelectronics STM32F407
Bus 001 Device 002: ID 19ff:0239 Dynex 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
michael@michael-HP-15-Notebook-PC:~$ dmesg
 USB disconnect, device number 8
[ 9179.651611] usb 1-3: new full-speed USB device number 9 using xhci_hcd
[ 9179.793344] usb 1-3: New USB device found, idVendor=0483, idProduct=5740
[ 9179.793350] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9179.793354] usb 1-3: Product: Tandem Virtual COM Port 
[ 9179.793357] usb 1-3: Manufacturer: TandemDiabetesCare
[ 9179.793359] usb 1-3: SerialNumber: 3100DF054850353831290443
[ 9179.799319] cdc_acm 1-3:1.0: ttyACM0: USB ACM device

Now with the Dexcom connected.
michael@michael-HP-15-Notebook-PC:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 04f3:228e Elan Microelectronics Corp. 
Bus 001 Device 006: ID 04f2:b52d Chicony Electronics Co., Ltd 

Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 010: ID 22a3:0047  
Bus 001 Device 002: ID 19ff:0239 Dynex 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
michael@michael-HP-15-Notebook-PC:~$ dmes
 cdc_acm 1-3:1.0: ttyACM0: USB ACM device
[ 9804.494083] usb 1-3: USB disconnect, device number 9
[ 9812.327391] usb 1-3: new full-speed USB device number 10 using xhci_hcd
[ 9812.470238] usb 1-3: New USB device found, idVendor=22a3, idProduct=0047
[ 9812.470256] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 9812.470263] usb 1-3: Product: DexCom Gen4 USB Serial
[ 9812.470269] usb 1-3: Manufacturer: DexCom
[ 9812.475515] cdc_acm 1-3:1.0: ttyACM0: USB ACM device


If start up windows 10 virtual box the t-slim works but the Dexcom wont. The device manager says that the device descriptor request failed. I don't have any Idea where to start? any help would be great.

---

### Post by michael330 on 2018-03-28
ok I havw loaded the usbserial.ko module and cp210x.ko module. Here is the output from lsmod.

cp210x                 28672  0
usbserial              45056  1 cp210x
nls_utf8               16384  1
isofs                  45056  1
rfcomm                 77824  14
xt_CHECKSUM            16384  1
iptable_mangle         16384  1
xt_tcpudp              16384  5
xt_comment             16384  8
vmnet                  53248  13
vmw_vsock_vmci_transport    28672  0
vsock                  36864  1 vmw_vsock_vmci_transport
vmw_vmci               69632  1 vmw_vsock_vmci_transport
vmmon                  90112  0
ipt_MASQUERADE         16384  2
nf_nat_masquerade_ipv4    16384  1 ipt_MASQUERADE
xfrm_user              32768  1
xfrm_algo              16384  1 xfrm_user
iptable_nat            16384  1
nf_conntrack_ipv4      16384  4
nf_defrag_ipv4         16384  1 nf_conntrack_ipv4
nf_nat_ipv4            16384  1 iptable_nat
xt_addrtype            16384  2
iptable_filter         16384  1
ccm                    20480  6
xt_conntrack           16384  1
nf_nat                 28672  2 nf_nat_masquerade_ipv4,nf_nat_ipv4
nf_conntrack          131072  6 nf_conntrack_ipv4,ipt_MASQUERADE,nf_nat_masquerade_ipv4,xt_conntrack,nf_nat_ipv4,nf_nat
libcrc32c              16384  2 nf_conntrack,nf_nat
br_netfilter           24576  0
aufs                  229376  0
bridge                143360  1 br_netfilter
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
pci_stub               16384  1
vboxpci                24576  0
cmac                   16384  1
vboxnetadp             28672  0
vboxnetflt             28672  0
vboxdrv               471040  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   20480  2
intel_rapl             20480  0
intel_powerclamp       16384  0
btusb                  45056  0
coretemp               16384  0
hid_multitouch         20480  0
btrtl                  16384  1 btusb
kvm_intel             200704  0
btbcm                  16384  1 btusb
kvm                   585728  1 kvm_intel
uvcvideo               90112  0
irqbypass              16384  1 kvm
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              176128  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
punit_atom_debug       16384  0
crct10dif_pclmul       16384  0
btintel                16384  1 btusb
cdc_acm                32768  0
crc32_pclmul           16384  0
bluetooth             544768  41 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ghash_clmulni_intel    16384  0
ecdh_generic           24576  1 bluetooth
pcbc                   16384  0
aesni_intel           188416  6
aes_x86_64             20480  1 aesni_intel
crypto_simd            16384  1 aesni_intel
joydev                 20480  0
glue_helper            16384  1 aesni_intel
cryptd                 24576  3 crypto_simd,ghash_clmulni_intel,aesni_intel
arc4                   16384  2
rtl8188ee              94208  0
intel_cstate           20480  0
input_leds             16384  0
hp_wmi                 16384  0
rtl_pci                32768  1 rtl8188ee
serio_raw              16384  0
rtlwifi                77824  2 rtl_pci,rtl8188ee
sparse_keymap          16384  1 hp_wmi
snd_hda_codec_hdmi     49152  1
mac80211              782336  3 rtl_pci,rtl8188ee,rtlwifi
snd_hda_codec_realtek    94208  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
wmi_bmof               16384  0
cfg80211              614400  2 mac80211,rtlwifi
snd_hda_intel          40960  6
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  23 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
soundcore              16384  1 snd
eeprom                 16384  0
tpm_crb                16384  0
shpchp                 36864  0
mei_txe                20480  0
processor_thermal_device    16384  0
int3403_thermal        16384  0
hp_wireless            16384  0
lpc_ich                24576  0
int340x_thermal_zone    16384  2 int3403_thermal,processor_thermal_device
int3400_thermal        16384  0
intel_soc_dts_iosf     16384  1 processor_thermal_device
acpi_thermal_rel       16384  1 int3400_thermal
mei                   102400  1 mei_txe
soc_button_array       16384  0
intel_int0002_vgpio    16384  1
mac_hid                16384  0
binfmt_misc            20480  1
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
binder_linux          102400  0
ashmem_linux           16384  0
ip_tables              24576  3 iptable_mangle,iptable_filter,iptable_nat
x_tables               40960  9 xt_comment,iptable_mangle,ip_tables,iptable_filter,xt_tcpudp,ipt_MASQUERADE,xt_CHECKSUM,xt_addrtype,xt_conntrack
autofs4                40960  2
usbhid                 49152  0
hid                   118784  2 usbhid,hid_multitouch
i915                 1822720  32
i2c_algo_bit           16384  1 i915
drm_kms_helper        167936  1 i915
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
sysimgblt              16384  1 drm_kms_helper
psmouse               147456  0
fb_sys_fops            16384  1 drm_kms_helper
r8169                  86016  0
ahci                   36864  2
drm                   360448  26 i915,drm_kms_helper
libahci                32768  1 ahci
mii                    16384  1 r8169
wmi                    24576  2 wmi_bmof,hp_wmi
dwc3                  118784  0
ulpi                   16384  1 dwc3
video                  40960  1 i915
udc_core               49152  1 dwc3

I compilled the  cp120.ko driver my self from [https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers). Any Ideas?

---

### Post by michael330 on 2018-03-28
What is a Aomic update failure ?
[21148.803443] cdc_acm 1-3:1.0: ttyACM0: USB ACM device
[21307.394757] [drm:intel_pipe_update_end [i915]] *ERROR* [COLOR=#ff0000]**Atomic update failure on pipe A (start=1277419 end=1277420) time 225 us, min 763, max 767, scanline start 757, end 768**[/COLOR]
[21767.619989] usbcore: registered new interface driver usbserial
[21767.620021] usbcore: registered new interface driver usbserial_generic
[21767.620045] usbserial: USB Serial support registered for generic
[21799.515805] usbcore: registered new interface driver cp210x
[21799.515839] usbserial: USB Serial support registered for cp210x
[22458.700342] usb 1-3: USB disconnect, device number 11
[22461.731936] usb 1-3: new full-speed USB device number 12 using xhci_hcd
[22461.875149] usb 1-3: New USB device found, idVendor=22a3, idProduct=0047
[22461.875166] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[22461.875176] usb 1-3: Product: DexCom Gen4 USB Serial
[22461.875186] usb 1-3: Manufacturer: DexCom
[22461.877115] cdc_acm 1-3:1.0: ttyACM0: USB ACM device

---

