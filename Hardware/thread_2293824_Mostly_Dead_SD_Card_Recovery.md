---
title: "Mostly Dead SD Card Recovery"
date: 2015-09-07
forum: Hardware
---

### Post by djfische on 2015-09-07
I just returned from an Alaskan cruise where my camera SD card died. I had a spare SD card and I continued taking photos but I have a busted card with a couple days of photos on it and I'd like to try to recover it if I can.

The camera is a Nikon DSLR and it formats cards as good old FAT, not exFAT or anything. The card in question is 16GB Patriot SDHC class 6 card. The card is a bit old and I probably should have replaced it. The card had been formatted by the camera not long before. I always format my empty cards with the camera regularly after dumping photos. I was taking photos, I turned the camera off and turned it back on and then suddenly the camera just said the SD card is unusable. I was in roughly 45F/7C weather at the time. At no point in the trip did the camera get below freezing.

The card is not being recognized whatsoever on Ubuntu, Mac or Windows. Dmesg shows nothing when unplugging or plugging in the card. Dmesg also shows nothing when running gparted. I've verified that my card reader is good as I've tried with a couple other cards I have. I've also tried the card on a Mac and a separate Windows computer with built-in card readers. It doesn't even show up in the disk utilities let alone mounting. I'm running Ubuntu 14.04 here and the software is up-to-date.

```
% sudo fdisk -l
# shows only /dev/sda, the card reader is /dev/sdb
% sudo fdisk -l /dev/sdb
# returns nothing, status code = 0
# takes about 5 full seconds to return nothing
# when the card reader is empty, this returns instantly

% sudo gparted /dev/sdb
# runs for about 20 seconds and then displays the message
# "Error opening /dev/sdb: No medium found"

% sudo testdisk /list
# Shows only /dev/sda
# It takes about 10 seconds longer to run when my SD card is in the reader
# but the result is the same
% sudo testdisk /dev/sdb
# Runs for about 10 seconds and then displays:
# **&#8203;**Unable to open file or device /dev/sdb

% sudo ddrescue -vv /dev/sdb busted-card.out ddrescue.log
ddrescue: Can't open input file: No medium found
# No other output; so much for very verbose

% sudo hdparm -N /dev/sdb
/dev/sdb:
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 max sectors   = 0/1, HPA is enabled
# The hdparm output is exactly the same regardless of whether the SD card is in the reader or not
# However, if the card is in the reader, it takes about 10 seconds and if the card reader is empty
# it is immediate
% sudo hdparm -I --verbose  /dev/sdb
/dev/sdb:
outgoing cdb:  85 08 0e 00 00 00 01 00 00 00 00 00 00 40 ec 00
SG_IO: ATA_16 status=0x2, host_status=0x0, driver_status=0x8
SG_IO: sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
incoming_data:  2e 2e 2f 2e 2e 2f 2e 2e 2f 64 65 76 69 63 65 73 2f 70 63 69 30 30 30 30 3a 30 30 2f 30 30 30 30 3a 30 30 3a 31 31 2e 30 2f 30 30 30 30 3a 30 32 3a 30 35 2e 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: desc[]:  00 00
      ATA_16 stat=00 err=00 nsect=00 lbal=00 lbam=00 lbah=00 dev=00


ATA device, with non-removable media
    Serial Number:      00000:/000000::0110.
    Firmware Revision:  200:.50
Standards:
    Likely used: 1
Configuration:
    hard sectored
    soft sectored
    not MFM encoded 
    spindle motor control option
    disk xfer rate > 5Mbs, <= 10Mbs
    disk xfer rate > 5Mbs
    rotational speed tol.
    track offset option
    Logical        max    current
    cylinders    11823    0
    heads        11822    0
    sectors/track    25449    0
    --
    bytes/track: 25647    bytes/sector: 30309
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:  1736838406 MBytes
    device size with M = 1000*1000:  1821207068 MBytes (1821207 GB)
    cache/buffer size  = unknown
Capabilities:
    IORDY not likely
    Buffer type: 302f: dual port, multi-sector with read caching ability
    Buffer size: 6168.0kB    bytes avail on r/w long: 14896
    Cannot perform double-word IO
    R/W multiple sector transfer: not supported
    DMA: not supported
    PIO: pio0 
```

I'm basically in the position where I'm willing to spend a bit of time on this but I'm not willing to spend $100s or $1000s on data recovery. I'd spend ~$100 if I got the photos on there.

Any suggestions are welcome and thanks in advance.

I'm reminded of the Miracle Max scene from Princess Bride and that's why I named the thread like I did. Hopefully my card is not all dead and all I can do is search for loose change.

---

### Post by tgalati4 on 2015-09-08
Install *testdisk* and use *photorec* to recover photos.

```
sudo apt-get install testdisk
man photorec
```

This only works if the SD card mounts correctly or is recognized by *fdisk*.

Since it appears that you have already installed *testdisk*, then you need to investigate techniques to improve mounting the SD card.  Try different readers, cameras, laptops, TV's, anything with an SD slot.  If you can bring it up, then there is a chance to revive it.  Was the card bent during traveling?  A bent card can break the small electronic traces and cause this condition.

---

### Post by djfische on 2015-09-08
The card was not bent and should be in good shape except that it suddenly refused to mount. I don't see anything physical on the surface to make me think there is a problem. It was completely enclosed inside the DSLR and wasn't directly exposed to anything. It doesn't stick out like it does on some cameras.

I'll read about photorec and I'll try a couple different SD card readers.

---

