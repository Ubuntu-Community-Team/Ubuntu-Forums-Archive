---
title: "O2Micro MemoryCard Bus.. SD/MMC Reader. Help Needed"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by loadeddreams on 2006-08-29
Installed Ubuntu and so far am please. I have my ATI 9600 working, and setup Compiz for some cool effects, and everything else has worked out of the box.

..However, my SD/MMC card reader will not work.
lspci gives me..
```
fragile@nebuchadnezzar:~$ lspci -v | grep O2
0000:00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
0000:00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
0000:00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator

```

After I load the sdhci module with sudo modprobe sdhci I get this in /var/log/syslog
```
fragile@nebuchadnezzar:~$ tail -f /var/log/syslog
Aug 29 06:01:34 localhost kernel: [17180985.216000] sdhci: Secure Digital Host Controller Interface driver, 0.10
Aug 29 06:01:34 localhost kernel: [17180985.216000] sdhci: Copyright(c) Pierre Ossman

```

and I seem to be lost from there. From the little I can gather, these are the only modules I need loaded. I see nothing in /dev that would be my card reader, either (sd/sg devices).

Any further steps I could take to help get this fixed? I've tried booting with the SD card in the laptop, not in the laptop.. Nothing this far seems to do it.
Thanks

---

### Post by BungaMan on 2006-08-30
As far as I can tell O2 Micro doesn't release specs of the controller and 'says' it's working on a linux driver.  Options are to use a usb card reader or if it is a card that you use for your digicam then connect the digicam via usb.  That's how I have to do it.

Before I forget, please contact O2 Micro and ask them for a linux driver.  The more emails the more they might actually think it would make sense to provide one.

[http://www.o2micro.com/](http://www.o2micro.com/)

---

### Post by loadeddreams on 2006-08-30
> **BungaMan said:**
> As far as I can tell O2 Micro doesn't release specs of the controller and 'says' it's working on a linux driver.  Options are to use a usb card reader or if it is a card that you use for your digicam then connect the digicam via usb.  That's how I have to do it.

Before I forget, please contact O2 Micro and ask them for a linux driver.  The more emails the more they might actually think it would make sense to provide one.

[http://www.o2micro.com/](http://www.o2micro.com/)

yep, I've been reading around a lot more and found what you've said to be true. There's a driver for it but it doesn't look like anyone has gotten it to work, so I'm going to buy a USB Card reader later, I can deal with using my USB on the camera until then :)
I'll contact o2micro as well asking for a driver. the more the better..!

---

### Post by FidO-DidO on 2006-11-16
You can download from [Muscle]("http://musclecard.com/") the [O2Micro OZSCR PCMCIA Smartcardbus Reader Driver]("ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz") for kernel 2.6. I don't know if I should install something after install the O2Micro driver in order to use the smartcard reader and the other memory card readers.

---

### Post by exobuzz on 2006-11-30
That driver is for the smartcard only. Not for the MMC reader.

---

### Post by hfdragon on 2007-06-11
> **FidO-DidO said:**
> You can download from [Muscle]("http://musclecard.com/") the [O2Micro OZSCR PCMCIA Smartcardbus Reader Driver]("ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz") for kernel 2.6. I don't know if I should install something after install the O2Micro driver in order to use the smartcard reader and the other memory card readers.

I have a smartcard reader on my laptop (acer travelmate 8215) and I can't donwload these drivers (the link seems to be down), do you know another place where I can download the drivers ?

---

### Post by craig@pop.co.za on 2008-01-18
I have a HP Compaq nc4000 and it really is sad that the SD does not work because O2Micro of HP have not provided drivers for linux.

---

### Post by Lucius Demon on 2008-03-12
that link at muscle does not work. i have had the reader working before but does anyone know where else the driver might be?

---

