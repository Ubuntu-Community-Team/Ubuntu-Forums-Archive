---
title: "udev rule for usb mic"
date: 2012-12-07
forum: Hardware
---

### Post by szpuni on 2012-12-07
Hello,

I have a problem with UDEV rule for USB microphone.
I want to use udev so when I connect microphone to my machine I will set up 100% gain on that microphone.

I was playing with different rules but none seem to work.

I'm using that command in shell to force it manually but I would like that this task is done by UDEV daemon.

```
/usr/bin/amixer -c 1 sset Mic,0 100%,100% unmute cap 2>&1 | logger 
```

Any ideas?

Thanks

Below udevadm info about that device:


```
looking at device '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/dsp1':
    KERNEL=="dsp1"
    SUBSYSTEM=="sound"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1':
    KERNELS=="card1"
    SUBSYSTEMS=="sound"
    DRIVERS==""
    ATTRS{id}=="default"
    ATTRS{number}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0':
    KERNELS=="7-1:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="snd-usb-audio"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="00"
    ATTRS{bInterfaceClass}=="01"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{modalias}=="usb:v0556p0001d0001dc00dsc00dp00ic01isc01ip00"
    ATTRS{supports_autosuspend}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.1/usb7/7-1':
    KERNELS=="7-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 90mA"
    ATTRS{urbnum}=="102645093"
    ATTRS{idVendor}=="0556"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0001"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="7"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="AKM             "
    ATTRS{product}=="AK5370  " 
```

---

### Post by steeldriver on 2012-12-07
DISCLAIMER: I'm pretty much a n00b at udev but this worked for me (for playing with a USB fingerprint reader device)

1. create a script somewhere for your amixer command (I used /usr/local/bin)

2. create a low-numbered udev rule file (I called mine '21-persistent-local.rules')

I think you can use pretty much any attributes that uniquely ID the device - but 'idVendor' and 'idProduct' are probably sensible choices

```
$ cat /etc/udev/rules.d/21-persistent-local.rules 
ATTR{idVendor}=="*XXXX*", ATTR{idProduct}=="*YYYY*", SYMLINK+="*myusbdevice*", GROUP:="usb", MODE:="0660", RUN+="/usr/local/bin/*myudevscript*"
```Obviously you may not need the SYMLINK / GROUP / MODE stuff if the device is already getting the necessary filename + permissions

Hope this gets you started

---

### Post by szpuni on 2012-12-14
I was playing with all sort of rules but none of them seem to work.

```
KERNEL=="card1", SUBSYSTEM=="sound", DRIVERS=="snd-usb-audio", RUN+="/usr/bin/amixer -c 1 sset Mic,0 100%,100% unmute cap 2>&1 | logger"

udev_rules_new: rules use 16080 bytes tokens (1340 * 12 bytes), 9468 bytes buffer
udev_rules_new: temporary index used 10140 bytes (507 * 20 bytes)
udev_device_new_from_syspath: device 0x8081718 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1'
udev_device_new_from_syspath: device 0x8081970 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0'
udev_rules_apply_to_event: RUN '/usr/bin/amixer -c 1 sset Mic,0 100%,100% unmute cap 2>&1 | logger' /etc/udev/rules.d/30-myrule-mic.rules:1
udev_event_execute_rules: device event will be ignored
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=sound
```


```
SUBSYSTEM=="usb", ATTRS{product}=="AK5370          ", RUN+="/usr/local/bin/mic.sh"

node_symlink: preserve already existing symlink '/dev/char/189:792' to '../bus/usb/007/025'
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pci0000:00/0000:00:1d.1/usb7/7-1
udevadm_test: MAJOR=189
udevadm_test: MINOR=792
udevadm_test: DEVNAME=/dev/bus/usb/007/025
udevadm_test: DEVTYPE=usb_device
udevadm_test: DRIVER=usb
udevadm_test: PRODUCT=556/1/1
udevadm_test: TYPE=0/0/0
udevadm_test: BUSNUM=007
udevadm_test: DEVNUM=025
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=usb
udevadm_test: DEVLINKS=/dev/char/189:792
udevadm_test: run: '/usr/local/bin/mic.sh'
udevadm_test: run: '/opt/sbin/pcscd --hotplug'
```

udevadm test returns some information about my command is being run or script but when I check volume on alsamixer it is still 74% in both cases.

