---
title: "Crystalhd, Adobe Flash 11.1, and Ubuntu 11.10"
date: 2012-01-04
forum: Hardware
---

### Post by librechick on 2012-01-04
I'm trying to figure out how to get acceleration for decoding video working with the crystalhd decoder card. It supports 720p and 1020p video. I mainly need 720p so I can watch hulu in hi def.

I have compiled and installed crystalhd. dmesg shows it is loaded. I  have Adobe Flash 11.1 64 bit, and Ubuntu 11.10 64 bit.

I added the following lines to the /etc/adobe/mms.cfg file:  EnableLinuxHWVideoDecode=1 OverrideGPUValidation=true Yet it still appears that adobe flash content is not being accelerated. I rebooted, I tried modprobe crystalhd, and so forth. Adobe Flash 11.1 64 bit is suppose to have support for crystalhd in Linux! Others have said they have gotten it working.

Why can't I? 

I also see crystalhd it in dmesg.

I have no idea how to tell if adobe's flash player is taking advantage of decoder card either.

---

### Post by schumi2012 on 2012-01-08
Hello,

would you provide the output of **dmesg | grep crystalhd**, please?

Which programs have you tried? Totem, I guess? To use totem with crystalhd acceleration you need to compile a gstreamer plugin.

I have written a short tutorial about that: [http://code.google.com/p/indicator-crystalhd/wiki/CrystalHDHowTo](http://code.google.com/p/indicator-crystalhd/wiki/CrystalHDHowTo)


Also, when it runs, please feel free to try out the crystalhd indicator which I've made yesterday:
[img]http://www.abload.de/img/chd2ydkw6.png[/img]
[http://code.google.com/p/indicator-crystalhd/](http://code.google.com/p/indicator-crystalhd/)

regards

---

### Post by librechick on 2012-01-08
I have only tested with Adobe Flash on Hulu. 

here is my output for dmesg:

[   13.494746] Loading crystalhd v3.10.0
[   13.494807] crystalhd 0000:14:00.0: Starting Device:0x1612
[   13.494839] crystalhd 0000:14:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.503445] crystalhd 0000:14:00.0: irq 45 for MSI/MSI-X
[   13.848170] crystalhd 0000:14:00.0: setting latency timer to 64
[ 1540.154796] crystalhd 0000:14:00.0: Opening new user[0] handle
[ 1542.604070] crystalhd 0000:14:00.0: [FMT CH] PIB:0 ff 420 2 2d0 190 2d0 0 0 0
[ 1543.181498] crystalhd 0000:14:00.0: MISSING 15 PICTURES
[ 1544.133779] crystalhd 0000:14:00.0: Opening new user[1] handle
[ 1544.247089] crystalhd 0000:14:00.0: Link invalid state notify mode 7 
[ 1544.368137] crystalhd 0000:14:00.0: Handle is already closed
[ 1544.368193] crystalhd 0000:14:00.0: Closing user[1] handle with mode ffffffff
[ 1544.591180] crystalhd 0000:14:00.0: Closing user[0] handle with mode 41c200
[ 1701.241296] crystalhd 0000:14:00.0: Opening new user[0] handle
[ 1703.620737] crystalhd 0000:14:00.0: [FMT CH] PIB:0 ff 420 2 2d0 190 2d0 0 0 0
[ 1704.041834] crystalhd 0000:14:00.0: MISSING 16 PICTURES
[ 1705.042516] crystalhd 0000:14:00.0: Opening new user[1] handle
[ 1705.142315] crystalhd 0000:14:00.0: Link invalid state notify mode 27 
[ 1705.260869] crystalhd 0000:14:00.0: Handle is already closed
[ 1705.260931] crystalhd 0000:14:00.0: Closing user[1] handle with mode ffffffff
[ 1705.433211] crystalhd 0000:14:00.0: Closing user[0] handle with mode 41c200
[ 1751.017698] crystalhd 0000:14:00.0: Opening new user[0] handle
[ 1753.162545] crystalhd 0000:14:00.0: Opening new user[1] handle
[ 1753.318615] crystalhd 0000:14:00.0: Link invalid state notify mode 3 
[ 1753.363569] crystalhd 0000:14:00.0: [FMT CH] PIB:0 ff 420 2 2d0 190 2d0 0 0 0
[ 1753.435477] crystalhd 0000:14:00.0: Handle is already closed
[ 1753.435548] crystalhd 0000:14:00.0: Closing user[1] handle with mode ffffffff
[ 1753.570818] crystalhd 0000:14:00.0: Closing user[0] handle with mode 41c200

---

### Post by schumi2012 on 2012-01-08
That looks good in a certain way. But it seems that you are trying to play more than one video at a time and as the crystalhd card can only handle one thread, you get these problems.

When I try to watch two youtube videos I get similar output and flash crashes at once.

So please try only to start one video and watch the cpu utilization with top i.e. and dmesg should show that one user handle was opened. You could also try the indicator which is quite nice to use.

---

### Post by librechick on 2012-01-08
Here is the thing. I am not trying to to play multiple videos. The crash was probably not the result of trying to play multiple videos. I actually had a beta flash installed. I corrected that although dmesg shows it I guess. Anyway.  I have another computer that has a faster CPU and it can handle 480p no problem. On the intel atom system with the decoder card it is less than perfect with or without the decoder card. I think.

I can't explain it. I'm not entirely sure the card is working. 

I also have one other issue that may be impacting this. The connection right now is only 1.5Mbps. I have tried with 3Mbps too though. I also have an order to increase it to 10Mbps although that hasn't taken effect yet. When that happens I'm hoping my problems are solved although I'm doubtful. As I said before a faster system played the 480p ok. The intel atom with decoder card did not.

I think I"m going to hold off on further testing until the 10Mbps connection is available. I know you need a faster connection than what I am testing with for 720p. 480p seems to work ok though on my one system though... so who knows (just not the one with the decoder card).

---

### Post by c-m on 2012-02-26
I too have problems with this getting this card working in linux.

I have installed the drivers

```
carl@Mini ~ $  dmesg | grep crystalhd
[   10.171852] Loading crystalhd v3.10.0
[   10.171922] crystalhd 0000:03:00.0: Starting Device:0x1612
[   10.172622] crystalhd 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.188581] crystalhd 0000:03:00.0: irq 44 for MSI/MSI-X
[   10.468403] crystalhd 0000:03:00.0: setting latency timer to 64
carl@Mini ~ $ 
  
```

I have the very latest flash installed.

There was no /etc/adobe/mms.cfg file, so i created it and added: ```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=true 
```

Yet on flash videos in youtube i'm not seeing and hardware acceleration. 

I have also installed VLC 2.1.0, but can't see how to make it use the Crystal HD card, even though it is supported.

dmesg

```

   10.171852] Loading crystalhd v3.10.0
[   10.171922] crystalhd 0000:03:00.0: Starting Device:0x1612
[   10.172622] crystalhd 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.188581] crystalhd 0000:03:00.0: irq 44 for MSI/MSI-X
[   10.468403] crystalhd 0000:03:00.0: setting latency timer to 64

```


Any help would be appreciated

---

### Post by quantaxin on 2012-08-17
Do we have any solution so far. I can't get adobe flash to use the hwaccelerator still.

---

