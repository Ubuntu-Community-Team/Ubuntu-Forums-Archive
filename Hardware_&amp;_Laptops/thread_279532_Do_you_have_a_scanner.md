---
title: "Do you have a scanner?"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by Haegin on 2006-10-18
Hi,
I am trying to create a program to install scanners on ubuntu but I need some hardware details so if you want your scanner to be supported then please can you post the make and model of your scanner and the output of lsusb. If you can point out the scanner then please do.
Currently the script is only supporting usb scanners but if its popular then I may try and add parallel scanners later.

Example (Note - I kinda made it up as the scanner isn't on this pc):

Epson CX6600
```

$ lsusb
Bus 003 Device 002: ID 0402:5602 ALi Corp. 
Bus 003 Device 001: ID 04b8:0813 Epson Corp.  <-This is the scanner
Bus 001 Device 026: ID 05fe:1010 Chic Technology Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

```

---

### Post by _simon_ on 2006-10-18
My scanner worked out of the box so not sure if you want / need this info but I know a few people have posted with the same scanner and they couldn't get it working.

Make: Canon, Canoscan LIDE 20

Bus 001 Device 003: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20

---

### Post by weemikey on 2006-10-18
michael@home:~$ lsusb
Bus 004 Device 002: ID 04a5:1005 Acer Peripherals Inc. (now BenQ Corp.)
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U  <- this is my scanner
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 043d:0057 Lexmark International, Inc. Z35 Printer
Bus 001 Device 001: ID 0000:0000

I am totally frustrated as I have NEVER been able to mount this scanner - even though Xsane site says it is.](*,) 

Any help at all is welcome!

---

### Post by Haegin on 2006-10-19
Brilliant, thanks both of you. If you want your scanner supported then keep it all coming!

---

### Post by Haegin on 2006-10-24
Acer 640bu

```
:~$ lsusb
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 005: ID 04a5:207e Acer Peripherals Inc. (now BenQ Corp.) Prisa 64 0BU
Bus 002 Device 001: ID 0000:0000
```

---

### Post by kent41 on 2006-10-24
I have a Canon LiDE 60 scanner working great on Breezy 5.10.

Here are some post that help me get my scanner going.
[URL="http://www.ubuntuforums.org/showthread.php?t=106647&highlight=LiDE+60"]
help #1 [/URL]  [ help #2]("http://www.zepan.org/index.php/2006/01/29/the-canon-lide-60-and-ubuntu-dapper/")


```

kent@GPS-3:~$ lsusb
Bus 004 Device 003: ID 04a9:221c Canon, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

---

### Post by blitzer on 2006-10-24
I have a UMAX Astra 3400 USB working great with Dapper Drake :mrgreen: 

```
$ lsusb
Bus 001 Device 004: ID 1606:0060 Umax [hex] Astra 3400U

```

Glad to help with anything for Ubuntu 8)

---

### Post by Haegin on 2006-11-09
Brilliant, thanks everybody who has posted so far. blitzer did you have to do anything to get the scanner working?

---

### Post by edmonds on 2006-11-09
hi
my scanner is a CanoScan 4600F. i don't know how to get it to work. It probably needs to be turned on but i can't see how without a progam to do it.
lsusb:
Bus 001 Device 004: ID 04a9:221b Canon, Inc.
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 002: ID 04a9:1093 Canon, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

The Device Manager recognises it as a Canoscan under a Hub. but seems to have no information on it.

I also have a Canon Printer so lsusb may  be showing  that??
tom

---

### Post by edemark on 2006-11-09
will this program work only for usb scanner or you plan to support parport scanners as well?
I have a genius colorpage vivid pro II 
I would love to make it work

---

### Post by mrojas73 on 2006-11-10
I would love to get my scanmaker 5950 working! I will post the my lsusb result when I get home tonight!

---

### Post by DOD1951 on 2006-11-10
This is a CannonScan LiDE 500F which does not work or at least does not get detected by Xsane :( The one last thing to get working before dumping Windows totally!

Bus 005 Device 006: ID 04a9:221f Canon, Inc.

---

### Post by mrojas73 on 2006-11-10
Here is the output for my Scanmaker 5950:

mrojas@Aspire5601:~$ lsusb
Bus 005 Device 002: ID 05da:30d8 Microtek International, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
mrojas@Aspire5601:~$ 

I hope you can help us and good luck!

---

### Post by minorthreat on 2006-11-11
HP Photosmart C3180 - An all-in-one scanner/copier/printer

```

Bus 002 Device 002: ID 03f0:5611 Hewlett-Packard

```

---

### Post by Haegin on 2006-11-11
[quote=tom]I also have a Canon Printer so lsusb may be showing that??[/quote]
Can you please unplug the printer and redo the lsusb otherwise I cannot tell which is the scanner.
[quote=edemark]will this program work only for usb scanner or you plan to support parport scanners as well?[/quote]
I hope to support parallel scanners as well in the future but currently I do not know how to set them up in sane and I don't have one to hand to use.

---

### Post by trachycarpus on 2006-11-11
I have only today installed Ubunto(my first linux) so any program which helped me get my HP Scanjet3770 working would be a great help.
Peter

---

### Post by Dogmeat on 2006-11-11
Lexmark X1270

Bus 001 Device 001: ID 0000:0000
Bus 002 Device 005: ID 043d:00ff Lexmark International, Inc.
Bus 002 Device 003: ID 043d:007a Lexmark International, Inc.
Bus 002 Device 004: ID 043d:007d Lexmark International, Inc. <-- Scanner
Bus 002 Device 002: ID 0424:0140 Standard Microsystems Corp.
Bus 002 Device 001: ID 0000:0000


This is a multifunction printer. I got the printer part working perfectly by following [this HOWTO]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer"). However, I couldn't find any references to getting the scanner part working.

Since you're adding support to lots of USB scanners, maybe you can give me a few pointers for me to get this scanner working with SANE on Dapper?

EDIT: Nevermind, all I had to do was edit /etc/sane.d/lexmark.conf and change the address. However xsane detects the scanner as a X1100. It makes some loud noises on like it's gonna start scanning but then it doesn't work :(. Any tips?

---

### Post by wendavid on 2006-11-16
my canoscan lide 30 worked right out of the box.

~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 001 Device 001: ID 0000:0000

---

### Post by carla on 2006-11-30
Canon Canoscan 8400F: 
*Bus 001 Device 007: ID 04a9:221e Canon, Inc. CanoScan 8400F*

---

### Post by matchstich on 2006-12-15
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 003: ID 04a5:2060 Acer Peripherals Inc. (now BenQ Corp.) Prisa 620U+/640U
Bus 003 Device 001: ID 0000:0000


been trying for a while now to get this to work, thanls

---

### Post by stig on 2006-12-18
Mine is a Hewlett-Packard ScanJet 5370c on USB and it does not work yet - still trying!

$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:0701 Hewlett-Packard ScanJet 5300c/5370c
Bus 002 Device 001: ID 0000:0000

---

### Post by eugenia on 2006-12-28
Bus 004 Device 004: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

Are you still working on this? 

This scanner worked perfectly with Breezy but jams with Dapper and Edgy. It still works with XP Professional so the problem is definitely Dapper/Edgy related.  Unfortunately the people at Ubuntu  won't do anything about it.

"To fix this, you'll need to upgrade to one of the latest CVS snapshots
and to compile/install on your own - sorry.
Gerhard Jeager"

Anyone know how to do this?](*,)

---

### Post by drew1313 on 2006-12-28
drew@Area51linux:~$ lsusb
Bus 005 Device 004: ID 03f0:1305 Hewlett-Packard ScanJet 4570c
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:b002 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 06a3:8021 Saitek PLC 
Bus 003 Device 001: ID 0000:0000  
drew@Area51linux:~$ 

I am new to Linux/ubuntu, never could get this scanner to work..](*,)

---

### Post by drew1313 on 2006-12-28
> **drew1313 said:**
> drew@Area51linux:~$ lsusb
Bus 005 Device 004: ID 03f0:1305 Hewlett-Packard ScanJet 4570c
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:b002 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 06a3:8021 Saitek PLC 
Bus 003 Device 001: ID 0000:0000  
drew@Area51linux:~$ 

I am new to Linux/ubuntu, never could get this scanner to work..](*,)
It works fine in widows: I even tried running xsane as root, no luck. shame, it's a good scanner!

---

### Post by LeslieL on 2006-12-29
I have a Canoscan 4400F that doesn't work. Xsane looks for a scanner and says "no devices available". I tried running xsane as root with the same result.
lsusb result:
Bus 004 Device 003: ID 04a9:2228 Canon, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Hope this is useful.

---

### Post by getafix123 on 2006-12-29
Bus 005 Device 083: ID 04b8:0815 Seiko Epson Corp.

Epson AcuLaser CX11NF Multi Function ..

---

### Post by captainpotato on 2007-01-02
Epson RX530 (works fine using the Epson drivers, converted using Alien, on Ubuntu 6.06):

Bus 004 Device 005: ID 04b8:081a Seiko Epson Corp.

Epson Perfection 610 (works fine using Kubuntu 6.06, no extra drivers needed):

Bus 001 Device 004: ID 04b8:0103 Seiko Epson Corp. Perfection 610

---

### Post by LocStock on 2007-01-03
Hey,

Mine is a Hewlett-Packard ScanJet G3010 on USB, can't get it to work... :-?

Bus 001 Device 003: ID 03f0:4205 Hewlett-Packard

---

### Post by ohrock on 2007-01-05
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 03f0:0211 Hewlett-Packard    <-  HP G85
Bus 001 Device 006: ID 04c5:1096 Fujitsu, Ltd    <- Fujitsu 5110EOX2
Bus 001 Device 001: ID 0000:0000

---

### Post by stig on 2007-01-15
Canon LIDE 25, 1200x2400 dpi

:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04a9:2220 Canon, Inc.
Bus 002 Device 001: ID 0000:0000

Got it last week and very pleased! Posted the following in the Beginner's Forum:

As a non-techie who was unable to get his previous HP scanners working with Ubuntu, I thought it was worth mentioning here that my new Canon flatbed scanner arrived yesterday and is working perfectly as far as I can tell.

It is a Canon LIDE 25 flatbed colour scanner (1200 x 2400 dpi) - bought in the UK from Amazon for 38 UK pounds including free delivery. It uses LEDs and there is no separate power cord - all the power needed for the LEDs comes through the USB cable.

I have sane, xsane and gocr software packages installed through Synaptic from the repository. I simply powered up the PC, connected the scanner to the PC by its USB cable, opened xsane from the Applications | Graphics menus - and scanned! After all the failures with HP scanners this is wonderful.

xsane seems to have lots of features - more than I need. And gocr let me convert an image to text easily and fairly accurately. Grrrreat!!:p

---

### Post by gorg on 2007-01-19
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 05d8:4005 Ultima Electronics Corp.   <<<<mem48u flatbed scanner
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 047d:101f Kensington PocketMouse Pro
Bus 001 Device 002: ID 03f0:3402 Hewlett-Packard
Bus 001 Device 001: ID 0000:0000
it is the ultima aka mem48u
i followed instructs found on the forums but it doesn't work
thanks

---

### Post by evilc on 2007-01-20
This is mine:  clive@clive:~$ lsusb   Bus 005 Device 001: ID 0000:0000    Bus 002 Device 001: ID 0000:0000    Bus 004 Device 003: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U  Bus 004 Device 001: ID 0000:0000    Bus 003 Device 002: ID 04fc:0015 Sunplus Technology Co., Ltd   Bus 003 Device 001: ID 0000:0000   Bus 001 Device 001: ID 0000:0000      The scanner is a Diamond View but shows up as Acer did work once but no more since powered off?

---

### Post by The Iron Curtain on 2007-01-21
Hi,
I have a Canon Canoscan LiDE 25

```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04a9:2220 Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  

