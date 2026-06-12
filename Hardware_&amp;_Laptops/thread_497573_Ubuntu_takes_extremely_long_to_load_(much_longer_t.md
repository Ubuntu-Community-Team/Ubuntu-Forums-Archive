---
title: "Ubuntu takes extremely long to load (much longer than it should)"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by Funzo22 on 2007-07-10
I just upgraded my hard drive, cloned my /home partition onto it and installed ubuntu.

Now, the boot process seems to hang very soon after it starts, and it takes probably around 5 or 10 minutes before it continues.


Here is the relevant output that I found in /var/log/syslog:

> Jul 10 01:53:35 dustin-desktop kernel: [   11.265161] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Jul 10 01:53:35 dustin-desktop kernel: [   11.265166] ata1.00: ATA-7: ST3500830A, 3.AAC, max UDMA/100
Jul 10 01:53:35 dustin-desktop kernel: [   11.265168] ata1.00: 976773168 sectors, multi 16: LBA48 
Jul 10 01:53:35 dustin-desktop kernel: [   11.265171] ata1.01: ATAPI, max UDMA/33
Jul 10 01:53:35 dustin-desktop kernel: [   11.265176] ata1.00: limited to UDMA/33 due to 40-wire cable
Jul 10 01:53:35 dustin-desktop kernel: [   11.331637] ata1.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 976773168
Jul 10 01:53:35 dustin-desktop kernel: [   11.331643] ata1.00: configured for UDMA/33
Jul 10 01:53:35 dustin-desktop kernel: [   11.514764] ata1.01: configured for UDMA/33
Jul 10 01:53:35 dustin-desktop kernel: [   11.514779] scsi1 : ata_piix
Jul 10 01:53:35 dustin-desktop kernel: [   11.685290] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [   11.696405] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [   11.861930] ata2.01: ATAPI, max MWDMA2
Jul 10 01:53:35 dustin-desktop kernel: [   12.029556] ata2.01: configured for MWDMA2
Jul 10 01:53:35 dustin-desktop kernel: [   12.029701] scsi 0:0:0:0: Direct-Access     ATA      ST3500830A       3.AA PQ: 0 ANSI: 5
Jul 10 01:53:35 dustin-desktop kernel: [   12.033576] scsi 0:0:1:0: CD-ROM            TOSHIBA  CD/DVDW SD-R5372 TU53 PQ: 0 ANSI: 5
Jul 10 01:53:35 dustin-desktop kernel: [   17.525203] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jul 10 01:53:35 dustin-desktop kernel: [   17.525211] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
Jul 10 01:53:35 dustin-desktop kernel: [   17.525213]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 10 01:53:35 dustin-desktop kernel: [   24.513730] ata2: port is slow to respond, please be patient (Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [   47.478832] ata2: port failed to respond (30 secs, Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [   47.478839] ata2: soft resetting port
Jul 10 01:53:35 dustin-desktop kernel: [   47.645650] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [   47.656796] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [   47.985907] ata2.01: configured for MWDMA2
Jul 10 01:53:35 dustin-desktop kernel: [   47.985924] ata2: EH complete
Jul 10 01:53:35 dustin-desktop kernel: [   53.473574] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jul 10 01:53:35 dustin-desktop kernel: [   53.473581] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
Jul 10 01:53:35 dustin-desktop kernel: [   53.473582]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 10 01:53:35 dustin-desktop kernel: [   60.462103] ata2: port is slow to respond, please be patient (Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [   83.427198] ata2: port failed to respond (30 secs, Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [   83.427205] ata2: soft resetting port
Jul 10 01:53:35 dustin-desktop kernel: [   83.593977] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [   83.605086] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [   83.934279] ata2.01: configured for MWDMA2
Jul 10 01:53:35 dustin-desktop kernel: [   83.934296] ata2: EH complete
Jul 10 01:53:35 dustin-desktop kernel: [   89.421944] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jul 10 01:53:35 dustin-desktop kernel: [   89.421952] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
Jul 10 01:53:35 dustin-desktop kernel: [   89.421953]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 10 01:53:35 dustin-desktop kernel: [   96.410473] ata2: port is slow to respond, please be patient (Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [  119.375570] ata2: port failed to respond (30 secs, Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [  119.375576] ata2: soft resetting port
Jul 10 01:53:35 dustin-desktop kernel: [  119.542346] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [  119.553459] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [  119.878656] ata2.01: configured for MWDMA2
Jul 10 01:53:35 dustin-desktop kernel: [  119.878672] ata2: EH complete
Jul 10 01:53:35 dustin-desktop kernel: [  125.366323] ata2.01: limiting speed to MWDMA1:PIO4
Jul 10 01:53:35 dustin-desktop kernel: [  125.366327] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jul 10 01:53:35 dustin-desktop kernel: [  125.366333] ata2.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
Jul 10 01:53:35 dustin-desktop kernel: [  125.366334]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 10 01:53:35 dustin-desktop kernel: [  132.350859] ata2: port is slow to respond, please be patient (Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [  155.327930] ata2: port failed to respond (30 secs, Status 0xd8)
Jul 10 01:53:35 dustin-desktop kernel: [  155.327936] ata2: soft resetting port
Jul 10 01:53:35 dustin-desktop kernel: [  155.494706] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [  155.505828] ATA: abnormal status 0x7F on port 0x00010177
Jul 10 01:53:35 dustin-desktop kernel: [  155.839002] ata2.01: configured for MWDMA1
Jul 10 01:53:35 dustin-desktop kernel: [  155.839026] ata2: EH complete
Jul 10 01:53:35 dustin-desktop kernel: [  155.839157] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Jul 10 01:53:35 dustin-desktop kernel: [  155.839175] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 16

It says that I am using a 40 pin wire, but I am pretty sure that this isnt true, because my old hard drive (which was only half a year old) never complained about the IDE cable, and also, my bios isn't complaining as it should if I were using a 40 pin wire.


Thanks in advance



Dustin


Edit: just in case I missed anything, I uploaded my entire syslog

---

### Post by dreadlord_chris on 2007-07-10
try opening your box and reseating the IDE cable - at both ends

---

### Post by Funzo22 on 2007-07-10
I reseated the IDE cable, and I moved my dvd drive over to another channel and it seems to be working now

Thanks!

---

### Post by dreadlord_chris on 2007-07-10
> **Funzo22 said:**
> I reseated the IDE cable, and I moved my dvd drive over to another channel and it seems to be working now

Thanks!

With the 80 pin IDE cables and the limited space in most modern setups - it's fairly easy to mis pushing both sides in at the hard drive connection.

---

