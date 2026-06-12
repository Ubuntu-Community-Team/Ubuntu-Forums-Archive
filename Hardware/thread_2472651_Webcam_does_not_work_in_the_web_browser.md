---
title: "Webcam does not work in the web browser"
date: 2022-03-07
forum: Hardware
---

### Post by autominus on 2022-03-07
I have two webcam with the same error. I was testing at Cheese and it is not good. Cheese records video with sound, but this app frozen about 5-10 seconds - recording is okay, system resources about 40%.

My main problem occurs when I'm trying to use videoconferencing, via web browser.
1. Video test only via web browser - is OK.
2. Sound test only via web browser - is OK.
3. Video and sound via web browser - the web browser frozen after 2 seconds. 

I'm trying to join videoconference via Zoom.us , as a result Firefox frozen, Chromium frozen but after 10 seconds disable webcam.

I have Logitech C270 and Xiaomi/Microdia IMILAB CMSXJ22A.  I'm testing webcam on Ubuntu 20.10 (Groovy Gorilla) and Ubuntu 21.10 (impish indri).

They both have similar error in the dmesg report: 
**Logitech: **usb 1-1.3: 3:1: cannot get freq 24000 at ep 0x82[B]
Microdia: [/B]usb 1-1.3: 3:1: cannot get freq at ep 0x84[B]

Logitech:

[/B]dmesg```

[ 2119.427350] usb 1-1.3: new high-speed USB device number 5 using xhci_hcd
[ 2119.621970] usb 1-1.3: New USB device found, idVendor=046d, idProduct=0825, bcdDevice= 0.21
[ 2119.621980] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[ 2119.621984] usb 1-1.3: Product: C270 HD WEBCAM
[ 2119.621988] usb 1-1.3: SerialNumber: 200901010001
[ 2120.057699] uvcvideo: Found UVC 1.00 device C270 HD WEBCAM (046d:0825)
[ 2120.063171] input: C270 HD WEBCAM as /devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input9
[ 2120.063676] usbcore: registered new interface driver uvcvideo
[ 2120.063683] USB Video Class driver (1.1.1)
[ 2120.085704] usb 1-1.3: current rate 16000 is different from the runtime rate 32000
[ 2120.091476] usb 1-1.3: current rate 24000 is different from the runtime rate 16000
[ 2120.094694] usb 1-1.3: 3:3: cannot set freq 24000 to ep 0x82
[ 2120.218713] usb 1-1.3: set resolution quirk: cval->res = 384
[ 2120.220860] usbcore: registered new interface driver snd-usb-audio
[ 2156.600718] usb 1-1.3: reset high-speed USB device number 5 using xhci_hcd
[ 2156.813523] kauditd_printk_skb: 517 callbacks suppressed

```

