---
title: "dmraid + ICH10R RAID10: &#8220;RAID set was not activated&#8221;"
date: 2010-01-29
forum: Hardware
---

### Post by CyberShadow on 2010-01-29
Hi,

I'm trying to mount an existing SATA RAID 10 set on a Gigabyte EX58-DS4 (ICH10R "fake" RAID). dmraid is giving me the following:
```

root@CyberShadow:/home/vladimir# dmraid -b
/dev/sde:   1465149168 total, "3QK0782F"
/dev/sdd:   1465149168 total, "GTE200P8H4T5BE"
/dev/sdc:   1465149168 total, "GTE200P8H4MSME"
/dev/sdb:   1465149168 total, "GTE200P8H4SXME"
/dev/sda:   1465149168 total, "GTE200P8H4STPE"

root@CyberShadow:/home/vladimir# dmraid -s
*** Group superset isw_cjdfhahhia
--> Superset
name   : isw_cjdfhahhia_My RAID 10
size   : 2930289152
stride : 128
type   : raid01
status : ok
subsets: 2
devs   : 4
spares : 0

root@CyberShadow:/home/vladimir# dmraid -r
/dev/sdd: isw, "isw_cjdfhahhia", GROUP, ok, 1465149166 sectors, data@ 0
/dev/sdc: isw, "isw_cjdfhahhia", GROUP, ok, 1465149166 sectors, data@ 0
/dev/sdb: isw, "isw_cjdfhahhia", GROUP, ok, 1465149166 sectors, data@ 0
/dev/sda: isw, "isw_cjdfhahhia", GROUP, ok, 1465149166 sectors, data@ 0

root@CyberShadow:/home/vladimir# dmraid -ay
RAID set "isw_cjdfhahhia_My RAID 10-0" was activated
RAID set "isw_cjdfhahhia_My RAID 10-1" was activated
RAID set "isw_cjdfhahhia_My RAID 10" was not activated
```
The verbose/debug flags don't offer much insight, but I'll post detailed logs on request.

---

