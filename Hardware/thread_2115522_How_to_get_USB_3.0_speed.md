---
title: "How to get USB 3.0 speed"
date: 2013-02-13
forum: Hardware
---

### Post by quirino77 on 2013-02-13
I know there was problem. Also know it was fixed. But don't know if it is just to work or to work as it should.

I have a Gigabyte 880GMA-USB3. It has a Etron USB 3.0 chip. It works, but only at USN 2.0 speed.

Can i get USB 3.0 speed?

I'm using Ubuntu 12.04, 64 bits, fresh install.

$ lspci |grep USB
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
02:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)


Thank's in advance.

---

### Post by andrew.46 on 2013-02-13
Bought my own motherboard because of usb 3.0 support:

```

root@skamandros/home/andrew# lspci |grep USB
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller

```

I see from looking at the specs of your board that on the back there are actually *4 usb 2.0 ports* and only 2 usb 3.0 ports. I could not work out what was connecting to the front of the case, whether 2.0 or 3.0 but this would be obvious on setup as usb 3.0 controller uses a much different cable :)

---

### Post by quirino77 on 2013-02-14
I had used the 3.0 ports. Already checked it.
Also i had tried 2 USB 3.0 external drives. No one got 3.0 speeds.

---

### Post by quirino77 on 2013-02-17
Bump.

---

### Post by Mark Phelps on 2013-02-17
Sorry to tell you this, but you're likely to be stuck with USB 2.0 speeds.

Couple of reasons why ...

First, I also have a Gigabyte mobo and was having the same problems in both Win7 and Ubuntu until I found a third-party Sony site that had both a firmware update (for the onboard chip) and a driver update.  After I applied them (in Windows, of course), I got USB 3.0 speeds.

Second, a quick Google revealed a thread on the Gigabyte forums where folks are complaining about a similar problem -- but in their case, they were able to find driver updates -- for Windows, of course.

So, unless some miracle occurs and new drivers (with the same features as the most current Windows drivers) are published for Linux, you're likely stuck with slower speeds.

---

### Post by quirino77 on 2013-02-20
Thank you for your help.
I was already expecting it.
Really bad. I will choose better when buying a mainboard again.

---

