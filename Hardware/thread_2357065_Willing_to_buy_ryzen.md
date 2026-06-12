---
title: "Willing to buy ryzen"
date: 2017-03-29
forum: Hardware
---

### Post by Dedalo on 2017-03-29
Hi there. I am willing to buy a new cpu to use as a workstation. I write programs in parallel fortran, and I use ubuntu as my OS, and compile with gfortran. I am not really urged to buy this computer, and I think I'll do it in the next months. I wanted to know how well is ubuntu working in ryzen, if I should wait to ryzen get more settled for bugs, optimization and prices. Also, if anyone wants to give me some recommendations on the specifications (motherboard I should buy, ram, hd, if ryzen 1700,1700x or 1800x, etc.) all will be greatly appreciated. The programs I run are heavy, so I need a lot of ram (32gb I think would be fine) and many processors as possible (I want to buy a ryzen 7). Is this a good idea or I have any better options with intel for the same amount of money?

Most important, if I buy a ryzen right now and install ubuntu with it, will it work everything fine?

Thanks in advance.

---

### Post by QIII on 2017-03-29
Hello!

There are problems, and there are anecdotal accounts of people who have gotten Ubuntu working with Ryzens.

One thing that is still very common, however, is that the limited selection of AM4 ***motherboards*** currently available almost universally demonstrate insurmountable problems with audio unless a separate audio card is used.

Personally, I've decided to wait for 3 - 6 months before I jump in -- unless one of my requests for gratis test hardware for blogging about comes in.

---

### Post by paulisdead on 2017-03-31
I actually came here to see what people were saying, since I decided to take the plunge and have the parts on the way now that newegg got the crosshair hero vi back in stock.

From the research I've done, I'm planning on installing the beta of ubuntu 17.04, for the updated 4.10 kernel.  From what I've heard there's crashing and SMT issues on pre 4.10 kernels.  If an older version of Ubuntu is needed, and you can't get the os installed, you could probably disable SMT, install the OS, and then install a kernel >=4.10, and then turn SMT back on.  I also picked the crosshair hero, since it has an Intel NIC, and those work really well on Linux (though it does amuse running an AMD cpu with Intel NIC and SSDs).

As QIII said, there's issues with the newer ALC1220 audio chip a lot of these boards use.  The 4.11 kernel, which is currently in a non-stable release candidate, does add support for it.  It should be stable enough for desktop use, though.  This is, however, the first driver for this chip, so it might not be very good.  I've got an Asus Xonar sound card I've been perfectly happy with, so I can use that.  I'm not sure if I even want to bother updating the kernel and trying the onboard audio, or just drop in this sound card.

The other thing is, it sounds like the hardware sensors for most of the boards aren't working in Linux yet.  That is going to make overclocking trickier for me, not being able to see temperatures inside the OS, but I can live with it.  I'll just have to stress test and reboot to BIOS really quick.

When playing games, it looks like I'll also want to switch from the powersave CPU governor to the performance governor.  There's some conjecture about why it helps frame rates so much, but it seems like when a game doesn't keep a core at full speed long enough, it throttles, and isn't up to full speed when it's needed again.  So the performance governor can help with framerates.

If you really want everything working out of the box, you'll likely have to wait until Ubuntu 17.10 comes out in October.

---

### Post by Dedalo on 2017-03-31
Thank you very much both of you. So, the audio problems can be fixed just by using an audio card? I think I'll wait a few months until everything works fine, but October sounds too much of waiting for me. Hope ubuntu 17.10 comes out earlier, is there any possibility for that? the other thing that scares me is the hardware sensors. I am planning to use the computer to make long runs, that could take some days of calculations. If the sensors are not working fine, I could get my computer burnt. I'm not planning to overclock it anyway.

In a few months I hope there are better suited motherboards for ryzen, but if I were going to buy one today, which would you recommend and which memory ram?

---

### Post by paulisdead on 2017-03-31
The hardware sensors I was referring to were just the ability to look at temps, fan RPM speeds and voltages inside the operating system.  The hardware can take care of itself, and if it overheats the cpu will throttle, or if it's extreme enough shutdown.  You shouldn't have any issues running it at stock speeds.

