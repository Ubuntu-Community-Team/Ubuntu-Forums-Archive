---
title: "Disabling onboard 100M prevents Gigabit working"
date: 2023-08-19
forum: Hardware
---

### Post by paulrb on 2023-08-19
I have built a modest home server from old parts. Motherboard is a Foxconn A6VMX with onboard 100Mb LAN. But I'm not using that port, I use a Gigabit PCI (not PCIe) card, which is working well under Ubuntu Server 22.04, to connect to my Gigabit switch.

Since the server runs 24/7, I've been trying to reduce idle power consumption (measured at the wall socket with one of those plug-in power meters). I have it down to around 42~43W, so not too bad, but shaving off a few more Watts would be even better.

Browsing the BIOS configuration pages, I realised I had not disabled the onboard 100Mb LAN. I did that, and the idle power consumption dropped to 35~36W, which quite surprised me, I was only hoping/expecting to save a couple of Watts.

But I then realised the server was not connecting to the router and had no IP address. The LEDs on the Gigabit card seemed to be flashing merrily away as usual.

So I've re-enabled the onboard LAN and the server is connecting ok again.

I would like to try again for that 7~8W saving, but don't know how to get the server to connect. I don't understand why disabling the onboard LAN would affect the PCI Gigabit LAN at all.

Google and the forum search don't seem to find me any similar topics, perhaps I'm not using the best search terms.

Can anyone help me to diagnose what's going on here? Please let me know what relavant details I need to provide.

Thanks!

Paul

---

### Post by TheFu on 2023-08-19
Perhaps 50% of those power savings were also because the PCI NIC was disabled?

I've found that getting hardware designed for low-power use is the easiest way to achieve lower power use.  That motherboard is from the time of MS-Vista ... so 2010-ish. Since then, much faster system with 50% power savings have been sold.  I replaced a Core i7 ITX from that time with a Ryzen 2600 and saved over 100W. Even with 6 HDDs in the newer system, it is still using 50% less power for about 5x the performance.  Replaced that 2600 + 1030 nvidia GPU, gained 40% more performance for $100 and dropped the power use even more.  Now have a system with nearly 20,000 passmarks, iGPU, and the 2600 power cost savings paid for itself over 2 yrs.  Plus there's my "happiness factor" which is worth a good $50/yr. ;)

Newer CPUs are much better at sipping power when they aren't used.  Often 50% or more in power savings.

---

### Post by paulrb on 2023-08-20
> **TheFu said:**
> Perhaps 50% of those power savings were also because the PCI NIC was disabled?


It wasn't completely disabled, it was still consuming power, it's LEDs were still flashing. But, like you, I also wondered if some of the power saving was because the PCI NIC was being ignored by the CPU and so the CPU was less busy and could spend more of its time in a low power state.

I know I could replace the motherboard/CPU to achieve power savings, and I have been researching that. But it would take a long time to recoup the cost of those new (or used, but more recent) components through power saving. That's because this server spends most of its time idle, so it's the idle power consumption that is important to me. Saving 10W would save about £30 per year, so I'm not going to be able to recoup the cost of a new motherboard, CPU (and new memory also of course) in 2 years.

While I'm researching what major replacement parts to choose (evidence about idle power consumption is patchy and conflicting) I'm having a little fun seeing what I can achieve with the components I have, or maybe replacing some minor components.

I've already replaced the PSU with a 80+ gold rated one, which saved 5~10W. It's a 400W PSU, I couldn't find anything lower that was for sale, used. I have also replaced the case fans with speed-controlled ones, saving a couple of Watts and quite a lot of noise!

I am also considering replacing the PCI NIC with a more recent PCIe NIC to see that will bring any savings, both through the NIC itself consuming less power when idle, and putting less load on the CPU and achieving more savings that way also.

---

### Post by TheFu on 2023-08-20
I feel you. My savings came due to 125W CPU--> 65W, an add-on GPU--> iGPU.  I'd switched to 80%+ Bronze PSUs about a decade ago. Think there was a deal on some Seasonic 430W for $40, so I bought a bunch. I couldn't get any lower ... er ... until I needed to replace an ITX case industrial PSU that was VERY LOUD.  Got a silent, 65W picoPSU for that. They made 80W and 120W versions. They move the AC/DC converter outside the case to a black brick.  The PSU inside the case is tiny.

