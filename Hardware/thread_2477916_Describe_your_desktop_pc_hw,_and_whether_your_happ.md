---
title: "Describe your desktop pc hw, and whether your happy with it.  (recommendations)"
date: 2022-08-11
forum: Hardware
---

### Post by david503 on 2022-08-11
I'm buying a new desktop PC. (Desktop not laptop).   I'm currently running a Lenovo 300something that's 8 years old and it's still running 18.04.  Time to upgrade, eh.

What brands do you recommend for desktop PC's?  I used to build my own rigs, but these days I want to go with a brand.  

I'm not going with lenovo again.  And absolutely *never* going with HP.  Years ago Dell was a total mess, but maybe that's changed? 

So far I've been advised to go with Asus.  My gripe is that they don't support dual monitors out of the box (like Lenovo does), unless one of them is *cough* VGA.  

It has to be an actual tower, not one of those "slim" format PC's. 

Anyway, what brands/models are you using and are you happy with what you have?

thank you

---

### Post by TheFu on 2022-08-11
> **david503 said:**
> I'm buying a new desktop PC.  I'm currently running a Lenovo 300something that's 8 years old and it's still running 18.04.  Time to upgrade, eh.
Perhaps.  I have a 2010 Core i5 that has been running all this time. It is currently a RAID storage server and a backup server. I've been planning to retire it, but don't have another machine that can accept the 10 SATA port connections.  The downside is that old CPU is using 105W, which can be felt in the monthly power bills.

> **david503 said:**
> What brands do you recommend?  I used to build my own rigs, but these days I want to go with a brand.  
After being burned a few times, I swore that I'd never, ever, buy a pre-built desktop computer again.  Had one that couldn't stay booted for 4 hrs before the OS would crash.  The support from the vendor was really just delay tactics - try X - oh, that didn't work? That's surprising.  2 weeks later, try Y - oh, that didn't work? Surprising.  They did this for 6 months.  I had better things to do in life and at the time was making lots of money to where the cost of that computer was less than 2 days of take home pay.  Around the same time, I'd built a dual CPU Celeron as a Linux server for home and it was running perfect.  This was before multi-CPU systems were available for home desktops.

Vendors were coming with proprietary stuff which locked me into only buying replacement/upgrade parts for 2x the real cost.  I've been putting together my new PCs and doing $300 huge upgrades every 5-10 yrs for decades.  My "old" 2010 Core i5 is inside a case that I first purchased in 1999. Everything inside is new, except the speaker that "beeps".  Until about 6 months ago, I was using the same mouse and keyboard too!

In short, for people who keep systems a long time, doing MB+CPU upgrades is much more cost effective and satisfying, since we get to pick when to replace specific parts, how much to spend and how much performance improvement is desired.  About every 5 yrs, doubling performance is pretty easy while nearly cutting power use 50% each time.

> **david503 said:**
> I'm not going with lenovo again.  And absolutely *never* going with HP.  Years ago Dell was a total mess, but maybe that's changed? 

Build your own.  Takes 30 minutes with a Philips head screw driver, tops.  There are lots of videos for this stuff and parts lists, but more and more, for non-gamers we can have great iGPU built into the CPU.  All of those systems are well supported by Linux at this point.

> **david503 said:**
> So far I've been advised to go with Asus.  My gripe is that they don't support dual monitors out of the box (like Lenovo does), unless one of them is *cough* VGA.  
What?  Forget  buying a computer.  Build one.  A Ryzen 5 5600G can support 3 monitors. No VGA (which actually was a problem for me), but there are $10-$25 video converter adapters to go to/from DVI --> HDMI or HDMI --> DVI.  You certainly aren't stuck with whatever GPU any desktop computer comes with unless you choose foolishly a NUC or other tiny-form-factor desktop.  If you stick with MicroATX - and put them into the normal mid-tower case, almost any but the $1000 GPUs will fit.

> **david503 said:**
> It has to be an actual tower, not one of those "slim" format PC's. 
Anyway, what brands/models are you using and are you happy with what you have?

Good choice.  At least you aren't being dumb and getting an expensive laptop for people who don't travel 80% of the time.  For most people, building an expensive desktop  (say $500) and buying a cheap laptop (say $300) will be 50% less than spending $1500 on an expensive laptop and you'll have much more flexibility and not worry about having $1500 stolen in airport lines or from a car break-in.  

