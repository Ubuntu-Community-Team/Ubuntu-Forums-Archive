---
title: "Mounting (possibly broken) sd card"
date: 2013-01-05
forum: Hardware
---

### Post by JTatts on 2013-01-05
Hi, 

I'm trying to mount an sd card that is possibly broken. Other sd cards work fine with my system. The problem is that the card does not even mount so I cannot try to reformat.

```

dmesg | tail
```gives

```
[ 3645.165479] usb 3-3: New USB device strings: Mfr=3, Product=4, SerialNumber=2
[ 3645.165485] usb 3-3: Product: USB Storage
[ 3645.165489] usb 3-3: Manufacturer: Generic
[ 3645.165493] usb 3-3: SerialNumber: 000000000207
[ 3645.166074] usb 3-3: ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 3645.166090] usb 3-3: ep 0x2 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 3645.167264] scsi24 : usb-storage 3-3:1.0
[ 3646.164308] scsi 24:0:0:0: Direct-Access     Generic  STORAGE DEVICE   0207 PQ: 0 ANSI: 0
[ 3646.166790] sd 24:0:0:0: Attached scsi generic sg2 type 0
[ 3656.419908] sd 24:0:0:0: [sdc] Attached SCSI removable disk
```Any ideas?

---

### Post by Bucky Ball on 2013-01-05
Welcome to the forums. Please provide the output of:
```

sudo blkid
```... between [code] tags.

---

### Post by JTatts on 2013-01-05
Here you go:

```
/dev/sda1: LABEL="SYSTEM" UUID="FC64A40164A3BCB0" TYPE="ntfs" 
/dev/sda2: UUID="3C967DEC967DA6D4" TYPE="ntfs" 
/dev/sda3: LABEL="SAMSUNG_REC" UUID="5222B4FA22B4E3DF" TYPE="ntfs" 
/dev/sda5: UUID="86DE-360F" TYPE="vfat" 
/dev/sda6: UUID="661d96a6-4dbd-4b74-bd39-af2bdde27b18" TYPE="swap" 
/dev/sda7: UUID="aa36b1c4-615c-4078-9863-6ca1592d63db" TYPE="ext4" 
/dev/sdb1: UUID="40456a28-66dd-40f5-9363-bf287af5fc19" TYPE="ext4" 
```If I'm understanding correctly, the card doesn't appear.

---

### Post by Bucky Ball on 2013-01-05
I'm presuming the SD is:

```
/dev/sda5: UUID="86DE-360F" TYPE="vfat"
```

If not, what is that? Do you see the SD card there (possibly dev/sda3)?

---

### Post by JTatts on 2013-01-05
sda5 is a partition on my hard disk.

I'm not sure what sda3 is. However, if I mount a different sd card, it shows up in sdc1. Thanks for the helping by the way!

```
/dev/sda1: LABEL="SYSTEM" UUID="FC64A40164A3BCB0" TYPE="ntfs" 
/dev/sda2: UUID="3C967DEC967DA6D4" TYPE="ntfs" 
/dev/sda3: LABEL="SAMSUNG_REC" UUID="5222B4FA22B4E3DF" TYPE="ntfs" 
/dev/sda5: UUID="86DE-360F" TYPE="vfat" 
/dev/sda6: UUID="661d96a6-4dbd-4b74-bd39-af2bdde27b18" TYPE="swap" 
/dev/sda7: UUID="aa36b1c4-615c-4078-9863-6ca1592d63db" TYPE="ext4" 
/dev/sdb1: UUID="40456a28-66dd-40f5-9363-bf287af5fc19" TYPE="ext4" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="CANON_DC" UUID="54C9-0429" TYPE="vfat"
```

---

### Post by Bucky Ball on 2013-01-05
What is sda1 now?

---

### Post by JTatts on 2013-01-05
sda1 is my main installation partition.

---

### Post by Bucky Ball on 2013-01-05
Is the result of blkid with the sd card in the machine? If not, put it in and try again.

---

### Post by JTatts on 2013-01-05
Ah, did you mean sdc1?

That is when I use a different sd card which mounts correctly.

I was just showing the difference between a working sd card and the malfunctioning one.

---

### Post by JTatts on 2013-01-05
Sorry, I just realised that my posts have been confusing.

With the malfunctioning sd card, no device appears with blkid.

With a functioning sd card, the device appears as,

```

/dev/sdc1: SEC_TYPE="msdos" LABEL="CANON_DC" UUID="54C9-0429" TYPE="vfat"
```

---

### Post by Bucky Ball on 2013-01-05
Might suggest a dodgy sd card ...

Is it formatted? I'm guessing so. Does it work on another machine or in Windows?

---

### Post by JTatts on 2013-01-05
It's definitely dodgy......

I was just hoping that there may be a way to force mount the card so that I can try to reformat it.

---

### Post by Bucky Ball on 2013-01-05
Well, if not being seen then that will be hard. You could see if it works elsewhere and reformat there to see if it makes a difference I guess.

---

### Post by JTatts on 2013-01-05
The output of dmesg gave me hope that the card was being seen but then having some problem being mounted.

---

### Post by Bucky Ball on 2013-01-05
How were you attempting to mount it? Try these commands with it in:

```
sudo mkdir /mnt/sdc
sudo mnt /dev/sdc /mnt/sdc
```From the looks of dmesg, it has no partitions on it to mount and is possibly unformatted.

---

### Post by ajgreeny on 2013-01-05
Is it seen in gparted, which you can either install or use from the ubuntu live CD/USB.

If it shows in the drop down box at top right you can try formatting it and/or using Device ->Create partition table, then making a new partition in the newly made free space.

---

### Post by JTatts on 2013-01-05
I assume you meant,

```

sudo mount /dev/sdc /mnt/sdc
```I get,

```

mount: no medium found on /dev/sdc
```

---

### Post by Bucky Ball on 2013-01-05
Well, if that is the response I doubt if it will show in Gparted. You could try but I'm betting it will be invisible there too.

---

### Post by JTatts on 2013-01-05
You are correct, it doesn't show up in gparted either.

---

### Post by Bucky Ball on 2013-01-05
My guess? Dead SD. Only option: try on another machine and if it shows, reformat and try again ...

---

