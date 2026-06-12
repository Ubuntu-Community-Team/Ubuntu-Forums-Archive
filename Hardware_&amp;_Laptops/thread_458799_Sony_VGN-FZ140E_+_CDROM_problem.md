---
title: "Sony VGN-FZ140E + CDROM problem"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by thenava on 2007-05-30
Hey guys, so I just purchased a Sony VGN-FZ140E. It contains a Sony AWG540A10 IDE drive. I couldn't install Ubuntu Feisty using a live disk, so I had to use the Alternative Install Disk. The installation went fine, but when I boot up the system, my CDROM drive is not detected. The system is trying to mount /dev/hda to /cdrom, but /dev/hda does not even exist in my computer. I tried looking in Device Manager and in the System Logs, but there is no mention of this hardware. Any help would be greatly appreciated.

---

### Post by thenava on 2007-05-30
Anyone?

---

### Post by dyous87 on 2007-08-09
Looks like no one has been able to reply to you on this. I don't know if you were able to fix it or what kind or progress you have have running ubuntu on your computer but this fixed the cdrom problem on mine:

```
sudo mknod /dev/hda b 3 0
```

Aside from that are you still running Ubuntu on this laptop. If so I would like to know how its going. 

I just got the laptop yesterday and I was able to successfully install ubuntu  using the alternative cd. 

Apart from that I have not been able to get the graphics drivers working. I am using the vesa drivers and it is running at a native resolution however this is only a temporary fix. 

Furthermore I have been unable to get wireless successfully working. I tried upgrading to Gutsy and my wireless card did detect networks however it connects and I still have not internet access. I havent tried this with ndiswrapper.

Also I notice that for an Intel Core 2 Duo with 2 gigs of ram it runs awfully slow. My old laptop is an Acer aspire 5672wlmi with an intel Core Duo and 2 gigs of ram at it runs much much quicker.

If you were able to get any of this working or if anyone else has this laptop and is trying to get ubuntu up and running I would appreciate your input.

---

