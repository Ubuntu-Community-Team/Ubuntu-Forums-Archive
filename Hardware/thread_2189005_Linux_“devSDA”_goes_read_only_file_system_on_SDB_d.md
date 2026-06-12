---
title: "Linux “/dev/SDA” goes read only file system on SDB device failure"
date: 2013-11-20
forum: Hardware
---

### Post by venkat-330 on 2013-11-20
[COLOR=#000000][FONT=Arial]i have a very peculiar issue that is running in my system.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Using debian linux :[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My system boots up very normally with a primary and secondary hard disk. suddenly my secondary hard disk fails with some I/O Error DRDY UNC errors which tends make my primary SDA to read only filesystem.[/FONT][/COLOR]

[LIST=1]
[*]how to avoid primary to be changed as read only
[*]What are all the steps i need to do for removing the SDB reference from the system
[/LIST]
[COLOR=#000000][FONT=Arial]Please guide[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Kernal Log::[/FONT][/COLOR]
2013 Nov 20 15:52:13::kernel::[  234.995333] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
2013 Nov 20 15:52:13::kernel::[  234.995405] ata1.01: BMDMA stat 0x65
2013 Nov 20 15:52:13::kernel::[  234.995465] ata1.01: failed command: READ DMA EXT
2013 Nov 20 15:52:13::kernel::[  234.995534] ata1.01: cmd 25/00:08:f8:17:00/00:00:25:00:00/f0 tag 0 dma 4096 in
2013 Nov 20 15:52:13::kernel::[  234.995537]          res 51/40:00:f8:17:00/40:00:25:00:00/10 Emask 0x9 (media error)
2013 Nov 20 15:52:13::kernel::[  234.996798] ata1.01: status: { DRDY ERR }
2013 Nov 20 15:52:13::kernel::[  234.996857] ata1.01: error: { UNC }
2013 Nov 20 15:52:13::kernel::[  235.117634] ata1.00: configured for UDMA/133
2013 Nov 20 15:52:13::kernel::[  235.149719] ata1.01: configured for UDMA/133
2013 Nov 20 15:52:13::kernel::[  235.149793] sd 0:0:1:0: [sdb] Unhandled sense code
2013 Nov 20 15:52:13::kernel::[  235.149852] sd 0:0:1:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
2013 Nov 20 15:52:13::kernel::[  235.149946] sd 0:0:1:0: [sdb] Sense Key : Medium Error [current] [descriptor]
2013 Nov 20 15:52:13::kernel::[  235.150121] Descriptor sense data with sense descriptors (in hex):
2013 Nov 20 15:52:13::kernel::[  235.150209]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
2013 Nov 20 15:52:13::kernel::[  235.150734]         25 00 17 f8 
2013 Nov 20 15:52:13::kernel::[  235.150925] sd 0:0:1:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
2013 Nov 20 15:52:13::kernel::[  235.151067] sd 0:0:1:0: [sdb] CDB: Read(10): 28 00 25 00 17 f8 00 00 08 00
2013 Nov 20 15:52:13::kernel::[  235.151486] end_request: I/O error, dev sdb, sector 620763128
2013 Nov 20 15:52:13::kernel::[  235.151551] Buffer I/O error on device sdb5, logical block 70778879
2013 Nov 20 15:52:13::kernel::[  235.151637] ata1: EH complete

---

### Post by Bashing-om on 2013-11-20
venkat-330; Hi ! Welcome to the forum .

Not much info to give any specifics.
Generally:
What format is used on device dsb ? 
  1. NTFS: Install that disk on a windows machine and run Windows' check disk and diagnostics on that drive.
  2. EXT4 (ubuntu's file system), what does "disk utility"-> "SMART" status report ?. Have you ran the "fsck" checks on the drive ?

Presently the system is detecting a problem and is protecting it's self from any additional damage by preventing any writes to disk. Fix the problem and journaling will be restored.

Just a pointer in the right direction.

[INDENT][INDENT]hope this is of some help
[/INDENT][/INDENT]

---

