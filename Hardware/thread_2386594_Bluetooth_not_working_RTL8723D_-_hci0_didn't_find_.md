---
title: "Bluetooth not working RTL8723D - hci0: didn't find patch for chip id 2 firmware error"
date: 2018-03-07
forum: Hardware
---

### Post by Kanfused on 2018-03-07
Hi,
This is a HP 15-BS576TX laptop which comes with Realtek RTL8723DE Wireless/Bluetooth module. I honestly cannot find a way to bring up the Bluetooth despite, the firmware are all available. The RTL8723DE firmware is recently available in kernel [linux-firmware.git repo]("https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/rtl_bt?id=6d5131107f2ba67a13f469ac770a55f101ba654d") and I have copied it to the /lib/firmware/rtl_bt directory too. 

The error is, it is asking for rtl8723b_config.bin file which is not available. Also, the bluetooth part of this laptop is detected as RTL8723B as per the kernel log. The reply from the firmware maintainer was: "Not all devices need the config file - rtl8723be does not."

```
    # dmesg  |grep -i bluetooth
    [   11.325095] Bluetooth: Core ver 2.22
    [   11.325111] Bluetooth: HCI device and connection manager initialized
    [   11.325113] Bluetooth: HCI socket layer initialized
    [   11.325115] Bluetooth: L2CAP socket layer initialized
    [   11.325118] Bluetooth: SCO socket layer initialized
    [   11.414774] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
    [   11.414775] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
    [   11.466838] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
    [   11.466840] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
    [   11.478765] Bluetooth: hci0: rom_version status=0 version=2
    [   11.478767] Bluetooth: hci0: didn't find patch for chip id 2
    [   21.410553] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
    [   21.410555] Bluetooth: BNEP filters: protocol multicast
    [   21.410557] Bluetooth: BNEP socket layer initialized

```
I have rtl8723D firmware in the directory and still, the kernel is detecting the device as RTL8723B and I cannot bring it up.

```
    hci0:    Type: Primary  Bus: USB
        BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
        DOWN 
        RX bytes:63 acl:0 sco:0 events:6 errors:0
        TX bytes:18 acl:0 sco:0 commands:6 errors:0
        Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
        Packet type: DM1 DH1 HV1 
        Link policy: 
        Link mode: SLAVE ACCEPT
```

When I tried, 
[B]# hciconfig hci0 up 
**Can't init device hci0: Invalid argument (22)**
[/B]
tail -f /var/log/kern.log shows this:

```
    Mar  8 01:51:21 HP-LAPTOP-15-BS00X kernel: [ 3116.853960] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
    Mar  8 01:51:21 HP-LAPTOP-15-BS00X kernel: [ 3116.853970] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
    Mar  8 01:51:21 HP-LAPTOP-15-BS00X kernel: [ 3116.854019] bluetooth hci0: Direct firmware load for rtl_bt/rtl8723b_config.bin failed with error -2
    Mar  8 01:51:21 HP-LAPTOP-15-BS00X kernel: [ 3116.854024] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
    Mar  8 01:51:21 HP-LAPTOP-15-BS00X kernel: [ 3116.855913] Bluetooth: hci0: rom_version status=0 version=2
    Mar  8 01:51:21 HP-LAPTOP-15-BS00X kernel: [ 3116.855920] Bluetooth: hci0: didn't find patch for chip id 2
```

And this is how the /lib/firmware/rtl_bt looks like. It has latest firmware for RTL8723D also copied into the directory:

```
    rtl8192ee_fw.bin
    rtl8192eu_fw.bin
    rtl8723a_fw.bin
[B]    rtl8723b_fw.bin
    rtl8723d_config.bin
    rtl8723d_fw.bin[/B]
    rtl8761a_fw.bin
    rtl8812ae_fw.bin
    rtl8821a_fw.bin
    rtl8821c_config.bin
    rtl8821c_fw.bin
    rtl8822b_config.bin
    rtl8822b_fw.bin
```

What is wrong, I cannot figure out. System detects the Bluetooth hardware as RTL8723B, while the wireless module is definitely RTL8723DE as written in the back of the laptop. The driver maintainer commented that the Bluetooth part of RTL8723B and RTL8723D are similar. So, What is the right thing to try? Is there a way to load the rtl8723d firmware and config file instead of rtl8723b firmware, will it fix the problem.

---

### Post by jeremy31 on 2018-03-07
I think you will have to wait for Realtek to release firmware that is patched for version 2.  I do not know if or when that will happen

---

### Post by Kanfused on 2018-03-08
> **jeremy31 said:**
> I think you will have to wait for Realtek to release firmware that is patched for version 2.  I do not know if or when that will happen

I already asked rtl_bt contributor Larry Fingers regarding this problem. But, as per him:
"I do not think there is any difference between the BT part of  rtl8723be and rtl8723de; however, I created the BT repo as a service. I  do not know anything about those devices, and I cannot help in  debugging."
"Not all devices need the config file - rtl8723be does not. There are  patches in the pipeline that suppress the message unless the config is  really needed. Ignore the message."

As per him, missing patch for chip id 2 is just a warning and not an issue. He has explained it here: [https://github.com/lwfinger/rtlwifi_new/issues/158](https://github.com/lwfinger/rtlwifi_new/issues/158) 

What I did try, is to move the rtl8723b_fw.bin to somewhere else and rename rtl8723d_fw.bin, rtl8723d_config.bin to rtl8723b_fw.bin and rtl8723b_config.bin respectively. But, that didn't fixed the problem. Instead, I got below error:
```
 230.491728] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[  230.491730] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[  230.534021] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[  230.537753] Bluetooth: hci0: rom_version status=0 version=2
[  230.537758] Bluetooth: hci0: unknown project id 9
[  319.303020] Bluetooth: hci0: rtl: examining hci_ver=08 hci_rev=000d lmp_ver=08 lmp_subver=8723
[  319.303029] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_config.bin
[  319.303165] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[  319.305177] Bluetooth: hci0: rom_version status=0 version=2
[  319.305187] Bluetooth: hci0: unknown project id 9


```
So, I reversed the naming and kept the firmware names intact.

Detailed lsusb: [https://pastebin.ca/3998303](https://pastebin.ca/3998303)
```
lsusb:
Bus 001 Device 002: ID 0bda:b009 Realtek Semiconductor Corp.
```

---

