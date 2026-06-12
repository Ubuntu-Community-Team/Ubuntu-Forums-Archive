---
title: "Diagnosing SAS/SATA errors"
date: 2014-11-06
forum: Hardware
---

### Post by MakOwner on 2014-11-06
I apologize for the wall of text, but I _really_ need help identifying where this error originates.  
I have a number of these that are running without issue, but I have been having problems with two of them.
This is day three of the burn - in on the last two I RMA'd.  I have RMA'd this pair twice already, and I think the vendor is starting to think I'm crazy...

This is a 16 drive external enclosure with a SAS expander in it with SATA drives installed.  
The first error happens and the whole array goes offline very quickly - so quickly I can reboot and none of the array devices are still current and the reboot usually mounts everything cleanly.

Is this error really coming from the SAS expander, a disk attached to the expander, or a driver issue between the SAS expander and the controller?
Not much I can do about hat last one - these are used out-of-support shelves, on out of support dell hardware..




```

[162435.404405]  end_device-4:0:0: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 66, phy 0,sas_addr 0x50019400008e6200
[162435.404414]  phy-4:0:8: mptsas: ioc0: delete phy 0, phy-obj (0xffff880036b21000)
[162435.404434]  port-4:0:0: mptsas: ioc0: delete port 0, sas_addr (0x50019400008e6200)
[162435.408723] sd 4:0:0:0: [sdc] Synchronizing SCSI cache
[162435.408782] sd 4:0:0:0: [sdc]  
[162435.408787] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.408879] scsi target4:0:0: mptsas: ioc0: delete device: fw_channel 0, fw_id 66, phy 0, sas_addr 0x50019400008e6200
[162435.409117]  end_device-4:0:1: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 67, phy 1,sas_addr 0x50019400008e6201
[162435.409121]  phy-4:0:9: mptsas: ioc0: delete phy 1, phy-obj (0xffff880036b22000)
[162435.409128]  port-4:0:1: mptsas: ioc0: delete port 1, sas_addr (0x50019400008e6201)
[162435.409618] sd 4:0:1:0: [sdd] Synchronizing SCSI cache
[162435.409658] sd 4:0:1:0: [sdd]  
[162435.409662] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.409720] scsi target4:0:1: mptsas: ioc0: delete device: fw_channel 0, fw_id 67, phy 1, sas_addr 0x50019400008e6201
[162435.409917]  end_device-4:0:2: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 68, phy 2,sas_addr 0x50019400008e6202
[162435.409921]  phy-4:0:10: mptsas: ioc0: delete phy 2, phy-obj (0xffff880036b23000)
[162435.409929]  port-4:0:2: mptsas: ioc0: delete port 2, sas_addr (0x50019400008e6202)
[162435.410380] sd 4:0:2:0: [sde] Synchronizing SCSI cache
[162435.410413] sd 4:0:2:0: [sde]  
[162435.410417] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.410479] scsi target4:0:2: mptsas: ioc0: delete device: fw_channel 0, fw_id 68, phy 2, sas_addr 0x50019400008e6202
[162435.410661]  end_device-4:0:3: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 69, phy 3,sas_addr 0x50019400008e6203
[162435.410666]  phy-4:0:11: mptsas: ioc0: delete phy 3, phy-obj (0xffff880036a0c000)
[162435.410673]  port-4:0:3: mptsas: ioc0: delete port 3, sas_addr (0x50019400008e6203)
[162435.412802] sd 4:0:3:0: [sdf] Synchronizing SCSI cache
[162435.412846] sd 4:0:3:0: [sdf]  
[162435.412850] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.412928] scsi target4:0:3: mptsas: ioc0: delete device: fw_channel 0, fw_id 69, phy 3, sas_addr 0x50019400008e6203
[162435.413122]  end_device-4:0:4: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 70, phy 4,sas_addr 0x50019400008e6204
[162435.413127]  phy-4:0:12: mptsas: ioc0: delete phy 4, phy-obj (0xffff880036a0d000)
[162435.413133]  port-4:0:4: mptsas: ioc0: delete port 4, sas_addr (0x50019400008e6204)
[162435.414580] sd 4:0:4:0: [sdg] Synchronizing SCSI cache
[162435.414623] sd 4:0:4:0: [sdg]  
[162435.414626] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.414696] scsi target4:0:4: mptsas: ioc0: delete device: fw_channel 0, fw_id 70, phy 4, sas_addr 0x50019400008e6204
[162435.414900]  end_device-4:0:5: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 71, phy 5,sas_addr 0x50019400008e6205
[162435.414904]  phy-4:0:13: mptsas: ioc0: delete phy 5, phy-obj (0xffff880036a0e000)
[162435.414910]  port-4:0:5: mptsas: ioc0: delete port 5, sas_addr (0x50019400008e6205)
[162435.417050] sd 4:0:5:0: [sdh] Synchronizing SCSI cache
[162435.417094] sd 4:0:5:0: [sdh]  
[162435.417098] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.417169] scsi target4:0:5: mptsas: ioc0: delete device: fw_channel 0, fw_id 71, phy 5, sas_addr 0x50019400008e6205
[162435.417359]  end_device-4:0:6: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 72, phy 6,sas_addr 0x50019400008e6206
[162435.417364]  phy-4:0:14: mptsas: ioc0: delete phy 6, phy-obj (0xffff880036a0f000)
[162435.417370]  port-4:0:6: mptsas: ioc0: delete port 6, sas_addr (0x50019400008e6206)
[162435.420807] sd 4:0:6:0: [sdi] Synchronizing SCSI cache
[162435.420851] sd 4:0:6:0: [sdi]  
[162435.420856] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.420930] scsi target4:0:6: mptsas: ioc0: delete device: fw_channel 0, fw_id 72, phy 6, sas_addr 0x50019400008e6206
[162435.421119]  end_device-4:0:7: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 73, phy 7,sas_addr 0x50019400008e6207
[162435.421124]  phy-4:0:15: mptsas: ioc0: delete phy 7, phy-obj (0xffff880036a80000)
[162435.421130]  port-4:0:7: mptsas: ioc0: delete port 7, sas_addr (0x50019400008e6207)
[162435.425572] sd 4:0:7:0: [sdj] Synchronizing SCSI cache
[162435.425615] sd 4:0:7:0: [sdj]  
[162435.425619] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.427597] scsi target4:0:7: mptsas: ioc0: delete device: fw_channel 0, fw_id 73, phy 7, sas_addr 0x50019400008e6207
[162435.427813]  end_device-4:0:8: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 74, phy 8,sas_addr 0x50019400008e6208
[162435.427817]  phy-4:0:16: mptsas: ioc0: delete phy 8, phy-obj (0xffff880036a81000)
[162435.427824]  port-4:0:8: mptsas: ioc0: delete port 8, sas_addr (0x50019400008e6208)
[162435.430188] sd 4:0:8:0: [sdk] Synchronizing SCSI cache
[162435.430534] sd 4:0:8:0: [sdk]  
[162435.430539] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.430617] scsi target4:0:8: mptsas: ioc0: delete device: fw_channel 0, fw_id 74, phy 8, sas_addr 0x50019400008e6208
[162435.430903]  end_device-4:0:9: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 75, phy 9,sas_addr 0x50019400008e6209
[162435.430908]  phy-4:0:17: mptsas: ioc0: delete phy 9, phy-obj (0xffff880036a82000)
[162435.430916]  port-4:0:9: mptsas: ioc0: delete port 9, sas_addr (0x50019400008e6209)
[162435.432836] sd 4:0:9:0: [sdl] Synchronizing SCSI cache
[162435.432879] sd 4:0:9:0: [sdl]  
[162435.432883] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.432957] scsi target4:0:9: mptsas: ioc0: delete device: fw_channel 0, fw_id 75, phy 9, sas_addr 0x50019400008e6209
[162435.433275]  end_device-4:0:10: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 76, phy 10,sas_addr 0x50019400008e620a
[162435.433280]  phy-4:0:18: mptsas: ioc0: delete phy 10, phy-obj (0xffff880036a83000)
[162435.433289]  port-4:0:10: mptsas: ioc0: delete port 10, sas_addr (0x50019400008e620a)
[162435.433557] md/raid:md2: Disk failure on sdc1, disabling device.
[162435.433557] md/raid:md2: Operation continuing on 11 devices.
[162435.434905] md: super_written gets error=-19, uptodate=0
[162435.434910] md/raid:md2: Disk failure on sdl1, disabling device.
[162435.434910] md/raid:md2: Operation continuing on 10 devices.
[162435.436285] md: super_written gets error=-19, uptodate=0
[162435.436289] md/raid:md2: Disk failure on sdj1, disabling device.
[162435.436289] md/raid:md2: Operation continuing on 9 devices.
[162435.436489] sd 4:0:10:0: [sdm] Synchronizing SCSI cache
[162435.436530] sd 4:0:10:0: [sdm]  
[162435.436532] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.436605] scsi target4:0:10: mptsas: ioc0: delete device: fw_channel 0, fw_id 76, phy 10, sas_addr 0x50019400008e620a
[162435.436789]  end_device-4:0:11: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 77, phy 11,sas_addr 0x50019400008e620b
[162435.436791]  phy-4:0:19: mptsas: ioc0: delete phy 11, phy-obj (0xffff880036b88000)
[162435.436796]  port-4:0:11: mptsas: ioc0: delete port 11, sas_addr (0x50019400008e620b)
[162435.437598] md: super_written gets error=-19, uptodate=0
[162435.437603] md/raid:md2: Disk failure on sdk1, disabling device.
[162435.437603] md/raid:md2: Operation continuing on 8 devices.
[162435.437793] sd 4:0:11:0: [sdn] Synchronizing SCSI cache
[162435.437829] sd 4:0:11:0: [sdn]  
[162435.437831] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[162435.437894] scsi target4:0:11: mptsas: ioc0: delete device: fw_channel 0, fw_id 77, phy 11, sas_addr 0x50019400008e620b
[162435.438197]  end_device-4:0:13: mptsas: ioc0: removing ssp device: fw_channel 0, fw_id 78, phy 24,sas_addr 0x50019400008e623e
[162435.438200]  phy-4:0:32: mptsas: ioc0: delete phy 24, phy-obj (0xffff880036b8f800)
[162435.438206]  port-4:0:13: mptsas: ioc0: delete port 13, sas_addr (0x50019400008e623e)
[162435.438737] scsi target4:0:12: mptsas: ioc0: delete device: fw_channel 0, fw_id 78, phy 24, sas_addr 0x50019400008e623e
[162435.438905] md: super_written gets error=-19, uptodate=0
[162435.438909] md/raid:md2: Disk failure on sdi1, disabling device.
[162435.438909] md/raid:md2: Operation continuing on 7 devices.
[162435.439946]  phy-4:4: mptsas: ioc0: delete phy 4, phy-obj (0xffff8800369a1400)
[162435.439952]  phy-4:5: mptsas: ioc0: delete phy 5, phy-obj (0xffff8800369a3800)
[162435.439957]  phy-4:6: mptsas: ioc0: delete phy 6, phy-obj (0xffff880036b20000)
[162435.439960]  phy-4:7: mptsas: ioc0: delete phy 7, phy-obj (0xffff880036b20800)
[162435.439964]  port-4:0: mptsas: ioc0: delete port 0, sas_addr (0x50019400008e623f)
[162435.440220] md: super_written gets error=-19, uptodate=0
[162435.440234] md/raid:md2: Disk failure on sdg1, disabling device.
[162435.440234] md/raid:md2: Operation continuing on 6 devices.
[162435.441523] md: super_written gets error=-19, uptodate=0
[162435.441527] md/raid:md2: Disk failure on sdf1, disabling device.
[162435.441527] md/raid:md2: Operation continuing on 5 devices.
[162435.442098] mptsas: ioc0: delete expander: num_phys 25, sas_addr (0x50019400008e623f)
[162435.442814] md: super_written gets error=-19, uptodate=0
[162435.442818] md/raid:md2: Disk failure on sdh1, disabling device.
[162435.442818] md/raid:md2: Operation continuing on 4 devices.
[162435.446821] md: super_written gets error=-19, uptodate=0
[162435.446831] md/raid:md2: Disk failure on sdd1, disabling device.
[162435.446831] md/raid:md2: Operation continuing on 3 devices.
[162435.448163] md: super_written gets error=-19, uptodate=0
[162435.448168] md/raid:md2: Disk failure on sde1, disabling device.
[162435.448168] md/raid:md2: Operation continuing on 2 devices.
[162435.449455] md: super_written gets error=-19, uptodate=0
[162435.449459] md/raid:md2: Disk failure on sdm1, disabling device.
[162435.449459] md/raid:md2: Operation continuing on 1 devices.
[162435.450744] md: super_written gets error=-19, uptodate=0
[162435.450748] md/raid:md2: Disk failure on sdn1, disabling device.
[162435.450748] md/raid:md2: Operation continuing on 0 devices.
[162435.452066] RAID conf printout:
[162435.452075]  --- level:6 rd:12 wd:0
[162435.452077]  disk 0, o:0, dev:sdm1
[162435.452080]  disk 1, o:0, dev:sdj1
[162435.452082]  disk 2, o:0, dev:sdn1
[162435.452085]  disk 3, o:0, dev:sdh1
[162435.452087]  disk 4, o:0, dev:sde1
[162435.452089]  disk 5, o:0, dev:sdg1
[162435.452092]  disk 6, o:0, dev:sdc1
[162435.452094]  disk 7, o:0, dev:sdi1
[162435.452096]  disk 8, o:0, dev:sdf1
[162435.452099]  disk 9, o:0, dev:sdl1
[162435.452101]  disk 10, o:0, dev:sdd1
[162435.452103]  disk 11, o:0, dev:sdk1
[162435.476510] RAID conf printout:
[162435.476519]  --- level:6 rd:12 wd:0
[162435.476523]  disk 0, o:0, dev:sdm1
[162435.476526]  disk 1, o:0, dev:sdj1
[162435.476529]  disk 2, o:0, dev:sdn1
[162435.476532]  disk 3, o:0, dev:sdh1
[162435.476534]  disk 4, o:0, dev:sde1
[162435.476537]  disk 5, o:0, dev:sdg1
[162435.476540]  disk 6, o:0, dev:sdc1
[162435.476542]  disk 7, o:0, dev:sdi1
[162435.476545]  disk 8, o:0, dev:sdf1
[162435.476547]  disk 10, o:0, dev:sdd1
[162435.476550]  disk 11, o:0, dev:sdk1
[162435.476559] RAID conf printout:
[162435.476561]  --- level:6 rd:12 wd:0
[162435.476564]  disk 0, o:0, dev:sdm1
[162435.476566]  disk 1, o:0, dev:sdj1
[162435.476568]  disk 2, o:0, dev:sdn1
[162435.476570]  disk 3, o:0, dev:sdh1
[162435.476572]  disk 4, o:0, dev:sde1
[162435.476574]  disk 5, o:0, dev:sdg1
[162435.476576]  disk 6, o:0, dev:sdc1
[162435.476578]  disk 7, o:0, dev:sdi1
[162435.476580]  disk 8, o:0, dev:sdf1
[162435.476582]  disk 10, o:0, dev:sdd1
[162435.476585]  disk 11, o:0, dev:sdk1
[162435.504099] RAID conf printout:
[162435.504109]  --- level:6 rd:12 wd:0
[162435.504114]  disk 0, o:0, dev:sdm1
[162435.504117]  disk 2, o:0, dev:sdn1
[162435.504120]  disk 3, o:0, dev:sdh1
[162435.504124]  disk 4, o:0, dev:sde1
[162435.504127]  disk 5, o:0, dev:sdg1
[162435.504130]  disk 6, o:0, dev:sdc1
[162435.504133]  disk 7, o:0, dev:sdi1
[162435.504136]  disk 8, o:0, dev:sdf1
[162435.504139]  disk 10, o:0, dev:sdd1
[162435.504142]  disk 11, o:0, dev:sdk1
[162435.504155] RAID conf printout:
[162435.504157]  --- level:6 rd:12 wd:0
[162435.504160]  disk 0, o:0, dev:sdm1
[162435.504162]  disk 2, o:0, dev:sdn1
[162435.504164]  disk 3, o:0, dev:sdh1
[162435.504166]  disk 4, o:0, dev:sde1
[162435.504168]  disk 5, o:0, dev:sdg1
[162435.504170]  disk 6, o:0, dev:sdc1
[162435.504172]  disk 7, o:0, dev:sdi1
[162435.504174]  disk 8, o:0, dev:sdf1
[162435.504176]  disk 10, o:0, dev:sdd1
[162435.504178]  disk 11, o:0, dev:sdk1
[162435.524019] RAID conf printout:
[162435.524024]  --- level:6 rd:12 wd:0
[162435.524027]  disk 0, o:0, dev:sdm1
[162435.524030]  disk 2, o:0, dev:sdn1
[162435.524033]  disk 3, o:0, dev:sdh1
[162435.524035]  disk 4, o:0, dev:sde1
[162435.524038]  disk 5, o:0, dev:sdg1
[162435.524041]  disk 6, o:0, dev:sdc1
[162435.524043]  disk 7, o:0, dev:sdi1
[162435.524046]  disk 8, o:0, dev:sdf1
[162435.524049]  disk 10, o:0, dev:sdd1
[162435.524054] RAID conf printout:
[162435.524056]  --- level:6 rd:12 wd:0
[162435.524059]  disk 0, o:0, dev:sdm1
[162435.524062]  disk 2, o:0, dev:sdn1
[162435.524065]  disk 3, o:0, dev:sdh1
[162435.524067]  disk 4, o:0, dev:sde1
[162435.524070]  disk 5, o:0, dev:sdg1
[162435.524073]  disk 6, o:0, dev:sdc1
[162435.524075]  disk 7, o:0, dev:sdi1
[162435.524078]  disk 8, o:0, dev:sdf1
[162435.524081]  disk 10, o:0, dev:sdd1
[162435.528028] RAID conf printout:
[162435.528032]  --- level:6 rd:12 wd:0
[162435.528035]  disk 0, o:0, dev:sdm1
[162435.528038]  disk 2, o:0, dev:sdn1
[162435.528041]  disk 3, o:0, dev:sdh1
[162435.528044]  disk 4, o:0, dev:sde1
[162435.528046]  disk 5, o:0, dev:sdg1
[162435.528049]  disk 6, o:0, dev:sdc1
[162435.528052]  disk 8, o:0, dev:sdf1
[162435.528055]  disk 10, o:0, dev:sdd1
[162435.528059] RAID conf printout:
[162435.528062]  --- level:6 rd:12 wd:0
[162435.528065]  disk 0, o:0, dev:sdm1
[162435.528068]  disk 2, o:0, dev:sdn1
[162435.528070]  disk 3, o:0, dev:sdh1
[162435.528073]  disk 4, o:0, dev:sde1
[162435.528076]  disk 5, o:0, dev:sdg1
[162435.528078]  disk 6, o:0, dev:sdc1
[162435.528081]  disk 8, o:0, dev:sdf1
[162435.528084]  disk 10, o:0, dev:sdd1
[162435.532027] RAID conf printout:
[162435.532032]  --- level:6 rd:12 wd:0
[162435.532035]  disk 0, o:0, dev:sdm1
[162435.532037]  disk 2, o:0, dev:sdn1
[162435.532040]  disk 3, o:0, dev:sdh1
[162435.532043]  disk 4, o:0, dev:sde1
[162435.532045]  disk 6, o:0, dev:sdc1
[162435.532048]  disk 8, o:0, dev:sdf1
[162435.532051]  disk 10, o:0, dev:sdd1
[162435.532055] RAID conf printout:
[162435.532058]  --- level:6 rd:12 wd:0
[162435.532061]  disk 0, o:0, dev:sdm1
[162435.532063]  disk 2, o:0, dev:sdn1
[162435.532066]  disk 3, o:0, dev:sdh1
[162435.532069]  disk 4, o:0, dev:sde1
[162435.532072]  disk 6, o:0, dev:sdc1
[162435.532074]  disk 8, o:0, dev:sdf1
[162435.532077]  disk 10, o:0, dev:sdd1
[162435.536028] RAID conf printout:
[162435.536032]  --- level:6 rd:12 wd:0
[162435.536036]  disk 0, o:0, dev:sdm1
[162435.536039]  disk 2, o:0, dev:sdn1
[162435.536041]  disk 3, o:0, dev:sdh1
[162435.536044]  disk 4, o:0, dev:sde1
[162435.536047]  disk 6, o:0, dev:sdc1
[162435.536050]  disk 10, o:0, dev:sdd1
[162435.536055] RAID conf printout:
[162435.536058]  --- level:6 rd:12 wd:0
[162435.536060]  disk 0, o:0, dev:sdm1
[162435.536063]  disk 2, o:0, dev:sdn1
[162435.536066]  disk 3, o:0, dev:sdh1
[162435.536069]  disk 4, o:0, dev:sde1
[162435.536071]  disk 6, o:0, dev:sdc1
[162435.536074]  disk 10, o:0, dev:sdd1
[162435.540028] RAID conf printout:
[162435.540032]  --- level:6 rd:12 wd:0
[162435.540035]  disk 0, o:0, dev:sdm1
[162435.540038]  disk 2, o:0, dev:sdn1
[162435.540041]  disk 4, o:0, dev:sde1
[162435.540043]  disk 6, o:0, dev:sdc1
[162435.540046]  disk 10, o:0, dev:sdd1
[162435.540051] RAID conf printout:
[162435.540053]  --- level:6 rd:12 wd:0
[162435.540056]  disk 0, o:0, dev:sdm1
[162435.540059]  disk 2, o:0, dev:sdn1
[162435.540061]  disk 4, o:0, dev:sde1
[162435.540064]  disk 6, o:0, dev:sdc1
[162435.540067]  disk 10, o:0, dev:sdd1
[162435.544027] RAID conf printout:
[162435.544032]  --- level:6 rd:12 wd:0
[162435.544035]  disk 0, o:0, dev:sdm1
[162435.544038]  disk 2, o:0, dev:sdn1
[162435.544040]  disk 4, o:0, dev:sde1
[162435.544043]  disk 6, o:0, dev:sdc1
[162435.544048] RAID conf printout:
[162435.544051]  --- level:6 rd:12 wd:0
[162435.544053]  disk 0, o:0, dev:sdm1
[162435.544056]  disk 2, o:0, dev:sdn1
[162435.544059]  disk 4, o:0, dev:sde1
[162435.544061]  disk 6, o:0, dev:sdc1
[162435.548027] RAID conf printout:
[162435.548031]  --- level:6 rd:12 wd:0
[162435.548034]  disk 0, o:0, dev:sdm1
[162435.548037]  disk 2, o:0, dev:sdn1
[162435.548040]  disk 4, o:0, dev:sde1
[162435.548045] RAID conf printout:
[162435.548047]  --- level:6 rd:12 wd:0
[162435.548050]  disk 0, o:0, dev:sdm1
[162435.548052]  disk 2, o:0, dev:sdn1
[162435.548055]  disk 4, o:0, dev:sde1
[162435.556025] RAID conf printout:
[162435.556029]  --- level:6 rd:12 wd:0
[162435.556032]  disk 0, o:0, dev:sdm1
[162435.556035]  disk 2, o:0, dev:sdn1
[162435.556040] RAID conf printout:
[162435.556043]  --- level:6 rd:12 wd:0
[162435.556045]  disk 0, o:0, dev:sdm1
[162435.556048]  disk 2, o:0, dev:sdn1
[162435.560032] RAID conf printout:
[162435.560036]  --- level:6 rd:12 wd:0
[162435.560039]  disk 2, o:0, dev:sdn1
[162435.560044] RAID conf printout:
[162435.560047]  --- level:6 rd:12 wd:0
[162435.560049]  disk 2, o:0, dev:sdn1
[162435.564032] RAID conf printout:
[162435.564037]  --- level:6 rd:12 wd:0
[162435.564396] md: unbind<sdc1>
[162435.580080] md: export_rdev(sdc1)
[162435.587324] md: unbind<sdd1>
[162435.612135] md: export_rdev(sdd1)
[162435.612530] md: unbind<sde1>
[162435.632098] md: export_rdev(sde1)
[162435.634364] md: unbind<sdn1>
[162435.652105] md: export_rdev(sdn1)
[162435.652572] md: unbind<sdg1>
[162435.668076] md: export_rdev(sdg1)
[162435.668466] md: unbind<sdi1>
[162435.692066] md: export_rdev(sdi1)
[162435.692790] md: unbind<sdh1>
[162435.712085] md: export_rdev(sdh1)
[162435.712270] md: unbind<sdl1>
[162435.736094] md: export_rdev(sdl1)
[162435.736246] md: unbind<sdm1>
[162435.756093] md: export_rdev(sdm1)
[162435.756589] md: unbind<sdf1>
[162435.776107] md: export_rdev(sdf1)
[162435.776371] md: unbind<sdj1>
[162435.796125] md: export_rdev(sdj1)
[162435.796252] md: unbind<sdk1>
[162435.820077] md: export_rdev(sdk1)
[162444.104289] mptsas: ioc0: add expander: num_phys 25, sas_addr (0x50019400008e623f)
[162444.333645] mptsas: ioc0: attaching ssp device: fw_channel 0, fw_id 78, phy 24, sas_addr 0x50019400008e623e
[162444.339103] scsi 4:0:13:0: Enclosure         RACKABLE SE3016-SAS       0227 PQ: 0 ANSI: 5
[162444.346523] ses 4:0:13:0: Attached Enclosure device
[162444.346630] ses 4:0:13:0: Attached scsi generic sg3 type 13
[162449.753209] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 66, phy 0, sas_addr 0x50019400008e6200
[162449.755111] scsi 4:0:14:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162449.755862] sd 4:0:14:0: Attached scsi generic sg4 type 0
[162449.757519] sd 4:0:14:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162449.801852] sd 4:0:14:0: [sdc] Write Protect is off
[162449.801862] sd 4:0:14:0: [sdc] Mode Sense: 73 00 00 08
[162449.804440] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 67, phy 1, sas_addr 0x50019400008e6201
[162449.804752] sd 4:0:14:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162449.806429] scsi 4:0:15:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162449.807249] sd 4:0:15:0: Attached scsi generic sg5 type 0
[162449.810148] sd 4:0:15:0: [sdd] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162449.851334] sd 4:0:15:0: [sdd] Write Protect is off
[162449.851343] sd 4:0:15:0: [sdd] Mode Sense: 73 00 00 08
[162449.853904] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 70, phy 4, sas_addr 0x50019400008e6204
[162449.854214] sd 4:0:15:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162449.856321] scsi 4:0:16:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162449.857635] sd 4:0:16:0: Attached scsi generic sg6 type 0
[162449.858650] sd 4:0:16:0: [sde] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162449.892412]  sdc: sdc1
[162449.902044] sd 4:0:16:0: [sde] Write Protect is off
[162449.902052] sd 4:0:16:0: [sde] Mode Sense: 73 00 00 08
[162449.904621] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 71, phy 5, sas_addr 0x50019400008e6205
[162449.904856] sd 4:0:16:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162449.906531] scsi 4:0:17:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162449.907410] sd 4:0:17:0: Attached scsi generic sg7 type 0
[162449.909418] sd 4:0:17:0: [sdf] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162449.918155]  sdd: sdd1
[162449.943352] sd 4:0:17:0: [sdf] Write Protect is off
[162449.943361] sd 4:0:17:0: [sdf] Mode Sense: 73 00 00 08
[162449.946198] sd 4:0:17:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162449.976693]  sde: sde1
[162450.009661]  sdf: sdf1
[162450.017017] sd 4:0:14:0: [sdc] Attached SCSI disk
[162450.059838] sd 4:0:15:0: [sdd] Attached SCSI disk
[162450.119912] sd 4:0:16:0: [sde] Attached SCSI disk
[162450.145235] sd 4:0:17:0: [sdf] Attached SCSI disk
[162453.672321] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 68, phy 2, sas_addr 0x50019400008e6202
[162453.745491] scsi 4:0:18:0: Direct-Access     ATA      Hitachi HUA72107 AB0A PQ: 0 ANSI: 5
[162453.746199] sd 4:0:18:0: Attached scsi generic sg8 type 0
[162453.747842] sd 4:0:18:0: [sdg] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162453.920505] sd 4:0:18:0: [sdg] Write Protect is off
[162453.920513] sd 4:0:18:0: [sdg] Mode Sense: 73 00 00 08
[162453.929218] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 69, phy 3, sas_addr 0x50019400008e6203
[162453.929470] sd 4:0:18:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162453.931212] scsi 4:0:19:0: Direct-Access     ATA      Hitachi HUA72107 A70M PQ: 0 ANSI: 5
[162453.932281] sd 4:0:19:0: Attached scsi generic sg9 type 0
[162453.933390] sd 4:0:19:0: [sdh] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162454.103126] sd 4:0:19:0: [sdh] Write Protect is off
[162454.103135] sd 4:0:19:0: [sdh] Mode Sense: 73 00 00 08
[162454.113054] sd 4:0:19:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162454.126583]  sdg: sdg1
[162454.310012]  sdh: sdh1
[162454.407200] sd 4:0:18:0: [sdg] Attached SCSI disk
[162454.590680] sd 4:0:19:0: [sdh] Attached SCSI disk
[162467.165846] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 72, phy 6, sas_addr 0x50019400008e6206
[162467.167775] scsi 4:0:20:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162467.168589] sd 4:0:20:0: Attached scsi generic sg10 type 0
[162467.170231] sd 4:0:20:0: [sdi] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162467.219161] sd 4:0:20:0: [sdi] Write Protect is off
[162467.219169] sd 4:0:20:0: [sdi] Mode Sense: 73 00 00 08
[162467.221707] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 73, phy 7, sas_addr 0x50019400008e6207
[162467.221999] sd 4:0:20:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162467.223671] scsi 4:0:21:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162467.224466] sd 4:0:21:0: Attached scsi generic sg11 type 0
[162467.226497] sd 4:0:21:0: [sdj] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162467.267303] sd 4:0:21:0: [sdj] Write Protect is off
[162467.267311] sd 4:0:21:0: [sdj] Mode Sense: 73 00 00 08
[162467.269830] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 74, phy 8, sas_addr 0x50019400008e6208
[162467.270109] sd 4:0:21:0: [sdj] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162467.271744] scsi 4:0:22:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162467.272608] sd 4:0:22:0: Attached scsi generic sg12 type 0
[162467.274371] sd 4:0:22:0: [sdk] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162467.285480]  sdi: sdi1
[162467.314059] sd 4:0:22:0: [sdk] Write Protect is off
[162467.314068] sd 4:0:22:0: [sdk] Mode Sense: 73 00 00 08
[162467.316614] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 75, phy 9, sas_addr 0x50019400008e6209
[162467.316902] sd 4:0:22:0: [sdk] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162467.318785] scsi 4:0:23:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162467.319625] sd 4:0:23:0: Attached scsi generic sg13 type 0
[162467.321297] sd 4:0:23:0: [sdl] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162467.333624]  sdj: sdj1
[162467.368806] sd 4:0:23:0: [sdl] Write Protect is off
[162467.368815] sd 4:0:23:0: [sdl] Mode Sense: 73 00 00 08
[162467.371338] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 76, phy 10, sas_addr 0x50019400008e620a
[162467.371600] sd 4:0:23:0: [sdl] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162467.373487] scsi 4:0:24:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162467.374239] sd 4:0:24:0: Attached scsi generic sg14 type 0
[162467.375920] sd 4:0:24:0: [sdm] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162467.380410]  sdk: sdk1
[162467.420672] sd 4:0:24:0: [sdm] Write Protect is off
[162467.420682] sd 4:0:24:0: [sdm] Mode Sense: 73 00 00 08
[162467.423250] mptsas: ioc0: attaching sata device: fw_channel 0, fw_id 77, phy 11, sas_addr 0x50019400008e620b
[162467.423468] sd 4:0:24:0: [sdm] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162467.425651] scsi 4:0:25:0: Direct-Access     ATA      ST3750641NS      4IST PQ: 0 ANSI: 5
[162467.426402] sd 4:0:25:0: Attached scsi generic sg15 type 0
[162467.428155] sd 4:0:25:0: [sdn] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[162467.435143]  sdl: sdl1
[162467.436826] sd 4:0:20:0: [sdi] Attached SCSI disk
[162467.470727] sd 4:0:25:0: [sdn] Write Protect is off
[162467.470736] sd 4:0:25:0: [sdn] Mode Sense: 73 00 00 08
[162467.473568] sd 4:0:25:0: [sdn] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[162467.478554] sd 4:0:21:0: [sdj] Attached SCSI disk
[162467.487021]  sdm: sdm1
[162467.499971] sd 4:0:22:0: [sdk] Attached SCSI disk
[162467.537043]  sdn: sdn1
[162467.578517] sd 4:0:23:0: [sdl] Attached SCSI disk
[162467.623910] sd 4:0:24:0: [sdm] Attached SCSI disk
[162467.678173] sd 4:0:25:0: [sdn] Attached SCSI disk
[172196.108153]  end_device-4:1:2: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 66, phy 0,sas_addr 0x50019400008e6200
[172196.108162]  phy-4:1:65: mptsas: ioc0: delete phy 0, phy-obj (0xffff880036b8e400)
[172196.108183]  port-4:1:2: mptsas: ioc0: delete port 2, sas_addr (0x50019400008e6200)
[172196.111535] sd 4:0:14:0: [sdc] Synchronizing SCSI cache
[172196.111594] sd 4:0:14:0: [sdc]  
[172196.111598] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.111713] scsi target4:0:14: mptsas: ioc0: delete device: fw_channel 0, fw_id 66, phy 0, sas_addr 0x50019400008e6200
[172196.113079]  end_device-4:1:3: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 67, phy 1,sas_addr 0x50019400008e6201
[172196.113086]  phy-4:1:66: mptsas: ioc0: delete phy 1, phy-obj (0xffff880036b8f400)
[172196.113095]  port-4:1:3: mptsas: ioc0: delete port 3, sas_addr (0x50019400008e6201)
[172196.114824] sd 4:0:15:0: [sdd] Synchronizing SCSI cache
[172196.114883] sd 4:0:15:0: [sdd]  
[172196.114887] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.114983] scsi target4:0:15: mptsas: ioc0: delete device: fw_channel 0, fw_id 67, phy 1, sas_addr 0x50019400008e6201
[172196.115222]  end_device-4:1:6: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 68, phy 2,sas_addr 0x50019400008e6202
[172196.115227]  phy-4:1:67: mptsas: ioc0: delete phy 2, phy-obj (0xffff8802031e5000)
[172196.115234]  port-4:1:6: mptsas: ioc0: delete port 6, sas_addr (0x50019400008e6202)
[172196.115769] sd 4:0:18:0: [sdg] Synchronizing SCSI cache
[172196.115809] sd 4:0:18:0: [sdg]  
[172196.115812] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.115889] scsi target4:0:18: mptsas: ioc0: delete device: fw_channel 0, fw_id 68, phy 2, sas_addr 0x50019400008e6202
[172196.116134]  end_device-4:1:7: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 69, phy 3,sas_addr 0x50019400008e6203
[172196.116139]  phy-4:1:68: mptsas: ioc0: delete phy 3, phy-obj (0xffff8802031e4000)
[172196.116146]  port-4:1:7: mptsas: ioc0: delete port 7, sas_addr (0x50019400008e6203)
[172196.116892] sd 4:0:19:0: [sdh] Synchronizing SCSI cache
[172196.116933] sd 4:0:19:0: [sdh]  
[172196.116937] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.117011] scsi target4:0:19: mptsas: ioc0: delete device: fw_channel 0, fw_id 69, phy 3, sas_addr 0x50019400008e6203
[172196.117219]  end_device-4:1:4: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 70, phy 4,sas_addr 0x50019400008e6204
[172196.117223]  phy-4:1:69: mptsas: ioc0: delete phy 4, phy-obj (0xffff880200903800)
[172196.117229]  port-4:1:4: mptsas: ioc0: delete port 4, sas_addr (0x50019400008e6204)
[172196.117751] sd 4:0:16:0: [sde] Synchronizing SCSI cache
[172196.117789] sd 4:0:16:0: [sde]  
[172196.117793] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.117873] scsi target4:0:16: mptsas: ioc0: delete device: fw_channel 0, fw_id 70, phy 4, sas_addr 0x50019400008e6204
[172196.118106]  end_device-4:1:5: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 71, phy 5,sas_addr 0x50019400008e6205
[172196.118111]  phy-4:1:70: mptsas: ioc0: delete phy 5, phy-obj (0xffff880200903c00)
[172196.118117]  port-4:1:5: mptsas: ioc0: delete port 5, sas_addr (0x50019400008e6205)
[172196.118635] sd 4:0:17:0: [sdf] Synchronizing SCSI cache
[172196.118675] sd 4:0:17:0: [sdf]  
[172196.118678] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.118757] scsi target4:0:17: mptsas: ioc0: delete device: fw_channel 0, fw_id 71, phy 5, sas_addr 0x50019400008e6205
[172196.118970]  end_device-4:1:8: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 72, phy 6,sas_addr 0x50019400008e6206
[172196.118974]  phy-4:1:71: mptsas: ioc0: delete phy 6, phy-obj (0xffff8800e8a51000)
[172196.118981]  port-4:1:8: mptsas: ioc0: delete port 8, sas_addr (0x50019400008e6206)
[172196.121824] sd 4:0:20:0: [sdi] Synchronizing SCSI cache
[172196.125116] sd 4:0:20:0: [sdi]  
[172196.125122] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.125357] scsi target4:0:20: mptsas: ioc0: delete device: fw_channel 0, fw_id 72, phy 6, sas_addr 0x50019400008e6206
[172196.125836]  end_device-4:1:9: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 73, phy 7,sas_addr 0x50019400008e6207
[172196.125842]  phy-4:1:72: mptsas: ioc0: delete phy 7, phy-obj (0xffff8800e8a57400)
[172196.125849]  port-4:1:9: mptsas: ioc0: delete port 9, sas_addr (0x50019400008e6207)
[172196.127948] sd 4:0:21:0: [sdj] Synchronizing SCSI cache
[172196.127990] sd 4:0:21:0: [sdj]  
[172196.127994] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.128252] scsi target4:0:21: mptsas: ioc0: delete device: fw_channel 0, fw_id 73, phy 7, sas_addr 0x50019400008e6207
[172196.128588]  end_device-4:1:10: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 74, phy 8,sas_addr 0x50019400008e6208
[172196.128593]  phy-4:1:73: mptsas: ioc0: delete phy 8, phy-obj (0xffff8800e8a08c00)
[172196.128599]  port-4:1:10: mptsas: ioc0: delete port 10, sas_addr (0x50019400008e6208)
[172196.130470] sd 4:0:22:0: [sdk] Synchronizing SCSI cache
[172196.131081] sd 4:0:22:0: [sdk]  
[172196.131086] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.131176] scsi target4:0:22: mptsas: ioc0: delete device: fw_channel 0, fw_id 74, phy 8, sas_addr 0x50019400008e6208
[172196.131476]  end_device-4:1:11: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 75, phy 9,sas_addr 0x50019400008e6209
[172196.131481]  phy-4:1:74: mptsas: ioc0: delete phy 9, phy-obj (0xffff8800e8a08800)
[172196.131489]  port-4:1:11: mptsas: ioc0: delete port 11, sas_addr (0x50019400008e6209)
[172196.133332] sd 4:0:23:0: [sdl] Synchronizing SCSI cache
[172196.133375] sd 4:0:23:0: [sdl]  
[172196.133379] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.133466] scsi target4:0:23: mptsas: ioc0: delete device: fw_channel 0, fw_id 75, phy 9, sas_addr 0x50019400008e6209
[172196.133766]  end_device-4:1:12: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 76, phy 10,sas_addr 0x50019400008e620a
[172196.133771]  phy-4:1:75: mptsas: ioc0: delete phy 10, phy-obj (0xffff880200119000)
[172196.133779]  port-4:1:12: mptsas: ioc0: delete port 12, sas_addr (0x50019400008e620a)
[172196.136688] sd 4:0:24:0: [sdm] Synchronizing SCSI cache
[172196.136731] sd 4:0:24:0: [sdm]  
[172196.136734] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.136825] scsi target4:0:24: mptsas: ioc0: delete device: fw_channel 0, fw_id 76, phy 10, sas_addr 0x50019400008e620a
[172196.137153]  end_device-4:1:13: mptsas: ioc0: removing sata device: fw_channel 0, fw_id 77, phy 11,sas_addr 0x50019400008e620b
[172196.137159]  phy-4:1:76: mptsas: ioc0: delete phy 11, phy-obj (0xffff880036b23800)
[172196.137167]  port-4:1:13: mptsas: ioc0: delete port 13, sas_addr (0x50019400008e620b)
[172196.140333] sd 4:0:25:0: [sdn] Synchronizing SCSI cache
[172196.140380] sd 4:0:25:0: [sdn]  
[172196.140384] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[172196.140479] scsi target4:0:25: mptsas: ioc0: delete device: fw_channel 0, fw_id 77, phy 11, sas_addr 0x50019400008e620b
[172196.140819]  end_device-4:1:1: mptsas: ioc0: removing ssp device: fw_channel 0, fw_id 78, phy 24,sas_addr 0x50019400008e623e
[172196.140825]  phy-4:1:89: mptsas: ioc0: delete phy 24, phy-obj (0xffff8802005c2400)
[172196.140835]  port-4:1:1: mptsas: ioc0: delete port 1, sas_addr (0x50019400008e623e)
[172196.143455] scsi target4:0:13: mptsas: ioc0: delete device: fw_channel 0, fw_id 78, phy 24, sas_addr 0x50019400008e623e
[172196.144741]  phy-4:4: mptsas: ioc0: delete phy 4, phy-obj (0xffff8800369a1400)
[172196.144751]  phy-4:5: mptsas: ioc0: delete phy 5, phy-obj (0xffff8800369a3800)
[172196.144759]  phy-4:6: mptsas: ioc0: delete phy 6, phy-obj (0xffff880036b20000)
[172196.144764]  phy-4:7: mptsas: ioc0: delete phy 7, phy-obj (0xffff880036b20800)
[172196.144769]  port-4:1: mptsas: ioc0: delete port 1, sas_addr (0x50019400008e623f)
[172196.151153] mptsas: ioc0: delete expander: num_phys 25, sas_addr (0x50019400008e623f)


```

