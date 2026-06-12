---
title: "Usb to RS232 adapter problem"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by skychris on 2007-12-18
Hi All :)
I have an "usb to serial" adapter and it gives me some troubles to intall it.
it only comes with the windows drivers and the only info I have about the manufaturer is that it's written HL-340 on the side... 
the output to "lsusb" sends
```
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 009: ID 4348:5523  
Bus 002 Device 002: ID 046d:c219 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:0892 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```
that shows me that the kernel recognise that somethig is hooked up but doesn't recognize the model or manufacturer. 
I came across some drivers for a similar device made by Prolific, which has a different ID, and some courageous people seem to have twitch and patch this driver for the HL-340 but the info are quite messy and the few attempts I made to adapt this driver myself ended up nowhere...
Is there a kind person out there to give me some clues and leads on this?
thanks a lot :)

---

### Post by skychris on 2007-12-18
following my previous post I made some research on the web and found some

first, the source of the "Prolific" based driver with the wrong ID, that should work with the HL-340.

[HTML]http://www.krn.ru/Support/Drivers/LinuxDriver_pl2303_v0213.zip[/HTML]

then a patch specifically for the HL-340

[HTML]http://trash.uid0.hu/stuff/pl2303_hl340.diff[/HTML] 

now the big question is .... how am I gonna put that together...:confused:

any help will be more than welcome:guitar:

---

### Post by skychris on 2007-12-18
](*,) now I'm starting to loose my mind...

after several hours spinning around the net for a solution, it's getting even more confusing... so far here's what I get

-my adapter, whoever made it, seems to have the pl-2303 chip used by Prolific Inc.
-For whatever reason the driver source provided by Prolific Inc. doesn't compile...
-the patch found for this mysterious HL-340 adapter does not patch anything since it probably too old for my kernel

... and all that for a mere serial port emulator, protocol that has been around for more than  25 years now, wow, that's some progress #-o 

well enough sarcasm :) I will not give up and I hope that somewhere, somebody got it working and will be kind enough to send me some clues...

---

### Post by upsfeup on 2007-12-19
I'm having the exact same problem as you.

The closest to a solution I have come so far is:

```
sudo modprobe usbserial vendor=0x4348 product=0x5523
```

After doing this the usb converter is "recognized" and installed on ttyUSB0

The problem is that all text comes garbled and so unusable. Yes.. I'm using the same settings on both ends: 9600 8N1.

---

### Post by skychris on 2007-12-19
hi upsfeup,

I got in the same dead end, with the "modprobe" trick... the "ttyUSB0" is there but the soft I'm using finds nothing. it even tries to do a scan of the ports to see if it recognize anything... 
This forum is great but on top of the "How to's" that simply throw a bunch of obscure command line to solve a problem, which is good when it does, they should add a "how it works" so we can understand what's going on when it doesn't work by knowing "what does what where..."

keep your hopes up
cheers

---

### Post by upsfeup on 2007-12-19
> **skychris said:**
> hi upsfeup,

I got in the same dead end, with the "modprobe" trick... the "ttyUSB0" is there but the soft I'm using finds nothing. it even tries to do a scan of the ports to see if it recognize anything... 
This forum is great but on top of the "How to's" that simply throw a bunch of obscure command line to solve a problem, which is good when it does, they should add a "how it works" so we can understand what's going on when it doesn't work by knowing "what does what where..."

keep your hopes up
cheers

I'm now trying a different approach: recompile the kernel modules.

Of course that I'm now with a bunch of new errors. If I get somewhere I'll post here.

---

### Post by upsfeup on 2007-12-19
Ok... I was able to recompile the module but after playing a lit bit more, i'm not so sure if it is needed.

My testbench is a laptop with ubuntu.
The serial cable is connected to a desktop with serial port and WinXP
I try to communicate between them using minicom on ubuntu and putty on the windows Desktop.

I tried to play with the baudrates and guess what?
Setting minicom to 9600 and putty to 19200 does the trick!

Now.. the problem is to fix this specially as I need to use  115200 and simply halving this value on minicom does not solve the problem.

This is getting very weird...

---

### Post by skychris on 2007-12-20
some improvement but still no luck... Here's the actual status

"lsusb" gives me 
 ```
Bus 005 Device 004: ID 046d:0892 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 008: ID 4348:5523 WinChipHead USB->RS 232 adapter with Prolifec PL 2303 chipset
Bus 001 Device 007: ID 046d:c219 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

```

which is better than before...

somewhere in "dmesg" I get 
```
[14890.276000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[14890.440000] usb 1-1: configuration #1 chosen from 1 choice
[14890.440000] usbserial_generic 1-1:1.0: generic converter detected
[14890.444000] usb 1-1: generic converter now attached to ttyUSB0

```

Which is good as well although I'm not sure that the "generic" is appropriate...

the outcome of this command
```
 ls -al /dev/ttyU*

```

gives me
```
crw-rw---- 1 root dialout 188, 0 2007-12-20 13:50 /dev/ttyUSB0

```

which I actually no idea what it means... 

the problem is that I'm not trying to connect to a standard device like a modem or a mouse, but to a telescope. an Meade LX90 with an Autostar pad and KStars to try to pilot it...

