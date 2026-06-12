---
title: "Wacom One works only partially"
date: 2021-01-11
forum: Hardware
---

### Post by quei on 2021-01-11
Hello everyone,
I bought a new graphic tablet, a Wacom One Creative Pen Display, but I found some problem to make it work properly with my laptop. I have Ubuntu 18.04.5 LTS, and after installing some of the recommended drivers and plugging in the tablet I obtained that the tablet's screen works, while the pen moves the mouse but only on the screen of the computer, i.e. it doesn't appear on the tablet's screen.
I tried to look into it, but I soon realized there must be something wrong:
the list of xsetwacom sees the pen and the eraser, but not the pad
```
$ xsetwacom list
Wacom One Pen Display 13 Pen stylus    id: 9    type: STYLUS    
Wacom One Pen Display 13 Pen eraser    id: 15    type: ERASER 
 
```
dmesg reports the tablet as unknown device
```

$ dmesg | grep wacom
[    2.413900] wacom: loading out-of-tree module taints kernel.
[    2.413952] wacom: module verification failed: signature and/or required key missing - tainting kernel
[    2.462157] wacom 0003:056A:03A6.0001: hidraw0: USB HID v1.10 Device [Wacom Co.,Ltd. Wacom One Pen Display 13] on usb-0000:00:14.0-1/input0
[    2.462237] wacom 0003:056A:03A6.0002: Unknown device_type for 'Wacom Co.,Ltd. Wacom One Pen Display 13'. Ignoring.
[    3.444860] Modules linked in: i915(+) snd_seq ecdh_generic cfg80211 thinkpad_acpi wmi snd_seq_device snd_timer drm_kms_helper nvram drm snd i2c_algo_bit fb_sys_fops lpc_ich syscopyarea mei_me video sysfillrect sysimgblt soundcore shpchp mei ip6table_filter ip6_tables mac_hid nf_conntrack_netbios_ns nf_conntrack_broadcast nf_nat_ftp nf_nat nf_conntrack_ftp nf_conntrack libcrc32c sch_fq_codel iptable_filter parport_pc ppdev lp parport ip_tables x_tables autofs4 wacom(OE) hid_generic usbhid hid rtsx_pci_sdmmc psmouse e1000e ahci rtsx_pci libahci ptp pps_core

```
xinput doesn't show the pad either
```

$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Wacom One Pen Display 13 Pen stylus         id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom One Pen Display 13 Pen eraser         id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C             id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=14    [slave  keyboard (3)]

```
Finally, looking into the Settings->Devices-> Wacom Tablet it says No Stylus Found, while it shows the Wacome One Pen Display 13 as tablet. Funnily enough when I try to use the calibration method, which should show some target in the tablet to point at with the pen in order to calibrate the screen, it shows it in the main screen and not in the tablet.
I tried following some simliar problem on the web, but whitout much success as I am not a big expert of Linux and I am worried to make things worse.
Any help would be much appreciated!
Cheers

---