Don't buy a full computer.  Please. It is a waste of so much and we get crap components.
[https://pcpartpicker.com/guide/rFLrxr/entry-level-amd-gaming-build](https://pcpartpicker.com/guide/rFLrxr/entry-level-amd-gaming-build) is an example build.  I haven't looked too closely, but right now, at Microcenter the Ryzen 5600G is $120.  I have this CPU+iGPU. It rocks.  6 cores.  Better GPU built-in than an nVidia GT 1030 with GDDR5 - I have one of those too.

Parts:
Case ($20 or reuse existing) Don't spend more than $50, that's just a waste.
PSU ($60 for a Bronze+ Corsair or Seasonic or reuse existing)
Motherboard (Asus B450/B550 - look for Intel NIC to avoid realtek issues) Most AM4 motherboards with B450, B550, X470 or X570 should work.
CPU/iGPU + cooler (Ryzen 5600g comes with a heatsink+fan)
RAM (16G is plenty)
500G SSD for the OS and immediate needs (I'm partial to Samsung 970 EVO or Pro)

and external that most people would reuse.  Keyboard, monitor(s), mouse, speakers, headset, webcam, 2T-4T HDD for backups.

The build is really like putting together a 20 piece lego these days.  The claims that motherboards need firmware updates to support the 5xxx Ryzen are just not true. I built a system with an Asus B450 last November and the CPU was supported already.  Of course, I did flash new BIOS immediately to the motherboard and for the Samsung SSD, just to be certain, but those tasks can wait a few weeks while you burn in the system, watch the cooling work and tweak the BIOS settings for reasonable performance.

Once you have this system, you can likely double performance in a year with a 58xx CPU swap and adding a $200 GPU. Keep everything else. The AM4 socket has lots of options and unlike Intel, you don't need a new motherboard for each new CPU.

Long term, building your own system just provides many more options at less total cost. You'll have industry standard parts.

I forgot, here's one of my systems - inxi -Fxxz:
```
$ inxi -Fxx
System:    Host: istar Kernel: 5.16.20-051620_5.16.20-generic x86_64 bits: 64 Desktop: N/A dm: lxdm
           Distro: Ubuntu 18.04.6 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 4602 date: 08/17/2021
CPU:       6 core AMD Ryzen 5 5600G with Radeon Graphics (-MT-MCP-) arch: N/A cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 48000
           clock speeds: min/max: 1400/5128 MHz 1: 1400 MHz 2: 1400 MHz 3: 1400 MHz 4: 1400 MHz 5: 1400 MHz
           6: 1400 MHz 7: 1400 MHz 8: 1400 MHz 9: 1400 MHz 10: 1400 MHz 11: 3999 MHz 12: 1400 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Device 1638 bus-ID: 0a:00.0 chip-ID: 1002:1638
           Display Server: X.Org 1.20.8 drivers: ati,vesa (unloaded: modesetting,fbdev,radeon)
           Resolution: 1920x1200@59.95hz
           OpenGL: renderer: N/A version: N/A Direct Render: N/A
Audio:     Card-1 Advanced Micro Devices [AMD] Device 15e3
           driver: snd_hda_intel bus-ID: 0a:00.6 chip-ID: 1022:15e3
           Card-2 Advanced Micro Devices [AMD/ATI] Device 1637
           driver: snd_hda_intel bus-ID: 0a:00.1 chip-ID: 1002:1637
           Sound: Advanced Linux Sound Architecture v: k5.16.20-051620-generic
Network:   Card-1: Intel I211 Gigabit Network Connection
           driver: igb port: d000 bus-ID: 03:00.0 chip-ID: 8086:1539
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full  
           Card-2: Intel 82575GB Gigabit Network Connection
           driver: igb port: c020 bus-ID: 07:00.0 chip-ID: 8086:10d6
           IF: enp7s0f0 state: up speed: 1000 Mbps duplex: full
           Card-3: Intel 82575GB Gigabit Network Connection
           driver: igb port: c000 bus-ID: 07:00.1 chip-ID: 8086:10d6
           IF: enp7s0f1 state: up speed: 1000 Mbps duplex: full
           Card-4: Intel 82575GB Gigabit Network Connection
           driver: igb port: b020 bus-ID: 08:00.0 chip-ID: 8086:10d6
           IF: enp8s0f0 state: up speed: 1000 Mbps duplex: full
           Card-5: Intel 82575GB Gigabit Network Connection
           driver: igb port: b000 bus-ID: 08:00.1 chip-ID: 8086:10d6
           IF: enp8s0f1 state: up speed: 1000 Mbps duplex: full
Drives:    HDD Total Size: 32826.5GB (73.0% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_970_EVO_500GB size: 500.1GB
...
Info:      Processes: 425 Uptime: 19 days Memory: 5702.7/15112.3MB
           Init: systemd v: 237 runlevel: 5 default: 2 Gcc sys: 7.5.0 alt: 4.8/5
           Client: Shell (bash 4.4.201 running in sshd) inxi: 2.3.56
```

---

### Post by TheFu on 2022-08-11
Hopefully, that uptime in the inxi output shows how stable this system is.

---

### Post by david503 on 2022-08-11
Thanks.  Like I said in my op, "[COLOR=#000000]I used to build my own rigs, but these days I want to go with a brand."[/COLOR]

[COLOR=#000000]So yea, I know how to build them, screwdriver and all, I did that for 20+ years.  I don't want custom rigs anymore.  Part of the reason is that I could be buying them for other people (such as employees, friends, family), and I don't want to spend the time repetitively building them.  (And supporting them.) 

[/COLOR]But anyway thanks for describing your custom stuff.  

Actually- I'm going to start a new thread about graphics cards- but I'll ask here quickly since you seem to know your stuff very well;  I'm looking for a card that supports a lot of monitors, like 4?.  No need for any fancy gamer stuff; just regular displays, but a lot of them.  So lots of hdml and/or display port outs.  Do you know of any good ones?  
Or alternatively, can I also drive monitors from PCI slots or does everything have to be on the graphics card?

thanks

---

### Post by TheFu on 2022-08-11
I've only read a bit about having more than 3 monitors connected. No clue.  I've never used more than 2 monitors on Linux.  

I'm confused that you think a PCI slot can drive a monitor.  Never heard of that.  We can insert as many GPUs into PCIe slots as a system supports and has power/bus to handle, and each can have multiple monitor support.  I think that's true.

I use workspaces extensively.

---

### Post by mIk3_08 on 2022-08-11
> **david503 said:**
> IAnyway, what brands/models are you using and are you happy with what you have?
 HP EliteBook. Very happy and contented with my machine. So far so good. Regards and cheers

---

### Post by david503 on 2022-08-11
Oh yea I meant PCIe not PCI (I'm old I still use the term "PCI" which came before PCIe.   You kids today!)

Ok thanks I'll look into PCIe graphics cards to augment the main video.  
Wait I just looked; I bet I can get away with just doing something like this: 

[https://www.amazon.com/Universal-Graphics-Displaylink-Supports-2048x1152/dp/B01CSG7TUC/ref=sr_1_8?crid=1UGI1O3O9CTEU&keywords=multiple%2Bmonitor%2Busb%2Blinux&qid=1660228083&s=electronics&sprefix=multiple%2Bmonitors%2Busb%2Blinux%2Celectronics%2C73&sr=1-8&th=1](https://www.amazon.com/Universal-Graphics-Displaylink-Supports-2048x1152/dp/B01CSG7TUC/ref=sr_1_8?crid=1UGI1O3O9CTEU&keywords=multiple%2Bmonitor%2Busb%2Blinux&qid=1660228083&s=electronics&sprefix=multiple%2Bmonitors%2Busb%2Blinux%2Celectronics%2C73&sr=1-8&th=1)

Anyway, never mind, I'll do the research, sorry to bother you. I'm amazed how much easier this is to do than in the old days. 

thanks again

---

### Post by TheFu on 2022-08-11
> **david503 said:**
> Oh yea I meant PCIe not PCI (I'm old I still use the term "PCI" which came before PCIe.   You kids today!)

Ok thanks I'll look into PCIe graphics cards to augment the main video.  
Wait I just looked; I bet I can get away with just doing something like this: 

[https://www.amazon.com/Universal-Graphics-Displaylink-Supports-2048x1152/dp/B01CSG7TUC/ref=sr_1_8?crid=1UGI1O3O9CTEU&keywords=multiple%2Bmonitor%2Busb%2Blinux&qid=1660228083&s=electronics&sprefix=multiple%2Bmonitors%2Busb%2Blinux%2Celectronics%2C73&sr=1-8&th=1](https://www.amazon.com/Universal-Graphics-Displaylink-Supports-2048x1152/dp/B01CSG7TUC/ref=sr_1_8?crid=1UGI1O3O9CTEU&keywords=multiple%2Bmonitor%2Busb%2Blinux&qid=1660228083&s=electronics&sprefix=multiple%2Bmonitors%2Busb%2Blinux%2Celectronics%2C73&sr=1-8&th=1)

Anyway, never mind, I'll do the research, sorry to bother you. I'm amazed how much easier this is to do than in the old days. 

thanks again

I remember MCA and ISA.  Some of my systems still have a 32-bit PCI slot too, for specific adapters.

I'd check for specific support of the Linux kernel you want.  All is not rosy with claimed Linux support, as you probably know and definitely not with displaylink. There are many caveats. I hope it does all work. More options are better than fewer, but USB3 is nowhere near enough bandwidth for modern GPU/display support. Beware of great claims, until you see it work, in-person.

---

### Post by coley9225 on 2022-08-11
[COLOR=#0F1111][FONT=&quot]Hello david, I use a laptop and would like a 3rd display. I looked at the item you linked to, and noticed the follow note:
    Windows XP 64-bit and Surface RT, Linux, Unix are not supported.
I would be a little leary of it, especially at that price. I have also read that usb a  type are no good for a monitor, must be usb c.
Good luck.[/FONT][/COLOR]

---

### Post by david503 on 2022-08-24
@TheFu Oh I'm actually using the displaylink port for one of my screens right now, and this pc is 8 years old running 18.04.

---

### Post by TheFu on 2022-08-24
> **david503 said:**
> @TheFu Oh I'm actually using the displaylink port for one of my screens right now, and this pc is 8 years old running 18.04.

Displaylink with 1 or 2 monitors in serial, should work.  Any more than that, and I wouldn't bet anyone.  There's the theory and the practice. They are often very different.
[https://wiki.archlinux.org/title/DisplayLink](https://wiki.archlinux.org/title/DisplayLink) is clear:
> DisplayLink devices on Linux still only have experimental support. While some people have had success in using them, it is generally not an easy process and not guaranteed to work.

---

