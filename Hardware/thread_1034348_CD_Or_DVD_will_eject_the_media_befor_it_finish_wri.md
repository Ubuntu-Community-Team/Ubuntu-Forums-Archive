---
title: "CD Or DVD will eject the media befor it finish writing"
date: 2009-01-08
forum: Hardware
---

### Post by frank392 on 2009-01-08
Hi,
when i try to burn an iso file (any) it fails to do it i will eject the media before it finish writing I have try it at many speeds and many programs, with the same result. here is the log output  of k3b:
>  System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.27-7-generic
Devices
-----------------------
PHILIPS DVD+-RW SDVD8441 PA48 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.8

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.8
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
Revision       : 'PA48'
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
Speed set to 1411 KB/s
Track 01: data   629 MB        Total size:      722 MB (71:36.33) = 322225 sectors
Lout start:      723 MB (71:38/25) = 322225 sectors
Current Secsize: 2048
ATIP info from disk:
Indicated writing power: 5
Is not unrestricted
Is not erasable
Disk sub type: Medium Type A, high Beta category (A+) (3)
ATIP start of lead in:  -11634 (97:26/66)
ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 37621
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
  1 seconds.
  0 seconds.
Operation starts.
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
cmd finished after 0.001s timeout 240s
/usr/bin/wodim: Cannot get next writable address for 'invisible' track.
/usr/bin/wodim: This means that we are checking recorded media.
/usr/bin/wodim: This media cannot be written in streaming mode anymore.
/usr/bin/wodim: If you like to write to 'preformatted' RW media, try to blank the media first.
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of  629 MB written.
Track 01:    1 of  629 MB written (fifo 100%) [buf  87%]   3.9x.
Track 01:    2 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:    3 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:    4 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:    5 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:    6 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:    7 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:    8 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:    9 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   10 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   11 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   12 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   13 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:   14 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:   15 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   16 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:   17 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   18 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   19 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:   20 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:   21 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   22 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   23 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   24 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   25 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:   26 of  629 MB written (fifo  99%) [buf  93%]   7.7x.
Track 01:   27 of  629 MB written (fifo 100%) [buf  87%]   7.5x.
Track 01:   28 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   29 of  629 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:   30 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   31 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:   32 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:   33 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:   34 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   35 of  629 MB written (fifo  99%) [buf  96%]   8.6x.
Track 01:   36 of  629 MB written (fifo 100%) [buf  90%]   7.7x.
Track 01:   37 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   38 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:   39 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   40 of  629 MB written (fifo 100%) [buf  93%]   8.5x.
Track 01:   41 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:   42 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   43 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:   44 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   45 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   46 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:   47 of  629 MB written (fifo 100%) [buf  93%]   7.9x.
Track 01:   48 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   49 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   50 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   51 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   52 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:   53 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:   54 of  629 MB written (fifo 100%) [buf  87%]   7.5x.
Track 01:   55 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   56 of  629 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:   57 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   58 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:   59 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:   60 of  629 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:   61 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   62 of  629 MB written (fifo 100%) [buf  90%]   2.9x.
Track 01:   63 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:   64 of  629 MB written (fifo 100%) [buf  90%]   8.2x.
Track 01:   65 of  629 MB written (fifo  99%) [buf  93%]   8.7x.
Track 01:   66 of  629 MB written (fifo  99%) [buf  93%]   8.2x.
Track 01:   67 of  629 MB written (fifo  99%) [buf  96%]   8.6x.
Track 01:   68 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:   69 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   70 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:   71 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:   72 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:   73 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:   74 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:   75 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   76 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   77 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:   78 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   79 of  629 MB written (fifo 100%) [buf  93%]   8.4x.
Track 01:   80 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:   81 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   82 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:   83 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:   84 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:   85 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:   86 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:   87 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:   88 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:   89 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:   90 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:   91 of  629 MB written (fifo 100%) [buf  93%]   8.4x.
Track 01:   92 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:   93 of  629 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:   94 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:   95 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:   96 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:   97 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:   98 of  629 MB written (fifo 100%) [buf  93%]   8.6x.
Track 01:   99 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  100 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  101 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  102 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  103 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  104 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  105 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  106 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  107 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  108 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  109 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  110 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  111 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  112 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  113 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  114 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  115 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  116 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  117 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  118 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  119 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  120 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  121 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  122 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  123 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  124 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:  125 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:  126 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  127 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  128 of  629 MB written (fifo  99%) [buf  96%]   8.8x.
Track 01:  129 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  130 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  131 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  132 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  133 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  134 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  135 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  136 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  137 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  138 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  139 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  140 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  141 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  142 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  143 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  144 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  145 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  146 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  147 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  148 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  149 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  150 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:  151 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:  152 of  629 MB written (fifo 100%) [buf  93%]   7.9x.
Track 01:  153 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  154 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  155 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  156 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  157 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  158 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  159 of  629 MB written (fifo 100%) [buf  93%]   8.1x.
Track 01:  160 of  629 MB written (fifo  99%) [buf  96%]   8.7x.
Track 01:  161 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  162 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  163 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  164 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  165 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  166 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  167 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  168 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  169 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  170 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  171 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  172 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  173 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  174 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  175 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  176 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  177 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  178 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  179 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  180 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  181 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  182 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  183 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  184 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  185 of  629 MB written (fifo 100%) [buf  93%]   7.9x.
Track 01:  186 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  187 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  188 of  629 MB written (fifo 100%) [buf  87%]   8.2x.
Track 01:  189 of  629 MB written (fifo 100%) [buf  90%]   8.7x.
Track 01:  190 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  191 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  192 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  193 of  629 MB written (fifo 100%) [buf  93%]   8.5x.
Track 01:  194 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  195 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  196 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  197 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  198 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  199 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  200 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  201 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  202 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  203 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  204 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  205 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  206 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  207 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  208 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  209 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  210 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  211 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  212 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  213 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  214 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  215 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  216 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  217 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  218 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  219 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  220 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  221 of  629 MB written (fifo  99%) [buf  96%]   8.7x.
Track 01:  222 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:  223 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  224 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  225 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  226 of  629 MB written (fifo 100%) [buf  93%]   8.5x.
Track 01:  227 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  228 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  229 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  230 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  231 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  232 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  233 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  234 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  235 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  236 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  237 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  238 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  239 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:  240 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  241 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  242 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  243 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:  244 of  629 MB written (fifo 100%) [buf  93%]   8.3x.
Track 01:  245 of  629 MB written (fifo 100%) [buf  93%]   7.9x.
Track 01:  246 of  629 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:  247 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  248 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  249 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  250 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  251 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  252 of  629 MB written (fifo 100%) [buf  93%]   8.1x.
Track 01:  253 of  629 MB written (fifo  99%) [buf  96%]   8.7x.
Track 01:  254 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  255 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  256 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  257 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  258 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  259 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  260 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  261 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  262 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  263 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  264 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  265 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  266 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  267 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  268 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  269 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  270 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  271 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  272 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  273 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  274 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  275 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  276 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  277 of  629 MB written (fifo 100%) [buf  93%]   8.5x.
Track 01:  278 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:  279 of  629 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:  280 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  281 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  282 of  629 MB written (fifo 100%) [buf  90%]   8.5x.
Track 01:  283 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  284 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  285 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  286 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  287 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  288 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  289 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  290 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  291 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  292 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  293 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  294 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  295 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  296 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  297 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  298 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  299 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  300 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  301 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  302 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  303 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:  304 of  629 MB written (fifo 100%) [buf  93%]   8.3x.
Track 01:  305 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:  306 of  629 MB written (fifo 100%) [buf  87%]   7.6x.
Track 01:  307 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  308 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  309 of  629 MB written (fifo 100%) [buf  90%]   7.8x.
Track 01:  310 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:  311 of  629 MB written (fifo  99%) [buf  93%]   7.8x.
Track 01:  312 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  313 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  314 of  629 MB written (fifo  99%) [buf  96%]   8.8x.
Track 01:  315 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  316 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  317 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  318 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  319 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  320 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  321 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  322 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  323 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  324 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  325 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  326 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  327 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  328 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  329 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  330 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  331 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  332 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  333 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  334 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  335 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  336 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  337 of  629 MB written (fifo  99%) [buf  93%]   8.4x.
Track 01:  338 of  629 MB written (fifo  99%) [buf  93%]   7.9x.
Track 01:  339 of  629 MB written (fifo 100%) [buf  87%]   7.7x.
Track 01:  340 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  341 of  629 MB written (fifo 100%) [buf  90%]   8.4x.
Track 01:  342 of  629 MB written (fifo 100%) [buf  90%]   7.9x.
Track 01:  343 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  344 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  345 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  346 of  629 MB written (fifo  99%) [buf  96%]   3.7x.
Track 01:  347 of  629 MB written (fifo 100%) [buf  93%]   8.2x.
Track 01:  348 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  349 of  629 MB written (fifo 100%) [buf  87%]   8.2x.
Track 01:  350 of  629 MB written (fifo 100%) [buf  90%]   8.7x.
Track 01:  351 of  629 MB written (fifo 100%) [buf  90%]   8.2x.
Track 01:  352 of  629 MB written (fifo  99%) [buf  93%]   8.7x.
Track 01:  353 of  629 MB written (fifo  99%) [buf  93%]   8.2x.
Track 01:  354 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  355 of  629 MB written (fifo 100%) [buf  87%]   8.2x.
Track 01:  356 of  629 MB written (fifo 100%) [buf  90%]   8.7x.
Track 01:  357 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  358 of  629 MB written (fifo  99%) [buf  93%]   8.7x.
Track 01:  359 of  629 MB written (fifo  99%) [buf  93%]   8.2x.
Track 01:  360 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  361 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  362 of  629 MB written (fifo 100%) [buf  90%]   8.7x.
Track 01:  363 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  364 of  629 MB written (fifo 100%) [buf  93%]   8.7x.
Track 01:  365 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  366 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  367 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  368 of  629 MB written (fifo 100%) [buf  90%]   8.7x.
Track 01:  369 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  370 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  371 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  372 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  373 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  374 of  629 MB written (fifo 100%) [buf  87%]   8.2x.
Track 01:  375 of  629 MB written (fifo 100%) [buf  90%]   8.8x.
Track 01:  376 of  629 MB written (fifo 100%) [buf  90%]   8.2x.
Track 01:  377 of  629 MB written (fifo 100%) [buf  93%]   8.7x.
Track 01:  378 of  629 MB written (fifo 100%) [buf  90%]   8.2x.
Track 01:  379 of  629 MB written (fifo  99%) [buf  93%]   8.7x.
Track 01:  380 of  629 MB written (fifo  99%) [buf  93%]   8.2x.
Track 01:  381 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  382 of  629 MB written (fifo 100%) [buf  87%]   8.2x.
Track 01:  383 of  629 MB written (fifo 100%) [buf  90%]   8.8x.
Track 01:  384 of  629 MB written (fifo 100%) [buf  90%]   8.2x.
Track 01:  385 of  629 MB written (fifo  99%) [buf  93%]   8.7x.
Track 01:  386 of  629 MB written (fifo  99%) [buf  93%]   8.2x.
Track 01:  387 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  388 of  629 MB written (fifo 100%) [buf  87%]   8.2x.
Track 01:  389 of  629 MB written (fifo 100%) [buf  90%]   8.8x.
Track 01:  390 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  391 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  392 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  393 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  394 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  395 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  396 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  397 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  398 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  399 of  629 MB written (fifo 100%) [buf  87%]   7.8x.
Track 01:  400 of  629 MB written (fifo 100%) [buf  87%]   8.0x.
Track 01:  401 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Track 01:  402 of  629 MB written (fifo 100%) [buf  90%]   8.0x.
Track 01:  403 of  629 MB written (fifo  99%) [buf  93%]   8.5x.
Track 01:  404 of  629 MB written (fifo  99%) [buf  93%]   8.0x.
Track 01:  405 of  629 MB written (fifo  99%) [buf  93%]   8.3x.
Track 01:  406 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  407 of  629 MB written (fifo 100%) [buf  96%]   9.1x.
Track 01:  408 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  409 of  629 MB written (fifo 100%) [buf  87%]   8.3x.
Track 01:  410 of  629 MB written (fifo 100%) [buf  90%]   8.8x.
Track 01:  411 of  629 MB written (fifo 100%) [buf  90%]   8.3x.
Track 01:  412 of  629 MB written (fifo  99%) [buf  93%]   8.7x.
Track 01:  413 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  414 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  415 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  416 of  629 MB written (fifo 100%) [buf  90%]   8.7x.
Track 01:  417 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  418 of  629 MB written (fifo  99%) [buf  93%]   8.6x.
Track 01:  419 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  420 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  421 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  422 of  629 MB written (fifo 100%) [buf  90%]   8.7x.
Track 01:  423 of  629 MB written (fifo 100%) [buf  90%]   8.1x.
Track 01:  424 of  629 MB written (fifo 100%) [buf  93%]   8.6x.
Track 01:  425 of  629 MB written (fifo  99%) [buf  93%]   8.1x.
Track 01:  426 of  629 MB written (fifo 100%) [buf  87%]   7.9x.
Track 01:  427 of  629 MB written (fifo 100%) [buf  87%]   8.1x.
Track 01:  428 of  629 MB written (fifo 100%) [buf  90%]   8.6x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 03 58 BD 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 47 00 00 00 00 0E 09 0C 00 00 00 01 00 00
Sense Key: 0x7 Data Protect, Segment 11
Sense Code: 0x00 Qual 0x01 (filemark detected) Fru 0x0
Sense flags: Blk 0 (not valid) end of medium
cmd finished after 0.181s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 449177600 bytes
Writing  time:  384.796s
Average write speed  11.2x.
Min drive buffer fill was 87%
Fixating...
Fixating time:    3.497s
/usr/bin/wodim: fifo had 7267 puts and 7076 gets.
/usr/bin/wodim: fifo was 0 times empty and 4920 times full, min fill was 97%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=8 -dao driveropts=burnfree -eject -data -tsize=322225s -



thank you very much

---

