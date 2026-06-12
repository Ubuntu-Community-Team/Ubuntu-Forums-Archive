---
title: "Lacie usb HDD monting causes total system crash"
date: 2014-09-22
forum: Hardware
---

### Post by raghav5 on 2014-09-22
Lacie 1tb rugged drive is not recognised when plugged in to usb 3 port on lenovo x230 laptop. lsusb shows the disk, but lsblk does not. 30 seconds after plugging in X crashes, and screen shows lots of the following repeating inifinately (taken from syslog)...

```
Sep 22 19:13:23 StinkPad kernel: [  315.825397] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSESep 22 19:13:23 StinkPad kernel: [  315.825398] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825399] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.825401] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825403] Add. Sense: Invalid field in parameter list
Sep 22 19:13:23 StinkPad kernel: [  315.825407] sd 9:0:0:0: [sdd] CDB: 
Sep 22 19:13:23 StinkPad kernel: [  315.825409] Read(10): 28 00 07 02 a1 0e 00 00 01 00
Sep 22 19:13:23 StinkPad kernel: [  315.825419] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825422] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 19:13:23 StinkPad kernel: [  315.825425] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825426] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.825429] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825432] Add. Sense: Invalid field in parameter list
Sep 22 19:13:23 StinkPad kernel: [  315.825434] sd 9:0:0:0: [sdd] CDB: 
Sep 22 19:13:23 StinkPad kernel: [  315.825435] Read(10): 28 00 07 02 a1 0f 00 00 01 00
Sep 22 19:13:23 StinkPad kernel: [  315.825922] sd 9:0:0:0: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
Sep 22 19:13:23 StinkPad kernel: [  315.825937] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825938] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 19:13:23 StinkPad kernel: [  315.825939] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825940] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.825942] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.825943] Add. Sense: Invalid field in parameter list
Sep 22 19:13:23 StinkPad kernel: [  315.825944] sd 9:0:0:0: [sdd] CDB: 
Sep 22 19:13:23 StinkPad kernel: [  315.825945] Read(10): 28 00 07 02 a1 11 00 00 01 00
Sep 22 19:13:23 StinkPad kernel: [  315.826176] sd 9:0:0:0: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
Sep 22 19:13:23 StinkPad kernel: [  315.826182] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826185] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 19:13:23 StinkPad kernel: [  315.826186] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826187] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.826189] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826191] Add. Sense: Invalid field in parameter list
Sep 22 19:13:23 StinkPad kernel: [  315.826196] sd 9:0:0:0: [sdd] CDB: 
Sep 22 19:13:23 StinkPad kernel: [  315.826197] Read(10): 28 00 07 02 a1 13 00 00 01 00
Sep 22 19:13:23 StinkPad kernel: [  315.826423] sd 9:0:0:0: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
Sep 22 19:13:23 StinkPad kernel: [  315.826428] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826431] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 19:13:23 StinkPad kernel: [  315.826433] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826434] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.826436] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826438] Add. Sense: Invalid field in parameter list
Sep 22 19:13:23 StinkPad kernel: [  315.826440] sd 9:0:0:0: [sdd] CDB: 
Sep 22 19:13:23 StinkPad kernel: [  315.826444] Read(10): 28 00 07 02 a1 15 00 00 01 00
Sep 22 19:13:23 StinkPad kernel: [  315.826671] sd 9:0:0:0: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
Sep 22 19:13:23 StinkPad kernel: [  315.826677] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826678] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 19:13:23 StinkPad kernel: [  315.826679] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826679] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.826681] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.826681] Add. Sense: Invalid field in parameter list
Sep 22 19:13:23 StinkPad kernel: [  315.826682] sd 9:0:0:0: [sdd] CDB: 
Sep 22 19:13:23 StinkPad kernel: [  315.826683] Read(10): 28 00 07 02 a1 16 00 00 01 00
Sep 22 19:13:23 StinkPad kernel: [  315.827152] sd 9:0:0:0: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
Sep 22 19:13:23 StinkPad kernel: [  315.827164] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.827164] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 19:13:23 StinkPad kernel: [  315.827165] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.827166] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.827168] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.827169] Add. Sense: Invalid field in parameter list
Sep 22 19:13:23 StinkPad kernel: [  315.827170] sd 9:0:0:0: [sdd] CDB: 
Sep 22 19:13:23 StinkPad kernel: [  315.827170] Read(10): 28 00 07 02 a1 18 00 00 01 00
Sep 22 19:13:23 StinkPad kernel: [  315.827650] sd 9:0:0:0: uas_sense_old: urb length 26 disagrees with IU sense data length 510, using 18 bytes of sense data
Sep 22 19:13:23 StinkPad kernel: [  315.827655] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.827658] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 22 19:13:23 StinkPad kernel: [  315.827660] sd 9:0:0:0: [sdd]  
Sep 22 19:13:23 StinkPad kernel: [  315.827661] Sense Key : Illegal Request [current] 
Sep 22 19:13:23 StinkPad kernel: [  315.827663] sd 9:0:0:0: [sdd]  



```

---

### Post by tgalati4 on 2014-09-22
I think your rugged drive is pulling too much current.  Do you have an external power supply for it?

---

