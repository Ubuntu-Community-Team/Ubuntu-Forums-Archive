---
title: "Help Me With Computer Build"
date: 2020-12-14
forum: Hardware
---

### Post by daniell59 on 2020-12-14
My present computer is 10 plus years old. Ready to build a new one.
I wont be using it for gaming.
I will be using a Ryzen CPU.

Some questions. Should I buy an APU CPU or go for a discrete video card?
The Ryzen 4750G looks interesting but is only available to big builders. 
B550 motherboard or 570?

---

### Post by DuckHook on 2020-12-14
> **daniell59 said:**
> …Should I buy an APU CPU or go for a discrete video card?
No gaming, but will you use other graphics&#8209;intensive apps like CAD, 3D modelling or video editing? If so, then dedicated graphics card would be better. Otherwise, APU is cheaper. I like the flexibility of a dedicated graphics card on my main rig, but servers are all APU because I need nothing more than basic graphics. It all depends on your use case.
> …B550 motherboard or 570?
Again, what is your use case? Do you need the features of the 570? If not, then no need to spend the cash.

---

### Post by daniell59 on 2020-12-15
> **DuckHook said:**
> No gaming, but will you use other graphics&#8209;intensive apps like CAD, 3D modelling or video editing? If so, then dedicated graphics card would be better. Otherwise, APU is cheaper. I like the flexibility of a dedicated graphics card on my main rig, but servers are all APU because I need nothing more than basic graphics. It all depends on your use case.

Again, what is your use case? Do you need the features of the 570? If not, then no need to spend the cash.

Thanks for your informative reply. I wont be using the computer for graphics intensive apps. Which would be more Linux friendly?

---

### Post by TheFu on 2020-12-15
Beware that some of the network adapters in the newer B550 and B570 motherboards are NOT working out of the box and may not on an LTS until kernel 5.10 is in the HWE kernel.  This leads to a chicken-egg problem.  The solution is to spend $25 to get an addon NIC or USB-GigE adapter and to use that for a few months.  Watch out for motherboards with 2.5Gbps onboard NICs. The vendor doesn't seem to matter. Even Intel has problems and has since March.

I like Ryzen and have one.  Is there a specific workload you are trying to solve?  In general, the Ryzens with on-board GPUs are on the lower performance scale, so if you can live with 10K passmarks instead of 22K+ passmarks, then the "G" CPUs with iGPU would be fine.

To get good advice, you'll need to be much more specific about your workloads.  At this point, most of the Ryzens CPUs/APUs are crazy expensive from just 6 weeks ago. It is a bad time to be building.  If you can, wait a few months for the prices to come down after availability isn't a problem anymore. While it shouldn't matter, CPU prices tend to follow bitcoin and bitcoin has been raising as normal financial companies are afraid not to be involved in some way.

Do research on motherboard capabilities - 
do you need 32G of RAM or 64G or 128G or 256G?
do you need 4, 6, 10 or more HDD connections?
do you need NVME for 1, 2, 4 storage devices?  If you use 2 NVMe, what does that do with the SATA ports available?
do you need 1, 2 or more ethernet ports? What speed?
do you need audio with optical (Toslink) out?
how many monitors do you want to support? Are their limits for the onboard DisplayPort such that daisy chaining doesn't work with 3 monitors?
what existing hardware do you plan to reuse?  For example, I have a VGA KVM-switch which connects 4 computers to my primary monitor. It uses ps2 keyboard and mice connectors, so I have USB-to-ps2 converters for most of the computers.  If I had to replace that KVM-switch and monitor, that would probably cost $400 more.

We can't answer those questions for you.

Make a spreadsheet/table of what you need and each motherboard being considered. Check all details. You may need to pull the manual down for the final few models that mostly match your needs to compare some details.

pcpartpicker.com is useful, but often has incorrect/incomplete data.

---

### Post by daniell59 on 2020-12-15
> **TheFu said:**
> Beware that some of the network adapters in the newer B550 and B570 motherboards are NOT working out of the box and may not on an LTS until kernel 5.10 is in the HWE kernel.  This leads to a chicken-egg problem.  The solution is to spend $25 to get an addon NIC or USB-GigE adapter and to use that for a few months.  Watch out for motherboards with 2.5Gbps onboard NICs. The vendor doesn't seem to matter. Even Intel has problems and has since March.

