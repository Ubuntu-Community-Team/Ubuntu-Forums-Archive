---
title: "Ubuntu won't automatically recognized my cd drive."
date: 2011-08-29
forum: Hardware
---

### Post by trauma-d on 2011-08-29
Hi, I just got a new Acer Aspire 5810tz and installed ubuntu 11.04 straight away everything works fine except my cd/dvdrw drive. If I put a disk in nothing happens unless I restart the computer. Sometimes it takes 2 or 3 restarts before it reads that there is a disk in the drive. Its not a really causing major problems its just really annoying. Any ideas?

---

### Post by trauma-d on 2012-05-30
I don't know if anyone else is experiencing this problem but I saw that the post had several views but no replies. This is still an issue I am having even after installing both ubuntu 11.10 and 12.04. I should mention that when I have a disk in the drive and restart and it reads it, if I eject it by right clicking the unity icon for it and selecting "eject" or if a program ejects it then I can put another disk in and it will read it. how ever if I follow the steps above but instead of putting another disk in I close the tray and try to open it again with the hardware button then it will require a restart. I don't know if the extra info helps but I figure it cant hurt. Thanks.

---

### Post by gordintoronto on 2012-05-30
On an occasion when the CD drive is working, perhaps you could open terminal and run this command:
sudo lshw -html > Desktop/config.htm

That should put a small file on your desktop, you can double-click it and it opens in your browser. Find the section which begins "cdrom" and copy/paste it here, perhaps inside a Code block. (open-square-bracket code close-square bracket, then the same containing /code)

---

### Post by trauma-d on 2012-06-15
> **gordintoronto said:**
> On an occasion when the CD drive is working, perhaps you could open terminal and run this command:
sudo lshw -html > Desktop/config.htm

That should put a small file on your desktop, you can double-click it  and it opens in your browser. Find the section which begins "cdrom" and  copy/paste it here, perhaps inside a Code block. (open-square-bracket  code close-square bracket, then the same containing /code)

Sorry for the late reply I have been without internet for a while. The fiberoptic lines that ran to my town where accidentally cut and so I haven't be able to get on in a while. but here is what the config.htm gave me...
```
id:cdrom
                   description: DVD-RAM writer                 product: DVD-RAM UJ862AS                 vendor: MATSHITA                 physical id: 1
                 bus info: scsi@4:0.0.0
                 logical name: /dev/cdrom
                 logical name: /dev/cdrw
                 logical name: /dev/dvd
                 logical name: /dev/dvdrw
                 logical name: /dev/sr0
                 version: 1.00                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                  configuration: ansiversion=5 status=ready                                                                    id:medium
                      physical id: 0
                    logical name: /dev/cdrom

```

---

