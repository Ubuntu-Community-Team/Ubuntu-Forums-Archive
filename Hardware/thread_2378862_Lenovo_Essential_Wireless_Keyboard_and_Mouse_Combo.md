---
title: "Lenovo Essential Wireless Keyboard and Mouse Combo doesn't work"
date: 2017-11-28
forum: Hardware
---

### Post by Pajinek on 2017-11-28
I bought new wireless keyboard on my Lenovo laptope and the mouse work good, but with the keyboard is problem. Only key "super" reacts on the keyboard. It is really pity, because i would like to use it. 

>> lsusb
 Bus 002 Device 007: ID 17ef:60a9 Lenovo

>> dmesg[ 3961.385133] usb 2-1.1: new full-speed USB device number 7 using ehci-pci
[ 3961.498284] usb 2-1.1: New USB device found, idVendor=17ef, idProduct=60a9
[ 3961.498293] usb 2-1.1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[ 3961.498297] usb 2-1.1: Product: Lenovo Essential Wireless Keyboard and Mouse Combo
[ 3961.500732] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:17EF:60A9.0013/input/input31
[ 3961.558148] hid-generic 0003:17EF:60A9.0013: input,hidraw0: USB HID v1.11 Keyboard [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.0-1.1/input0
[ 3961.560226] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/0003:17EF:60A9.0014/input/input32
[ 3961.560522] hid-generic 0003:17EF:60A9.0014: input,hidraw1: USB HID v1.11 Mouse [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.0-1.1/input1
[ 3961.561910] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/0003:17EF:60A9.0015/input/input33
[ 3961.621523] hid-generic 0003:17EF:60A9.0015: input,hidraw2: USB HID v1.11 Device [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.0-1.1/input2
[ 3961.623123] hid-generic 0003:17EF:60A9.0016: hiddev0,hidraw3: USB HID v1.11 Device [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.0-1.1/input3
[ 3961.818437] input input31: event field not found
[ 4034.664569] input input31: event field not found
[ 4034.784573] input input31: event field not found
.....

>>tail /var/log/Xorg.0.log
[    13.473] (**) Option "xkb_model" "pc105"
[    13.473] (**) Option "xkb_layout" "cz"
[  4346.801] (II) UnloadModule: "libinput"
[  4346.801] (II) UnloadModule: "libinput"

>> lsb_release  -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

> uanme -a 
Linux pavel-ThinkPad-T510 4.13.0-17-generic

---

### Post by thatsmyboy on 2017-11-28
I ran into this problem today! So strange that you posted too. I tried it on a Windows computer and I found that the keyboard was STILL finicky. I tried switching batteries, but I didn't have any that were very fresh. It could be as simple as that. My laptop is less than 3 months old, but who knows about the batteries that they sent. Good luck!  (My ALT key works, but not the SUPER to my knowledge).

---

### Post by Pajinek on 2017-12-01
Currently I receive diffrerent output in dmesg. I tried to combinate tips from forums, but nothing helped me. Super and alt keys work :) 

[   44.037051] rfkill: input handler disabled
[   44.181815] input input7: event field not found
[  314.090763] perf: interrupt took too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
[  411.773476] perf: interrupt took too long (3356 > 3126), lowering kernel.perf_event_max_sample_rate to 59500
[  565.239438] input input7: event field not found
[  565.343437] input input7: event field not found
[  846.804181] perf: interrupt took too long (4215 > 4195), lowering kernel.perf_event_max_sample_rate to 47250

---

### Post by thatsmyboy on 2017-12-01
If it helps, here's my output ( this is just for your benefit, I decided to go corded for myself) : 

```
>> dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-96-generic (buildd@lgw01-10) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 (Ubuntu 4.4.0-96.119-generic 4.4.83)
.....
[    6.884120] usb 3-2: new full-speed USB device number 2 using uhci_hcd
[    7.056173] usb 3-2: New USB device found, idVendor=17ef, idProduct=60a9
[    7.056188] usb 3-2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    7.056196] usb 3-2: Product: Lenovo Essential Wireless Keyboard and Mouse Combo
[    7.423698] hidraw: raw HID events driver (C) Jiri Kosina
[    7.480144] usbcore: registered new interface driver usbhid
[    7.480154] usbhid: USB HID core driver
[    7.507920] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/0003:17EF:60A9.0001/input/input7
[    7.568693] hid-generic 0003:17EF:60A9.0001: input,hidraw0: USB HID v1.11 Keyboard [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.1-2/input0
[    7.569570] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/0003:17EF:60A9.0002/input/input8
[    7.576503] hid-generic 0003:17EF:60A9.0002: input,hidraw1: USB HID v1.11 Mouse [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.1-2/input1
[    7.579030] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.2/0003:17EF:60A9.0003/input/input9
[    7.637427] hid-generic 0003:17EF:60A9.0003: input,hidraw2: USB HID v1.11 Device [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.1-2/input2
[    7.644258] hid-generic 0003:17EF:60A9.0004: hiddev0,hidraw3: USB HID v1.11 Device [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.1-2/input3
[    8.430364] IPv6: ADDRCONF(NETDEV_UP): wls33: link is not ready
[    8.444733] IPv6: ADDRCONF(NETDEV_UP): wls33: link is not ready
[    8.463851] IPv6: ADDRCONF(NETDEV_UP): ens32: link is not ready
[    8.533509] r8169 0000:01:00.0 ens32: link down
[    8.533951] IPv6: ADDRCONF(NETDEV_UP): ens32: link is not ready
[    8.827650] IPv6: ADDRCONF(NETDEV_UP): wls33: link is not ready
[   18.016121] input input7: event field not found
[   18.160124] input input7: event field not found
[   19.288130] input input7: event field not found
[   19.448127] input input7: event field not found
[   22.864125] input input7: event field not found
[   22.976130] input input7: event field not found
[   23.000128] input input7: event field not found
[   23.128129] input input7: event field not found
[   26.184137] input input7: event field not found
[   26.312136] input input7: event field not found
[   26.336142] input input7: event field not found
[   26.480153] input input7: event field not found
[   78.029705] perf interrupt took too long (2532 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  139.000154] input input7: event field not found
[  139.184154] input input7: event field not found
[  139.880172] input input7: event field not found
[  140.032152] input input7: event field not found
[  140.080173] input input7: event field not found
[  140.224158] input input7: event field not found
[  292.152229] input input7: event field not found
[  292.280228] input input7: event field not found
[  409.752277] input input7: event field not found
[  409.872273] input input7: event field not found
[  410.528261] input input7: event field not found
[  410.640255] input input7: event field not found
[ 8637.453728] perf interrupt took too long (5012 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[12563.580144] usb 3-2: USB disconnect, device number 2
[12619.744044] usb 1-5.1: new full-speed USB device number 4 using ehci-pci
[12619.840376] usb 1-5.1: New USB device found, idVendor=17ef, idProduct=60a9
[12619.840385] usb 1-5.1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[12619.840392] usb 1-5.1: Product: Lenovo Essential Wireless Keyboard and Mouse Combo
[12619.844469] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.1/1-5.1:1.0/0003:17EF:60A9.0005/input/input10
[12619.901890] hid-generic 0003:17EF:60A9.0005: input,hidraw0: USB HID v1.11 Keyboard [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.7-5.1/input0
[12619.905123] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.1/1-5.1:1.1/0003:17EF:60A9.0006/input/input11
[12619.905872] hid-generic 0003:17EF:60A9.0006: input,hidraw1: USB HID v1.11 Mouse [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.7-5.1/input1
[12619.908661] input: Lenovo Essential Wireless Keyboard and Mouse Combo as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.1/1-5.1:1.2/0003:17EF:60A9.0007/input/input12
[12619.964446] hid-generic 0003:17EF:60A9.0007: input,hidraw2: USB HID v1.11 Device [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.7-5.1/input2
[12619.966620] hid-generic 0003:17EF:60A9.0008: hiddev0,hidraw3: USB HID v1.11 Device [Lenovo Essential Wireless Keyboard and Mouse Combo] on usb-0000:00:1d.7-5.1/input3
[12740.350069] input input10: event field not found
[12740.558041] input input10: event field not found
[12740.718060] input input10: event field not found
[12740.894037] input input10: event field not found
.....

>> tail /var/log/Xorg.0.log
[ 12620.348] (**) evdev: Lenovo Essential Wireless Keyboard and Mouse Combo: YAxisMapping: buttons 4 and 5
[ 12620.348] (**) evdev: Lenovo Essential Wireless Keyboard and Mouse Combo: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 12620.348] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.1/1-5.1:1.1/0003:17EF:60A9.0006/input/input11/event5"
[ 12620.348] (II) XINPUT: Adding extended input device "Lenovo Essential Wireless Keyboard and Mouse Combo" (type: MOUSE, id 10)
[ 12620.349] (II) evdev: Lenovo Essential Wireless Keyboard and Mouse Combo: initialized for relative axes.
[ 12620.350] (WW) evdev: Lenovo Essential Wireless Keyboard and Mouse Combo: ignoring absolute axes.
[ 12620.351] (**) Lenovo Essential Wireless Keyboard and Mouse Combo: (accel) keeping acceleration scheme 1
[ 12620.351] (**) Lenovo Essential Wireless Keyboard and Mouse Combo: (accel) acceleration profile 0
[ 12620.351] (**) Lenovo Essential Wireless Keyboard and Mouse Combo: (accel) acceleration factor: 2.000
[ 12620.351] (**) Lenovo Essential Wireless Keyboard and Mouse Combo: (accel) acceleration threshold: 4

>> lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

>> uname -a
Linux Zotac 4.4.0-96-generic #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


```

If you need another test, I'd be happy to run along side you. Let me know how it goes.
 thatsmyboy

---

### Post by Pajinek on 2017-12-05
Hi, I tried other distributions and I have some problem. Keyboard works in BIOS and GRUB, but not after boot of kernel. I created bug for Fedoras (26/27) [https://bugzilla.redhat.com/show_bug.cgi?id=1521100](https://bugzilla.redhat.com/show_bug.cgi?id=1521100)

---

### Post by Pajinek on 2018-02-21
I still can't resolve this issue. But I found next project that tries to make workaround [https://github.com/fabianbl/lenovo_professional_wireless_keyboard](https://github.com/fabianbl/lenovo_professional_wireless_keyboard).

---

### Post by Pajinek on 2018-05-05
I upgraded system to latest kernel and the problem is not still resolved. 

4.15.0-20-generic (Ubuntu 18.04 LTS)

---

### Post by darkhole on 2018-05-15
I just reported this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1771431](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1771431)

The bug is still present in the latest Ubuntu version (18.04 bionic beaver) with stable kernel.

It's also reported by people from Linux Mint, Fedora and others.

[https://forums.lenovo.com/t5/Linux-Discussion/Professional-Wireless-Keyboard-not-working-on-Linux/td-p/3726486](https://forums.lenovo.com/t5/Linux-Discussion/Professional-Wireless-Keyboard-not-working-on-Linux/td-p/3726486)
[https://ubuntuforums.org/showthread.php?t=2378862](https://ubuntuforums.org/showthread.php?t=2378862)
[https://askubuntu.com/questions/897729/lenovo-professional-wireless-keyboard-and-mouse-combo-not-working-in-ubuntu](https://askubuntu.com/questions/897729/lenovo-professional-wireless-keyboard-and-mouse-combo-not-working-in-ubuntu)
[https://forums.linuxmint.com/viewtopic.php?f=49&t=260093&sid=20a073d5dd8abb1b7f23be608d7fdfd7](https://forums.linuxmint.com/viewtopic.php?f=49&t=260093&sid=20a073d5dd8abb1b7f23be608d7fdfd7)
[https://unix.stackexchange.com/questions/377830/linux-hid-driver-for-primax-wireless-keyboards/](https://unix.stackexchange.com/questions/377830/linux-hid-driver-for-primax-wireless-keyboards/)

[https://github.com/y-trudeau/linux_lenovo_ultraslim_plus](https://github.com/y-trudeau/linux_lenovo_ultraslim_plus)

---

### Post by master2neo on 2018-08-25
Hello for those who have not yet been able to operate your keyboard the solution is this:

[https://github.com/emarcanor/Driver_...im_plus_Ubuntu](https://github.com/emarcanor/Driver_...im_plus_Ubuntu)

The e compiled for the Lenovo Essential Wireless Keyboard and Mouse combo version.

it's just to download enter the directory and run the install. In any case it does not work for you to let me know and I hope you serve them!

---

### Post by wildmanne39 on 2018-08-25
Hello master2neo, Thanks for the solution! You posted in an English only sub-forum, please translate your posts in the future before posting.

Thanks!

---

### Post by Pajinek on 2019-06-15
I can confirm that this issue was fixed in 5.1.8-300.fc30.x86_64 - Fedora 30 [https://bugzilla.redhat.com/show_bug.cgi?id=1625415](https://bugzilla.redhat.com/show_bug.cgi?id=1625415)

---

