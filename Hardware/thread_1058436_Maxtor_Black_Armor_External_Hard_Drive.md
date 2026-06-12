---
title: "Maxtor Black Armor External Hard Drive"
date: 2009-02-02
forum: Hardware
---

### Post by 72andsunny on 2009-02-02
Hi all,

I'm having a little trouble getting my computer to recognize this new external hard drive. When I plug it in, I get an "unable to mount drive" message. I've tried partitioning it with GParted, but I get "Error while setting new disklabel".

I'm new to Ubuntu, any help would be appreciated; here's some info from my post in the beginner's forum:

________________________________________________________________________

please post here the output of
Code:

sudo lshw -C disk -sanitize|less

and
Code:

sudo lspci

to enter these commands, you will need to get a command line interface -for instance by Applications>Accessories>Terminal or Konsole or just alt+ctrl+F2 (to go back to the desktop use alt+ctrl+f7)
First one just said: (END)

Here's the other

:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

---

### Post by sedawk on 2009-02-02
Start Ubuntu without the drive.
Clean the message buffer with "sudo dmesg -c"
Connect the drive (and turn it on).
Wait 20 seconds
Run "dmesg" and post the output here.

---

### Post by 72andsunny on 2009-02-02
> **sedawk said:**
> Start Ubuntu without the drive.
Clean the message buffer with "sudo dmesg -c"
Connect the drive (and turn it on).
Wait 20 seconds
Run "dmesg" and post the output here.
 
Hope this is everything:

