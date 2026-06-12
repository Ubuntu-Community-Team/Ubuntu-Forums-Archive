---
title: "New motherboard bundle recommendations please"
date: 2019-03-21
forum: Hardware
---

### Post by iamtheeggman2 on 2019-03-21
Hi

I was just wondering if you had any fast but quiet motherboard recommendations for upgrading the pc. I don't want to spend more than £100 but it's not a tight budget. I am obviously not looking for state of the art.. But maybe I might want to play mid spec games in the future.

---

### Post by TheFu on 2019-03-21
What do you have today?  Some system information will provide some facts.

Here's mine on this machine:
```
$** inxi -v 1**
System:    Host: posc Kernel: 4.15.0-46-generic x86_64 (64 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
CPU:       Quad core Intel **Core i5-8250U** (-HT-MCP-) speed/max: 800/3400 MHz
**Graphics:  Card: Intel UHD Graphics 620**
           Display Server: X.Org 1.19.6 driver: intel
           Resolution: 1920x1080@60.01hz
           GLX Renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2)
           GLX Version: 3.0 Mesa 18.0.5
Drives:    HDD Total Size: 500.1GB (6.0% used)
Info:      Processes: 258 Uptime: 3 days **Memory: 3090.0/7859.5MB**
           Client: Shell (bash) inxi: 2.2.35 
```
I've bolded the most important items.  Passmark estimate for Core i5-8250U is about 7600.  Note how the motherboard isn't even listed? I'm using on-board GPU, so not great for gaming (I don't game).

Another box here:
```
$ inxi -v 1
System:    Host: hadar Kernel: 4.15.0-43-generic x86_64 (64 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
CPU:       Hexa core AMD **Ryzen 5 2600** Six-Core (-HT-MCP-)
           speed/max: 1413/3500 MHz
**Graphics:  Card: NVIDIA Device 1d01**
           Display Server: X.Org 1.19.6 driver: nvidia
           Resolution: 1920x1080@60.01hz
           GLX Renderer: N/A GLX Version: N/A
Drives:    HDD Total Size: 1000.2GB (51.2% used)
Info:      Processes: 276 Uptime: 18 days **Memory: 2696.2/15970.9MB**
           Client: Shell (bash) inxi: 2.2.35 
```
Passmark about 14,400 - so twice as fast, roughly.

A new motherboard isn't going to make a PC faster.  A new GPU and new CPU will.  What is important to you will be how much faster can a new CPU be and how much does it cost to get one?  Almost always, a new CPU means a new MB and perhaps new RAM and a new GPU will be required.  The GPU drives the MB, which drives the RAM choice.  For £100, I doubt any upgrade would be worth it besides just a GPU.  On a really slow box, an SSD upgrade from a spinning HDD would be more noticeable, unless the machine is from 2012 or earlier. Around 2012, MB bus architectures expanded to handle much more throughput.  I have a few systems from 2010 still. They can't handle USB3 bandwidth, but a cheap system from 2014 doesn't have any issues with lots of USB3 devices at all.

Motherboards don't make any noise. It is the cooling, which is a case and PSU problem, that makes the noise. Cooling is required for the GPU, HDDs, SSDs, and CPU. An 80% "bronze" PSU will generate less heat for the power than cheapo, included-with-case PSUs.  Those can usually be found cheap - saw a Seasonic 650W for $40 earlier this week. Higher efficiency PSUs make even less heat, which need less cooling, which means slower fans, which means the system will be quieter.

£100 isn't much.  Over here there have been MB+CPU bundles for $120 with an AMD Ryzen 1600. The stock cooler, included, is fairly quiet.  If you don't have compatible DDR4 RAM to reuse, I don't see how you can bother with an upgrade. Get the budget to £200 and it starts making sense.  I would stay away from the Ryzen2 with on-board GPUs for another year, but Ryzen2 2600/2700 are amazing values right now.  

So ... please post some facts about the current system. We can't read minds.

---

### Post by iamtheeggman2 on 2019-03-21
house@house:~$ inxi -v 1
System:    Host: house Kernel: 4.15.0-45-generic i686 bits: 32
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.1 LTS
CPU:       Dual core AMD Athlon II X2 250 (-MCP-) speed/max: 1800/3000 MHz
Graphics:  Card: NVIDIA GK208 [GeForce GT 710B]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1024x768@75.03hz, 1024x768@75.03hz
           OpenGL: renderer: GeForce GT 710/PCIe/SSE2/3DNOW!
           version: 4.6.0 NVIDIA 390.77
