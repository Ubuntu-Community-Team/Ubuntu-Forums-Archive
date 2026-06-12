---
title: "Upgrading CPU"
date: 2021-04-06
forum: Hardware
---

### Post by daniell59 on 2021-04-06
While I wait for computer component prices to return to normal, I am thinking of upgrading the CPU on my dinosaur. Presently I have E8400 2 core CPU. I see offerings on Ebay for a four core CPU that is also for socket 775. Would I notice a difference? Presently all is well except when I watch live Youtube videos. The CPU usage hits 100 percent, then the computer locks up.

---

### Post by Autodave on 2021-04-06
How much RAM do you have?  What version of 'buntu are you running?  Have you tried running *uBlock *on your browser?

---

### Post by daniell59 on 2021-04-06
> **Autodave said:**
> How much RAM do you have?  What version of 'buntu are you running?  Have you tried running *uBlock *on your browser?

RAM 4 GIG
Ubuntu 20.04
I don't know what uBlock is.

---

### Post by CatKiller on 2021-04-06
> **daniell59 said:**
> Presently all is well except when I watch live Youtube videos. The CPU usage hits 100 percent, then the computer locks up.
The ideal solution to that would be to, by hook or by crook, enable hardware acceleration for the video decoding process, so that you don't have to do it all in software on the CPU. The media decoding block is included with GPUs - both dedicated and integrated - but support varies. Newer decoding blocks are needed for newer encodings - like VP9 - but there are browser extensions to request streams encoded with the older H.264 if that turns out to be what you end up with hardware support for.

---

