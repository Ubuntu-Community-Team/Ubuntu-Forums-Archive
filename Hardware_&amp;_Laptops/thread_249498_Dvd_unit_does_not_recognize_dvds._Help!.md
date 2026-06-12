---
title: "Dvd unit does not recognize dvds. Help!"
date: 2006-09-02
forum: Hardware &amp; Laptops
---

### Post by agrabah on 2006-09-02
Hello!

This really is a somewhat persistent problem (I also experienced it with other distros). When I put a dvd (sometimes even a normal cd), the dvd unit starts to turn it, makes a few hiccups and then stops. The system does not recognize the dvd. I can't mount it manually either (tried that with many problematic dvds). Dmesg makes the following "eloquent" statement:

```
[4295994.770000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[4295996.811000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
```

(many times over)

I suspect it is a defective unit, but I'm not really sure. Google hasn't turned up anything useful (or even remotely familiar problem). My linux guru hasn't been able to help me either (otner than advising me to buy a new unit).

So any ideas? Is it a broken dvd unit or am I missing something?

Tine

---

### Post by dlwofford on 2006-09-29
Your not alone!
Same thing here. Plays CD-roms fine but if I put a DVD in muliple 
[COLOR="Red"][17180841.740000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00[/COLOR]
errors in a dmesg. Also the DVD never appears to mount and i have tried multiple dvd's.

---

### Post by LinuxConvertJune2006 on 2006-10-10
Anyone have any idea? My 64bit Ubuntu macihne has this issue but not my 32bit. It could be a blank DVD or a movie, but Ubuntu sometimes doesn't recognize. Here is dmesg:
 dmesg | tail
[867290.610170] cdrom: This disc doesn't have any tracks I recognize!
[867399.106808] attempt to access beyond end of device
[867399.106871] hdd: rw=0, want=68, limit=4
[867399.106911] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
[867411.752201] attempt to access beyond end of device
[867411.752272] hdd: rw=0, want=68, limit=4
[867411.752314] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
[867758.315710] attempt to access beyond end of device
[867758.315773] hdd: rw=0, want=68, limit=4
[867758.315778] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16



And here is manually mount attempt with blank DVD-R inserted , note a reboot normally fixes this but its really annoying:

umount /dev/cdrom
umount: /dev/hdd is not mounted (according to mtab)
sudo mount -t iso9660 /dev/cdrom /media/cdrom
mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by buro9 on 2008-02-14
Seeing the same thing here:
```

Feb 14 09:57:04 ukscdev003 kernel: [17181005.452000] hda: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
Feb 14 09:57:06 ukscdev003 kernel: [17181007.592000] hda: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
Feb 14 09:57:08 ukscdev003 kernel: [17181009.732000] hda: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
Feb 14 09:57:10 ukscdev003 kernel: [17181011.872000] hda: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00

```

There's nothing in the DVD drive, but these errors are populating the log every few seconds.

From the boot I just did:
```

Feb 14 09:34:18 ukscdev003 kernel: [17179573.828000] SvrWks CSB5: IDE controller at PCI slot 0000:00:0f.1
Feb 14 09:34:18 ukscdev003 kernel: [17179573.832000] SvrWks CSB5: chipset revision 147
Feb 14 09:34:18 ukscdev003 kernel: [17179573.832000] SvrWks CSB5: not 100%% native mode: will probe irqs later
Feb 14 09:34:18 ukscdev003 kernel: [17179573.832000] SvrWks CSB5: simplex device: DMA forced
Feb 14 09:34:18 ukscdev003 kernel: [17179573.832000]     ide0: BM-DMA at 0x08b0-0x08b7, BIOS settings: hda:DMA, hdb:pio
Feb 14 09:34:18 ukscdev003 kernel: [17179573.832000] SvrWks CSB5: simplex device: DMA forced
Feb 14 09:34:18 ukscdev003 kernel: [17179573.832000]     ide1: BM-DMA at 0x08b8-0x08bf, BIOS settings: hdc:DMA, hdd:DMA
Feb 14 09:34:18 ukscdev003 kernel: [17179573.832000] Probing IDE interface ide0...
Feb 14 09:34:18 ukscdev003 kernel: [17179574.344000] hda: HL-DT-STCD-RW/DVD-ROM GCC-4240N, ATAPI CD/DVD-ROM drive
Feb 14 09:34:18 ukscdev003 kernel: [17179574.792000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Feb 14 09:34:18 ukscdev003 kernel: [17179574.792000] Probing IDE interface ide1...
Feb 14 09:34:18 ukscdev003 kernel: [17179575.476000] hda: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Feb 14 09:34:18 ukscdev003 kernel: [17179575.476000] Uniform CD-ROM driver Revision: 3.20
Feb 14 09:34:18 ukscdev003 kernel: [17179575.480000] hda: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
Feb 14 09:34:18 ukscdev003 kernel: [17179575.496000] hda: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00

```

It's not causing any problems as we're not using the drive... more a case of lots of noise in the syslog and a desire to stop that.

---