```

I just plugged it in and I have no Idea where to go from there, but I wil continue searching the forums.

Hope this helps :D

EDIT: I just noticed [this post]("http://ubuntuforums.org/showpost.php?p=2015456&postcount=30") and it worked. Thank you!

---

### Post by ACGilbert on 2007-01-24
Hi,
I've got a Microtek ScanMaker 4900 which xsane doesn't see and which the Sane Project lists as unsupported.

$ lsusb
Bus 005 Device 004: ID 05e3:0760 Genesys Logic, Inc. Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 005: ID 05da:30d9 Microtek International, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

Thanks,
AC

---

### Post by BLTicklemonster on 2007-01-26
Go for it!!! I want to use the scanner on my Lexmark X1270.

```
$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 001 Device 006: ID 043d:00ff Lexmark International, Inc. 
Bus 001 Device 005: ID 043d:007d Lexmark International, Inc. 
Bus 001 Device 004: ID 043d:007a Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by BLTicklemonster on 2007-01-26
> **Dogmeat said:**
> Lexmark X1270

Bus 001 Device 001: ID 0000:0000
Bus 002 Device 005: ID 043d:00ff Lexmark International, Inc.
Bus 002 Device 003: ID 043d:007a Lexmark International, Inc.
Bus 002 Device 004: ID 043d:007d Lexmark International, Inc. <-- Scanner
Bus 002 Device 002: ID 0424:0140 Standard Microsystems Corp.
Bus 002 Device 001: ID 0000:0000


This is a multifunction printer. I got the printer part working perfectly by following [this HOWTO]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer"). However, I couldn't find any references to getting the scanner part working.

Since you're adding support to lots of USB scanners, maybe you can give me a few pointers for me to get this scanner working with SANE on Dapper?

