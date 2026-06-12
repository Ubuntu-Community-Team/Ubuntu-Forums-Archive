---
title: "Unable to mount cdrom0"
date: 2010-03-28
forum: Hardware
---

### Post by talha06 on 2010-03-28
Hello everyone,

[FONT="Trebuchet MS"]I've been using my Acer 5520G for 1.5 years and I haven't taken any errors with my cd/dvd writer until last a few days. 

When I put a cd/dvd to my cd/dvd writer, it works: I hear sounds as before and the rom's light is on. But when I try to open disc (also I can't see the disc's label, it always writes "**cdrom0**") I take a message like this : 
[/FONT]
"**[SIZE="3"]Unable to mount cdrom0[/SIZE]**

[SIZE="3"]mount: special device /dev/scd0 does not exist"[/SIZE]

[FONT="Trebuchet MS"]Please, waiting ur helps..

Thanx in advance,
with regards,
Talha[/FONT]

---

### Post by voja15 on 2010-03-28
Take a look at this thread:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1326285](http://www.uluga.ubuntuforums.org/showthread.php?t=1326285)

---

### Post by talha06 on 2010-03-28
Thanx for ur interest, but I have already looked the page that u linked.. I'm not able to see the bold cold that is quoted..

---

### Post by voja15 on 2010-03-28
And what do you get when you execute
```
sudo lshw -C disk
```

---

### Post by talha06 on 2010-03-28
> **voja15 said:**
> And what do you get when you execute
```
sudo lshw -C disk
```
Here's the output:
```
*-disk                  
       description: ATA Disk
       product: WDC WD2500BEVS-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXC108211918
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=c92b25a6
```

---

