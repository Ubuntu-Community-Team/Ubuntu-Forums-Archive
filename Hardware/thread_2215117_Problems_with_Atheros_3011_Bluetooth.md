---
title: "Problems with Atheros 3011 Bluetooth"
date: 2014-04-04
forum: Hardware
---

### Post by larry-splane on 2014-04-04
I am relatively new to Linux so please take this into account.

I have a HP Pavilion DM1 4310NR Net book and I am currently running Kubuntu 13.10 with 3.11.0-19-generic kernel

I have followed the instructions in wireless.kernel.org in the ATH3K section, but I still cannot get my Bluetooth adapter to work.
 
I added the PID/VID to the ATH3K.c supported list and the PID/VID in the BTUSB.c black list. 

The ATH3K-1.fw is located in the /lib/firmware directory

When I try to Modprobe ATH3K the terminal kicks back a fatal error and states that module is not found. 

I have tried to run Modprobe -r btusb but this returns a error as well.

Please advise, anyone. I think it is something silly that I am missing, I have searched these forums, and I cannot find anything relating to this problem. Forgive me if I missed a similar problem that has been resolved.

Here is a terminal dump that might help someone see what I am missing.
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]lsusb -v
Bus 004 Device 002: ID 0cf3:311f Atheros Communications, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0cf3 Atheros Communications, Inc.
  idProduct          0x311f 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          185
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass        224 Wireless
      bFunctionSubClass       1 Radio Frequency
      bFunctionProtocol       1 Bluetooth
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1[/TD]
[/TR]
[/TABLE]

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
[/TD]
[/TR]
[/TABLE]

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]lsmod
Module                  Size  Used by
cdc_mbim               13000  0 
cdc_ncm                19368  1 cdc_mbim
cdc_wdm                18399  1 cdc_mbim
usbnet                 37607  2 cdc_mbim,cdc_ncm
joydev                 17097  0 
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
kvm_amd                50537  0 
parport_pc             31981  0 
ppdev                  17391  0 
kvm                   368975  1 kvm_amd
arc4                   12536  2 
microcode              18894  0 
ath9k                 136361  0 
ath9k_common           13619  1 ath9k
ath9k_hw              429197  2 ath9k_common,ath9k
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
rfcomm                 53664  16 
mac80211              517444  1 ath9k
psmouse                90642  0 
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
videobuf2_memops       13170  1 videobuf2_vmalloc
bnep                   18959  2 
btusb                  23443  0 
videobuf2_core         39125  1 uvcvideo
snd_hda_codec_idt      44605  1 
videodev              107508  2 uvcvideo,videobuf2_core
bluetooth             323656  22 bnep,btusb,rfcomm
snd_hda_codec_hdmi     40402  1 
cfg80211              401762  3 ath,ath9k,mac80211
serio_raw              13189  0 
k10temp                12958  0 
snd_hda_intel          42658  5 
snd_hda_codec         164003  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
i2c_piix4              17682  0 
snd_timer              24447  2 snd_pcm,snd_seq
snd                    60790  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12600  1 snd
hp_accel               25756  0 
lis3lv02d              19500  1 hp_accel
binfmt_misc            13140  1 
input_polldev          13648  1 lis3lv02d
mac_hid                13037  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
ums_realtek            17733  0 
usb_storage            48294  1 ums_realtek
radeon               1312332  3 
r8169                  61562  0 
ahci                   25579  2 
i2c_algo_bit           13197  1 radeon
mii                    13654  2 r8169,usbnet
ttm                    75982  1 radeon
drm_kms_helper         46867  1 radeon
libahci                26619  1 ahci
drm                   242400  5 ttm,drm_kms_helper,radeon
wmi                    18590  1 hp_wmi
video                  18777  0[/TD]
[/TR]
[/TABLE]

****UPDATE***** 

I added ATH3K to modprobe with the sudo command, obvious mistake. I still could not remove btusb with the command sudo modprobe -r btusb. Actually, when I typed sudo modprobe ath3k, they both appear in the lsmod, but the bluetooth  service still does not work.

-------------------------------------------------------------------------------------------------------------------------------------------
me@HP-Pavilion-dm1-Notebook-PC:~$ lsmod


pp
btusb                  23443  0                                                                                                                          
k10temp                12958  0                                                                                                                          
snd                    60790  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi                                                                                                                                     
bluetooth             323656  23 bnep,ath3k,btusb,rfcomm
--------------------------------------------------------------------------------------------------------------------------------------------


I noticed that there are Bluetooth coexistence issues with Atheros Wireless and Atheros Bluetooth so I ran this

sudo modprobe ath9k btcoex_enable=1

Still no sucess. I will keep digging but really hope someone is tracking that I am doing wrong here.

---

