---
title: "Problem Mounting DVDs on CD/DVD combo (Hardy)"
date: 2009-05-05
forum: Hardware
---

### Post by j_niquito30 on 2009-05-05
Hi everyone,

I have a HP Pavilion DV6448se. I recently changed from PCLinuxOS to Ubuntu Hardy. Last night, I realized that I couldn't mount/play/read DVDs but I was able to do the same with CDs. I searched the forum and came up with couple of solutions:

* Re-installed the libdvd files along with hal
* Installed the libdvdcss from the mediaubuntu repo
* Installed VLC and other Media Players
* sudo mount -t iso9660 /dev/scd0 /media/cdrom0

But none of these worked for me. Here is the cat /etc/fstab
```


# /dev/sda5
UUID=22d7b8b8-2335-4d0d-8a45-01efc9e9102c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

Also, the error msg's from dmesg
```


[  162.722887] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  162.722894] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  162.722898] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[  162.722903] end_request: I/O error, dev sr0, sector 64
[  162.722907] Buffer I/O error on device sr0, logical block 8
[  165.132951] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  165.132958] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  165.132962] sr 2:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  165.132967] end_request: I/O error, dev sr0, sector 64
[  165.132970] Buffer I/O error on device sr0, logical block 8
[  166.768927] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  166.768934] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  166.768938] sr 2:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  166.768943] end_request: I/O error, dev sr0, sector 0
[  166.768947] Buffer I/O error on device sr0, logical block 0
[  166.768953] Buffer I/O error on device sr0, logical block 1
[  168.540987] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  168.540992] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  168.540996] sr 2:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  168.541000] end_request: I/O error, dev sr0, sector 0
[  168.541003] Buffer I/O error on device sr0, logical block 0
[  170.200812] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  170.200819] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  170.200823] sr 2:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  170.200828] end_request: I/O error, dev sr0, sector 0
[  170.200832] Buffer I/O error on device sr0, logical block 0
[  197.257440] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  197.257449] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  197.257454] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[  197.257458] end_request: I/O error, dev sr0, sector 64
[  197.257517] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[  500.590495] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  500.590504] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  500.590509] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[  500.590514] end_request: I/O error, dev sr0, sector 64
[  500.590518] Buffer I/O error on device sr0, logical block 8
[  504.343585] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  504.343593] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  504.343598] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[  504.343602] end_request: I/O error, dev sr0, sector 64
[  504.343605] Buffer I/O error on device sr0, logical block 8
[  507.866488] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  507.866498] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  507.866503] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[  507.866507] end_request: I/O error, dev sr0, sector 0
[  507.866511] Buffer I/O error on device sr0, logical block 0
[  507.866519] Buffer I/O error on device sr0, logical block 1
[  510.820241] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  510.820249] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  510.820254] sr 2:0:0:0: [sr0] Add. Sense: No seek complete
[  510.820258] end_request: I/O error, dev sr0, sector 0
[  510.820261] Buffer I/O error on device sr0, logical block 0


```

And finally, sudo lshw -C disk

```


  *-cdrom                 
       description: DVD-RAM writer
       product: DVD A  DS8AZH
       vendor: Slimtype
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NH61
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom


```

I'd appreciate any suggestion or a fix. Thank you !!!

---

