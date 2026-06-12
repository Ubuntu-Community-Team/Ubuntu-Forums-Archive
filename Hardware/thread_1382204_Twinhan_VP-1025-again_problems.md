---
title: "Twinhan VP-1025-again problems"
date: 2010-01-15
forum: Hardware
---

### Post by batjka on 2010-01-15
Good time of day! 
I recently acquired a DVB-card with the trade name "TwinhanDTV Sat Express"-in fact it is "Twinhan VP-1025". But after all the items of this post [http://ubuntuforums.org/showthread.php?t=246959]("http://ubuntuforums.org/showthread.php?t=246959"), I saw the following:

batjka@baby:~$ dmesg | grep bt
[    9.554374] Linux video capture interface: v2.00
[    9.592452] bttv: driver version 0.9.18 loaded
[    9.592457] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.616125] bt878: AUDIO driver version 0.0.0 loaded


With the bttv driver is not even defined. 

 Careful examination of the DVB-card revealed that she has a little prefix, namely the 1025i and is defined as:

batjka@baby:~$ lspci | grep Twinhan
02:01.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)


and 

batjka@baby:~$ dmesg
.............
[   14.687475] Mantis 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                      
[   14.687582] irq: 22, latency: 32                                                                 
[   14.687584]  memory: 0xdfeff000, mmio: 0xe0908000                                                
[   14.687588] found a UNKNOWN PCI UNKNOWN device on (02:01.0),                                     
[   14.687591]     Mantis Rev 1 [1822:0012], irq: 22, latency: 32                                   
[   14.687594]     memory: 0xdfeff000, mmio: 0xe0908000                                             
[   14.690516]     MAC Address=[00:08:ca:ca:08:bf]                                                  
[   14.690568] mantis_alloc_buffers (0): DMA=0x15470000 cpu=0xd5470000 size=65536                   
[   14.690585] mantis_alloc_buffers (0): RISC=0x17579000 cpu=0xd7579000 size=1000                   
[   14.690592] DVB: registering new adapter (Mantis dvb adapter)                                    
[   14.924935] ppdev: user-space parallel port driver                                               
[   14.968376] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17                   
[   14.968696] Intel ICH 0000:00:1f.5: setting latency timer to 64                                  
[   15.119030] psmouse serio1: ID: 10 00 64<3>mantis_ca_init (0): Registering EN50221 device        
[   15.212748] mantis_ca_init (0): Registered EN50221 device                                        
[   15.212766] mantis_hif_init (0): Adapter(0) Initializing Mantis Host Interface 
.............


But if you notice that there is no frontend:

batjka@baby:~$ ls /dev/dvb/adapter1
ca0  demux0  dvr0  net0

batjka@baby:~$ lsmod
Module                  Size  Used by
bsd_comp               13824  0      
ppp_async              17024  1      
crc_ccitt              10240  1 ppp_async
option                 28164  1          
usb_storage            99776  0          
bridge                 56212  0          
stp                    10756  1 bridge   
bnep                   20224  2          
input_polldev          12040  0          
video                  25616  0          
output                 11136  1 video    
xfs                   552744  1          
reiserfs              235520  3          
lp                     17156  0          
snd_intel8x0           37660  4          
snd_ac97_codec        112292  1 snd_intel8x0
ppdev                  15748  0             
ac97_bus                9984  1 snd_ac97_codec
snd_pcm_oss            46208  0               
snd_mixer_oss          22656  1 snd_pcm_oss   
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          11012  0                                        
snd_seq_oss            38016  0                                        
snd_seq_midi           14464  0                                        
snd_rawmidi            29824  1 snd_seq_midi                           
snd_seq_midi_event     15360  2 snd_seq_oss,snd_seq_midi               
snd_seq                57136  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
isl6421                10112  1                                                          
snd_timer              29320  2 snd_pcm,snd_seq                                          
snd_seq_device         15244  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mantis                 48900  0                                                           
lnbp21                 10624  1 mantis                                                    
mb86a16                28928  1 mantis                                                    
b2c2_flexcop_pci       15764  0                                                           
snd                    62500  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device                                                 
ir_common              57984  1 mantis                                                              
stb6100                15236  1 mantis                                                              
tda10021               14212  1 mantis                                                              
b2c2_flexcop           37132  1 b2c2_flexcop_pci                                                    
soundcore              15456  1 snd                                                                 
psmouse                61588  0
tda10023               14852  1 mantis
stb0899                43140  1 mantis
stv0299                17800  1 mantis
cx24123                21768  2 b2c2_flexcop
snd_page_alloc         17160  2 snd_intel8x0,snd_pcm
serio_raw              13572  0
pcspkr                 10752  0
iTCO_wdt               19236  0
iTCO_vendor_support    11908  1 iTCO_wdt
cx24113                16004  2 b2c2_flexcop
nvidia               7097928  34
dvb_core               99208  3 mantis,b2c2_flexcop,stv0299
s5h1420                19588  1 b2c2_flexcop
pl2303                 25348  0
ir_core                15628  2 mantis,ir_common
i2c_core               31892  14 isl6421,mantis,lnbp21,mb86a16,stb6100,tda10021,b2c2_flexcop,tda10023,stb0899,stv0299,cx24123,cx24113,nvidia,s5h1420
usbserial              39528  4 option,pl2303
shpchp                 40340  0
intel_agp              34236  1
agpgart                42440  2 nvidia,intel_agp
parport_pc             40100  1
parport                42476  3 lp,ppdev,parport_pc
8139too                31616  0
8139cp                 27904  0
mii                    13568  2 8139too,8139cp
floppy                 62532  0


Who has any ideas on how to make this card work properly?

---

### Post by wowks on 2010-09-27
> **batjka said:**
> ho has any ideas on how to make this card work properly?

no

---

