---
title: "o2 Micro, SmartCardBus reader"
date: 2005-02-28
forum: Hardware &amp; Laptops
---

### Post by mirtux on 2005-02-28
Hi,
   i have problem regarding a digital media card reader on my Acer Travelmate laptop. Does anybody of you had this device functioning? This is what i get with **lspci**

 ```

0000:02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay Controller
0000:02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay Controller
0000:02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx MultiMediaBay Accelerator
0000:02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay Controller

``` 

Thanks for help,
MC

---

### Post by cory-79 on 2005-03-23
Same problem here !
```

0000:02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay Controller 
0000:02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay Controller 
0000:02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx MultiMediaBay Accelerator
 0000:02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3 SmartCardBus MultiMediaBay Controller 
``` 

Anyone know hot to make them work ?

---

### Post by mirtux on 2005-03-24
Hi,
  i've mada a comprehensive search through the net but still nothing... 

but we'll continue...

Regards,
MC

---

### Post by mirtux on 2005-03-24
I've asked O2micro about a possible linux driver.... i'll post here the reply....

Regards,
MC

---

### Post by cory-79 on 2005-03-30
Tnx for any info!

---

### Post by remedy on 2005-04-03
Hello, 
Is there any news to this thread? I have the same card and would really like to get it working. 

Thanks!

---

### Post by mirtux on 2005-04-04
Hi,
  this is the mail i've received from O2Micro:

[i] "We are going to work on releasing a Linux driver for the flash media
 reader.  We are very busy with several other projects as well.  As for
 publicly available documentation, we are not able to release any at this
 time."[/i]

He told me that he put me in the drived update list, so don't worry when i'll know something i'll put it here! ;)

Regards,
MC

---

### Post by VictorE on 2006-03-22
Has anyone had a update on this issue?  I would like to see if I can get my internal card reader to work with 5.1

---

### Post by VRWarper on 2006-03-28
*bump* I'm also interested in an update if any. I'm surprised that there is still so little about this card reader.

---

### Post by krko7365 on 2006-04-24
[QUOTE=VictorE]Has anyone had a update on this issue?  I would like to see if I can get my internal card reader to work with 5.1[/QUOTE]

So... I guess we will have to reverse-engineer the device. Anyone knows where to start? I am willing to pitch in if I can be of any help. Would be nice to get the thing working finally.
Chris

---

### Post by lifeempowered.com on 2006-05-07
I'm definately in on this one too, have Averatec 3320 EH-1 with this device and would like to be able to access my pics without plugging my camera in every time!  I'm not a super genius when it comes to reverse engineering but will see what I can do and post any results...

---

### Post by jeff_sadowski on 2006-06-20
Good news and bad news

First the good news

