---
title: "Need motherboard for Ryzen 5600g"
date: 2023-06-21
forum: Hardware
---

### Post by sofasurfer on 2023-06-21
I'm having trouble understanding all the mumbo jumbo so I'm asking for advice. I'm a common desktop internet browser, video watcher, podast downloader and sometime bookkeeper with a splash of image editor and writer. I am building a new pc and want to be food for years to come...all on a tight budget. I have decided on a Ryzen 5600g cpu. I am having trouble finding a compatible motherboard. I need an ATX form factor. I have located a ASUS Prime B550-PLUS ( [https://www.amazon.com/ASUS-B550-PLUS-Motherboard-DisPlayPort-Addressable/dp/B089CT5GDM?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=ATVPDKIKX0DER&th=1](https://www.amazon.com/ASUS-B550-PLUS-Motherboard-DisPlayPort-Addressable/dp/B089CT5GDM?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&smid=ATVPDKIKX0DER&th=1) ). At $129 it is about as much as I want to spend. I think this is about as good as I will ever need. I do wish iy was a little less expensive though. Please verify if this MB will work with the Ryzen 5600g. 
If you have any more affordable ideas please tell me. I read that Ryzen 5600g does not have PCIe so maybe this motherboard is overkill...but is it really a significant factor.
Anyway, your thoughts are appreciated.

---

### Post by QIII on 2023-06-21
While it does not support PCIe 4.0, it does support PCIe 3.0.  It won't support PCIe 4.0 because AMD compromised to put the GPU on the die.

If you have a PCIe 3.0 board, you're fine.  With a PCIe 4.0 board, you will get PCIe 3.0 speeds.  The PCIe 4.0 spec is backwards compatible with PCIe 3.0 -- but will only perform at PCIe 3.0 spec.

---