EDIT: Nevermind, all I had to do was edit /etc/sane.d/lexmark.conf and change the address. However xsane detects the scanner as a X1100. It makes some loud noises on like it's gonna start scanning but then it doesn't work :(. Any tips?

I show this

#usb /dev/usb/scanner0
usb 0x043d 0x007c

and have these to chose from

Bus 001 Device 006: ID 043d:00ff Lexmark International, Inc. 
Bus 001 Device 005: ID 043d:007d Lexmark International, Inc. 
Bus 001 Device 004: ID 043d:007a Lexmark International, Inc. 


how would I know which to use? 00ff, 007d or 007a?

---

### Post by radtek on 2007-01-27
[FONT="Arial"]Samsung multifunction laserprinter SCX 4100 

Downloaded the drivers from the website but only the printer works. No scanner shows up.
```
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 004: ID 04e8:3413 Samsung Electronics Co., Ltd
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
A working scanner would be *awesome*[/FONT]

---

### Post by BLTicklemonster on 2007-01-27
I wonder what the status of this is at this time?


Has anyone tried this: [http://www.lexmark.com/lexmark/sequentialem/home/0,7070,204816596_659668505_0_en,00.html](http://www.lexmark.com/lexmark/sequentialem/home/0,7070,204816596_659668505_0_en,00.html) ???

---

### Post by magician on 2007-01-28
Hi!

I am using an older scanner: 

Totalscan Express  (from Storm Technologies)
 type dp66vs.

Storm is out of business since 1998.

Please can you help me out, I found nothing on this scanner, Xsane No devices available

$ lsusb
Bus 001 Device 001: ID 0000:0000  

Regards
Magician:D

---

### Post by Haegin on 2007-01-28
I am still working on this but it is going slowly as I haven't had much spare time recently. I am currently working on a script that will identify scanners from the lspci codes and set them up on sane so if they are not supported on sane then I probably wont be able to help but please by all means submit your details as I may be able to find a sane driver you have overlooked.

---

### Post by hakan69 on 2007-01-28
Hi
I have an Epson Perfection 1250 Photo. It works right out of the box.
Lsusb gives:
Bus 001 Device 004: ID 04b8:010f Seiko Epson Corp. Perfection 1250

Regards/Hakan

---

### Post by Aggienator on 2007-01-28
Canon 3200F (doesn't work!)

```
:~$ lsusb
Bus 001 Device 004: ID 03f0:0004 Hewlett-Packard DeskJet 895c
Bus 001 Device 003: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 006: ID 0781:0002 SanDisk Corp. SDDR-31 ImageMate II CompactFlash Reader
Bus 005 Device 004: ID 0409:005a NEC Corp. 
Bus 005 Device 005: ID 05dc:a640 Lexar Media, Inc. 
Bus 005 Device 002: ID 04a9:2216 Canon, Inc. CanoScan 3200F
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
```

If you produce something that will make it work I'll be VERY grateful!

---

### Post by amanita on 2007-01-29
Epson Perfection V100

Should work - according to sane (not yet for me).


```


:~$ lsusb
Bus 002 Device 003: ID 046d:c03f Logitech, Inc. 
Bus 002 Device 002: ID 046d:c512 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04b8:012d Seiko Epson Corp.     [COLOR="Red"]<--scanner [/COLOR]
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  


```

---

### Post by beaulanger on 2007-01-29
Visioneer Onetouch 8920 USB

beau@beau-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04a9:1094 Canon, Inc. PIXMA iP3000x Printer
Bus 001 Device 001: ID 0000:0000  
[COLOR="Red"][B]Bus 002 Device 003: ID 0461:0371 Primax Electronics, Ltd Visioneer Onetouch 8920 Scanner
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 0000:0000  [/B][/COLOR]
Bus 005 Device 006: ID 046d:c20d Logitech, Inc. 
Bus 005 Device 004: ID 05e3:0606 Genesys Logic, Inc. 
Bus 005 Device 001: ID 0000:0000

---

### Post by miseljt on 2007-01-29
HP PSC-1600

```
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:4811 Hewlett-Packard 
Bus 003 Device 003: ID 0aec:3050 Neodio Technologies Corp. ND3050 8-in-1 Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000 
```

---

### Post by mrojas73 on 2007-02-08
Is he still working on the program, he hasn't reported back in a while.

---

### Post by Haegin on 2007-02-09
I am still working on it, albeit very slowly - I am learning perl as I go though I will try and work on it a load tonight.

Sorry I'm slow but life is rather busy at the moment.

---

### Post by JohnnyVW on 2007-02-12
OK, here's what I have:

Visioneer Onetouch 9020USB

johnny@ubuntujohnny:~$ lsusb
Bus 005 Device 002: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
**[COLOR="Red"]Bus 005 Device 003: ID 04a7:022c Visioneer [/COLOR]**
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 03f0:1104 Hewlett-Packard DeskJet 959c
Bus 003 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 05e3:0502 Genesys Logic, Inc. GL620USB GeneLink USB-USB Bridge
Bus 004 Device 001: ID 0000:0000 

This is one of three things keeping me from deleting XP.  ;)

---

### Post by mrojas73 on 2007-02-13
> **Human Prototype said:**
> I am still working on it, albeit very slowly - I am learning perl as I go though I will try and work on it a load tonight.

Sorry I'm slow but life is rather busy at the moment.
Hey...we undersand,  I just wanted to make sure you were a live!!!!

Anyways, I am glad you are still working on it.

---

### Post by MeduZa on 2007-02-16
Canon Pixma MP530 all in one:

$sane-find-scanner -q

found USB scanner (vendor=0x04a9 [Canon], product=0x1712 [MP530]) at libusb:002:002

PD: the command sane-find-scanner -q show only the info for the scanner

---

### Post by vratnica on 2007-02-21
CanoScan FB630P

muris@muris-desktop:~$ lsusb
Bus 005 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 005 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

---

### Post by joey on 2007-02-21
```

Bus 005 Device 007: ID 03f0:4205 Hewlett-Packard 

```

HP Scanjet G3010  (someone else reported it here).  Not supported by anyone it seems.

---

### Post by heyheyhey on 2007-02-25
I have a Canoscan LiDE 500F and lsusb: givesBus 006 Device 002: ID 16d8:5523  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 008: ID 04a9:221f Canon, Inc. 
Bus 005 Device 005: ID 07c4:3260 Datafab Systems, Inc. 
Bus 005 Device 003: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:109d Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 046d:c225 Logitech, Inc. 
Bus 004 Device 004: ID 046d:c221 Logitech, Inc. 
Bus 004 Device 002: ID 046d:c223 Logitech, Inc. 
Bus 004 Device 003: ID 0db0:6855 Micro Star International 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c518 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

One of those two canon inc is it. the other is a conan pixima iP 90 printer. your call which is which. If you could get this working I would be free of windoze.

Cheers for your effort
josh

---

### Post by Princey on 2007-02-27
lsusb
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
Bus 002 Device 003: ID 04f2:0111 Chicony Electronics Co., Ltd
Bus 002 Device 005: ID 03f0:0604 Hewlett-Packard DeskJet 840c
Bus 002 Device 004: ID 0458:400a KYE Systems Corp. (Mouse Systems)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0bda:0103 Realtek Semiconductor Corp.
Bus 001 Device 002: ID 03f0:4105 Hewlett-Packard <<<HP ScanJet 4370
Bus 001 Device 001: ID 0000:0000

Still struggling to get it to work.

---

### Post by bratliff on 2007-02-28
I need to mount my hp 3970 scanjet flatbed scanner.

bob

---

### Post by SoundBytes on 2007-03-15
> **heyheyhey said:**
> I have a Canoscan LiDE 500F and lsusb: givesBus 006 Device 002: ID 16d8:5523  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 008: ID 04a9:221f Canon, Inc. 
Bus 005 Device 005: ID 07c4:3260 Datafab Systems, Inc. 
Bus 005 Device 003: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:109d Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 046d:c225 Logitech, Inc. 
Bus 004 Device 004: ID 046d:c221 Logitech, Inc. 
Bus 004 Device 002: ID 046d:c223 Logitech, Inc. 
Bus 004 Device 003: ID 0db0:6855 Micro Star International 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c518 Logitech, Inc.  
Bus 002 Device 001: ID 0000:0000  

One of those two canon inc is it. the other is a conan pixima iP 90 printer. your call which is which. If you could get this working I would be free of windoze.

Cheers for your effort
josh


Greetings,

I also have a CanoScan LiDE 500F that I would like to get working, and I'm also pretty green to Linux (and Ubuntu). I ran lsusb and the return I got was 'Bus 005 Device 004: ID 04a9:221f Canon, Inc. ' I have no other Canon devices, so I'm sure that is the one. I hope this helps.  
Thanks for all you are doing,
SoundBytes

---

### Post by Z.K. on 2007-03-17
I am not sure if you are still looking for scanners, but mine is a Visioneer OneTouch 7600 USB and I have never been able to get it to work in Linux.  

lsusb
Bus 005 Device 001: ID 0000:0000

//This is my scanner
Bus 004 Device 003: ID 04a7:0211 Visioneer OneTouch 7600 Scanner   

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 0000:0000

---

### Post by teaker1s on 2007-03-17
04a9:221f CanoScan LiDE 500F.
ID 04a9:109d Canon iP90

look here
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=CanoScan+LiDE+500F&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=CanoScan+LiDE+500F&bus=any&v=&p=)[http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=CanoScan+LiDE+500F&bus=any&v=&p=]("http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon&model=CanoScan+LiDE+500F&bus=any&v=&p=")
your scanner isn't currently supported by sane.
Canon do a linux driver?

---

### Post by Calvarez3 on 2007-03-17
I'm having the same problem as LeslieL 

I have a Canon CanoScan 4400F, it is recognized in device manager but I can not get any program to recognize it.

Bus 005 Device 002: ID 0424:2504 Standard Microsystems Corp. 
Bus 005 Device 003: ID 04a9:2228 Canon, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by MoebusNet on 2007-03-21
HP Scanjet 4370 not supported in SANE. I've tried the 3900 installation instructions but so far no go.

output from $ lsusb

Bus 004 Device 004: ID 03f0:4105 Hewlett-Packard 
Bus 004 Device 003: ID 0781:5406 SanDisk Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 001: ID 0000:0000

---

### Post by teaker1s on 2007-03-21
If I remember I tempted a"trust" scanner into life by altering the config file of a similar model with vendor and product id and usb bus location.
The sane project guys are friendly from my experience , if your scanner isn't listed jot them a email

---

### Post by harmony on 2007-03-24
Artec Ultima 2000 not working

```
~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:092b Logitech, Inc. 
Bus 001 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner
Bus 001 Device 001: ID 0000:0000
```

---

### Post by tarcar54 on 2007-03-28
Hi,
I have a scanner ...
here is the lsusb output :

Bus 001 Device 004: ID 04a9:2215 Canon, Inc. CanoScan 3000/3000F/3000ex

I'd like to use it !

Thanks a lot, Carlo.

---

### Post by tarcar54 on 2007-03-28
Hi,
I olso have an usb disk ...
Bus 001 Device 005: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
it appears in the usb listing for few seconds, then disappeared ...
I works fine with other OS.
Thanks for help !

---

### Post by bratliff on 2007-03-30
I installed the sane hp scanjet 3900 package from soundforge. My scanner is recognized but when I use xsane I get the error-failed to open device:libusb:003:002: Access to resource has been denied.

ratliff

---

### Post by MoebusNet on 2007-03-30
I found this in a thread "Problem with my scanner HP Scanjet 3970" by nashnash. Sorry, but I don't know how to link to his thread in the forum. It got my HP Scanjet 4370 working with Sane!

Permissions are probably your problem still. To figure out which device is your scanner, open device manager:
System > Administration > Device Manager
The tree probably has several USB controllers, each with devices under them. Dig down until you find your scanner. Under your scanner is "USB Raw Device Access." Select this, and look at the Advanced tab on the right. One of the entries should be linux.device_file which will show you the filename for this device. On my system, my 3970 is /dev/bus/usb/001/002. Yours is probably different. So, on my system, I type in a terminal
Code:

sudo chmod a+w /dev/bus/usb/001/002

which does the trick for me.

Eric
Attached Thumbnails
Click image for larger version Name: Screenshot-Device Manager.png Views: 16 Size: 98.7 KB ID: 18802

---

### Post by hummingbird on 2007-04-02
Hiddy...

Well, this is a first response for me, so forgive the blunders.  I have a scanner and lsusb tells me this:

> Bus 005 Device 002: ID 04b8:011c Seiko Epson Corp. Perfection 3200
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

Hmm, hope that did the trick. 
Caio,

---

### Post by sharke on 2007-04-03
Epson CX4900 Multi Function Printing works fine only scans as root.
The bus seems to change with reboot . I am using Fiesty 64.

Bus 005 Device 012: ID 04b8:082b Seiko Epson Corp. 


regards
Sharke

---

### Post by 11hjpphty76lkjj on 2007-04-03
Something for everyone to keep in mind.  

Most HP Multifunction devices; printers/scanner/copiers are already supported by [HPLIP]("http://hplip.sourceforge.net") .  HP ScanJet devices are not supported by HPLIP, although some of them may be supported by the [sane backend]("http://www.sane-project.org/sane-supported-devices.html"). 

HPLIP is developed by HP and as such we do a large amount of testing with the actual devices to ensure a stable and well development application.

Just my two cents..

A

---

### Post by dj9866 on 2007-04-04
HP Scanjet G4050

dj@dj-laptop:~$ lsusb
Bus 003 Device 008: ID 03f0:4605 Hewlett-Packard 
Bus 003 Device 007: ID 03f0:6004 Hewlett-Packard DeskJet 5550
Bus 003 Device 003: ID 058f:6387 Alcor Micro Corp. 
Bus 003 Device 004: ID 046d:c518 Logitech, Inc. 
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by el_poderoso on 2007-04-04
I have an Epson V100 Photo and I'm having dependancy hell. The only scanner software (other than Xsane) that I have to work with is an RPM file. If I had a neat little deb file, I'd be a real happy camper.  Mitch

mitch@mitch-desktop:~$ lsusb
Bus 001 Device 006: ID 04b8:012d Seiko Epson Corp.
Bus 001 Device 004: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003Bus 001 Device 005: ID 03f0:1604 Hewlett-Packard DeskJet 940c
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000
mitch@mitch-desktop:~$

---

### Post by ralphrj on 2007-04-05
Visioneer 7100 USB

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 05e3:0700 Genesys Logic, Inc. SIIG US2256 CompactFlash Card Reader
Bus 001 Device 004: ID 03f0:c202 Hewlett-Packard 
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 002: ID 04a7:0229 Visioneer 
Bus 001 Device 001: ID 0000:0000

---

### Post by Giana on 2007-04-10
here is mine

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04b8:0808 Seiko Epson Corp. 
Bus 001 Device 001: ID 0000:0000  

Unfortunately, my EPSON Stylus CX5400 does not (yet) scan....

G.

---

### Post by noynac on 2007-04-10
> **Human Prototype said:**
> Hi, I am trying to create a program to install scanners on ubuntu but I need some hardware details so if you want your scanner to be supported then please can you post the make and model of your scanner and the output of lsusb....

> **mrojas73 said:**
> Is he still working on the program, he hasn't reported back in a while.

> **Human Prototype said:**
> I am still working on it, albeit very slowly - I am learning perl as I go though I will try and work on it a load tonight. Sorry I'm slow but life is rather busy at the moment.

I wondered if anyone knows when this program will be available? My Epson 3490 scanner will not work under Feisty, and this program would be quite helpful to me.

Thanks!

---

### Post by kingtsy on 2007-05-03
Hi,

Mine is a canoscan 3000 ex with usb. I haven't make it work on ubuntu since 6.06 up to now 7.04.

Bus 005 Device 002: ID 04a9:2215 Canon, Inc. CanoScan 3000/3000F/3000ex
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 0000:0000 

Thanks in advance very much.:)

---

### Post by nanotube on 2007-05-03
mine's a canoscan 620U or 620FBU or something like that (don't have it hooked up or even in same room at the moment, since it doesn't work with linux ...

edit: ah, it's Canoscan FB 620U (google to the rescue).

still don't have it hooked up, so no lsusb for now...

---

### Post by BLTicklemonster on 2007-05-03
There mere fact that this thread even exists just goes to show you what a sorry state Hardware is in these days. In their Myopia, the neglect to see the world around them.

"Linux? Ain't that Lucy Van Buren's little brother on Peanuts?"

---

### Post by cezfx on 2007-05-12
Hiya

Bus 004 Device 003: ID 04a9:2216 Canon, Inc. CanoScan 3200F <my scanner>
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

:confused:   Just tried Inkscape on Ubuntu and it's sooo much better than when it runs on Windows XP; would love to be able to use my scanner to get images into it!

sincerely

Ceri

---

### Post by cbaez55 on 2007-05-25
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:4205 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
This is the information I get with lsusb

---

### Post by Princey on 2007-05-25
> **cbaez55 said:**
> Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:4205 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
This is the information I get with lsusb

To those with HP Scanners with ID 03f0:4105, if you're having problems, I can point you to the right direction to get it working. For those with ID 03f0:4205 I think it uses the same SANE drivers as the 03f0:4105. Just to be sure, the HP ScanJet 43xx, 53xx uses the same drivers as the ScanJet 3700. Please verify if your scanners are indeed part of the group that I can point you to the right thread to get your scanner working.

---

### Post by xzero1 on 2007-05-25
Bus 003 Device 002: ID 04f2:0112 Chicony Electronics Co., Ltd KU-8933 Keyboard with PS/2 Mouse port
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c506 Logitech, Inc. MX-700 Cordless Mouse Receiver
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 045e:00bd Microsoft Corp. Fingerprint Reader
Bus 001 Device 006: ID 03f0:0a01 Hewlett-Packard <-- Printer
Bus 001 Device 005: ID 03f0:3002 Hewlett-Packard <-- Scanner
Bus 001 Device 004: ID 050d:0233 Belkin Components 
Bus 001 Device 001: ID 0000:0000  

Note: I also have wintv-go pci card and this is the device that the xsane pics up as my "scanner".
Thanks for all your hard work.

---

### Post by hummingbird59 on 2007-05-27
Canon PIXMA  MP 600 - downloaded driver from canon au website but xsane still cannot see it.  Howver, I am totally new to this so it may be something I am doing wrong.  Any help much appreciated as this is the ONLY problem I have with Linux as of today!:p


EDIT:  Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04a9:1718 Canon, Inc. 
Bus 001 Device 005: ID 03f0:3502 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000


THANK YOU!

---

### Post by Haegin on 2007-06-06
Hi all,

Sorry about the delay in this project getting off the ground - it was interrupted by a gap year trip to the Philippines and trying to get my own small business going.

I should have a semi workable version going by the end of the week but as I do not have access to any scanners (other than my Epson CX6600) I will be relying on user feedback to let me know what this tool works with and what scanners that should work don't work.

At the moment I am only implementing the epson backend. This is partly because I have an Epson scanner and so I can test it but also because the epson backend seems to work very well for most of the tested scanners according to the SANE website ([http://www.sane-project.org/sane-backends.html#S-EPSON](http://www.sane-project.org/sane-backends.html#S-EPSON)).

---

### Post by Aggienator on 2007-06-07
Hope you had a great time in the Philippines, look forward to trying out the development!

---

### Post by jbman on 2007-06-07
```
Bus 003 Device 012: ID 04a9:220c Canon, Inc. CanoScan D1250U2
```

Canon, Inc. CanoScan D1250U2

---

### Post by tarmacadam on 2007-06-10
I have an epson perfection 4490 photo. 

I really appreciate your effort here, it will be very helpful [for everyone]. If you'd like some help in your endeavor, please contact me. 



```

lsusb =>

**Bus 005 Device 004: ID 04b8:0119 Seiko Epson Corp. **
Bus 005 Device 002: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c50a Logitech, Inc. 
Bus 002 Device 003: ID 05ac:020b Apple Computer, Inc. 
Bus 002 Device 002: ID 05ac:1003 Apple Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  

```

Thanks, 
Ben

---

### Post by Haegin on 2007-06-10
> **tarmacadam said:**
> I have an epson perfection 4490 photo. 

I really appreciate your effort here, it will be very helpful [for everyone]. If you'd like some help in your endeavor, please contact me. 

Thanks, 
Ben

Hi Ben,

I will definitely be trying to get your scanner to work in the near future but (despite it being an Epson) it is not covered by the epson SANE backend but by the iscan backend (which is made by Epson I think) which requires some extra libraries installed. I will be concentrating on the epson backend first as I can test this one better but the work on this is almost completed I think.

I hope to build a deb for the iscan library which will install all the files to the correct locations on Ubuntu (from some forum threads it appears they sometimes get put in /usr/local/etc but this may be because people are using checkinstall.

Once I have this deb available on the internet I will be able to proceed and add support for devices requiring the iscan backend. If anybody has packaging experience and wishes to package iscan (according to the Ubuntu packaging guidelines) please contact me as packaging is something I have not done in the past.

I will be working on the interface design later as the current code is command line based only (but can successfully install many epson scanners that are supported by the epson backend automatically) and will be releasing the first beta as soon as it is possible to install a scanner through a graphical user interface. This will hopefully be today provided pygtk isn't too confusing. :D

---

### Post by Haegin on 2007-06-10
Right,

I have the first testing version ready and it should work with all the USB scanners listed on the SANE site as working with the epson backend. The complete list is below. For more information check the README file in the archive. Please please please flood me with feedback on how it works with your scanner etc. I will begin working on more backends ASAP.

I hope to have a much better interface ready for the next release but I'm currently still struggling with pygtk and list views so if anybody feels like arranging a half hour session on IRC to give me some help understanding the fine art of pygtk and tree views please contact me.

Hope you all enjoy this and that it helps some of you.

NOTE - THIS *ONLY* WORKS FOR THE SCANNERS LISTED BELOW AND EVEN THOSE ARE POSSIBLY UNCERTAIN. ANYTHING ELSE IS A **GUARANTEED NO**.

_**Scanners:**_
Perfection 636U
Perfection 610
Perfection 640
Perfection 1200U
Perfection 1240
Perfection 1640
Perfection 1650
Perfection 1660
Perfection 2400
Perfection 2450
Perfection 3200
Perfection 4870
Perfection 4990
Expression 1600
Expression 1680
CX-3200
CX-3600
CX-3800
CX-4200
CX-4600
CX-4800
CX-5200
CX-5400
CX-6400
CX-6600
RX-500
RX-600
RX-452
AcuLaser CX-11

---

### Post by BLTicklemonster on 2007-06-12
Great work. Still waiting for the Lexmark, maybe one day someone will figure out how to make one work in linux.

---

### Post by joseph_chapman on 2007-06-20
jchapman@jchapman-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0a82:2002 Syscan 
Bus 001 Device 005: ID 413c:8000 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
jchapman@jchapman-laptop:~$ sane-find-scanner -q
found USB scanner (vendor=0x0a82, product=0x2002, chip=LM983x?) at libusb:001:006

---

### Post by guitarchris on 2007-06-20
Hi, happy to help especially if it gets my scanner going ;) - the only reason I keep W2k  (damn!).
 This is a multifunction device. The printer worked straight off and it copies OK but the scanner is not recognised despite all the entries in sane being present and correct.

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04b8:0818 Seiko Epson Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046e:5251 Behavior Tech. Computer Corp. 
Bus 001 Device 001: ID 0000:0000

---

### Post by kathmary on 2007-06-24
~$ lsusb
Bus 004 Device 002: ID 04a9:2219 Canon, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

This is a CanoScan 9950F.  Cost me a pretty penny and would really like to use it with Ubuntu.
Wish you luck sorting it all out!

---

### Post by pediatracancun on 2007-06-25
I've an Epson CX4900 scanner, which is not supported by xsane.
In order to use it, with Ubuntu Feisty and Ubuntu Gusty hurd 1, I do the following:
- the scanner is on and connected to a USB port.
- in a terminal write: lsusb
- this gives us two parameters, ie:: Bus 002 Device 004: ID 04b8:082b Seiko Epson Corp.
- in terminal write: sudo chmod 666 /dev/bus/usb/x/y - where x=Bus (002 in this example) and Y=Device=004.

after this execute the XSane program and your scanner will work during this session.
Next time you restart the computer you will have to repeat this procedure.

Hope this helps to you.  :KS

---

### Post by Arenlor on 2007-06-26
> **Dogmeat said:**
> Lexmark X1270

Bus 001 Device 001: ID 0000:0000
Bus 002 Device 005: ID 043d:00ff Lexmark International, Inc.
Bus 002 Device 003: ID 043d:007a Lexmark International, Inc.
Bus 002 Device 004: ID 043d:007d Lexmark International, Inc. <-- Scanner
Bus 002 Device 002: ID 0424:0140 Standard Microsystems Corp.
Bus 002 Device 001: ID 0000:0000


This is a multifunction printer. I got the printer part working perfectly by following [this HOWTO]("http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark+printer"). However, I couldn't find any references to getting the scanner part working.

Since you're adding support to lots of USB scanners, maybe you can give me a few pointers for me to get this scanner working with SANE on Dapper?

EDIT: Nevermind, all I had to do was edit /etc/sane.d/lexmark.conf and change the address. However xsane detects the scanner as a X1100. It makes some loud noises on like it's gonna start scanning but then it doesn't work :(. Any tips?

Bus 003 Device 010: ID 043d:00ff Lexmark International, Inc. 
Bus 003 Device 009: ID 043d:007d Lexmark International, Inc. 
Bus 003 Device 008: ID 043d:007a Lexmark International, Inc. 

Same printer/scanner, got the printer working, and I'm willing to beta/alpha anything for you, this is my secondary printer, I have another if i need to.

---

### Post by fanihi on 2007-06-27
Hi,
I am running ubuntu feity fawn and I have a Canon LiDE 80 flatbed scanner I'd like to use but I haven't been able to get it to work with ubuntu. Here are some info that I've collected based on some of the web "scans" I've done so far.

$ lsusb
Bus 002 Device 002: ID 0518:0002 EzKEY Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:2214 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  

$ scanimage -L
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2214 [CanoScan], chip=GL841) at libusb:001:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

I have added the following entry in /etc/sane.d/genesys.conf:
usb 0x04a9 0x2214

I don't think I have a backend driver installed. I'm not sure but genesys seems to be the proper choice based on the chip=GL841 shown above.

I really would appreciate any help to get my scanner working.

Thanks in advance,
John:(

---

### Post by Haegin on 2007-06-28
> **fanihi said:**
> Hi,
I am running ubuntu feity fawn and I have a Canon LiDE 80 flatbed scanner I'd like to use but I haven't been able to get it to work with ubuntu. Here are some info that I've collected based on some of the web "scans" I've done so far.
<SNIP>


Hey John,

Sorry to bring bad news but your scanner isn't supported by the sane-project so I am unable to help you. So far you have done as much as you can as the genesys driver will be the right one when they get around to supporting it.

The homepage for the driver is here: [http://www.meier-geinitz.de/sane/genesys-backend/](http://www.meier-geinitz.de/sane/genesys-backend/). You could try asking there to see if it is being worked on.

Good Luck

--------

To anybody else interested I will be bringing out a new version as soon as I have got the new GUI code sorted out. If anybody can help me with GTK Cell Renderers PLEASE PM me and let me know. I will be really grateful.

---

### Post by tico on 2007-06-29
> **DOD1951 said:**
> This is a CannonScan LiDE 500F which does not work or at least does not get detected by Xsane :( The one last thing to get working before dumping Windows totally!

Bus 005 Device 006: ID 04a9:221f Canon, Inc.

Same with me. Still waiting for a solution to make my scanner work.

---

### Post by venik212 on 2007-07-25
I know this is an old post, but it is a new problem for me: I need to support (on kubuntu) a UMAX uc1260, which is a parallel scanner.

Thanks

---

### Post by Haegin on 2007-07-26
> **venik212 said:**
> I know this is an old post, but it is a new problem for me: I need to support (on kubuntu) a UMAX uc1260, which is a parallel scanner.

Thanks

According to the SANE website your scanner isn't supported (only the scsi version is) so it would require writing an entirely new driver for your scanner.

The list of UMAX scanners supported by SANE is here: [http://www.sane-project.org/sane-mfgs.html#Z-UMAX](http://www.sane-project.org/sane-mfgs.html#Z-UMAX)

**For more general use with scanners:**

In general, if you have a scanner you want to get working then you need to check the SANE website [here]("http://www.sane-project.org/sane-mfgs.html") and see if your scanner is supported. If it is then you need to see what backend it uses and then look at the configuration file for that backend. For information on the backends use the link in the last column of the table of supported scanners which is a link to the manpage for that backend. Alternatively you can simply use man sane-<backendname> if you have the backend installed on your computer.

The USB scanners will use UDEV rules to make them writeable by the scanner group when hotplugged so if you have permission problems (can only use the scanner as root) then check the UDEV rules in /etc/udev/rules.d/45-libsane.rules to make sure there is an entry for your scanner with the correct manufacturer ID and product ID (these can be checked using lsusb).

Try all this first before posting in this thread for help. Also remember to google for your scanner and Linux to see if there is another guide for another distro that you can adapt. All my experience is with USB scanners (though I am happy to give parallel and scsi scanners a try) so I may not be able to help so much with them.

Good luck!

---

### Post by venik212 on 2007-07-27
Thanks for this very helpful and fast response.

---

### Post by ronny_d on 2007-07-27
I am considering buying a Canon Lide 25 for Ubuntu Feisty Fawn 7.04 desktopversion with usb 1.1 
(so no laptop). I hope then you also support that one although i cannot give you specs now... (i am still considering to buy that one); yet i very much hope when i buy it it already works just like that without hassle, simply plug in and that's it: "automatically". I am trying to find out somewhere else on this forum whether the scanner i named is o.k. for my system.

---

### Post by venik212 on 2007-07-27
I connected a Canonscan N650U USB scanner to my computer, after installing Kooka, Sane and Xsane.  The system sees the scanner and identifies it correctly, but I still cannot scan.  I looked for a relevant file in /usr/local/etc/plustek but that entire directory is not there, for some reason.
I know I am missing something trivial, but what is it?

---

### Post by venik212 on 2007-07-27
I guess I am still really a newbie, since I do not know how to follow the following instructions from the Sane installetion procedure:
"Then do the make step and after that as root user perform the make install  step."
(from Gerhard J&#65533;ger <gerhard@gjaeger.de>)
I have installed Sane, Xsane, Plustek and the sane backend stuff.

---

### Post by MotHaiBa on 2007-08-08
Hi, I am running Fiesty Fawn. I have a Diamond View (Mitsubishi 650U). The scanner is on line 2.

When I startup XSane, the following message appears "Failed to open device `snapscan:libusb:003:003' Invalid argument.

The scanner works correctly in Win XP.

$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U
Bus 003 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I really would appreciate any help to get my scanner working.

Thanks in advance :)