I found a driver for this device.
[http://www.musclecard.com/sourcedrivers.html](http://www.musclecard.com/sourcedrivers.html)

under
 O2Micro Smartcardbus PCMCIA Smartcard Reader
[ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz](ftp://scrdriver:scrdriver@209.19.104.194/Linux/O2Micro_PCMCIA_SCR_203_Linux_Kernel26_OpenSource.tar.gz)


Now the bad news

Well maybe not bad for yall using ubuntu your probably using an older kernel
but for me using the 2.6.16 kernel the pcmcia structures have changed and I'll have to hack a bit before I can get these drivers working

I did a make in the kernel module directory and got error messages like so
/root/test/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:205: error: unknown field ‘attach’ specified in initializer
/root/test/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:206: error: unknown field ‘event’ specified in initializer
/root/test/OZSCR_2.0.3_Kern_2.6/src/ozscrlx-2.6.13/ozscrlx.c:207: error: unknown field ‘detach’ specified in initializer

and saw some articles mentioning the relevent changes in pcmcia_driver stucture

it looks like .attach has been replaced with .probe
.detach with .remove

and .event has been moved out of this structure into the unified event handler
(I have no idea what this is and how to use it)

I'm sure some others that have more experiance with writing device drivers than me could solve these issues in a jiffy but this is going to take me a while and I'll have to recrute some more experianced people to help.

I tried a quick replace and built a module when I tried loading I got these errors in my dmesg

ozscrlx: Unknown symbol pcmcia_deregister_client
ozscrlx: Unknown symbol pcmcia_register_client

So those need fixed also

I found information on these changes here
[http://lists.infradead.org/pipermail/linux-pcmcia/2005-September/002604.html](http://lists.infradead.org/pipermail/linux-pcmcia/2005-September/002604.html)
and
[http://lists.infradead.org/pipermail/linux-pcmcia/2005-September/002612.html](http://lists.infradead.org/pipermail/linux-pcmcia/2005-September/002612.html)

if someone can help me out building it correctly I would greatly appriciate the help thanks.

Jeff Sadowski

---

### Post by jeff_sadowski on 2006-06-20
Oh I forgot to mention to install the drivers you'll need to get 
pcsclite from [http://pcsclite.alioth.debian.org/](http://pcsclite.alioth.debian.org/)
it built and installed with no issues for me

---

### Post by LiquidStranger on 2006-06-26
I have an Acer Travelmate C300 with the O2 Micro cardreader, but installing pcsclite failed:
```
marc@ubuntop:~/1_downloads/pcsc-lite-1.3.1$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

Couldn't find something useful in the config.log mentioned, but then i'm kind of a noob concerning Linux...
Any help would be appreciated.

---

### Post by MurdocTD on 2006-08-21
To Jeff:
I found [this]("http://gentoo-wiki.com/HARDWARE_Gentoo_Acer_Travelmate_803LCi_Manual#Smartcardreader") howto. Maybe this helps with your 2.6.16 Kernel as well.



```
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I fixed this problem by installing the package "g++" under Ubuntu 6.06. This installs also the linux-headers. Maybe this is the problem.

I managed to compile the driver but I can't mount my MMC card. After loading the Kernel module dmesg shows this:

```
[17193900.084000] OZSCRLX version: O2Micro SmartCardBus Reader for kernel 2.6 (above 2.6.13)
[17193900.084000] OZSCRLX init_ozscrlx: major num: 123
[17193900.084000] OZSCRLX init_ozscrlx: function complete!
```

But there are no messages that a new device has been found when I put the card into the slot. 
Does anyone know how to access the card from here?
I have an Acer Travelmate 8100 with the card reader slot at the front of the Laptop.

Okay, just found my problem with accesing the card:
I forgot to install the pcscd daemon. Now I got a little further. The daemon gives me this error message:

```
pcscdaemon.c:258:main() pcscd set to foreground with debug send to stderr
pcscdaemon.c:249:main() using new config file: /etc/reader.conf
readerfactory.c:1097:RFInitializeReader() Attempting startup of O2Micro SmartCardBus Reader 00 00.
readerfactory.c:939:RFBindFunctions() Loading IFD Handler 2.0
ifdhandler.c:121:IFDHCreateChannel Lun 0, Channel F10000

ctapi.c:106:CT_init CT_init enter
ctapi.c:119:CT_init Try to open channel dev/ozscrlx
ctapi.c:136:CT_init CT_init exit (-11)
readerfactory.c:1132:RFInitializeReader() Open Port F10000 Failed (/dev/ozscrlx)
readerfactory.c:1014:RFUnloadReader() Unloading reader driver.
readerfactory.c:250:RFAddReader() O2Micro SmartCardBus Reader init failed.
pcscdaemon.c:463:main() pcsc-lite 1.2.9-beta9 daemon ready.
```

Has anyone got this far and has found a solution?

---

### Post by BungaMan on 2006-09-08
If it is any comfort to you, I get the same result :(

```
$ sudo pcscd -d -a -f
pcscdaemon.c:258:main() pcscd set to foreground with debug send to stderr
readerfactory.c:1097:RFInitializeReader() Attempting startup of O2Micro SmartCardBus Reader 00 00.
readerfactory.c:939:RFBindFunctions() Loading IFD Handler 2.0
readerfactory.c:1132:RFInitializeReader() Open Port F10000 Failed (/dev/ozscrlx)
readerfactory.c:1014:RFUnloadReader() Unloading reader driver.
readerfactory.c:250:RFAddReader() O2Micro SmartCardBus Reader init failed.
pcscdaemon.c:463:main() pcsc-lite 1.2.9-beta9 daemon ready.
```

---

### Post by pep100 on 2006-09-25
I have a Travelmate C301. When I tried to install Muscle Smartcard reader driver, I got the following:

Found pcsclite 1.2.9 in /usr/lib
Kernel includes directory not found

Any Ideas??? Thanks

---

### Post by SpookyET on 2007-12-26
I have a TravelMate 8100 as well. I want to make it work as well.

---

### Post by excogitation on 2008-03-19
So did anybody ever get it to work?

---

