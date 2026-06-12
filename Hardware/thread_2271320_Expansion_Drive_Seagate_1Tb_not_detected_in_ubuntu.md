---
title: "Expansion Drive Seagate 1Tb not detected in ubuntu"
date: 2015-03-29
forum: Hardware
---

### Post by manikandan2 on 2015-03-29
I am trying to open expansion drive in ubuntu. But it is not detecting but the LED in drive is blinking. I followed some threads in ubuntu forums but nothing worked for me. I tried below.

**#dmesg | tail -n 20**


[13752.855063] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13752.855065] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13752.855066] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13752.855068] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[13870.290416] usb 3-4: USB disconnect, device number 17
[13870.290432] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290443] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290471] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290483] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290506] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290513] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290552] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290565] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[13870.290753] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[13870.290773] option 3-4:1.0: device disconnected
[13870.290888] eth1: unregister 'huawei_ether' usb-0000:00:14.0-4, Huawei Ethernet Device
[13870.311570] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[13870.311585] option 3-4:1.2: device disconnected
[13870.311717] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[13870.311726] option 3-4:1.3: device disconnected


Help me what to do now.I have some important files in my drive.

---

### Post by matt_symes on 2015-03-29
Hi

It looks like your GSM USB modem is having problems as well as evidenced by the dmesg output. There is nothing in the dmesg output that references the hard drive.

Try plugging the USB hard drive into a different port and seeing if that makes a difference. 

Also try booting into a LiveCD/USB and seeing if you can access the drive that way. That will eliminate updates that may have happened to your installed system.

Out of interest can you post links to the things you have already tried.

Kind regards

---

### Post by manikandan2 on 2015-03-29
I restart my system after that i tried again, and i got the below message.

 mca140@mca140-MANI:~$ dmesg | tail -n 20[   22.362344] ath: EEPROM regdomain: 0x8164
