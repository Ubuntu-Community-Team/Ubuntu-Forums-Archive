---
title: "RTL8101E Ethernet card NOT working"
date: 2008-10-02
forum: Hardware
---

### Post by zoobave on 2008-10-02
```
02:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev ff)
```

I installed ubuntu 7.10 on my  new HP dv5-1102tu laptop. But, Ethernet card is not working properly.
I can able to  set the static IP on eth0. But, i can't ping any device that is connected to my laptop. 

When I gave the command as a normal user: 
```
$ lshw
```
it lists all the devices.

But, When I gave the command as a ROOT user: 
```
$ sudo lshw
```

```
PCI (sysfs)
```
and stay there for a long time.

Please help me

---

### Post by ronnielsen1 on 2008-10-02
[http://ph.ubuntuforums.com/showthread.php?t=782267&page=2](http://ph.ubuntuforums.com/showthread.php?t=782267&page=2)

Looks like they solved the problem there

---

### Post by zoobave on 2008-10-02
thanks. now it works

---