Drives:    HDD Total Size: 502.1GB (3.1% used)
Info:      Processes: 200 Uptime: 8 min Memory: 805.7/2011.7MB
           Client: Shell (bash) inxi: 2.3.56 
house@house:~$

I don't think i spent much more than £100 when i bought this like ten years ago. The thing is, at the time, windows was a lot slower than linux so i stuck with linux,however, i have been pleasantly surprised by seeing how fast windows 8.1 runs on my laptop, so i was thinking about getting another motherboard bundle (mb cpu ram) withing a decent price range to see how well it would cope on today's standards. my main priority is silence, i am concerned that with the faster cpus you can expect more heat issues and thus faster and noisier fans...

---

### Post by TheFu on 2019-03-21
Athlon II X2 250 is about 1700 passmarks. You've had a good run with that, but new MBs and CPUs are in a completely different class for performance and throughput. I'd suggest picking an AM4 MB that is compatible with Ryzen and the best CPU you can get for the remaining cash - so compatible A6/A8 or Ryzen.  Any Ryzen that doesn't have an onboard GPU would be suggested now because the onboard GPUs require a kernel that isn't default to even boot.  If Ryzen is outside your range, at least an A8. Not sure it will do midrange games.

Always check the passmarks for any CPU. Similar model numbers can have huge differences in performance.  I was comparing a 9600 and 9500 - one was about 5000 passmarks and the other are about half that.  Be careful.

DDR4 RAM is still getting cheaper. Ryzen likes 3000MHz and faster RAM. That also needs to be considered. 4G is a low-RAM system these days, so aim for 8G.

---

### Post by mastablasta on 2019-03-22
for games the GPU is much more important than the CPU, so if you buy a CPU without GPU, invest into the GPU as much as you can.

my has passmark less than 500 i believe, so the numbers above make me drool. :)  anyway i added the GT730 to this PC (70 EUR) and the PC can run most games to about 2012 with more or less tweaking. actually i ran some newer ones as well but they were not so graphically intense (strategy games, platformers...). most of heavy processing for games is usually done on GPU anyway. so in theory if you jammed a stronger GPU in there you would see a boost for games. the 710 - these 10 series are meant to watch movies on HD, not really for gaming. i checked their comparison when i was my GPU died and found out they are slower than my (at the time) 13 year mid range old GPU card. 

also midspec games do OK on the new intel GPUs and as mentioned the A6/8 sersies seem to support games well. not sure how quiet they are though. 


you are correct - more power, means more heat, means fans (or if you want quiet you need watter cooling system). 
fans can also be good, there are some very quiet ones out there. larger fans are usually quieter. i have a server with very large fan (no fan on the CPU/GPU) and it is really quiet, you can barely hear it.

---

### Post by iamtheeggman2 on 2019-03-24
which software do you run for passmark results?

---

