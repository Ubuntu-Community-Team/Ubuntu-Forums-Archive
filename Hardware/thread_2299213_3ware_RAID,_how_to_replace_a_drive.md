---
title: "3ware RAID, how to replace a drive"
date: 2015-10-16
forum: Hardware
---

### Post by Gregor D Seas on 2015-10-16
Hello, 

I am new to RAIDs and a server I have inherited is showing a SMART-FAILURE in the 3ware 9650SE-8LPML RAID-5 array. I have found from looking around that SMART-FAILURE is one of these obscure errors that may be due a pending drive failure or a manufacturer's low threshold setting etc. 

At this point I would like to change the drive. I have been reading the documentation of the 3ware User's Guide and I was hoping to get step-by-step information about what to do. Apparently it is not the case. Does anyone have any resource of how I would go about replacing the drive?

Thank you!


```
# /usr/sbin/tw_cli info c2 

Unit  UnitType  Status         %RCmpl  %V/I/M  Stripe  Size(GB)  Cache  AVrfy
------------------------------------------------------------------------------
u0    SINGLE    OK             -       -       -       931.312   W      OFF    
u1    RAID-1    OK             -       -       -       931.312   W      OFF    
u2    SPARE     OK             -       -       -       931.505   -      OFF    

VPort Status         Unit Size      Type  Phy Encl-Slot    Model
------------------------------------------------------------------------------
p0    OK             u0   931.51 GB SATA  0   -            ST31000340NS        
p1    SMART-FAILURE  u1   931.51 GB SATA  1   -            ST31000340NS        
p2    OK             u1   931.51 GB SATA  2   -            ST31000340NS        
p3    OK             u2   931.51 GB SATA  3   -            ST31000340NS        

Name  OnlineState  BBUReady  Status    Volt     Temp     Hours  LastCapTest
---------------------------------------------------------------------------
bbu   On           Yes       OK        OK       OK       0      xx-xxx-xxxx  

```

---