journalctl -b
```

mar 07 18:08:17 RPi4 kernel: uvcvideo: Found UVC 1.00 device C270 HD WEBCAM (046d:0825)
mar 07 18:08:17 RPi4 kernel: input: C270 HD WEBCAM as /devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/>
mar 07 18:08:17 RPi4 kernel: usbcore: registered new interface driver uvcvideo
mar 07 18:08:17 RPi4 kernel: USB Video Class driver (1.1.1)
mar 07 18:08:17 RPi4 kernel: usb 1-1.3: current rate 16000 is different from the runtime rate 32000
mar 07 18:08:17 RPi4 kernel: usb 1-1.3: current rate 24000 is different from the runtime rate 16000
mar 07 18:08:17 RPi4 kernel: usb 1-1.3: 3:3: cannot set freq 24000 to ep 0x82
mar 07 18:08:17 RPi4 kernel: usb 1-1.3: set resolution quirk: cval->res = 384
mar 07 18:08:17 RPi4 kernel: usbcore: registered new interface driver snd-usb-audio
mar 07 18:08:17 RPi4 mtp-probe[4538]: checking bus 1, device 5: "/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/000>
mar 07 18:08:17 RPi4 mtp-probe[4538]: bus: 1, device: 5 was not an MTP device
mar 07 18:08:17 RPi4 systemd[1531]: Reached target Sound Card.
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) config/udev: Adding input device C270 HD WEBCAM (/dev/input/event9)
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (**) C270 HD WEBCAM: Applying InputClass "libinput keyboard catchall"
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) Using input driver 'libinput' for 'C270 HD WEBCAM'
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 80 paused 0
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (**) C270 HD WEBCAM: always reports core events
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (**) Option "Device" "/dev/input/event9"
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (**) Option "_source" "server/udev"
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) event9  - C270 HD WEBCAM: is tagged by udev as: Keyboard
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) event9  - C270 HD WEBCAM: device is a keyboard
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) event9  - C270 HD WEBCAM: device removed
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci00>
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) XINPUT: Adding extended input device "C270 HD WEBCAM" (type: KEYBOARD, i>
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (**) Option "xkb_model" "pc105"
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (**) Option "xkb_layout" "pl"
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (WW) Option "xkb_variant" requires a string value
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (WW) Option "xkb_options" requires a string value
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) event9  - C270 HD WEBCAM: is tagged by udev as: Keyboard
mar 07 18:08:17 RPi4 /usr/libexec/gdm-x-session[1590]: (II) event9  - C270 HD WEBCAM: device is a keyboard
mar 07 18:08:17 RPi4 systemd-udevd[4527]: controlC2: Process '/usr/sbin/alsactl -E HOME=/run/alsa -E XDG_RUNTIME_DIR=/run/alsa/runti>

```

[B]Microdia:

[/B]dmesg```

[ 3124.599578] usbcore: registered new interface driver uvcvideo 
[ 3124.599585] USB Video Class driver (1.1.1) [ 3133.287821] usb 1-1.3: new high-speed USB device number 7 using xhci_hcd
[ 3133.724035] usb 1-1.3: New USB device found, idVendor=0c45, idProduct=636d, bcdDevice= 1.00
[ 3133.724054] usb 1-1.3: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[ 3133.724065] usb 1-1.3: Product: USB 2.0 Camera
[ 3133.724074] usb 1-1.3: Manufacturer: Sonix Technology Co., Ltd.
[ 3133.724084] usb 1-1.3: SerialNumber: SN0001
[ 3133.727161] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:636d)
[ 3133.735160] input: USB 2.0 Camera: USB Camera as /devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input11
[ 3133.740339] usb 1-1.3: 3:1: cannot get freq at ep 0x84
[ 3134.005831] usb 1-1.3: 3:1: cannot get freq at ep 0x84
[ 3134.021742] usb 1-1.3: 3:1: cannot get freq at ep 0x8**4**
```

lsusb
```

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 062a:4101 MosArt Semiconductor Corp. Wireless Keyboard/Mouse
Bus 001 Device 011: ID 3938:1080  
Bus 001 Device 017: ID 0c45:636d Microdia USB2.0 Hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsusb -t
```

/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/4p, 480M
        |__ Port 1: Dev 17, If 2, Class=Audio, Driver=snd-usb-audio, 480M
        |__ Port 1: Dev 17, If 0, Class=Video, Driver=uvcvideo, 480M
        |__ Port 1: Dev 17, If 3, Class=Audio, Driver=snd-usb-audio, 480M
        |__ Port 1: Dev 17, If 1, Class=Video, Driver=uvcvideo, 480M
        |__ Port 3: Dev 11, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 3: Dev 11, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
        |__ Port 4: Dev 4, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 4: Dev 4, If 1, Class=Human Interface Device, Driver=usbhid, 12M

```


Thank you in advance for your help.

---

### Post by TheFu on 2022-03-08
Does the pi have sufficient power for multiple USB devices to be connected concurrently?  I've had power issues when just connecting a single USB device to a pi.

Do both work if only 1 webcam is connected?
Do they work on x86-64 Ubuntu systems?  I have friends with Logitech C270 webcams and they don't have any issue with Jitsi meetings or facebook's similar thing.

---

