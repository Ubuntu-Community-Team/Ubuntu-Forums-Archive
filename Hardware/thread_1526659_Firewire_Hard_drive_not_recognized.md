---
title: "Firewire Hard drive not recognized"
date: 2010-07-08
forum: Hardware
---

### Post by peyu on 2010-07-08
Hi everybody,

I have a 500 Gb hard drive disk with a NTFS partition that can be connected by usb or firewire. I'm using ubuntu 10.04.

When I plug it through usb, everything works fine (ntfs partition automount and I can read and write).
But, when I plug it through firewire, ubuntu doesn't mount it and doesn't recognize the partition format.

here is the dmesg output:

```
[ 4725.304454] ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
[ 4726.256744] ieee1394: Error parsing configrom for node 0-00:1023
[ 4726.256815] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[ 4737.354463] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0001d20e00ad0688]
[ 4737.361872] scsi7 : SBP-2 IEEE-1394
[ 4737.362000] ieee1394: sbp2: Workarounds for node 0-00:1023: 0x20 (firmware_revision 0x012804, vendor_id 0x0001d2, model_id 0x000001)
[ 4738.364772] ieee1394: sbp2: Logged into SBP-2 device
[ 4738.364829] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 4738.365568] scsi 7:0:0:0: Direct-Access-RBC ST350083 0A                    PQ: 0 ANSI: 4
[ 4738.365864] sd 7:0:0:0: Attached scsi generic sg4 type 14
[ 4738.389793] sd 7:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 4738.390019] sd 7:0:0:0: [sdc] Write Protect is off
[ 4738.390023] sd 7:0:0:0: [sdc] Mode Sense: 11 00 00 00
[ 4738.390378] sd 7:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4738.391375]  sdc: sdc1
[ 4738.410638] sd 7:0:0:0: [sdc] Attached SCSI disk

```

And also the lspci output:
```
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:06.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)

```

Do you have any idea about what can happen?

Thanks in advance!!

---

### Post by dabl on 2010-07-08
I am not expert on Firewire devices, but I have not read that Ubuntu is expected to mount a NTFS partition automatically ( I see you have it working for USB, but it might not work for IEEE-1394).

With your Firewire drive connected, boot your computer, and when it is completely finished, run

```
sudo fdisk -lu
```

Is the Firewire drive seen?  If so, probably it is the NTFS format that is keeping it from being mounted automatically.

---

### Post by IcarusR on 2010-07-08
The drive is seen this it...

> sd 7:0:0:0: [sdc] Attached SCSI disk

Try mounting it manually with something like this

```
sudo mount -t ntfs /dev/sdc1 /some/mount/point
```

Obviously create & use your own mount point.

Should mount ntfs firewire drives automatically, my ipod (ntfs firewire) does.

---

### Post by cabol on 2010-07-08
Dear all,
I have the same problem than peyu. The drive is recognized (via firewire) by Ubuntu, but you cannot work with it.
This is the screen after DABL's suggestion:

```

```
Disco /dev/sda: 60.0 GB, 60022480896 bytes
255 cabezas, 63 sectores/pista, 7297 cilindros, 117231408 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x0006f850

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048   114247679    57122816   83  Linux
/dev/sda2       114249726   117229567     1489921    5  Extendida
/dev/sda5       114249728   117229567     1489920   82  Linux swap / Solaris

Disco /dev/sdb: 320.1 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros, 625142448 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00000000

El disco /dev/sdb no contiene una tabla de particiones válida

Disco /dev/sdc: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00000000

El disco /dev/sdc no contiene una tabla de particiones válida
```

```



Thanks in advance!!

---

### Post by dabl on 2010-07-08
> **cabol said:**
> 

El disco /dev/sdc no contiene una tabla de particiones válida


I don't read or speak Spanish, but I think this says "no valid partition table", right?  If so, that's a problem.  To be read by a default Ubuntu system, each hard drive needs a "MS-DOS Type" partition table on it.

[http://tldp.org/HOWTO/Partition/](http://tldp.org/HOWTO/Partition/)

---

### Post by peyu on 2010-07-08
dear dabl,
This is the problem: the same disk, through usb, has a valid partition table and can be mounted automatically, but through firewire, has not a valid partition table... 
I think it has something to do with firewire driver but i am quite a newbie and i have no idea how to search for more information into my system...

---

### Post by dabl on 2010-07-08
> **peyu said:**
> 

I think it has something to do with firewire driver 


I think you are probably right about that.  I have not had the experience of dealing with a firewire drive.  There's probably a driver module available, but you may have to compile it.

Sorry, I can't do more. 

If you figure out how to make it work, be sure to post the solution for others.

---

### Post by IcarusR on 2010-07-09
> Should mount ntfs firewire drives automatically, my ipod (ntfs firewire) does.

ipod is actually fat32. 
Just tried it & can not get it to work. Always was a fiddle !!
Needs 3 modules loaded in a particular order... & a lot of luck.

ieee1394
ohci1394
sbp2

---