---

### Post by Lektorvis on 2007-08-14
Hi 

My CanoScan 3000F doesn't work with SANE either, so I'll send you a whole lot of good karma if you can make it work.


$ lsusb
Bus 001 Device 002: ID 04a9:2215 Canon, Inc. CanoScan 3000/3000F/3000ex
Bus 001 Device 001: ID 0000:0000  

Get back if you need further information.

---

### Post by regomodo on 2007-08-14
yes x3 and none of them work

Visioneer 4400
Epson 4180
Nikon Coolscan V ED

---

### Post by venik212 on 2007-08-23
I guess we shall never be able to use those Canon scanners with Linux/SANE.
That is why I still run WINDOWS.

---

### Post by jimaring on 2007-09-10
new@laptop:~$ lsusb
Bus 001 Device 003: ID 045e:00a4 Microsoft Corp.
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 006: ID 04b8:012d Seiko Epson Corp.
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:7404 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000

---

### Post by jingo811 on 2007-09-14
My scanner worked right away in Dapper 6.06 I just pressed Acquire in GIMP and it started scanning.  With Feisty 7.04 it opens up this Xsane program that have to complicate things for the worse and then freeze up everytime I want to scan.

```
~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 04a9:2204 Canon, Inc. CanoScan FB630U
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

Can anybody give me tips on where to read about troubleshooting matters for scanners in Feisty?

---

### Post by flickerfly on 2007-09-14
Visioneer Strobe XP 100 

```
Bus 004 Device 003: ID 04a7:0425 Visioneer 
```

This is, I believe, an early revision that Visioneer no longer supports.

---

### Post by jjalocha on 2007-09-14
Epson Stylus CX3900 Printer/Scanner

```

