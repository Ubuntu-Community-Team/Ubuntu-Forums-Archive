---
title: "Vista's Disk Check Ruined My External HDD"
date: 2010-01-08
forum: Hardware
---

### Post by omaralqady on 2010-01-08
I have a 320GB Western Digital My Passport Essential external HDD, which usually works fine in both Ubuntu and Vista except that when I connect it to Vista it gave a warning about something being wrong with it and an option to either do a disk check or continue and I usually dismissed the warning and continued until yesterday when Ubuntu warned me about bad sectors on the same disk, and I don't know how to repair bad sectors in FAT32 in Ubuntu so I used Vista's disk check and checked the "Scan for and attempt recovery of bad sectors", and "Automatically fix file system errors", and left it overnight and when I woke up it was still not done, so I cancelled it. After that Vista was not able to read the disk, and Ubuntu doesn't mount it and GParted doesn't read it, but the "Disk Utility" in Ubuntu reads as a non partitioned WD external HDD "2199 GB"! and when I tried fdisk -l it does not list it. Here is the output of "sudo lsusb":
```
omar@3omar:~$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 002 Device 003: ID 064e:a103 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1058:0704 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 15d9:0a33 Unknown 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
And here is the output of "dmesg | tail":
```
omar@3omar:~$ dmesg | tail
[37152.574612] sd 9:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[37152.574617] sd 9:0:0:0: [sdc] Sense Key : Illegal Request [current] 
[37152.574624] Info fld=0x0
[37152.574626] sd 9:0:0:0: [sdc] Add. Sense: Logical block address out of range
[37152.574634] end_request: I/O error, dev sdc, sector 2775038072
[37152.577645] sd 9:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[37152.577650] sd 9:0:0:0: [sdc] Sense Key : Illegal Request [current] 
[37152.577655] Info fld=0x0
[37152.577657] sd 9:0:0:0: [sdc] Add. Sense: Logical block address out of range
[37152.577663] end_request: I/O error, dev sdc, sector 2775037984

```
I'm currently running "testdisk" on the disk but it is also reading it as a 2199 GB drive and it's counting up cylinders and the bottom line reads "Read error at x/2/1" and x is increasing one by one so it's taking a terribly long time and I'm not sure that this will even work so I thought I'd use this time to look up other possibilities.

Sorry for such a lengthy post :) but I would greatly appreciate all help and suggestions :)

---

