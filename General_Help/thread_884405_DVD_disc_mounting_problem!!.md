---
title: "DVD disc mounting problem!!"
date: 2008-08-09
forum: General Help
---

### Post by ivikas on 2008-08-09
Hello all,

         i have mastered a DVD data disc in win xp and it simply doesn't mount in ubuntu 8.04.I have been facing this problem for long time with other 
linux distros.some disc simply doesn't come up. some time this DVD disc mounts on linux(other distro) but it refuses to unmount ,simply keeps on refreshing(reading,i could hear the processor fan running sound).


                  sometime when i try to unmound a disc,it says some application is using it,device busy,is there any way to force unmount dic in such cases??

here is the dmesg output(My DVD dic is not coming up in ubuntu 8.04)

[ 1013.794117] UDF-fs: No VRS found
[ 1013.832289] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1013.832724] ISOFS: changing to secondary root
[ 1503.366709] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1503.366716] sr 0:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1503.366721] Info fld=0x10
[ 1503.366723] sr 0:0:0:0: [sr0] Add. Sense: No seek complete
[ 1503.366727] end_request: I/O error, dev sr0, sector 64
[ 1503.366730] Buffer I/O error on device sr0, logical block 8

please give me a hack for this

Thanks in advance

Vikas

---