Bus 003 Device 005: ID 04b8:082f Seiko Epson Corp. 

```

EDIT: I forgot to mention that I got this one working on Feisty with the following:
[http://ubuntuforums.org/showpost.php?p=2656092&postcount=15](http://ubuntuforums.org/showpost.php?p=2656092&postcount=15)

---

### Post by TeaSwigger on 2007-09-17
Good old HP ScanJet 5370c, working beautifully under Windows 2kpro and not at all with ubuntu / kubuntu. xsane claims there are no devices. Every now and then it may show in a lsusb. Here's a lucky grab:

```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 022: ID 03f0:0701 Hewlett-Packard ScanJet 5300c/5370c
Bus 001 Device 001: ID 0000:0000
```

The only thing left I need windows for. ;)

---

### Post by Julian David Pitt on 2007-09-17
Canoscan 3200F

Has anyone managed to get this working?
Output of lsusb

julian@feisty:~$ lsusb
Bus 005 Device 007: ID 04cc:1520 Philips Semiconductors
Bus 005 Device 005: ID 04a9:2216 Canon, Inc. CanoScan 3200F
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 06a3:ff17 Saitek PLC
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 413c:2003 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000

This scanner is shown in the "device manager"? but cannot be seen in either xsane or Kooka?

---

### Post by dedieko on 2007-09-21
Scanner UMAX Astra 4100

```
Bus 002 Device 002: ID 0461:038c Primax Electronics, Ltd 
```

---

### Post by eeried on 2007-09-21
I'd like to buy Epson Perfection V200 but it isn't on the sane-project list. However that list doesn't seem to be updated, which is a problem.

Is that scanner supported?

I'm looking for a scanner able to scan slides and negatives. There isn't much choice if you can't spend above 100$/€.

---

### Post by Julian David Pitt on 2007-09-22
> **jjalocha said:**
> Epson Stylus CX3900 Printer/Scanner

```

