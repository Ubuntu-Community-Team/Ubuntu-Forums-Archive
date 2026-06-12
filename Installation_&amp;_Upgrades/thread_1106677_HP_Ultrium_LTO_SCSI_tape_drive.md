---
title: "HP Ultrium LTO SCSI tape drive"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by yirgacheffe on 2009-03-25
Hi,

I am having problem while attempting to talk to this tape drive.
I can see the SCSI card, but not the tape. 

To start with, I change the ID's in the SCSI setup utility during boot
to whatever is my TAPE drive' s ID switch is set to.
I leave other options as default (parity check = enabled, auto termination=enabled).

Then after boot, I have the /dev/uuid-xxxx does not exist, dropping to a shell error.

The only way to boot is editing the boot argument with rootdelay=120 appended
to it.
Will but, all OK, but can' t see the tape drive.

I have all other things set up I think (st in /etc/modules, etc) but I think the problem is prior to this point..

few diagnostic command outputs:


```
lsscsi
```
[2:0:0:0]    disk    ATA      ST3200827AS      3.AA  -       
[3:0:0:0]    disk    ATA      ST3320620A       3.AA  -       
[3:0:1:0]    cd/dvd  HL-DT-ST DVDRAM GSA-H42N  RL00  -       

```
cat /proc/scsi/scsi
```
Attached devices:
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3200827AS      Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3320620A       Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 01 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GSA-H42N  Rev: RL00
  Type:   CD-ROM                           ANSI  SCSI revision: 05
```
root=bootarg cat /proc/cmdline
```
root=UUID=f2bb642e-7da4-4898-beba-dceb3274d7ef ro quiet splash rootdelay=120

```
dmesg
```

[   17.456038] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   17.456041]         <Adaptec 3944A Ultra SCSI adapter>
[   17.456043]         aic7895C: Ultra Wide Channel A, SCSI Id=5, 32/253 SCBs
[   17.456045] 
[   17.456830] aic7xxx 0000:04:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19

....
[   32.468034] scsi1 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   32.468037]         <Adaptec 3944A Ultra SCSI adapter>
[   32.468039]         aic7895C: Ultra Wide Channel B, SCSI Id=5, 32/253 SCBs
[   32.468041] 

...
[   33.160341] scsi: waiting for bus probes to complete ...
[   36.409416] scsi 2:0:0:0: Direct-Access     ATA      ST3200827AS      3.AA PQ: 0 ANSI: 5
[   36.409621] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[   36.409726] scsi 3:0:0:0: Direct-Access     ATA      ST3320620A       3.AA PQ: 0 ANSI: 5
[   36.409842] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[   36.413186] scsi 3:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42N  RL00 PQ: 0 ANSI: 5
[   36.413392] scsi 3:0:1:0: Attached scsi generic sg2 type 5

...

[  156.465303] ppdev0: registered pardevice
[  156.513347] ppdev0: unregistered pardevice
[  156.644684] ppdev0: registered pardevice
[  156.692039] ppdev0: unregistered pardevice
[  158.245180] ppdev0: registered pardevice
[  158.293216] ppdev0: unregistered pardevice

```
mt -f /dev/nst0 status
```

/dev/nst0: No such file or directory

```
sudo /dev/MAKEDEV -v st0
```

create st0	c 9 0 root:tape 0660
create nst0	c 9 128 root:tape 0660
create st0l	c 9 32 root:tape 0660
create nst0l	c 9 160 root:tape 0660
create st0m	c 9 64 root:tape 0660
create nst0m	c 9 192 root:tape 0660
create st0a	c 9 96 root:tape 0660
create nst0a	c 9 224 root:tape 0660

- after this, there is stiil no /dev/st0, nst0 etc....they are created in /home, and mt -f still returns no such device.



Any help would be appreciated.
regards
Sid

---

