---
title: "Adaptec RAID 5 -&gt; Rejecting I/O to offline device"
date: 2015-01-21
forum: Hardware
---

### Post by michalczech on 2015-01-21
Hi, 

I have server IBM 7979 with Adaptec raid controller, and it hangs regularly with message 
```
Rejecting I/O to offline device
```

Ubuntu 14.04.1
```

root@beehive:~# uname -a
Linux beehive 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

HDD from WD Red Series ( with TLER support )

Raid Configuration 
```
root@beehive:~# arcconf getconfig 1
Controllers found: 1
----------------------------------------------------------------------
Controller information
----------------------------------------------------------------------
   Controller Status                        : Optimal
   Channel description                      : SAS/SATA
   Controller Model                         : IBM ServeRAID 8k    
   Controller Serial Number                 : 4063ECC
   Controller World Wide Name               : 5005076B04063ECC
   Physical Slot                            : 0
   Installed memory                         : 256 MB
   Copyback                                 : Disabled
   Background consistency check             : Enabled
   Background consistency check period      : 30
   Automatic Failover                       : Enabled
   Host bus type                            : unknown
   Host bus speed                           : 0 MHz
   Host bus link width                      : 0 bit(s)/link(s)
   Stayawake period                         : Disabled
   Spinup limit internal drives             : 0
   Spinup limit external drives             : 0
   Defunct disk drive count                 : 0
   Logical devices/Failed/Degraded          : 1/0/0
   --------------------------------------------------------
   Controller Version Information
   --------------------------------------------------------
   BIOS                                     : 5.2-0 (16002)
   Firmware                                 : 5.2-0 (16002)
   Driver                                   : 1.2-0 (30200)
   Boot Flash                               : 5.1-0 (15411)
   --------------------------------------------------------
   Controller Battery Information
   --------------------------------------------------------
   Status                                   : Optimal
   Over temperature                         : No
   Capacity remaining                       : 100 percent
   Time remaining (at current draw)         : 5 days, 12 hours, 0 minutes

----------------------------------------------------------------------
Logical device information
----------------------------------------------------------------------
Logical device number 0
   Logical device name                      : WDARRAY
   Block Size of member drives              : Unknown
   RAID level                               : 5
   Unique Identifier                        : DE172470
   Status of logical device                 : Optimal
   Size                                     : 366233088 MB
   Parity space                             : 0 MB
   Stripe-unit size                         : 512 KB
   Read-cache setting                       : Enabled
   Read-cache status                        : On
   Write-cache setting                      : On when protected by battery/ZMM
   Write-cache status                       : On
   Partitioned                              : Yes
   Protected by Hot-Spare                   : No
   Bootable                                 : Yes
   Failed stripes                           : No
   Power settings                           : Disabled
   --------------------------------------------------------
   Logical device segment information
   --------------------------------------------------------
   Segment 0                                : Present (Controller:1,Enclosure:0,Slot:2)      WD-WXM1E74FEWAF
   Segment 1                                : Present (Controller:1,Enclosure:0,Slot:4)      WD-WXM1E74KMXLZ
   Segment 2                                : Present (Controller:1,Enclosure:0,Slot:7)      WD-WXM1E74HZ8VX


