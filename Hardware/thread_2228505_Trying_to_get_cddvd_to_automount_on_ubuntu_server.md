---
title: "Trying to get cd/dvd to automount on ubuntu server"
date: 2014-06-07
forum: Hardware
---

### Post by wesley-johnb on 2014-06-07
Hello,

I am trying to automount CDs and DVDs on my server running ubuntu server 12.04. Im having issue mounting it manually(much less mounting it automatically). My end goal is to be able to insert and disc and then access is from across the network.

when I run:

```
sudo mount -t iso9660 /dev/sr0 /media/cdrom
```
i get this:
```

mount: block device /dev/[  704.249893] sr 2:0:0:0: [sr0]  
[  704.249896] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  704.249897] sr 2:0:0:0: [sr0]  
[  704.249898] Sense Key : Illegal Request [current] 
[  704.249900] sr 2:0:0:0: [sr0]  
[  704.249902] Add. Sense: Illegal mode for this track
[  704.249904] sr 2:0:0:0: [sr0] CDB: 
[  704.249905] Read(10): 28 00 00 00 00 10 00 00 01 00
[  704.249909] end_request: I/O error, dev sr0, sector 64
[  704.249945] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So then I ran this:
```
dmesg | tail
```

it outputs:
```

[  704.249893] sr 2:0:0:0: [sr0]  
[  704.249896] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  704.249897] sr 2:0:0:0: [sr0]  
[  704.249898] Sense Key : Illegal Request [current] 
[  704.249900] sr 2:0:0:0: [sr0]  
[  704.249902] Add. Sense: Illegal mode for this track
[  704.249904] sr 2:0:0:0: [sr0] CDB: 
[  704.249905] Read(10): 28 00 00 00 00 10 00 00 01 00
[  704.249909] end_request: I/O error, dev sr0, sector 64
[  704.249945] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

Is there anything special I need to have installed for this sort of thing to work? I tried using autofs and I'm getting the error message as I get when I try and manually mount it.

thanks

---

### Post by wesley-johnb on 2014-06-13
Anyone? I'm trying to share the drive across the network. I want to be able to stick a CD in and play it on another machine

---