[   22.362346] ath: EEPROM indicates we should expect a country code
[   22.362347] ath: doing EEPROM country->regdmn map search
[   22.362348] ath: country maps to regdmn code: 0x5b
[   22.362349] ath: Country alpha2 being used: IN
[   22.362349] ath: Regpair used: 0x5b
[   22.362350] ath: regdomain 0x8164 dynamically updated by country IE
[   22.362366] cfg80211: Regulatory domain changed to country: IN
[   22.362366] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.362367] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.362368] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.362369] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   22.362370] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   24.975789] init: plymouth-upstart-bridge main process ended, respawning
[   25.001928] init: plymouth-upstart-bridge main process ended, respawning
[   29.825853] init: plymouth-stop pre-start process (1832) terminated with status 1
[   49.139231] audit_printk_skb: 129 callbacks suppressed
[   49.139233] type=1400 audit(1427649052.908:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2599 comm="apparmor_parser"
[   49.139238] type=1400 audit(1427649052.908:65): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2599 comm="apparmor_parser"
[   49.139528] type=1400 audit(1427649052.908:66): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2599 comm="apparmor_parser"
mca140@mca140-MANI:~$

---

### Post by Vladlenin5000 on 2015-03-29
Again, nothing to do with an external drive. 
Have you tried the suggestions in post #2 already? If so, what were the results?

---

### Post by manikandan2 on 2015-03-30
I tried the steps suggested in post #2 but its not working.

With Booting my drive is not detecting. and after changing port below message received for the command : 

mca140@mca140-MANI:~$ dmesg | tail -n 20
[10771.531061] scsi 9:0:0:0: Direct-Access     Seagate  Expansion        0636 PQ: 0 ANSI: 6
[10771.531813] sd 9:0:0:0: Attached scsi generic sg2 type 0
[10771.538468] sd 9:0:0:0: [sdb] Spinning up disk...
[10797.389986] usb 1-1.2: USB disconnect, device number 11
[10777.049397] ......................ready
[10798.167575] sd 9:0:0:0: [sdb] READ CAPACITY failed
[10798.167583] sd 9:0:0:0: [sdb]  
[10798.167586] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[10798.167589] sd 9:0:0:0: [sdb] Sense not available.
[10798.167671] sd 9:0:0:0: [sdb] Write Protect is off
[10798.167679] sd 9:0:0:0: [sdb] Mode Sense: 00 06 04 5e
[10798.167761] sd 9:0:0:0: [sdb] Asking for cache data failed
[10798.167768] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[10798.168349] sd 9:0:0:0: [sdb] READ CAPACITY failed
[10798.168356] sd 9:0:0:0: [sdb]  
[10798.168359] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[10798.168367] sd 9:0:0:0: [sdb] Sense not available.
[10798.168439] sd 9:0:0:0: [sdb] Asking for cache data failed
[10798.168446] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[10798.168452] sd 9:0:0:0: [sdb] Attached SCSI disk
mca140@mca140-MANI:~$

mca140@mca140-MANI:~$ sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000dc1ce


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482347007   241172480   83  Linux
/dev/sda2       482347008   964691967   241172480   83  Linux
/dev/sda3       964691968   976773119     6040576   82  Linux swap / Solaris
mca140@mca140-MANI:~$

---

### Post by matt_symes on 2015-04-01
Hi

Sorry for the delay in posting. I've been AFK.

This *may* be due to the delay used to let the drive settle down before reading the drive sense information.

I would certainly investigate this as a possibility.

Open a terminal and copy and paste this into it.

```
echo "options usb_storage delay_use=10" | sudo tee /etc/modprobe.d/usb_storage_delay.conf
```

Enter your password. It will not be echoed to the screen.

This will create the file usb_storage_delay.conf and change the delay to 10 seconds as opposed to 1 second.

Reboot your PC and plug the USB device into *the same port as you did for your last post*.

Is it detected ? There will be at least a 10 second delay! 

If it's detected then we can lower the delay time until we find the sweet spot. 

If it's not detected then post the dmesg output again.

Kind regards

---

### Post by mlnease on 2015-11-24
Hello,

I'm having an identical problem with my Seagate expansion drive.  I've tried:


[LIST=1]
[*]Try plugging the USB hard drive into a different port and seeing if that makes a difference. 
[*]Also try booting into a LiveCD/USB and seeing if you can access the drive that way. That will eliminate updates that may have happened to your installed system. 
[*]and ```
echo "options usb_storage delay_use=10" | sudo tee /etc/modprobe.d/usb_storage_delay.conf
``` 
[/LIST]
 but to no avail.

The Seagate LED lights up and the disk spins.

```
lsusb 
dmesg | tail
```
 returns:

```
mn@mn-OptiPlex-745-trusty:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bc2:5021 Seagate RSS LLC FreeAgent GoFlex USB 2.0
Bus 001 Device 005: ID 0bc2:2312 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mn@mn-OptiPlex-745-trusty:~$ dmesg | tail
[10020.155588] [UFW BLOCK] IN=wlan0 OUT= MAC=00:0d:54:aa:ef:52:30:10:b3:34:70:19:08:00 SRC=192.168.0.11 DST=192.168.0.8 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=34784 DF PROTO=UDP SPT=21979 DPT=17099 LEN=181 
[10133.060785] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[10258.159100] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[10382.253941] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[10507.353606] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[10632.447937] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[10757.544956] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[10882.637747] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[11007.734918] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[11133.155140] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:da:cc:48:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
mn@mn-OptiPlex-745-trusty:~$ 

```So I've found quite a few posts describing a similar problem with Seagate expansion drives but am not finding any solutions.

Any ideas, anyone?

Thanks in advance.

---

### Post by matt_symes on 2015-11-24
Hi

@mlnease.

Can we see if we can get some more info from  your logs.

Open a terminal and type

```
tail -f /var/log/syslog
```

Plug the drive into a USB port and wait for 20 seconds and post the entire output that tail followed from syslog.

dmesg is not the best log to be looking at. I'm hoping that will shed more light on what's happening.

After the drive has settled down can you also post the output of 

```
sudo parted -l
```

and finally this with the drive attached and settled.

```
sudo lshw -C storage
```

Hopefully we can get to the bottom of this.

I'm not convinced this is a hardware issue yet but we'll have to checkout that possibility at some point.

Kind regards

---

### Post by mlnease on 2015-11-24
> **matt_symes said:**
> Hi

@mlnease.

Can we see if we can get some more info from  your logs.

Open a terminal and type

```
tail -f /var/log/syslog
```

Plug the drive into a USB port and wait for 20 seconds and post the entire output that tail followed from syslog.

dmesg is not the best log to be looking at. I'm hoping that will shed more light on what's happening.

```
$ tail -f /var/log/syslog
Nov  24 15:20:55 mn-OptiPlex-745-trusty kernel: [ 5044.820037] scsi 6:0:0:0:  Direct-Access     Seagate  Expansion        0634 PQ: 0 ANSI: 6
Nov 24 15:20:55 mn-OptiPlex-745-trusty kernel: [ 5044.822390] sd 6:0:0:0: Attached scsi generic sg2 type 0
Nov 24 15:20:55 mn-OptiPlex-745-trusty mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3"
Nov 24 15:20:55 mn-OptiPlex-745-trusty mtp-probe: bus: 1, device: 6 was not an MTP device
Nov  24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.929873] sd 6:0:0:0:  [sdb] 1953525167 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.931342] sd 6:0:0:0: [sdb] Write Protect is off
Nov 24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.931347] sd 6:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Nov  24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.932351] sd 6:0:0:0:  [sdb] Write cache: enabled, read cache: enabled, supports DPO and FUA
Nov 24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.950384]  sdb:
Nov 24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.977357] sd 6:0:0:0: [sdb] Attached SCSI disk
```
      
After the drive has settled down can you also post the output of 

```
sudo parted -l
```

```
$ sudo parted -l
[sudo] password for mn: 
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  247GB  247GB   primary   ext4            boot
 2      247GB   500GB  253GB   extended
 6      247GB   494GB  247GB   logical   ext4
 5      494GB   500GB  6139MB  logical   linux-swap(v1)


Model: Seagate Expansion (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: Seagate FreeAgent GoFlex (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot
```

and finally this with the drive attached and settled.

```
sudo lshw -C storage
```
```
mn@mn-OptiPlex-745-trusty:~$ sudo lshw -C storage
[sudo] password for mn: 
  *-ide:0                 
       description: IDE interface
       product: 82801H (ICH8 Family) 4 port SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=ata_piix latency=0
        resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4)  ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=16)  ioport:ecc0(size=16)
  *-ide:1
       description: IDE interface
       product: 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode]
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list
       configuration: driver=ata_piix latency=0
        resources: irq:20 ioport:fe40(size=8) ioport:fe50(size=4)  ioport:fe60(size=8) ioport:fe70(size=4) ioport:fed0(size=16)  ioport:ecd0(size=16)
  *-scsi:0
       physical id: 1
       logical name: scsi0
       capabilities: emulated
  *-scsi:1
       physical id: 2
       logical name: scsi1
       capabilities: emulated
  *-scsi:2
       physical id: 3
       bus info: usb@1:3
       logical name: scsi6
  *-scsi:3
       physical id: 4
       bus info: usb@1:4
       logical name: scsi4
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
mn@mn-OptiPlex-745-trusty:~$ 
```

Hopefully we can get to the bottom of this.

I'm not convinced this is a hardware issue yet but we'll have to checkout that possibility at some point.

Kind regards

Thanks *very* much for your time and attention.

---

### Post by matt_symes on 2015-11-24
Hi

Keep the disc in the same port. Don't unplug it for the moment.

Interesting !

Your syslog messages are showing it's find the drive (sdb) but it's not finding any valid partitions for it.

That is also confirmed by the output from parted.

However the interesting thing is it's not binding the usb-storage module to the usb drive.

The is evidenced by the output of syslog and also confirmed by the output of lshw.

This is your device.

```
  *-scsi:2
       physical id: 3
       bus info: usb@1:3
       logical name: scsi6
```

It has no capabilities or driver loaded. It is also confirmed by the output from syslog.

```
"/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3"
```

So the question is why is there no driver being bound to the usb port.

Don't remove the drive yet. Keep it attached to the same port and powered.

I'm going to make coffee.

Kind regards

---

### Post by efflandt on 2015-11-24
What partitions do you (think you) have on that drive, or is it a fresh unformatted drive with no partitions on it yet?

---

### Post by mlnease on 2015-11-24
Thanks--wish I could brew you a cup.

---

### Post by matt_symes on 2015-11-24
Hi

> **efflandt said:**
> What partitions do you (think you) have on that drive, or is it a fresh unformatted drive with no partitions on it yet?

I'm not sure if the partitions are the main problem. 

I'm more confused as to why the drive is not showing the capabilities of *emulated scsi* and has no driver bound to it. Especially as the entry in syslog states...

```
Nov 24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.977357] sd 6:0:0:0: [sdb] Attached SCSI disk
```

This is from a pen drive that has been dd with data from /dev/zero. When plugged in it's still seen to what it is and a driver is bound to it.
```

  *-scsi:2
       physical id: 3
       bus info: usb@2:5
       logical name: scsi7
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
```

This is what i would expect so the OP's hard drive seems odd to me.

@mlnease. 

Can you create a bootable USB stick with an older version of Ubuntu (12.04) and see if the disk is recognised when you boot into it as a LiveCD.

Kind regards

---

### Post by mlnease on 2015-11-24
> **efflandt said:**
> What partitions do you (think you) have on that drive, or is it a fresh unformatted drive with no partitions on it yet?

Sorry, I'm quite ignorant of partitioning; that said though, I've been using this device successfully for a year or more (all my backups etc., including backups of quite a few DVDs) with ne'er a problem until yesterday.  So presumably there *are* (or at least *were*) partitions on the drive.

Thanks very much for your time and attention.

---

### Post by mlnease on 2015-11-24
> **matt_symes said:**
> Hi



I'm not sure if the partitions are the main problem. 

I'm more confused as to why the drive is not showing the capabilities of *emulated scsi* and has no driver bound to it. Especially as the entry in syslog states...

```
Nov 24 15:20:59 mn-OptiPlex-745-trusty kernel: [ 5048.977357] sd 6:0:0:0: [sdb] Attached SCSI disk
```

This is from a pen drive that has been dd with data from /dev/zero. When plugged in it's still seen to what it is and a driver is bound to it.
```

  *-scsi:2
       physical id: 3
       bus info: usb@2:5
       logical name: scsi7
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
```

This is what i would expect so the OP's hard drive seems odd to me.

@mlnease. 

Can you create a bootable USB stick with an older version of Ubuntu (12.04) and see if the disk is recognised when you boot into it as a LiveCD.

Kind regards

Unfortunately the only USB stick I have on hand contains some of the data now unavailable on the expansion drive so I'm reluctant to delete/format it for this purpose.  I'll try to rectify this soon and get back to you.

Thanks again for your time and for your patience.

---

### Post by matt_symes on 2015-11-24
Hi

> **mlnease said:**
> Unfortunately the only USB stick I have on hand contains some of the data now unavailable on the expansion drive so I'm reluctant to delete/format it for this purpose.  I'll try to rectify this soon and get back to you.

Thanks again for your time and for your patience.

No problem. I have to sleep now though as it's 1.30am here.

We can continue this tomorrow if you like. I'll be online in the evening.

Kind regards

---

### Post by mlnease on 2015-11-24
> **matt_symes said:**
> Hi



No problem. I have to sleep now though as it's 1.30am here.

We can continue this tomorrow if you like. I'll be online in the evening.

Kind regards
See you then--thanks again and pleasant dreams.

---

### Post by matt_symes on 2015-11-25
Hi

Was it readable from a LiveCD/USB ?

Kind regards

---

### Post by mlnease on 2015-11-25
> **matt_symes said:**
> Hi

Was it readable from a LiveCD/USB ?

Kind regards

Hello again and sorry for the slow reply--I still haven't got my hands on a USB stick but it was *not* readable from a LiveCD.

Thanks again for your continued interest in this problem.  I'm going to be away from my machine for a day or two but really look forward to resuming this correspondence.

---

### Post by matthew82 on 2015-11-27
I have a Seagate 1TB external that is recognized on my Hp Mini 311. I've never had issues with it not being recognized. Though that doesn't help you guys out. The Seagate 1TB External that I have is partitioned with the NTFS from factory. If there's anything I can do to help (being that mine is recognized) I'll certainly help. We shall get to the bottom of this!

---

### Post by matt_symes on 2015-11-27
Hi

@matthew82. Any help with this is greatly received.

> **mlnease said:**
> Hello again and sorry for the slow reply--I still haven't got my hands on a USB stick but it was *not* readable from a LiveCD.

Thanks again for your continued interest in this problem.  I'm going to be away from my machine for a day or two but really look forward to resuming this correspondence.

I was wondering what hdparm makes of the drive.

Can you post the output of these commands

```
sudo hdparm -I /dev/sdX
```

where X is the drive and not a partition. eg /dev/sdb.

```
sudo hdparm --read-sector 0 /dev/sdX
```

Kind regards

---

### Post by mlnease on 2015-11-28
Hello Again,

I hope you have the time and inclination to take up this correspondence again.  If I've understood you correctly, the outputs you requested are below.

Also I've got an 8GB SanDisk Cruzer thumb drive but don't yet know how to install Ubuntu onto it.  If anyone can refer me to a good tutorial I'd appreciate it very much.

> **matt_symes said:**
> Hi

@matthew82. Any help with this is greatly received.



I was wondering what hdparm makes of the drive.

Can you post the output of these commands

```
sudo hdparm -I /dev/sdX
```

where X is the drive and not a partition. eg /dev/sdb.
```
sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
    Model Number:       WDC WD5000AAKX-001CA0                   
    Serial Number:      WD-WCAYUE437193
    Firmware Revision:  15.01H15
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  976773168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      476940 MBytes
    device size with M = 1000*1000:      500107 MBytes (500 GB)
    cache/buffer size  = 16384 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 8
    Recommended acoustic management value: 128, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
            Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    NCQ priority information
            DMA Setup Auto-Activate optimization
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Read/Write Long (AC1), obsolete
       *    SCT Write Same (AC2)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    84min for SECURITY ERASE UNIT. 84min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50014ee2b027861d
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 2b027861d
Checksum: correct
```

```
sudo hdparm --read-sector 0 /dev/sdX
```
```
sudo hdparm --read-sector 0 /dev/sda

/dev/sda:
reading sector 0: succeeded
63eb 1090 d08e 00bc b8b0 0000 d88e c08e
befb 7c00 00bf b906 0200 a4f3 21ea 0006
be00 07be 0438 0b75 c683 8110 fefe 7507
ebf3 b416 b002 bb01 7c00 80b2 748a 8b01
024c 13cd 00ea 007c eb00 00fe 0000 0000
0000 0000 0000 0000 0000 8000 0001 0000
0000 0000 faff 9090 c2f6 7480 f605 70c2
0274 80b2 79ea 007c 3100 8ec0 8ed8 bcd0
2000 a0fb 7c64 ff3c 0274 c288 bb52 0417
07f6 7403 be06 7d88 17e8 be01 7c05 41b4
aabb cd55 5a13 7252 813d 55fb 75aa 8337
01e1 3274 c031 4489 4004 4488 89ff 0244
04c7 0010 8b66 5c1e 667c 5c89 6608 1e8b
7c60 8966 0c5c 44c7 0006 b470 cd42 7213
bb05 7000 76eb 08b4 13cd 0d73 845a 0fd2
d083 be00 7d93 82e9 6600 b60f 88c6 ff64
6640 4489 0f04 d1b6 e2c1 8802 88e8 40f4
4489 0f08 c2b6 e8c0 6602 0489 a166 7c60
0966 75c0 664e 5ca1 667c d231 f766 8834
31d1 66d2 74f7 3b04 0844 377d c1fe c588
c030 e8c1 0802 88c1 5ad0 c688 00bb 8e70
31c3 b8db 0201 13cd 1e72 c38c 1e60 00b9
8e01 31db bff6 8000 c68e f3fc 1fa5 ff61
5a26 be7c 7d8e 03eb 9dbe e87d 0034 a2be
e87d 002e 18cd feeb 5247 4255 0020 6547
6d6f 4800 7261 2064 6944 6b73 5200 6165
0064 4520 7272 726f 0a0d bb00 0001 0eb4
10cd 3cac 7500 c3f4 c100 0000 0000 2080
0021 fe83 ffff 0800 0000 a800 1cc0 fe00
ffff fe05 ffff b7fe 1cc0 a002 1d77 0000
0000 0000 0000 0000 0000 0000 0000 0000
0000 0000 0000 0000 0000 0000 0000 aa55
```

Kind regards
Thanks again for your time and attention.

---

### Post by matt_symes on 2015-11-28
Hi
```

Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
```

Your drive is frozen ?

Can you please post the output this command again to be sure. 

```
sudo hdparm -I /dev/sdX
```

Please could you not post it inside my post but outside like the command above. It's much, much easier for me to read on this laptop ( small screen, tired eyes :) )

Kind regards

---

### Post by mlnease on 2015-11-28
> **matt_symes said:**
> Hi
```

Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
```

Your drive is frozen ?

Can you please post the output this command again to be sure. 

```
sudo hdparm -I /dev/sdX
```

Please could you not post it inside my post but outside like the command above. It's much, much easier for me to read on this laptop ( small screen, tired eyes :) )

Kind regards

Sorry about that!  Better?
```

sudo hdparm -I /dev/sda
[sudo] password for mn: 

/dev/sda:

ATA device, with non-removable media
    Model Number:       WDC WD5000AAKX-001CA0                   
    Serial Number:      WD-WCAYUE437193
    Firmware Revision:  15.01H15
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors:  976773168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      476940 MBytes
    device size with M = 1000*1000:      500107 MBytes (500 GB)
    cache/buffer size  = 16384 KBytes
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 8
    Recommended acoustic management value: 128, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
            Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Gen3 signaling speed (6.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    NCQ priority information
            DMA Setup Auto-Activate optimization
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Read/Write Long (AC1), obsolete
       *    SCT Write Same (AC2)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    84min for SECURITY ERASE UNIT. 84min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50014ee2b027861d
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 2b027861d
Checksum: correct
```

---

### Post by matt_symes on 2015-11-28
Hi

> **mlnease said:**
> Sorry about that!  Better?

Yes. Thanks. I'm not the spring chicken i once was :D

```

sudo hdparm -I **/dev/sda**
[sudo] password for mn: 

...

Model Number:       **WDC WD5000AAKX-001CA0**                   
Serial Number:      WD-WCAYUE437193

....

Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        **frozen**
    not    expired: security count
        supported: enhanced erase
 ...

```

/dev/sda ? Model Number:       WDC WD5000AAKX-001CA0   , Serial Number:  WD-WCAYUE437193

^^^ This is *definitely* the external drive ? sd**a** ?

If so then hdparm is reporting the drive frozen.

The reason i'm asking if you're sure is due to the drives block device (sda) and the model WDC (western digital ?)

I don't doubt you're right but i just want to ask if you're sure that is the correct drive.

**EDIT**: Are you running these commands from a LiveCD/USB ? Just trying to understand sda.

Kind regards

---

### Post by mlnease on 2015-11-28
> **matt_symes said:**
> Hi



Yes. Thanks. I'm not the spring chicken i once was :D

Ditto!

```

sudo hdparm -I **/dev/sda**
[sudo] password for mn: 

...

Model Number:       **WDC WD5000AAKX-001CA0**                   
Serial Number:      WD-WCAYUE437193

....

Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        **frozen**
    not    expired: security count
        supported: enhanced erase
 ...

```

/dev/sda ? Model Number:       WDC WD5000AAKX-001CA0   , Serial Number:  WD-WCAYUE437193

^^^ This is *definitely* the external drive ? sd**a** ?

If so then hdparm is reporting the drive frozen.

The reason i'm asking if you're sure is due to the drives block device (sda) and the model WDC (western digital ?)

I don't doubt you're right but i just want to ask if you're sure that is the correct drive.

**EDIT**: Are you running these commands from a LiveCD/USB ? Just trying to understand sda.

Kind regards
Well--no, no and no--sorry, I got everything wrong.  dev/sda is where my ubuntu partitions are (on my Western Digital hard drive) and I'm running this from one of those partitions.  I'll reboot into a live cd and run the commands again, but I don't know on sd***?*** How can I determine which sd to use in the commands?

---

### Post by matt_symes on 2015-11-28
Hi

> How can I determine which sd to use in the commands? 

A sure fire way to tell is to use the output of syslog and when the drive is plugged in.

OPen a terminal and type

```
tail -f /var/log/syslog
```

Plug the external drive in and watch the text that appears. sdX should appear where X is the drive block device designator.

I was confused because i would not expect to see an external drive frozen.

So if you could run these commands again

```
sudo hdparm -I /dev/sdX
```

```
sudo hdparm --read-sector 0 /dev/sdX
```

Kind regards

---

### Post by mlnease on 2015-11-28
Well, hey now--outputs below:

> **matt_symes said:**
> Hi



A sure fire way to tell is to use the output of syslog and when the drive is plugged in.

OPen a terminal and type

```
tail -f /var/log/syslog
```

Plug the external drive in and watch the text that appears. sdX should appear where X is the drive block device designator.

I was confused because i would not expect to see an external drive frozen.

So if you could run these commands again

```
sudo hdparm -I /dev/sdX
```

```
sudo hdparm --read-sector 0 /dev/sdX
```

Kind regards

```
ubuntu@ubuntu:~$ tail -f /var/log/syslog
Nov 28 21:40:33 ubuntu kernel: [  730.014589] sd 6:0:0:0: [sdb] 1953525167 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 28 21:40:33 ubuntu kernel: [  730.015347] sd 6:0:0:0: [sdb] Write Protect is off
Nov 28 21:40:33 ubuntu kernel: [  730.015351] sd 6:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Nov 28 21:40:33 ubuntu kernel: [  730.015354] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Nov 28 21:40:33 ubuntu kernel: [  730.017417] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Nov 28 21:40:33 ubuntu kernel: [  730.017424]  sdb:
Nov 28 21:40:33 ubuntu kernel: [  730.032917] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Nov 28 21:40:33 ubuntu kernel: [  730.032922] sd 6:0:0:0: [sdb] Attached SCSI disk
Nov 28 21:43:21 ubuntu kernel: [  897.633014] usb 1-4: USB disconnect, address 5
Nov 28 21:43:39 ubuntu kernel: [  915.174112] usb 1-3: USB disconnect, address 6
Nov 28 21:44:22 ubuntu kernel: [  958.520064] usb 1-3: new high speed USB device using ehci_hcd and address 7
Nov 28 21:44:22 ubuntu kernel: [  958.672374] usb 1-3: configuration #1 chosen from 1 choice
Nov 28 21:44:22 ubuntu kernel: [  958.672649] scsi7 : SCSI emulation for USB Mass Storage devices
Nov 28 21:44:22 ubuntu kernel: [  958.672797] usb-storage: device found at 7
Nov 28 21:44:22 ubuntu kernel: [  958.672799] usb-storage: waiting for device to settle before scanning
Nov 28 21:44:27 ubuntu kernel: [  963.670233] usb-storage: device scan complete
Nov 28 21:44:27 ubuntu kernel: [  963.846869] scsi 7:0:0:0: Direct-Access     Seagate  Expansion        0634 PQ: 0 ANSI: 6
Nov 28 21:44:27 ubuntu kernel: [  963.847383] sd 7:0:0:0: Attached scsi generic sg2 type 0
Nov 28 21:44:27 ubuntu kernel: [  963.849348] sd 7:0:0:0: [sdb] 1953525167 512-byte logical blocks: (1.00 TB/931 GiB)
Nov 28 21:44:27 ubuntu kernel: [  963.850513] sd 7:0:0:0: [sdb] Write Protect is off
Nov 28 21:44:27 ubuntu kernel: [  963.850517] sd 7:0:0:0: [sdb] Mode Sense: 2b 00 10 08
Nov 28 21:44:27 ubuntu kernel: [  963.850519] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Nov 28 21:44:27 ubuntu kernel: [  963.852838] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Nov 28 21:44:27 ubuntu kernel: [  963.852845]  sdb:
Nov 28 21:44:27 ubuntu kernel: [  963.868209] sd 7:0:0:0: [sdb] Assuming drive cache: write through
Nov 28 21:44:27 ubuntu kernel: [  963.868214] sd 7:0:0:0: [sdb] Attached SCSI disk
```
Not sure what I'm reading though--I see the Seagate drive but does this tell me how to replace **X** in the commands?

---

### Post by matt_symes on 2015-11-28
Hi

The drive is

```
sdb
```

```
sudo hdparm -I /dev/sdb
sudo hdparm --read-sector 0 /dev/sdb
```

Kind regards

---

### Post by mlnease on 2015-11-28
That's what I was afraid of:

> **matt_symes said:**
> Hi

The drive is

```
sdb
```

```
sudo hdparm -I /dev/sdb
sudo hdparm --read-sector 0 /dev/sdb
```

Kind regards

```
ubuntu@ubuntu:~$ sudo hdparm -I /dev/sdb

/dev/sdb:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
ubuntu@ubuntu:~$
```

```
sudo hdparm --read-sector 0 /dev/sdb

/dev/sdb:
reading sector 0: FAILED: Invalid exchange
```

---

### Post by matt_symes on 2015-11-28
Hi

The next thing to do is to take the hard drive out of its external housing and put it into a computer.

Usually they're just SATA hard drives with some USB to SATA circuitry.

Take it out and put it into a PC - i.e try to read it without the USB to SATA bridge - and hope for the best.

If this works then get yourself a new housing. If not then sorry...

Kind regards

---

### Post by mlnease on 2015-11-28
> **matt_symes said:**
> Hi

The next thing to do is to take the hard drive out of its external housing and put it into a computer.

Usually they're just SATA hard drives with some USB to SATA circuitry.

Take it out and put it into a PC - i.e try to read it without the USB to SATA bridge - and hope for the best.

If this works then get yourself a new housing. If not then sorry...

Kind regards

OK, I'll try that.  I've tried to figure out how to open the housing before but that's another problem.

Thanks a million for all your time and advice.

Best Wishes,

mn

---

### Post by matt_symes on 2015-11-28
Hi

> **mlnease said:**
> OK, I'll try that.  I've tried to figure out how to open the housing before but that's another problem.

Thanks a million for all your time and advice.

Best Wishes,

mn

Please post back if it's a success or failure. 

It'll help me help others and it'll also help others when they have a similar problem, searching for a solution.

Kind regards

---

### Post by mlnease on 2015-11-28
> **matt_symes said:**
> Hi



Please post back if it's a success or failure. 

It'll help me help others and it'll also help others when they have a similar problem, searching for a solution.

Kind regards

Good reminder, thanks.  

Well, I managed to manhandle the housing off the hard drive thanks to a thoughtful tutorial [here]("http://amichalec.net/2012/12/opening-seagate-portable-drive/"); I would add to the author's instructions that considerable *force* is necessary to separate the components and yes, some studs will break.

I haven't attempted to install it in my tower yet but when I do I'll report the results here--with, I hope, the notation 'SOLVED'.

I would also add that--after my experiences with this device and those I've read about of so many others--I definitely will *not* buy another Seagate Expansion Drive.  I'd be interested to know if any readers have had better experiences with other brands of external hard drives.

---

### Post by matt_symes on 2015-11-28
Hi

> **mlnease said:**
> I would also add that--after my experiences with this device and those I've read about of so many others--I definitely will *not* buy another Seagate Expansion Drive.  I'd be interested to know if any readers have had better experiences with other brands of external hard drives.

I had a 1T Seagate external that failed. Took the hard drive out of its housing and the drive worked when plugged in via SATA.

I have a 2T Seagate external that has lasted me years now. 

Not really sure what to make of that as it's a tiny sample size.

BTW: Good luck.

Kind regards

---

### Post by mlnease on 2015-11-28
> **matt_symes said:**
> Hi



I had a 1T Seagate external that failed. Took the hard drive out of its housing and the drive worked when plugged in via SATA.

I have a 2T Seagate external that has lasted me years now. 

Not really sure what to make of that as it's a tiny sample size.

BTW: Good luck.

Kind regards

Interesting.  I wonder if the 1T's were less reliable than the 2T's--as I recall, most of the problems I read about were with 1T's.  At any rate, I'll be glad to add my tiny datum to your tiny sample.

That said, I guess part of my final frustration with the device was its physical inaccessibility.  It is a black box, clearly designed to prevent the end user's access.  

The author of the tutorial quoted a quip to the effect that "if you can't open it, you don't own it".  Maybe not literally true, but--especially as I'm really *not* a hardware guy--I must say it strikes a familiar chord.

BTW:  Thanks again!

---

### Post by mlnease on 2015-11-28
I've installed the stripped down drive in my tower to no avail.  As I've said though, I'm really not a hardware guy;  I haven't installed a lot of second hard drives and may have got something wrong.

So I have no way of knowing whether the fault lies in the USB to SATA bridge, my installation or elsewhere.  I guess that's the end of the line unless I take it to The Shop.

Thanks again for all your time and attention.

---

### Post by matt_symes on 2015-11-28
Hi

> **mlnease said:**
> I've installed the stripped down drive in my tower to no avail.  As I've said though, I'm really not a hardware guy;  I haven't installed a lot of second hard drives and may have got something wrong.

That's a shame. I was really hoping it would work right off the bat.

Do you have a local friend you could ask to check the connections ? 

BTW: I would run the hdparm commands against that drive again and see if you get the same errors.

Make sure you get the drive right. If you get the same errors then i would not hold out too much hope. 

hdparm is a low level tool that bypasses a lot of the file system functionality in the kernel and that is why it's so useful a tool. It can talk to the drive directly.

> So I have no way of knowing whether the fault lies in the USB to SATA bridge, my installation or elsewhere.  I guess that's the end of the line unless I take it to The Shop.

A simple test would be to put a working drive into the caddy and connect that to your PC and see if your PC can see if correctly.

> Thanks again for all your time and attention.

No problem at all.

Kind regards

---

### Post by matt_symes on 2015-11-29
Hi

I was going to suggest, if you want someone to check your cabling, take some photos (smart phone or digital camera) and attach them as images to your next post.

Someone can then take a look.

You may have to compress and reduce the dimensions of the photos to fit the forums image size and dimensions limits.

Kind regards

---

### Post by Bucky Ball on 2015-11-29
> **matt_symes said:**
> 
I was going to suggest, if you want someone to check your cabling, take some photos (smart phone or digital camera) and attach them as images to your next post.


A tip: Use 'Adv Reply' and the paperclip icon in the toolbar there to attach pics (rather than inserting them in the body of your post). Cheers. :)

