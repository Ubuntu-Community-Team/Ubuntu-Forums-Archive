---
title: "Linux Compatible Motherboard"
date: 2024-05-22
forum: Hardware
---

### Post by daniell59 on 2024-05-22
This motherboard seems perfect for my needs. Here is the problem. A reviewer in PC Parts Picker said that he had great difficulty installing Ethernet Drivers in Linux. Why would that be the case.


MSI PRO B650M-P ProSeries Motherboard

[https://www.amazon.com/MSI-B650M-P-ProSeries-Motherboard-Processors/dp/B0C7SJFDXK/ref=cm_cr_arp_d_product_top?ie=UTF8](https://www.amazon.com/MSI-B650M-P-ProSeries-Motherboard-Processors/dp/B0C7SJFDXK/ref=cm_cr_arp_d_product_top?ie=UTF8)

---

### Post by TheFu on 2024-05-22
Because the chips used for the ethernet suck or are much too new?
[https://www.msi.com/Motherboard/PRO-B650M-P/Specification](https://www.msi.com/Motherboard/PRO-B650M-P/Specification) says it uses  Realtek® 8125BG 2.5G LAN

Avoid Realtek NICs.  There's a reason they are so cheap.  There are a few different ways.

a) Buy an Intel PCIe NIC, install and use that instead. Just disable the Realtek junk in the BIOS.

b) Choose a motherboard with an Intel NIC instead.  Usually the list of motherboards will be greatly reduced doing this and they cost about $20 more, which is less than a separate Intel PCIe NIC would cost and it won't use a slot.

Watch out for bleeding edge hardware, in addition to hardware that doesn't work well with Linux.  Of course, you are free to seek out the Linux drivers for that exact chip and hope that the hassles with it aren't too great.  DMKS might be setup to automatically re-link the new driver or it might take 1-2 yrs before that happens.  Every new kernel will need that. New kernels happen about 2-4 times every month.

You have some choices.

I decided that dealing with realtek wasn't worth the hassles and only buy motherboards with Intel NICs.  When the 2.5Gbps Intel NIC was new, I specifically bought an older model motherboard that used an older Intel NIC that I 100% knew was well supported.  Since all my networking devices are GigE, not 2.5Gbps, this wasn't a hard choice for me.  If you don't have a router or switches that support 2.5Gbps, it may not be a hard choice for you either.  If you don't plan to get faster network gear in the next 5 yrs, then I wouldn't worry about it and I'd get a motherboard with a different NIC chip that is well supported.

---

### Post by Dennis N on 2024-05-22
I'm using an MSI Pro B660M-G motherboard. This is an Intel board, while yours is AMD. Still, it has the same Realtek® RTL8125BG 2.5Gbps LAN controller. Completed this build in Jan 2023. With this board, I have not had any problems with the ethernet or anything else so I am satisfied.

---

### Post by daniell59 on 2024-05-22
> **TheFu said:**
> Because the chips used for the ethernet suck or are much too new?
[https://www.msi.com/Motherboard/PRO-B650M-P/Specification](https://www.msi.com/Motherboard/PRO-B650M-P/Specification) says it uses  Realtek® 8125BG 2.5G LAN

Avoid Realtek NICs.  There's a reason they are so cheap.  There are a few different ways.

a) Buy an Intel PCIe NIC, install and use that instead. Just disable the Realtek junk in the BIOS.

b) Choose a motherboard with an Intel NIC instead.  Usually the list of motherboards will be greatly reduced doing this and they cost about $20 more, which is less than a separate Intel PCIe NIC would cost and it won't use a slot.

Watch out for bleeding edge hardware, in addition to hardware that doesn't work well with Linux.  Of course, you are free to seek out the Linux drivers for that exact chip and hope that the hassles with it aren't too great.  DMKS might be setup to automatically re-link the new driver or it might take 1-2 yrs before that happens.  Every new kernel will need that. New kernels happen about 2-4 times every month.

You have some choices.

I decided that dealing with realtek wasn't worth the hassles and only buy motherboards with Intel NICs.  When the 2.5Gbps Intel NIC was new, I specifically bought an older model motherboard that used an older Intel NIC that I 100% knew was well supported.  Since all my networking devices are GigE, not 2.5Gbps, this wasn't a hard choice for me.  If you don't have a router or switches that support 2.5Gbps, it may not be a hard choice for you either.  If you don't plan to get faster network gear in the next 5 yrs, then I wouldn't worry about it and I'd get a motherboard with a different NIC chip that is well supported.
Thanks so much for your informative reply. I don't want added complications in my life. I will search for a MB that has an Intel NIC. Since I will be using the Ryzen 8600G CPU, I want a MB that has display port. I read that HDMI does not support Linux.

