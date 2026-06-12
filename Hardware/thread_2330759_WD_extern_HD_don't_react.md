---
title: "WD extern HD don't react"
date: 2016-07-14
forum: Hardware
---

### Post by møllerik on 2016-07-14
UBUNTU 14.04 LTS / WD-elements /TOSHIBA Satellite

erik@erik-SATELLITE-C70D-B:~$ sudo smartctl -t long /dev/sdg
[sudo] password for erik: 
sudo: smartctl: command not found
erik@erik-SATELLITE-C70D-B:~$ sudo smartctl -a /dev/sdg
sudo: smartctl: command not found
erik@erik-SATELLITE-C70D-B:~$ sudo fdisk -l

ADVARSEL: GPT (GUID-partitionstabel) detekteret på »/dev/sda«! Værktøjet fdisk understøtter ikke GPT. Brug GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 hoveder, 63 sektorer/spor, 121601 cylindre, i alt 1953525168 sektorer
Enheder = sektorer af 1 * 512 = 512 byte
Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte
I/O-størrelse (minimum/optimal): 512 byte / 512 byte
Diskidentifikation: 0x00000000

    Enhed Opstart   Start         ****     Blokke   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 hoveder, 63 sektorer/spor, 121601 cylindre, i alt 1953525168 sektorer
Enheder = sektorer af 1 * 512 = 512 byte
Sektorstørrelse (logisk/fysisk): 512 byte / 512 byte
I/O-størrelse (minimum/optimal): 512 byte / 512 byte
Diskidentifikation: 0xe8900690

    Enhed Opstart   Start         ****     Blokke   Id  System
erik@erik-SATELLITE-C70D-B:~$ 

What to do ?

---

### Post by weatherman2 on 2016-07-14
Start with these commands and show the output here:

```

lsusb
dmesg | grep -i usb

```

smartctl won't work until you install smartmontools:

```

sudo apt-get update
sudo apt-get install smartmontools

```

or use the Gui version which is easier to use but also installs smartmontools:

```

sudo apt-get update
sudo apt-get install gsmartcontrol

```

But the smartctl test you were trying to launch may take hours to complete.  I wouldn't run that until you have done some basic diagnostics first.  (Also, how do you know it is on /dev/sdg ?)

I'd look the Attributes first before even running any test:

```

sudo smartctl -a /dev/sdX

```

(Replace /dev/sdX with the real device ID of your WD drive, whenever you finally detect it.)

---

### Post by oldfred on 2016-07-14
Only the new fdisk with 16.04 sees gpt partitioned drives.
Use 
sudo parted -l
sudo gdisk -l /dev/sdb 
or if sdg?

Disks includes smart monitor. In Disks click on icon in upper right corner.

---

