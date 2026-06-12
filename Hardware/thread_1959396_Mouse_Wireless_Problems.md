---
title: "Mouse Wireless Problems"
date: 2012-04-15
forum: Hardware
---

### Post by xxtodinhoxx on 2012-04-15
Good evening,

 I am new to linux world, I would like help installing my mouse, enter some information I find useful.

My mouse:
[http://www.dealextreme.com/p/2-4ghz-wireless-optical-mouse-with-usb-receiver-black-1-aa-34332](http://www.dealextreme.com/p/2-4ghz-wireless-optical-mouse-with-usb-receiver-black-1-aa-34332)

I use Ubuntu 11.04

dmesg:::::::::::::::::::::::::::::::

[ 5910.258593] generic-usb 0003:0603:1602.1A92: input,hiddev0,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1a.1-2/input0
[ 5910.258703] usb 4-2: USB disconnect, device number 123
[ 5910.992160] usb 4-2: new low speed USB device number 124 using uhci_hcd
[ 5911.208237] input: USB Device USB Device as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input6813
[ 5911.208622] generic-usb 0003:0603:1602.1A93: input,hiddev0,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1a.1-2/input0
[ 5911.208731] usb 4-2: USB disconnect, device number 124
[ 5911.776078] usb 4-2: new low speed USB device number 125 using uhci_hcd
[ 5911.994078] input: USB Device USB Device as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input6814
[ 5911.994416] generic-usb 0003:0603:1602.1A94: input,hiddev0,hidraw0: USB HID v1.11 Mouse [USB Device USB Device] on usb-0000:00:1a.1-2/input0
[ 5911.994514] usb 4-2: USB disconnect, device number 125


lsmod:::::::::::::::

Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
bnep                   17923  2 
rfcomm                 38408  8 
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
arc4                   12473  2 
snd_hda_codec_idt      60049  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth             148839  23 bnep,rfcomm,btusb
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                63474  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
iwlagn                273973  0 
mac80211              393421  1 iwlagn
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  2 iwlagn,mac80211
binfmt_misc            17292  1 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  0 
uas                    17699  0 
i915                  509554  4 
drm_kms_helper         32889  1 i915
drm                   196290  5 i915,drm_kms_helper
firewire_ohci          35846  0 
ahci                   21634  3 
libahci                25761  1 ahci
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
r8169                  47200  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915

---