There's no chance 17.10 will come out early, the 17 refers to the year, and the 10 the month.  Ubuntu has been very steady and on time with their releases, one every april and another every october, but there's technically always a reason it could be delayed.

---

### Post by P-I H on 2017-03-31
I have a system with a Ryzen 7 1700 cpu, a MSI Tomahawk B350 motherboard and  Crucial Ballistix Sport DDR4 16GB 2x8GB 2400MHz (PC4-19200) DDR4 memory.
The system works fine with a 23% overclock with the stock Wraith Spire cooler. The system is using 98W when browsing and streaming HD content (usage when the inxi command was performed). Memory runs according to specification.
```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.10.0-14-generic x86_64 (64 bit)
           Desktop: Gnome Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Device: laptop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0
           UEFI: American Megatrends v: 1.20 date: 03/16/2017
CPU:       Octa core AMD Ryzen 7 1700 Eight-Core (-HT-MCP-) cache: 4096 KB 
           clock speeds: max: 3700 MHz 1: 1550 MHz 2: 1550 MHz 3: 1550 MHz
           4: 1550 MHz 5: 1550 MHz 6: 1550 MHz 7: 1550 MHz 8: 3700 MHz
           9: 1550 MHz 10: 1550 MHz 11: 1550 MHz 12: 1550 MHz 13: 1550 MHz
           14: 1550 MHz 15: 1550 MHz 16: 1550 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tonga PRO [Radeon R9 285/380]
           Display Server: X.Org 1.18.4 drivers: ati,amdgpu (unloaded: modesetting,fbdev,vesa,radeon)
           Resolution: 1920x1200@59.95hz
           GLX Renderer: Gallium 0.4 on AMD TONGA (DRM 3.9.0 / 4.10.0-14-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.2
Audio:     Card-1 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-2 Advanced Micro Devices [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380]
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-14-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
Drives:    HDD Total Size: 610.2GB (10.4% used)
           ID-1: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-2: /dev/sdb model: KINGSTON_SV300S3 size: 120.0GB
           ID-3: /dev/sdc model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 60G (28%) fs: ext4 dev: /dev/sdc2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: No active sensors found. Have you configured your sensors yet? mobo: N/A gpu: 61.0
Info:      Processes: 357 Uptime: 9:02 Memory: 3039.5/16059.3MB
           Client: Shell (bash) inxi: 2.3.8 
p-i@pi-MS-7A34:~$

```
There are however a couple of thousand unexpected warnings listed with the command
journalctl -p warning -b
These do not impact usability or boot time.
```
-- Logs begin at Fri 2017-03-31 11:47:16 CEST, end at Fri 2017-03-31 20:53:08 CEST. --
mar 31 11:47:16 pi-MS-7A34 kernel: IO_PAGE_FAULT device=24:00.0 domain=0x0003 address=0x000000f400239400 flags=0x0010]
mar 31 11:47:16 pi-MS-7A34 kernel: AMD-Vi: Event logged [
mar 31 11:47:16 pi-MS-7A34 kernel: IO_PAGE_FAULT device=24:00.0 domain=0x0003 address=0x000000f400238400 flags=0x0010]
mar 31 11:47:16 pi-MS-7A34 kernel: AMD-Vi: Event logged [
mar 31 11:47:16 pi-MS-7A34 kernel: IO_PAGE_FAULT device=24:00.0 domain=0x0003 address=0x000000f400239680 flags=0x0010]
mar 31 11:47:16 pi-MS-7A34 kernel: AMD-Vi: Event logged [
mar 31 11:47:16 pi-MS-7A34 kernel: IO_PAGE_FAULT device=24:00.0 domain=0x0003 address=0x000000f400238680 flags=0x0010]
mar 31 11:47:16 pi-MS-7A34 kernel: AMD-Vi: Event logged [
mar 31 11:47:16 pi-MS-7A34 kernel: IO_PAGE_FAULT device=24:00.0 domain=0x0003 address=0x000000f400239800 flags=0x0010]

```

