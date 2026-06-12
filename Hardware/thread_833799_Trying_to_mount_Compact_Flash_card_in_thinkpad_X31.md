---
title: "Trying to mount Compact Flash card in thinkpad X31"
date: 2008-06-18
forum: Hardware
---

### Post by JamesX31 on 2008-06-18
Hi folks,
I'm new to this forum and started with linux a few weeks ago.  I've installed Hardy Heron on a thinkpad X31.  I've managed to solve most problems through forum searches and updates for bug fixes, but just can't resolve this one.

I'm trying to mount and access a compact flash card (just plain flash memory).

I hoped it would just appear in the mount directory, but no such luck!

When I insert / remove the card, /var/log/syslog shows:

Jun 19 11:02:29 X31 kernel: [ 2279.980649] pccard: PCMCIA card inserted into slot 1
Jun 19 11:02:30 X31 kernel: [ 2279.980662] cs: memory probe 0xe8000000-0xefffffff: excluding 0xe8000000-0xefffffff
Jun 19 11:02:30 X31 kernel: [ 2279.980690] cs: memory probe 0xc0200000-0xcfffffff: excluding 0xc0200000-0xc11fffff 0xc1a00000-0xc21fffff 0xc2a00000-0xc31fffff 0xc3a00000-0xcc1fffff 0xcca00000-0xcd1fffff 0xcda00000-0xce1fffff 0xcea00000-0xcf1fffff 0xcfa00000-0xd01fffff
Jun 19 11:02:30 X31 kernel: [ 2279.986364] pcmcia: registering new device pcmcia1.0
Jun 19 11:02:30 X31 kernel: [ 2280.819024] scsi2 : pata_pcmcia
Jun 19 11:02:30 X31 kernel: [ 2280.819600] ata3: PATA max PIO0 cmd 0x4100 ctl 0x410e irq 3
Jun 19 11:03:00 X31 kernel: [ 2306.371666] ata3.00: qc timeout (cmd 0x91)
Jun 19 11:03:00 X31 kernel: [ 2306.371676] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
Jun 19 11:03:00 X31 kernel: [ 2306.371681] ata3: failed to recover some devices, retrying in 5 secs
Jun 19 11:03:36 X31 kernel: [ 2337.312877] ata3.00: qc timeout (cmd 0x91)
Jun 19 11:03:36 X31 kernel: [ 2337.312886] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
Jun 19 11:03:36 X31 kernel: [ 2337.312891] ata3: failed to recover some devices, retrying in 5 secs
Jun 19 11:04:11 X31 kernel: [ 3312.323068] ata3.00: qc timeout (cmd 0x91)
Jun 19 11:04:11 X31 kernel: [ 3312.323078] ata3.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x4)
Jun 19 11:04:11 X31 kernel: [ 3312.323084] ata3: failed to recover some devices, retrying in 5 secs
Jun 19 11:04:17 X31 NetworkManager: <debug> [1213837457.191743] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 
Jun 19 11:17:02 X31 /USR/SBIN/CRON[8078]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 19 11:18:28 X31 kernel: [ 6775.722935] pccard: card ejected from slot 1
Jun 19 11:18:28 X31 NetworkManager: <debug> [1213838308.826616] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/pcmcia__1__1'). 

(Why's the network manager getting involved?)


At the time of inserting the card, this folder appears:

/sys/bus/pcmcia/devices/1.0

And disappears when I remove the card


sudo fdisk -l   only shows my HDD


pccardctl info    gives this:

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2="CF 4GB"
PRODID_3=""
PRODID_4=""
MANFID=004f,0000
FUNCID=4


pccardctl ident    gives this:

Socket 0:
  no product info available
Socket 1:
  product info: "", "CF 4GB", "", ""
  manfid: 0x004f, 0x0000
  function: 4 (fixed disk)


lspcmcia     gives this:

Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:00.1)
Socket 1 Device 0:	[pata_pcmcia]		(bus ID: 1.0)


pccardctl status    gives this:

Socket 0:
  no card
Socket 1:
  3.3V 16-bit PC Card
  Subdevice 0 (function 0) bound to driver "pata_pcmcia"


I haven't got a clue how to actually mount the thing.  I have found the mount command, but don't know what to use for the device.

Any pointers will be much appreciated!


Cheers
James

---

### Post by JamesX31 on 2008-06-27
Can anyone offer me any pointers as to what to try next?

Thanks!

---

### Post by JamesX31 on 2008-07-10
Does anyone know if this is actually possible?

---

### Post by JamesX31 on 2008-07-23
Hmmm, I guess not

---

### Post by orbister on 2008-11-02
This chap seems to think it is possible:

[http://www.marzocca.net/linux/ubuntux31.html](http://www.marzocca.net/linux/ubuntux31.html)

I'll try it as soon as I get a CF card, or a SD/MMC -> CF adaptor.

Ian

---

