---
title: "slow computer"
date: 2014-06-06
forum: Hardware
---

### Post by Thylacine1 on 2014-06-06
My computer seems to be very slow. I am using Ubuntu 12.04 LTS and did a hardinfo system report and got the following, which is only an excerpt from the full report


[TABLE]
[TR]
[TD="class: sstitle, colspan: 2"]Computer[/TD]
[/TR]
[TR]
[TD="class: field"]Processor[/TD]
[TD="class: value"]4x Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz[/TD]
[/TR]
[TR]
[TD="class: field"]Memory[/TD]
[TD="class: value"]3908MB (2201MB used)[/TD]
[/TR]
[TR]
[TD="class: field"]Operating System[/TD]
[TD="class: value"]Ubuntu 12.04.4 LTS
[/TD]
[/TR]
[/TABLE]

......[TABLE]
[TR]
[TD="class: stitle, colspan: 2"][TABLE]
[TR]
[TD="class: stitle, colspan: 2"][/TD]
[/TR]
[TR]
[TD="class: sstitle, colspan: 2"]Processors[/TD]
[/TR]
[TR]
[TD="class: field"]Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz[/TD]
[TD="class: value"]1197.00MHz[/TD]
[/TR]
[TR]
[TD="class: field"]Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz[/TD]
[TD="class: value"]1197.00MHz[/TD]
[/TR]
[TR]
[TD="class: field"]Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz[/TD]
[TD="class: value"]1197.00MHz[/TD]
[/TR]
[TR]
[TD="class: field"]Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz[/TD]
[TD="class: value"]1197.00MHz[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[/TR]
[TR]
[TD="class: field"]Does this mean that my CPU is broken, or does it mean that something is slowing it down, because as I understand it, all four cores should be running at 3.07 GHZ?
[/TD]
[/TR]
[TR]
[TD="class: field"]Do I need to get a new CPU ?
[/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: field"][/TD]
[TD="class: value"][/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2014-06-06
To save power, Intel CPUs slow down automatically.  Relax.
[https://en.wikipedia.org/wiki/SpeedStep](https://en.wikipedia.org/wiki/SpeedStep)

---

### Post by Thylacine1 on 2014-06-06
Thanks, I guess. But now I do not know why my computer is so slow. It seems strange to me that you can plug a computer into a car and have it tell you what is wrong with the car, but you can't get a computer to tell you why it is underperforming, or even, apparently, get reliable user-friendly software to plug into your computer to analyse it without being a computer genius. Any suggestions would be helpful.

---

### Post by QIII on 2014-06-06
Hello!

If your car's engine were running at 5000 RPM at a stoplight, you would be concerned that something was wrong.  Not so much if it's running at 750 RPM.  

Just like that engine, your cores should not be running at 3.07GHz if your computer is at idle.  If they were, that would indicate that something is wrong.  The CPU should throttle down when it idles, just like your car.  When you need to accelerate and you step on the gas, the RPMs increase.  You don't want your car red-lining at a stoplight.

Can you quantify "slow".  "Seems slow" is subjective.  What exactly do you mean by slow, and what are you doing at the time?

---

### Post by TheFu on 2014-06-06
> **Thylacine1 said:**
> Thanks, I guess. But now I do not know why my computer is so slow. It seems strange to me that you can plug a computer into a car and have it tell you what is wrong with the car, but you can't get a computer to tell you why it is underperforming, or even, apparently, get reliable user-friendly software to plug into your computer to analyse it without being a computer genius. Any suggestions would be helpful.

Oops. Since the data was all about CPUs, I mistakenly thought your "running slow" issue was just about the CPUs slowing down when there isn't a workload that requires more ... or when running on battery.

Performance for any computer comes down to the following items:
* CPU
* RAM
* Disk I/O
* Network I/O
* System Tuning Parameters

There are tools to watch each of these things. More complex tools watch them all.  Many people know that it is better to ahve performance data BEFORE there is any issue, so we setup system monitoring that runs every minute for years.  This provides a baseline for comparison, if/when anything "different" occurs.

Since I run servers, the tools that I use for these things are rather involved to setup and use.  One of the more simple tools that works on desktops and servers is SysUsage. However, I don't think you should install it. It isn't a simple GUI.  

Some very simple tools are top, ntop, saidar and nmon .
When the computer is slow, what is using all the CPU, RAM, Disk & Net I/O?  That's what you want to figure out first.  Often it is just running too much crap concurrently on an underpowered system.  Sometimes it is due to hardware starting to fail.

I've heard of conky - don't know much about it. Might be useful, but so is turning down the GUI "cheese."

---

### Post by varunendra on 2014-06-07
> **TheFu said:**
> Performance for any computer comes down to the following items:
* CPU
* RAM
* Disk I/O
* Network I/O
* System Tuning Parameters

Just want to add two more important factors, since they are common reasons -

* Correct drivers for devices
* CPU/system temperature

Most often, when a potentially powerful computer is performing slow, especially in Linux, the reason is an inefficient graphics driver.

Quite less often, mostly in older systems but can happen in brand new ones too, the system becomes slow, even to a crawling speed if the CPU or the VRM (Voltage Regulation Module) section overheats.

The common reasons for CPU overheating are too much dust in the heat-sink, improper contact between CPU and heat-sink, bad, dried or no heat-sink compound (the creamy heat-transferring-agent) between CPU & heat-sink, stopped (broken or stuck) heat-sink-fan.

The most common reason for VRM section (the MOSFETs and other parts around CPU that control its current and voltage) overheating is no air flow over it, which usually happens when a user replaces the stock heat-sink with one whose air-flow is not downwards (towards the motherboard), and does nothing to dissipate heat from the VRM section MOSFETs. Motherboards like Asus prevent damage to the parts in this case by throttling down the FSB, resulting in slower CPU performance.

To see which graphics card(s) and driver(s) you have, please show us the outputs of -
```
lspci -nnk | grep -iA3 vga
```

To monitor temperatures of system components, you can install 'psensor' (a GUI program) -
```
sudo apt-get install psensor
```

But like QIII, I would also like to first know how you quantify "slow". Any particular observations? Practical examples?

**PS:**
I know I went over the edge above, but I blame ***TheFu*** for provoking me by providing that list, I couldn't resist the urge to try completing it. :p

---

### Post by Thylacine1 on 2014-06-07
Thanks guys. You're all wonderful. I did try "top" but as far as I could see everything was in order.
here is the VGA 
michael@ubuntu:~$ lspci -nnk | grep -iA3 vga
01:00.0  VGA compatible controller [0300]: Advanced Micro Devices, Inc.  [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] [1002:68f9]
    Subsystem: Micro-Star International Co., Ltd. Device [1462:2120]
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

I have also installed psensor as you suggested. I don't run a lot of crap on my machine, have two almost empty 230 Gb HDD and with an i3 540 and 4Gigs of RAM i would have thought that it would handle things quicker than my old laptop with a 1.7GHz processor and 2 Gigs of RAM. I do only text, email and internet, no gaming and only occasionally editing of photos, yet everything from booting, downloading, loading programs, switching screens etc is slower than the laptop, which also runs Ubuntu 12.04 LTS.

---

### Post by varunendra on 2014-06-07
**[COLOR="#FF0000"]CAUTION![/COLOR]** Fiddling with graphics may lead to a unusable OS, forcing you to either do some extensive troubleshooting, or even reinstall it!

You are currently using 'fglrx' proprietary driver for your graphics card which is usually supposed to deliver better performance, but I have seen issues with it here on the forums. As such, I'd suggest you try the native one.

Your card is this : [http://www.pcidatabase.com/search.php?device_search_str=0x68f9&device_search=Search](http://www.pcidatabase.com/search.php?device_search_str=0x68f9&device_search=Search)
It is known to be well supported by the native driver : [https://help.ubuntu.com/community/RadeonDriver#Fully_Supported](https://help.ubuntu.com/community/RadeonDriver#Fully_Supported)

To properly remove (purge) the fglrx driver, note this section on the page linked above : [https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver](https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver)
..which leads to : [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx)

Once properly purged, you should automatically be using the native driver since next boot. Confirm that with -
```
lspci -nnk | grep -iA3 vga
lsmod | egrep 'fglrx|radeon'
```
In the first command's output, "Kernel driver in use" should be "radeon". In the second output, you should see only "radeon", no "fglrx". If so, is the performance improved?

If the performance remains the same, or even goes down, you can reinstall the fglrx driver by simply accepting the driver proposed by "Additional Drivers" program, or following this (scary) guide : [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

**PS:** I don't take responsibility for any flames or smoke that may come out from the notebook while trying all this :-\"

---

### Post by QIII on 2014-06-07
Hey!  It's not scary!  At least not the parts of it I wrote!  Sections 2.1, 4 and 5.2 are some of the best instructions I have ever seen on the internet!  :)

---

### Post by varunendra on 2014-06-07
> **QIII said:**
> Hey!  It's not scary!  At least not the parts of it I wrote!  Sections 2.1, 4 and 5.2 are some of the best instructions I have ever seen on the internet!  :)

Happy onboard/embedded graphics user here, always! Those ATI/Nvidia issues and their troubleshooting procedures are alien territories for me. So you see, I got no donuts for you. But have some digital popcorn for the hard work (shows in the instructions) you've done! :popcorn:

---

### Post by TheFu on 2014-06-07
One more thought - often slow computers really are just slow DNS servers. That can make an otherwise fast system, feel slow. There is a tool that will find the fastest (not necessarily the most trusted) DNS server for your location.  I ran that a few months ago, found the fastest DNS that didn't rob my privacy, then setup my home router to use it and all the systems here to only point to the router for DNS. The fastest was NOT my ISP, BTW.

Oh - and I have 1 system that uses the fglrx driver.  After every new kernel is installed, I manually reinstall that driver like this:
```
sudo aptitude --reinstall install fglrx 
 export DISPLAY=:0
 fglrxinfo 

``` There are other steps, but those can only be performed when X/Windows is NOT running. That means stopping all GUIs - even the login manager, then running some aticonfig commands.  Yours will be different from mine, so I won't post them here. RTFM to see the options. The system with the ATI GPU is for a silent media center running Plex and XBMC - fairly specialized.


How is this system connected?  If wifi, try wired to see how much that helps.  wifi connections can be terrible or great. If it has been awhile, use a wifi analyzer to determine if your neighbors are screwing with your connection.  I discovered last night that a close neighbor 
had gotten a new router installed that was on the same frequency as mine. Throughput sucked the last few weeks.  Need to change to a different channel this morning.  28 or 30 systems here are wired, so the change in performance due to wifi interference really isn't noticeable for the lite-surfing done on those. I expect a 20% performance boost by just changing the channel on the router this morning.

Anyway - gives you some more things to look into.

---

