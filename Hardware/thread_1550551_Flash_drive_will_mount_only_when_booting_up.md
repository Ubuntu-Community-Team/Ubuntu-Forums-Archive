---
title: "Flash drive will mount only when booting up"
date: 2010-08-11
forum: Hardware
---

### Post by ajmburgos09 on 2010-08-11
Hi there. I'm currently using Jaunty. Flash drives normally automount when I connect them but at a certain point in time it stopped working. They only mounted when I connect them while Jaunty is still booting up.

---

### Post by pastalavista on 2010-08-11
> **ajmburgos09 said:**
> Hi there. I'm currently using Jaunty. Flash drives normally automount when I connect them but at a certain point in time it stopped working. They only mounted when I connect them while Jaunty is still booting up.
You shouldn't have that problem if you unmount the drive before you remove it. Also, if you have several different versions of the drive in the "Computer" window of Nautilus, remove them all.

---

### Post by ajmburgos09 on 2010-08-11
> **pastalavista said:**
> You shouldn't have that problem if you unmount the drive before you remove it. Also, if you have several different versions of the drive in the "Computer" window of Nautilus, remove them all.

I experimented a little. When I was rebooting I plugged in the flash drive. After logging in, I could see that the flash drive is mounted. I unmounted, unplugged, then plugged it back again, but it wasn't mounted by ubuntu.

---

### Post by pastalavista on 2010-08-11
In that case, run Alt+F2 'gconf-editor' & open Apps/Nautilus/Preferences & make sure 'media_automount' is enabled (checked)

---

### Post by ajmburgos09 on 2010-08-11
I don't know if this would help...

