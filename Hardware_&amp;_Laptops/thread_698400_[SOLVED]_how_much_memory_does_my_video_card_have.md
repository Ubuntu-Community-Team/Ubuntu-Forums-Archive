---
title: "[SOLVED] how much memory does my video card have?"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by dustman on 2008-02-16
hello!

I looked over the forums to find a way to see how much memory has the video card allocated. I have a laptop with an ATI Radeon Xpress 200M video card. I have 1.5 GB of RAM, and the computer uses 1.2 of it. So i suppose the video card takes the rest. I tried with "lshw", which returned:```
dustman@dustman-laptop:~$ sudo lshw
.... 
*-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
....

```
I couldn't figure out where i can find the video memory allocated :confused: . 
Anybody has any ideas?

Cheers!

Radu

---

### Post by oldsoundguy on 2008-02-16
I SERIOUSLY doubt that the on board chip is allocating and holding .3gb of ram.  Most likely 64mb .  Even the super high end plug in video cards for desktops have (currently) 512mb on board, and most non gamers are content with as low as 64mb of on board.

Check your bios.  You may get an answer there.

---

### Post by dustman on 2008-02-16
i did check my bios, and there's nothing there to be seen. I mean, there is nothing in the bios that tells that my video card has 64 MB (or more). I know that i have 1.5 GB of RAM, and the computer (in ubuntu and in wingoz) shows the same amount of RAM available: 1.2 GB. So in conclusion, the video card gets the rest. In vista and winxp, i can see that the video card has 256 MB RAM....my question is how can i see this sort of stuff in ubuntu? cause lshw doesn't show anything like that.

Cheers!

Radu

---

### Post by 444 on 2008-02-16
I don't think there is a way, aside from looking at the available system ram.

[http://phoronix.com/forums/showthread.php?t=5988](http://phoronix.com/forums/showthread.php?t=5988)


And yes, ATi HyperMemory can and often does take up 256.

---

### Post by oldsoundguy on 2008-02-16
if WinDOZE says it is sucking up 256, then 256 it is .. something else has to account for the difference ... what Ubuntu version are you running as some only recognize a certain amount of memory on board.

---

### Post by dustman on 2008-02-17
> **oldsoundguy said:**
> if WinDOZE says it is sucking up 256, then 256 it is .. something else has to account for the difference ... what Ubuntu version are you running as some only recognize a certain amount of memory on board.

i have Ubuntu 7.10, and the thing is that i'm not concerned about the RAM remaining for the computer to use. I'd like to play some games, and that's why i want to know how much RAM does my video card have. I remember that in Ubuntu 6.06, when i installed the proprietary drivers from ATI, i also got kinda of an application like a control panel for my video card, but now i don't remember what it was called. Perhaps that utility could tell me what i'm looking for?



[EDIT] Found that the ATI control panel can be installed by : "sudo apt-get install fglrx-control" , but it doesn't show how much allocated RAM  the video card has :( .

---

### Post by Yellow Pasque on 2008-02-17
I'm using the radeonhd driver and the command in bold shows what I have (in this case 128MB). I believe the proprietary fglrx driver makes a similar entry in the Xorg log, so try that command or maybe substitute grep memory. If that fails, open up the log and wade through it.

```
[dan@harvest Desktop]# **cat /var/log/Xorg.0.log | grep RAM**
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x7ffc000
(--) RADEONHD(0): **VideoRAM: 131072 kByte**
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x7ffc000
(II) RADEONHD(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0x7ffc000
(II) Initializing built-in extension XINERAMA
```

---

### Post by nilarimogard on 2008-02-17
Exactly 131072 kByte it says i have too, but my card suppose to have 256 mb, Ubuntu only sees 131 mb or what?

---

### Post by Yellow Pasque on 2008-02-17
> **nilarimogard said:**
> Exactly 131072 kByte it says i have too, but my card suppose to have 256 mb, Ubuntu only sees 131 mb or what?
It sounds that way. Perhaps there's an option you can specify in your xorg.conf to let X know you have more than 128MB of memory.

EDIT: I changed my integrated video's RAM to 256MB in my BIOS and it does show 256MB, so you should definitely investigate your missing RAM
```
[dan@harvest Desktop]# cat /var/log/Xorg.0.log | grep RAM
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0xfffc000
(--) RADEONHD(0): VideoRAM:** 262144 kByte**
```

---

### Post by dustman on 2008-02-18
> **Temüjin said:**
> I'm using the radeonhd driver and the command in bold shows what I have (in this case 128MB). I believe the proprietary fglrx driver makes a similar entry in the Xorg log, so try that command or maybe substitute grep memory. If that fails, open up the log and wade through it.

```
[dan@harvest Desktop]# **cat /var/log/Xorg.0.log | grep RAM**
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x7ffc000
(--) RADEONHD(0): **VideoRAM: 131072 kByte**
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0x7ffc000
(II) RADEONHD(0): AtomBIOS requests 16kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0x7ffc000
(II) Initializing built-in extension XINERAMA
```


thanks man :D that did it! the output:
```
dustman@dustman-laptop:~$ cat /var/log/Xorg.0.log | grep RAM
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) Initializing built-in extension XINERAMA

```
so i guess i have 128 MB RAM...right :D?

---

