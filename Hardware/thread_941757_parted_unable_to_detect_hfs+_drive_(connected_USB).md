---
title: "parted unable to detect hfs+ drive (connected USB)"
date: 2008-10-08
forum: Hardware
---

### Post by keyshawn on 2008-10-08
I have an HFS+ formatted ide hard drive (from an iBook whose logic board is dead). 
I would like to access the data on it. 

I have an IDE to USB adapter and it is being detected in my the /var/log/syslog. Here is the syslog:

```

Oct  8 12:55:18 skorasaurus-lappy kernel: [97812.100583] usb 7-1: new high speed USB device using ehci_hcd and address 6
Oct  8 12:55:18 skorasaurus-lappy kernel: [97812.233290] usb 7-1: configuration #1 chosen from 1 choice
Oct  8 12:55:18 skorasaurus-lappy kernel: [97812.233973] scsi6 : SCSI emulation for USB Mass Storage devices
Oct  8 12:55:18 skorasaurus-lappy kernel: [97812.234257] usb-storage: device found at 6
Oct  8 12:55:18 skorasaurus-lappy kernel: [97812.234260] usb-storage: waiting for device to settle before scanning
Oct  8 12:55:19 skorasaurus-lappy NetworkManager: <debug> [1223484919.406381] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6'). 
Oct  8 12:55:19 skorasaurus-lappy NetworkManager: <debug> [1223484919.423404] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0'). 
Oct  8 12:55:23 skorasaurus-lappy kernel: [97817.225402] usb-storage: device scan complete
Oct  8 12:55:23 skorasaurus-lappy kernel: [97817.226227] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Oct  8 12:55:23 skorasaurus-lappy kernel: [97817.237198] sd 6:0:0:0: [sdb] Attached SCSI disk
Oct  8 12:55:23 skorasaurus-lappy kernel: [97817.237258] sd 6:0:0:0: Attached scsi generic sg2 type 0
Oct  8 12:55:23 skorasaurus-lappy NetworkManager: <debug> [1223484923.916059] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host'). 
Oct  8 12:55:23 skorasaurus-lappy NetworkManager: <debug> [1223484923.920110] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host_scsi_device_lun0'). 
Oct  8 12:55:23 skorasaurus-lappy NetworkManager: <debug> [1223484923.923260] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct  8 12:55:23 skorasaurus-lappy NetworkManager: <debug> [1223484923.983672] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_JMicron_USB_to_ATA_ATAPI_Bridge_152D203380B6_0_0'). 

```It is also detected in my dmesg:

```

[97812.100583] usb 7-1: new high speed USB device using ehci_hcd and address 6
[97812.233290] usb 7-1: configuration #1 chosen from 1 choice
[97812.233973] scsi6 : SCSI emulation for USB Mass Storage devices
[97812.234257] usb-storage: device found at 6
[97812.234260] usb-storage: waiting for device to settle before scanning
[97817.225402] usb-storage: device scan complete
[97817.226227] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[97817.237198] sd 6:0:0:0: [sdb] Attached SCSI disk
[97817.237258] sd 6:0:0:0: Attached scsi generic sg2 type 0

```Doing some searching, I found that I had to install hfsutils, hfsprogs, and hfsplus; 
and did that. 