There is a minor problem with the MSI motherboard as it takes about 20 sec before the system shows the boot screen.

---

### Post by Dedalo on 2017-04-02
Thank you, is really helpful and instructive to know your experiences, and all other help about things I don't know.

---

### Post by paulisdead on 2017-04-06
So I got most of the parts in (Newegg shorted me 5 of the 120mm fans I ordered) and got things built up with the Asus Crosshair Hero VI, and so far so good.  I didn't bother trying the onboard audio, but everything else is working.  I did manage to get the hardware sensors working by manually building this driver [https://github.com/groeck/it87](https://github.com/groeck/it87) and adding it87 to /etc/modules.
```

paulisdead@deepthought:~/Downloads/it87$ sensors
asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM

it8665-isa-0290
Adapter: ISA adapter
in0:          +0.49 V  (min =  +1.72 V, max =  +0.34 V)
in1:          +0.68 V  (min =  +0.38 V, max =  +1.93 V)
in2:          +1.97 V  (min =  +0.80 V, max =  +1.83 V)
in3:          +1.96 V  (min =  +2.64 V, max =  +0.74 V)
in4:          +0.56 V  (min =  +0.29 V, max =  +1.58 V)
in5:          +0.44 V  (min =  +2.76 V, max =  +0.71 V)
in6:          +0.89 V  (min =  +2.65 V, max =  +2.66 V)
3VSB:         +1.65 V  (min =  +0.11 V, max =  +1.21 V)
Vbat:         +1.56 V  
+3.3V:        +1.66 V  
fan1:         927 RPM  (min =   11 RPM)
fan4:           0 RPM  (min =   -1 RPM)
fan5:        5443 RPM  (min =   -1 RPM)
fan6:           0 RPM  (min =   -1 RPM)
temp1:        +40.0°C  (low  = -92.0°C, high =  -9.0°C)  sensor = thermistor
temp2:        +28.0°C  (low  = +103.0°C, high = -34.0°C)  sensor = thermistor
temp3:        +30.0°C  (low  = -14.0°C, high = -14.0°C)  sensor = thermistor

```

So it looks like some stuff is a bit off, but fan1 seems to be the first CPU fan, and fan5 looks like it's my AIO water cooler pump and those look right.  Voltages look way off, though.  The 40C for temp1 lines up with what I was seeing with Ryzen Master for the CPU temp.  The X models (1700X and 1800X) report their temps as 20C higher, so temps are looking really nice.

I've had some wonkiness with the board sometimes not booting up when I've got the ram at 3200mhz, but that's nothing specific to ubuntu, hopefully they fix that in the next bios update.

---

### Post by Dedalo on 2017-05-02
What would you recommend? should I wait a few more months? I think I will buy ryzen 7 1700, is that a good option or should I go for an X? which motherboard would you recommend, which memory ram? I also want to use CUDA, which gpu should I buy for a reasonable price/performance? is it OK to run CUDA in an nvidia gpu with amd cpu? which hard drive should I buy for better performance? does anyone know if CUDA is compatible with ubuntu and ryzen?

I don't think prices are going to get any better, but perhaps there will be better options for motherboards in a few more months, what you think? there will be any improvement from hardware for ryzen?

---

### Post by paulisdead on 2017-05-02
Depends on exactly what you want to do with the system.  The X models tend to overclock better, so if you're planning on that, it might be worth it.  I got my 1700X on sale, so it was only a $30 difference between the 1700 and 1700x.

I like my crosshair hero vi, but am using an add in soundcard.  Some of the B350 chipset motherboards use an older realtek chip, so they should work better under linux in the near term.  The 4.11 kernel can be installed for the newer alc 1220 sound chips, though.  I think I saw in another thread somebody returning a gigabyte board for bad linux support (I swore of gigabyte a long time ago for that and their quirky crap).  One of the reasons I got the crosshair hero was that it has an Intel NIC, which works great in Linux.  I haven't heard any complaints about the realtek nics, but you might check on a specific board before you grab it.

