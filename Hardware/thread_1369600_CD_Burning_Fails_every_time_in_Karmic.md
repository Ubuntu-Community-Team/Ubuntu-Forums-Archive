---
title: "CD Burning Fails every time in Karmic"
date: 2010-01-01
forum: Hardware
---

### Post by lexxonnet on 2010-01-01
Hi There,

Just trying to see if anyone else is experiencing this problem. I've been having trouble burning CDs in Linux since Jaunty at least. I don't do it often enough, but I've tried 4 times today and produced 4 coasters in the process.

I'm running Kubuntu Karmic at present. I've tried burning CDs with K3B, Brasero, Gnomebaker and from the Command Line, using cdrecord.

All of them seem to fail. I've tried running them as root and otherwise and at different speeds, without any success.

Here is my output from cdrecord, attempting to burn an audio cd.

```

root@maxwell:~# cdrecord -v speed=2 dev=3,0,0 -audio k3b_audio_0_01.wav k3b_audio_0_02.wav k3b_audio_0_03.wav k3b_audio_0_04.wav k3b_audio_0_05.wav k3b_audio_0_06.wav k3b_audio_0_07.wav k3b_audio_0_08.wav k3b_audio_0_09.wav k3b_audio_0_10.wav k3b_audio_0_11.wav k3b_audio_0_12.wav k3b_audio_0_13.wav
wodim: No write mode specified.
wodim: Asuming -tao mode.      
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 0 = CD-DA                                                         
scsidev: '3,0,0'                                                            
scsibus: 3 target: 0 lun: 0                                                 
WARNING: the deprecated pseudo SCSI syntax found as device specification.   
Support for that may cease in the future versions of wodim. For now,        
the device will be mapped to a block device file where possible.            
Run "wodim --devices" for details.                                          
Linux sg driver version: 3.5.27                                             
Wodim version: 1.1.9                                                        
SCSI buffer size: 64512                                                     
Device type    : Removable CD-ROM                                           
Version        : 5                                                          
Response Format: 2                                                          
Capabilities   :                                                            
Vendor_info    : 'TEAC    '                                                 
Identification : 'DVD+-RW DVW28SLC'                                         
Revision       : 'A.06'                                                     
Device seems to be: Generic mmc2 DVD-R/DVD-RW.                              
Current: 0x0009 (CD-R)                                                      
Profile: 0x002B (DVD+R/DL)                                                  
Profile: 0x001B (DVD+R)                                                     
Profile: 0x001A (DVD+RW)                                                    
Profile: 0x0016 (DVD-R/DL layer jump recording)                             
Profile: 0x0015 (DVD-R/DL sequential recording)                             
Profile: 0x0014 (DVD-RW sequential recording)                               
Profile: 0x0013 (DVD-RW restricted overwrite)                               
Profile: 0x0012 (DVD-RAM)                                                   
Profile: 0x0002 (Removable disk)                                            
Profile: 0x0011 (DVD-R sequential recording)                                
Profile: 0x0010 (DVD-ROM)                                                   
Profile: 0x000A (CD-RW)                                                     
Profile: 0x0009 (CD-R) (current)                                            
Profile: 0x0008 (CD-ROM)                                                    
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).                     
Driver flags   : MMC-3 SWABAUDIO BURNFREE                                   
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R                           
Drive buf size : 1267712 = 1238 KB                                          
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device  
communication breaks or freezes immediately after that.                     
FIFO size      : 12582912 = 12288 KB                                        
Track 01: audio   23 MB (02:20.44) no preemp                                
Track 02: audio   46 MB (04:33.97) no preemp                                
Track 03: audio   29 MB (02:53.45) no preemp                                
Track 04: audio   31 MB (03:04.85) no preemp                                
Track 05: audio   28 MB (02:47.08) no preemp                                
Track 06: audio   82 MB (08:08.74) no preemp                                
Track 07: audio   86 MB (08:33.04) no preemp                                
Track 08: audio   76 MB (07:34.36) no preemp                                
Track 09: audio   89 MB (08:51.00) no preemp                                
Track 10: audio   58 MB (05:46.30) no preemp                                
Track 11: audio   92 MB (09:08.09) no preemp                                
Track 12: audio   66 MB (06:34.93) no preemp                                
Track 13: audio   53 MB (05:20.48) no preemp                                
Total size:      767 MB (76:00.76) = 342057 sectors                         
Lout start:      767 MB (76:02/57) = 342057 sectors                         
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
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 17789         
Speed set to 705 KB/s                                                       
Starting to write CD/DVD at speed   4.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts. 
Waiting for reader process to fill input buffer ... input buffer ready.     
Performing OPC...                                                           
Starting new track at sector: 0                                             
Track 01:   23 of   23 MB written (fifo 100%) [buf 100%]   4.2x.            
Track 01: Total bytes read/written: 24773616/24773616 (10533 sectors).      
Starting new track at sector: 10685                                         
Track 02:   22 of   46 MB written (fifo 100%) [buf 100%]   4.0x.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 50 21 00 00 1B 00                                                                                           
status: 0x2 (CHECK CONDITION)                                                                                                 
Sense Bytes: 70 00 03 00 04 27 73 0E 00 00 00 00 0C 00 00 00                                                                  
Sense Key: 0x3 Medium Error, Segment 0                                                                                        
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0                                                                              
Sense flags: Blk 272243 (not valid)                                                                                           
cmd finished after 2.978s timeout 40s                                                                                         

write track data: error after 23115456 bytes
wodim: A write error occured.               
wodim: Please properly read the error message above.
Writing  time:   94.862s                            
Average write speed  52.6x.                         
Min drive buffer fill was 81%                       
Fixating...                                         
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00                                      
status: 0x2 (CHECK CONDITION)                                            
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 72 03 00 00             
Sense Key: 0x5 Illegal Request, Segment 0                                
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0
Sense flags: Blk 0 (not valid)                                                           
cmd finished after 0.909s timeout 480s                                                   
cmd finished after 0.909s timeout 480s
wodim: Cannot fixate disk.
Fixating time:    0.921s
wodim: fifo had 946 puts and 756 gets.
wodim: fifo was 0 times empty and 717 times full, min fill was 92%.


```

I don't seem to have any issues burning in Windows on my other partition. I've searched through a few bug reports and can't seem to find a solution anywhere. Please let me know if anyone else is facing this bug!!

Oh, and a Happy New Year to everyone :)

---