So, saving the power savings from a 125W CPU and CAD GPU definitely saved my power bill to a noticeable level each month.  I poo-pooed others making claims of power savings, until I looked at the output from my UPS display.  One UPS is putting out 120 W - it supports networking, telephone, KVM-swtich disk array, and a Ryzen computer.  The other UPS is putting out 95W with a similar Ryzen and array and 1 WAN router.  Some of the HDDs in this 2nd system are 10+ yrs old.

Neither have dedicated GPUs any more.
BTW, the first system is doing heavy processing during that reading.
```
$ uptime
 08:28:11 up 3 days, 17 min,  2 users,  load average: 4.34, [B]10.18, 11.66
[/B]
```
all cores being used.
I need to check that the devices are evenly split between the UPSes.  Had to replace a burned out UPS (lightning) a week ago and haven't migrated all the peripheral power stuff back yet.

I did retire an old external array - think the lightning took out the circuit board on it too. If I could find a replacement circuit board, I think it can be made live again. I see that 1 of my HDDs is running hot, 54°C. Need to move a case fan to blow over that disk, assuming it will fit on the front of the case to get it below 50° and perhaps even lower.
```
$ sudo hddtemp /dev/sd[a-g]
/dev/sda: Hitachi HDP725050GLA360: 50°C
/dev/sdb: WDC WD8002FZWX-00BKUA0: 54°C
/dev/sdc: WDC WD20EFRX-68AX9N0: 35°C
/dev/sdd: TOSHIBA DT01ACA200: 36°C
/dev/sde: Hitachi HUA723020ALA641: 37°C
/dev/sdf: WDC WD20EFRX-68AX9N0: 36°C

```
The last 4 drives are in a drive cage with a 120mm fan keeping them cool.
The first 2 drives are just mounted in the front of the case, no fan blowing over them at all. There are 2 case fans, not counting the PSU, CPU, and drive cage fans. One is on a side panel and the other is in the top. Think moving the top fan to the bottom front of the case will blow over those 2 hot HDDs.

There's also an NVMe SSD - 
```
Temperature Sensor 1                : 46 C
Temperature Sensor 2                : 50 C
```
They run hotter. Not a worrying temp to me.

I won't let power concerns taint the need for cooling.

---

### Post by paulrb on 2023-08-21
Interesting, thanks.

But I'm no nearer to figuring out how to get my PCI NIC working when the motherboard's onboard LAN port is disabled in the BIOS.

---