Whole thing I want to get is to force 100% gain on microphone when it is connected instead of 74% which is set by default.

Maybe there is different of doing that?
Any ideas?

---

### Post by szpuni on 2012-12-14
below udev with first rule from previous post:

```
[5706] main: initialize max_childs to 238
[5706] event_queue_insert: seq 1466 queued, 'remove' 'sound'
[5706] worker_new: seq 1466 forked new worker [5709]
[5706] event_queue_insert: seq 1467 queued, 'remove' 'sound'
[5706] worker_new: seq 1467 forked new worker [5710]
[5706] event_queue_insert: seq 1468 queued, 'remove' 'sound'
[5709] udev_device_read_db: device 0x806f160 filled with db symlink data '/dev/dsp1'
[5706] worker_new: seq 1468 forked new worker [5711]
[5706] event_queue_insert: seq 1469 queued, 'remove' 'sound'
[5709] update_link: no reference left, remove '/dev/char/14:19'
[5709] udev_node_remove: removing device node '/dev/dsp1'
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1466 processed with 0
[5712] udev_device_read_db: device 0x806b2b0 filled with db file data
[5712] update_link: no reference left, remove '/dev/char/116:32'
[5712] update_link: no reference left, remove '/dev/snd/by-id/usb-AKM_AK5370-00'
[5712] update_link: no reference left, remove '/dev/snd/by-path/pci-0000:00:1d.1-usb-0:1:1.0'
[5712] udev_node_remove: removing device node '/dev/snd/controlC1'
[5712] udev_monitor_send_device: passed -1 bytes to monitor 0x806b650
[5712] worker_new: seq 1469 processed with 0
[5706] worker_new: seq 1469 forked new worker [5712]
[5706] event_queue_delete: seq 1466 done with 0
[5706] event_queue_delete: seq 1469 done with 0
[5706] event_queue_insert: seq 1470 queued, 'remove' 'sound'
[5706] event_queue_insert: seq 1471 queued, 'remove' 'usb'
[5706] event_queue_insert: seq 1472 queued, 'remove' 'usb'
[5706] udev_monitor_send_device: passed 261 bytes to monitor 0x80670f8
[5706] event_queue_insert: seq 1473 queued, 'remove' 'usb'
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1472 processed with 0
[5706] event_queue_delete: seq 1472 done with 0
[5711] udev_device_read_db: device 0x806ed70 filled with db symlink data '/dev/snd/pcmC1D0c'
[5711] update_link: no reference left, remove '/dev/char/116:56'
[5711] udev_node_remove: removing device node '/dev/snd/pcmC1D0c'
[5711] udev_monitor_send_device: passed -1 bytes to monitor 0x806b1d8
[5711] worker_new: seq 1468 processed with 0
[5706] event_queue_delete: seq 1468 done with 0
[5710] udev_device_read_db: device 0x806e908 filled with db symlink data '/dev/audio1'
[5710] update_link: no reference left, remove '/dev/char/14:20'
[5710] udev_node_remove: removing device node '/dev/audio1'
[5710] udev_monitor_send_device: passed -1 bytes to monitor 0x806ec98
[5710] worker_new: seq 1467 processed with 0
[5706] event_queue_delete: seq 1467 done with 0
[5709] udev_device_new_from_syspath: device 0x806f950 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7'
[5709] udev_device_new_from_syspath: device 0x806e908 has devpath '/devices/pci0000:00/0000:00:1d.1'
[5709] udev_device_new_from_syspath: device 0x806e9c0 has devpath '/devices/pci0000:00'
[5709] udev_event_execute_rules: device event will be ignored
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1470 processed with 0
[5706] udev_monitor_send_device: passed 155 bytes to monitor 0x80670f8
[5706] event_queue_delete: seq 1470 done with 0
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1471 processed with 0
[5706] udev_monitor_send_device: passed 261 bytes to monitor 0x80670f8
[5706] event_queue_delete: seq 1471 done with 0
[5709] udev_device_read_db: device 0x806f138 filled with db symlink data '/dev/bus/usb/007/026'
[5709] udev_rules_apply_to_event: RUN '/opt/sbin/pcscd --hotplug' /etc/udev/rules.d/99-MYSecondRule.rules:1
[5709] update_link: no reference left, remove '/dev/char/189:793'
[5709] udev_node_remove: removing device node '/dev/bus/usb/007/026'
[5709] util_run_program: '/opt/sbin/pcscd --hotplug'
[5706] udev_monitor_send_device: passed 245 bytes to monitor 0x80670f8
[5709] util_run_program: '/opt/sbin/pcscd --hotplug' returned with exitcode 0
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1473 processed with 0
[5706] event_queue_delete: seq 1473 done with 0
[5706] event_queue_insert: seq 1474 queued, 'add' 'usb'
[5706] udev_monitor_send_device: passed 242 bytes to monitor 0x80670f8
[5709] udev_device_new_from_syspath: device 0x806e908 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1'
[5709] udev_rules_apply_to_event: LINK 'char/189:794' /lib/udev/rules.d/50-udev-default.rules:4
[5709] udev_rules_apply_to_event: MODE 0664 /lib/udev/rules.d/50-udev-default.rules:54
[5709] udev_rules_apply_to_event: NAME 'bus/usb/007/027' /lib/udev/rules.d/50-udev-default.rules:54
[5709] udev_rules_apply_to_event: RUN '/opt/sbin/pcscd --hotplug' /etc/udev/rules.d/99-MYSecondRule.rules:1
[5709] udev_device_update_db: create db link (bus/usb/007/027 char/189:794)
[5709] udev_node_add: creating device node '/dev/bus/usb/007/027', devnum=189:794, mode=0664, uid=0, gid=0
[5709] udev_node_mknod: mknod(/dev/bus/usb/007/027, 020664, (189,794))
[5709] udev_node_mknod: chmod(/dev/bus/usb/007/027, 020664)
[5709] udev_node_mknod: chown(/dev/bus/usb/007/027, 0, 0)
[5709] update_link: '/dev/char/189:794' with target '/dev/bus/usb/007/027' has the highest priority 0, create it
[5709] node_symlink: creating symlink '/dev/char/189:794' to '../bus/usb/007/027'
[5709] util_run_program: '/opt/sbin/pcscd --hotplug'
[5706] event_queue_insert: seq 1475 queued, 'add' 'usb'
[5706] event_queue_insert: seq 1476 queued, 'add' 'sound'
[5706] event_queue_insert: seq 1477 queued, 'add' 'sound'
[5706] event_queue_insert: seq 1478 queued, 'add' 'sound'
[5706] event_queue_insert: seq 1479 queued, 'add' 'sound'
[5706] event_queue_insert: seq 1480 queued, 'add' 'sound'
[5706] event_queue_insert: seq 1481 queued, 'add' 'usb'
[5709] util_run_program: '/opt/sbin/pcscd --hotplug' returned with exitcode 0
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1474 processed with 0
[5706] event_queue_delete: seq 1474 done with 0
[5706] udev_monitor_send_device: passed 258 bytes to monitor 0x80670f8
[5706] udev_monitor_send_device: passed 279 bytes to monitor 0x80670f8
[5710] udev_monitor_send_device: passed -1 bytes to monitor 0x806ec98
[5710] worker_new: seq 1481 processed with 0
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1475 processed with 0
[5706] event_queue_delete: seq 1481 done with 0
[5706] event_queue_delete: seq 1475 done with 0
[5706] udev_monitor_send_device: passed 152 bytes to monitor 0x80670f8
[5709] udev_device_new_from_syspath: device 0x806ea10 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0'
[5709] udev_rules_apply_to_event: RUN '/usr/bin/amixer -c 1 sset Mic,0 100%,100% unmute cap 2>&1 | logger' /etc/udev/rules.d/30-myrule-mic.rules:1
[5709] udev_event_execute_rules: device event will be ignored
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1476 processed with 0
[5706] event_queue_delete: seq 1476 done with 0
[5706] udev_monitor_send_device: passed 201 bytes to monitor 0x80670f8
[5706] udev_monitor_send_device: passed 188 bytes to monitor 0x80670f8
[5706] udev_monitor_send_device: passed 192 bytes to monitor 0x80670f8
[5706] udev_monitor_send_device: passed 203 bytes to monitor 0x80670f8
[5710] udev_device_new_from_syspath: device 0x806f968 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/dsp1'
[5712] udev_device_new_from_syspath: device 0x806f900 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1'
[5710] udev_rules_apply_to_event: LINK 'char/14:19' /lib/udev/rules.d/50-udev-default.rules:4
[5712] udev_rules_apply_to_event: LINK 'char/116:32' /lib/udev/rules.d/50-udev-default.rules:4
[5710] udev_rules_apply_to_event: GROUP 11 /etc/udev/rules.d/55-lfs.rules:34
[5710] udev_event_execute_rules: no node name set, will use kernel supplied name 'dsp1'
[5712] udev_rules_apply_to_event: [5711] udev_device_new_from_syspath: GROUP 11 /etc/udev/rules.d/55-lfs.rules:17
[5710] udev_device_update_db: [5712] udev_rules_apply_to_event: device 0x806f8d0 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/audio1'
NAME 'snd/controlC1' /etc/udev/rules.d/55-lfs.rules:17
create db link (dsp1 char/14:19)
[5710] udev_node_add: creating device node '/dev/dsp1', devnum=14:19, mode=0660, uid=0, gid=11
[5712] udev_device_new_from_syspath: device 0x806bb70 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1'
[5710] udev_node_mknod: [5711] udev_rules_apply_to_event: mknod(/dev/dsp1, 020660, (14,19))
LINK 'char/14:20' /lib/udev/rules.d/50-udev-default.rules:4
[5712] udev_device_new_from_syspath: [5710] udev_node_mknod: device 0x806bc88 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0'
chmod(/dev/dsp1, 020660)
[5711] udev_rules_apply_to_event: GROUP 11 /etc/udev/rules.d/55-lfs.rules:31
[5710] udev_node_mknod: [5712] udev_rules_apply_to_event: chown(/dev/dsp1, 0, 11)
IMPORT 'usb_id --export /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1' /lib/udev/rules.d/60-persistent-alsa.rules:7
[5711] udev_event_execute_rules: [5712] util_run_program: no node name set, will use kernel supplied name 'audio1'
'usb_id --export /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1'
[5711] udev_device_update_db: create db link (audio1 char/14:20)
[5711] udev_node_add: creating device node '/dev/audio1', devnum=14:20, mode=0660, uid=0, gid=11
[5710] update_link: [5711] udev_node_mknod: '/dev/char/14:19' with target '/dev/dsp1' has the highest priority 0, create it
mknod(/dev/audio1, 020660, (14,20))
[5710] node_symlink: [5711] udev_node_mknod: creating symlink '/dev/char/14:19' to '../dsp1'
chmod(/dev/audio1, 020660)
[5711] udev_node_mknod: chown(/dev/audio1, 0, 11)
[5710] udev_monitor_send_device: passed -1 bytes to monitor 0x806ec98
[5710] worker_new: seq 1478 processed with 0
[5706] event_queue_delete: seq 1478 done with 0
[5709] udev_device_new_from_syspath: device 0x806e990 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/pcmC1D0c'
[5709] udev_rules_apply_to_event: LINK 'char/116:56' /lib/udev/rules.d/50-udev-default.rules:4
[5711] update_link: '/dev/char/14:20' with target '/dev/audio1' has the highest priority 0, create it
[5709] udev_rules_apply_to_event: [5711] node_symlink: GROUP 11 /etc/udev/rules.d/55-lfs.rules:19
creating symlink '/dev/char/14:20' to '../audio1'
[5709] udev_rules_apply_to_event: NAME 'snd/pcmC1D0c' /etc/udev/rules.d/55-lfs.rules:19
[5711] udev_monitor_send_device: [5709] udev_device_update_db: passed -1 bytes to monitor 0x806b1d8
create db link (snd/pcmC1D0c char/116:56)
[5709] udev_node_add: [5711] worker_new: creating device node '/dev/snd/pcmC1D0c', devnum=116:56, mode=0660, uid=0, gid=11
seq 1479 processed with 0
[5709] udev_node_mknod: mknod(/dev/snd/pcmC1D0c, 020660, (116,56))
[5709] udev_node_mknod: chmod(/dev/snd/pcmC1D0c, 020660)
[5709] udev_node_mknod: chown(/dev/snd/pcmC1D0c, 0, 11)
[5706] event_queue_delete: seq 1479 done with 0
[5709] update_link: '/dev/char/116:56' with target '/dev/snd/pcmC1D0c' has the highest priority 0, create it
[5709] node_symlink: creating symlink '/dev/char/116:56' to '../snd/pcmC1D0c'
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1477 processed with 0
[5706] event_queue_delete: seq 1477 done with 0
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR=AKM'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ENC=AKM\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_VENDOR_ID=0556'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL=AK5370'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ENC=AK5370\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_MODEL_ID=0001'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_REVISION=0001'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_SERIAL=AKM_AK5370'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_TYPE=audio'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_BUS=usb'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_INTERFACES=:010100:010200:'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_INTERFACE_NUM=00'
[5712] util_run_program: '/lib/udev/usb_id' (stdout) 'ID_USB_DRIVER=snd-usb-audio'
[5712] util_run_program: 'usb_id --export /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1' returned with exitcode 0
[5712] udev_rules_apply_to_event: LINK 'snd/by-id/usb-AKM_AK5370-00' /lib/udev/rules.d/60-persistent-alsa.rules:9
[5712] udev_rules_apply_to_event: IMPORT 'path_id /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1' /lib/udev/rules.d/60-persistent-alsa.rules:12
[5712] util_run_program: 'path_id /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1'
[5712] util_run_program: '/lib/udev/path_id' (stdout) 'ID_PATH=pci-0000:00:1d.1-usb-0:1:1.0'
[5712] util_run_program: 'path_id /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1' returned with exitcode 0
[5712] udev_rules_apply_to_event: LINK 'snd/by-path/pci-0000:00:1d.1-usb-0:1:1.0' /lib/udev/rules.d/60-persistent-alsa.rules:13
[5712] udev_rules_apply_to_event: ATTR '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1/../uevent' writing 'change' /lib/udev/rules.d/78-sound-card.rules:5
[5706] event_queue_insert: seq 1482 queued, 'change' 'sound'
[5712] udev_device_update_db: created db file for '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card1/controlC1' in '/dev/.udev/db/\x2fdevices\x2fpci0000:00\x2f0000:00:1d.1\x2fusb7\x2f7-1\x2f7-1:1.0\x2fsound\x2fcard1\x2fcontrolC1'
[5712] udev_node_add: creating device node '/dev/snd/controlC1', devnum=116:32, mode=0660, uid=0, gid=11
[5712] udev_node_mknod: mknod(/dev/snd/controlC1, 020660, (116,32))
[5712] udev_node_mknod: chmod(/dev/snd/controlC1, 020660)
[5712] udev_node_mknod: chown(/dev/snd/controlC1, 0, 11)
[5712] update_link: '/dev/char/116:32' with target '/dev/snd/controlC1' has the highest priority 0, create it
[5712] node_symlink: creating symlink '/dev/char/116:32' to '../snd/controlC1'
[5712] update_link: '/dev/snd/by-id/usb-AKM_AK5370-00' with target '/dev/snd/controlC1' has the highest priority 0, create it
[5712] node_symlink: creating symlink '/dev/snd/by-id/usb-AKM_AK5370-00' to '../controlC1'
[5712] update_link: '/dev/snd/by-path/pci-0000:00:1d.1-usb-0:1:1.0' with target '/dev/snd/controlC1' has the highest priority 0, create it
[5712] node_symlink: creating symlink '/dev/snd/by-path/pci-0000:00:1d.1-usb-0:1:1.0' to '../controlC1'
[5712] udev_monitor_send_device: passed -1 bytes to monitor 0x806b650
[5706] event_queue_delete: seq 1480 done with 0
[5706] udev_monitor_send_device: passed 155 bytes to monitor 0x80670f8
[5712] worker_new: seq 1480 processed with 0
[5709] udev_device_new_from_syspath: device 0x806f138 has devpath '/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0'
**[5709] udev_rules_apply_to_event: RUN '/usr/bin/amixer -c 1 sset Mic,0 100%,100% unmute cap **2>&1 | logger' /etc/udev/rules.d/30-MYRULE-mic.rules:1
[5709] udev_event_execute_rules: device event will be ignored
[5709] udev_monitor_send_device: passed -1 bytes to monitor 0x806e830
[5709] worker_new: seq 1482 processed with 0
[5706] event_queue_delete: seq 1482 done with 0
[5706] handle_signal: worker [5710] exit
[5706] worker_unref: worker [5710] cleaned up
[5706] handle_signal: worker [5709] exit
[5706] worker_unref: worker [5709] cleaned up
```

So code is being run but vaule do not change any ideas?

---

### Post by steeldriver on 2012-12-14
Sorry no idea

As an alternative approach maybe you could use alsactrl to store the desired level(s) and then restore them in a startup script?

---