I returned the Corsair ram I got for the gskill FlareX that was made for Ryzen, and it's working much better and has no boot issues at 3200mhz.  You're also limited to 2 single die dimms if you want 3200mhz.  Which pretty much means if you want more than 16GBs of RAM, you're looking at a max of 2400mhz, so no sense in buying anything faster.  Unless the package says made for Ryzen, I'd check the Qualified Vendor List (QVL) for whatever board you decide on.

Cuda will work fine, it's pretty much platform agnostic.

Get an SSD over a hard disk if you can.  I got an Intel 600p NVME drive and it works fine in Linux on my board.  Samsung also makes some fine drives too.  Crucial's performance isn't great, but they've been reliable for me, at least.  Only reason to get a hard disk these days is as secondary bulk storage.  You really want programs and games and stuff to run off an SSD these days.  Stay away from OCZ, Mushkin and sandisk.  If the board has the slot, you can use one of the newer NVME drives which hook straight into the PCI-E bus.

There's not really going to be any sizable hardware improvement till a second generation, which I don't think we'll see before a year.  BIOS, driver and kernel updates will help a bit, though.  If you want to wait for better compatibility, I'd hold out till October when Ubuntu 17.10 comes out and has a newer kernel built in, that will affect things the most.

---

### Post by paulisdead on 2017-05-03
So I'm hearing on the asus forums that with the beta bioses, some people are managing to hit 3200mhz with 4 dimms of the gskill flarex.  Sounds like it's taking some tweaking with the bclk and loosening the timings, so if you're comfortable doing that, it's an option.

---

### Post by Dedalo on 2017-05-04
Thank you verymuch! really helpful post, I will take note of it all. I will wait until October. 

I will also want more than 16gb of ram, if I can pay it, I will get 64gb, because I want to work with really big systems of equations, and I think I will probably need it to store arrays and matrices.

The crosshair motherboard sounds nice, also the ram you mentioned. What if I want full speed of ram with 64gb? thank you verymuch! and which GPU would you recommend for hard programming work in CUDA?

---

### Post by paulisdead on 2017-05-04
With respect to memory it seems like things are in a bit of a flux on the platform now, so I can't say for sure, but I don't think they'll be able to run 64gbs over 2400mhz.  Things might work out with 32gbs with manual tweaking, but it's tough to say at the moment.

I haven't really played with Cuda, but it seems pretty much like with graphics as to what's best, the answer being "How much money do you really want to throw at this?"  There are the high end dedicated tesla cards for compute use that run thousands, the Geforce Titan models that are over $1000, and the various 10XX models going around right now.  Maybe check out some benchmarks and see what looks good for your budget, here's some from phoronix [https://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1070&num=4](https://www.phoronix.com/scan.php?page=article&item=nvidia-gtx-1070&num=4) you can probably find more benchmarks around on that site, and hopefully close to the usage scenario you want to use it for.  The benchmarks on that site are good, but sometimes the news can get a bit sensationalist.

---

### Post by Dedalo on 2017-05-05
Thank you verymuch.

---

### Post by Dedalo on 2017-06-10
Hey! I am lucky to have listened to you. Have you heard the news about the threadripper? there will be also a GPU by AMD that will be launched at the end of this month: 