### Post by paulrb on 2023-08-22
This is what I see when the on-board LAN is enabled in BIOS:
```

  *-network DISABLED
       description: Ethernet interface
       product: RTL810xE PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 01
       serial: 00:1f:e2:51:90:95
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 latency=0 link=no multicast=yes
       resources: irq:17 ioport:d800(size=256) memory:feaff000-feafffff memory:feac0000-feadffff
  *-network
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 10
       serial: fc:75:16:67:4c:de
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full ip=192.168.1.200 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff

```
and when disabled in BIOS:
```

  *-network DISABLED
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: fc:75:16:67:4c:de
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 latency=64 link=no maxlatency=64 mingnt=32 multicast=yes
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff

```
[s]Apologies for errors in the above, I took photos of the screen and used Google Lens, because I had no other means of copying the text![/s]
Edit: post updated with corrected output (thanks @TheFu for suggesting redirecting the output to file! #-o)

---

### Post by TheFu on 2023-08-22
> **paulrb said:**
>  
Apologies for errors in the above, I took photos of the screen and used Google Lens, because I had no other means of copying the text!

Couldn't redirection be used?  Then you'd save the output to a file, then copy that/those files to a flash drive 
or 
boot into a "Try Ubuntu" environment 
or 
boot normally without the NICs being disabled,

then post the file contents here.

If you don't know how to use redirection, there are so many powerful things on Unix you are missing.  Actually, redirection works on MS-DOS and later as well.
If you'd like to know more things about making the shell your bitch, google for "art of the command line" - there's a github page with text about many things.  I re-read it every year because there's always something I wasn't ready to learn last year that would have saved me time and effort.

Most commands output to stdout, which easily redirects.  A few will send important stuff we want to stderr instead - bad program.  But we can redirect stderr to a file too, if needed.  There are some really great things in having stdout and stderr separate ... for example, use in a crontab.  Errors should go to stderr, so if only stderr is allowed to be emailed to a human, we get the "no news, is good news" out of our scheduled tasks, but errors aren't missed.

---

### Post by paulrb on 2023-08-23
Very good point, don't know why I didn't think of that. Just save the output to a file, then access it when the LAN is working! Will do.

---

### Post by TheFu on 2023-08-23
> **paulrb said:**
> Very good point, don't know why I didn't think of that. Just save the output to a file, then access it when the LAN is working! Will do.

As part of my daily backups, I capture all sorts of system information, including drivers used, by saving command output to text files that get included in the backup area.  If you watch these forums long enough, you'll see that partition tables sometimes become corrupted - both copies - so having many days of backups with that information is a machine-usable format means being able to put it back with 100% accuracy in just a few minutes.  I never believed I'd run into that problem myself ... I've been a Unix/Linux admin about 30 yrs now. I know partitioning.  Then it happened to me about a month ago. The problem was caused by a USB controller doing odd things - odd to me.  Thankfully, I had backups of that partition layout.  Just sayin'.

BTW, there's always more to learn, so we can do it better.  As I try to help people here, I'm constantly learning both what NOT to do, but also how to get out of self-inflicted problems AND how to avoid them.  My main job as an admin is to prevent issues BEFORE they happen.  When your systems are being used by 25K people to keep the company going, downtime for even an hour costs $millions in real money.

My home systems benefit from much of what I've learned at work, though my personal budget isn't anything like my work budgets.  I might spend $500/yr on stuff here in a really bad year.  I had a lightning strike this year that took out a UPS (from 2007), batteries (4 yr old), and got me to retire a 13 yr old computer, finally.  With that retirement, I bought an 8TB HDD to hold the data on the other computer ... discovered the 10 yr old drives in it were still mostly fine, so I got a hot-swap HDD cage so those HDDs could be put into another relatively new computer.  Oh, and a raspberry pi4 was on my list since 2019, got one of those when they came available here for list price.  Think I've spent over $400 in the last 2 months.  In any single year, I expect about 10% of my storage to fail.  As they fail, I buy a replacement that is 2x the size to keep the number of ports used down.

Anyway, I'm out of ideas for getting an addon NIC with realtek working as you like.  I don't have any realtek NICs here. They are specifically avoided after I wasted far too much time with a bad one.

---

### Post by paulrb on 2023-08-28
Updated post #6 with corrected output.

---

### Post by paulrb on 2023-08-29
I think I figured it out...

With the on-board 100MB LAN enabled in the BIOS, Ubuntu was assigning the logical name "enp2s0" to the on-board LAN and "enp3s0" to the 1GB PCI LAN card.

With the on-board LAN disabled in the BIOS, Ubuntu was assigning the  logical name "enp2s0" to the PCI LAN  card (and no name to the on-board LAN, of course, because it was no longer visible to Ubuntu).

This meant that the network configuration file (/etc/netplan/00-installer-config.yaml) was now incorrect because it was looking for "enp3s0":
```

# This is the network config written by 'subiquity'
network:
  ethernets:
    enp3s0:
      dhcp4: true
  version: 2

```

I edited the above, changing "enp3s0" to "enp2s0" and restarted. Problem solved!

"sudo lshw -C network" now shows:
```

  *-network                 
       description: Ethernet interface
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: fc:75:16:67:4c:de
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full ip=192.168.1.200 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff memory:febc0000-febdffff

```
and "ip a" shows:
```

: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether fc:75:16:67:4c:de brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.200/24 brd 192.168.1.255 scope global dynamic enp2s0
       valid_lft 42255sec preferred_lft 42255sec
    inet6 fe80::fe75:16ff:fe67:4cde/64 scope link 
       valid_lft forever preferred_lft forever

```

So... after all this, did I make any improvements in the idle power consumption? No, back to 42~43W. So I think all the improvement I saw must have been because of reduced CPU usage when there was no network connection, and the power saving from disabling the on-board LAN was negligible. Still, I learned a few things on the way.

---

