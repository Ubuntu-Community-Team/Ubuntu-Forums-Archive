---
title: "Firewire IPOD not mounting on 8.10"
date: 2008-11-05
forum: Hardware
---

### Post by 454abp on 2008-11-05
Hi,

since upgrading to 8.10 i have a problem with my IPOD Classic (3rd generation). It is not mounting any more on my system.

Dmesg has the following output:

```

[ 1361.914781] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a27000275787b]  
[ 1361.916200] ieee1394: Node changed: 0-00:1023 -> 0-01:1023                   
[ 1361.921465] scsi4 : SBP-2 IEEE-1394                                          
[ 1363.123864] ieee1394: sbp2: Logged into SBP-2 device                         
[ 1363.125451] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]                                                                            
[ 1363.129066] scsi 4:0:0:0: Direct-Access-RBC Apple    iPod             1.53 PQ: 0 ANSI: 2                                                                     
[ 1365.059349] sd 4:0:0:0: [sdc] Spinning up disk....ready                      
[ 1367.215657] sd 4:0:0:0: [sdc] 29297520 512-byte hardware sectors (15000 MB)  
[ 1367.218740] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled           
[ 1367.221696] sd 4:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA                                                         
[ 1367.227208] sd 4:0:0:0: [sdc] 29297520 512-byte hardware sectors (15000 MB)  
[ 1367.232125] sd 4:0:0:0: [sdc] Test WP failed, assume Write Enabled           
[ 1367.234969] sd 4:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA                                                         
[ 1367.239776]  sdc: sdc1 sdc2                                                  
[ 1367.259583] sd 4:0:0:0: [sdc] Attached SCSI removable disk                   
[ 1367.265834] sd 4:0:0:0: Attached scsi generic sg3 type 14                    
[ 1367.404657] end_request: I/O error, dev sdc, sector 104                      
[ 1367.404674] __ratelimit: 3 callbacks suppressed                              
[ 1367.404679] Buffer I/O error on device sdc, logical block 13                 
[ 1367.404688] Buffer I/O error on device sdc, logical block 14                 
[ 1367.404692] Buffer I/O error on device sdc, logical block 15                 
[ 1367.404696] Buffer I/O error on device sdc, logical block 16                 
[ 1367.404699] Buffer I/O error on device sdc, logical block 17                 
[ 1367.404702] Buffer I/O error on device sdc, logical block 18                 
[ 1367.404706] Buffer I/O error on device sdc, logical block 19                 
[ 1367.404709] Buffer I/O error on device sdc, logical block 20                 
[ 1367.404712] Buffer I/O error on device sdc, logical block 21                 
[ 1367.404716] Buffer I/O error on device sdc, logical block 22                 
[ 1367.405472] end_request: I/O error, dev sdc, sector 104                      
[ 1367.407063] end_request: I/O error, dev sdc, sector 104                      
[ 1367.407871] end_request: I/O error, dev sdc, sector 104                      
[ 1367.410911] end_request: I/O error, dev sdc, sector 104                      
[ 1367.590651] end_request: I/O error, dev sdc, sector 0                        
[ 1367.591419] end_request: I/O error, dev sdc, sector 0                        
[ 1367.592261] end_request: I/O error, dev sdc, sector 0                        
[ 1367.600801] end_request: I/O error, dev sdc, sector 63                       
[ 1367.601574] end_request: I/O error, dev sdc, sector 63                       
[ 1367.602211] end_request: I/O error, dev sdc, sector 65                       
[ 1367.634722] end_request: I/O error, dev sdc, sector 80325                    
[ 1367.635465] end_request: I/O error, dev sdc, sector 80325                    
[ 1367.636095] end_request: I/O error, dev sdc, sector 80327                    
[ 1367.751871] end_request: I/O error, dev sdc, sector 63                       
[ 1367.752623] end_request: I/O error, dev sdc, sector 63                       
[ 1367.753247] end_request: I/O error, dev sdc, sector 65                       
[ 1367.756249] end_request: I/O error, dev sdc, sector 0                        
[ 1367.756998] end_request: I/O error, dev sdc, sector 8                        
[ 1367.757625] end_request: I/O error, dev sdc, sector 0                        
[ 1367.759601] end_request: I/O error, dev sdc, sector 0                        
[ 1367.847657] end_request: I/O error, dev sdc, sector 80325                    
[ 1367.848408] end_request: I/O error, dev sdc, sector 80325                    
[ 1367.849026] end_request: I/O error, dev sdc, sector 80327                    
[ 1367.852160] end_request: I/O error, dev sdc, sector 0                        
[ 1367.852911] end_request: I/O error, dev sdc, sector 8                        
[ 1367.853535] end_request: I/O error, dev sdc, sector 0                        
[ 1367.854333] end_request: I/O error, dev sdc, sector 0                        
[ 1370.065431] end_request: I/O error, dev sdc, sector 0                        
[ 1370.066245] end_request: I/O error, dev sdc, sector 0                        
[ 1370.067080] end_request: I/O error, dev sdc, sector 0                        

```

Does any of you has a clue about that?

/454abp

---

### Post by zwrtwtr on 2008-11-06
Same here. Fresh kubuntu intrepid install and a 3G ipod classic.

Worked like a charm on hardy...

Zw

---

