---
title: "Travan tape drive"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by Koybe on 2007-03-22
Hi there,

I'm trying to get an old travan drive to work on ubuntu 6.06.
I had to modprobe ide-scsi, then here's what i get :

```
dmesg | grep hdf
[42949378.010000]     ide2: BM-DMA at 0x0900-0x0907, BIOS settings: hde:DMA, hdf:pio
[42949379.280000] hdf: Seagate STT20000A, ATAPI TAPE drive
[42949386.870000] ide-tape: hdf <-> ht0: Seagate STT20000A rev 8A51
[42949386.880000] ide-tape: hdf <-> ht0: 1000KBps, 6*54kB buffer, 9720kB pipeline, 110ms tDSC

```And i got error when tryning to don anything on the tape : 
```
 sudo mt -f /dev/ht0 status
ide-tape: ht0: I/O error, pc=34, key=3, asc=30, ascq=0
...
```I found some information by googling that ask to disable DMA on the drive... but hdf does not exist on my /dev :
```
sudo hdparm -d0 /dev/hdf
/dev/hdf: No such file or directory

```I tried to do it on /dev/ht0 but then I got again the I/O errors.

What can I do to make the tape drive working?

I tried this :
```
rmmod ide-tape
rmmod ide-scsi
modprobe ide-scsi
```

After that it is now scsi emulated... but I stil can't get it work :
```
[42949448.580000] SCSI subsystem initialized
[42949448.590000] scsi0 : SCSI host adapter emulation for IDE ATAPI devices
[42949448.590000]   Vendor: Seagate   Model: STT20000A         Rev: 8A51
[42949448.590000]   Type:   Sequential-Access                  ANSI SCSI revision: 02
[42949448.630000] st: Version 20050830, fixed bufsize 32768, s/g segs 256
[42949448.630000] st 0:0:0:0: Attached scsi tape st0<4>st0: try direct i/o: yes (alignment 512 B), max page reachable by HBA 1048575
[42949448.650000] st 0:0:0:0: Attached scsi generic sg0 type 1

```
```
sudo mt -f /dev/st0 status
mt: /dev/st0: Input/output error

```

Thank you for any help.

---

### Post by semjaza on 2008-07-12
I'm having this issue as well. . . anyone have a solution?

---

