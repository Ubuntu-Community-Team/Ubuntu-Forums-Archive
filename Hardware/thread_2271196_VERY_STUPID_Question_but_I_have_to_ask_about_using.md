---
title: "VERY STUPID Question but I have to ask about using Windows to Update FW"
date: 2015-03-28
forum: Hardware
---

### Post by robertzito on 2015-03-28
]Okay, I am starting to see issues with my new wifi router and my Ubuntu 14.04LTS running on my Dell Inspiron 17R (5720, Mid 2012) so I want to see about getting a firmware update for my wifi and networking hardware. I am sometimes not able to lockup to the SSID. So I have been doing some searching and the most promising thing I am finding is [/COLOR]http://linux.dell.com/repo/community/ubuntu/ 

This is probably a stupid stupid question! 

My machine is dual boot and have not booted into windows in over a year now. But if I did boot into windows and ran all my firmware updates there does it make the fw current in Ubuntu?  

I always understood firmware to be the instructions between the bios and hardware in assembly code as a layer one and the OS as layer two. So if the FW is embedded will that also update them when running in Ubuntu?   

I ran [/COLOR]sudo dmidecode -s bios-version and the result was A14 and I then ran sudo dmidecode -s bios-release-date the result was 12/18/2012.

I run my updates almost every day, but that 12/18/2012 date is what was probably what was on the laptop when I bought it. What would be the difference if I went out and bought a brand new laptop today and loaded Ubuntu 14.04 LTS would I do not think I would have the same problem I am having with hardware from 2012 with hardware from 2015 if 14.04 is the latest and greatest? 

I know is an FW issue because all my newer stuff has no issue with the router and it supports both 2.4 and 5ghz[/FONT][/SIZE]

So at the end of the day the question is, if I bootup into windows and I use all the Dell supported Windows methods to update my firmwares and even bios would it have any impact when booting into Ubuntu?

Sorry, just had to ask because I can not find much on this....

---

### Post by Mark Phelps on 2015-03-28
> But if I did boot into windows and ran all my firmware updates there does it make the fw current in Ubuntu? 

Firmware is specific to individual devices and is unrelated to the OS you use with those devices.  So, once you update the firmware for a device, it stays that way until you change it.

> So if the FW is embedded will that also update them when running in Ubuntu? You update firmware on devices using instructions and code specific to that device.  Most firmware update programs are written for Windows and not only will not run in Linux, you should not even try to run them in Linux -- as any problems that ensue will likely "brick" the device.

> if 14.04 is the latest and greatest? Ubuntu 14.10 is the "latest".  Plus, Ubuntu 15.04 is going to be coming out in only a few weeks.

> I know is an FW issue because all my newer stuff has no issue with the router and it supports both 2.4 and 5ghzActually, if other "stuff" works OK with the router, then firmware is most definitely NOT the issue!  Firware operation is independent of the OS in use, so if a device works fine in Windows but does not in Linux, that has nothing at all to do with the firmware.

---

### Post by robertzito on 2015-03-28
Mark, thanks for taking the time to give me a better understanding.

Eye opener:
[COLOR=#000000]Actually, if other "stuff" works OK with the router, then firmware is most definitely NOT the issue! Firware operation is independent of the OS in use, so if a device works fine in Windows but does not in Linux, that has nothing at all to do with the firmware.

Will wait till 15.04 before troubleshooting, because there was one time my VPN kept failing, switch over to the old wifi and worked fine, but again it is intermittently so will look for patterns in replicating before I touch anything.... [/COLOR]

---