---

### Post by mlnease on 2015-12-05
> **Bucky Ball said:**
> A tip: Use 'Adv Reply' and the paperclip icon in the toolbar there to attach pics (rather than inserting them in the body of your post). Cheers. :)
Please excuse the slow response and thanks for your attention--that was sound advice.

Unfortunately I did take it to the shop and the pros couldn't find the data (or the partition) either--so it's toast unless I pay for a serious retrieval effort, i.e. having the disk taken out and put into a new hard drive.

We may well do that--some of the data my wife had entrusted to this device is really valuable to her (family photos etc.).

What I take away from this is, don't entrust your backups (of anything) to an external hard drive.  From all the unsolved posts I've found on the subject, they can't be trusted to last.  Live and learn.

I hope others might learn from this *before* losing their data, but why would someone search for a solution before the problem occurs?

Thanks again all round.

---

### Post by Bucky Ball on 2015-12-05
Unfortunate outcome. As there is no 'resovled' button, please see first link in my signature for 'solved'. Thanks.

'Back in the old days' the theory was grandfather, father, son. Bit un-PC now and 'gender-ist' to call it that now, but what it essentially means is, for serious backup (business, the serious home user) you have your original, a backup of that, and a back up of the back up. Simple in theory, costly and a hassle in reality, but when you think about it, the only failsafe way of backing up your data, and even then, all three drives could fail at the same time! 

