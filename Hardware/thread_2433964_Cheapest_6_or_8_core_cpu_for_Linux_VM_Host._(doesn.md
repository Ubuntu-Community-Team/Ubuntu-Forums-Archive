---
title: "Cheapest 6 or 8 core cpu for Linux VM Host. (doesn't need to be brand new)"
date: 2019-12-28
forum: Hardware
---

### Post by bunny9000 on 2019-12-28
Hi all.

I'm trying to either migrate to or build a super-cheap VM lab host system on a 0$ budget. I don't want my upgrade or new system to use a boat load more electricity than my current system since I'm the one paying the bill and I don't need the cores be super fast, just need a few more of them.

**Use Case**

Main use case for my PC is a little light web browsing, but mostly project work requiring the running of virtual machines of up to 4 servers and guests combined with the option to run more.

[B]Current System
[/B]Linux Ubuntu Mate 18.04
i5 2400 quad core - Think this is sandy bridge.
 16GB DDR3 ram - Upgrade to 24 or 32 is on the cards if staying with this platform.
2x samsung evo 860 SSDs. 

**Problem**

Running 4vms with 3 to 4 cores flat-lines the machine even when I spread the vms between fast SSDs and spinners. It gets there - eventually.

**Current Train of thought** - I guess I've got a couple of options. 

I think the motherboard can handle an I7-3770S and those seem reasonably priced. That would get me up to 8 threads without a big investment and without a massive tdp. the i5 is a 95watt tdp and I think it drains about 110 or so watts from the wall.

An old intel exeon base system or gather an old xeon cpu and used motherboard, etc.

An old phenom 2 x6 cpu either pre built or build from parts.

The Ryzen 5 with 6 cores and ryzen 7 with 8 cores seems to be in vogue and they don't seem to be that expensive or power hungry for what you get but it's a lot more $$ and I wouldn't be able to use the ram from the i5 pc.

Buy another cheap 4 core desktop and spread the vm load over two machines.

Buy a cheaper machine with a compatible socket then throw away or sell the cpu and upgrade it.

**Thrown out options**

Old rack mounted servers are temping because 5 year old systems are cheap, but I know from experience rack mounted servers are loud and chew electricity and then you're dealing with SAS drives and possibly dual cpus and dual power units.

**So what you you do if you were running on a really low budget?**

---

### Post by crip720 on 2019-12-28
With 4 VMs plus host your ram is just a bit over 3GBs per machine, that is one bottle neck.  Might be best to spread out VMs over different machines, than having one do all the work and burning out.  Newer stuff might be easier on electric cost over time.  Need to decide on paying now or later or cutting down some where else.  One machine doing everything will cost more than two machines doing half the work.

---

### Post by bunny9000 on 2019-12-28
Yep. It might be cheaper for now to get a second PC. The cpu upgrades for this motherboard seem to be mostly from china and I'm not sure I'd trust them. The local ones are really expensive.

I was looking for a cheap way to get this pc into 8 cores, but by the time you've got the cpu upgrade you're into second hand quad core territory which can serve the purpose.

---

### Post by TheFu on 2019-12-28
I've run 20 VMs on 16GB of RAM.  RAM typically isn't an issue for most small/home VM uses that don't need GUIs .... or when Windows VMs are limited. People over allocate RAM all-the-time. Most of my servers get 1GB of RAM, no need for more.  Mine is only running 6 VMs now:
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        7.7G        2.8G        628K        5.2G        7.3G
Swap:          4.3G        1.5G        2.7G
```

I vaguely remember reading that Ryzen disk controllers have issues with samsung evo 860 storage devices.  This may or may not be the situation still. [https://eu.community.samsung.com/t5/Cameras-IT-Everything-Else/860-EVO-250GB-causing-freezes-on-AMD-system/td-p/575813](https://eu.community.samsung.com/t5/Cameras-IT-Everything-Else/860-EVO-250GB-causing-freezes-on-AMD-system/td-p/575813)   IDK.    By pure luck, I put an 860 into an 8th-gen Core i5 and a Micron SSD into a Ryzen 5 2600.  Both systems are nice, but the Ryzen is significantly faster for many reasons. 

As you know, Ryzen requires DDR4 RAM and really prefers 3000 Mhz or faster RAM. An upgrade would be RAM+CPU+MB and perhaps new storage.   A Ryzen 1600 is 6 core, 12 threads for US$80. Pair that with a $75 B450 motherboard and $70 of DDR4 RAM.

A Core i7-3770s is only 8900 passmarks. [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-3770S+%40+3.10GHz&id=897](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Core+i7-3770S+%40+3.10GHz&id=897) The cheapest I'm seeing this CPU is $280! Ouch.
A Ryzen 2600 (not X) is over 13,000 passmarks: [https://www.cpubenchmark.net/desktop.html](https://www.cpubenchmark.net/desktop.html) and US$120.
A Ryzen 1600 is 11,500 passmarks for $80.  The non-X Ryzen models are 65W THD.

If you have spare parts available and only need to replace the MB+CPU+RAM ($220 total), it will probably cost less than that Core i7 ($280) and provide 22% more passmarks.  Run the numbers and the costs.  Some things to consider.

These are prices that I can walk into a computer store here and get today. Actually, put 3 things into a cart 
BoM:
[LIST]
[*]Gigabyte B450 AORUS M AM4 mATX AMD Motherboard
[*]AMD Ryzen 5 1600 3.2GHz 6 Core AM4 Boxed Processor...
[*]G.Skill Ripjaws V 16GB 2 x 8GB DDR4-3200 PC4-25600...
[/LIST]
** $196.04.**

I have an Asus B450 MB, that exact RAM and a Ryzen 2600 CPU. You got options.  Heck, I'd replace my Core i5-750 with this setup if I didn't just order a new projector for the house. There's always next month. ;)

---

### Post by bunny9000 on 2020-01-10
Thanks for that 'thefu'. That iformation was really good. It was a really tough choice though. 

In the end I decided to upgrade the RAM in the desktop to (2x8GB) + existing 2X4GB = 24GB and sell 2 of the old 2x4GB sticks. I brought a hardware based RAID card because I just felt safer than going software raid so because vms I set it up in a simple raid 0 for faster disk IO. The card can go up to RAID 10 so there is more options for lab stuff. It doesn't destroy boot time either and it wasn't that expensive. 

I then decided as I'm writing this to install XCP-NG and run the PC as a full hypervisor. I love virtualbox, but as far as I can tell it has static ram allocation. Hyper V, XCP & vsphere to name a few have dynamic RAM so I can / could run more VMS with the 16GB I had. I wasn't that impressed with the other kernel based hypervisors.

I did also ended up with a low powered quad core DDR3 1U rack server. Nothing quite like running a server to keep your neighbours up all night. This will also run XCP-NG and it will be run only when really needed.

Off to go setup stuff now :)

I agree, there is always next month. For now I'm OK with the setup.

---