---

### Post by daniell59 on 2024-05-22
> **daniell59 said:**
> Thanks so much for your informative reply. I don't want added complications in my life. I will search for a MB that has an Intel NIC. Since I will be using the Ryzen 8600G CPU, I want a MB that has display port. I read that HDMI does not support Linux.


Thanks so much for your informative reply. I don't want added complications in my life. I will search for a MB that has an Intel NIC. Since I will be using the Ryzen 8600G CPU, I want a MB that has display port. I read that HDMI does not support Linux.

---

### Post by Dennis N on 2024-05-22
I'm using an MSI Pro B660M-G motherboard. This is an Intel board, while yours is AMD. Still, it has the same Realtek® RTL8125BG 2.5Gbps LAN controller. Completed this build in Jan 2023. With this board, I have not had any problems with the ethernet or anything else so I am happy with it. I also have an older MSI B360M-VD built in 2018. No problems with that system either.

(Duplicate post because the first version returned a server error - bad gateway)

---

### Post by currentshaft on 2024-05-22
> **daniell59 said:**
> I read that HDMI does not support Linux.

Really need to stop believing everything you read online. A shocking majority of it is wrong.

HDMI works fine. Ethernet works fine. I've never needed to install a driver for either in over 15 years of Linux use.

---

### Post by daniell59 on 2024-05-22
> **currentshaft said:**
> Really need to stop believing everything you read online. A shocking majority of it is wrong.

HDMI works fine. Ethernet works fine. I've never needed to install a driver for either in over 15 years of Linux use.
The problem is with HDMI 2.1.

---

### Post by TheFu on 2024-05-22
> **daniell59 said:**
> The problem is with HDMI 2.1.