### Post by rsteinmetz70112 on 2021-04-06
Looking at this depending on motherboard you may well be able to upgrade the CPU and may see a performance increase.
Is the computer using all of its RAM and starting to swap before it locks up? More RAM (if possible) may help.
The website [https://www.cpu-upgrade.com/](https://www.cpu-upgrade.com/) about cpu upgrades for many motherboards.

---

### Post by oldfred on 2021-04-06
If you do not have an SSD, that would give you the biggest bang for the buck.

I had an old dual core2 system and in 2011 added a tiny 60GB SSD. System was so much better I put off upgrading to a new system for 3 years.

---

### Post by daniell59 on 2021-04-06
> **oldfred said:**
> If you do not have an SSD, that would give you the biggest bang for the buck.

I had an old dual core2 system and in 2011 added a tiny 60GB SSD. System was so much better I put off upgrading to a new system for 3 years.

I have recently installed an SSD. It did make a big difference. As I previously mentioned, my main concern is the computer locking up while watching live Youtube videos.

---

### Post by Autodave on 2021-04-06
[I]uBlock 

[/I]is an add-on for your browser.  It does a great job of blocking ads and other things running in the background.  It allows more of your computing power to go to what you want: the video.  Try it: you have nothing to lose.

---

### Post by poorguy on 2021-04-06
> **daniell59 said:**
> Presently I have E8400 2 core CPU. I see offerings on Ebay for a four core CPU that is also for socket 775.

Make certain that your existing motherboard bios will support the processor you are getting before purchasing the processor.

Make sure that there is an available bios upgrade if you need to upgrade your motherboard bios to support a quad core processor.

Just because the socket is an LGA775 doesn't mean the motherboard and bios will support the processor you are wanting.

Do you're homework and research well and make sure all of your bases are covered before purchasing a different processor.

---

### Post by mastablasta on 2021-04-07
if it's locking up when at full power it is likely overheating or losing power from PSU. monitor temperatures with psensor. if temperature goes too high, you might need to reaply the paste, get a better cooler/fan, increase the air flow...

also it all depend how much a used CPU will costs you. but getting high CPU on videos means you GPU is not doing it's job, so getting a GPU that will support at least videos, will also help. but again you need to see why the lockups are happening and i just retired one of these E CPUs. it had constant issues. overheating, i would get it new thermal paste and cleaned it up. it would work for a while then it started with lockups and reboots. i changed the PSU. it helped for a week or two and then it started again. finally i had enough and my kid bought an old model Ryzen on sale while this E3300 retired.

problem right now is that even older models of CPU and GPU are expensive.

---

### Post by daniell59 on 2021-04-07
> **mastablasta said:**
> if it's locking up when at full power it is likely overheating or losing power from PSU. monitor temperatures with psensor. if temperature goes too high, you might need to reaply the paste, get a better cooler/fan, increase the air flow...

also it all depend how much a used CPU will costs you. but getting high CPU on videos means you GPU is not doing it's job, so getting a GPU that will support at least videos, will also help. but again you need to see why the lockups are happening and i just retired one of these E CPUs. it had constant issues. overheating, i would get it new thermal paste and cleaned it up. it would work for a while then it started with lockups and reboots. i changed the PSU. it helped for a week or two and then it started again. finally i had enough and my kid bought an old model Ryzen on sale while this E3300 retired.

problem right now is that even older models of CPU and GPU are expensive.
A used processor on Ebay can be purchased for $10. Not a big gamble.
This is from the motherboard manual
LGA775 socket for Intel® CoreTM2 Extreme/CoreTM2
Quad/ CoreTM2 Duo/Pentium® dual-core/Celeron® dual-
core /Celeron® Processors
Compatible with Intel ® 05B/05A/06 processors
Support Intel ® 45nm Multi-Core CPU

---

### Post by mastablasta on 2021-04-08
make sure what is wrong first. you might end up upgrading and still have the same issue.

---

### Post by hk42 on 2021-04-08
Although not understanding a word of it I was
inspired by this video:
[https://www.youtube.com/watch?v=w132eifHeWk](https://www.youtube.com/watch?v=w132eifHeWk)
I replaced an E5200 dual core by a second hand XEON  5450 quad core:
[https://fr.aliexpress.com/item/2041514744.html](https://fr.aliexpress.com/item/2041514744.html)
All went well and speed was multiplied by 3.
Very cheap upgrade just assure you have good cooling.

---

### Post by poorguy on 2021-04-08
> **daniell59 said:**
> RAM 4 GIG
Ubuntu 20.04


I'd increase memory before I'd upgrade the processor.
I'm running Ubuntu 20.04.2 on an Intel E7400 and I have 8.0GB of memory and Ubuntu flies.

```


Dell-OptiPlex-XE:~$ inxi -Fxz
System:    Kernel: 5.8.0-48-generic x86_64 bits: 64 compiler: N/A Desktop: Gnome 3.36.7 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Desktop System: Dell product: OptiPlex XE v: N/A serial: <filter> 
           Mobo: Dell model: 0TNXNR v: A01 serial: <filter> BIOS: Dell v: A05 date: 01/09/2013 
CPU:       Topology: Dual Core model: Intel Core2 Duo E7400 bits: 64 type: MCP arch: Penryn rev: A 
           L2 cache: 3072 KiB 
           flags: lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx bogomips: 11171 
           Speed: 1596 MHz min/max: 1600/2800 MHz Core speeds (MHz): 1: 1596 2: 1596 
Graphics:  Device-1: Intel 4 Series Integrated Graphics vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           Display: wayland server: X.Org 1.20.9 driver: i915 resolution: 1024x768~60Hz 
           OpenGL: renderer: Mesa DRI Intel Q45/Q43 (ELK) v: 2.1 Mesa 20.2.6 direct render: Yes 
Audio:     Device-1: Intel 82801JD/DO HD Audio vendor: Dell driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
           Sound Server: ALSA v: k5.8.0-48-generic 
Network:   Device-1: Broadcom and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe vendor: Dell 
           driver: tg3 v: kernel port: 0980 bus ID: 05:00.0 
           IF: enp5s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
           Device-2: Broadcom and subsidiaries NetXtreme BCM5761 Gigabit Ethernet PCIe vendor: Dell 
           driver: tg3 v: kernel port: 0980 bus ID: 06:00.0 
           IF: enp6s0 state: down mac: <filter> 
Drives:    Local Storage: total: 149.05 GiB used: 7.63 GiB (5.1%) 
           ID-1: /dev/sda vendor: Western Digital model: WD1600AAJS-22PSA0 size: 149.05 GiB 
RAID:      Hardware-1: Intel SATA Controller [RAID mode] driver: ahci v: 3.0 bus ID: 00:1f.2 
Partition: ID-1: / size: 145.22 GiB used: 7.63 GiB (5.3%) fs: ext4 dev: /dev/sda5 
Sensors:   System Temperatures: cpu: 31.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 192 Uptime: 21h 50m Memory: 7.68 GiB used: 1014.3 MiB (12.9%) Init: systemd 
           runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
Dell-OptiPlex-XE:~$ 



```

---

### Post by dddman on 2021-04-08
I have recently tried Ubuntu in 2 & 4 core configurations and found 2core usable, but a bit slow and 4 core to be visibly faster.  I'm currently running 4 core and 4G of ram and its plenty fast.

---

### Post by poorguy on 2021-04-08
To be fair I ran Ubuntu on dual core processors and 4.0GB of memory for years and had no complaints.

I found 8.0GB of memory at a garage sale for $10.00 bought it and installed it and what a difference 8.0GB of memory makes.

I guess it all boils down to what each user considers to be fast and what each user is used to using.

All of my computers are Frankenstein builds created from spare parts and discarded computers.

---

### Post by TheFu on 2021-04-08
I had a system with that same CPU. It had 16G of RAM and easily handled 10+ virtual machines concurrently. In order of upgrades that will matter most for watching youtube.
[LIST=1]
[*] New GPU with hardware support AND ubuntu drivers to decode mpeg/h.264 and h.265 video
[*] More RAM - 4G is anemic today.  8G is a happy place for Linux OSes.
[*] Newer CPU - compare passmark ratings for both CPUs to temper your expectations.
[*] Faster SSD - there's only so much that a SATA SSD can do. Perhaps 550 MB/sec.
[*] Tuned swap to 4.1G on all desktops; more isn't better.
[*] Clean dust from the system, cables, coolers, fans, everywhere. Get heat under control for each component.
[/LIST]

When the E8400 CPU was created, Intel wasn't doing onboard iGPUs yet.  For youtube video, any chromebook would be faster, regardless of CPU.  Why?  Because the GPUs all have hardware support for decoding hidef youtube video. That is a key decision that google and chromebook manufacturers require.  Video playback is all about the GPU and drivers.

---

### Post by hk42 on 2021-04-08
[> **TheFu said:**
> 
When the E8400 CPU was created, Intel wasn't doing onboard iGPUs yet.  For youtube video, any chromebook would be faster, regardless of CPU.  Why?  Because the GPUs all have hardware support for decoding hidef youtube video. That is a key decision that google and chromebook manufacturers require.  Video playback is all about the GPU and drivers.
Even quite expensive and power hungry old graphic cards are less efficient at decoding HEVC and UHD than a recent cheap mobile phone.
But I believe they are good for games.
Having OS and swap on an SSD is a good improvement for old hardware.

---

### Post by daniell59 on 2021-04-08
At this point I wish that the motherboard would die. This would give me the motivation to build a new system. Now what do I do with the two 10 + year old Lian LI cases? They are aluminum with a removable MB tray. The problem with them is the 80mm fans. Discarding them would be like abandoning an old sick dog.

---

### Post by rsteinmetz70112 on 2021-04-08
I think I have only one case newer that 10 years old, of course Ive replaced motherboards and PSU fans and drives in all of them.

---

### Post by TheFu on 2021-04-08
> **daniell59 said:**
> At this point I wish that the motherboard would die. This would give me the motivation to build a new system. Now what do I do with the two 10 + year old Lian LI cases? They are aluminum with a removable MB tray. The problem with them is the 80mm fans. Discarding them would be like abandoning an old sick dog.

all my cases are over 20 yrs old.  Reuse. Buy $20 ones to sell older computers.

---

### Post by guiverc on 2021-04-08
I doubt I can provide much more, however I'll provide the following

The closest cpu I have to yours is 
- dell [optiplex] 755 (c2d-e8300, 8gb, amd/ati radeon rv610/radeon hd2400 pro/xt)

and it's a system I don't mind using at all. In fact it's pretty much equivalent to another
- dell [optiplex] 780 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)

I needed to test a *problematic* box [*vostro 430*] so stole 4GB of RAM each out of those two boxes (*as I knew those two boxes were reliable and they had the correct DDR3 RAM I needed*) for testing; hey it would only be for days-weeks and I didn't expect the drop from 8GB to 4GB to make much difference - but boy was I wrong.

Both machines instead of being a *joy* to use with 8GB of RAM, became a *chore* to use, for the same tasks I then performed on them.  Tweaking *swap* on the boxes restored some of the performance drop, but RAM matters.  Both machines are great again, as they've got their RAM back (both at 8GB again).


FYI:  [COLOR=#0000cd]*In using the two systems, I don't actually notice a difference between the c2d-8300 & c2q-9400, in fact usually don't know or care which box I'm using (as they both share the same screens/mouse/keyboard), but what I notice and what you notice will be very dependent on how we use our machines & what we're doing.  *

*Last year I moved my primary Debian Bullseye/sid from the 755 to the  780, not because of speed/cpu, but the 780 has larger disks; and it  freed up the 755's disk so it could be use for full disk QA-testing  installs which was the huge benefit of the move... Faster cpu may have  entered my thinking, but all I remember now in the why I made the move  was disk space.  If there is a cpu speed difference, it's not  significant in my experience. but again it'll depend how you use your  box.*
[/COLOR]
*My 2c.*

---

### Post by daniell59 on 2021-04-09
> **rsteinmetz70112 said:**
> I think I have only one case newer that 10 years old, of course Ive replaced motherboards and PSU fans and drives in all of them.

Do you think that a case that is limited to 80mm fans should be ruled out for modern builds?

---

### Post by TheFu on 2021-04-09
> **daniell59 said:**
> Do you think that a case that is limited to 80mm fans should be ruled out for modern builds?

Why?  CPUs today use 50% less power than 10 yrs ago for 2x+ more performance.  The only people I know with cooling issues have hot GPUs or 6 HDDs inside the case or a power-hungry CPU pulling 125+W.  I have just 1 2010 CPU pulling 125W on the CPU.  All the newer CPUs, I've specifically selected to use 65W or less.

My newest Ryzen 5 65W peak CPU has a $70 fanless GPU and an m.2 SSD.  Other storage for it is in a NAS (just another Ubuntu Server system) on the network. Besides the PSU fan, it doesn't have any case fans.  Cooling isn't an issue.  The stock CPU cooler it came with quickly brings the temperature down when the system isn't busy. When it is busy, it gets to the max allowed temperature, 95 C, but most of the time, it is below 50 C.

---

### Post by rsteinmetz70112 on 2021-04-09
> **daniell59 said:**
> Do you think that a case that is limited to 80mm fans should be ruled out for modern builds?

Only one of my current cases has had any cooling problem. Most of them are tower style but I have a some full size desktop cases, a few 2U rack cases which typically have at least 4 HDDs and a couple of shorter cases. They generally do not have case fans and use only the PSU to draw air through the case. The 2U rack cases do have multiple fans in them. The case I had problems with is a shorter mid-tower case so I added a case fan which solved the problem. I have an identical case I've never had problems with. Since I recently replaced the motherboard I haven't had any problems even without the case fan. I don't do gaming, lots of video nor do I overclock the CPUs so generally the load on the computers is fairly light.

---

### Post by mastablasta on 2021-04-12
what about USB ports? mine still has 2 USB2.0 ports at the front. case has one 80 mm fan i added and it pulls out any extra the heat nicely. 

i was thinking about replacing only the motherboard, CPU (would need a Ryzen 5 or Core i5) and ram (as much as possible & i could afford - maybe 32 GB?!) and milk the GPU while it lasts. it has 3 HDD drives, 2 DVD drives (not that they are used much - i think one can only write&read CD and read DVD but not write them) and a floppy drive. i was thinking of replacing floppy drive maybe with a card reader or to add a SSD drive. but i am not sure card reared would be worth it. i do have USB card reader i got for few eur a while back from Aliexpress and is working just fine when i need it. 

i do play games occasionally but mostly i like older ones. so for now the GT730 works well (and supports the VGA output to my 1280x1024 monitor) and when i upgrade it would be within this range or maybe something similar to GTX 1650 (could be an AMD equivalent), so i could try some of the newer games as well. power shouldn't be an issue. system has a descent 2 year old 500 W bronze PSU. i have old single core Athlon and it never overheated the box so far. 

another option is to get a new box (maybe miniITX) and use this one as video server. maybe add some wireless controller for some old platform or racing games.

---

### Post by daniell59 on 2021-06-14
I am continuing getting lockups when watching live Youtube videos, especially when opening other windows.
I said to myself. Let me try it with Windows 10 which  unlike Ubuntu, it on a hard drive. Ubuntu is on an SSD. No matter what I do, I cannot get the computer to lockup. Why?

---

### Post by daniell59 on 2021-06-15
How do I troubleshoot Ubuntu?

---

### Post by TheFu on 2021-06-15
> **daniell59 said:**
> How do I troubleshoot Ubuntu?

Start by looking at all the log files in /var/log/ for errors and warnings. If you google "ubuntu log files" some tips to make that easier should come up.

If the log files aren't saved between reboots, there is a setting that will keep them longer. It requires editing the journald.conf file. The file has self-documenting style and points to more detailed information.  But I think they changed the defaults to keep logs between boots after a few months of not keeping any logs.

There are new-school and old-school methods to search the logs. I'm old-school, but think the new log system tools that came with systemd actually made searching and accessing specific logs 100x easier.

Always start with the log files.   Always.  Actually read them. Read the errors. Often, the error will provide a solution.  Try that.  Failing that, copy/paste the error with timestamps and hostnames removed into google and see what the world has to say about any specific error.

---

### Post by daniell59 on 2021-06-16
The lockups are becoming more frequent. My latest log. I have no idea what this means.

---

### Post by mastablasta on 2021-06-16
just lock up it is difficult to troubleshoot. i had this motherboard that no matter what i changed and tried (software and hardware) it just keep having one or another issue. i threw it away.

if windows works but Ubuntu doesn't it can be due to:

[LIST]
[*]drivers (for GPU or motherboard)
[*]overheating (power management is off - drivers are at fault but can also be a setup in system) - psensor will show if overheating is the issue
[*]slightly faulty ram (window uses ram differently than Linux. it loads it differently. so sometime the error in one system is not noticed because of that.
[/LIST]

i have very old laptop. no matter what windows XP that came with it crashed. needless to say it had too low ram anyway (384 MB of which 32MB was reserved for GPU). it worked for about 10 minutes and then it would lock, freeze... anyway i installed linux on it and no such issues.

anyway, use what works best. if windows works good on it and has no issues, then just use that. it is not a bad OS and no matter what, it still beats wasting time troubleshooting and getting Ubuntu to work.

---

### Post by daniell59 on 2021-06-16
> **mastablasta said:**
> just lock up it is difficult to troubleshoot. i had this motherboard that no matter what i changed and tried (software and hardware) it just keep having one or another issue. i threw it away.

if windows works but Ubuntu doesn't it can be due to:

[LIST]
[*]drivers (for GPU or motherboard)
[*]overheating (power management is off - drivers are at fault but can also be a setup in system) - psensor will show if overheating is the issue
[*]slightly faulty ram (window uses ram differently than Linux. it loads it differently. so sometime the error in one system is not noticed because of that.
[/LIST]

i have very old laptop. no matter what windows XP that came with it crashed. needless to say it had too low ram anyway (384 MB of which 32MB was reserved for GPU). it worked for about 10 minutes and then it would lock, freeze... anyway i installed linux on it and no such issues.

anyway, use what works best. if windows works good on it and has no issues, then just use that. it is not a bad OS and no matter what, it still beats wasting time troubleshooting and getting Ubuntu to work.

Thanks for your thoughtful reply. The only think that I am sure of is that it is not overheating.

---

### Post by rsteinmetz70112 on 2021-06-16
Sometime stuff just happens. I have one computer that is supposed to be a Windows 10 workstation which I cannot install Windows 10 on. I can't figure out why. I can run a live session of Ubuntu or install Windows 7 but no matter what I do Windows 10 installs fail. I have at least 10 other Windows workstations with the same model motherboard and similar, if not identical, CPUs, memory and SDDs. I've replaced the memory (twice) and the SDD once and still is won't install. 
I know this has nothing to do with the OPs issue but it illustrates the random variability of hardware.

---

### Post by daniell59 on 2021-06-16
It seems that the lockup problem is limited to Firefox. I have been using Google Chrome, and so far I have not experienced any system freezes. Also, Google Chrome uses less of my CPU and RAM resources. I hope this continues to be the case.

---

### Post by TheFu on 2021-06-17
> **daniell59 said:**
> It seems that the lockup problem is limited to Firefox. I have been using Google Chrome, and so far I have not experienced any system freezes. Also, Google Chrome uses less of my CPU and RAM resources. I hope this continues to be the case.

Did you look at the log files?  We don't need to be guessing.  The logs HAVE the answer for what the issue is and sometimes they have the solution too.

If there is nothing in the logs (doubtful), .... 

If it is just firefox, have you tried running in safe-mode? There is a command line option for that. It doesn't have any extensions.
If it still crashes in safe mode, I'd force a reinstall of firefox, then restart the program.
If it still crashes, then I'd look at the GPU drivers.
If it still crashes, then I'd look at swap and RAM allocations.  Ensure you have at least 4.1G of swap.  The **swapon -s** command will show the current swap.

Check the log files.

---

### Post by daniell59 on 2021-06-17
> **TheFu said:**
> Did you look at the log files?  We don't need to be guessing.  The logs HAVE the answer for what the issue is and sometimes they have the solution too.

If there is nothing in the logs (doubtful), .... 

If it is just firefox, have you tried running in safe-mode? There is a command line option for that. It doesn't have any extensions.
If it still crashes in safe mode, I'd force a reinstall of firefox, then restart the program.
If it still crashes, then I'd look at the GPU drivers.
If it still crashes, then I'd look at swap and RAM allocations.  Ensure you have at least 4.1G of swap.  The **swapon -s** command will show the current swap.

Check the log files.

Thanks for your informative reply. This will be a challenge for me.

---

### Post by TheFu on 2021-06-17
> **daniell59 said:**
> Thanks for your informative reply. This will be a challenge for me.

Really?

Google: "ubuntu log files"
Google: "firefox safe-mode"
Google: "ubuntu gpu crash"
Google: "ubuntu swap size setup"

It can be useful to put the Ubuntu release number into the google query for things that change based on the release.

With the GPU, 21.04 made Wayland the default and the release notes for that release (21.04) has specific information. 

>  I don't know what uBlock is. 
Did you google "ubuntu uBlock"?  10 seconds and you'd know the answer.

Use whatever web search tool you like. In general, Bing sucks for Linux questions, so perhaps use some other search tool.  I don't use google all the time for privacy reasons, but sometimes the other tools fail.

---

### Post by rsteinmetz70112 on 2021-06-17
I will say I have experienced lockup caused by Firefox. I believe they are generally related to graphics hardware/drivers. My solution is to use another browser.

---

### Post by Yellow Pasque on 2021-06-17
If you're sure there's no overheating, run Memtest to verify RAM integrity

---

### Post by daniell59 on 2021-06-17
> **Yellow Pasque said:**
> If you're sure there's no overheating, run Memtest to verify RAM integrity

I did that. It showed 0 problems after one pass. Do you think that I need more passes?

---

### Post by TheFu on 2021-06-17
> **daniell59 said:**
> I did that. It showed 0 problems after one pass. Do you think that I need more passes?

YES!  Leave it running overnight.

Did you look at the log files yet?!!!!!!!!!!!!!  Guessing isn't helping.  The answer is 99% in those logs.

---

### Post by daniell59 on 2021-06-18
> **TheFu said:**
> YES!  Leave it running overnight.

Did you look at the log files yet?!!!!!!!!!!!!!  Guessing isn't helping.  The answer is 99% in those logs.

I find the logs somewhat overwhelming. Page after page. I do not know what to look for. First off, what category, hardware

---

### Post by TheFu on 2021-06-18
> **daniell59 said:**
> I find the logs somewhat overwhelming. Page after page. I do not know what to look for. First off, what category, hardware

I'd look for *errors* and *warnings*, but you feel free to do what you think is best.

It is a good idea to scan through an entire log file at least once ... see what's inside. Don't let your eye glaze over. Actually read the lines.  As with most new things, our first look can be a little scary. The more we look, the better we become at pulling information out.  If we never make the effort, we won't improve.

---

### Post by oldfred on 2021-06-18
My system seems to be working ok, but I get at least two screen fulls of messages, all warnings.

sudo egrep -i 'warn|error' /var/log/*g

---

### Post by TheFu on 2021-06-18
> **oldfred said:**
> My system seems to be working ok, but I get at least two screen fulls of messages, all warnings.

sudo egrep -i 'warn|error' /var/log/*g

Two screens is better than thousands of pages. ;) Quite manageable.  Plus realizing that some "warnings" are just kernel messages about hardware our system(s) don't have is useful over the long term.

Log-fu is a skill.

---

