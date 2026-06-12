---
title: "LSI 3WARE 9750 Getting CFG-OP-FAIL intermittently"
date: 2015-06-10
forum: Hardware
---

### Post by mike4ubuntu on 2015-06-10
I have 3 boxes running Ubuntu 14.04 that use a LSI 3WARE 9750 (4I4E) RAID Controller that have all been getting CFG-OP-FAIL status now have putting in the latest Ubuntu updates.  It then degrades the Array.  If I reboot, it will, most of the time, clear it out, but then often will come back a some time after the re-boot.  Since the 3ware controllers have all been running fine up to this point, it really seems as if an update caused this issue.  Is anybody else seeing this?

```

 uname -a
Linux lic1 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

$ sudo tw_cli  /c0 show all | grep -i firmware
/c0 Firmware Version = FH9X 5.12.00.013


```


```

$ sudo tw_cli /c0 show
[sudo] password for mike: 

Unit  UnitType  Status         %RCmpl  %V/I/M  Stripe  Size(GB)  Cache  AVrfy
------------------------------------------------------------------------------
u0    RAID-10   VERIFYING      -       58%     256K    7450.56   RiW    ON     
u1    RAID-10   DEGRADED       -       -       256K    5587.91   RiW    ON     

VPort Status         Unit Size      Type  Phy Encl-Slot    Model
------------------------------------------------------------------------------
p0    OK             u0   3.63 TB   SATA  0   -            ST4000DM000-1F2168  
p1    OK             u0   3.63 TB   SATA  1   -            ST4000DM000-1F2168  
p2    OK             u0   3.63 TB   SATA  2   -            ST4000DM000-1F2168  
p3    OK             u0   3.63 TB   SATA  3   -            ST4000DM000-1F2168  
p4    OK             u1   2.73 TB   SATA  4   -            ST3000DM001-9YN166  
p5    OK             u1   2.73 TB   SATA  5   -            ST3000DM001-9YN166  
p6    OK             u1   2.73 TB   SATA  6   -            ST3000DM001-9YN166  
p7    CFG-OP-FAIL    -    2.73 TB   SATA  7   -            ST3000DM001-1CH166  

```

---