----------------------------------------------------------------------
Physical Device information
----------------------------------------------------------------------
      Device #0
         Device is a Hard drive
         State                              : Online
         Block Size                         : Unknown
         Supported                          : Yes
         Transfer Speed                     : SATA 3.0 Gb/s
         Reported Channel,Device(T:L)       : 0,2(2:0)
         Reported Location                  : Enclosure 0, Slot 2
         Reported ESD(T:L)                  : 2,0(0:0)
         Vendor                             : WDC
         Model                              : WD7500BFCX-68N6G
         Firmware                           : 82.00A82
         Serial number                      : WD-WXM1E74FEWAF
         Reserved Size                      : 7877158 KB
         Used Size                          : 0 MB
         Unused Size                        : 45547668 MB
         Total Size                         : 45555361 MB
         Write Cache                        : Disabled (write-through)
         FRU                                : None
         S.M.A.R.T.                         : No
         S.M.A.R.T. warnings                : 0
         SSD                                : No
         NCQ status                         : Disabled
      Device #1
         Device is a Hard drive
         State                              : Online
         Block Size                         : Unknown
         Supported                          : Yes
         Transfer Speed                     : SATA 3.0 Gb/s
         Reported Channel,Device(T:L)       : 0,4(4:0)
         Reported Location                  : Enclosure 0, Slot 4
         Reported ESD(T:L)                  : 2,0(0:0)
         Vendor                             : WDC
         Model                              : WD7500BFCX-68N6G
         Firmware                           : 82.00A82
         Serial number                      : WD-WXM1E74KMXLZ
         Reserved Size                      : 7877158 KB
         Used Size                          : 0 MB
         Unused Size                        : 45547668 MB
         Total Size                         : 45555361 MB
         Write Cache                        : Disabled (write-through)
         FRU                                : None
         S.M.A.R.T.                         : No
         S.M.A.R.T. warnings                : 0
         SSD                                : No
         NCQ status                         : Disabled
      Device #2
         Device is a Hard drive
         State                              : Online
         Block Size                         : Unknown
         Supported                          : Yes
         Transfer Speed                     : SATA 3.0 Gb/s
         Reported Channel,Device(T:L)       : 0,7(7:0)
         Reported Location                  : Enclosure 0, Slot 7
         Reported ESD(T:L)                  : 2,0(0:0)
         Vendor                             : WDC
         Model                              : WD7500BFCX-68N6G
         Firmware                           : 82.00A82
         Serial number                      : WD-WXM1E74HZ8VX
         Reserved Size                      : 7877158 KB
         Used Size                          : 0 MB
         Unused Size                        : 45547668 MB
         Total Size                         : 45555361 MB
         Write Cache                        : Disabled (write-through)
         FRU                                : None
         S.M.A.R.T.                         : No
         S.M.A.R.T. warnings                : 0
         SSD                                : No
         NCQ status                         : Disabled
      Device #3
         Device is an Enclosure services device
         Reported Channel,Device(T:L)       : 2,0(0:0)
         Enclosure ID                       : 0
         Expander ID                        : 0
         Enclosure Logical Identifier       : 5005076A04072860
         Type                               : SES2
         Vendor                             : IBM-ESXS
         Model                              : VSC7160
         Firmware                           : 1.07
         Status of Enclosure services device
            Speaker status                  : Not available



Command completed successfully.

```

```
root@beehive:~# arcconf getlogs 1 device
Controllers found: 1
<ControllerLog controllerID="0" type="0" time="1421846303" version="1" tableFull="false">
    <driveErrorEntry adapterID="0" channelID="0" deviceID="5" slotNum="5" enclIndex="0" numParityErrors="0" linkFailures="0" hwErrors="0" abortedCmds="12986" mediumErrors="0"/>
    <driveErrorEntry adapterID="0" channelID="0" deviceID="6" slotNum="6" enclIndex="0" numParityErrors="0" linkFailures="0" hwErrors="0" abortedCmds="12984" mediumErrors="0"/>
    <driveErrorEntry adapterID="0" channelID="2" deviceID="0" slotNum="0" enclIndex="0" numParityErrors="0" linkFailures="47" hwErrors="0" abortedCmds="0" mediumErrors="0"/>
    <driveErrorEntry adapterID="0" channelID="0" deviceID="7" slotNum="7" enclIndex="0" numParityErrors="0" linkFailures="107" hwErrors="0" abortedCmds="1" mediumErrors="2"/>
    <driveErrorEntry adapterID="0" channelID="0" deviceID="3" slotNum="3" enclIndex="0" numParityErrors="0" linkFailures="0" hwErrors="0" abortedCmds="4707" mediumErrors="0"/>
</ControllerLog>


Command completed successfully.