I also ran the diskmounter script (wget [http://media.ubuntu-nl.org/scripts/diskmounter](http://media.ubuntu-nl.org/scripts/diskmounter)), 
as recommended on [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
but the mac hard drive was not detected.

Then, I received some advice in the irc channel to ensure the appropriate kernel modules were loaded: 
I did that: 

modprobe -l|grep hfs
/lib/modules/2.6.24-19-generic/ubuntu/fs/squashfs/squashfs.ko
/lib/modules/2.6.24-19-generic/kernel/net/sched/sch_hfsc.ko
/lib/modules/2.6.24-19-generic/kernel/fs/hfs/hfs.ko
/lib/modules/2.6.24-19-generic/kernel/fs/hfsplus/hfsplus.ko

i then did: sudo modprobe hfs 
and sudo modprobe hfsplus 

Following the directions on [http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus), 

I ran parted, but it did not detect the hard drive:

```

skorasaurus@skorasaurus-lappy:~$ sudo parted /dev/sda
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  78.8GB  78.8GB  primary   ntfs         boot 
 2      78.8GB  160GB   81.2GB  extended                    
 5      78.8GB  157GB   77.8GB  logical   ext3              
 6      157GB   160GB   3356MB  logical   linux-swap      

```This line (I presume after I ran parted, but I'm not sure), displayed as well
in the syslog: 
```

Oct  8 13:02:32 skorasaurus-lappy kernel: [98245.245807] program parted is using a deprecated SCSI ioctl, please convert it to SG_IO

```So, 
How can I mount this ?


EDIT: 
I restarted my computer with the drive already attached and this was my /var/log/syslog/ :
[code]
Oct 18 07:52:52 skorasaurus-lappy syslogd 1.5.0#1ubuntu1: restart.
Oct 18 07:52:52 skorasaurus-lappy anacron[20244]: Job `cron.daily' terminated
Oct 18 07:52:52 skorasaurus-lappy anacron[20244]: Normal exit (1 job run)
Oct 18 08:08:27 skorasaurus-lappy -- MARK --
Oct 18 08:17:01 skorasaurus-lappy /USR/SBIN/CRON[21445]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 18 08:28:27 skorasaurus-lappy -- MARK --
Oct 18 08:48:27 skorasaurus-lappy -- MARK --
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <debug> [1224335191.633500] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Day Man' 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / Day Man 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Deactivating device eth1. 
Oct 18 09:06:31 skorasaurus-lappy avahi-daemon[5231]: Withdrawing address record for 169.254.6.220 on eth1.
Oct 18 09:06:31 skorasaurus-lappy avahi-daemon[5231]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.6.220.
Oct 18 09:06:31 skorasaurus-lappy avahi-daemon[5231]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 18 09:06:31 skorasaurus-lappy avahi-daemon[5231]: Withdrawing address record for fe80::222:69ff:fe0a:ef69 on eth1.
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) started... 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'Day Man' is encrypted, but NO valid key exists.  New key needed. 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'Day Man'. 
Oct 18 09:06:31 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <debug> [1224335197.520702] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'gary_motel' 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / gary_motel 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Deactivating device eth1. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) started... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'gary_motel' is encrypted, but NO valid key exists.  New key needed. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'gary_motel'. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key for network 'gary_motel' received. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:37 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'gary_motel' is encrypted, and a key exists.  No new key needed. 
Oct 18 09:06:38 skorasaurus-lappy NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was '0' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 676172795f6d6f74656c' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:39 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <debug> [1224335206.485140] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'gary_motel' 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / gary_motel 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Deactivating device eth1. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) started... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'gary_motel' is encrypted, but NO valid key exists.  New key needed. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'gary_motel'. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key for network 'gary_motel' received. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:46 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'gary_motel' is encrypted, and a key exists.  No new key needed. 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was '0' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 676172795f6d6f74656c' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:48 skorasaurus-lappy NetworkManager: <info>  Supplicant state changed: 0 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key request for network 'Day Man' was canceled. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) failure scheduled... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) failed for access point (Day Man) 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) failed. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Deactivating device eth1. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth1'. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Will activate connection 'eth1/gary_motel'. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) started... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:53 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'gary_motel' is encrypted, and a key exists.  No new key needed. 
Oct 18 09:06:54 skorasaurus-lappy NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was '0' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 676172795f6d6f74656c' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <debug> [1224335215.959086] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'gary_motel' 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth1 / gary_motel 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  Deactivating device eth1. 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelling... 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handler scheduled... 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): waiting for device to cancel activation. 
Oct 18 09:06:55 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) cancellation handled. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1): cancelled. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <WARN>  nm_device_802_11_wireless_set_wep_enc_key(): error setting key for device eth1: Invalid argument 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Device eth1 activation scheduled... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) started... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'gary_motel' is encrypted, but NO valid key exists.  New key needed. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'gary_motel'. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) New wireless user key for network 'gary_motel' received. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Oct 18 09:06:56 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless): access point 'gary_motel' is encrypted, and a key exists.  No new key needed. 
Oct 18 09:06:57 skorasaurus-lappy NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 18 09:06:57 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 18 09:06:57 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: response was '0' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 676172795f6d6f74656c' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  SUP: response was 'OK' 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Oct 18 09:06:58 skorasaurus-lappy NetworkManager: <info>  Supplicant state changed: 0 
Oct 18 09:07:06 skorasaurus-lappy kernel: [59867.103047] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Oct 18 09:07:06 skorasaurus-lappy NetworkManager: <info>  Supplicant state changed: 1 
Oct 18 09:07:06 skorasaurus-lappy NetworkManager: <info>  Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'gary_motel'. 
Oct 18 09:07:06 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 18 09:07:06 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Oct 18 09:07:08 skorasaurus-lappy avahi-daemon[5231]: Registering new address record for fe80::222:69ff:fe0a:ef69 on eth1.*.
Oct 18 09:07:08 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Oct 18 09:07:08 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Oct 18 09:07:08 skorasaurus-lappy NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Oct 18 09:07:08 skorasaurus-lappy avahi-autoipd(eth1)[17178]: Got SIGTERM, quitting.
Oct 18 09:07:08 skorasaurus-lappy avahi-autoipd(eth1)[17178]: Callout STOP, address 169.254.6.220 on interface eth1
Oct 18 09:07:08 skorasaurus-lappy avahi-autoipd(eth1)[17179]: client: RTNETLINK answers: Cannot assign requested address
Oct 18 09:07:08 skorasaurus-lappy avahi-autoipd(eth1)[17179]: Script execution failed with return value 2
Oct 18 09:07:10 skorasaurus-lappy NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Oct 18 09:07:14 skorasaurus-lappy dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Oct 18 09:07:14 skorasaurus-lappy dhclient: DHCPOFFER of 192.168.0.112 from 192.168.0.1
Oct 18 09:07:14 skorasaurus-lappy dhclient: DHCPREQUEST of 192.168.0.112 on eth1 to 255.255.255.255 port 67
Oct 18 09:07:14 skorasaurus-lappy dhclient: DHCPACK of 192.168.0.112 from 192.168.0.1
Oct 18 09:07:14 skorasaurus-lappy avahi-daemon[5231]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.112.
Oct 18 09:07:14 skorasaurus-lappy avahi-daemon[5231]: New relevant interface eth1.IPv4 for mDNS.
Oct 18 09:07:14 skorasaurus-lappy avahi-daemon[5231]: Registering new address record for 192.168.0.112 on eth1.IPv4.
Oct 18 09:07:14 skorasaurus-lappy NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth1 
Oct 18 09:07:14 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 18 09:07:14 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started... 
Oct 18 09:07:14 skorasaurus-lappy dhclient: bound to 192.168.0.112 -- renewal in 4847 seconds.
Oct 18 09:07:15 skorasaurus-lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Oct 18 09:07:15 skorasaurus-lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Oct 18 09:07:15 skorasaurus-lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>    address 192.168.0.112 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>    netmask 255.255.255.0 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>    broadcast 192.168.0.255 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>    gateway 192.168.0.1 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>    nameserver 192.168.0.1 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>    domain name 'gha.chartermi.net' 
Oct 18 09:07:15 skorasaurus-lappy dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 18 09:07:15 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 18 09:07:15 skorasaurus-lappy avahi-daemon[5231]: Withdrawing address record for 192.168.0.112 on eth1.
Oct 18 09:07:15 skorasaurus-lappy avahi-daemon[5231]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.112.
Oct 18 09:07:15 skorasaurus-lappy avahi-daemon[5231]: Interface eth1.IPv4 no longer relevant for mDNS.
Oct 18 09:07:15 skorasaurus-lappy avahi-daemon[5231]: Withdrawing address record for fe80::222:69ff:fe0a:ef69 on eth1.
Oct 18 09:07:15 skorasaurus-lappy avahi-daemon[5231]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.112.
Oct 18 09:07:15 skorasaurus-lappy avahi-daemon[5231]: New relevant interface eth1.IPv4 for mDNS.
Oct 18 09:07:15 skorasaurus-lappy avahi-daemon[5231]: Registering new address record for 192.168.0.112 on eth1.IPv4.
Oct 18 09:07:16 skorasaurus-lappy NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 18 09:07:16 skorasaurus-lappy NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 18 09:07:16 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Finish handler scheduled. 
Oct 18 09:07:16 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 18 09:07:16 skorasaurus-lappy NetworkManager: <info>  Activation (eth1) successful, device activated. 
Oct 18 09:07:16 skorasaurus-lappy NetworkManager: <debug> [1224335236.245876] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'gary_motel' 
Oct 18 09:07:16 skorasaurus-lappy ntpdate[22319]: step time server 91.189.94.4 offset 2.120212 sec
Oct 18 09:07:19 skorasaurus-lappy avahi-daemon[5231]: Registering new address record for fe80::222:69ff:fe0a:ef69 on eth1.*.
Oct 18 09:07:28 skorasaurus-lappy kernel: [59886.487166] eth1: no IPv6 routers present
Oct 18 09:17:01 skorasaurus-lappy /USR/SBIN/CRON[22479]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 18 09:28:29 skorasaurus-lappy -- MARK --
Oct 18 09:48:29 skorasaurus-lappy -- MARK --
Oct 18 10:07:31 skorasaurus-lappy kernel: [63482.987402] usb 7-1: new high speed USB device using ehci_hcd and address 3
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.121080] usb 7-1: configuration #1 chosen from 1 choice
Oct 18 10:07:31 skorasaurus-lappy NetworkManager: <debug> [1224338851.169394] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6'). 
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.579463] usbcore: registered new interface driver libusual
Oct 18 10:07:31 skorasaurus-lappy NetworkManager: <debug> [1224338851.662616] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0'). 
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.632764] Initializing USB Mass Storage driver...
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.633279] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.634007] usbcore: registered new interface driver usb-storage
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.634018] USB Mass Storage support registered.
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.634296] usb-storage: device found at 3
Oct 18 10:07:31 skorasaurus-lappy kernel: [63483.634300] usb-storage: waiting for device to settle before scanning
Oct 18 10:07:36 skorasaurus-lappy kernel: [63488.627128] usb-storage: device scan complete
Oct 18 10:07:36 skorasaurus-lappy kernel: [63488.627969] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Oct 18 10:07:36 skorasaurus-lappy kernel: [63488.631399] sd 4:0:0:0: [sdb] Attached SCSI disk
Oct 18 10:07:36 skorasaurus-lappy kernel: [63488.631485] sd 4:0:0:0: Attached scsi generic sg2 type 0
Oct 18 10:07:36 skorasaurus-lappy NetworkManager: <debug> [1224338856.804366] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host'). 
Oct 18 10:07:36 skorasaurus-lappy NetworkManager: <debug> [1224338856.808184] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host_scsi_device_lun0'). 
Oct 18 10:07:36 skorasaurus-lappy NetworkManager: <debug> [1224338856.809722] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_152d_2338_152D203380B6_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Oct 18 10:07:36 skorasaurus-lappy NetworkManager: <debug> [1224338856.918179] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_JMicron_USB_to_ATA_ATAPI_Bridge_152D203380B6_0_0'). 
Oct 18 10:17:01 skorasaurus-lappy /USR/SBIN/CRON[23666]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 18 10:28:03 skorasaurus-lappy dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.0.1 port 67
Oct 18 10:28:39 skorasaurus-lappy last message repeated 3 times
Oct 18 10:29:48 skorasaurus-lappy last message repeated 4 times
Oct 18 10:30:57 skorasaurus-lappy last message repeated 5 times
Oct 18 10:31:58 skorasaurus-lappy last message repeated 6 times
Oct 18 10:32:18 skorasaurus-lappy init: tty4 main process (4786) killed by TERM signal
Oct 18 10:32:18 skorasaurus-lappy init: tty5 main process (4787) killed by TERM signal
Oct 18 10:32:18 skorasaurus-lappy init: tty2 main process (4789) killed by TERM signal
Oct 18 10:32:18 skorasaurus-lappy init: tty3 main process (4791) killed by TERM signal
Oct 18 10:32:18 skorasaurus-lappy init: tty6 main process (4793) killed by TERM signal
Oct 18 10:32:18 skorasaurus-lappy init: tty1 main process (5783) killed by TERM signal
Oct 18 10:32:19 skorasaurus-lappy dhclient: DHCPREQUEST of <null address> on eth1 to 192.168.0.1 port 67
Oct 18 10:32:21 skorasaurus-lappy gdm[5600]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Oct 18 10:32:21 skorasaurus-lappy gdm[5600]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Oct 18 10:32:21 skorasaurus-lappy avahi-daemon[5231]: Got SIGTERM, quitting.
Oct 18 10:32:21 skorasaurus-lappy avahi-daemon[5231]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.112.
Oct 18 10:32:21 skorasaurus-lappy NetworkManager: <info>  Supplicant state changed: 0 
Oct 18 10:32:21 skorasaurus-lappy dhclient: receive_packet failed on eth1: Network is down
Oct 18 10:32:22 skorasaurus-lappy kernel: [64972.068977] ip6_tables: (C) 2000-2006 Netfilter Core Team
Oct 18 10:32:23 skorasaurus-lappy exiting on signal 15
Oct 18 10:33:16 skorasaurus-lappy syslogd 1.5.0#1ubuntu1: restart.
Oct 18 10:33:16 skorasaurus-lappy kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 18 10:33:16 skorasaurus-lappy kernel: Loaded 27890 symbols from /boot/System.map-2.6.24-21-generic.
Oct 18 10:33:16 skorasaurus-lappy kernel: Symbols match kernel version 2.6.24.
Oct 18 10:33:16 skorasaurus-lappy kernel: Loaded 22211 symbols from 104 modules.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008 (Ubuntu 2.6.24-21.42-generic)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6df000 (ACPI NVS)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000bf6df000 - 00000000c0000000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] 2166MB HIGHMEM available.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] 896MB LOWMEM available.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] found SMP MP-table at 000f7d60
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Entering add_active_range(0, 0, 784080) 0 entries of 256 used
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Zone PFN ranges:
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   DMA             0 ->     4096
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   Normal       4096 ->   229376
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   HighMem    229376 ->   784080
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Movable zone start PFN for each node
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]     0:        0 ->   784080
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] On node 0 totalpages: 784080
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   HighMem zone: 4333 pages used for memmap
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   HighMem zone: 550371 pages, LIFO batch:31
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] DMI present.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F7BF0 checksum 0
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: RSDP 000F7BF0, 0024 (r2 PTLTD )
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: XSDT BF6D0A71, 009C (r1 ACRSYS ACRPRDCT  6040000 INNA        0)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: FACP BF6DBBD7, 00F4 (r3 INTEL  CRESTLNE  6040000 ALAN        1)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: DSDT BF6D2BBA, 8FA9 (r2 INTEL  CRESTLNE  6040000 MSFT  3000000)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: FACS BF6DEFC0, 0040
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: HPET BF6DBCCB, 0038 (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: MCFG BF6DBD03, 003C (r1 INTEL  CRESTLNE  6040000 LOHR       5A)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: TCPA BF6DBD3F, 0032 (r1 Intel   CRESTLN  6040000          5A52)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: TMOR BF6DBD71, 0026 (r1 PTLTD            6040000 PTL         3)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: SLIC BF6DBD97, 0176 (r1 ACRSYS ACRPRDCT  6040000 ANNI        1)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: ASF! BF6DBF0D, 0063 (r32 OEMID  OEMTBL    6040000 PTL         1)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: APIC BF6DBF70, 0068 (r1 PTLTD  ^I APIC    6040000  LTP        0)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: BOOT BF6DBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: SSDT BF6D256B, 064F (r1 SataRe  SataPri     1000 INTL 20050624)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: SSDT BF6D1ED9, 0692 (r1 SataRe  SataSec     1000 INTL 20050624)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: SSDT BF6D1D0E, 01CB (r1 BrtRef  DD01BRT     1000 INTL 20050624)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: SSDT BF6D10C9, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: SSDT BF6D1023, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050624)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: SSDT BF6D0B0D, 0516 (r1  PmRef    CpuPm     3000 INTL 20050624)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: DMI detected: Acer
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Processor #0 6:15 APIC version 20
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Processor #1 6:15 APIC version 20
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000e0000
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777955
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Kernel command line: root=UUID=09db1760-5e81-4abb-a75e-cbf878c32868 ro quiet splash
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Initializing CPU#0
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 18 10:33:16 skorasaurus-lappy kernel: [    0.000000] Detected 1862.058 MHz processor.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.489118] Console: colour VGA+ 80x25
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.489121] console [tty0] enabled
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.489459] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.489746] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642149] Memory: 3097860k/3136320k available (2177k kernel code, 37240k reserved, 1006k data, 368k init, 2218816k highmem)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642156] virtual kernel memory layout:
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642157]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642158]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642159]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642160]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642161]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642161]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642162]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642165] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642209] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.642349] hpet clockevent registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722217] Calibrating delay using timer specific routine.. 3728.27 BogoMIPS (lpj=7456559)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722240] Security Framework initialized
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722246] SELinux:  Disabled at boot.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722260] AppArmor: AppArmor initialized
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722264] Failure registering capabilities with primary security module.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722272] Mount-cache hash table entries: 512
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722400] Initializing cgroup subsys ns
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722405] Initializing cgroup subsys cpuacct
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722415] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722421] monitor/mwait feature present.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722423] using mwait in idle threads.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722427] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722429] CPU: L2 cache: 1024K
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722432] CPU: Physical Processor ID: 0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722433] CPU: Processor Core ID: 0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722435] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722445] Compat vDSO mapped to ffffe000.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.722457] Checking 'hlt' instruction... OK.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.738567] SMP alternatives: switching to UP code
Oct 18 10:33:16 skorasaurus-lappy kernel: [   18.740113] Early unpacking initramfs... done
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.064973] ACPI: Core revision 20070126
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.065026] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.210367] CPU0: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz stepping 0d
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.210383] SMP alternatives: switching to SMP code
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.211074] Booting processor 1/1 eip 3000
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.221165] Initializing CPU#1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301210] Calibrating delay using timer specific routine.. 3724.05 BogoMIPS (lpj=7448106)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301217] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301221] monitor/mwait feature present.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301224] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301226] CPU: L2 cache: 1024K
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301228] CPU: Physical Processor ID: 0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301229] CPU: Processor Core ID: 1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301230] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301662] CPU1: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz stepping 0d
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301684] Total of 2 processors activated (7452.33 BogoMIPS).
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.301869] ENABLING IO-APIC IRQs
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.302066] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.449065] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469043] Brought up 2 CPUs
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469066] CPU0 attaching sched-domain:
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469068]  domain 0: span 03
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469070]   groups: 01 02
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469073] CPU1 attaching sched-domain:
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469074]  domain 0: span 03
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469075]   groups: 02 01
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469278] net_namespace: 64 bytes
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469288] Booting paravirtualized kernel on bare hardware
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469710] Time: 10:32:51  Date: 10/18/08
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469737] NET: Registered protocol family 16
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469905] EISA bus registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.469909] ACPI: bus type pci registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.470359] PCI: PCI BIOS revision 3.00 entry at 0xfdba1, last bus=16
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.470361] PCI: Using configuration type 1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.470375] Setting up standard PCI resources
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.472687] ACPI: EC: Look up EC in DSDT
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.475026] ACPI: BIOS _OSI(Linux) query ignored via DMI
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.475029] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.475840] ACPI: Interpreter enabled
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.475843] ACPI: (supports S0 S3 S4 S5)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.475856] ACPI: Using IOAPIC for interrupt routing
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.900560] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.900562] ACPI: EC: driver started in poll mode
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.900602] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.901672] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.901677] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.903188] PCI: Transparent bridge - 0000:00:1e.0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.903279] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.903552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.903676] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.903798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
Oct 18 10:33:16 skorasaurus-lappy kernel: [   19.903939] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.697953] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698055] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698155] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698253] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698351] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698450] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698548] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698645] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698789] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698817] pnp: PnP ACPI init
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.698824] ACPI: bus type pnp registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.701474] ACPI: EC: non-query interrupt received, switching to interrupt mode
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.901203] pnp: PnP ACPI: found 11 devices
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.901206] ACPI: ACPI bus type pnp unregistered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.901210] PnPBIOS: Disabled by ACPI PNP
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.901403] PCI: Using ACPI for IRQ routing
Oct 18 10:33:16 skorasaurus-lappy kernel: [   23.901405] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.072972] NET: Registered protocol family 8
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.072974] NET: Registered protocol family 20
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.073003] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.073007] hpet0: 3 64-bit timers, 14318180 Hz
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.074042] AppArmor: AppArmor Filesystem Enabled
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.076846] Time: tsc clocksource has been installed.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.076855] Switched to high resolution mode on CPU 0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.076958] Switched to high resolution mode on CPU 1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089567] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089570] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089572] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089575] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089577] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089580] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089582] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089591] system 00:06: iomem range 0xfed00000-0xfed003ff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089598] system 00:08: ioport range 0x800-0x80f has been reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089600] system 00:08: ioport range 0x1000-0x107f has been reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089603] system 00:08: ioport range 0x1180-0x11bf has been reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089605] system 00:08: ioport range 0xfe00-0xfe00 has been reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.089608] system 00:08: iomem range 0xff800000-0xff800fff could not be reserved
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119940] PCI: Bridge: 0000:00:1c.0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119943]   IO window: 2000-2fff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119950]   MEM window: f6000000-f7ffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119955]   PREFETCH window: f0000000-f1ffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119961] PCI: Bridge: 0000:00:1c.1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119964]   IO window: 3000-3fff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119970]   MEM window: f8000000-f9ffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119975]   PREFETCH window: f2000000-f3ffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119981] PCI: Bridge: 0000:00:1c.2
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119984]   IO window: 4000-4fff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119990]   MEM window: fa000000-fbffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.119994]   PREFETCH window: f4000000-f5ffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120004] PCI: Bus 16, cardbus bridge: 0000:0f:06.0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120005]   IO window: 00001400-000014ff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120010]   IO window: 00005000-000050ff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120016]   PREFETCH window: c4000000-c7ffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120021]   MEM window: c8000000-cbffffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120026] PCI: Bridge: 0000:00:1e.0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120027]   IO window: disabled.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120034]   MEM window: fc200000-fc2fffff
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120038]   PREFETCH window: disabled.
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120074] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120081] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120109] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120114] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120141] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120147] PCI: Setting latency timer of device 0000:00:1c.2 to 64
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120162] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120179] ACPI: PCI Interrupt 0000:0f:06.0[A] -> GSI 22 (level, low) -> IRQ 19
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.120194] NET: Registered protocol family 2
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.157481] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.157706] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.158209] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.158554] TCP: Hash tables configured (established 131072 bind 65536)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.158557] TCP reno registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.169572] checking if image is initramfs... it is
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.805540] Freeing initrd memory: 7707k freed
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.805700] Simple Boot Flag at 0x36 set to 0x1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.806272] audit: initializing netlink socket (disabled)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.806285] audit(1224325975.764:1): initialized
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.806515] highmem bounce pool size: 64 pages
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808274] VFS: Disk quotas dquot_6.5.1
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808351] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808481] io scheduler noop registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808483] io scheduler anticipatory registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808485] io scheduler deadline registered
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808495] io scheduler cfq registered (default)
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808509] Boot video device is 0000:00:02.0
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808738] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808803] assign_interrupt_mode Found MSI capability
Oct 18 10:33:16 skorasaurus-lappy kernel: [   24.808858] Allocate Port Service[0000:00:1c.0:pcie00]

---

### Post by keyshawn on 2008-10-13
polite bump.

---