---

### Post by tgalati4 on 2014-11-06
I would suspect a power problem.  Perhaps the power supply on the box can't handle all of those SATA cards.  Do you have a link for the specifications of the enclosure?  What is the rated power for the enclosure?  I would use a kill-a-watt meter to measure the power draw from the wall socket, then a volt meter to measure the 12VDC on one of the power connectors.  What kind of disk drives are you using?  Perhaps take some drives out and test the SATA cards with less bays filled.

---

### Post by MakOwner on 2014-11-07
> **tgalati4 said:**
> I would suspect a power problem.  Perhaps the power supply on the box can't handle all of those SATA cards.  Do you have a link for the specifications of the enclosure?  What is the rated power for the enclosure?  I would use a kill-a-watt meter to measure the power draw from the wall socket, then a volt meter to measure the 12VDC on one of the power connectors.  What kind of disk drives are you using?  Perhaps take some drives out and test the SATA cards with less bays filled.

These are old SGI Rackable enclosures and I have googled for a manual with no success. 
There are 10 Seagate (Seagate ST3750641NS) drives and 2 Hitachi (Hitachi HUA721075KLA330) drives.
The Hitachi drives are "Enterprise" class drives, while those Seagates are consumer level purchases, but were generally purchased right at the start or before the trend of crippling drives for the consumer market was started.

---