### Post by Dennis N on 2019-03-24
For the CPU, you can just find your processor model on this web site and get the scores:
[https://www.cpubenchmark.net/](https://www.cpubenchmark.net/)

---

### Post by TheFu on 2019-03-24
> **iamtheeggman2 said:**
> which software do you run for passmark results?

I just look them up. All benchmarks like passmarks are sorta contrived workloads that nobody in the real would actually experience. OTOH, they do provide a weighted method to compare common end-user task performance between different CPUs and chipsets.  You may notice that I used rounded up/down numbers for the passmarks in post in these forums.  Identical systems will have slightly different results.  Systems based on the same CPU with different MB supporting chips will be a little more different.  But in the big scheme of things, does that really matter to people like us just wanting to know relative performance to about 500 passmark accuracy?

If you can get a 12,000 passmark CPU for $80 or a 6,000 CPU for $70, which would you pick?  That's the sort of decision making we are talking about.  Or of a CPU is $80 for 12,000 passmarks and another is $180 for 12,500 passmarks, which would be a better choice?  This is generally the AMD Ryzon vs Intel Core i5 value proposition these days.

The Intel i5 includes a iGPU, that could be very important for non-gamers.
The Intel i5 has fewer cores, but each is faster than the Ryzen. That could be important for gamers where fewer threats are used.  
You get to weight these different options.

I got an nvidia 1030 GPU for my build for a few different reasons. It was a hassle to get working the way I needed mainly because they dropped VGA output. I wanted the 10xx GPU to have little longer driver support. Was let down with my older 7200gs and Quadro cards that wouldn't work at the resolution I wanted in the new box.  Knowing what I know today, I'd take a long look at AMD GPU cards.  My knowledge of them is almost non-existent, but driver support has to be better for a 2 yr old GPU than what I've seen.

---

### Post by Dennis N on 2019-03-24
> Drives: HDD Total Size: 502.1GB (3.1% used)
In your system upgrades, I would replace this 500 gB HDD your information shows with an SSD. This single move will most likely give you a very noticeable improvement in performance.

Comment:
Our oldest computer (still being used) in this household has the same Athlon II X2 250 processor. I built it using an Asus BIOS motherboard in 2011. Replacing it's HDD with an SSD made a big difference in usability.

---

### Post by iamtheeggman2 on 2019-03-24
> **Dennis N said:**
> In your system upgrades, I would replace this 500 gB HDD you information shows with an SSD. This single move will most likely give you a very noticeable improvement in performance.

Comment:
Our oldest computer (still being used) in this household has the same Athlon II X2 250 processor. I built it using an Asus BIOS motherboard in 2011. Replacing it's HDD with an SSD made a big difference in usability.

Hi, 

It is not 3.1% used at all its way beyond that. Its totally inaccurate on that issue.

> **Dennis N said:**
> For the CPU, you can just find your processor model on this web site and get the scores:
[https://www.cpubenchmark.net/](https://www.cpubenchmark.net/)

Hi, FX 8300 AM3 is something I am considering buying but I can't get a result on that site...

---

### Post by Dennis N on 2019-03-24
> **iamtheeggman2 said:**
> Hi, FX 8300 AM3 is something I am considering buying but I can't get a result on that site...

Is this what you are looking for?
[https://www.cpubenchmark.net/cpu.php?cpu=AMD+FX-8300+Eight-Core&id=1825](https://www.cpubenchmark.net/cpu.php?cpu=AMD+FX-8300+Eight-Core&id=1825)

---

### Post by iamtheeggman2 on 2019-03-27
Hi there

I bought the amd FX-8350 8 with 14gb ram plus its got a a large silent cooler master heat sink so it is quiet. Bought ssd too to use as primary drive.

---

### Post by pqwoerituytrueiwoq on 2019-03-27
If you wanted to run some light games without running on the lowest quality setting the game allows, bear in mind this will go over budget (close to double if you get it new)
i would suggest a ryzen apu 2200g/2400g (i forget the 1st gen model number)
4GBx2 DDR4 3200
some compatible board you can get cheap
a decent aftermarket cooler can quite stuff down if you find it loud, Hyper 212s run as low as $15 when they are on sale in the US

---

### Post by Dennis N on 2019-03-27
> **iamtheeggman2 said:**
> Hi there

I bought the amd FX-8350 8 with 14gb ram plus its got a a large silent cooler master heat sink so it is quiet. Bought ssd too to use as primary drive.

I noticed that one too when I first searched for the 8300 processor. Smart decision to add the SSD. Enjoy your new system.

---

### Post by iamtheeggman2 on 2019-03-31
Well I can confirm it runs pretty well with ubuntu, though I had a few crashes which I first blamed on the ram because 4gb was not being recognised. However it turns out that the some of the sticker on the stick of ram itself was covering some of gold contacts! I have however upon removing continued to get crashes from the NVIDIA card I had installed. Luckily I noticed the crash some several times during boot up and it read nouveau. Luckily I had a radeon card spare so that has been put in and I've had no problem since.

From power to loading sky news under 50 seconds and that's on the old hdd and I'll install the ssd this morning.

---

### Post by kurt18947 on 2019-03-31
I don't know if this is current, I became aware of it a few months ago. The GPU integral to some Ryzen processors would not allow booting Ubuntu 18.04. My MoBo is an Asrock AB350M. I have a Ryzen3 2200G (the G means it has an integrated Vega GPU) and it wouldn't boot when the monitor was connected to the onboard video. My fix was to install a couple years old AMD based video card and connect to that. Now the machines boots and works great. I'm not a gamer so not having a bleeding edge GPU is not an isssue. I'm not sure when this problem will be fixed or perhaps it already has been fixed. Something to check into though.

---

### Post by iamtheeggman2 on 2019-04-01
BTW on Windows ten this using a ssd boots in 20 seconds or so

> **kurt18947 said:**
> I don't know if this is current, I became aware of it a few months ago. The GPU integral to some Ryzen processors would not allow booting Ubuntu 18.04. My MoBo is an Asrock AB350M. I have a Ryzen3 2200G (the G means it has an integrated Vega GPU) and it wouldn't boot when the monitor was connected to the onboard video. My fix was to install a couple years old AMD based video card and connect to that. Now the machines boots and works great. I'm not a gamer so not having a bleeding edge GPU is not an isssue. I'm not sure when this problem will be fixed or perhaps it already has been fixed. Something to check into though.

Interesting, thanks.

---