### Post by TheFu on 2023-06-21
PCPartPicker is where I start when building new systems. [https://pcpartpicker.com/builds/](https://pcpartpicker.com/builds/) has examples.  I like to reuse components for as long as possible to keep costs down.  For example, I have a case from 1999 that I've been using for 2+ decades.  Why buy stuff we don't need?  My typical upgrade is a MB+CPU and I reuse everything else.  Last fall, I did a pure CPU-only upgrade because the 40% faster CPU was the same socket type (AM4) as the prior CPU used. It was an easy swap for $120 to get 40% more performance.

I start by choosing the CPU.  I have 2 systems with Ryzen 5600G APUs. They were a good value at the time. Don't know if they still are.  Anyway, those APUs are AM4, so they need an AM4 motherboard.  APU is AMD's way of saying it is a CPU+integrated GPU.  I have B450s, but the B550 would be fine too and allow upgrades to the Ryzen 6xxx line when those CPUs get cheaper in a few years.

All x86_64 motherboards in the last 10+ yrs have supported PCIe.  Don't worry too much about v3 or v4. If you aren't using $500 CPUs and $500 GPUs, it doesn't matter.

I believe the Asus "Prime" line uses inferior network options.  That's your choice.  I want an Intel NIC in my motherboard to avoid dumb problems that seem to follow the other options.  Intel did have some issues with their 2.5Gbps NICs (which I think the Asus B550 STRIX used.  Do your research on the NIC in the motherboard you've selected.  Perhaps there aren't any remaining issues. It has been almost 2 yrs.  Definitely check. Don't assume everything will be fine.  You may end up buying a $30 PCIe Intel NIC to use until those issues are fixed, eventually.  I specifically did not buy an Asus B550 to avoid 2.5Gbps NIC issues that were common at the time.

Here's the board I have:
```
$ inxi -bz
System:    Kernel: 5.15.0-75-generic x86_64 bits: 64 Desktop: FVWM2 2.6.8 
           Distro: **Ubuntu 20.04.6 LTS** (Focal Fossa) 
Machine:   Type: Desktop Mobo: **ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx** serial: <filter> 
           UEFI: American Megatrends v: 5003 date: 02/03/2023 
CPU:       6-Core: AMD **Ryzen 5 5600G** with Radeon Graphics type: MT MCP speed: 4171 MHz min/max: 1400/4200 MHz 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] driver: amdgpu v: kernel 
           Display: x11 server: X.Org 1.20.13 **driver: amdgpu**,ati unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-75-generic LLVM 12.0.0) v: 4.6 Mesa 21.2.6 
Network:   Device-1: [B]Intel I211 Gigabit Network driver: igb 
[/B]Drives:    Local Storage: total: 1.83 TiB used: 146.58 GiB (7.8%) 
Info:      Processes: 425 Uptime: 3d 23h 27m Memory: 30.71 GiB used: 5.50 GiB (17.9%) Shell: bash inxi: 3.0.38
```

I'm using this sort of RAM:
```
$ sudo inxi -mxx
Memory:    RAM: total: 30.71 GiB used: 5.41 GiB (17.6%) 
           Array-1: capacity: 128 GiB slots: 4 EC: None max module size: 32 GiB note: est. 
           Device-1: DIMM_A1 size: No Module Installed 
           Device-2: DIMM_A2 size: 16 GiB speed: 3200 MT/s type: DDR4 manufacturer: **G Skill Intl part-no: F4-3200C16-16GVK** 
           Device-3: DIMM_B1 size: No Module Installed 
           Device-4: DIMM_B2 size: 16 GiB speed: 3200 MT/s type: DDR4 manufacturer: **G Skill Intl part-no: F4-3200C16-16GVK **

```
Ryzen is known to be picky about RAM.  You'll also want to load the current, latest BIOS to get more compatibility.  Asus used to make that really easy - directly over the internet, but they removed that capability in newer BIOS versions.

Also, it is worth your time to read the motherboard guide BEFORE buying.  Most motherboards have some unexpected limitations.  For example, mine have (2) m.2 slots which would typically be used for an NVMe storage.  When that gets used, it steals bandwidth from the CPU slots, which may or may not matter.  Additionally, if you use an m.2 SATA SSD, then you'll need to set the slot to SATA mode, which makes 2 normal SATA ports unusable.  Talk about a surprise, if you don't know it will happen.  Today, that doesn't matter so much, since NVMe and SATA m.2 SSDs cost about the same.  3 yrs ago, NVMe SATA was 2x the price.

If you stay with an AM4 socket and a B4xx/B5xx or X470/X570 motherboards, you'll be fine, probably. There are no guarantees.  None of those motherboards will support the Ryzen 7xxxx line, which is AM5 w/ DDR5 RAM.  You are buying at the end of a socket run.  AMD sockets last longer, support more CPUs and usually support the same type of RAM, DDR4 for AM4.  At this point, the Ryzen 7xxx series with a newer AM5 motherboard and DDR5 RAM.  

Intel seems to have new sockets every 2 yrs, so what should be a simple CPU-only upgrade becomes a CPU+motherboard upgrade - adding $60-$200 to that cost.

Anyway, hope this is helpful.  Take notes, do your research, track important caveats.

---

### Post by aljames2 on 2023-06-21
You could consider the B450 version of that board which is PCIe 3.0 as already mentioned. All you really need for the 5600g cpu.  This would address your concern over price.
[https://www.amazon.com/ASUS-Prime-II-Motherboard-Flashback/dp/B08KH12V25/ref=mp_s_a_1_3?crid=COP1XI3NTHE7&keywords=5600g+asus+b450&qid=1687366596&sprefix=5600g+asus+b450%2Caps%2C112&sr=8-3](https://www.amazon.com/ASUS-Prime-II-Motherboard-Flashback/dp/B08KH12V25/ref=mp_s_a_1_3?crid=COP1XI3NTHE7&keywords=5600g+asus+b450&qid=1687366596&sprefix=5600g+asus+b450%2Caps%2C112&sr=8-3)

No real upgrade room though on the B450 board, but this may be all you need, to do the things you want.

---

### Post by Yellow Pasque on 2023-06-23
> **QIII said:**
> While it does not support PCIe 4.0, it does support PCIe 3.0.  It won't support PCIe 4.0 because AMD compromised to put the GPU on the die.

Not quite. Zen3 CPU's, including the 5600G, have 20 lanes of PCIe 4.0 (and another 4 lanes of PCIe 3.0 that connect to the chipset). Usually, the 20 lanes connect the CPU to the PCIe GPU slot and an M.2/SSD slot. See diagram: [https://www.overclock3d.net/reviews/cpu_mainboard/here_s_what_you_need_to_know_about_amd_s_b550_chipset/1](https://www.overclock3d.net/reviews/cpu_mainboard/here_s_what_you_need_to_know_about_amd_s_b550_chipset/1)

When you say "compromised with PCIe 3.0", I believe what you are thinking of is the B550 chipset itself, which uses PCIe 3.0 lanes. AMD chose not to PCIe 4.0 on the B550 to keep its power/transistor budget down, and because the extra bandwidth isn't needed on most single GPU systems.
The X570 chipset is for those who want PCIe 4.0 throughout the whole setup, but it is more costly and harder to cool (some mobos even use fans on it).

[QUOTE=TheFu]Do your research on the NIC in the motherboard you've selected[/QUOTE]

The board the OP's looking at uses a Realtek RTL8111H chip, which should work without issue. I have the same chipset in my MSI B550 Mag Tomahawk and it works well enough for my needs without any extra configuration. Intel does have great network chips, but it's not something I'd worry about in regards to the OP's use cases.

---

### Post by him610 on 2023-06-24
> I want an Intel NIC in my motherboard to avoid dumb problems that seem to follow the other options.
TheFu gives good advice here. Intel NIC is one of my motherboard requirements for a system build.

---

### Post by Yellow Pasque on 2023-06-25
> **him610 said:**
> Intel NIC is one of my motherboard requirements for a system build.

Why? Intel chips are known for less CPU usage vs. Realtek, but I don't think most users would notice a difference with typical web browsing. I think it's going to be hard to find a good B450/B550 board with Intel NIC around the OP's budget line. Maybe you folks should recommend a specific motherboard for the user if you feel Intel NIC is a dealbreaker.

---

### Post by Yellow Pasque on 2023-06-25
NVM (double post)

---

### Post by exploder on 2023-06-25
I am using an ASRock  B450/ac R2.0 with a 5600g. I've not had any issues at all with it running any Linux distro.

---

### Post by him610 on 2023-06-25
I built this about 3 years ago.
```
$ inxi -M
Machine:
  Type: Desktop Mobo: ASRock model: B450M/ac
```

They still sell them at Amazon for a reasonable price. (~$75)
[https://www.amazon.com/ASRock-B450M-Promontory-Micro-Motherboard/dp/B09KZYMP8P/ref=asc_df_B09KZYMP8P/?tag=hyprod-20&linkCode=df0&hvadid=583259186550&hvpos=&hvnetw=g&hvrand=9516859188244995399&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9052643&hvtargid=pla-1642229600054&psc=1&gclid=Cj0KCQjwy9-kBhCHARIsAHpBjHjZD4Wqhn4SqtREDMOcJsoogUEBy-Gw-QhJx_ZFP64koWsxkPeeQDQaAlSQEALw_wcB]("https://www.amazon.com/ASRock-B450M-Promontory-Micro-Motherboard/dp/B09KZYMP8P/ref=asc_df_B09KZYMP8P/?tag=hyprod-20&linkCode=df0&hvadid=583259186550&hvpos=&hvnetw=g&hvrand=9516859188244995399&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9052643&hvtargid=pla-1642229600054&psc=1&gclid=Cj0KCQjwy9-kBhCHARIsAHpBjHjZD4Wqhn4SqtREDMOcJsoogUEBy-Gw-QhJx_ZFP64koWsxkPeeQDQaAlSQEALw_wcB")

---

### Post by TheFu on 2023-06-25
> **Yellow Pasque said:**
> Why? Intel chips are known for less CPU usage vs. Realtek, but I don't think most users would notice a difference with typical web browsing. I think it's going to be hard to find a good B450/B550 board with Intel NIC around the OP's budget line. Maybe you folks should recommend a specific motherboard for the user if you feel Intel NIC is a dealbreaker.

Thought I did by posting my exact motherboards and saying I have 2 of them.

When it comes to Linux compatibility, I usually start with BSD compatibility.  Let me explain.  "Linux compatible" has all sorts of caveats, I've learned and been burned.  Got a "Linux Compatible" RAID HBA many years ago only to discover that the RAID parts of it only worked with a 3 yr old kernel. No updates for newer kernels were made.  OTOH, if a company supports BSD, then they generally support Linux extremely well too ... with F/LOSS drivers.  So, when I'm buying hardware, I look for BSD support.  Works for scanners, printers, and peripherals too.  Intel seems to support BSD across their line, while RealTek has a list of 5 - just 5 - NICs that work on BSD.  

Plus I've had quality issues with a few different RealTek and Marvell NICs.  Failures and dropped packets, That's no good for a desktop system that isn't in industrial environments.  One of them worked fine for 2 yrs, then started dropping packets.  I was an early adopter of GigE at home.  The first cheap NICs I got, Marvell, peaked around 250 Mbps. To get GigE back then, spending $150 for the NIC was necessary.  But even 250 Mbps was twice as fast and worth it to me.

Also, the performance for GigE was never near what the $25 Intel NIC I bought to replace the failing Realtek got.  There's just something not as good and if I can avoid that by spending $20 more on a motherboard, that's a bargain to me.

Remember "Win-Modems?"  They were mostly software driver-based and didn't work with Linux until someone figured out how to create a wrapper so the Windows drivers worked on Linux.  I bought one - when I was new to Linux and didn't know better.  It was one of my first lessons.  I avoid "hardware" that offloads to the CPU.  That has always bothered me.  Fake RAID does that too.  All the limitations of HW-RAID, but none of the performance or flexibility of SW-RAID.  Realtek NICs feel like that to me.

---

### Post by Yellow Pasque on 2023-06-26
> **TheFu said:**
> Thought I did by posting my exact motherboards and saying I have 2 of them.

That model seems a good bit out of the OP's price range. I think it was one of the higher end B450 boards. I have a similar B450 Gigabyte/Aorus board, which has Intel NIC and Wifi, but I wouldn't recommend it to the OP.

> Plus I've had quality issues with a few different RealTek and Marvell NICs.  Failures and dropped packets

Yeah, I've had some issues with Realtek NIC's at times. They were usually sorted out by subsequent kernels. But when specifically looking at the RTL8111H, which a lot of B550 boards use, I don't have an issue nor do I remember seeing any reports of them on modern kernels.

> Remember "Win-Modems?" Realtek NICs feel like that to me.

Yes, I do remember Winmodems very well. (The Lucent ones I had weren't too bad, at least on Windows, since they at least had their own DSP.) But I don't see a direct parallel to the current situation. Back then, we had much slower, single core CPU's, and the winmodems required more configuration to work on Linux. The amount of CPU a NIC might use today is nominal in most SOHO cases. The same goes for onboard audio. It used to be a big deal to have a dedicated audio processor rather than an onboard one. Today, not so much. And, as I said, the RTL8111H driver is baked into the Linux kernel and should work out of the box unless running an old kernel. Requiring Intel network chips is going to eliminate a lot of potential mobo's for the OP, but maybe they will see the value proposition the same way you do.

---

### Post by TheFu on 2023-06-26
> **Yellow Pasque said:**
>  

Yes, I do remember Winmodems very well. (The Lucent ones I had weren't too bad, at least on Windows, since they at least had their own DSP.) But I don't see a direct parallel to the current situation. Back then, we had much slower, single core CPU's, and the winmodems required more configuration to work on Linux. The amount of CPU a NIC might use today is nominal in most SOHO cases. The same goes for onboard audio. It used to be a big deal to have a dedicated audio processor rather than an onboard one. Today, not so much. And, as I said, the RTL8111H driver is baked into the Linux kernel and should work out of the box unless running an old kernel. Requiring Intel network chips is going to eliminate a lot of potential mobo's for the OP, but maybe they will see the value proposition the same way you do.

I returned the WinModem and got one with the correct UART.  I don't remember the exact UART, xxx650a?, but there was a specific model that "just worked". It wasn't/isn't worth my time to struggle with difficult hardware. [https://tldp.org/HOWTO/Serial-HOWTO-18.html](https://tldp.org/HOWTO/Serial-HOWTO-18.html)

As for audio, I had a few SB-Live 5.1 PCI cards that moved to every new system I owned for about a decade. Because they were well supported and didn't need any specialized help to work.  Not high-end audio, but sufficient for my needs.  Eventually almost all built-in MB audio "just worked" and that has been sufficient on desktops for my needs.

I thought NICs would "just work" and understood that some were less cable, but still worked.  Then I had a string of quality issues with RealTek NICs.  Burn me once ... 

Most of my job is to avoid issues before they can happen. Generally, I have hardware for 10 yrs, so over the lifetime, that extra $20 is just $2/yr to retain my sanity.  I didn't always think this way. The first 10 yrs, I spent way too much time trying to make unsupported and poorly implemented hardware work.

---

### Post by Yellow Pasque on 2023-06-26
Well, we haven't got much feedback from the OP at this point, but I''d recommend this: [https://www.amazon.com/MSI-B550M-PRO-VDH-ProSeries-Motherboard/dp/B089D1YG11/ref=sr_1_2?keywords=B550M+PRO-VDH](https://www.amazon.com/MSI-B550M-PRO-VDH-ProSeries-Motherboard/dp/B089D1YG11/ref=sr_1_2?keywords=B550M+PRO-VDH)

---

### Post by TheFu on 2023-06-26
If using the B550 chipset is desired, for $10 more: [https://www.amazon.com/ASUS-ROG-B550-F-Motherboard-Addressable/dp/B0915BYW7Z](https://www.amazon.com/ASUS-ROG-B550-F-Motherboard-Addressable/dp/B0915BYW7Z) - with intel 2.5Gbps NIC.
There are motherboards for $20 cheaper, B520 with the whatever chipset ... no Intel NIC.  I'd probably skip the B520 or B420 chipsets, since they have fewer RAM slots and fewer PCIe slots - enough to be an issue if you need to add a few other cards. No 10Gbps USB3.2 either.

An *Asus Prime B450M-A II* is $70 currently, with a $10 promotion at newegg.
An *MSI B450M PRO-VDH MAX Micro ATX AM4 Motherboard* is $75 at amazon.

I've been happy enough with MSI or Asus, but disappointed with most other vendors. One MB worked for a few years, before different parts started failing, slowly.  At the end, even getting into the BIOS was nearly impossible. It ignored the BIOS activation keystrokes about 19 out of 20 attempts.

I'd hit pcpartpicker.net to get the major filters like CPU compatibility, m.2 slots, SATA ports, audio, .... Sadly, they don't list NIC chips, so that cannot be easily filtered beyond claimed speed.

---

### Post by Yellow Pasque on 2023-07-01
> **QIII said:**
> While it does not support PCIe 4.0, it does support PCIe 3.0.  It won't support PCIe 4.0 because AMD compromised to put the GPU on the die.

I have to apologize because you were right about the 5x00G APU's having PCI-e 3.0. AMD's graphic was made before the APU's came out. It makes sense because a PCI-e 4.0 GPU slot isn't needed with integrated graphics.

> **TheFu said:**
> If using the B550 chipset is desired, for $10 more: [https://www.amazon.com/ASUS-ROG-B550-F-Motherboard-Addressable/dp/B0915BYW7Z](https://www.amazon.com/ASUS-ROG-B550-F-Motherboard-Addressable/dp/B0915BYW7Z) - with intel 2.5Gbps NIC.

It's refurbished/"renewed", but if the OP doesn't mind that, it could be a good board.

> I've been happy enough with MSI or Asus, but disappointed with most other vendors.

It's been a mixed bag for me. I remember some bad midrange boards from MSI and ASUS. I had a midrange ASUS 690G board that insisted on putting extra voltage into the CPU at default settings (seemed like ASUS assumed everyone wanted to overclock) and probably overheated/killed a beloved Athlon X2 5050e with a passive cooling setup. I also had a midrange MSI 690G board that had a really bad cooler on the chipset (I could wiggle it a bit). I tried to reattach the cooler with better thermal material, but that board didn't last too long.
Still, I try not to overgeneralize. I don't build as many systems these days, but I'm happy with my current MSI mobo, and I used to avoid Gigabyte mobos for AMD CPU's, but the last system I built with one was just fine. I evaluate on a case by case basis and don't put too much stock into mobo brand names unless I see an overwhelming trend in reviews that says otherwise.

> I'd hit pcpartpicker.net to get the major filters like CPU compatibility, m.2 slots, SATA ports, audio, .... Sadly, they don't list NIC chips, so that cannot be easily filtered beyond claimed speed.

They don't list specific audio chipsets either, because mobo makers realized a true premium onboard audio processor was a poor return on investment by 2005 or so. If people wanted better audio than what the mobo offered, they would get a dedicated card like you with the SB-Live or me with my beloved M-Audio Revolution card (which hopped around my systems for more than a decade until PCI slots went away).
I feel like onboard NIC's are the same way nowadays. Cheap Realtek 81xx series chips get the job done in most cases, even on Linux. If they don't, then the user is probably better off finding a dedicated PCI-e NIC than limiting themselves to specific mobos with certain network chipsets. There are some exceptions like small form factors where PCI-e slots are limited or larger systems that require a bunch of other PCI-e peripherals. But otherwise, it's not as big of a deal as it used to be.

---

