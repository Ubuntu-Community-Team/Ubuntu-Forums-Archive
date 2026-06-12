---
title: "El disco tiene muchos sectores erroneos"
date: 2010-03-26
forum: Hardware
---

### Post by Air23 on 2010-03-26
Hola!

Ayer a la noche me apareció un alerta diciendo "Uno o mas discos pueden estar fallado".

Al clickear en el icono que apareció en el area de notificación se abre la Utilidad de discos y me dice "El disco tiene muchos sectores erróneos" y que respalde los datos y cambie el disco (pego capturas de la pantalla)

[[IMG]http://img2.imageshack.us/img2/5802/260302461.th.png[/IMG]](http://img2.imageshack.us/i/260302461.png/) [[IMG]http://img545.imageshack.us/img545/2540/260302462.th.png[/IMG]](http://img545.imageshack.us/i/260302462.png/) [[IMG]http://img214.imageshack.us/img214/4662/260302463.th.png[/IMG]](http://img214.imageshack.us/i/260302463.png/) [[IMG]http://img231.imageshack.us/img231/2228/260302464.th.png[/IMG]](http://img231.imageshack.us/i/260302464.png/) [[IMG]http://img686.imageshack.us/img686/3876/260302465.th.png[/IMG]](http://img686.imageshack.us/i/260302465.png/)

La PC en cuestión es una notebook Dell Inspiron 1545 prácticamente nueva (comprada hace menos de un mes) con Ubuntu KK.
El HD es un Samsung HM160HI.

Decidi investigar un poquito y encontré que existe un bug en libatasmart en el cual Palimpsest da falsos positivos ([https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136))

Instale Smartmontools y corri un test obteniendo lo siguiente:
```
gra@gra-laptop:~/Descargas$ sudo smartctl -t long -F samsung /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 54 minutes for test to complete.
Test will complete after Fri Mar 26 04:29:22 2010

Use smartctl -X to abort test.
gra@gra-laptop:~/Descargas$ sudo smartctl -a /dev/sda
[sudo] password for gra: 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM160HI
Serial Number:    S21TJ56SA05745
Firmware Version: HH100-15
User Capacity:    160.041.885.696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Fri Mar 26 04:32:48 2010 ART

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (  54) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  54) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       1937
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       367
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       79
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       44
191 G-Sense_Error_Rate      0x0032   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       2
194 Temperature_Celsius     0x0022   079   079   000    Old_age   Always       -       53 (Lifetime Min/Max 22/53)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4734
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       55
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       361
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        79         -
# 2  Short offline       Completed without error       00%        77         -
# 3  Extended offline    Completed without error       00%        77         -
# 4  Short offline       Completed without error       00%        76         -
# 5  Short offline       Completed without error       00%        75         -
# 6  Short offline       Completed without error       00%         1         -
# 7  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```
Tambien probe con Hard Disk Sentinel([http://www.hdsentinel.com/](http://www.hdsentinel.com/))
```

  -- General Information --

    Application Information
    -----------------------
    Installed Version . . . . . . . . . . . . . . . .  Hard Disk Sentinel 0.03
    Current Date And Time . . . . . . . . . . . . . .  26-3-10 03:19:45

    Computer Information
    --------------------
    Computer Name . . . . . . . . . . . . . . . . . .  gra-laptop
    MAC Address . . . . . . . . . . . . . . . . . . .  00:23:AE:EA:19:D0

    System Information
    ------------------
    OS Version. . . . . . . . . . . . . . . . . . . .  Linux : 2.6.31-20-generic (#57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010)
    Process ID. . . . . . . . . . . . . . . . . . . .  5727
    Uptime. . . . . . . . . . . . . . . . . . . . . .  56078 sec (0 days, 15 hours, 34 min, 38 sec)



  -- Physical Disk Information - Disk: #0: SAMSUNG HM160HI --

    Hard Disk Summary
    -----------------
    Hard Disk Number. . . . . . . . . . . . . . . . .  0
    Hard Disk Device. . . . . . . . . . . . . . . . .  /dev/sda
    Interface . . . . . . . . . . . . . . . . . . . .  S-ATA
    Hard Disk Model ID. . . . . . . . . . . . . . . .  SAMSUNG HM160HI
    Hard Disk Revision. . . . . . . . . . . . . . . .  HH100-15
    Hard Disk Serial Number . . . . . . . . . . . . .  S21TJ56SA05745
    Hard Disk Total Size. . . . . . . . . . . . . . .  165148 MB
    Current Temperature . . . . . . . . . . . . . . .  48 °C (118 °F)
    Power On Time . . . . . . . . . . . . . . . . . .  3 days, 6 hours
    Estimated Remaining Lifetime. . . . . . . . . . .  35 days
    Health. . . . . . . . . . . . . . . . . . . . . .  ##------------------ 14 % (Poor)
    Performance . . . . . . . . . . . . . . . . . . .  #################### 100 % (Excellent)

    The drive found 222 bad sectors during its self test.
    Based on the number of remapping operations, the health of the disk was decreased in different steps.
    There are 55 weak sectors found on the disk surface. They may be remapped any time in the later use of the disk.
      It is recommended to backup often to prevent data loss.

    ATA Information
    ---------------
    Hard Disk Cylinders . . . . . . . . . . . . . . .  310101
    Hard Disk Heads . . . . . . . . . . . . . . . . .  16
    Hard Disk Sectors . . . . . . . . . . . . . . . .  63
    Total Sectors . . . . . . . . . . . . . . . . . .  312581808
    ATA Revision. . . . . . . . . . . . . . . . . . .  7
    Bytes Per Sector. . . . . . . . . . . . . . . . .  554
    Buffer Size . . . . . . . . . . . . . . . . . . .  8192 KB
    Multiple Sectors. . . . . . . . . . . . . . . . .  16
    Error Correction Bytes. . . . . . . . . . . . . .  4
    Unformatted Capacity. . . . . . . . . . . . . . .  165148 MB
    Maximum PIO Mode. . . . . . . . . . . . . . . . .  4
    Maximum Multiword DMA Mode. . . . . . . . . . . .  2
    Maximum UDMA Mode . . . . . . . . . . . . . . . .  150 MB/s (7)
    Active UDMA Mode. . . . . . . . . . . . . . . . .  150 MB/s (6)
    Minimum Multiword DMA Transfer Time . . . . . . .  120 ns
    Recommended Multiword DMA Transfer Time . . . . .  120 ns
    Minimum PIO Transfer Time Without IORDY . . . . .  120 ns
    Minimum PIO Transfer Time With IORDY. . . . . . .  120 ns
    ATA Control Byte. . . . . . . . . . . . . . . . .  Valid
    ATA Checksum Value. . . . . . . . . . . . . . . .  Valid

    Acoustic Management Configuration
    ---------------------------------
    Acoustic Management . . . . . . . . . . . . . . .  Supported
    Acoustic Management . . . . . . . . . . . . . . .  Enabled
    Current Acoustic Level. . . . . . . . . . . . . .  Min performance and volume (80h)
    Recommended Acoustic Level. . . . . . . . . . . .  Max performance and volume (FEh)

    EIDE Properties
    ---------------
    Read Ahead Buffer . . . . . . . . . . . . . . . .  Supported
    DMA . . . . . . . . . . . . . . . . . . . . . . .  Supported
    Ultra DMA . . . . . . . . . . . . . . . . . . . .  Supported
    S.M.A.R.T.. . . . . . . . . . . . . . . . . . . .  Supported
    Power Management. . . . . . . . . . . . . . . . .  Supported
    Write Cache . . . . . . . . . . . . . . . . . . .  Supported
    Host Protected Area . . . . . . . . . . . . . . .  Supported
    Advanced Power Management . . . . . . . . . . . .  Supported
    Power Up In Standby . . . . . . . . . . . . . . .  Not supported
    48-bit LBA Addressing . . . . . . . . . . . . . .  Supported
    Device Configuration Overlay. . . . . . . . . . .  Supported
    IORDY Support . . . . . . . . . . . . . . . . . .  Supported
    Read/Write DMA Queue. . . . . . . . . . . . . . .  Not supported
    NOP Command . . . . . . . . . . . . . . . . . . .  Supported
    Trusted Computing . . . . . . . . . . . . . . . .  Not supported
    64-bit World Wide ID. . . . . . . . . . . . . . .  F0500000143263A5
    Streaming . . . . . . . . . . . . . . . . . . . .  Not supported
    Media Card Pass Through . . . . . . . . . . . . .  Not supported
    General Purpose Logging . . . . . . . . . . . . .  Supported
    Error Logging . . . . . . . . . . . . . . . . . .  Supported
    CFA Feature Set . . . . . . . . . . . . . . . . .  Not supported
    Long Physical Sectors (1) . . . . . . . . . . . .  Not supported
    Long Logical Sectors. . . . . . . . . . . . . . .  Not supported
    Write-Read-Verify . . . . . . . . . . . . . . . .  Supported, Enabled
    NV Cache Feature. . . . . . . . . . . . . . . . .  Not supported
    NV Cache Power Mode . . . . . . . . . . . . . . .  Not supported
    NV Cache Size . . . . . . . . . . . . . . . . . .  Not supported
    Free-fall Control . . . . . . . . . . . . . . . .  Not supported
    Free-fall Control Sensitivity . . . . . . . . . .  Not supported

    SSD Features
    ------------
    Data Set Management . . . . . . . . . . . . . . .  Not supported
    TRIM Command. . . . . . . . . . . . . . . . . . .  Not supported
    Deterministic Read After TRIM . . . . . . . . . .  Not supported

    S.M.A.R.T. Details
    ------------------
    Off-line Data Collection Status . . . . . . . . .  Never Started
    Self Test Execution Status. . . . . . . . . . . .  Successfully Completed
    Total Time To Complete Off-line Data Collection .  54 seconds
    Execute Off-line Immediate. . . . . . . . . . . .  Supported
    Abort/restart Off-line By Host. . . . . . . . . .  Not supported
    Off-line Read Scanning. . . . . . . . . . . . . .  Supported
    Short Self-test . . . . . . . . . . . . . . . . .  Supported
    Extended Self-test. . . . . . . . . . . . . . . .  Supported
    Conveyance Self-test. . . . . . . . . . . . . . .  Not supported
    Selective Self-Test . . . . . . . . . . . . . . .  Supported
    Save Data Before/After Power Saving Mode. . . . .  Supported
    Enable/Disable Attribute Autosave . . . . . . . .  Supported
    Error Logging Capability. . . . . . . . . . . . .  Supported
    Short Self-test Estimated Time. . . . . . . . . .  2 minutes
    Extended Self-test Estimated Time . . . . . . . .  54 minutes

    Security Mode
    -------------
    Security Mode . . . . . . . . . . . . . . . . . .  Supported
    Security Erase. . . . . . . . . . . . . . . . . .  Supported
    Security Erase Time . . . . . . . . . . . . . . .  26 minutes
    Security Enhanced Erase Feature . . . . . . . . .  Supported
    Security Enhanced Erase Time. . . . . . . . . . .  26 minutes
    Security Enabled. . . . . . . . . . . . . . . . .  No
    Security Locked . . . . . . . . . . . . . . . . .  No
    Security Frozen . . . . . . . . . . . . . . . . .  No
    Security Counter Expired. . . . . . . . . . . . .  No
    Security Level. . . . . . . . . . . . . . . . . .  High

    Serial ATA Features
    -------------------
    S-ATA Compliance. . . . . . . . . . . . . . . . .  Yes
    S-ATA I Signaling Speed (1.5 Gps) . . . . . . . .  Supported
    S-ATA II Signaling Speed (3 Gps). . . . . . . . .  Not supported
    Receipt Of Power Management Requests From Host. .  Not supported
    PHY Event Counters. . . . . . . . . . . . . . . .  Supported
    Non-Zero Buffer Offsets In DMA Setup FIS. . . . .  Not supported
    DMA Setup Auto-Activate Optimization. . . . . . .  Supported, Disabled
    Device Initiating Interface Power Management. . .  Supported, Disabled
    In-Order Data Delivery. . . . . . . . . . . . . .  Not supported
    Asynchronous Notification . . . . . . . . . . . .  Not supported
    Software Settings Preservation. . . . . . . . . .  Supported, Enabled
    Native Command Queuing (NCQ). . . . . . . . . . .  Supported
    Queue Length. . . . . . . . . . . . . . . . . . .  32

    S.M.A.R.T.
    ----------
No.  Attribute                Thre.. Value  Worst  Data                Status                   Flags                                                  
1    Raw Read Error Rate      51     100    100    000000000000        OK                       Error-Rate, Performance, Statistical, Critical         
3    Spin Up Time             25     252    252    000000000791        OK                       Performance, Statistical, Critical                     
4    Start/Stop Count         0      100    100    00000000016F        OK (Always passing)      Self Preserving, Event Count, Statistical              
5    Reallocated Sectors Co.. 10     252    252    000000000000        OK                       Self Preserving, Event Count, Statistical, Critical    
9    Power-On Time Count      0      252    252    00000000004E        OK (Always passing)      Self Preserving, Event Count, Statistical              
12   Drive Power Cycle Count  0      100    100    00000000002C        OK (Always passing)      Self Preserving, Event Count, Statistical              
191  G-sense Error Rate       0      252    252    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              
192  Power off Retract Cycle  0      100    100    000000000002        OK (Always passing)      Self Preserving, Event Count, Statistical              
194  HDD Temperature          0      94     82     003400160030        OK (Always passing)      Self Preserving, Statistical                           
196  Reallocation Event Count 0      100    100    00000000123F        OK (Always passing)      Self Preserving, Event Count, Statistical              
197  Current Pending Sector.. 0      100    100    000000000037        OK (Always passing)      Event Count, Statistical                               
198  Off-Line Uncorrectable.. 0      100    100    0000000000DE        OK (Always passing)      Self Preserving, Event Count                           
199  Ultra ATA CRC Error Co.. 0      252    252    000000000000        OK (Always passing)      Self Preserving, Event Count, Performance, Statistical 
200  Write Error Rate         0      252    252    000000000000        OK (Always passing)      Error-Rate, Statistical        
```

No estoy seguro sobre como interpretar estos resultados y si estas pruebas sirven o son suficientes para saber si el disco de verdad falla o es uno de los falsos positivos. 
Si no fueran suficientes les pido que me digan que otras pruebas puedo realizar para saber si es un falso positivo o no.

Edito: hice la tarea y lei el manual de smartctl ([http://smartmontools.sourceforge.net/man/smartctl.8.html](http://smartmontools.sourceforge.net/man/smartctl.8.html)).
Segun entendi hay un problema cuando el valor normalizado (VALUE) es menor o igual al umbral por lo cual estaria todo bien. Al principio (antes de leer el man) pense que los umbrales eran maximos y no minimos por lo cual estaba preocupadisimo.

¿Entendi bien? ¿Estoy en lo cierto y puedo quedarme tranquilo o tengo que hacer mas cosas?

Muchas gracias :p

---

### Post by guillermolisi on 2010-03-26
Las dos pruebas que hiciste por tu cuenta me parecen definitorias por encima de Palimpsest.
Fijate con "dmesg" en consola/terminal (sin las comillas) si tenes entradas referidas a fallos en el disco, como para completar el trabajo que te tomaste.

---

### Post by Air23 on 2010-03-26
Esta es la salida de "dmesg"
```
[    0.403115] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.403118] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.403120] system 00:0c: iomem range 0x100000-0x7d8bf3ff could not be reserved
[    0.403123] system 00:0c: iomem range 0x7d8bf400-0x7dafffff could not be reserved
[    0.403126] system 00:0c: iomem range 0x7db00000-0x7dbfffff has been reserved
[    0.403129] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
[    0.403132] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.403135] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.403138] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.403141] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.403144] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.403147] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.403150] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.403152] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.403155] system 00:0c: iomem range 0xfed1c800-0xfed1cfff has been reserved
[    0.403158] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.403161] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.437830] AppArmor: AppArmor Filesystem Enabled
[    0.437899] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:0b
[    0.437901] pci 0000:00:1c.0:   IO window: disabled
[    0.437907] pci 0000:00:1c.0:   MEM window: disabled
[    0.437912] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.437917] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0c
[    0.437919] pci 0000:00:1c.1:   IO window: disabled
[    0.437925] pci 0000:00:1c.1:   MEM window: 0xf6900000-0xf69fffff
[    0.437930] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.437935] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:09
[    0.437939] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    0.437946] pci 0000:00:1c.2:   MEM window: 0xf6800000-0xf68fffff
[    0.437951] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.437956] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.437959] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.437966] pci 0000:00:1c.4:   MEM window: 0xf6600000-0xf67fffff
[    0.437971] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.437980] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.437982] pci 0000:00:1e.0:   IO window: disabled
[    0.437988] pci 0000:00:1e.0:   MEM window: disabled
[    0.437992] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.438009]   alloc irq_desc for 16 on node -1
[    0.438011]   alloc kstat_irqs on node -1
[    0.438016] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.438023] pci 0000:00:1c.0: setting latency timer to 64
[    0.438032]   alloc irq_desc for 17 on node -1
[    0.438033]   alloc kstat_irqs on node -1
[    0.438037] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.438042] pci 0000:00:1c.1: setting latency timer to 64
[    0.438051]   alloc irq_desc for 18 on node -1
[    0.438052]   alloc kstat_irqs on node -1
[    0.438056] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.438061] pci 0000:00:1c.2: setting latency timer to 64
[    0.438070] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.438076] pci 0000:00:1c.4: setting latency timer to 64
[    0.438084] pci 0000:00:1e.0: setting latency timer to 64
[    0.438089] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.438092] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.438094] pci_bus 0000:0c: resource 1 mem: [0xf6900000-0xf69fffff]
[    0.438097] pci_bus 0000:09: resource 0 io:  [0xd000-0xdfff]
[    0.438100] pci_bus 0000:09: resource 1 mem: [0xf6800000-0xf68fffff]
[    0.438102] pci_bus 0000:0d: resource 0 io:  [0xc000-0xcfff]
[    0.438105] pci_bus 0000:0d: resource 1 mem: [0xf6600000-0xf67fffff]
[    0.438108] pci_bus 0000:0d: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.438110] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.438113] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.438148] NET: Registered protocol family 2
[    0.438239] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.438540] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.438977] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.439238] TCP: Hash tables configured (established 131072 bind 65536)
[    0.439241] TCP reno registered
[    0.439342] NET: Registered protocol family 1
[    0.439404] Trying to unpack rootfs image as initramfs...
[    0.501441] Switched to high resolution mode on CPU 1
[    0.503999] Switched to high resolution mode on CPU 0
[    0.627435] Freeing initrd memory: 7470k freed
[    0.631337] cpufreq-nforce2: No nForce2 chipset.
[    0.631364] Scanning for low memory corruption every 60 seconds
[    0.631462] audit: initializing netlink socket (disabled)
[    0.631478] type=2000 audit(1269624681.628:1): initialized
[    0.640168] highmem bounce pool size: 64 pages
[    0.640173] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.641608] VFS: Disk quotas dquot_6.5.2
[    0.641665] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.642188] fuse init (API version 7.12)
[    0.642265] msgmni has been set to 1706
[    0.642456] alg: No test for stdrng (krng)
[    0.642469] io scheduler noop registered
[    0.642471] io scheduler anticipatory registered
[    0.642473] io scheduler deadline registered
[    0.642514] io scheduler cfq registered (default)
[    0.642526] pci 0000:00:02.0: Boot video device
[    0.642810]   alloc irq_desc for 24 on node -1
[    0.642812]   alloc kstat_irqs on node -1
[    0.642824] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.642836] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.642995]   alloc irq_desc for 25 on node -1
[    0.642997]   alloc kstat_irqs on node -1
[    0.643006] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.643017] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.643180]   alloc irq_desc for 26 on node -1
[    0.643182]   alloc kstat_irqs on node -1
[    0.643191] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.643202] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.643357]   alloc irq_desc for 27 on node -1
[    0.643359]   alloc kstat_irqs on node -1
[    0.643368] pcieport-driver 0000:00:1c.4: irq 27 for MSI/MSI-X
[    0.643379] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.643482] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.643593] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.643743] ACPI: AC Adapter [AC] (on-line)
[    0.643815] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.644727] ACPI: Lid Switch [LID]
[    0.644772] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.644779] ACPI: Power Button [PBTN]
[    0.644821] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.644824] ACPI: Sleep Button [SBTN]
[    0.645527] ACPI: SSDT 7dac29cf 0023F (v01  PmRef   BspIst 00003000 INTL 20050624)
[    0.645995] ACPI: SSDT 7dac2de5 005C6 (v01  PmRef   BspCst 00003001 INTL 20050624)
[    0.646337] Monitor-Mwait will be used to enter C-1 state
[    0.646363] Monitor-Mwait will be used to enter C-2 state
[    0.646371] Marking TSC unstable due to TSC halts in idle
[    0.646384] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.646407] processor LNXCPU:00: registered as cooling_device0
[    0.646411] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.646837] ACPI: SSDT 7dac2c0e 001D7 (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.647165] ACPI: SSDT 7dac33ab 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.647592] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.647614] processor LNXCPU:01: registered as cooling_device1
[    0.647618] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.659852] thermal LNXTHERM:01: registered as thermal_zone0
[    0.659861] ACPI: Thermal Zone [THM] (60 C)
[    0.659927] isapnp: Scanning for PnP cards...
[    0.709085] ACPI: Battery Slot [BAT0] (battery absent)
[    1.013849] isapnp: No Plug & Play device found
[    1.014933] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.016248] brd: module loaded
[    1.016677] loop: module loaded
[    1.016746] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.016820] ahci 0000:00:1f.2: version 3.0
[    1.016836] ahci 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.016873]   alloc irq_desc for 28 on node -1
[    1.016875]   alloc kstat_irqs on node -1
[    1.016887] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    1.016937] ahci: SSS flag set, parallel bus scan disabled
[    1.016976] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.016979] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    1.016985] ahci 0000:00:1f.2: setting latency timer to 64
[    1.040084] scsi0 : ahci
[    1.040191] scsi1 : ahci
[    1.040249] scsi2 : ahci
[    1.040304] scsi3 : ahci
[    1.040358] scsi4 : ahci
[    1.040417] scsi5 : ahci
[    1.040814] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 28
[    1.040818] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 28
[    1.040820] ata3: DUMMY
[    1.040821] ata4: DUMMY
[    1.040824] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 28
[    1.040828] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 28
[    1.041723] Fixed MDIO Bus: probed
[    1.041756] PPP generic driver version 2.4.2
[    1.041859] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.041882]   alloc irq_desc for 22 on node -1
[    1.041884]   alloc kstat_irqs on node -1
[    1.041890] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.041908] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.041911] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.041941] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.045837] ehci_hcd 0000:00:1a.7: debug port 1
[    1.045844] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.045859] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.061014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.061093] usb usb1: configuration #1 chosen from 1 choice
[    1.061121] hub 1-0:1.0: USB hub found
[    1.061128] hub 1-0:1.0: 6 ports detected
[    1.061192]   alloc irq_desc for 20 on node -1
[    1.061194]   alloc kstat_irqs on node -1
[    1.061199] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.061209] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.061212] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.061244] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.065155] ehci_hcd 0000:00:1d.7: debug port 1
[    1.065162] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.065175] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.080017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.080073] usb usb2: configuration #1 chosen from 1 choice
[    1.080100] hub 2-0:1.0: USB hub found
[    1.080106] hub 2-0:1.0: 6 ports detected
[    1.080166] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.080184] uhci_hcd: USB Universal Host Controller Interface driver
[    1.080211] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.080219] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.080222] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.080252] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.080279] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    1.080354] usb usb3: configuration #1 chosen from 1 choice
[    1.080379] hub 3-0:1.0: USB hub found
[    1.080386] hub 3-0:1.0: 2 ports detected
[    1.080430]   alloc irq_desc for 21 on node -1
[    1.080432]   alloc kstat_irqs on node -1
[    1.080437] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.080443] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.080447] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.080474] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.080508] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    1.080584] usb usb4: configuration #1 chosen from 1 choice
[    1.080609] hub 4-0:1.0: USB hub found
[    1.080615] hub 4-0:1.0: 2 ports detected
[    1.080658] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.080665] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.080669] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.080700] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.080728] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
[    1.080803] usb usb5: configuration #1 chosen from 1 choice
[    1.080827] hub 5-0:1.0: USB hub found
[    1.080834] hub 5-0:1.0: 2 ports detected
[    1.080881] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.080887] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.080891] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.080920] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.080947] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    1.081034] usb usb6: configuration #1 chosen from 1 choice
[    1.081058] hub 6-0:1.0: USB hub found
[    1.081064] hub 6-0:1.0: 2 ports detected
[    1.081112] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.081118] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.081121] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.081151] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.081178] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    1.081250] usb usb7: configuration #1 chosen from 1 choice
[    1.081273] hub 7-0:1.0: USB hub found
[    1.081280] hub 7-0:1.0: 2 ports detected
[    1.081322] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.081329] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.081333] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.081362] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.081389] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.081459] usb usb8: configuration #1 chosen from 1 choice
[    1.081482] hub 8-0:1.0: USB hub found
[    1.081488] hub 8-0:1.0: 2 ports detected
[    1.081584] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.103423] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.119354] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.119360] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.119363] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.119365] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.119368] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.119422] mice: PS/2 mouse device common for all mice
[    1.119529] rtc_cmos 00:04: RTC can wake from S4
[    1.119560] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.119591] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.119694] device-mapper: uevent: version 1.0.3
[    1.120250] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.120340] device-mapper: multipath: version 1.1.0 loaded
[    1.120342] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.120460] EISA: Probing bus 0 at eisa.0
[    1.120466] Cannot allocate resource for EISA slot 1
[    1.120497] EISA: Detected 0 cards.
[    1.120643] cpuidle: using governor ladder
[    1.120733] cpuidle: using governor menu
[    1.121228] TCP cubic registered
[    1.121377] NET: Registered protocol family 10
[    1.121812] lo: Disabled Privacy Extensions
[    1.122138] NET: Registered protocol family 17
[    1.122155] Bluetooth: L2CAP ver 2.13
[    1.122157] Bluetooth: L2CAP socket layer initialized
[    1.122159] Bluetooth: SCO (Voice Link) ver 0.6
[    1.122161] Bluetooth: SCO socket layer initialized
[    1.122195] Bluetooth: RFCOMM TTY layer initialized
[    1.122198] Bluetooth: RFCOMM socket layer initialized
[    1.122200] Bluetooth: RFCOMM ver 1.11
[    1.122949] Using IPI No-Shortcut mode
[    1.123011] PM: Resume from disk failed.
[    1.123022] registered taskstats version 1
[    1.123127]   Magic number: 2:217:543
[    1.123224] rtc_cmos 00:04: setting system clock to 2010-03-26 17:31:22 UTC (1269624682)
[    1.123227] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.123228] EDD information not available.
[    1.150111] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.396068] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.400358] ata1.00: ATA-8: SAMSUNG HM160HI, HH100-15, max UDMA7
[    1.400361] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    1.400398] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    1.406396] ata1.00: configured for UDMA/133
[    1.421145] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HI  HH10 PQ: 0 ANSI: 5
[    1.421255] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.421291] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.421331] sd 0:0:0:0: [sda] Write Protect is off
[    1.421334] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.421354] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.421464]  sda: sda1 sda2 sda3 sda4 < sda5
[    1.554157] Clocksource tsc unstable (delta = -192963181 ns)
[    1.554165]  sda6 >
[    1.554471] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.583215] usb 1-5: configuration #1 chosen from 1 choice
[    1.696072] usb 1-6: new high speed USB device using ehci_hcd and address 3
[    1.903205] usb 1-6: configuration #1 chosen from 1 choice
[    2.144074] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.160660] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-L633C, DW10, max UDMA/100, ATAPI AN
[    2.160675] ata2.00: applying bridge limits
[    2.177962] ata2.00: configured for UDMA/100
[    2.193766] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L633C DW10 PQ: 0 ANSI: 5
[    2.199305] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.199307] Uniform CD-ROM driver Revision: 3.20
[    2.199382] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.199424] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.516065] ata5: SATA link down (SStatus 0 SControl 300)
[    2.852074] ata6: SATA link down (SStatus 0 SControl 300)
[    2.868098] Freeing unused kernel memory: 540k freed
[    2.868389] Write protecting the kernel text: 4580k
[    2.868441] Write protecting the kernel read-only data: 1840k
[    2.976824] Linux agpgart interface v0.103
[    2.979367] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    2.979775] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    2.983069] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    3.046849] [drm] Initialized drm 1.1.0 20060810
[    3.077775] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.077781] i915 0000:00:02.0: setting latency timer to 64
[    3.079088] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[    3.079092] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    3.079197]   alloc irq_desc for 29 on node -1
[    3.079200]   alloc kstat_irqs on node -1
[    3.079209] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    3.080365] sky2 driver version 1.23
[    3.080407] sky2 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.080422] sky2 0000:09:00.0: setting latency timer to 64
[    3.080448] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    3.080553]   alloc irq_desc for 30 on node -1
[    3.080555]   alloc kstat_irqs on node -1
[    3.080572] sky2 0000:09:00.0: irq 30 for MSI/MSI-X
[    3.081231] sky2 eth0: addr 00:23:ae:ea:19:d0
[    3.135138] Initializing USB Mass Storage driver...
[    3.184503] [drm] i2c_init DPDDC-D
[    3.189047] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.189187] usbcore: registered new interface driver usb-storage
[    3.189190] USB Mass Storage support registered.
[    3.189317] usb-storage: device found at 2
[    3.189319] usb-storage: waiting for device to settle before scanning
[    3.315466] [drm] fb0: inteldrmfb frame buffer device
[    3.328749] acpi device:3e: registered as cooling_device2
[    3.329431] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:3c/input/input5
[    3.329469] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    3.329532] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    3.329599] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:43/input/input6
[    3.329625] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    3.329647] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.728867] [drm] LVDS-8: set mode 1366x768 c
[    4.289533] Console: switching to colour frame buffer device 170x48
[    4.667687] PM: Starting manual resume from disk
[    4.667692] PM: Resume from partition 8:5
[    4.667694] PM: Checking hibernation image.
[    4.667909] PM: Resume from disk failed.
[    4.721429] EXT4-fs (sda3): barriers enabled
[    4.732833] kjournald2 starting: pid 419, dev sda3:8, commit interval 5 seconds
[    4.732946] EXT4-fs (sda3): delayed allocation enabled
[    4.732949] EXT4-fs: file extents enabled
[    4.733464] EXT4-fs: mballoc enabled
[    4.733480] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    5.342020] type=1505 audit(1269624686.717:2): operation="profile_load" pid=444 name=/usr/share/gdm/guest-session/Xsession
[    5.345440] type=1505 audit(1269624686.721:3): operation="profile_load" pid=445 name=/sbin/dhclient3
[    5.346130] type=1505 audit(1269624686.721:4): operation="profile_load" pid=445 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.346507] type=1505 audit(1269624686.721:5): operation="profile_load" pid=445 name=/usr/lib/connman/scripts/dhclient-script
[    5.406117] type=1505 audit(1269624686.780:6): operation="profile_load" pid=446 name=/usr/bin/evince
[    5.417317] type=1505 audit(1269624686.793:7): operation="profile_load" pid=446 name=/usr/bin/evince-previewer
[    5.423919] type=1505 audit(1269624686.797:8): operation="profile_load" pid=446 name=/usr/bin/evince-thumbnailer
[    5.461243] type=1505 audit(1269624686.837:9): operation="profile_load" pid=448 name=/usr/lib/cups/backend/cups-pdf
[    5.462048] type=1505 audit(1269624686.837:10): operation="profile_load" pid=448 name=/usr/sbin/cupsd
[    8.188363] usb-storage: device scan complete
[    8.190446] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    8.191015] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    8.195052] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   14.936182] udev: starting version 147
[   14.988526] Adding 2096440k swap on /dev/sda5.  Priority:-1 extents:1 across:2096440k 
[   15.023991] lib80211: common routines for IEEE802.11 drivers
[   15.023995] lib80211_crypt: registered algorithm 'NULL'
[   15.027401] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.027406] Disabling lock debugging due to kernel taint
[   15.041558] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.041572] wl 0000:0c:00.0: setting latency timer to 64
[   15.067417] Linux video capture interface: v2.00
[   15.070295] uvcvideo: Found UVC 1.00 device Integrated_Webcam_1.3M (0c45:63ee)
[   15.126163] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.133751] input: Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7
[   15.144966] usbcore: registered new interface driver uvcvideo
[   15.144969] USB Video Class driver (v0.1.0)
[   15.145419] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   15.171715] lp: driver loaded but no devices found
[   15.193403] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.229618] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.229645] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.231589] lib80211_crypt: registered algorithm 'TKIP'
[   15.232188] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   15.304569] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   15.313210] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.313284] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.370397] EXT4-fs (sda3): internal journal on sda3:8
[   15.607366] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input12
[   15.635396] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input13
[   15.716972] EXT4-fs (sda6): barriers enabled
[   15.717964] kjournald2 starting: pid 870, dev sda6:8, commit interval 5 seconds
[   15.718325] EXT4-fs (sda6): internal journal on sda6:8
[   15.718329] EXT4-fs (sda6): delayed allocation enabled
[   15.718331] EXT4-fs: file extents enabled
[   15.728058] EXT4-fs: mballoc enabled
[   15.728072] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   15.871226] __ratelimit: 3 callbacks suppressed
[   15.871229] type=1505 audit(1269635497.245:12): operation="profile_replace" pid=1009 name=/usr/share/gdm/guest-session/Xsession
[   15.873101] type=1505 audit(1269635497.249:13): operation="profile_replace" pid=1010 name=/sbin/dhclient3
[   15.873808] type=1505 audit(1269635497.249:14): operation="profile_replace" pid=1010 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.874187] type=1505 audit(1269635497.249:15): operation="profile_replace" pid=1010 name=/usr/lib/connman/scripts/dhclient-script
[   15.882035] type=1505 audit(1269635497.257:16): operation="profile_replace" pid=1011 name=/usr/bin/evince
[   15.894079] type=1505 audit(1269635497.269:17): operation="profile_replace" pid=1011 name=/usr/bin/evince-previewer
[   15.901096] type=1505 audit(1269635497.277:18): operation="profile_replace" pid=1011 name=/usr/bin/evince-thumbnailer
[   15.910768] type=1505 audit(1269635497.285:19): operation="profile_replace" pid=1014 name=/usr/lib/cups/backend/cups-pdf
[   15.911574] type=1505 audit(1269635497.285:20): operation="profile_replace" pid=1014 name=/usr/sbin/cupsd
[   15.914760] type=1505 audit(1269635497.289:21): operation="profile_replace" pid=1015 name=/usr/sbin/tcpdump
[   16.208918] sky2 eth0: enabling interface
[   16.209180] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.251210] ppdev: user-space parallel port driver
[   26.305019] eth1: no IPv6 routers present
[   60.676249] CE: hpet increasing min_delta_ns to 15000 nsec
[ 6823.268086] usb 2-3: new high speed USB device using ehci_hcd and address 2
[ 6823.402536] usb 2-3: configuration #1 chosen from 1 choice
[ 6823.408560] scsi7 : SCSI emulation for USB Mass Storage devices
[ 6823.417583] usb-storage: device found at 2
[ 6823.417587] usb-storage: waiting for device to settle before scanning
[ 6828.416256] usb-storage: device scan complete
[ 6828.416840] scsi 7:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 6828.417395] sd 7:0:0:0: Attached scsi generic sg3 type 0
[ 6829.836829] sd 7:0:0:0: [sdc] 3966976 512-byte logical blocks: (2.03 GB/1.89 GiB)
[ 6829.837573] sd 7:0:0:0: [sdc] Write Protect is off
[ 6829.837578] sd 7:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 6829.837582] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 6829.840197] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 6829.840205]  sdc: sdc1
[ 6829.892713] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 6829.892721] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by guillermolisi on 2010-03-26
No parece haber problemas registrados en el log sobre el disco pero si queres estar mas tranquilo usa la maquina y cada tanto echale una mirada a ese log para ver si registra algun evento sobre el HD.

Otro indicio es que si tenes sectores con defectos en algun momento la maquina se plancha, cambia notoriamente su respuesta, porque esta intentando recuperar una lectura/grabacion defectuosa. Si esto no sucede, siempre responde parejo, no deberia haber fallos registrados en dmesg y con eso podrias dormir tranquilo por un buen rato.

Igual tenes varios mese por delante para que se venza la garantia.

---

### Post by Air23 on 2010-03-26
Me quedo tranquilo entonces :p

¡Muchisimas gracias Guillermo!

---

### Post by Mister X on 2010-03-31
El SMART te muestra la cuenta de sectores defectuosos:
```
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       55
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       361
```

El sentinel tambien:

```
    Power On Time . . . . . . . . . . . . . . . . . .  3 days, 6 hours
    Estimated Remaining Lifetime. . . . . . . . . . .  35 days
    Health. . . . . . . . . . . . . . . . . . . . . .  ##------------------ 14 % (Poor)
    Performance . . . . . . . . . . . . . . . . . . .  #################### 100 % (Excellent)

    The drive found 222 bad sectors during its self test.
    Based on the number of remapping operations, the health of the disk was decreased in different steps.
    There are 55 weak sectors found on the disk surface. They may be remapped any time in the later use of the disk.
      It is recommended to backup often to prevent data loss.

```

---

