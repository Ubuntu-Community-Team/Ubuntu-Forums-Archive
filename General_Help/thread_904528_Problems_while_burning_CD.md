---
title: "Problems while burning CD"
date: 2008-08-29
forum: General Help
---

### Post by Promille on 2008-08-29
Hey guys. I got a really annoying problem going on here. It's two years since i changed to ubuntu, and ever since i had problems burning cd's, whether its music or data cd. I really have no clue what the problem is, I'm completely blank. I've tried several apps, and it ALLWAYS happens. It usually occurs when its 20-30 % complete though. Here is the debug output from k3b, but unfortunately I don't understand much of it. This never happened on Windows for what its worth. Could it be a driver problem?

Any help is greatly appriciated

-Promille

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
PHILIPS DVD+-RW SDVD8441 PX43 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'PHILIPS '
Identification : 'DVD+-RW SDVD8441'
Revision       : 'PX43'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0000 (Reserved/Unknown) 
Profile: 0x0000 (Reserved/Unknown) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Track 01: data   690 MB        
Total size:      793 MB (78:36.24) = 353718 sectors
Lout start:      793 MB (78:38/18) = 353718 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type C, low Beta category (C-) (6)
  ATIP start of lead in:  -11559 (97:27/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 21
Manufacturer: Ricoh Company Limited
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 6128
Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
Speed set to 4234 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Errno: 5 (Input/output error), read track info scsi sendcmd: no error
CDB:  52 01 00 00 00 FF 00 00 1C 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 240s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  690 MB written.
Track 01:    1 of  690 MB written (fifo 100%) [buf  87%]   3.6x.
Track 01:    2 of  690 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:    3 of  690 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:    4 of  690 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:    5 of  690 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:    6 of  690 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:    7 of  690 MB written (fifo 100%) [buf  93%]   8.6x.
Track 01:    8 of  690 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:    9 of  690 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   10 of  690 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   11 of  690 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   12 of  690 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   13 of  690 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:   14 of  690 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:   15 of  690 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   16 of  690 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   17 of  690 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:   18 of  690 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   19 of  690 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:   20 of  690 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:   21 of  690 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:   22 of  690 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   23 of  690 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   24 of  690 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   25 of  690 MB written (fifo 100%) [buf  93%]   8.3x.
Track 01:   26 of  690 MB written (fifo  99%) [buf  93%]   7.7x.
Track 01:   27 of  690 MB written (fifo 100%) [buf  87%]   7.5x.
Track 01:   28 of  690 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   29 of  690 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:   30 of  690 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   31 of  690 MB written (fifo 100%) [buf  93%]   8.3x.
Track 01:   32 of  690 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:   33 of  690 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:   34 of  690 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   35 of  690 MB written (fifo 100%) [buf  96%]   8.6x.
Track 01:   36 of  690 MB written (fifo 100%) [buf  90%]   7.7x.
Track 01:   37 of  690 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   38 of  690 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:   39 of  690 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   40 of  690 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:   41 of  690 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:   42 of  690 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   43 of  690 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   44 of  690 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:   45 of  690 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   46 of  690 MB written (fifo 100%) [buf  93%]   8.3x.
Track 01:   47 of  690 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:   48 of  690 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:   49 of  690 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   50 of  690 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   51 of  690 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   52 of  690 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:   53 of  690 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:   54 of  690 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:   55 of  690 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   56 of  690 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:   57 of  690 MB written (fifo 100%) [buf  90%]   7.7x.
Track 01:   58 of  690 MB written (fifo  99%) [buf  93%]   8.2x.
Track 01:   59 of  690 MB written (fifo 100%) [buf  93%]   7.8x.
Track 01:   60 of  690 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:   61 of  690 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   62 of  690 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:   63 of  690 MB written (fifo 100%) [buf  90%]   1.9x.
Track 01:   64 of  690 MB written (fifo 100%) [buf  90%]  12.6x.
Track 01:   65 of  690 MB written (fifo  99%) [buf  93%]  13.4x.
Track 01:   66 of  690 MB written (fifo  99%) [buf  93%]  12.6x.
Track 01:   67 of  690 MB written (fifo  99%) [buf  96%]  13.4x.
Track 01:   68 of  690 MB written (fifo  99%) [buf  93%]  12.5x.
Track 01:   69 of  690 MB written (fifo 100%) [buf  87%]  12.2x.
Track 01:   70 of  690 MB written (fifo 100%) [buf  87%]  12.5x.
Track 01:   71 of  690 MB written (fifo 100%) [buf  90%]  13.4x.
Track 01:   72 of  690 MB written (fifo 100%) [buf  90%]  12.5x.
Track 01:   73 of  690 MB written (fifo  99%) [buf  93%]  13.2x.
Track 01:   74 of  690 MB written (fifo  99%) [buf  93%]  12.2x.
Track 01:   75 of  690 MB written (fifo 100%) [buf  87%]  11.9x.
Track 01:   76 of  690 MB written (fifo 100%) [buf  87%]  12.2x.
Track 01:   77 of  690 MB written (fifo 100%) [buf  90%]  13.1x.
Track 01:   78 of  690 MB written (fifo 100%) [buf  90%]  12.2x.
Track 01:   79 of  690 MB written (fifo 100%) [buf  93%]  13.0x.
Track 01:   80 of  690 MB written (fifo  99%) [buf  93%]  12.3x.
Track 01:   81 of  690 MB written (fifo 100%) [buf  87%]  12.0x.
Track 01:   82 of  690 MB written (fifo 100%) [buf  87%]  12.3x.
Track 01:   83 of  690 MB written (fifo 100%) [buf  90%]  13.1x.
Track 01:   84 of  690 MB written (fifo 100%) [buf  90%]  12.3x.
Track 01:   85 of  690 MB written (fifo  99%) [buf  93%]  12.9x.
Track 01:   86 of  690 MB written (fifo  99%) [buf  93%]  12.1x.
Track 01:   87 of  690 MB written (fifo 100%) [buf  87%]  11.8x.
Track 01:   88 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:   89 of  690 MB written (fifo 100%) [buf  90%]  12.9x.
Track 01:   90 of  690 MB written (fifo 100%) [buf  90%]  12.1x.
Track 01:   91 of  690 MB written (fifo  99%) [buf  93%]  12.8x.
Track 01:   92 of  690 MB written (fifo  99%) [buf  93%]  12.1x.
Track 01:   93 of  690 MB written (fifo 100%) [buf  87%]  11.8x.
Track 01:   94 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:   95 of  690 MB written (fifo 100%) [buf  87%]  12.5x.
Track 01:   96 of  690 MB written (fifo 100%) [buf  90%]  13.4x.
Track 01:   97 of  690 MB written (fifo 100%) [buf  90%]  12.4x.
Track 01:   98 of  690 MB written (fifo  99%) [buf  93%]  13.0x.
Track 01:   99 of  690 MB written (fifo 100%) [buf  90%]  12.3x.
Track 01:  100 of  690 MB written (fifo  99%) [buf  93%]  13.0x.
Track 01:  101 of  690 MB written (fifo  99%) [buf  93%]  12.3x.
Track 01:  102 of  690 MB written (fifo 100%) [buf  87%]  12.0x.
Track 01:  103 of  690 MB written (fifo 100%) [buf  87%]  12.3x.
Track 01:  104 of  690 MB written (fifo 100%) [buf  90%]  13.1x.
Track 01:  105 of  690 MB written (fifo 100%) [buf  90%]  12.3x.
Track 01:  106 of  690 MB written (fifo  99%) [buf  93%]  13.1x.
Track 01:  107 of  690 MB written (fifo  99%) [buf  93%]  12.3x.
Track 01:  108 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  109 of  690 MB written (fifo 100%) [buf  87%]  12.4x.
Track 01:  110 of  690 MB written (fifo 100%) [buf  90%]  13.2x.
Track 01:  111 of  690 MB written (fifo 100%) [buf  90%]  12.1x.
Track 01:  112 of  690 MB written (fifo  99%) [buf  93%]  12.8x.
Track 01:  113 of  690 MB written (fifo  99%) [buf  93%]  12.1x.
Track 01:  114 of  690 MB written (fifo 100%) [buf  87%]  11.8x.
Track 01:  115 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  116 of  690 MB written (fifo 100%) [buf  90%]  13.0x.
Track 01:  117 of  690 MB written (fifo 100%) [buf  90%]  12.2x.
Track 01:  118 of  690 MB written (fifo  99%) [buf  93%]  12.9x.
Track 01:  119 of  690 MB written (fifo  99%) [buf  93%]  12.2x.
Track 01:  120 of  690 MB written (fifo 100%) [buf  87%]  11.9x.
Track 01:  121 of  690 MB written (fifo 100%) [buf  87%]  12.2x.
Track 01:  122 of  690 MB written (fifo 100%) [buf  90%]  13.0x.
Track 01:  123 of  690 MB written (fifo 100%) [buf  90%]  12.2x.
Track 01:  124 of  690 MB written (fifo  99%) [buf  93%]  13.0x.
Track 01:  125 of  690 MB written (fifo  99%) [buf  93%]  12.0x.
Track 01:  126 of  690 MB written (fifo  99%) [buf  93%]  12.3x.
Track 01:  127 of  690 MB written (fifo 100%) [buf  87%]  12.0x.
Track 01:  128 of  690 MB written (fifo  99%) [buf  96%]  13.5x.
Track 01:  129 of  690 MB written (fifo 100%) [buf  90%]  12.0x.
Track 01:  130 of  690 MB written (fifo 100%) [buf  87%]  12.3x.
Track 01:  131 of  690 MB written (fifo 100%) [buf  90%]  13.2x.
Track 01:  132 of  690 MB written (fifo 100%) [buf  90%]  12.4x.
Track 01:  133 of  690 MB written (fifo 100%) [buf  93%]  13.1x.
Track 01:  134 of  690 MB written (fifo  99%) [buf  93%]  12.4x.
Track 01:  135 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  136 of  690 MB written (fifo 100%) [buf  87%]  12.4x.
Track 01:  137 of  690 MB written (fifo 100%) [buf  90%]  13.2x.
Track 01:  138 of  690 MB written (fifo 100%) [buf  90%]  12.4x.
Track 01:  139 of  690 MB written (fifo  99%) [buf  93%]  12.9x.
Track 01:  140 of  690 MB written (fifo  99%) [buf  93%]  12.1x.
Track 01:  141 of  690 MB written (fifo 100%) [buf  87%]  11.8x.
Track 01:  142 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  143 of  690 MB written (fifo 100%) [buf  90%]  12.9x.
Track 01:  144 of  690 MB written (fifo 100%) [buf  90%]  12.1x.
Track 01:  145 of  690 MB written (fifo  99%) [buf  93%]  12.9x.
Track 01:  146 of  690 MB written (fifo  99%) [buf  93%]  12.1x.
Track 01:  147 of  690 MB written (fifo 100%) [buf  87%]  11.9x.
Track 01:  148 of  690 MB written (fifo 100%) [buf  87%]  12.2x.
Track 01:  149 of  690 MB written (fifo 100%) [buf  90%]  13.0x.
Track 01:  150 of  690 MB written (fifo 100%) [buf  90%]  12.2x.
Track 01:  151 of  690 MB written (fifo  99%) [buf  93%]  12.9x.
Track 01:  152 of  690 MB written (fifo  99%) [buf  93%]  12.2x.
Track 01:  153 of  690 MB written (fifo 100%) [buf  87%]  11.9x.
Track 01:  154 of  690 MB written (fifo 100%) [buf  87%]  12.2x.
Track 01:  155 of  690 MB written (fifo 100%) [buf  90%]  13.0x.
Track 01:  156 of  690 MB written (fifo 100%) [buf  90%]  12.0x.
Track 01:  157 of  690 MB written (fifo 100%) [buf  90%]  12.3x.
Track 01:  158 of  690 MB written (fifo  99%) [buf  93%]  13.0x.
Track 01:  159 of  690 MB written (fifo  99%) [buf  93%]  12.3x.
Track 01:  160 of  690 MB written (fifo  99%) [buf  96%]  13.1x.
Track 01:  161 of  690 MB written (fifo  99%) [buf  93%]  12.3x.
Track 01:  162 of  690 MB written (fifo 100%) [buf  87%]  12.0x.
Track 01:  163 of  690 MB written (fifo 100%) [buf  87%]  12.3x.
Track 01:  164 of  690 MB written (fifo 100%) [buf  90%]  13.1x.
Track 01:  165 of  690 MB written (fifo 100%) [buf  90%]  12.3x.
Track 01:  166 of  690 MB written (fifo  99%) [buf  93%]  13.1x.
Track 01:  167 of  690 MB written (fifo  99%) [buf  93%]  12.3x.
Track 01:  168 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  169 of  690 MB written (fifo 100%) [buf  87%]  12.4x.
Track 01:  170 of  690 MB written (fifo 100%) [buf  90%]  13.2x.
Track 01:  171 of  690 MB written (fifo 100%) [buf  90%]  12.4x.
Track 01:  172 of  690 MB written (fifo  99%) [buf  93%]  13.2x.
Track 01:  173 of  690 MB written (fifo  99%) [buf  93%]  12.4x.
Track 01:  174 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  175 of  690 MB written (fifo 100%) [buf  87%]  12.2x.
Track 01:  176 of  690 MB written (fifo 100%) [buf  90%]  12.9x.
Track 01:  177 of  690 MB written (fifo 100%) [buf  90%]  12.1x.
Track 01:  178 of  690 MB written (fifo  99%) [buf  93%]  12.8x.
Track 01:  179 of  690 MB written (fifo  99%) [buf  93%]  12.1x.
Track 01:  180 of  690 MB written (fifo 100%) [buf  87%]  11.8x.
Track 01:  181 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  182 of  690 MB written (fifo 100%) [buf  90%]  12.9x.
Track 01:  183 of  690 MB written (fifo 100%) [buf  90%]  12.1x.
Track 01:  184 of  690 MB written (fifo  99%) [buf  93%]  12.8x.
Track 01:  185 of  690 MB written (fifo  99%) [buf  93%]  12.1x.
Track 01:  186 of  690 MB written (fifo 100%) [buf  87%]  11.8x.
Track 01:  187 of  690 MB written (fifo 100%) [buf  87%]  12.1x.
Track 01:  188 of  690 MB written (fifo 100%) [buf  87%]  12.5x.
Track 01:  189 of  690 MB written (fifo 100%) [buf  90%]  13.4x.
Track 01:  190 of  690 MB written (fifo 100%) [buf  90%]  12.5x.
Track 01:  191 of  690 MB written (fifo  99%) [buf  93%]  13.3x.
Track 01:  192 of  690 MB written (fifo 100%) [buf  90%]  12.6x.
Track 01:  193 of  690 MB written (fifo  99%) [buf  93%]  13.3x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 82 0C 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 47 00 00 00 00 0E 09 0C 00 00 00 01 00 00
Sense Key: 0x7 Data Protect, Segment 11
Sense Code: 0x00 Qual 0x01 (filemark detected) Fru 0x0
Sense flags: Blk 0 (not valid) end of medium 
cmd finished after 0.647s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 202399744 bytes
Writing  time:  143.399s
Average write speed  33.8x.
Min drive buffer fill was 87%
Fixating...
Fixating time:    3.900s
/usr/bin/wodim: fifo had 3380 puts and 3189 gets.
/usr/bin/wodim: fifo was 0 times empty and 2225 times full, min fill was 96%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=24 -dao driveropts=burnfree -eject -data -tsize=353718s -

---

### Post by Promille on 2008-08-29
C'mon guys,  someone gotta have some clue about this :(

---

### Post by skullmunky on 2008-08-29
i think this is actually a reported bug, the relevant part being:
```

/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'

```

search in the bug database and see if there's a solution there.

Another thing you can try: replace wodim, the program that does the burning, with the more mature original cdrtools.

[http://ubuntuforums.org/showthread.php?p=5552123](http://ubuntuforums.org/showthread.php?p=5552123)

---

### Post by Therion on 2008-08-29
Cheap suggestion (it worked for me!):  Change your 40 wire, 40 connector cable for an **80 wire,** 40 connector cable.  [See this pic](http://upload.wikimedia.org/wikipedia/commons/thumb/6/61/IDE_cable_40_pin_&_80_pin.jpg/454px-IDE_cable_40_pin_&_80_pin.jpg).  

Cable is same-same, but the additional wires (even though they don't connect any pins) eliminate electromagnetic "noise".  Mine set me back about $5 at my local computer warehouse and I've been problem free since I switched.

---

### Post by Promille on 2008-08-30
Thanks for the suggestion guys. I dont think i should change the wires, because its a laptop. But thanks for the suggestion anyways.

I read the other tread Skullmunky and did exactly what it said,but k3b still says "using Wodim 1.1.6"

Currently I'm on 35%, ill let you know how it went

-Promille

---