### Post by jdunn on 2008-11-09
Same here.  3rd generation Ipod w/Firewire.  However, I switched from using Kubuntu all these years to Ubuntu (I'm not happy with KDE 4).  It makes sense the desktop suite would have nothing to do with it.  Anyway, My Ipod worked fine all these years but on 8.10, it won't mount.

---

### Post by teddks on 2008-11-09
Are you talking about the all-white iPods with the full touch controls?

I have one of those, and while I use USB mostly, I have a computer with a firewire card that I could throw the liveCD on.

---

### Post by jdunn on 2008-11-10
> **teddks said:**
> Are you talking about the all-white iPods with the full touch controls?

I'm not sure.  They are all white.  The Reverse, Forward, Menu and Play touch-buttons are above (not on) the touch-wheel.  I guess USB can be used for data transfers but only Firewire (12V) or an AC-outlet adapter can charge the unit.

[IMG]http://www.kernelthread.com/mac/ipod/images/specs_new.jpg[/IMG]

---

### Post by teddks on 2008-11-10
> **jdunn said:**
> I'm not sure.  They are all white.  The Reverse, Forward, Menu and Play touch-buttons are above (not on) the touch-wheel.  I guess USB can be used for data transfers but only Firewire (12V) or an AC-outlet adapter can charge the unit.

[IMG]http://www.kernelthread.com/mac/ipod/images/specs_new.jpg[/IMG]

That's the one.

I'll give it a whirl on the liveCD and post back with my results.

---

### Post by crazedgremlin on 2008-11-11
Yep, I've got this problem, too.  Besides those dmesg outputs, I tried to manually mount and got this:

```

root@doom:/media# mount -t vfat /dev/sdc ipod/
mount: /dev/sdc: can't read superblock
root@doom:/media# mount -t vfat /dev/sdc1 ipod/
mount: /dev/sdc1: can't read superblock
root@doom:/media# mount -t vfat /dev/sdc2 ipod/
mount: /dev/sdc2: can't read superblock
```

---

### Post by sadrak on 2008-11-30
Same problem here :-/

USB works, firewire not ...

with USB it mounts as:
/dev/sdb2 on /media/IPOD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


here are the output from dmesg after plugin with firewire:
```

[   70.529536] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[000a270002134f76]
[   70.532808] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[   70.536953] scsi4 : SBP-2 IEEE-1394
[   71.789643] ieee1394: sbp2: Logged into SBP-2 device
[   71.789723] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[   71.792467] scsi 4:0:0:0: Direct-Access-RBC Apple    iPod             1.53 PQ: 0 ANSI: 2
[   73.626151] sd 4:0:0:0: [sdb] Spinning up disk.....ready
[   77.465634] sd 4:0:0:0: [sdb] 58595040 512-byte hardware sectors (30001 MB)
[   77.467725] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   77.469561] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   77.472611] sd 4:0:0:0: [sdb] 58595040 512-byte hardware sectors (30001 MB)
[   77.474732] sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   77.476428] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   77.476441]  sdb: sdb1 sdb2
[   77.488201] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   77.488432] sd 4:0:0:0: Attached scsi generic sg3 type 14
[   77.636375] end_request: I/O error, dev sdb, sector 104
[   77.636388] Buffer I/O error on device sdb, logical block 13
[   77.636402] Buffer I/O error on device sdb, logical block 14
[   77.636410] Buffer I/O error on device sdb, logical block 15
[   77.636417] Buffer I/O error on device sdb, logical block 16
[   77.636425] Buffer I/O error on device sdb, logical block 17
[   77.636433] Buffer I/O error on device sdb, logical block 18
[   77.636440] Buffer I/O error on device sdb, logical block 19
[   77.636448] Buffer I/O error on device sdb, logical block 20
[   77.636456] Buffer I/O error on device sdb, logical block 21
[   77.636464] Buffer I/O error on device sdb, logical block 22
[   77.637230] end_request: I/O error, dev sdb, sector 104
[   77.638257] end_request: I/O error, dev sdb, sector 104
[   77.639038] end_request: I/O error, dev sdb, sector 104
[   77.639804] end_request: I/O error, dev sdb, sector 104
[   77.691566] end_request: I/O error, dev sdb, sector 0
[   77.692976] end_request: I/O error, dev sdb, sector 0
[   77.696775] end_request: I/O error, dev sdb, sector 0
[   77.698931] end_request: I/O error, dev sdb, sector 80325
[   77.704618] end_request: I/O error, dev sdb, sector 80325
[   77.705379] end_request: I/O error, dev sdb, sector 80327
[   77.706963] end_request: I/O error, dev sdb, sector 63
[   77.707744] end_request: I/O error, dev sdb, sector 63
[   77.708516] end_request: I/O error, dev sdb, sector 65
[   77.750214] end_request: I/O error, dev sdb, sector 80325
[   77.752311] end_request: I/O error, dev sdb, sector 80325
[   77.753079] end_request: I/O error, dev sdb, sector 80327
[   77.761134] end_request: I/O error, dev sdb, sector 0
[   77.761931] end_request: I/O error, dev sdb, sector 8
[   77.762697] end_request: I/O error, dev sdb, sector 0
[   77.769046] end_request: I/O error, dev sdb, sector 0
[   77.827953] end_request: I/O error, dev sdb, sector 63
[   77.829251] end_request: I/O error, dev sdb, sector 63
[   77.830025] end_request: I/O error, dev sdb, sector 65
[   77.831895] end_request: I/O error, dev sdb, sector 0
[   77.833022] end_request: I/O error, dev sdb, sector 0
[   77.834160] end_request: I/O error, dev sdb, sector 0
[   80.033784] end_request: I/O error, dev sdb, sector 0
[   80.035624] end_request: I/O error, dev sdb, sector 0
[   80.036480] end_request: I/O error, dev sdb, sector 0


```

---

### Post by zbeckerd on 2008-12-10
Yes my 3g pod worked fine in every other version going back to the 5.xx era.  Does not work with firewire now on 8.10.  Usb is fine (but 3g's do not charge on usb).

---

### Post by exparrot16 on 2008-12-28
I just discovered that I have this same problem. Firewire worked fine in several previous versions of Ubuntu but not now. Oh well. I've got a spare usb cable for now...

---