I like Ryzen and have one.  Is there a specific workload you are trying to solve?  In general, the Ryzens with on-board GPUs are on the lower performance scale, so if you can live with 10K passmarks instead of 22K+ passmarks, then the "G" CPUs with iGPU would be fine.

To get good advice, you'll need to be much more specific about your workloads.  At this point, most of the Ryzens CPUs/APUs are crazy expensive from just 6 weeks ago. It is a bad time to be building.  If you can, wait a few months for the prices to come down after availability isn't a problem anymore. While it shouldn't matter, CPU prices tend to follow bitcoin and bitcoin has been raising as normal financial companies are afraid not to be involved in some way.

Do research on motherboard capabilities - 
do you need 32G of RAM or 64G or 128G or 256G?
do you need 4, 6, 10 or more HDD connections?
do you need NVME for 1, 2, 4 storage devices?  If you use 2 NVMe, what does that do with the SATA ports available?
do you need 1, 2 or more ethernet ports? What speed?
do you need audio with optical (Toslink) out?
how many monitors do you want to support? Are their limits for the onboard DisplayPort such that daisy chaining doesn't work with 3 monitors?
what existing hardware do you plan to reuse?  For example, I have a VGA KVM-switch which connects 4 computers to my primary monitor. It uses ps2 keyboard and mice connectors, so I have USB-to-ps2 converters for most of the computers.  If I had to replace that KVM-switch and monitor, that would probably cost $400 more.

We can't answer those questions for you.

Make a spreadsheet/table of what you need and each motherboard being considered. Check all details. You may need to pull the manual down for the final few models that mostly match your needs to compare some details.

pcpartpicker.com is useful, but often has incorrect/incomplete data.

Thanks for your thoughtful and informative reply. I am not in any particular rush. Somebody with a 10 year old computer is obviously not in a hurry for the latest and greatest. My present computer, Asus P5Q is working adequately on Ubuntu 20.04 except in one case. When I watch live stream youtube videos, it becomes sluggish after several minutes. 
I am thinking of waiting for the Ryzen 4750G to hit the retail market. I don't want to pay $400 for a gray market one.

---

### Post by TheFu on 2020-12-15
> **daniell59 said:**
> Thanks for your thoughtful and informative reply. I am not in any particular rush. Somebody with a 10 year old computer is obviously not in a hurry for the latest and greatest. My present computer, Asus P5Q is working adequately on Ubuntu 20.04 except in one case. When I watch live stream youtube videos, it becomes sluggish after several minutes. 
I am thinking of waiting for the Ryzen 4750G to hit the retail market. I don't want to pay $400 for a gray market one.

Just some more things for consideration.

I have a Core i5-750 from 2010. It is time to replace that system and consolidate another (Pentium G3258) into the new, yet to be determined, system.  I've been retiring 125W CPUs for 65W and less power hungry CPUs the last few years.  I use lots of virtual machines, but always plan to have 2 physical systems, each capable of running all the VMs alone. The simple swap to lower power CPU has materially impacted the house electric bill. I never would have thought it possible, but our electric bills have been about $5-$10/month less since retiring a Core i7-920 (2009) for a Ryzen. 

My new system is a Ryzen 5 2600 with an Asus B450 motherboard. It is 2 yrs old this month. With 2 sticks of RAM, it is very stable.  With 4 sticks of RAM (same exact RAM model), I have to reduce the RAM speed from 3200 Mhz to 2800 Mhz for good, multi-week, stability.  Any faster and the system will crash under load within 3 days. I should return the 4 sticks of RAM together to get a replacement "set" from the vendor. It is lifetime warranted. I didn't need to double the RAM until about 6 months ago. In general, the system uses about 40% of the RAM under load, even today.

The Asus motherboard I picked has an onboard i211 GigE NIC.  That was a very specific choice for me for a number of reasons that are important to my needs. Under heavy network loads, Intel just does better than the other alternatives at this price-point.

Power use is under 210W total for 4 computers, 2 external arrays, multiple external storage devices, multiple routers, switches and our VoIP phone system, according to UPS measurements.  Newer computers are much more efficient with power than 10 yr old systems. Even 5 yr old systems aren't nearly as efficient.

