---
title: "Bluetooth sometimes does not connect"
date: 2015-04-16
forum: Hardware
---

### Post by vmonkey on 2015-04-16
Hi,

I am using this laptop - Acer Apsire V15 NX.MQLEC.002 and have installed Ubuntu on it as a second OS. When using bluetooth it always works in windows but only sometimes in ubuntu (14.04). Switching it off and on in win sometimes helps.

dmesg | grep Bluetooth returns
```
[    6.386969] Bluetooth: Core ver 2.19
[    6.386990] Bluetooth: HCI device and connection manager initialized
[    6.386996] Bluetooth: HCI socket layer initialized
[    6.386998] Bluetooth: L2CAP socket layer initialized
[    6.387004] Bluetooth: SCO socket layer initialized
[   10.423861] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.423864] Bluetooth: BNEP filters: protocol multicast
[   10.423872] Bluetooth: BNEP socket layer initialized
[   10.437520] Bluetooth: RFCOMM TTY layer initialized
[   10.437530] Bluetooth: RFCOMM socket layer initialized
[   10.437535] Bluetooth: RFCOMM ver 1.11
```

pactl list modules | grep blue
```
Název: module-bluetooth-policy
        module.description = "When a bluetooth sink or source is added, load module-loopback"
    Název: module-bluetooth-discover
        module.description = "Detect available bluetooth audio devices and load bluetooth audio drivers"
```

cat /var/log/syslog | grep blue
```
Apr 16 12:42:22 vmonkey-Aspire-VN7-591G bluetoothd[873]: Unable to get service record: Host is down (112)
Apr 16 12:42:27 vmonkey-Aspire-VN7-591G bluetoothd[873]: Host is down (112)
Apr 16 12:42:37 vmonkey-Aspire-VN7-591G bluetoothd[873]: Unable to get service record: Host is down (112)
Apr 16 12:44:29 vmonkey-Aspire-VN7-591G pulseaudio[2072]: [pulseaudio] module-bluetooth-device.c: Failed to get device address/path from module arguments.
Apr 16 12:44:29 vmonkey-Aspire-VN7-591G pulseaudio[2072]: [pulseaudio] module.c: Failed to load module "module-bluetooth-device" (argument: ""): initialization failed.
Apr 16 12:58:10 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.111 path=/MediaEndpoint/HFPAG
Apr 16 12:58:10 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.111 path=/MediaEndpoint/HFPHS
Apr 16 12:58:10 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.111 path=/MediaEndpoint/A2DPSource
Apr 16 12:58:10 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.111 path=/MediaEndpoint/A2DPSink
Apr 16 12:58:44 vmonkey-Aspire-VN7-591G bluetoothd[873]: Unable to get service record: Host is down (112)
```

From syslog1 I also found
```
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Bluetooth daemon 4.101
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Starting SDP server
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: DIS cannot start: GATT is disabled
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Failed to init deviceinfo plugin
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Failed to init proximity plugin
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Failed to init time plugin
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Failed to init alert plugin
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Failed to init thermometer plugin
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Failed to init gatt_example plugin
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Bluetooth Management interface initialized
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Unknown command complete for opcode 19
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: hci0: Set Discoverable (0x0006) failed: Not Powered (0x0f)
Apr 16 09:44:57 vmonkey-Aspire-VN7-591G bluetoothd[873]: Adapter /org/bluez/873/hci0 has been enabled
Apr 16 09:45:01 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPAG
Apr 16 09:45:01 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPHS
Apr 16 09:45:01 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Apr 16 09:45:01 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Apr 16 09:45:07 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.60 path=/MediaEndpoint/HFPAG
Apr 16 09:45:07 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.60 path=/MediaEndpoint/HFPHS
Apr 16 09:45:07 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.60 path=/MediaEndpoint/A2DPSource
Apr 16 09:45:07 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint registered: sender=:1.60 path=/MediaEndpoint/A2DPSink
Apr 16 09:45:07 vmonkey-Aspire-VN7-591G dbus[853]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G blueman-mechanism: Starting blueman-mechanism 
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G dbus[853]: [system] Successfully activated service 'org.blueman.Mechanism'
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G blueman-mechanism: loading Network 
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G blueman-mechanism: loading Config 
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G blueman-mechanism: loading Ppp 
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G blueman-mechanism: loading RfKill 
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.60 path=/MediaEndpoint/HFPAG
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.60 path=/MediaEndpoint/HFPHS
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.60 path=/MediaEndpoint/A2DPSource
Apr 16 09:45:08 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.60 path=/MediaEndpoint/A2DPSink
Apr 16 09:45:24 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/HFPAG
Apr 16 09:45:24 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/HFPHS
Apr 16 09:45:24 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Apr 16 09:45:24 vmonkey-Aspire-VN7-591G bluetoothd[873]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Apr 16 09:45:24 vmonkey-Aspire-VN7-591G bluetoothd[873]: hci0: Remove UUID (0x0011) failed: Busy (0x0a)
Apr 16 09:45:38 vmonkey-Aspire-VN7-591G blueman-mechanism: Exiting 

```

