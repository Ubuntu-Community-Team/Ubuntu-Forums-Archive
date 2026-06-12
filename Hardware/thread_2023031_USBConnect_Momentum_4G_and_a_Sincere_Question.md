---
title: "USBConnect Momentum 4G and a Sincere Question"
date: 2012-07-11
forum: Hardware
---

### Post by jasonditz on 2012-07-11
So I've been using Ubuntu on both my laptop and netbook forever and I had/have a Sprint U727 from work. Its nominally 3g but slow as all getout. Fortunately I have really reliable broadband here and have only had to fall back on the card a couple times a year. (last used it seven months ago)

Anyhow, my employer switched and got a business deal with AT&T and sent me a USB Momentum 4G today. Hardware works on my Mac Mini desktop, but didn't immediately work plug-and-play on either Ubuntu system. 

The physical hardware of the AT&T card is a Sierra Wireless 313U, which according to Sierra's site runs on Ubuntu 9.04 (but isn't officially supported). Sierra, of course, has drivers built right into the kernel, and modinfo shows that they are indeed on both systems.

Now, if anyone can point me in the right direction for a simple fix great, but failing that I'm looking for some honest advice: 

My employer is offering to let me keep the Sprint one instead and send this one back, but the Sprint version costs them somewhat more and is very slow. But I'd have to decide within a couple days because they have limited time to return the AT&T one. 

Given this information, should I assume I will figure out the AT&T card with more fiddling (the drivers are installed, after all) or should I just scrap it and keep the Sprint one?

---

### Post by sshields2173 on 2012-08-18
hi jason

i am using ubuntu 11.04 and have found sierra telstra 4G wireless toggle does not automatically configure. 

I ran as root the command *lsusb -t -d 19d2:0031* and it listed usb devices not connected as

root@simons-ThinkPad-L512:~# lsusb -t -d 19d2:0031
2-1.1:1.0: No such file or directory
2-1.1:1.1: No such file or directory
2-1.1:1.3: No such file or directory
2-1.1:1.4: No such file or directory
1-1.3:1.0: No such file or directory
1-1.6:1.2: No such file or directory
1-1.6:1.3: No such file or directory
2-1.1:1.7: No such file or directory
1-1.1:1.0: No such file or directory
1-1.1:1.1: No such file or directory
1-1.1:1.2: No such file or directory
1-1.1:1.3: No such file or directory
1-1.1:1.4: No such file or directory
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
        |__ Port 1: Dev 11, If 0, Class=vend., Driver=, 480M
        |__ Port 1: Dev 11, If 1, Class=vend., Driver=, 480M
        |__ Port 1: Dev 11, If 3, Class=vend., Driver=, 480M
        |__ Port 1: Dev 11, If 4, Class=vend., Driver=, 480M
        |__ Port 1: Dev 11, If 7, Class=vend., Driver=, 480M
        |__ Port 1: Dev 11, If 9, Class=stor., Driver=usb-storage, 480M
        |__ Port 4: Dev 3, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
        |__ Port 4: Dev 3, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 1: Dev 6, If 0, Class=comm., Driver=, 480M
        |__ Port 1: Dev 6, If 1, Class=data, Driver=, 480M
        |__ Port 1: Dev 6, If 2, Class=comm., Driver=, 480M
        |__ Port 1: Dev 6, If 3, Class=still, Driver=, 480M
        |__ Port 1: Dev 6, If 4, Class=vend., Driver=, 480M
        |__ Port 3: Dev 4, If 0, Class=vend., Driver=, 12M
        |__ Port 6: Dev 5, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 6: Dev 5, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 6: Dev 5, If 2, Class=vend., Driver=, 12M
        |__ Port 6: Dev 5, If 3, Class=app., Driver=, 12M

so maybe ubuntu don't have device drivers for it.

Anyway if you find any intel on how to connect ubuntu to sierra 4G i'd sure like a heads up.

If I discover anything I'll pass it on.

I'll put it here and [http://simonsaysbiz.com/technology](http://simonsaysbiz.com/technology)

thanks
simon

---