---

### Post by daniell59 on 2020-12-15
Three years ago I built a computer for my wife.
Asrock AB350 Pro
Ryzen 3 2200G

She could not be happier.

---

### Post by mastablasta on 2020-12-16
if you don't have special needs and dont' need the latest, then get a Ryzen 5 3xxx series, add dual channel ram 2x8 GB or 2x16 GB and a nvme disk. you won't know what hit you. my kid got a laptop with Ryzen 5 3600, onboard AMD Vega 8 GPU,  8GB single channel ram, 256gb nvme drive. youtube & internet runs well, school work runs, older games like CS GO, minecraft, garys mod, team fortress2 run very well. apparently (based on online tests) many of newer games would run just as well, but he is not interested into them at the moment. some had Doom 2016 running on this config. so a massive overkill for your stated needs. price of laptop was 410 EUR, no OS pre-loaded. in Germany they were selling them with larger drive and more ram or DVD drive in them for about a 100 -150 EUR more.

also if you don't plan to expand later on (add multiple disks, GPU card and such) then have a look at NUC machines. they have a couple of Ryzen ones out there.

for you tube videos, internet browsing... Intel i3 and Ryzen 3 are more than enough. Ryzen 5 or Intel i5 (even a bit older generation) are overkill for that.

---

### Post by daniell59 on 2020-12-16
Let me add the following. With my future new build, I would like to create a virtual machine. Would that be adversely affected by not having a discrete video card?

---

### Post by Yellow Pasque on 2020-12-16
> **mastablasta said:**
> if you don't have special needs and dont' need the latest, then get a Ryzen 5 3xxx series, add dual channel ram 2x8 GB or 2x16 GB and a nvme disk. you won't know what hit you.

I'm going to +1 this. You can get a nice Ryzen 3400G now, and quit waiting on uncertain market factors. I also think you should seriously consider going with a B450 board, as they are priced to move and the only thing you will miss compared to B550 is PCI-e 4.0 for SSD's. If you don't know what that is, you probably don't need it.