Bus 003 Device 005: ID 04b8:082f Seiko Epson Corp. 

```

EDIT: I forgot to mention that I got this one working on Feisty with the following:
[http://ubuntuforums.org/showpost.php?p=2656092&postcount=15](http://ubuntuforums.org/showpost.php?p=2656092&postcount=15)

I tried the above link but it didn't work for me I'm afraid but then I am a noob so I might have done something wrong I guess?

---

### Post by kelvin spratt on 2007-09-22
i have a canon 25 lite does not work in Feisty detects ok just does not scan works perfect in Elive Gem.

---

### Post by ecr959 on 2007-09-22
I know I'm very late replying to this post, but I just read it for the first time , 10 minutes ago.
I am using Ubuntu 7.10 (gutsy) and I do daily upgrade/updates.  This is an Acer laptop.
My scanner is unsupported, according to the SANE website.  It is a HP Scanjet 4600.

----------------
eddie@ecrbook:~$ lsusb
Bus 005 Device 004: ID 5986:0100  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 047d:1032 Kensington 
Bus 002 Device 004: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 006: ID 03f0:3005 Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
eddie@ecrbook:~$ 
-----------------
I wish lots of success for the original poster,  I would like to get some feedback from him/her.   Thanks.

---

### Post by jjalocha on 2007-09-22
Julian, maybe you could post some more information about what didn't work exactly, or where you're stuck. I'd love to help you out. Don't be afraid to ask "nooby" questions. I have lots of them too! (You can send me a private message if you prefer.)

---

### Post by paulororke on 2007-10-02
I have a Canoscan 3000ex.  xsane says it doesn't see it and I can't use it.

#lsusb
Bus 002 Device 009: ID 04a9:2215 Canon, Inc. CanoScan 3000/3000F/3000ex

I'd love to see this work!

---

### Post by Julian David Pitt on 2007-10-03
> **jjalocha said:**
> Julian, maybe you could post some more information about what didn't work exactly, or where you're stuck. I'd love to help you out. Don't be afraid to ask "nooby" questions. I have lots of them too! (You can send me a private message if you prefer.)

I would love to post the info but currently I cannot even get in to my system as it seems to think it is returning from hibernation and cannot find the image to boot, help?

---

### Post by antonr on 2007-10-08
Hi,
I have a Canoscan LiDE 25

$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04a9:2220 Canon, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I am on Kubuntu 7.04.

The first app I've tried is Kooka, and it detects the scanner as 
plustek:libusb:002:002 Canon LiDE25
but when it does a "preview" or "final scan", the result image is blank.
The scanner does not make any noise as expected.
(It works in WinXP and it makes noises when scanning).
The software shows a progress bar as if it is scanning, however.

I'll keep investigating.
Thanks for your effort.

---

### Post by ebattleon on 2007-10-16
garvin@garvin-desktop:~$ lsusb
Bus 004 Device 005: ID 0930:6532 Toshiba Corp.
Bus 004 Device 004: ID 046d:08cc Logitech, Inc.
Bus 004 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 004: ID 03f0:0a01 Hewlett-Packard *
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

*this is my scanner though not supported by sane:(

---

### Post by Mordac85 on 2007-10-17
I have an HP 5370c, which I have been able to working in Gentoo and SuSE, but still can't get it going in kubuntu.  scanimage -L detects it, but sane can't see it.  Hope it helps, something should be easier to use than what we have now.

Bus 003 Device 003: ID 03f0:0701 Hewlett-Packard ScanJet 5300c/5370c

---

### Post by ebattleon on 2007-10-18
Hi

garvin@garvin-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 006: ID 03f0:0a01 Hewlett-Packard [COLOR="Sienna"](Scanjet 2400c Scanner)[/COLOR]
Bus 003 Device 005: ID 04a5:2331 Acer Peripherals Inc. (now BenQ Corp.) [COLOR="Sienna"](Benq 5160c Scanner)[/COLOR]
Bus 003 Device 003: ID 046d:08cc Logitech, Inc.
Bus 003 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

both are unsupported by sane:(

---

### Post by collgra on 2007-10-20
my scanner is:

gary@Ubuntuabit:~$ lsusb
Bus 007 Device 003: ID 03f0:2405 Hewlett-Packard

Thanks, I would love to have a driver.

Gary

---

### Post by NIT006.5 on 2007-11-18
> **ecr959 said:**
> I know I'm very late replying to this post, but I just read it for the first time , 10 minutes ago.
I am using Ubuntu 7.10 (gutsy) and I do daily upgrade/updates.  This is an Acer laptop.
My scanner is unsupported, according to the SANE website.  It is a HP Scanjet 4600.


I have the same problem with the same scanner (and there are quite a few posts on the forum about the HP Scanjet 4600 being unsupported). Up until recently, I was using XP in VirtualBox to connect to my scanner, but since an upgrade somewhere along the line (could have been the Gutsy upgrade), I have just noticed that my VirtualBox doesn't allow XP to connect to the USB scanner now - i.e. unless someone can help with drivers for this, I might as well throw it away. 

I'm having a really hard time explaining to my boss why Linux (being a superior system) doesn't support a scanner that worked in Windoze. :( And anyone vaguely aware of the economic situation in Zimbabwe will understand that going out and buying a new scanner just isn't an option here....

I've checked forums everywhere and I've even tried filing a complaint with HP - I'm just not making any progress and I keep coming to the same dead end: the scanner just isn't supported. So if anyone can help with this, it would be truly and greatly appreciated!

---

### Post by gregfulkerson on 2007-11-19
Bus 001 Device 011: ID 04a9:2215 Canon, Inc. CanoScan 3000/3000F/3000ex


Thanks!
Greg

---

### Post by gregfulkerson on 2007-11-19
my advice to some of you is to install virtualbox, load up windows as a virtual machine, and use your scanner through this. I am able to do it, but I would prefer integration with my host ubuntu system.

---

### Post by sambucuself on 2007-11-23
lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 031: ID 043d:00ff Lexmark International, Inc. 
Bus 001 Device 026: ID 043d:007d Lexmark International, Inc. 
Bus 001 Device 025: ID 043d:007a Lexmark International, Inc. 
Bus 001 Device 002: ID 05d5:8001 Super Gate Technology Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

Lexmark Scanner/Printer X1270

can't get the sane backend to compile on amd64

HELP!

---

### Post by maxwellcom on 2007-11-24
CanoScan LiDE 90

```
Bus 005 Device 004: ID 04a9:1900 Canon, Inc. 
```

Can't get it to work...

---

### Post by oldcdr on 2007-11-25
I have a Microtek Scanmaker 4800 which worked perfectly on Ubuntu 7.04 but does not work on 7.10.  When I go to the Applications menu and select XSane I get the error message:

Fail to open device 'smb3840:libusb:004:002':  Acces to resource has been denied.

XSane documentation says my scanner should work.

TIA

---

### Post by ubifrost on 2007-11-26
Bus 004 Device 006: ID 04b8:0838 Seiko Epson Corp. 
EpsonDX7450

The printer works fine.

---

### Post by oldcdr on 2007-11-28
Microtek ScanMaker 4800

It is detected but I can't get access to it.  Any suggestions?

---

### Post by subs on 2007-11-28
here u are

> Bus 002 Device 002: ID 05d8:4009 Ultima Electronics Corp. Umax Astraslim

---

### Post by JhonQ on 2007-11-28
jhonny@jhonny-desktop:~$ lsusb
Bus 005 Device 005: ID 0204:6026
Bus 005 Device 004: ID 04a5:2137 Acer Peripherals Inc. (now BenQ Corp.)
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:7604 Hewlett-Packard
Bus 001 Device 005: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
Bus 001 Device 001: ID 0000:0000

BenQ Scanner 5250C

---

### Post by chaiwalla on 2007-11-29
I have a Canon D1250U2

 -desktop:~$ lsusb
[COLOR="Red"]**Bus 004 Device 005: ID 04a9:220c Canon, Inc. CanoScan D1250U2[/COLOR]**[/COLOR]
Bus 004 Device 004: ID 046d:0a01 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 0458:0003 KYE Systems Corp. (Mouse Systems) Genius NetScroll+
Bus 002 Device 001: ID 0000:0000  
 

It would be great to get it working with Ubuntu

---

### Post by bonejob on 2007-12-22
bonejob@pavel-chekov:~$ lsusb
Bus 002 Device 007: ID 04a9:10bc Canon, Inc. 
Bus 002 Device 005: ID 059f:0351 LaCie, Ltd 
Bus 002 Device 003: ID 0409:0059 NEC Corp. HighSpeed Hub
***[COLOR="Red"]Bus 002 Device 002: ID 04a9:2219 Canon, Inc.[/COLOR]*** 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


My scanner (highlighted in red) is a Canon CanoScan 9950F - a fairly high-end scanner that so far is not supported by SANE. That is one of the chief reasons I still keep Windows around. If I want to scan - something I do fairly often - no choice but to scroll down to the bottom of the GRUB menu and boot up Vista. If you can change that situation, I for one would be most grateful. For some odd reason, NONE of Canon's higher-end scanners is supported!

---

### Post by shearroller on 2007-12-26
I too have a MIcrotek 4800 but like the others with this scanner I'm denied access to the resource.

Bus 002 Device 003: ID 05da:30cf Microtek International, Inc. ScanMaker 4800

---

### Post by ymo on 2007-12-30
Ubuntu 7.10

I have a Genius ColorPage-Vivid 1200X USB scanner.

Bus 001 Device 004: ID 0458:201d KYE Systems Corp. (Mouse Systems) ColorPage-Vivid 1200 X

I found it in /etc/udev/rules.d/45-libsane.rules:

SYSFS{idVendor}=="0458", SYSFS{idProduct}=="201d", MODE="664", GROUP="scanner"

but Xsane reports "Failed to open device `gt68xx:libusb:001:004': Invalid argument.

