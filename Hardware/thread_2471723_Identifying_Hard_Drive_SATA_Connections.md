---
title: "Identifying Hard Drive SATA Connections"
date: 2022-02-07
forum: Hardware
---

### Post by rsteinmetz70112 on 2022-02-07
I have a computer with 4 identical SATA hard drives. I have their UUIDs and their /dev/sd designations. How can I identify which of the SATA ports on the motherboard they are connected to without unplugging them to see which one is missing or removing them from the case?

---

### Post by tea for one on 2022-02-07
If you download and run the recently created script [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info), I'm pretty sure that the output contains disk and UUID details.

Alternatively via the terminal
```
lsblk -e 7 -o name,size,type,uuid,fstype
```

On third thoughts, I don't think that my suggestion(s) will be very helpful because the physical ports on the motherboard will not be identified.

Instead of removing the drives one by one, does your UEFI/BIOS allow you to isolate them individually?

---

### Post by oldfred on 2022-02-08
From my system:
My HDD is SATA and shown as port 1, my USB Samsung 850 says port 6 (but is USB?) and NVMe shows no port.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -o NAME,MODEL,SERIAL,WWN,HCTL [/COLOR]
NAME        MODEL                          SERIAL          WWN                  HCTL 
sda         HGST_HTS721010A9E630           JR10004M0M0V8E  0x5000cca8a8c8a63b   [COLOR=#ff0000]1[/COLOR]:0:0:0 
&#9500;&#9472;sda1                                                     0x5000cca8a8c8a63b    
......  removed extra reduncant info
&#9492;&#9472;sda10                                                    0x5000cca8a8c8a63b    
sdb         SSD_850_EVO                    000000123ACC                         [COLOR=#ff0000]6[/COLOR]:0:0:0 
&#9500;&#9472;sdb1                                                                           
.....
nvme0n1     Samsung SSD 970 EVO Plus 500GB S4P2NF0M514514L eui.0025385591b07f8f  
&#9500;&#9472;nvme0n1p1                                                eui.0025385591b07f8f  
...

[/FONT]
```

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo lshw -c storage -c disk        [/COLOR]
[sudo] password for fred:  
  *-usb                      
       description: Mass storage device 
       product: VLI Product String 
       vendor: VLI Manufacture String 
       physical id: 2 
       bus info: usb@2:2 
       version: 0.00 
       serial: 000000123ACC 
       capabilities: usb-3.10 scsi 
       configuration: driver=uas maxpower=896mA speed=5000Mbit/s 
  *-sata 
       description: SATA controller 
       product: Q170/Q150/B150/H170/H110/Z170/CM236 Chipset SATA Controller [AHCI Mode] 
       vendor: Intel Corporation 
       physical id: 17 
       bus info: pci@0000:00:17.0 
       version: 31 
       width: 32 bits 
       clock: 66MHz 
       capabilities: sata msi pm ahci_1.0 bus_master cap_list 
       configuration: driver=ahci latency=0 
       resources: irq:139 memory:ef428000-ef429fff memory:ef42c000-ef42c0ff ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:ef42b000-ef42b7ff 
  *-storage 
       description: Non-Volatile memory controller 
       product: NVMe SSD Controller SM981/PM981/PM983 
       vendor: Samsung Electronics Co Ltd 
       physical id: 0 
       bus info: pci@0000:10:00.0 
       version: 00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list 
       configuration: driver=nvme latency=0 
       resources: irq:16 memory:ef000000-ef003fff 
     *-nvme0 
          description: NVMe device 
          product: Samsung SSD 970 EVO Plus 500GB 
          physical id: 0 
          logical name: /dev/nvme0 
          version: 2B2QEXM7 
          serial: S4P2NF0M514514L 
          configuration: nqn=nqn.2014.08.org.nvmexpress:144d144dS4P2NF0M514514L     Samsung SSD 970 EVO Plus 500GB state=live 
        *-namespace 
             description: NVMe namespace 
             physical id: 1 
             logical name: /dev/nvme0n1 
             size: 465GiB (500GB) 
             capabilities: gpt-1.00 partitioned partitioned:gpt 
             configuration: guid=28b13235-0c01-4a92-bb59-96c0739f1591 logicalsectorsize=512 sectorsize=512 
  *-scsi:0 
       physical id: a 
       logical name: [COLOR=#ff0000]scsi1[/COLOR] 
       capabilities: emulated 
     *-disk 
          description: ATA Disk 
          product: HGST HTS721010A9 
          physical id: 0.0.0 
          bus info: scsi@[COLOR=#ff0000]1[/COLOR]:0.0.0 
          logical name: /dev/sda 
          version: A3J0 
          serial: JR10004M0M0V8E 
          size: 931GiB (1TB) 
          capabilities: gpt-1.00 partitioned partitioned:gpt 
          configuration: ansiversion=5 guid=1ab0dbe4-1876-4f34-81ea-f2c2b2b55b74 logicalsectorsize=512 sectorsize=4096 
  *-scsi:1 
       physical id: b 
       logical name: [COLOR=#ff0000]scsi6[/COLOR] 
     *-disk 
          description: SCSI Disk 
          product: SSD 850 EVO 
          vendor: Samsung 
          physical id: 0.0.0 
          bus info: scsi@[COLOR=#ff0000]6[/COLOR]:0.0.0 
          logical name: /dev/sdb 
          version: EMT2 
          serial: 000000123ACC 
          size: 232GiB (250GB) 
          capabilities: gpt-1.00 partitioned partitioned:gpt 
          configuration: ansiversion=6 guid=793704b9-76db-45ea-83f1-c50c71d1f9f2 logicalsectorsize=512 sectorsize=512 
[COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]

[/FONT]
```

More info:
[https://delightlylinux.wordpress.com/2019/08/02/how-to-find-a-hard-drives-sata-port-in-bash/](https://delightlylinux.wordpress.com/2019/08/02/how-to-find-a-hard-drives-sata-port-in-bash/)

---

