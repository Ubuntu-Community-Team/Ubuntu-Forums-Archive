---
title: "[AcerAspireOne 522] Cpu Fan not working"
date: 2011-04-16
forum: Hardware
---

### Post by tigrezno on 2011-04-16
LM-sensors are not working but I can read temperature with gkrellm

When temperature reaches 100C, system goes shutdown

It looks like cpu fan is just not working

Any suggestion?

---

### Post by KegHead on 2011-04-16
Hi!

It could be a kernel problem.

Try:

sudo apt-get update

sudo aptitude install linux-image -f

or

sudo apt-get install linux-image -f

You'll need to restart.

KegHead

---

### Post by tigrezno on 2011-04-16
> **KegHead said:**
> Hi!

It could be a kernel problem.

Try:

sudo apt-get update

sudo aptitude install linux-image -f

or

sudo apt-get install linux-image -f

You'll need to restart.

KegHead

well I'm using last 11.04 beta

the same happened with debian and archlinux

Should I ask for a windows7 usb image to acer?

---

### Post by KegHead on 2011-04-16
Hi!

I would replace the fan.

It's easy to do!

KegHead

---

### Post by tigrezno on 2011-04-16
> **KegHead said:**
> Hi!

I would replace the fan.

It's easy to do!

KegHead

But I bought it yesterday, it came with win7 so I suppose they won't change it back

---

### Post by KegHead on 2011-04-16
Hi!

Does your fan work ok w/windows?

KegHead

---

### Post by tigrezno on 2011-04-16
> **KegHead said:**
> Hi!

Does your fan work ok w/windows?

KegHead

It is my fault, I didn't tested on windows at all, just installed linux.

There is an alt+f10 solution to restore win7, but after linux it won't work.

So I'm stuck right now

I'll be asking acer for a copy of win7

---

### Post by KegHead on 2011-04-16
Hi!

Did they supply you with any disks?

KegHead

---

### Post by tigrezno on 2011-04-16
> **KegHead said:**
> Hi!

Did they supply you with any disks?

KegHead

nope, those netbooks come with a hidden 4gb memory with recovery information, but after installing linux it won't work anymore

---

### Post by KegHead on 2011-04-16
Hi!

Try a google search on how to tap that recovery mode.

Good Luck!

KegHead

---

### Post by qamelian on 2011-04-16
You need to build your own recovery media on a memory stick on that unit using the tool provided with Windows 7. 
I think you may have picked up a defective unit. I've have Ubuntu 10.10, 11.04, 32 bit & 64 bit on my 522 and the fan works fine.

---

### Post by tigrezno on 2011-04-16
> **qamelian said:**
> You need to build your own recovery media on a memory stick on that unit using the tool provided with Windows 7. 
I think you may have picked up a defective unit. I've have Ubuntu 10.10, 11.04, 32 bit & 64 bit on my 522 and the fan works fine.

That is my worry, a defective unit...

I hope not, but since I can't install windows 7, i'll wait for acer's reply

---

### Post by KegHead on 2011-04-16
Hi!

There is a challenge;

1. Can't get into windows.

2. Retailer/vendor may not credit/replace without original OS.

KegHead

---

### Post by GTMoraes on 2011-04-17
I guess, in this case, downloading a copy of Windows 7 of your version thru Torrent or something would be legal, since you have the rights of the system.

It would be just like having a backup copy.
Download Windows 7 on a trusteable download site (torrents are faster) and use the Software key provided underneath your netbook.
You should have Win7 back in no time.

Good luck =)
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by GTMoraes on 2011-04-17
whoops, sorry =(
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by tigrezno on 2011-04-18
Hi guys, I solved it. It was a faulty unit (damn bad luck)

Changed for a new one and it works great. I'm still reticent to install linux, i'll be testing it for a week or so.

---

### Post by GTMoraes on 2011-04-18
It would be bad luck if you couldn't change it =)
Good thing you've noticed on time.
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[size=1]|[color=#7FFF00]Microsoft WMM 4000[/color]|[/size]
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by tigrezno on 2011-04-18
Yes, I'm currently cloning the entire HDD with the help of systemrescuecd

Thanks for the help

---

