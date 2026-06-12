---
title: "Playstation Joystick (Chinese) USB Only - Detected but does not work. Works on RPi."
date: 2014-02-24
forum: Hardware
---

### Post by devmod on 2014-02-24
I used to use this joystick ( [http://www.aliexpress.com/item/Free-shipping-GC-LFB-Pro-Fighting-Stick-Super-Street-Fighter-IV-PC-PS2-8-Key-Joystick/552016907.html](http://www.aliexpress.com/item/Free-shipping-GC-LFB-Pro-Fighting-Stick-Super-Street-Fighter-IV-PC-PS2-8-Key-Joystick/552016907.html) ) with my raspberry pi with any distro with no issues (raspbian mostly) 

Whenever I connected it I would see:
```

[  242.816706] usb 1-1.2: new full-speed USB device number 19 using dwc_otg
[  242.928285] usb 1-1.2: New USB device found, idVendor=0810, idProduct=0003
[  242.928325] usb 1-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[  242.928345] usb 1-1.2: Product: USB Gamepad 
[  242.944840] input: USB Gamepad  as /devices/platform/bcm2708_usb/usb1/1-1/1-1.2/1-1.2:1.0/input/input30
[  242.947992] hid-generic 0003:0810:0003.001F: input,hidraw0: USB HID v1.10 Joystick [USB Gamepad ] on usb-bcm2708_usb-1.2/input0

```
And it would work with no issues.

However, now that I am using ubuntu saucy the joystick gets detected but nothing happens when I press the buttons or move the joystick.

When I connected I see this:
```

[133623.629883] usb 3-7: new full-speed USB device number 6 using xhci_hcd
[133623.648310] usb 3-7: New USB device found, idVendor=054c, idProduct=0268
[133623.648320] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[133623.648326] usb 3-7: Product: \xffffffe5\xffffff80\xffffff80\xffffff80\xffffff80\xffffffe4\xffffff85\xffffff8c\xffffff85\xffffff8c\xffffffe5\xffffff8d\xffffff99\xffffff8d\xffffff99\xffffffe4\xffffff85\xffffff94\xffffff85\xffffff94\xffffffe4\xffffffa5\xffffff94\xffffffa5\xffffff94\xffffffe4\xffffffb9\xffffff8f\xffffffb9\xffffff8f\xffffffe5\xffffff88\xffffffa8\xffffff88\xffffffa8\xffffffe3\xffffff8c\xffffffa9\xffffff8c\xffffffa9\xffffffe4\xffffff8c\xffffffa0\xffffff8c\xffffffa0\xffffffe6\xffffffb9\xffffffaf\xffffffb9\xffffffaf\xffffffe7\xffffff89\xffffffb4\xffffff89\xffffffb4\xffffffe6\xffffffb1\xffffffaf\xffffffb1\xffffffaf\xffffffe6\xffffff95\xffffffac\xffffff95\xffffffac\xffffffe9\xffffffbd\xffffffb2\xffffffbd\xffffffb2
[133623.648331] usb 3-7: Manufacturer: \xffffffe5\xffffff8c\xffffff80\xffffff8c\xffffff80\xffffffe6\xffffffb9\xffffffaf\xffffffb9\xffffffafy\xffffffe3\xffffff99\xffffff94\xffffff99\xffffff94\x03
[133623.921037] sony 0003:054C:0268.0008: Fixing up Sony Sixaxis report descriptor
[133623.923062] input: \xffffffe5\xffffff8c\xffffff80\xffffff8c\xffffff80\xffffffe6\xffffffb9\xffffffaf\xffffffb9\xffffffafy\xffffffe3\xffffff99\xffffff94\xffffff99\xffffff94\x03 \xffffffe5\xffffff80\xffffff80\xffffff80\xffffff80\xffffffe4\xffffff85\xffffff8c\xffffff85\xffffff8c\xffffffe5\xffffff8d\xffffff99\xffffff8d\xffffff99\xffffffe4\xffffff85\xffffff94\xffffff85\xffffff94\xffffffe4\xffffffa5\xffffff94\xffffffa5\xffffff94\xffffffe4\xffffffb9\xffffff8f\xffffffb9\xffffff8f\xffffffe5\xffffff88\xffffffa8\xffffff88\xffffffa8\xffffffe3\xffffff8c\xffffffa9\xffffff8c\xffffffa9\xffffffe4\xffffff8c\xffffffa0\xffffff8c\xffffffa0\xffffffe6\xffffffb9\xffffffaf\xffffffb9\xffffffaf\xffffffe7\xffffff89\xffffffb4\xffffff89\xffffffb4\xffffffe6\xffffffb1\xffffffaf\xffffffb1\xffffffaf\xffffffe6\xffffff95\xffffffac\xffffff95\xffffffac\xffffffe9\xffffffbd\xffffffb2\xffffffbd\xffffffb2 as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/input/input14
[133623.925654] sony 0003:054C:0268.0008: input,hiddev0,hidraw2: USB HID v1.11 Joystick [\xffffffe5\xffffff8c\xffffff80\xffffff8c\xffffff80\xffffffe6\xffffffb9\xffffffaf\xffffffb9\xffffffafy\xffffffe3\xffffff99\xffffff94\xffffff99\xffffff94\x03 \xffffffe5\xffffff80\xffffff80\xffffff80\xffffff80\xffffffe4\xffffff85\xffffff8c\xffffff85\xffffff8c\xffffffe5\xffffff8d\xffffff99\xffffff8d\xffffff99\xffffffe4\xffffff85\xffffff94\xffffff85\xffffff94\xffffffe4\xffffffa5\xffffff94\xffffffa5\xffffff94\xffffffe4\xffffffb9\xffffff8f\xffffffb9\xffffff8f\xffffffe5\xffffff88\xffffffa8\xffffff88\xffffffa8\xffffffe3\xffffff8c\xffffffa9\xffffff8c\xffffffa9\xffffffe4\xffffff8c\xffffffa0\xffffff8c\xffffffa0\xffffffe6\xffffffb9\xffffffaf\xffffffb9\xffffffaf\xffffffe7\xffffff89\xffffffb4\xffffff89\xffffffb4\xffffffe6\xffffffb1\xffffffaf\xffffffb1\xffffffaf\xffffffe6\xffffff95\xffffffac\xffffff95\xffffffac\xffffffe9\xffffffbd\xffffffb2\xffffffbd\xffffffb2] on usb-0000:00:14.0-7/input0

```

```

$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 6: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
    |__ Port 7: Dev 6, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 8: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 8: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 8: Dev 3, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 9: Dev 4, If 0, Class=Human Interface Device, Driver=usbfs, 12M
    |__ Port 10: Dev 5, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 10: Dev 5, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M

```

```

$ lsmod
Module                  Size  Used by
hid_sony               13029  0 
bnep                   18959  2 
rfcomm                 53664  6 
bluetooth             323656  10 bnep,rfcomm
parport_pc             31981  0 
ppdev                  17391  0 
snd_hda_codec_realtek    50261  1 
snd_hda_codec_hdmi     40373  1 
x86_pkg_temp_thermal    13810  0 
coretemp               13195  0 
kvm_intel             128218  0 
kvm                   368949  1 kvm_intel
crc32_pclmul           12967  0 
mxm_wmi                12893  0 
joydev                 17097  0 
snd_hda_intel          42658  8 
snd_hda_codec         164003  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                89488  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25094  1 snd_seq_midi
microcode              18894  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
psmouse                90642  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24447  2 snd_pcm,snd_seq
serio_raw              13189  0 
snd                    60790  26 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei_me                 13933  0 
mei                    66411  1 mei_me
lpc_ich                16864  0 
soundcore              12600  1 snd
i915                  594442  14 
video                  18777  1 i915
drm_kms_helper         46867  1 i915
wmi                    18590  1 mxm_wmi
drm                   242400  13 i915,drm_kms_helper
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
intel_smartconnect     12610  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
hid_generic            12492  0 
hid_logitech_dj        18165  0 
usbhid                 47361  0 
hid                    87370  5 hid_sony,hid_generic,usbhid,hid_logitech_dj
usb_storage            48294  0 
ahci                   25579  3 
r8169                  61562  0 
libahci                26619  1 ahci
mii                    13654  1 r8169

```

```

$ uname -a
Linux mediacenter 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:53:31 UTC 2014 i686 i686 i686 GNU/Linux

```

I have tried all of the suggestions I have found and nothing works... 

```

~$ sudo jstest /dev/input/js0 
[sudo] password for mediacenter: 
Driver version is 2.1.0.
Joystick (&#21248;&#28271;y&#13908; &#20480;&#16716;&#21337;&#16724;&#18772;&#20047;&#21032;&#13097;&#17184;&#28271;&#29300;&#27759;&#25964;&#40818;) has 27 axes (X, Y, Z, Rz, (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null))
and 19 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead, BtnA, BtnB, BtnC, (null), (null), (null)).
Testing ... (interrupt to exit)
Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:     0  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:     0  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:     0  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:     0  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:     0  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:     0  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:     0  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:     0  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:     0  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:     0 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:     0 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:     0 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:     0 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:     0 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:     0 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:     0 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:     0 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:     0 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:     0 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:     0 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:     0 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:     0 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:     0 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:     0 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:-32767 24:     0 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:-32767 24:-32767 25:     0 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:-32767 24:-32767 25:-32767 26:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:-32767  6:-32767  7:-32767  8:-32767  9:-32767 10:-32767 11:-32767 12:-32767 13:-32767 14:-32767 15:-32767 16:-32767 17:-32767 18:-32767 19:-32767 20:-32767 21:-32767 22:-32767 23:-32767 24:-32767 25:-32767 26:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off 12:off 13:off 14:off 15:off 16:off 17:off 18:off 
(After printing this I press buttons but nothing happens )

```

Any help would be greatly appreciated !! 

Thanks

---

### Post by devmod on 2014-03-05
Tried blacklisting sixaxis (sony module) to see if joystick would be detected with some generic module and no go... 

I am still unable to use this device on Ubuntu. I don't understand how it works on my RPi with debian so easily. It seems like it is using some generic module...

---

