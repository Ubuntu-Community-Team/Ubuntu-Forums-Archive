---
title: "Hardy - Webcam out of phase with new kernel"
date: 2008-06-05
forum: Hardware
---

### Post by dulfe on 2008-06-05
Hello!

I have a Sony VAIO with a build in webcam (VCC6)... after many hours searching for drivers... I made it work with kernel 2.6.24-16-generic (see picture 1) but with kernels 2.6.17 and 2.6.18 it does not work properly... the image shows out of phase (like a bad adjusted focus - see picture 2). 

FYI: Both pictures have been taken at the same distance from the camera.

Any ideas why?

Thank you!

Picture 1: [IMG]http://www.ulfe.info/images/good.jpg[/IMG]
Picture 2: [IMG]http://www.ulfe.info/images/bad.jpg[/IMG]

---

### Post by steveneddy on 2008-06-05
Find out what the driver is and recompile and install the video driver.

What is the output of

```
lsusb
```

??

---

### Post by dulfe on 2008-06-06
Thank you for the prompt reply!

The driver is _"Ricoh R5U870 Linux Driver - Version 0.11.0, 2008/1/19"_.

The output of **lsusb** is:

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```

I recompiled the driver against kernel .17 and .18 but it did not work... The problem persists.

Thank You!

---

### Post by Sealbhach on 2008-06-06
There's a lot of us Vaio owners with the same problem.

[http://ubuntuforums.org/showthread.php?t=289836&page=21](http://ubuntuforums.org/showthread.php?t=289836&page=21)

I don't really use it but it would be nice to have the option.

What webcam app is that you're using?

.

---

### Post by dulfe on 2008-06-07
The program that I was using is XAWTV.

After reading the link you sent... I tried this and now it works:

1. I recompiled the driver using the new Kernel.
2. Modprobed the module.
3. Restarted the computer.
4. At this point I started XAWTV and the problem persisted. :(
5. Opened Ekiga and started the video.... the webcam worked perfectly!
6. I opened XAWTV again the for my surprise the webcam worked fine too!
7. Restarted the computer.
8. Opened XAWTV and it works ok.

So... I am guessing Ekiga did some kind of custom setup to my webcam that fixed it.

Thank you all!

---

