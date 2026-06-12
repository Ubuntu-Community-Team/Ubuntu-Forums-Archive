---
title: "TV Tuner Card"
date: 2013-07-18
forum: Hardware
---

### Post by hi452 on 2013-07-18
Okay I have been using linux for about 3 months, done nothing fabulous but I know my way around it all pretty well. I am running Ubuntu 12.04.2 LTS, but if there is compatibility issues I would be willing to reinstall a lower version of Ubuntu. Probably wouldn't hurt my old pentium 4 processor any! :mrgreen:

If you cant guess by the fact it doesn't have a state of the art processor but instead has a pentium 4, this is my home server we are talking about.I want to be able to use this computer as a DVR for some tv shows to avoid renting a cable box from my provider. I am only looking to record/capture the unencrypted channels that you do NOT need a box to watch anyhow. I then stream the saved recorded files to my windows clients on my network through file sharing. (I already have this set up.) Seems totally plausible to me.

So I was able to acquire a nice tuning card pretty cheap, used. I got the WinTV PVR 350 as I know there is linux support for it and it was a decent card when it came out several a year ago. I installed it in my computer and I am blown away at what happens. Do you wanna know what happens?

NOTHING. So what do I need to do to be able to make this card work to record my shows? I know I need a program like MythTV or MeTV to record with, but I suppose I also need the drivers for the card, and I have no clue where to get or how to install them and see this as more of an issue than the program which I should be able to figure out on my own. I would also like to know If I have to configure a certain file so that when my server boots it automatically starts what it needs to. 

Thanks.

---

### Post by chest069 on 2013-07-19
Hello,

I did some searching on google and see that it is supported. Open up the package manager and search for [COLOR=#000000][FONT=Arial][B]Hauppauge and IVTV drivers and see if it works to get the card working for you,

Also here are some links on the card and info:
[http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html)
[http://linuxtv.org/wiki/index.php/Hauppauge](http://linuxtv.org/wiki/index.php/Hauppauge)
[http://linuxtv.org/](http://linuxtv.org/)
[http://linuxtv.org/wiki/index.php/Hardware_Device_Information](http://linuxtv.org/wiki/index.php/Hardware_Device_Information)
[http://en.wikipedia.org/wiki/LinuxTV](http://en.wikipedia.org/wiki/LinuxTV)

Hope this helps you get started and you can also ask your question at Ask Ubuntu [http://askubuntu.com/](http://askubuntu.com/) . Good luck.[/B][/FONT][/COLOR]

---

### Post by hi452 on 2013-07-19
Okay I went into the package manager and installed the proper drivers. What would be the easiest and most reliable way of testing to see if I have it working correctly or not?

---

### Post by scbingham on 2013-07-19
I have 12.04LTS & a WinTV Nova-TD usb stick.
lsusb finds it. I installed MeTV & it worked.

I don't recall having to download any drivers.

---

### Post by hi452 on 2013-07-19
Okay well lspci finds my card but MeTV doesn't. Did you have to configure MeTV in a certain way?

---

### Post by scbingham on 2013-07-19
No, just 'straight out of the box'. In fact, there doesn't seem to be any device config options.

I've had a search around, I guess you do need a driver for a pci card.

I did notice a brief mention of SageTV.

Not really sure I'm able to help. Have you tried the Multimedia and Video section? Maybe click on 'report post' & ask the mods to move your thread.

Good luck.

---

### Post by dannyboy79 on 2013-07-20
the kernel has support built right in for this. i use it with mythtv and a PVR-500 as well. 
you can check dmesg to see if the hardware is initializing
```
dmesg | grep ivtv
```

you should see something similar to this
```
[   36.720380] ivtv: Start initialization, version 1.4.3
[   36.720576] ivtv0: Initializing card 0
[   36.720584] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   36.744204] ivtv0:  info: base addr: 0xdc000000
[   36.744213] ivtv0:  info: Enabling pci device
[   36.744247] ivtv0:  info: Bus Mastering Enabled.
[   36.744252] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   36.744262] ivtv0:  info: 2051 (rev 1) at 00:08.0, irq: 11, latency: 64, memory: 0xdc000000
[   36.744265] ivtv0:  info: attempting ioremap at 0xdc000000 len 0x00800000
[   36.745172] ivtv0:  info: attempting ioremap at 0xdd000000 len 0x00800000
[   36.746046] ivtv0:  info: attempting ioremap at 0xde000000 len 0x00010000
[   36.746067] ivtv0:  info: activating i2c...
[   36.907355] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   36.907358] ivtv0:  info: NTSC tuner detected
[   37.900749] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   41.182239] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[   41.287740] msp3400 0-0040: MSP4448G-B3 found @ 0x80 (ivtv i2c driver #0)
[   41.403374] ivtv0:  info: Allocate DMA encoder MPG stream: 256 x 32768 buffers (8192kB total)
[   41.403671] ivtv0:  info: Allocate DMA encoder YUV stream: 256 x 32768 buffers (8192kB total)
[   41.403959] ivtv0:  info: Allocate DMA encoder VBI stream: 61 x 17472 buffers (1040kB total)
[   41.404109] ivtv0:  info: Allocate DMA encoder PCM stream: 143 x 4608 buffers (643kB total)
[   41.404228] ivtv0:  info: Allocate DMA decoder MPG stream: 16 x 65536 buffers (1024kB total)
[   41.404264] ivtv0:  info: Allocate decoder VBI stream: 29 x 2304 buffers (65kB total)
[   41.404294] ivtv0:  info: Allocate DMA decoder YUV stream: 16 x 65536 buffers (1024kB total)
[   41.408482] ivtv0: Registered device video0 for encoder MPG (8192 kB)
[   41.408833] ivtv0: Registered device video32 for encoder YUV (8192 kB)
[   41.409162] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   41.409486] ivtv0: Registered device video24 for encoder PCM (640 kB)
[   41.409825] ivtv0: Registered device radio0 for encoder radio
[   41.410177] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[   41.410503] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[   41.410843] ivtv0: Registered device vbi16 for decoder VOUT
[   41.416279] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[   41.416288] ivtv0: Initialized card: Hauppauge WinTV PVR-350

```

you can test it's output using this
```
cat /dev/video0 > test.mpg
```
then just hit ctrl-c to cancel that command and then use vlc or mplayer to check the mpg file
```
vlc test.mpg
```

this is of course assuming you have an analog coax cable connected to it.

---

