---
title: "Trouble reading DVD/CDs with a USB device"
date: 2009-11-24
forum: Hardware
---

### Post by gzipper on 2009-11-24
I have tried the supposed "fixes" (editing fstab and eject) but cant get the drive to read any disks. I tried several disks I know works, and all were data CD/DVD disks. Mounting it doesn't even get the drive to spin as if its not even trying to read.

Its a USB device. Worked fine under 9.04 and 8.04. Manual mounting doesn't work either, though if I boot without a disk the drive will show up under "Places" but immediatly I insert a disc it dissapears with following message in syslog:

```
desktop kernel: [  208.265663] sr 8:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
desktop kernel: [  208.265666] sr 8:0:0:0: [sr0] Sense Key : Illegal Request [current] 
desktop kernel: [  208.265669] sr 8:0:0:0: [sr0] Add. Sense: Logical block address out of range
desktop kernel: [  208.265672] end_request: I/O error, dev sr0, sector 0
desktop kernel: [  208.265674] __ratelimit: 30 callbacks suppressed
desktop kernel: [  208.265676] Buffer I/O error on device sr0, logical block 0
desktop kernel: [  208.267412] sr 8:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
desktop kernel: [  208.267415] sr 8:0:0:0: [sr0] Sense Key : Illegal Request [current] 
desktop kernel: [  208.267417] sr 8:0:0:0: [sr0] Add. Sense: Logical block address out of range
desktop kernel: [  208.267419] end_request: I/O error, dev sr0, sector 0
desktop kernel: [  208.267420] Buffer I/O error on device sr0, logical block 0
desktop kernel: [  208.289166] cdrom: This disc doesn't have any tracks I recognize!
desktop kernel: [  208.327165] sr 8:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
desktop kernel: [  208.327169] sr 8:0:0:0: [sr0] Sense Key : Illegal Request [current] 
desktop kernel: [  208.327172] sr 8:0:0:0: [sr0] Add. Sense: Logical block address out of range
desktop kernel: [  208.327176] end_request: I/O error, dev sr0, sector 0
desktop kernel: [  208.327179] Buffer I/O error on device sr0, logical block 0
desktop kernel: [  208.329790] sr 8:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
desktop kernel: [  208.329793] sr 8:0:0:0: [sr0] Sense Key : Illegal Request [current] 
desktop kernel: [  208.329796] sr 8:0:0:0: [sr0] Add. Sense: Logical block address out of range
desktop kernel: [  208.329799] end_request: I/O error, dev sr0, sector 0
desktop kernel: [  208.329801] Buffer I/O error on device sr0, logical block 0
```


System info:

dmesg | grep -i DVD -n10

```
829-[   11.000062] usb-storage: device scan complete
830:[   11.030062] scsi 8:0:0:0: CD-ROM            TSSTcorp CDDVDW SE-S224Q  TS00 PQ: 0 ANSI: 0
831:[   11.035429] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
832-[   11.035431] Uniform CD-ROM driver Revision: 3.20
833-[   11.035488] sr 8:0:0:0: Attached scsi CD-ROM sr0
834-[   11.035524] sr 8:0:0:0: Attached scsi generic sg6 type 5
835-[   77.469614] xor: automatically using best checksumming function: generic_sse
836-[   77.510003]    generic_sse: 11938.800 MB/sec


```

Something is causing the boot to hang for a long time...

lshw -C disk
```
*-cdrom
       description: DVD-RAM writer
       product: CDDVDW SE-S224Q
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=nodisc


```

Thanks for any input.

---