does somebody could tell me with the info I gave on my serial port if it could work properly or do I have to look into KStars for the reason why I can't get a connection..

Thanks 

Chris

---

### Post by upsfeup on 2007-12-20
Got it!

The  pl2303 cannot be used. 

The actual device is a Ch341 that didn't had any drivers written. But I found them in

[http://article.gmane.org/gmane.linux.usb.devel/57633](http://article.gmane.org/gmane.linux.usb.devel/57633)

Now I have access to all baudrates.

[Edit]
There seems to be yet another patch that might be better:

[http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/5111b7f7ce20a634](http://groups.google.com/group/fa.linux.kernel/browse_thread/thread/5111b7f7ce20a634)

I'll try it tomorrow.

---

### Post by DiViDe on 2008-01-17
hi! i have the same problem, i'm new to linux and i don't know how to do these things... do you have an update on this?

---

### Post by skychris on 2008-02-11
- bump -

close to 900 people read it and only 9 replies.. :( does anybody have more info on this adapter ?

---

### Post by kizmat on 2008-02-14
There's a patch that adds the ch341.ko driver to linux source 2.6.22.
[http://lwn.net/Articles/246334/](http://lwn.net/Articles/246334/)

run it against linux-source-2.6.22 package
* cd /usr/src/linux-source-2.6.22
* patch -p1 < [path_of_your_patch]
* cp /boot/config-2.6.22-14-generic /usr/src/linux-source-2.6.22/.config
* make menuconfig (select CONFIG_USB_SERIAL_CH341, under "Device driver -> usb support -> usb serial converter support -> usb winchiphead ch341 single port serial driver"

I didn't want to build the whole kernel modules so I did
* make drivers/usb/serial/ch341.ko
* cp drivers/usb/serial/ch341.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/
* add "/lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/ch341.ko: /lib/modules/2.6.22-14-generic/kernel/drivers/usb/serial/usbserial.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/core/usbcore.ko" to /lib/modules/2.6.22-14-generic/modules.dep
* Make it load on boot -> echo ch341 >> /etc/modules
* To load it, modprobe ch341

Hope it helps, and looking forward to this incorporating into the next version 

ksc

---

### Post by skychris on 2008-02-19
Thanks a lot Kizmat,

that's exactly what I was looking for, I came across this ch341 patch but as I've never patched my kernel and I only found the source code for this ch341, I didn't really know what to do with it. I'll try to do it and post the result here.

---

### Post by aggie on 2008-02-22
Sorry but I'm really new to linux and i'm now sure what you did to make it work.

I have the same cable and I need to get this to work.

What can I do if I don't want to recompile the kernal?

I'm not sure what your instructions are and where do I get drivers/usb/serial/ch341.ko

can I copy the paste the code you have once I get my hands on the drivers/usb/serial/ch341.ko file?

thanks

---

### Post by cdcase on 2008-02-23
For those still stumped, check out my post regarding the same topic here. It's got the driver as well as step by step instructions on how to get the cable working.

[http://ubuntuforums.org/showpost.php?p=4390820&postcount=27](http://ubuntuforums.org/showpost.php?p=4390820&postcount=27)

---

### Post by kevmitch on 2008-02-24
I'm not sure I have the exact solution to your problem, but here is what I know.

I picked up a usb->serial converter from The Source in Canada and I determined that it was prolific based on looking in Device manager in windows after installing the driver. With this knowledge, I found that the kernel (2.6.23 anyway) has a driver for prolific converters. The module is called pl2303. This is probably more appropriate than the generic module it looks like your system is choosing (though don't quote me on that). In any case, try to load the pl2303 module using

modprobe pl2303

If you can't load this module it is either because a) it doesn't exist in your kernel version or b) Ubuntu doesn't compile it in the stock kernel (I use Debian so I don't know for sure). To solve the first problem you could try upgrading to the most recent kernel version linux-image-2.6.24-1-amd64 or linux-image-2.6.24-1-686 for 32 bit. To solve the second problem, you'll have to recompile the kernel itself with the module enabled. If this turns out to be the case, reply and I'll give instructions.

Once you have the module loaded, you should see the device file appear in the /dev directory. Just about any piece of hardware has a device file and programs use this file to interact with the hardware. The idea is that all the vendor specific stuff is wrapped inside the module which knows how to correctly communicate with the device and then provides a device file which is a more general interface. This way programs (such as kstars) don't have to know that you're using a prolific usb->serial converter. They just need to know the location of the device file of your serial port. 

The command 

ls -l /dev/ttyU* 

just gives you the names of the various device files that match that pattern. Using the pl2303 module, you will most likely get the same result from this command which is telling your that the device file is 
/dev/ttyUSB0. You need to tell kstars to look here for your telescope. Since I don't have a telescope myself, and am not terribly familiar with kstars, I can't be 100% sure, but I think you'll want to the "Devices" Menu and select "Configure INDI". Then you'll want to put /dev/ttyUSB0 in the "Telescope port" field.

---

### Post by kevmitch on 2008-02-25
Ooops, sorry I missed the second page before my post. Looks like its not quite the prolific module you're after after all.

---