This is the motherboard I have, a Gigabyte/AORUS B450 Pro Wifi ( [https://www.newegg.com/gigabyte-b450-aorus-pro-wifi/p/N82E16813145082?Item=N82E16813145082](https://www.newegg.com/gigabyte-b450-aorus-pro-wifi/p/N82E16813145082?Item=N82E16813145082) )
I chose it because it's got Intel networking chips, premium ALC1220-VB audio with fancy German capacitors, 2 NVMe slots, and a very reasonable price. I don't do heavy gaming and this worked perfectly with a Ryzen 2400G. I have an Nvidia GTX950 card, but I stopped using that in favor of the onboard graphics as they play better with Linux and now offer good video decode acceleration in Firefox through VA-API (i.e. smooth/efficient Youtube viewing).

That's just my opinion and food for thought. If you really want to wait for the 4750G, that's cool too.

---

### Post by Yellow Pasque on 2020-12-16
> **daniell59 said:**
> Let me add the following. With my future new build, I would like to create a virtual machine. Would that be adversely affected by not having a discrete video card?

What do you plan to do with the VM? I have VM's I use for Ubuntu packaging with the system mentioned above. They run fine.
If you really plan to do heavy 3D stuff in VM's, you'll have to jump through some hoops to get PCI-e passthrough working. Otherwise, the CPU is being used for the VM's graphics processing and a fancy GPU won't help.

---

### Post by TheFu on 2020-12-16
I looked at Ryzen CPU prices a few days ago for a friend (and myself), they are crazy for any popular model.  Even the 3100 is 30% higher than it should be now.  Until inventory becomes available again in a few months, this is NOT the time to do upgrades or new builds.

I've always found NUC (small as possible) computers to be about $100-$200 overpriced for what you get. Some microITX and microATX systems which are sized about 1/3rd of a mid-tower case don't have that premium cost ... that is when supplies are flowing.

If you just want a media playing machine, get a rapberry pi.  
[LIST]
[*]1080p = r-pi v3
[*]4k = r-pi v4
[/LIST]
These are silent, tiny, handle the popular video codeces in hardware. Audio is fine, but if you want high-end audio, there are add on "hat" devices for the GPIO with amplifiers.  I drive our projection system and THX audio using a $35 r-pi v3.

BTW, someone found a Linux distro that has the Intel 2.5Gbps NIC drivers provided and working out of the box. That's excellent news. Hopefully, Ubuntu 21.04 will have them too, so worst case it would be a few months having to run a different OS, then switch to a non-LTS Ubuntu for about a year before 22.04 LTS is available.  My network only has GigE stuff today and I wasn't planning to move to anything less than 5Gbps when that hardware gets cheap.

---

### Post by daniell59 on 2020-12-16
> **TheFu said:**
> I looked at Ryzen CPU prices a few days ago for a friend (and myself), they are crazy for any popular model.  Even the 3100 is 30% higher than it should be now.  Until inventory becomes available again in a few months, this is NOT the time to do upgrades or new builds.

I've always found NUC (small as possible) computers to be about $100-$200 overpriced for what you get. Some microITX and microATX systems which are sized about 1/3rd of a mid-tower case don't have that premium cost ... that is when supplies are flowing.

If you just want a media playing machine, get a rapberry pi.  
[LIST]
[*]1080p = r-pi v3
[*]4k = r-pi v4
[/LIST]
These are silent, tiny, handle the popular video codeces in hardware. Audio is fine, but if you want high-end audio, there are add on "hat" devices for the GPIO with amplifiers.  I drive our projection system and THX audio using a $35 r-pi v3.

BTW, someone found a Linux distro that has the Intel 2.5Gbps NIC drivers provided and working out of the box. That's excellent news. Hopefully, Ubuntu 21.04 will have them too, so worst case it would be a few months having to run a different OS, then switch to a non-LTS Ubuntu for about a year before 22.04 LTS is available.  My network only has GigE stuff today and I wasn't planning to move to anything less than 5Gbps when that hardware gets cheap.
I also noticed that PSU prices have also gone up. There is no emergency for me. I have two old homebuilt computers, a tablet and a smartphone.

---

### Post by mastablasta on 2020-12-17
> **TheFu said:**
> 
I've always found NUC (small as possible) computers to be about $100-$200 overpriced for what you get. Some microITX and microATX systems which are sized about 1/3rd of a mid-tower case don't have that premium cost ... that is when supplies are flowing.


well yes, if yu build yourself and have space - slightly bigger costs less and can be made silent or low volume, yet still good. i found nice case that could even fit larger GPU card, but in the end the kid wanted bigger to add more drives in future. and bigger ones were cheaper and since it was his money...

as for VM - unless you plan to do some GPU intensive stuff, you need strong CPU and lots of RAM. as much as possible.

linux server (e.g. for testing) is not an issue. i also ran xubuntu desktop on WindowsXP - single core machine, 4 GB ram, PAE kernel. so i could allocate only 1.5 GB ram to Virtual box VM. and it also worked reasonably well. i installed many linux distros and also ran them in live session. no issues, just a bit slow. again i could not assign a core to Vm because i had only 1 core total :-)

Ryzen 5 + 16 GB ram will be a non issue. you can even run multiple VM at the same time.

---

### Post by TheFu on 2020-12-17
> **mastablasta said:**
> 
Ryzen 5 + 16 GB ram will be a non issue. you can even run multiple VM at the same time.

Hope so. Mine usually runs 10-20 VMs o problem. In 2008, 10-20 VMs fine on a Core2 Duo.  For linux servers, usually less than 1G RAM for each VM is needed. I start w/ 512MB allocated and move up or down from there.  A few VMs have needed more RAM, but most are happy w/ 512mb.

Don't use GUIs unless you want resource sucking bloat.  Running MS-Windows uses the most bloat of all my VMs. Usually onl power that VM on when actually needed.

---

### Post by daniell59 on 2020-12-17
> **Yellow Pasque said:**
> What do you plan to do with the VM? I have VM's I use for Ubuntu packaging with the system mentioned above. They run fine.
If you really plan to do heavy 3D stuff in VM's, you'll have to jump through some hoops to get PCI-e passthrough working. Otherwise, the CPU is being used for the VM's graphics processing and a fancy GPU won't help.

Just to play around with VM. I really have no pressing need for it. I just want my system to be able to  handle it.

---

### Post by P-I H on 2020-12-17
I built this computer a month back and is very pleased with the performance.
```
p-i@pi-TUF-B550M:~$ inxi -Fz
System:    Kernel: 5.8.0-33-generic x86_64 bits: 64 Desktop: N/A Distro: Ubuntu 20.10 (Groovy Gorilla) 
Machine:   Type: Desktop System: ASUS product: N/A v: N/A serial: <filter> 
           Mobo: ASUSTeK model: TUF GAMING B550M-PLUS (WI-FI) v: Rev X.0x serial: <filter> 
           UEFI: American Megatrends v: 1212 date: 11/04/2020 
CPU:       Info: 6-Core model: AMD Ryzen 5 5600X bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 2196 MHz min/max: 2200/3700 MHz Core speeds (MHz): 1: 2196 2: 2196 3: 2187 4: 2196 5: 2195 
           6: 2196 7: 2184 8: 2196 9: 2195 10: 2199 11: 2193 12: 2197 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] 
           driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.9 driver: amdgpu,ati unloaded: fbdev,modesetting,radeon,vesa 
           resolution: 2560x1440 
           OpenGL: renderer: AMD Radeon RX 5700 (NAVI10 DRM 3.38.0 5.8.0-33-generic LLVM 11.0.0) v: 4.6 Mesa 20.2.1 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Starship/Matisse HD Audio driver: snd_hda_intel 
           Device-3: Logitech Webcam C250 type: USB driver: snd-usb-audio,uvcvideo 
           Sound Server: ALSA v: k5.8.0-33-generic 
Network:   Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi 
           IF: wlp6s0 state: up mac: <filter> 
           Device-2: Realtek RTL8125 2.5GbE driver: N/A 
Drives:    Local Storage: total: 1.36 TiB used: 86.33 GiB (6.2%) 
           ID-1: /dev/nvme0n1 vendor: Samsung model: SSD 970 EVO 500GB size: 465.76 GiB 
           ID-2: /dev/nvme1n1 vendor: Kingston model: SA2000M8500G size: 465.76 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 860 EVO 500GB size: 465.76 GiB 
Partition: ID-1: / size: 456.96 GiB used: 86.30 GiB (18.9%) fs: ext4 dev: /dev/nvme0n1p2 
Swap:      ID-1: swap-1 type: file size: 2.00 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:   System Temperatures: cpu: 32.5 C mobo: 44.0 C gpu: amdgpu temp: 60.0 C 
           Fan Speeds (RPM): fan-1: 878 fan-2: 908 fan-3: 834 fan-7: 0 gpu: amdgpu fan: 0 
Info:      Processes: 352 Uptime: 45m Memory: 15.54 GiB used: 2.89 GiB (18.6%) Shell: Bash inxi: 3.1.07 
p-i@pi-TUF-B550M:~$
``` 
It handles almost anything
[https://www.phoronix.com/scan.php?page=article&item=amd-ryzen-5600x&num=2](https://www.phoronix.com/scan.php?page=article&item=amd-ryzen-5600x&num=2)
I run Windows 10, Ubuntu 20.10 and the Ubuntu development version (Hippo Hirsute), installed on different disks in the computer.
Oracle VirtualBox isn't installed at present, but was installed earlier.
In case gaming performance isn't necessary I suppose a Radeon RX 550 GPU is OK.
Sensors is working OK, when "acpi_enforce_resources=lax" is included in /etc/default/grub
To get suspend to work I have added "iommu=soft" in /etc/default/grub. There is however a problem with suspend in Ubuntu 20.10 now. It worked before and it works OK in W10 and Hippo Hirsute.

---

### Post by Yellow Pasque on 2020-12-17
> **P-I H said:**
> I built this computer a month back and is very pleased with the performance.
```
Network:   Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi 
           Device-2: Realtek RTL8125 2.5GbE driver: N/A 
``` 


So does the LAN work on that or not? It looks like you're using wireless and the RTL8125 chip does not have a driver loaded. I think this is what the 'TheFu' referred to earlier about not having support until kernel 5.10

---

### Post by TheFu on 2020-12-17
Ryzen 5 5600X can handle anything, easily.  I've not seen that CPU available anywhere, except in pre-built systems or for 20+% over the MSRP.

---

### Post by P-I H on 2020-12-17
@Yellow Pasque
The Realtek RTL8125B works in Wi10 and with linux kernel 5.9 and 5.10, I'm using the  5.10 kernel in Hippo Hirsute.
```
Network:   Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi 
           IF: wlp6s0 state: up mac: <filter> 
           Device-2: Realtek RTL8125 2.5GbE driver: r8169
```
In 20.10 I'm using WiFi at about 200 Mbps.

@TheFu
I was lucky to get one at the release day. The price in Sweden is about $398,  but now it's not available.

---

### Post by TheFu on 2020-12-17
Very lucky, indeed. the 5600x is almost 2x faster than the 1600. Pretty impressive for the same number of cores over about 4 yrs of CPU improvements.
I have a self-imposed $150 price limitation for a CPU.  A few months ago, the $100 3100 was looking like **the deal** for price/performance.  I maintain a simple line chart in a spreadsheet with price/performance for about 10 CPUs in the $100-$250 price range.  I've written off Intel because they seem to change compatible sockets every 6 months which breaks the entire cheap upgrade after 3 yr plan. With Ryzen, just swapping the CPU only can nearly quadruple performance after a few years while not buying $800 CPUs, ever.  Now that AMD has the $/Watts nailed to be pretty great too and are less prone to all the Intel CPU security issues, there is little reason to choose Intel for a desktop build in my mind.

Laptops, and I'm still not sold on AMD for lower power and long battery life yet. With laptops, upgrades beyond RAM and storage aren't really any option.

Lots of choices and complexities. Wouldn't want this to be easy after all. No fun that way. ;(

---

### Post by tanmayjain01 on 2021-05-18
Hey Daniell,

It's not hard to build a PC for yourself. You can try using a few websites which allows you to check the compatibility of the pc parts before buying them. For this, you can use PC Part Picker, PC Builder, and BuildMyPC. Although, I recommend using PCPartPicker, as this is one of the most old and reliable website out there for checking the compatibility of the parts.

If you're not sure on this, you can read [my post on pc builder reviews]("https://thepcbuild.net/best-custom-pc-builder-websites/") where I reviewed all these websites for building the PC. Once you checked and find the compatible parts, I recommend you to connect with any local computer shop person for arranging and building your desktop correctly.

Also, best of luck for your build :)

---

### Post by daniell59 on 2021-05-18
> **tanmayjain01 said:**
> Hey Daniell,

It's not hard to build a PC for yourself. You can try using a few websites which allows you to check the compatibility of the pc parts before buying them. For this, you can use PC Part Picker, PC Builder, and BuildMyPC. Although, I recommend using PCPartPicker, as this is one of the most old and reliable website out there for checking the compatibility of the parts.

If you're not sure on this, you can read [my post on pc builder reviews]("https://thepcbuild.net/best-custom-pc-builder-websites/") where I reviewed all these websites for building the PC. Once you checked and find the compatible parts, I recommend you to connect with any local computer shop person for arranging and building your desktop correctly.

Also, best of luck for your build :)

My present impediment is not how to build, but to find components at a reasonable price. The Ryzen 5000G series would seemingly solve my problem if it ever becomes available in the retail market.

---

### Post by him610 on 2021-05-18
> to find components at a reasonable price
A couple of other folks have said it in earlier posts. You can basically build a model of your intended system at pcpartspicker; it also checks compatibility. It will also show you the best current prices, and if you think they are too high, you can wait awhile. 
Consider these points: 
Motherboard will determine case size.
Power Supply Unit: Semi-modular or fully-modular
Disks: 2.5 inch SSD or newer NVME (don't lose that small screw that comes with your motherboard)

You can always build an economically minimum system then upgrade as resources become available.
Modeling your build is the fun part of building a computer. Satisfaction is when it successfully boots.

---

### Post by TheFu on 2021-05-18
pcpartspicker is great, but not 100% accurate and definitely not always finding the cheapest, reputable, seller.  I use it for broad searches and comparisons only.
I've been burned due to inaccurate data too.
Always read the motherboard manual BEFORE buying, so you know any caveats about RAM, BIOS, storage and power connections before it is too late.

---