<Edit> Fixed once I discovered that all I needed to do was copy the ccd569.fw (found it on my Windows box - easier than finding the CD) file into /usr/share/sane/gt68xx

On the other hand my SCSI Canon LiDE FB620S needed nothing more than the creation of a symbolic link before Xsane would use it.

/dev/scanner -> /dev/sg3

---

### Post by swells5 on 2008-02-07
_**Canon 4400F scanner**_

Bus 005 Device 005: ID 04a9:2228 Canon, Inc. <<<< [COLOR="Red"]SCANNER[/COLOR]
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 003 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 003 Device 001: ID 0000:0000

good luck with your endeavor, and thanks
steve

---

### Post by Neeewbeee on 2008-02-16
My HP Scanjet 4600 is found by sane-find-scanner byt not by xsane.

Bus 005 Device 003: ID 03f0:3005 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0d8c:0102 C-Media Electronics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 03f0:3e02 Hewlett-Packard 
Bus 001 Device 004: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000

---

### Post by TimTow on 2008-03-10
/$ lsusb
Bus 002 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 04a9:1728 Canon, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

i have a canon mx310, printer recognized, no scanner

---

### Post by Orion2000za on 2008-03-14
> **antonr said:**
> Hi,
I have a Canoscan LiDE 25

$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04a9:2220 Canon, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I am on Kubuntu 7.04.