```
tail -f /var/log/messages
Aug 11 18:24:43 alvin-laptop kernel: [ 3257.019304] usb 2-4: configuration #1 chosen from 1 choice
Aug 11 18:24:43 alvin-laptop kernel: [ 3257.026618] scsi410 : SCSI emulation for USB Mass Storage devices
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.036431] scsi 410:0:0:0: Direct-Access     Kingston DataTraveler 120 PMAP PQ: 0 ANSI: 0 CCS
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.090380] sd 410:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.096272] sd 410:0:0:0: [sdb] Write Protect is off
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.120269] sd 410:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.131266] sd 410:0:0:0: [sdb] Write Protect is off
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.131298]  sdb: sdb1
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.152992] sd 410:0:0:0: [sdb] Attached SCSI removable disk
Aug 11 18:24:48 alvin-laptop kernel: [ 3262.153143] sd 410:0:0:0: Attached scsi generic sg2 type 0
Aug 11 18:32:39 alvin-laptop kernel: [ 3733.029109] usb 2-4: USB disconnect, address 3
Aug 11 18:32:41 alvin-laptop kernel: [ 3735.025068] usb 1-7: new high speed USB device using ehci_hcd and address 10
Aug 11 18:32:41 alvin-laptop kernel: [ 3735.281111] usb 1-7: no configuration chosen from 0 choices
Aug 11 18:32:41 alvin-laptop kernel: [ 3735.281360] usb 1-7: USB disconnect, address 10
Aug 11 18:32:41 alvin-laptop kernel: [ 3735.520101] usb 1-7: new high speed USB device using ehci_hcd and address 11
Aug 11 18:32:42 alvin-laptop kernel: [ 3735.795390] usb 1-7: no configuration chosen from 0 choices
Aug 11 18:32:42 alvin-laptop kernel: [ 3735.795558] usb 1-7: USB disconnect, address 11
Aug 11 18:32:42 alvin-laptop kernel: [ 3736.033075] usb 1-7: new high speed USB device using ehci_hcd and address 12
Aug 11 18:32:42 alvin-laptop kernel: [ 3736.176177] usb 1-7: configuration #1 chosen from 1 choice
Aug 11 18:32:42 alvin-laptop kernel: [ 3736.185686] scsi411 : SCSI emulation for USB Mass Storage devices
Aug 11 18:32:47 alvin-laptop kernel: [ 3741.201808] scsi 411:0:0:0: Direct-Access     Kingston DataTraveler 120 PMAP PQ: 0 ANSI: 0 CCS
Aug 11 18:32:47 alvin-laptop kernel: [ 3741.532257] usb 1-7: reset high speed USB device using ehci_hcd and address 12
Aug 11 18:32:48 alvin-laptop kernel: [ 3742.238332] sd 411:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
Aug 11 18:32:48 alvin-laptop kernel: [ 3742.241734] sd 411:0:0:0: [sdb] Write Protect is off
Aug 11 18:32:48 alvin-laptop kernel: [ 3742.248586] sd 411:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
Aug 11 18:32:48 alvin-laptop kernel: [ 3742.249609] sd 411:0:0:0: [sdb] Write Protect is off
Aug 11 18:32:48 alvin-laptop kernel: [ 3742.249634]  sdb: sdb1
Aug 11 18:32:48 alvin-laptop kernel: [ 3742.250844] sd 411:0:0:0: [sdb] Attached SCSI removable disk
Aug 11 18:32:48 alvin-laptop kernel: [ 3742.250989] sd 411:0:0:0: Attached scsi generic sg2 type 0
Aug 11 18:32:49 alvin-laptop kernel: [ 3743.225186] usb 1-7: USB disconnect, address 12
Aug 11 18:32:49 alvin-laptop kernel: [ 3743.225321] sd 411:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 11 18:32:49 alvin-laptop kernel: [ 3743.225495] sd 411:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 11 18:32:49 alvin-laptop kernel: [ 3743.476081] usb 1-7: new high speed USB device using ehci_hcd and address 13
Aug 11 18:32:49 alvin-laptop kernel: [ 3743.610298] usb 1-7: configuration #1 chosen from 1 choice
Aug 11 18:32:49 alvin-laptop kernel: [ 3743.612224] scsi412 : SCSI emulation for USB Mass Storage devices
Aug 11 18:32:54 alvin-laptop kernel: [ 3748.624802] scsi 412:0:0:0: Direct-Access     Kingston DataTraveler 120 PMAP PQ: 0 ANSI: 0 CCS
Aug 11 18:32:54 alvin-laptop kernel: [ 3748.639800] sd 412:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
Aug 11 18:32:54 alvin-laptop kernel: [ 3748.640400] sd 412:0:0:0: [sdb] Write Protect is off
Aug 11 18:32:54 alvin-laptop kernel: [ 3748.647039] sd 412:0:0:0: [sdb] 7837696 512-byte hardware sectors: (4.01 GB/3.73 GiB)
Aug 11 18:32:54 alvin-laptop kernel: [ 3748.647655] sd 412:0:0:0: [sdb] Write Protect is off
Aug 11 18:32:54 alvin-laptop kernel: [ 3748.647679]  sdb: sdb1
Aug 11 18:32:55 alvin-laptop kernel: [ 3748.675319] sd 412:0:0:0: [sdb] Attached SCSI removable disk
Aug 11 18:32:55 alvin-laptop kernel: [ 3748.681053] sd 412:0:0:0: Attached scsi generic sg2 type 0
Aug 11 18:32:55 alvin-laptop kernel: [ 3749.323222] usb 1-7: USB disconnect, address 13
Aug 11 18:32:55 alvin-laptop kernel: [ 3749.323353] sd 412:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 11 18:32:55 alvin-laptop kernel: [ 3749.323514] sd 412:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Aug 11 18:32:55 alvin-laptop kernel: [ 3749.577158] usb 1-7: new high speed USB device using ehci_hcd and address 14
Aug 11 18:32:56 alvin-laptop kernel: [ 3749.710098] usb 1-7: configuration #1 chosen from 1 choice
Aug 11 18:32:56 alvin-laptop kernel: [ 3749.718140] scsi413 : SCSI emulation for USB Mass Storage devices
```

---

### Post by ajmburgos09 on 2010-08-11
> **pastalavista said:**
> In that case, run Alt+F2 'gconf-editor' & open Apps/Nautilus/Preferences & make sure 'media_automount' is enabled (checked)

I tried it and media_automount is enabled.

---

### Post by pastalavista on 2010-08-11
Well then, what kind of filesystem is on the drive? Have you hard-disconnected (without safely removing) from a Windows or Mac? If it has a Mac or Windows filesystem on it, you'll need to mount it on that machine and do a checkdisk to make it mountable on Linux again. If you can remember more about what you did before rather than since it stopped working, it would be easier to solve.

---

### Post by ajmburgos09 on 2010-08-12
I did a checkdisk on my flash drive in Vista and then safely removed it but it still isn't mounted. I think I'll have to try my luck by installing 10.04.

---

### Post by ajmburgos09 on 2010-08-12
Thanks for the help. I'll try my luck on 10.04.

---

