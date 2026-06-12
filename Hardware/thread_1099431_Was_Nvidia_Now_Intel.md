---
title: "Was Nvidia Now Intel?"
date: 2009-03-18
forum: Hardware
---

### Post by Ben Leedham on 2009-03-18
Hi,

 I installed Ubuntu 8.10 on a Dell Latitude D820, all went well and I was happy. 

On initial set up I got a notification telling me restricted drivers were available and that Nvidia 177 drivers were installed, this meant I could have wobbly windows and a rotating cube, again I was happy.

After about a week something happened, my wobbly windows stopped working. I checked to see if I had somehow lost the Nvidia driver but it was still installed.

I did an lshw and oddly I was being told:

```
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
```

I don't really know what has happened, I never did an lshw while everything was working so I never actually saw it telling me I had an Nvidia card, but I did have desktop 3d effects working using a restricted Nvidia driver.

One thing that did work still was dual monitors, when I say worked, it displayed a mirrored output across 2 monitors ( my laptop monitor and an external monitor ).

I used EnvyNG to see what graphics drivers I could install and indeed it told me I had the 177 Nvidia drivers installed, but weren't recommended, as lshw was telling me I didn't have an nvidia card I agreed with EnvyNG, I removed them. 

When I restarted the mirrored monitors stopped working, I used EnvyNG to re-install the Nvidia 177 driver and the mirrored monitors came back to life. 

How can an Nvidia driver have any effect on an Intel card?

If anyone has any idea what is going on I would appreciate the help, even explaining this in writing makes me feel like I am going a bit mental.

Cheers.

---