```


```
root@beehive:~# arcconf getlogs 1 event
Controllers found: 1
<ControllerLog controllerID="0" type="6" time="1421846370">
    <eventlog>
        <event Date="1421837567" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="28 00 06 9d a0 00 00 04 00 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="7"/>
        <event Date="1421837587" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="2a 00 18 e0 00 8f 00 00 08 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="4"/>
        <event Date="1421837592" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="28 00 04 2b 83 c7 00 00 08 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="2"/>
        <event Date="1421842574" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="28 00 18 df e1 47 00 00 10 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="4"/>
        <event Date="1421843053" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="28 00 0a a0 00 00 00 04 00 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="7"/>
        <event Date="1421843081" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="28 00 2a 24 18 00 00 04 00 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="2"/>
        <event Date="1421843081" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="2a 00 28 ac 0a 13 00 00 08 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="4"/>
        <event Date="1421843085" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="1c 01 02 00 2c 00 00 00 00 00 00 00" lun="0" controllerID="0" channelID="2" deviceID="0"/>
        <event Date="1421843121" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="1c 01 02 00 2c 00 00 00 00 00 00 00" lun="0" controllerID="0" channelID="2" deviceID="0"/>
        <event Date="1421843122" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_SENSE_DATA" subTypeCode="12" cdb="1c 01 02 00 2c 00 00 00 00 00 00 00" data="70 00 06 00 00 00 00 00 00 00 00 00 29 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00" lun="0" controllerID="0" channelID="2" deviceID="0"/>
        <event Date="1421843053" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_SENSE_DATA" subTypeCode="12" cdb="a0 00 00 00 00 00 00 00 10 08 00 00" data="70 00 05 00 00 00 00 00 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00" lun="0" controllerID="0" channelID="2" deviceID="0"/>
        <event Date="1421843058" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_CONTAINER_GROUP" groupCode="3" priority="3" subType="FSA_EXE_CT_PPI_UPDATE" subTypeCode="3" age="1191" controllerID="0"/>
        <event Date="1421843058" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_CONTAINER_GROUP" groupCode="3" priority="3" subType="FSA_EXE_CT_PPI_UPDATE" subTypeCode="3" age="1192" controllerID="0"/>
        <event Date="1421843067" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_CONTAINER_GROUP" groupCode="3" priority="3" subType="FSA_EXE_CT_PPI_UPDATE" subTypeCode="3" age="1193" controllerID="0"/>
        <event Date="1421843079" eventType="FSA_EM_BATTERY_CHANGE" eventCode="0x4000" batteryEventType="FSA_BATTERY_LOW_DEGRADING" batteryEventCode="3" priorState="0" currentState="2" controllerID="0"/>
        <event Date="1421843081" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="51207" status_bits="15" temperature="3050" current="0" designCapacity="0" fullCapacity="1980" remainingCapacity="1980" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="3060" voltage="4120" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421843426" eventType="FSA_EM_BATTERY_CHANGE" eventCode="0x4000" batteryEventType="FSA_BATTERY_GOOD" batteryEventCode="4" priorState="2" currentState="3" controllerID="0"/>
        <event Date="1421843426" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="1" status_bits="15" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="0" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421843454" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="32768" status_bits="0" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="4140" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421843826" eventType="FSA_EM_EXPANDED_EVENT" eventCode="0x10000000" groupType="FSA_EXE_SCSI_GROUP" groupCode="2" priority="3" subType="FSA_EXE_SCSI_COMMAND_TIMEOUT" subTypeCode="13" cdb="28 00 26 fe 3c 5b 00 01 00 00 00 00" lun="0" controllerID="0" channelID="0" deviceID="2"/>
        <event Date="1421843828" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="2" status_bits="0" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="2018" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="0" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421843925" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="1" status_bits="11" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="0" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421843927" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="2" status_bits="0" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="1980" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="0" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421843930" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="32768" status_bits="0" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="4100" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421845486" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="2048" status_bits="0" temperature="3040" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="0" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421845986" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="32768" status_bits="0" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="4080" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421846041" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="32768" status_bits="0" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="4100" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
        <event Date="1421846178" eventType="FSA_EM_ENHANCED_BATTERY_CHANGE" eventCode="0x8000000" capabilities_bits="0" event_bits="32768" status_bits="0" temperature="0" current="0" designCapacity="0" fullCapacity="0" remainingCapacity="0" DramCurrentDraw="0" nextReconDate="0" lastReconDate="0" tabStatusRegisterBits="0" tabControlRegisterBits="0" rombStatusRegisterBits="0" rombControlRegisterBits="0" max_temperature="0" voltage="4080" batSubSysColdStartedDays="0" batSubSysColdStartedHours="0" batSubSysColdStartedMinutes="0" batSubSysColdStartedSeconds="0" controllerID="0"/>
    </eventlog>
</ControllerLog>

```


Anybody have idea why this happen ?

Raid work under high stress ( few virtal machines )

---

