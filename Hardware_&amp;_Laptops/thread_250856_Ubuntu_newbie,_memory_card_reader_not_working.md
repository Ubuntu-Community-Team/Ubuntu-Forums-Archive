---
title: "Ubuntu newbie, memory card reader not working"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by tapanp on 2006-09-04
hi there,

I am a ubuntu/linux newbie .. I installed Ubuntu over my windows Xp installation and now have a dual boot installation on my Compaq presario laptop V2148AP.

Everything seems to work just fine. Except my built in 6-1 Memory card reader.

It does not show up when I insert a memory card.. nor am I able to browse through to it.

Another thing I need to do is, have access to my windows partitions through Linux ..

please help

Tapan

---

### Post by x64Jimbo on 2006-09-04
It may not be set to automount. Can you find the device with lspci?

---

### Post by tapanp on 2006-09-05
how do i check that

---

### Post by x64Jimbo on 2006-09-05
Run the command:
lspci

---

### Post by skiwi on 2006-09-05
mine also can't workable. the lspci as follow:
01:09.0 CardBus bridge: ENE Technology Inc CB-720/2/4 Cardbus Controller (rev 01)
01:09.1 CardBus bridge: ENE Technology Inc CB-720/2/4 Cardbus Controller (rev 01)
01:09.2 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller

how to mount it.

thanks

---

### Post by x64Jimbo on 2006-09-05
Once you have a card inserted, try typing something like:
```
sudo mkdir /media/flash1
sudo mount /dev/sda1 /media/flash1
```
Make sure that you try different devices like sda, sdb, sdc, etc. if the first one doesn't work.

---

### Post by mrastas on 2006-11-03
Hi,

I noticed the same problem. I just upgraded to EDGY from Dapper and my SD reader stopped working.

lspci

02:06.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

I tried to manually mount, but i don not have sda1 in dev.

Can it be perhaps something else in dev, or is there a nother problem than automount?

Marko

---

### Post by yusufk on 2006-11-17
Hi,

I also "lost" my mmc after upgrading to Edgy. Any updates on this topic?

02:06.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller


Regards
Y

---

### Post by x64Jimbo on 2006-11-18
Looks like the driver for the device that you two have may have been removed from Ubuntu with the Edgy release. You may wish to file a bug report.

---

### Post by sloggerkhan on 2006-11-18
On my comp I have to type 

 modprobe tifm_sd

to get the card reader working. I think it is unique to certain laptops though. (As a way to get the card reader working.)

---

### Post by giruzz on 2006-11-21
Tanks sloggerkhan...

You just saved me!

giruzz

---

### Post by sloggerkhan on 2006-11-22
weird quirk, isn't it?

---

### Post by ArukiRei on 2006-11-26
> **sloggerkhan said:**
> On my comp I have to type 

 modprobe tifm_sd

to get the card reader working. I think it is unique to certain laptops though. (As a way to get the card reader working.)

I tried to get this to work but I'm getting an error like it's not available anymore. :-? 

```
FATAL: Module tifm_sd not found.
```

---

### Post by mrastas on 2006-11-27
Just tried and it works like a charm...
I modified the /etc/modules file to include tifm_sd.

Thanks for your tip sloggerkhan!!!

PS. has anybody filled a bug report or is this a ubuntu bug?

---

### Post by woody_sud on 2007-08-17
Stop the car, Its not a module problem, I have same with Ricoh device, not working. I read overthere is a kernel problem and the bug is registered, I hope this bug will be fixed in Gutsi gobin

---

### Post by primski on 2007-08-17
What? no way to get Ricoh built-in to Prestigio laptop working on Feisty?

---