Of course rfkill list returns
```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

I've already tried reinstalling all bluetooth-related packages but still no luck. I've also tried another device (speakers) but problem persists. Also hcitool scan also does not detect any devices.
Blueman applet just throws "Stream setup failed".

Thanks for answers!

---

### Post by jeremy31 on 2015-04-16
Can you post ```
uname -a; lsusb; dmesg | grep -i firmware
```

---

### Post by vmonkey on 2015-04-16
```
vmonkey@vmonkey-Aspire-VN7-591G:~$ uname -a; lsusb; dmesg | grep -i firmware
Linux vmonkey-Aspire-VN7-591G 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 04f2:b469 Chicony Electronics Co., Ltd 
Bus 003 Device 004: ID 06cb:2970 Synaptics, Inc. 
Bus 003 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 006: ID 04ca:300d Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.140960] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   11.431585] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   11.434126] snd_hda_intel 0000:00:03.0: Applying patch firmware 'hda-jack-retask.fw'
[   11.434245] snd_hda_intel 0000:00:1b.0: Applying patch firmware 'hda-jack-retask.fw'
```

---

### Post by jeremy31 on 2015-04-16
I can't believe it ever works as it should be an Atheros bluetooth that is part of an Atheros wifi combo chipset and I don't think it is supported correctly by the kernel.
```
modprobe -c | grep -i 300d | grep ath3k
```

I suspect you will see no result.

I can help you build a couple new modules for your kernel so that bluetooth does work correctl

---

### Post by vmonkey on 2015-04-17
You're right, no output. I've found this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1394368"), which seems to be the case. According to [this post]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1394368/comments/13") I copied firmware files AthrBT_0x11020100.dfu and ramps_0x11020100_40.dfu from Program Files\Common Files\QCA-Bluetooth to /lib/firmware/ar3k-folder and upgraded to latest [mainline kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-vivid/"). However the issue is still present. Any help would be greatly appreciated. Thanks for feedback!

---

### Post by jeremy31 on 2015-04-17
ok ```
wget https://www.dropbox.com/s/cxr2usc4qopudx1/bluetooth-utopic-3.tar.gz
```
```
tar -zxf bluetooth.utopic-3.tar.gz
```
```
sudo apt-get install build-essential linux-headers-generic
```
```
cd bluetooth
```
```
cp /boot/config-$(uname -r) .config
```
```
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
```
```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
```
```
sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
```
sudo cp ath3k.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
```
echo ath3k | sudo tee -a /etc/modules
```

Reboot and see if it works

---

### Post by vmonkey on 2015-04-18
Thanks for answer! However I cannot get to successful compilation - I've yet tried 3 different kernels. For example in the newest 4 (link posted above) I get 

```

/home/vmonkey/bt/bluetooth/hci_ath.c: In function &#8216;ath_wakeup_ar3k&#8217;:
/home/vmonkey/bt/bluetooth/hci_ath.c:63:2: error: implicit declaration of function &#8216;tty_set_termios&#8217; [-Werror=implicit-function-declaration]
  tty_set_termios(tty, &ktermios);

```

---

### Post by jeremy31 on 2015-04-18
Try this, different source file
```
rm ~/bluetooth
```
```
wget https://www.dropbox.com/s/rlv2prqzzptcr6f/bluetooth-trusty.tar.gz
```
```
tar -zxf bluetooth-trusty.tar.gz
```
```
cd bluetooth
```
```
cp /usr/src/linux-headers-$(uname -r)/Module.symvers Module.symvers
```
```
cp /boot/config-$(uname -r) .config
```
```
make -C /lib/modules/$(uname -r)/build M=$PWD modules
```
```
sudo cp btusb.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
```
sudo cp ath3k.ko /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```
```
echo ath3k | sudo tee -a /etc/modules
```

Reboot

---

### Post by dablik415 on 2016-01-06
I have totally the same problem. I don't know if it is fixed yet or no, but by using above mentioned process bluetooth still doesn't work correctly. 
If there is any other way, can you be so generous and write it down please?? That technical stuff is out of my control.
Thanks in advance.

---