The rule also went that you had one copy (the original) on your computer, the back up on an external was stored in another part of the building away from the machine, the back up of the back up was stored off-premises. This covered just about everything: theft, fire, natural disaster, etc. But again, not 100% ... but probably about 99. 

Good luck in future with your backups and the OS. :)

---

### Post by mlnease on 2015-12-06
> **Bucky Ball said:**
> Unfortunate outcome. As there is no 'resovled' button, please see first link in my signature for 'solved'. Thanks.

'Back in the old days' the theory was grandfather, father, son. Bit un-PC now and 'gender-ist' to call it that now, but what it essentially means is, for serious backup (business, the serious home user) you have your original, a backup of that, and a back up of the back up. Simple in theory, costly and a hassle in reality, but when you think about it, the only failsafe way of backing up your data, and even then, all three drives could fail at the same time! 

The rule also went that you had one copy (the original) on your computer, the back up on an external was stored in another part of the building away from the machine, the back up of the back up was stored off-premises. This covered just about everything: theft, fire, natural disaster, etc. But again, not 100% ... but probably about 99. 

Good luck in future with your backups and the OS. :)

Sound advice again, thanks.  Though this is far from SOLVED for me, I'll defer to you and mark it as such.

Thanks again for your time and attention.

Sorry, but 'Mark Solved' doesn't appear under thread tools.

---

