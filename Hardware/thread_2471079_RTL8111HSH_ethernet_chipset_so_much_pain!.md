---
title: "RTL8111HSH ethernet chipset: so much pain!"
date: 2022-01-20
forum: Hardware
---

### Post by kenlibero on 2022-01-20
I've been fighting with an ethernet chipset since months ago, tons of searches without results.
After more than 15 years of linux, different distros on many computers, never ever seen something like that.

My configuration:
HP Desktop PC M01-F1000a (2W898AV)
motherboard: HP 87D6 "erica3"
ethernet: Realtek RTL8111HSH (RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller rev 15)
wifi: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter
os: Ubuntu 20.04.3

I've tried both r8169 driver and r8168-dkms drivers.
The problem is always the same: randomly on machine starting, let's say 1/3 of the times, ethernet is not working, only wifi connects.
Usually I can get it working after one or more attempts of ethernet restarting:
sudo ip link set enp10s0 down && sudo ip link set enp10s0 up

Does someone have any clues about that strange situation, please?

---

### Post by TheFu on 2022-01-20
Sorry. Sometimes Realtek just sucks on Linux.
Use Intel next time.  Sadly, some Intel chips have not-so-great Linux support. The new Intel 2.5Gbps ones (some Ryzen B550 and X570 motherboards have those) had people buying $25 Intel PRO/1000 NIC to get networking while intel and the kernel guys try to fix the issues. That chip is a Intel I225-V.  Some ASUS Z490 Boards have the same NIC with the issue.

I know intel 82575GB, i210 and i211 chips are well supported with igb driver. 
I know the intel 82574L chips are well supported with the e1000e driver too. 

All my wifi uses Intel chips.

I've had issues with 
* RTL8111/8168/8411
* Marvell 88E8001
NICs.  I have on machine left with those still. It also has a dual-port Intel 82574L NIC.

---

### Post by kenlibero on 2022-01-21
Thank you for your suggestions TheFu.
I guess I'll be forced to mount an external ethernet card to get some stability.

What really drives me nuts is that the internal ethernet actually does work, but it has that random behavior at startup. And also when it's not working at startup, it usually does after a couple of eth restarts by command line.
It looks to me like there's a kind of conflict among drivers, or something like that. Maybe ethernet works only if it comes alive before or after some other periperhal (wifi?)
This is just a supposition, though. I tried to confirm it examining boot logs, but I have no certainty at all by now.

Any other thoughts could be precious.

---

### Post by TheFu on 2022-01-21
Sometimes a loose MB connection to the onboard NIC is the cause too.  I had a RT81111 become flaky with dropped packets.  I was only getting around 200 Mbps after all the resends.  Swapped in a $10 Maxell skge card I'd had for 10 yrs that on a good day would get 300Mbps even when it was new.  Retired that system a few months ago and now have PCIe quad port Intel in the new system with an i211 on the MB.  Live and learn.

Here's that new box - it is a Ryzen:
```
$ inxi -Nxx
Network:   Card-1: Intel I211 Gigabit Network Connection
           driver: igb port: d000 bus-ID: 03:00.0 chip-ID: 8086:1539
           Card-2: Intel 82575GB Gigabit Network Connection
           driver: igb port: c020 bus-ID: 07:00.0 chip-ID: 8086:10d6
           Card-3: Intel 82575GB Gigabit Network Connection
           driver: igb port: c000 bus-ID: 07:00.1 chip-ID: 8086:10d6
           Card-4: Intel 82575GB Gigabit Network Connection
           driver: igb port: b020 bus-ID: 08:00.0 chip-ID: 8086:10d6
           Card-5: Intel 82575GB Gigabit Network Connection
           driver: igb port: b000 bus-ID: 08:00.1 chip-ID: 8086:10d6
```
Crazy stable and 920+ Mbps with all the cards.  I only use 3 of the ports.  Red, Green and Black LANs.  Red is internet facing, Green is the server LAN and Black is the storage/management LAN. Too bad I can't to IOMMU passthru for just 1 port on the PCIe card. That would be better for security.

---

### Post by kenlibero on 2022-01-22
I didn't mention that I already tried with another external card:

```
$ inxi -Nxx
Network:
  Device-1: Realtek driver: r8169 v: kernel port: e000 bus ID: 03:00.0 
  chip ID: 10ec:8161 
  Device-2: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter 
  vendor: Hewlett-Packard driver: rtl8821ce v: v5.5.2.1_35598.20191029 
  port: d000 bus ID: 09:00.0 chip ID: 10ec:c821 
  Device-3: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Hewlett-Packard driver: r8169 v: kernel port: c000 bus ID: 0a:00.0 
  chip ID: 10ec:8168 
```

Different realtek chip, but exactly the same behavior. Should I conclude that all chips by realtek (or many of them) are not well supported by ubuntu 20.04, and therefore everyone should add an intel card?
It sounds very strange to me.

---

### Post by TheFu on 2022-01-22
> **kenlibero said:**
> I didn't mention that I already tried with another external card:
...
Different realtek chip, but exactly the same behavior. Should I conclude that all chips by realtek (or many of them) are not well supported by ubuntu 20.04, and therefore everyone should add an intel card?
It sounds very strange to me.

I'd be more inclined to blame something outside the computer. If the cable or switch ports are marginal then not-so-great drivers could matter.

Both of the NICs above are using the same driver. That's another data point. Millions of Linux users do use Realtek and never notice any issues daily.  Could you just be unlucky? Sure, but 2 devices would be extremely unlikely.

Have you tried a different kernel which would have different drivers?
I looked up the  10ec:8161 driver and it seems correct.
Are there any clues in these forums for  the specific version of the card(s) being used?  For example, different HW revisions can require different drivers.

---

### Post by kenlibero on 2022-01-24
I think you're right TheFu!

I already tried to change the cable, and to choose a different port on the router, with no success.
Yesterday I tried with another router.
Before I was using a Technicolor TG789vac v2 vdsl router, now I'm connected with a Zyxel.
The last 4/5 reboots went fine for ethernet. It's early to say that the problem is solved as it's episodical, but I hope so.

I had't before a strong idea to blame the router, cause I'm using it also with other linux machines through wifi connections, and they work well.
It's very interesting to know that the combination poor port signal + not perfect driver can generate this kind of random behavior.

Thank you very much for your support :)
I'll monitor the situation some other days, and I'll surely come back for a further feedback.

---

### Post by kenlibero on 2022-02-02
Here I am!
After one week with the new router, not a single ethernet fault at startup. Great :)
I guess we can mark this thread as solved.

I learnt something very useful:
> **TheFu said:**
> If the cable or switch ports are marginal then not-so-great drivers could matter.

Even if with other computers the previous router I used was ok, when it had to interact with the not-so-great realtek driver it randomly gave connection troubles.
So, as an alternative solution to mount an external ethernet card, you could also give a chance to that old router you have in a drawer ;)

Of course the best solution should be to solve the driver issues, but you know, sometimes it's just "Whatever Works".

Thanks again TheFu.

---

