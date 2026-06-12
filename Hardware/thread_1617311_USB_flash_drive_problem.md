---
title: "USB flash drive problem"
date: 2010-11-09
forum: Hardware
---

### Post by Merhawi on 2010-11-09
I have a 4GB USB flash drive that I have been using for about 5 months. It was functioning and suddenly stopped working when I mounted it into a computer. An ubuntu operating system does not totally recognize the device and in windows it gets displayed in 'My Computer' and cannot open it, format it, or anything else; it says the device is not accessible or could not be read. The same thing in Mac. I have used the device in a music player box that plays from usb flash and memory card. I have formated it once and it started to work again and now it's not working. I am looking forward to see solutions for my problems if you guys have any.
                                                              thanks in advance,
                                                              Merhawi

---

### Post by mastablasta on 2010-11-09
it could be that it reached the limit. every usb has a limited number of write cycles, don't know about how much reading it can take though...

---

### Post by Fafler on 2010-11-09
We need more info. Open a terminal. Type
```
tail -f /var/log/messages
```
Insert flashdrive. Post results.

---

### Post by Merhawi on 2010-11-10
I first invoked the command "tail -f /var/log/messages" before inserting the flash into the computer and found the following result:

```
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074023]  [<c01bdbed>] sys_write+0x3d/0x70
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074026]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074027] ---[ end trace 206bc8fc1b769790 ]---
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074054] Restarting tasks ... done.
Nov 10 17:35:56 lab3-pc26 kernel: [ 1914.668402] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 10 17:35:57 lab3-pc26 kernel: [ 1916.248876] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
Nov 10 17:35:57 lab3-pc26 kernel: [ 1916.248879] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Nov 10 17:35:57 lab3-pc26 kernel: [ 1916.249058] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 10 17:36:13 lab3-pc26 pulseaudio[4930]: pid.c: Stale PID file, overwriting.
Nov 10 17:37:32 lab3-pc26 syslogd 1.5.0#5ubuntu3: restart.
```

and the cursor was blinking as if it is processing something. Then I inserted the flash as found the following result (including the above result):

```
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074023]  [<c01bdbed>] sys_write+0x3d/0x70
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074026]  [<c0103f6b>] sysenter_do_call+0x12/0x2f
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074027] ---[ end trace 206bc8fc1b769790 ]---
Nov 10 17:35:55 lab3-pc26 kernel: [ 1914.074054] Restarting tasks ... done.
Nov 10 17:35:56 lab3-pc26 kernel: [ 1914.668402] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 10 17:35:57 lab3-pc26 kernel: [ 1916.248876] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
Nov 10 17:35:57 lab3-pc26 kernel: [ 1916.248879] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Nov 10 17:35:57 lab3-pc26 kernel: [ 1916.249058] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov 10 17:36:13 lab3-pc26 pulseaudio[4930]: pid.c: Stale PID file, overwriting.
Nov 10 17:37:32 lab3-pc26 syslogd 1.5.0#5ubuntu3: restart.
Nov 10 17:38:54 lab3-pc26 kernel: [ 2093.368018] usb 1-4: new high speed USB device using ehci_hcd and address 5
Nov 10 17:38:54 lab3-pc26 kernel: [ 2093.502405] usb 1-4: configuration #1 chosen from 1 choice
Nov 10 17:38:54 lab3-pc26 kernel: [ 2093.502720] scsi5 : SCSI emulation for USB Mass Storage devices
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.504944] scsi 5:0:0:0: Direct-Access     SKYMEDI  USB Drive        1.00 PQ: 0 ANSI: 2
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.506159] sd 5:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.514152] sd 5:0:0:0: [sdb] READ CAPACITY(16) failed
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.514156] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.514159] sd 5:0:0:0: [sdb] Use 0xffffffff as device size
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.514163] sd 5:0:0:0: [sdb] 4294967296 512-byte hardware sectors: (2.19 TB/2.00 TiB)
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.514650] sd 5:0:0:0: [sdb] Write Protect is off
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.517526] sd 5:0:0:0: [sdb] Very big device. Trying to use READ CAPACITY(16).
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.519773] sd 5:0:0:0: [sdb] READ CAPACITY(16) failed
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.519776] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.519779] sd 5:0:0:0: [sdb] Use 0xffffffff as device size
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.519783] sd 5:0:0:0: [sdb] 4294967296 512-byte hardware sectors: (2.19 TB/2.00 TiB)
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.520904] sd 5:0:0:0: [sdb] Write Protect is off
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.520913]  sdb:<3>end_request: I/O error, dev sdb, sector 0
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.521897] __ratelimit: 20 callbacks suppressed
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.531786] Dev sdb: unable to read RDB block 0
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.538529]  unable to read partition table
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.538624] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Nov 10 17:38:59 lab3-pc26 kernel: [ 2098.538690] sd 5:0:0:0: Attached scsi generic sg2 type 0
```

and still the mouse cursor was blinking; lab3 is the user name of the account I logged in as, and it's a limited account.


Thank you for trying to help me.

---

### Post by efflandt on 2010-11-10
It sounds like it is toast, because Linux cannot determine its size, is guessing (trying) 4294967296 512-byte hardware sectors: (2.19 TB/2.00 TiB) when it should be more like 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB), and cannot even read sector 0.

Note that the user you are running as should not affect the system recognizing the device and its partition(s) (lab3-pc26 is your computer name), that would only affect whether you can "mount" it if or after it is recognized as a drive and assigned /dev/sdb* devices.

---

### Post by Merhawi on 2010-11-11
I am not that experienced in the unix system and so couldn't understand the technical terms you used to explain the problem. But I want to know if there is any way of solving the problem with my flash drive; I can get access to an administrator account if there is any solution that needs administrative privilage. It's okay even if the solution is formating the flash, I got no data that I need, I only need the free memory that enables me save data in the future.
Thank you anyway!

---

### Post by vexorian on 2010-11-11
you should first confirm if it is an issue with ubuntu or the flash drive. For that, try a different computer, if the flash drive works, it is an issue with ubuntu.

Else, then it is probably really "toasted" which means that your flash drive died.

---