And resolutions over 1080p.  [https://arstechnica.com/gadgets/2024/02/hdmi-forum-to-amd-no-you-cant-make-an-open-source-hdmi-2-1-driver/](https://arstechnica.com/gadgets/2024/02/hdmi-forum-to-amd-no-you-cant-make-an-open-source-hdmi-2-1-driver/)   You can thank the HDMI standards people for that limitation.  The linux and GPU guys have tried.  Even gaining access to the specifications requires huge payments and a legal team which AMD wasn't able to crack.

Linux definitely supports HDMI, BTW.  I use it today and have since around 2008.  

Of course, whether playback of DRM videos will work is really the only issue with HDMI and Linux that I know.  The answer for that is simple. Stay at 1080p resolutions or get a streaming device with proprietary hardware and drivers to watch DRM-locked content.  I don't have any 4K displays anywhere, so it hasn't been an issue on any of my devices.  Further, we tend to watch movies on a 1080p projector which doesn't support any HDCP to my knowledge, so all of this is a non-issue.  I do have a few 4K videos, Those all seem to play fine ... er ... at 1080p.  Cannot really test any higher resolutions.

Lots of Linux people have multiple 4K monitors and those work fine.  They can be connected via DP or HDMI.  It is only the DRM parts that create issues. Commercial content players, not day-to-day productivity programs, might have DRM.

---

### Post by daniell59 on 2024-05-22
> **TheFu said:**
> And resolutions over 1080p.  [https://arstechnica.com/gadgets/2024/02/hdmi-forum-to-amd-no-you-cant-make-an-open-source-hdmi-2-1-driver/](https://arstechnica.com/gadgets/2024/02/hdmi-forum-to-amd-no-you-cant-make-an-open-source-hdmi-2-1-driver/)   You can thank the HDMI standards people for that limitation.  The linux and GPU guys have tried.  Even gaining access to the specifications requires huge payments and a legal team which AMD wasn't able to crack.

Linux definitely supports HDMI, BTW.  I use it today and have since around 2008.  

Of course, whether playback of DRM videos will work is really the only issue with HDMI and Linux that I know.  The answer for that is simple. Stay at 1080p resolutions or get a streaming device with proprietary hardware and drivers to watch DRM-locked content.  I don't have any 4K displays anywhere, so it hasn't been an issue on any of my devices.  Further, we tend to watch movies on a 1080p projector which doesn't support any HDCP to my knowledge, so all of this is a non-issue.  I do have a few 4K videos, Those all seem to play fine ... er ... at 1080p.  Cannot really test any higher resolutions.

Lots of Linux people have multiple 4K monitors and those work fine.  They can be connected via DP or HDMI.  It is only the DRM parts that create issues. Commercial content players, not day-to-day productivity programs, might have DRM.

Thanks for clarifying the issue. As of now, I have not found an AMD 5 motherboard with Intel NICs.

---

### Post by TheFu on 2024-05-22
I'd be surprised if MSI and Asus didn't have at least 2 models to do that.    I haven't looked at AM5 motherboards at all.  I have Asus B450s * in my systems.  The B550 has an Intel 2.5Gbps NIC, but it is AM4, not AM5.

BTW, it does appear that DisplayPort supports DRM at 4K, but you should check that.  I have an HDMI-to-DP cable ($10) because my monitor doesn't have any HDMI inputs, but my KVM switch is only HDMI + USB for mouse and keyboard.  Again, I don't have any 4k displays and my main display is only 1920x1200, so not even QHD (1440p).

Asus ROG STRIX B650-A GAMING WIFI ATX AM5 Motherboard - has an intel NIC.
MSI MEG X670E GODLIKE EATX AM5 Motherboard does too, but that's a huge motherboard (E-ATX). Full height, not for a mid-tower case.

I used PCpartpicker and since they don't filter on NICs, I did some comparisons manually where the NIC chip is listed.  Personally, I wouldn't get any MB besides Asus or MSI (not the cheaper ASRock or Gigabyte or any of the other others. Also, I won't want wifi on my motherboard. Wifi is a negative to me.

---

### Post by daniell59 on 2024-05-23
I might be better off with AM4. Another thing to think about.

---

### Post by TheFu on 2024-05-23
> **daniell59 said:**
> I might be better off with AM4. Another thing to think about.

Depends on your workloads, how far into the future you want to take the computer and upgrade plans.
With either AM4 or AM5, there are multiple generations of CPUs along the upgrade path.  With AM4, those are all known, today. With AM5, they will still be coming in the future, but many early AM5 systems will have limitations around PCIe bandwidth which may or may not be important. Only you can know.

I retired a Core i7 from 2009 and replaced it with an AM4 Ryzen 2600 (65W).  That was a huge performance boost.  Got a B450 motherboard which was late enough to get updates to and support all AM4 CPUs/APUs.  Perhaps I was lucky. Don't know.  I know my power bill dropped when this replacement happened. In theory, it shouldn't have dropped THAT much, but it was noticed. I think it was about $450 for the MB, CPU, and RAM in this box.

Next, I replaced a failure Pentium G3258 which was a NAS and media server that just couldn't transcode hidef stuff for all my playback devices.  The Realtek NIC had failed years earlier. Getting into the BIOS at boot was a 1 in 20 gamble.  The motherboard was pretty flakey.  Fortunately, the CPU+MB was just $99 when I got it new.  The G3258 was a terrific value purchase.  Anyway, replaced it with a Ryzen 5600G ($119) and the exact same AM4 B450 motherboard that I already had. The B550 versions were out, but everyone was having trouble with 2.5Gbps NIC drivers.  People were buying $30 Intel PRO/1000 NICs to put into their systems, just to have a working network. You can find those threads here.  Because it was a few years later, the MB, CPU, RAM for this build were about $270 total.  There was really no power savings with this swap, but going from 6000 ----> 19500 passmarks is quite noticeable.

Then Ryzen 5600G APUs started getting cheap and the nvidia GPU in the Ryzen 2600 had been causing issues where my patching efforts basically just automatically reinstalled the nvidia drivers every time.  With the cheaper 5600G APUs, drivers were built into the 5.10 and later kernels. Plus that APU was faster than the nVidia 1030GT and could run encoding for h.265 and h.264 video in the APU hardware without impacting any CPU.  The 5600G was about 40% faster than the 2600. Anyway, this was one of the reasons people prefer AMD over Intel.  There's a clear, cheap, CPU-swap, upgrade path within a motherboard series.  I decided that having 2 systems which were nearly identical would provide redundancy for my server VMs and container workloads.  All of the workload could be run on 1 machine, if needed.  Having 2 identical systems would aid in troubleshooting.  Plus, I'd already know the "gotchas" with the motherboard, because I'd already discovered them.  I offset this upgrade cost by selling some DDR4 RAM and the 2600 to a friend.  $120 - $80 = $40 for a 40% performance increase?  Can you say bargain?  

I may have 1 more APU upgrade on these AM4 systems.  The trick is to do the upgrade before there's too much scarcity and prices for the chips starts rising.  I don't want to exceed the 65W power use if I can avoid it.  I'm used to the lower power bills, quieter systems and higher performance.

Because my networking is a little more complex than the average person would use, I have an extra NIC in my systems.
```
$ inxi -Nz
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           Device-2: Intel 82575GB Gigabit Network driver: igb 
           Device-3: Intel 82575GB Gigabit Network driver: igb 
           Device-4: Intel 82575GB Gigabit Network driver: igb 
           Device-5: Intel 82575GB Gigabit Network driver: igb 

```
For people who don't do CPU-only upgrades, Ryzen might not be the best value.  Ryzen pushed Intel to lower their prices on some very capable MB+CPU bundles.  For me, it is all about the passmarks, though AMD iGPUs are definitely better than the intel iGPUs.  That might matter to some.  I screwed around with the hardware transcoding in the Ryzen APU for a few weeks and found that for real-time transcoding, it was fine, but for anything to be archived, using CPU transcoding with handbrake was much better quality at 1/3rd the file size. Of course, using a CPU to transcode and not a GPU is much slower. 

I have to transcode all VP9 content, so my playback devices don't crash.  VP9 can make impressive videos at very small sizes, but if they can't be played, they are useless.

Anyway, your needs are different, so your choices will be different.  I'd probably go with an AM5 at this point, assuming the passmarks and budget aligned.  I've been temped by a few Intel Core i5 and even i3 bundles.  For laptops, I've always gotten Intel-based systems. For a while, they just did better sipping of battery. I don't think that difference exists anymore, but I haven't gotten a new laptop since 2018. I use a tablet for much of my portable computing needs these days.

When I'm comparing "value" for upgrades, I make a graph of cost/passmark and look for pricing mistakes.  Often, the line isn't linear with some popular CPUs being above it and some great sale CPUs dropping below the line.  The 5600G dropped below that line and I pounced.  I used $70 as the price the iGPU added, since getting a CPU without an iGPU would require at least a $70 GPU be added.  For a gamer, the iGPU isn't even a consideration, unless you plan to run Windows in a VM and have GPU passthru setup.  You'll use the iGPU for the host OS and the discrete GPU for gaming.  There's also a value in extending the upgrade period that AM5 provides.  Only you can decide what that intangible value might be.  

If my systems were slow and old today, I'd probably consider AM5 carefully.  $100 extra for "newer" might be acceptable. Depends on how tight your budget is and what performance levels you've decided are needed.  There are people in these forums happily running 1st-gen Ryzen computers.  Chances are the motherboards they have cannot support newer Ryzen CPUs.  AM5 is still first generation and the motherboards are too. 

Anyway, lots of choices.

---

### Post by daniell59 on 2024-05-23
> **TheFu said:**
> Depends on your workloads, how far into the future you want to take the computer and upgrade plans.
With either AM4 or AM5, there are multiple generations of CPUs along the upgrade path.  With AM4, those are all known, today. With AM5, they will still be coming in the future, but many early AM5 systems will have limitations around PCIe bandwidth which may or may not be important. Only you can know.

I retired a Core i7 from 2009 and replaced it with an AM4 Ryzen 2600 (65W).  That was a huge performance boost.  Got a B450 motherboard which was late enough to get updates to and support all AM4 CPUs/APUs.  Perhaps I was lucky. Don't know.  I know my power bill dropped when this replacement happened. In theory, it shouldn't have dropped THAT much, but it was noticed. I think it was about $450 for the MB, CPU, and RAM in this box.

Next, I replaced a failure Pentium G3258 which was a NAS and media server that just couldn't transcode hidef stuff for all my playback devices.  The Realtek NIC had failed years earlier. Getting into the BIOS at boot was a 1 in 20 gamble.  The motherboard was pretty flakey.  Fortunately, the CPU+MB was just $99 when I got it new.  The G3258 was a terrific value purchase.  Anyway, replaced it with a Ryzen 5600G ($119) and the exact same AM4 B450 motherboard that I already had. The B550 versions were out, but everyone was having trouble with 2.5Gbps NIC drivers.  People were buying $30 Intel PRO/1000 NICs to put into their systems, just to have a working network. You can find those threads here.  Because it was a few years later, the MB, CPU, RAM for this build were about $270 total.  There was really no power savings with this swap, but going from 6000 ----> 19500 passmarks is quite noticeable.

Then Ryzen 5600G APUs started getting cheap and the nvidia GPU in the Ryzen 2600 had been causing issues where my patching efforts basically just automatically reinstalled the nvidia drivers every time.  With the cheaper 5600G APUs, drivers were built into the 5.10 and later kernels. Plus that APU was faster than the nVidia 1030GT and could run encoding for h.265 and h.264 video in the APU hardware without impacting any CPU.  The 5600G was about 40% faster than the 2600. Anyway, this was one of the reasons people prefer AMD over Intel.  There's a clear, cheap, CPU-swap, upgrade path within a motherboard series.  I decided that having 2 systems which were nearly identical would provide redundancy for my server VMs and container workloads.  All of the workload could be run on 1 machine, if needed.  Having 2 identical systems would aid in troubleshooting.  Plus, I'd already know the "gotchas" with the motherboard, because I'd already discovered them.  I offset this upgrade cost by selling some DDR4 RAM and the 2600 to a friend.  $120 - $80 = $40 for a 40% performance increase?  Can you say bargain?  

I may have 1 more APU upgrade on these AM4 systems.  The trick is to do the upgrade before there's too much scarcity and prices for the chips starts rising.  I don't want to exceed the 65W power use if I can avoid it.  I'm used to the lower power bills, quieter systems and higher performance.

Because my networking is a little more complex than the average person would use, I have an extra NIC in my systems.
```
$ inxi -Nz
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           Device-2: Intel 82575GB Gigabit Network driver: igb 
           Device-3: Intel 82575GB Gigabit Network driver: igb 
           Device-4: Intel 82575GB Gigabit Network driver: igb 
           Device-5: Intel 82575GB Gigabit Network driver: igb 

```
For people who don't do CPU-only upgrades, Ryzen might not be the best value.  Ryzen pushed Intel to lower their prices on some very capable MB+CPU bundles.  For me, it is all about the passmarks, though AMD iGPUs are definitely better than the intel iGPUs.  That might matter to some.  I screwed around with the hardware transcoding in the Ryzen APU for a few weeks and found that for real-time transcoding, it was fine, but for anything to be archived, using CPU transcoding with handbrake was much better quality at 1/3rd the file size. Of course, using a CPU to transcode and not a GPU is much slower. 

I have to transcode all VP9 content, so my playback devices don't crash.  VP9 can make impressive videos at very small sizes, but if they can't be played, they are useless.

Anyway, your needs are different, so your choices will be different.  I'd probably go with an AM5 at this point, assuming the passmarks and budget aligned.  I've been temped by a few Intel Core i5 and even i3 bundles.  For laptops, I've always gotten Intel-based systems. For a while, they just did better sipping of battery. I don't think that difference exists anymore, but I haven't gotten a new laptop since 2018. I use a tablet for much of my portable computing needs these days.

When I'm comparing "value" for upgrades, I make a graph of cost/passmark and look for pricing mistakes.  Often, the line isn't linear with some popular CPUs being above it and some great sale CPUs dropping below the line.  The 5600G dropped below that line and I pounced.  I used $70 as the price the iGPU added, since getting a CPU without an iGPU would require at least a $70 GPU be added.  For a gamer, the iGPU isn't even a consideration, unless you plan to run Windows in a VM and have GPU passthru setup.  You'll use the iGPU for the host OS and the discrete GPU for gaming.  There's also a value in extending the upgrade period that AM5 provides.  Only you can decide what that intangible value might be.  

If my systems were slow and old today, I'd probably consider AM5 carefully.  $100 extra for "newer" might be acceptable. Depends on how tight your budget is and what performance levels you've decided are needed.  There are people in these forums happily running 1st-gen Ryzen computers.  Chances are the motherboards they have cannot support newer Ryzen CPUs.  AM5 is still first generation and the motherboards are too. 

Anyway, lots of choices.
Thanks for your informative reply. At my age I don't have to worry about future proofing. I use the computer for surfing the web, watching You Tube videos and I would like to have more capacity for such things as virtual machine.

---

### Post by TheFu on 2024-05-23
> **daniell59 said:**
> Thanks for your informative reply. At my age I don't have to worry about future proofing. I use the computer for surfing the web, watching You Tube videos and I would like to have more capacity for such things as virtual machine.

What type and how many concurrent VMs?
Which hypervisor do you use currently?  If not KVM/QEMU, would you consider switching?

In 2008, I was running 20 VMs, mostly servers, on 8GB of RAM and a Core2 Duo CPU.  The server VMs used between 384MB and 1GB of RAM.  Desktops and MS-Windows needed more resourced.   Alas, Ubuntu Server has bloated to where it really needs 768MB as the minimal amount of RAM per VM.  OTOH, we have Linux Containers these days which are 10x lighter (resources for 1 VM can accommodate 10 Linux Containers as a rough estimate).  I've heard of 100:1 container densities, so specialized containers can be supported.  MS-Windows cannot be run in a container, so a full, bloated, VM is the only way.  4-6GB of RAM allocated for a Windows VM seems sufficient.

Doing the types of things you list is something easily handled by most Pentium (not even Core i3) computers from 10 yrs ago with 8-16GB of RAM can handle.  People often over-buy hardware, beyond their true needs.   AM5 would be overkill.  Even an AM4 Ryzen 5600G would be overkill.  

A Ryzen 3200G (7300 passmarks) looks to be around $50.
Or a Ryzen 4600G (13000 passmarks) is about $90 ... same MB and RAM would work for about double the performance.  Of course, if you have and want to spend more money, people will happily take it.  If you aren't interested in gaming or even mid-level GPU performance (I'm not), then Ryzen with a built-in iGPU is likely the best deal.

I'd compare the Ryzen 3200G, 3400G, 4600G and 5600G models.  All three can use the same motherboard of a B450 or B550.  Of course, you can look at the X470/X570 motherboards, if you want to spend more and have more SATA ports.  I think the intent was for the Xx70 models to have longer firmware updates and support for more AM4 CPUs/APUs.  Would be worth checking the supported iGPU resolutions between those APU models. They might be different, so if you use or plan to use a 4K monitor, that could be a reason to spend more on a newer APU.   Looks to me like the 4600G and 5600G have the same iGPU, running at the same clock speed with the same number of graphics cores.  [https://www.tomshardware.com/reviews/amd-ryzen-5-5600g-review/6](https://www.tomshardware.com/reviews/amd-ryzen-5-5600g-review/6) has some comparisons with other iGPUs from Intel and AMD.  The article claimed to have an nvidia 1030GT, but I must have missed it.  I own a 1030GT and find the Radeon iGPU in the 5600G to perform noticeably better. I didn't do any benchmarking, but it just "feels faster" and it definitely is less hassle with drivers.  "Feels faster" means 20-50% faster for my type of use.  Heck, just saw that the 5600G is $110 at Wally-world.  

Pricing I found today:
$50 - 3200G
$90 - 4600G
$110 - 5600G

BTW, my 5600G is a NAS for the LAN here.  It is currently running 5 VMs, 4 LXC containers, and memory use (I'm not exactly careful, since I have RAM headroom):
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        21Gi       2.3Gi       208Mi       7.4Gi       9.0Gi
Swap:         4.1Gi       1.9Gi       2.2Gi
```
If I weren't lazy, bet I could get that RAM use down below 14GB.

And top says:
```
top - 15:07:23 up 5 days,  4:33,  2 users,  load average: 0.32, 0.28, 0.28
Tasks: 610 total,   2 running, 608 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.4 us,  0.0 sy,  0.0 ni, 99.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  31449.6 total,   2317.3 free,  21584.8 used,   7547.6 buff/cache
MiB Swap:   4200.0 total,   2233.5 free,   1966.5 used.   9198.0 avail Mem 

```
Hardly any effort for the CPU.  It isn't doing much right now - just playing some music. It is over 90% idle.  My desktop is inside the VM, but my local workstation is on a different computer.

---

### Post by Yellow Pasque on 2024-05-25
> **daniell59 said:**
> A reviewer in PC Parts Picker said that he had great difficulty installing Ethernet Drivers in Linux. Why would that be the case.

Don't know, but Ubuntu 24.04 should have no problem with the RTL8125B. First off, it works at Gigabit speed with the r8169 driver since Ubuntu 20.04. Second, if you want the 2.5Gbps speed, 24.04 makes it easy with r8125-dkms package available in the standard repos. (Or use PPA if you demand the latest version: [https://launchpad.net/~awesometic/+archive/ubuntu/ppa?field.series_filter=noble](https://launchpad.net/~awesometic/+archive/ubuntu/ppa?field.series_filter=noble) )

>  I don't want added complications in my life. I will search for a MB that has an Intel NIC

Considering that most AMD mobos use Realtek LAN, you will be adding complication to your life if you limit your onboard LAN choice to Intel. Realtek is just fine for day to to day usage (i.e. not doing thing like extreme gaming, NAS, etc.). If you really require an Intel NIC, you can get a dedicated Intel NIC for $25

---