Threadripper cpu: [http://wccftech.com/amd-threadripper-1920-12-core-cpu-vega-16gb8gb-cards-leaked/](http://wccftech.com/amd-threadripper-1920-12-core-cpu-vega-16gb8gb-cards-leaked/)

Vega gpu: [http://www.pcworld.com/article/3197095/components-graphics/amds-first-radeon-vega-graphics-card-isnt-for-you-and-gamers-may-be-waiting-a-while.html](http://www.pcworld.com/article/3197095/components-graphics/amds-first-radeon-vega-graphics-card-isnt-for-you-and-gamers-may-be-waiting-a-while.html)

According to what that link says, it is designed for scientists! I think I will still saving money until I can get a threadripper with one of this gpus, perhaps I'll get first the cpu, and when I can I'll get the gpu.

I would like to know if I'll be able to use double precision with these gpus, because that article only talks about single precision.

---

### Post by scpatl4now on 2017-07-05
I have been running a desktop with Ryzen 1700+ and 16GB RAM with ASUS Prime X370-Pro MB (I got it on sale for $50 off at Micro Center with bundled CPU) and I have had zero problems running 17.04 (problems are more with software).  It leaves my other system in the dust.  Video that would take an hour to encode on my other system literally takes 10 mins.  I am VERY happy with my purchase of Ryzen...just make sure you have the latest BIOS update.  They were coming out at a brisk pace for a while there.

---

### Post by Dedalo on 2017-08-01
Thanks for posting scaptl4now!

Does anyone know if the vega gpu is able to work with double precision? I've heard that gpu's mostly work in single precision, but I think that the ones that are made for professional development like cuda can work in double precision. Anyone know more about this? thanks.

---

### Post by pjssilva2 on 2017-08-02
I would probably avoid Ryzen for now. It seems to have problems with heavy multithread compilation. See this post:

[https://ubuntuforums.org/showthread.php?t=2367415](https://ubuntuforums.org/showthread.php?t=2367415)

---

### Post by mastablasta on 2017-08-04
is it a hardware or a software issue? does it affect users that don't do any compilation?

---

### Post by niet-giftig on 2017-08-04
> **mastablasta said:**
> is it a hardware or a software issue? 
That question is what´s the tread is about, and also the thread on the AMD forum
> **mastablasta said:**
> does it affect users that don't do any compilation?
eh,
Someone says : The brakes are not working properly as far as we can see!
You ask : Are the brakes only not working when I drive to New York?

If, I say **IF ** there is something wrong with the chip, then it occurs on the worst possible moment, that is when you do not expect it.

---

### Post by mastablasta on 2017-08-07
> **niet-giftig said:**
> 
eh,
Someone says : The brakes are not working properly as far as we can see!
You ask : Are the brakes only not working when I drive to New York?

If, I say **IF ** there is something wrong with the chip, then it occurs on the worst possible moment, that is when you do not expect it.

perhaps i missunderstood the thread? 

but to me it seems like the error is only showing to some users while others do not see it at all.

so to use your naalogy it woul dbe the breaks do not work on my new car. i would say it seems only you (and some others that bought certain lot/series) have a problem as they seem to work fine on my car. 

we would call them monday cars (cars made on moday). good brand car that keeps breaking. my father uncle had one of those (its engine even cracked and died), until they replaced it for a new car. worked nicely ever since.

anyway to move away from the cars the thread really describes how some poeple do not get the error at all.

furthermore i am intereste dis the erro showing only when compiling under GCC or would it actually give issues opening libre office doc, playing games? furthermore there is hardly any talk of any windows issues. only BSD and Linux for now. if it is a softwar eissue they will resolve it with firmware update (i mean other CPUs had issues on launch as well but were fixed later with updates).

furthermore if it's an issue that doesn't affect average home user (only those that do some major compiling) then it might be worth buying it now and updating it with firmware later.

---

### Post by niet-giftig on 2017-08-07
> **mastablasta said:**
> 
furthermore if it's an issue that doesn't affect average home user (only those that do some major compiling) then it might be worth buying it now and updating it with firmware later.

But until I'm sure that it does not affect the "average" home user, I keep a little distance.
Sometimes it will need a new stepping, and is not curable with microcode.

Last bits  I read is that a marketing person from AMD says :
AMD engineers found the problem to be very complex and characterize it as a "performance marginality problem exclusive to certain workloads on Linux. .
English is not my native language but..., wow language is beautiful
If handbrake is such a workload, then I do not like it

[URL="http://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Segv-Response"]http://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Segv-Response

[/URL]By the way, if there is a rumour that a special type of car has problems with the brakes, I would not buy the car.
Cannot take the risk, even if you say that you did not noticed it until now.
As usual there are people that are saying:  I do not have the problem, so it is not a problem.

---

### Post by mastablasta on 2017-08-08
> **niet-giftig said:**
> 
Last bits  I read is that a marketing person from AMD says :
AMD engineers found the problem to be very complex and characterize it as a "performance marginality problem exclusive to certain workloads on Linux. .
English is not my native language but..., wow language is beautiful
If handbrake is such a workload, then I do not like it


heh does not invoke confidence. although it is supposed to be a minor issue on linux. i wonder what about handbrake or compiling software on widnows 10?

Actually i was hoping just a first few batches were not good, not the whole architecture. still i wonder how come the problme doesn't appear for some (see links and bug report).

few years ago we had a bad rate on a few of our premium products. various solutions were tried and nothing made sense until it came out that obviously a batch of electronic controls was faulty. we took care of it in a very expencive way, but it was best for consumers. luckilly we caught most before they even came to consumers. quality control was tightened and so far so good. still it was a strange issue. it only appeared in some seemingly random cases.

---

### Post by TheFu on 2017-08-08
Segfault issue with Ryzen:
Overloaded CPUs - that's my simplistic description (probably wrong).
* [https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Test-Stress-Run](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Test-Stress-Run)
* [https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Segv-Response](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-Segv-Response) 
has more.

Be careful folks.  I've been seeing some nice deals - MB+CPU combos, but haven't purchased a Ryzen.  Waiting for them to completely, cleanly, solve the issue somehow.

---

### Post by mastablasta on 2017-08-09
to me the interesting part is that it affects **"some PC's"**.

another strange thing is the issue is not yet reported on windows (without any linux involvement). i would think someone saying the CPU is bad would want to test it on various OS. otherwise the claim just looks bad.

also the alternative is intel which with latest CPU won't have the same socket it seems. so if you got an older you wouldn't be able to upgrade it.
or if they can somehow fix it with software.

---

### Post by TheFu on 2017-08-09
Those posts come from a highly respected, linux-centric, website.  The issues are real.  He isn't the only one having them.  AMD has agreed.  He has tested it on multiple OSes ... different Linux kernels.  The issue is that AMD didn't test enough on Linux and has been caught.  We are a loud group of people.

The alternative is to wait until the solution comes.  Intel has had issues with new CPUs working correctly under Linux too. 

Intel changes sockets to help out MB vendors. That might not be the primary reason, but MB vendors have a history of trouble supporting different CPUs on the same socket.  Just look at the Xeon line with v2, v3, v4, v5 CPUs going into the same socket and not being supported.  It is the same when MB vendors change RAM requirements DDR-->DDR2-->DDR3-->DDR4.  In the real-world, changes in RAM performance are very slight and hardly worth it. It is mainly a way to force people to buy newer RAM so they can justify their prices.  I'd love to run my existing DDR3 on a new system. Sure, on paper there should be a 40% performance increase, but it doesn't work that way - more like a 3-7% increase.  Meh.  Hardly worth the added expense.

I really want a Ryzen-based system for the price/performance. Been watching them for about 4 months, waiting for all these issues to be well-understood AND solved.  With a 65W Ryzen 1600, I can replace 3 of my other systems. That is compelling for a $350 upgrade (MB+CPU+RAM).

---

### Post by mastablasta on 2017-08-09
i will wait for a bit more too before buying a new one. One of Ryzen 5 is on my mind for video processing. if issue is only on linux i might go sooner with a windows build. still i will wait a bit if they find anything on windows or preferably if they find a solution for linux. i would really like to go the linux way this time and slowly move away from windows.

---

### Post by vasa1 on 2017-08-10
I don't know if this is helpful or relevant: [ryzen-test]("https://github.com/suaefar/ryzen-test")

---

### Post by mastablasta on 2017-08-10
@Vasa - yes, that is the test.

looks like those made in July 2017 and later (actually W25 and later) are free of the bug. well at least this is what some are now saying. : [https://community.amd.com/thread/215773?start=735&tstart=0](https://community.amd.com/thread/215773?start=735&tstart=0)

i wonder if AMD would be confirming it even if it is true.

---