:~$ dmesg
[  122.376062] usb 5-3: new high speed USB device using ehci_hcd and address 2
[  122.522246] usb 5-3: configuration #1 chosen from 1 choice
[  122.525939] scsi2 : SCSI emulation for USB Mass Storage devices
[  122.527146] usb-storage: device found at 2
[  122.527164] usb-storage: waiting for device to settle before scanning
[  126.757847] usb-storage: device scan complete
[  126.760094] scsi 2:0:0:0: Direct-Access     Maxtor_  BlackArmor       101J PQ: 0 ANSI: 4
[  126.761720] scsi 2:0:0:1: CD-ROM            Maxtor_  VirtualCDROM          PQ: 0 ANSI: 0
[  126.766538] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  126.768278] sd 2:0:0:0: [sdb] Write Protect is off
[  126.768303] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[  126.768315] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  126.771891] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[  126.773385] sd 2:0:0:0: [sdb] Write Protect is off
[  126.773407] sd 2:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[  126.773418] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  126.773436]  sdb: unknown partition table
[  126.795927] sd 2:0:0:0: [sdb] Attached SCSI disk
[  126.796108] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  126.799852] sr0: scsi3-mmc drive: 50x/61x caddy
[  126.799872] Uniform CD-ROM driver Revision: 3.20
[  126.800067] sr 2:0:0:1: Attached scsi CD-ROM sr0
[  126.800229] sr 2:0:0:1: Attached scsi generic sg2 type 5
[  128.108743] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  128.108774] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  128.108793] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  128.108812] end_request: I/O error, dev sdb, sector 312581632
[  128.108827] Buffer I/O error on device sdb, logical block 39072704
[  129.061699] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  129.061717] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  129.061727] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  129.061738] end_request: I/O error, dev sdb, sector 312581632
[  129.061746] Buffer I/O error on device sdb, logical block 39072704
[  130.017209] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  130.017238] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  130.017255] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  130.017275] end_request: I/O error, dev sdb, sector 312581792
[  130.017291] Buffer I/O error on device sdb, logical block 39072724
[  130.986690] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  130.986719] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  130.986738] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  130.986757] end_request: I/O error, dev sdb, sector 312581792
[  130.986772] Buffer I/O error on device sdb, logical block 39072724
[  131.955242] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  131.955272] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  131.955291] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  131.955311] end_request: I/O error, dev sdb, sector 312581800
[  131.955326] Buffer I/O error on device sdb, logical block 39072725
[  132.919817] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  132.919846] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  132.919864] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  132.919883] end_request: I/O error, dev sdb, sector 312581800
[  132.919899] Buffer I/O error on device sdb, logical block 39072725
[  133.892056] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  133.892087] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  133.892106] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  133.892126] end_request: I/O error, dev sdb, sector 312581800
[  133.892141] Buffer I/O error on device sdb, logical block 39072725
[  134.863131] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  134.863161] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  134.863180] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  134.863199] end_request: I/O error, dev sdb, sector 312581800
[  134.863214] Buffer I/O error on device sdb, logical block 39072725
[  135.816716] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  135.816756] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  135.816774] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  135.816794] end_request: I/O error, dev sdb, sector 312581800
[  135.816811] Buffer I/O error on device sdb, logical block 39072725
[  136.775699] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  136.775727] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  136.775747] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  136.775766] end_request: I/O error, dev sdb, sector 312581800
[  136.775782] Buffer I/O error on device sdb, logical block 39072725
[  137.755652] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  137.755682] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  137.755700] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  137.755719] end_request: I/O error, dev sdb, sector 312581800
[  137.755735] Buffer I/O error on device sdb, logical block 39072725
[  138.742598] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  138.742627] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  138.742647] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  138.742665] end_request: I/O error, dev sdb, sector 312581744
[  138.742681] Buffer I/O error on device sdb, logical block 39072718
[  139.407158] UDF-fs: Partition marked readonly; forcing readonly mount
[  139.570017] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'BLACKARMOR', timestamp 2008/04/17 08:57 (1e20)
[  139.727670] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  139.727699] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  139.727718] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  139.727737] end_request: I/O error, dev sdb, sector 312581792
[  140.716984] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  140.717014] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  140.717032] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  140.717051] end_request: I/O error, dev sdb, sector 312581800
[  141.666688] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  141.666707] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  141.666716] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  141.666726] end_request: I/O error, dev sdb, sector 312581800
[  143.053286] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  143.053316] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  143.053335] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  143.053354] end_request: I/O error, dev sdb, sector 312581632
[  144.005412] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  144.005443] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  144.005461] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  144.005481] end_request: I/O error, dev sdb, sector 312581632
[  144.005494] printk: 4 messages suppressed.
[  144.005518] Buffer I/O error on device sdb, logical block 39072704
[  144.951261] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  144.951290] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  144.951309] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  144.951328] end_request: I/O error, dev sdb, sector 312581792
[  145.902336] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  145.902365] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  145.902383] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  145.902403] end_request: I/O error, dev sdb, sector 312581792
[  146.853103] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  146.853133] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  146.853153] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  146.853173] end_request: I/O error, dev sdb, sector 312581800
[  147.806333] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  147.806364] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  147.806383] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  147.806403] end_request: I/O error, dev sdb, sector 312581800
[  148.751804] sd 2:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  148.751833] sd 2:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[  148.751852] sd 2:0:0:0: [sdb] Add. Sense: No additional sense information
[  148.751871] end_request: I/O error, dev sdb, sector 312581800
[  148.751885] printk: 4 messages suppressed.
[  148.751897] Buffer I/O error on device sdb, logical block 39072725

---

### Post by 72andsunny on 2009-02-03
anyone think i'd have better luck with a different brand?

---

### Post by minsf on 2009-02-03
rather than having 2 threads on the same issue, and wasting people's time, please close one of them (add [SOLVED] to the original title).

---

### Post by minsf on 2009-02-03
EDIT: Forget it. i was suggesting you use gparted to get a new partition table because dmesg complains about this, but i didnt notice that you have already tried to do it. ignore this post

---

### Post by sedawk on 2009-02-03
The first lines are okay, but then you are getting lots of errors in "dmesg"
output. Try using a different USB port or a different USB cable and
see if the errors are gone.
(E.g. use rear ports on your PC, front ports are known to be buggy with
 high-speed devices like hard-disks. Use a (short) USB 2.0 cable).

---

