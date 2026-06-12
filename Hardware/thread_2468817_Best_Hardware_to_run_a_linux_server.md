---
title: "Best Hardware to run a linux server"
date: 2021-11-10
forum: Hardware
---

### Post by bydataarts on 2021-11-10
Iam looking to build a low power linux Server to run some cameras around the house and host my files. iam looking to spend about 500-600$

---

### Post by TheFu on 2021-11-11
> **bydataarts said:**
> Iam looking to build a low power linux Server to run some cameras around the house and host my files. iam looking to spend about 500-600$

Don't think I'd bother with a full Linux.  A friend was looking to setup property monitoring for about 10 homes and had decided to use cheap raspberry pi computers with the "official" pi camera.  In the end, he got it working, but for much greater hassle and added expense of using typical small-biz/consumer camera connected to a webapp on a cloudy service with an annual fee.

You didn't really provide any details about the requirements.
[LIST]
[*]Any specific camera hardware required?
[*]Night vision?
[*]Wired or wifi cameras?
[*]IP or some other protocols are fine?
[*]Resolution?
[*]Video or still photography only?
[*]Is power available or will batteries be needed?  If batteries - will they be easily accessible or do you need 1-2 yr lifespans?
[*]Are there privacy (legal) considerations?
[*]Any specific software already selected that must be supported?
[*]Does this need client access over the internet?
[*]How many concurrent viewers need to be supported per feed/stream?
[/LIST]

If you plan to setup a house with 5 bdrs and 25 cameras with video feeds, that is very different than having 2 cameras used to watch a dog during the day.

$500 seems very high cost for a 2 camera system, but it is nowhere near what a 25 camera system would need.

I would prototype any solution on either hardware I already own or get a $50 raspberry pi to use as a "server".  If you want a real server with real server hardware, you'll either need to alter your budget to be around $2500 or go with used hardware that is very noisy, hot, and power hungry.  Some of those older servers will only work with the Ubuntu release of the same year they were released, though I hope that doesn't happen nearly as often any more.  The cheapo, new, Dell "servers" in the ~$500 price area tend not to actually have server capabilities - just a case that appears to be a server. No redundant PSUs, no redundant internal buses, no DRAC/IPMI ... no dual NIC setups and no HW-RAID controller.

So ... what do you really mean by "server"?

---

### Post by Tadaen_Sylvermane on 2021-11-13
I can't give specifics on what you should get. I can give you a current running example of mine at the moment.

```
top - 13:57:27 up 4 days, 12:37,  2 users,  load average: 0.78, 0.75, 0.72Tasks: 293 total,   2 running, 290 sleeping,   0 stopped,   1 zombie
%Cpu(s): 18.3 us,  2.0 sy,  0.0 ni, 78.7 id,  0.1 wa,  0.0 hi,  0.9 si,  0.0 st
MiB Mem :  15724.2 total,    180.8 free,   5207.8 used,  10335.6 buff/cache
MiB Swap:   6144.0 total,   4512.7 free,   1631.2 used.  10125.6 avail Mem
```

This machine is currently running (all docker) a minecraft server not currently being accessed, mariadb that is in use regularly by at least 4 clients at any given time, mythtv backend that is running a single tuner at the moment, zoneminder with a single camera (this was to test more than anything) as well as basic file sharing / backup target. It is mostly in the above range all the time. This is the hardware I'm using. Got the system on Craigslist for 100 bucks, added most of the hard drives and ssds. Doesn't take much for basic stuff around the house. Yes it is old and uses a bit of power but at the same time the cost to build a new machine that would use less power would take 5 or 10 years to pay for itself at best but would then be that old already. 

```
sudo inxi -CDIM
Machine:
  Type: Server System: Intel product: S1200BTL v: ....................
  serial: 140825021
  Mobo: Intel model: S1200BTL v: E98681-352 serial: QSBT41301767 BIOS: Intel
  v: S1200BT.86B.02.01.0044.072520181346 date: 07/25/2018
CPU:
  Topology: Quad Core model: Intel Xeon E31225 bits: 64 type: MCP
  L2 cache: 6144 KiB
  Speed: 1596 MHz min/max: 1600/3400 MHz Core speeds (MHz): 1: 1596 2: 1596
  3: 1596 4: 1596
Drives:
  Local Storage: total: 9.43 TiB used: 7.22 TiB (76.5%)
  ID-1: /dev/sda vendor: Crucial model: CT120BX500SSD1 size: 111.79 GiB
  ID-2: /dev/sdb vendor: Seagate model: ST95005620AS size: 465.76 GiB
  ID-3: /dev/sdc vendor: Western Digital model: WD10EURX-63UY4Y0
  size: 931.51 GiB
  ID-4: /dev/sdd vendor: Seagate model: ST1000NM0055 91Y1655 LENOVO
  size: 931.51 GiB
  ID-5: /dev/sde vendor: Western Digital model: WD40EZRZ-22GXCB0 size: 3.64 TiB
  ID-6: /dev/sdf vendor: Western Digital model: WD10EURX-63UY4Y0
  size: 931.51 GiB
  ID-7: /dev/sdg vendor: Seagate model: ST2000LM007-1R8174 size: 1.82 TiB
  ID-8: /dev/sdh vendor: HGST (Hitachi) model: HTS541075A9E680 size: 698.64 GiB
Info:
  Processes: 291 Uptime: 4d 12h 43m Memory: 15.36 GiB used: 5.49 GiB (35.7%)
  Init: systemd runlevel: 5 Shell: bash inxi: 3.0.38
```

---