The first app I've tried is Kooka, and it detects the scanner as 
plustek:libusb:002:002 Canon LiDE25
but when it does a "preview" or "final scan", the result image is blank.
The scanner does not make any noise as expected.
(It works in WinXP and it makes noises when scanning).
The software shows a progress bar as if it is scanning, however.

I'll keep investigating.
Thanks for your effort.
Unless you solved it already:
install scanbuttond by 
sudo aptitude install scanbuttond
from command line run
scanbuttond -r 1000000

Then try Kooka again, it should now work

---

### Post by Orion2000za on 2008-03-14
> **Neeewbeee said:**
> My HP Scanjet 4600 is found by sane-find-scanner byt not by xsane.

Bus 005 Device 003: ID 03f0:3005 Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0d8c:0102 C-Media Electronics, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 03f0:3e02 Hewlett-Packard 
Bus 001 Device 004: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000

do you get an output from command
scanimage -T ?

you might also try "sudo xsane", I had problems with having to use sudo myself with one scanner.

Sinclair

---

### Post by wordchisler on 2008-03-17
NeatReceipts Scanalizer
It is showing up as a Plustek in Ubuntu but XSane / Kooka can't find it.

---

### Post by silvanus2005 on 2008-03-23
I have a Canoscan LiDE 90, it„s detected when i run the command lsusb, but xsane don„t detect it.This the output when I run lsusb:
Bus 005 Device 006: ID 04a9:1900 Canon, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0566:3107 Monterey International Corp. 
Bus 002 Device 004: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by Princey on 2008-03-31
Guys, I did a fresh install of Hard Heron (Beta), opened up kooka and it complained about xsane not installed. Installed it and what a joy to know that my HP SCANJET 4370 worked perfectly. Now, that's good news.

---

### Post by Book 'em Dano on 2008-04-13
I have a Visioneer OneTouch 7100 usb connected scanner that is not recognized by SANE:(.  The following is the output of lsusb:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04a7:0229 Visioneer

---

### Post by Martje_001 on 2008-04-13
I've got an Canon Pixma MP150 :). It's recognized by sane, and everything (incl. buttons) is working.

---

### Post by SuporteTecnicoID on 2008-04-15
> **sambucuself said:**
> lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 031: ID 043d:00ff Lexmark International, Inc. 
Bus 001 Device 026: ID 043d:007d Lexmark International, Inc. 
Bus 001 Device 025: ID 043d:007a Lexmark International, Inc. 
Bus 001 Device 002: ID 05d5:8001 Super Gate Technology Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

Lexmark Scanner/Printer X1270

can't get the sane backend to compile on amd64

HELP!

HI,,,,

Look in my site, for procedure for install this Scanner and Printer X1270c LexMark:

[http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/](http://www.indexdata.com.br/Linux/Drivers/Impressoras/LexMark/)

Best Regards....

SuporteTecnicoID
[www.indexdata.com.br](www.indexdata.com.br)

---

### Post by mezzmerized17 on 2008-04-20
I have a Lexmark X1185 all-in-one.  

lsusb
Bus 003 Device 003: ID 0930:6540 Toshiba Corp. 
Bus 003 Device 002: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 043d:007b Lexmark International, Inc. 
Bus 001 Device 005: ID 043d:007c Lexmark International, Inc. 
Bus 001 Device 004: ID 043d:007a Lexmark International, Inc. 
Bus 001 Device 003: ID 058f:9360 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c21a Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

I assume that the 3 Lexmark entries are printer/scanner/copier, but I'm just guessing.

I know Lexmark and Linux are estranged, to say the least, but I hope this helps.

I am happy to give any info or test anything.

Thanks.

---

### Post by laluz on 2008-04-20
Bus 002 Device 007: ID 04c5:10fe Fujitsu, Ltd

---

### Post by nakah1 on 2008-04-25
I have Canon 4400F and are not working. Please help.

---

### Post by Richhard on 2008-04-29
I have a Brother DCP-130c Printer- Scanner combination.
Now anything is working :) after lot of tinker around.

Remark: 
the support from Brother is quite OK, *buntu is the problem!!
8.04 is absolutly disapointing, compared to Mandriva:
there you just click -> install the drivers + wrapper (from Brother)
and aything is perfect!!

---

### Post by lammergeir on 2008-05-12
I too have a Canon 3200F scanner. Running Hardy on AMD64 3800, and can only get scanner to work through a virtual machine.
Anyone actually managed to get it to work in Ubuntu?

---

### Post by desiretosee on 2008-05-14
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 007: ID 04a9:221f Canon, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I have also a canon Lide 500f scanner. It is pitty, that the company does not support driver for it. thanks for the asking and your effort to solve this problem.

---

### Post by editrix on 2008-06-10
An old but very good Plustek OpticPro 9636T that worked beautifully in Dapper, once I uncommented the appropraite line in /etc/sane.d/plustek_pp.conf, but no luck whatsover in Hardy.

---

### Post by Basket_Case on 2008-06-13
Lexmark X1270

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 043d:00ff Lexmark International, Inc. 
Bus 002 Device 004: ID 043d:007d Lexmark International, Inc. 
Bus 002 Device 003: ID 043d:007a Lexmark International, Inc. 
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Basket_Case on 2008-06-13
I can confirm the Lexmark X1270 scanner works OK under Xsane image scanner using Ubuntu 8.04, although I can't get the OCR to work in Xsane. Also managed, after much jiggery pokery to get the printer to using z600 driver

---

### Post by on4aa on 2008-06-21
It is a real deception that the excellent HP ScanJet 5400c is only very basically been supported by XSANE. For example, I cannot switch to grayscale scans in XSANE. This is due to the lack of a proper backend for this scanner.

A couple of years ago there was some development by reverse-engineering of a beta-version backend that I have not tried yet. See: [http://sourceforge.net/projects/hp5400backend/](http://sourceforge.net/projects/hp5400backend/)

Maybe you may also get some ideas from the "all-in-one" printer-scanners being supported at: [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

Here is the output:

ubuntu@ubuntu:~$ lsusb
Bus 005 Device 010: ID 041e:4045 Creative Technology, Ltd 
Bus 005 Device 009: ID 041e:4048 Creative Technology, Ltd 
Bus 005 Device 008: ID 03f0:1005 Hewlett-Packard ScanJet 5400c
Bus 005 Device 007: ID 041e:404b Creative Technology, Ltd 
Bus 005 Device 006: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 005 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 002: ID 0781:7460 SanDisk Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0baf:6112 U.S. Robotics FaxModem Model 5633
Bus 002 Device 002: ID 0463:ffff MGE UPS Systems UPS
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Many thanks in advance for your help!

Serge

---

### Post by eternity*7 on 2008-07-21
Have Mitsubishi Diamond View DV65OU scanner with Windows installation cd. and USB connection. How do I get it going with Ubuntu please? I'm a newbie!!!

---

### Post by zipperback on 2008-07-22
lsusb | grep Canon

Bus 001 Device 004: ID 04a9:2206 Canon, Inc. CanoScan N650U/N656U

This scanner worked out of the box for me under Ubuntu Hardy, I have not tried it with any other version of Linux.

- zipperback
:popcorn:

---

