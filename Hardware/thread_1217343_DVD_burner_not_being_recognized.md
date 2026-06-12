---
title: "DVD burner not being recognized"
date: 2009-07-19
forum: Hardware
---

### Post by pnoland on 2009-07-19
Hello, I apologize if this subject has come up before.  I've searched around prior to registering with the forum and did not find a solution.

My issue is that my Memorex 20x dvd burner is not working at all with Ubuntu 9.04.  It works just fine in my Windows partition and the odd thing is when I tried Debian 5.0 it worked there as well.  I managed to get Ubuntu installed from the minimal cd/net installation since even the live CD did not work with my dvd drive (dropped me to a busybox).  

When I boot in to my linux partition I get the following message before the login screen: "ata3 SRST failed (error=16)" so I'm not sure what to do to fix this issue.  I have tried the all_generic_idle and irqpoll boot options.  The drive itself is not broken since like I said it works in Vista and Debian 5.0 (but I'd rather use Ubuntu...)

Any help would be fantastic before I get fed up and go waste money on a new DVD drive.

Other than that I'm enjoying my time with Ubuntu!

---

### Post by khelben1979 on 2009-07-19
My guess is that your Ubuntu Linux kernel lacks proper support for your DVD drive.

You don't need to buy a new DVD drive in order to use this DVD burner with Ubuntu and there are several options which will get it working, I think.

One option is that you learn how to compile your own Linux kernel to get the inbuilt hardware support with your kernel.

Another option is to investigate if the distribution is lacking packages which you need to get this working.

---

