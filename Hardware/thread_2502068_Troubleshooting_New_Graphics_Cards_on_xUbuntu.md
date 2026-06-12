---
title: "Troubleshooting New Graphics Cards on xUbuntu"
date: 2024-10-31
forum: Hardware
---

### Post by zoomiest2 on 2024-10-31
I just bought new (inexpensive) graphics cards, and installed them in my desktop computer, running the most recent version of xUbuntu.
They were painfully slow!
I installed ubuntu-drivers, and restarted the computer. The UI was still painfully slow. 

What does a slow interface mean? 

Is this the outcome of being too cheap to buy high end graphics cards, or is there something I can do to speed these up?

The cards are *Glorto Radeon HD 5450 1GB GPU.*

---

### Post by TheFu on 2024-11-01
Radeon HD 5450 is 15 yr old.  You've already selected the "lite" Xubuntu DE, so there isn't much more you can do.  I'd think it should be fine for that DE.

When it comes to Linux, and you already know this, you'll need to look at the log files to know what is actually the issue.  It could be thousands of things.

I've never heard of "Glorto".

Also, your idea of "most recent version" and ours can be different, so please run this command and post the results:
**inxi -bGxz**
When posting, show both the command AND the output. Also, use the Advanced Editor and wrap that cmd+output in forum code tags so the columns line up.  

Doing this doesn't mean you don't still need to review the log files.  If you need to learn how to do that, google "ubuntu log files" for guides, as there are many different methods and tricks to reduce how much you actually look at in many hundreds of thousands of lines of logs.

---

### Post by zoomiest2 on 2024-11-02
Is this how you prefer to see the output? Thanks for your help.
```
zoomiest@VMech:~$ inxi -bGxzSystem:
  Kernel: 6.8.0-48-generic x86_64 bits: 64 compiler: N/A Desktop: Xfce 4.16.0
    Distro: Ubuntu 22.04.5 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop Mobo: ASUSTeK model: SABERTOOTH X79 v: Rev 1.xx
    serial: <superuser required> UEFI: American Megatrends v: 1104
    date: 04/10/2012
CPU:
  Info: quad core Intel Core i7-3820 [MT MCP] arch: Sandy Bridge speed (MHz):
    avg: 2250 min/max: 1200/3800
Graphics:
  Device-1: AMD Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
    vendor: Hightech Information System driver: radeon v: kernel
    bus-ID: 01:00.0
  Device-2: AMD Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
    vendor: Hightech Information System driver: radeon v: kernel
    bus-ID: 02:00.0
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: ati,modesetting
    unloaded: fbdev,radeon,vesa gpu: radeon resolution: 1: 1050x1680~60Hz
    2: 1680x1050~60Hz
  OpenGL: renderer: AMD CAICOS (DRM 2.50.0 / 6.8.0-48-generic LLVM 15.0.7)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes
Network:
  Device-1: Intel 82579V Gigabit Network vendor: ASUSTeK P8P67 Deluxe
    driver: e1000e v: kernel port: f040 bus-ID: 00:19.0
Drives:
  Local Storage: total: 11.03 TiB used: 109.09 GiB (1.0%)
Info:
  Processes: 303 Uptime: 13m Memory: 19.51 GiB used: 2.21 GiB (11.3%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2525 Shell: Bash
  v: 5.1.16 inxi: 3.3.13



```

---

### Post by zoomiest2 on 2024-11-02
I thought this was interesting, but I don't know exactly what to do about it.
```
zoomiest@VMech:/var/log$ sudo cat gpu-manager.log |morelog_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/6.8.0-48-generic/kernel
Looking for nvidia modules in /lib/modules/6.8.0-48-generic/kernel/nvidia-550srv
Looking for nvidia modules in /lib/modules/6.8.0-48-generic/kernel/nvidia-550
Looking for nvidia modules in /lib/modules/6.8.0-48-generic/kernel/nvidia-535srv
Looking for nvidia modules in /lib/modules/6.8.0-48-generic/kernel/nvidia-535
Looking for nvidia modules in /lib/modules/6.8.0-48-generic/kernel/nvidia-470srv
Looking for nvidia modules in /lib/modules/6.8.0-48-generic/kernel/nvidia-470
Found nvidia.ko module in /lib/modules/6.8.0-48-generic/kernel/nvidia-470/nvidia.ko
Looking for amdgpu modules in /lib/modules/6.8.0-48-generic/kernel
Looking for amdgpu modules in /lib/modules/6.8.0-48-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? yes
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 1002:6779
BusID "PCI:1@0:0:0"
Is boot vga? yes
Vendor/Device Id: 1002:6779
BusID "PCI:2@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:02:00.0/driver
The device is not bound to any driver.
Skipping "/dev/dri/card1", driven by "radeon"
Found "/dev/dri/card1", driven by "radeon"
output 0:
    card1-DVI-D-1
Number of connected outputs for /dev/dri/card1: 1
Skipping "/dev/dri/card1", driven by "radeon"
Skipping "/dev/dri/card0", driven by "radeon"
Skipping "/dev/dri/card1", driven by "radeon"
Skipping "/dev/dri/card0", driven by "radeon"
Does it require offloading? no
last cards number = 2
Has amd? yes
Has intel? no
Has nvidia? no
How many cards? 2
Has the system changed? No
AMD IGP detected
Desktop system detected
or laptop with open drivers
Nothing to do



```

---

### Post by zoomiest2 on 2024-11-02
I will just return these terrible graphics cards... Sorry to bother you. Thank you for the information about their age.

---

### Post by Yellow Pasque on 2024-11-02
I don't see anything interesting/unexpected, except maybe:
> Found nvidia.ko module in /lib/modules/6.8.0-48-generic/kernel/nvidia-470/nvidia.ko
Why do you have the nvidia 470 driver installed? It shouldn't be "hurting" anything, but why?
```
sudo apt purge *470*
```

---

### Post by Yellow Pasque on 2024-11-02
> **zoomiest2 said:**
> I will just return these terrible graphics cards...

They're not that bad if all you want is a basic video output. They should run Xubuntu 24 just fine. If the interface is lagging, something seems wrong. The only thing I can think of is that you try and force the radeon X driver to be used over the generic X "modesetting" driver (and remove remnants of the nvidia 470 driver, as I pointed out in the last post).
Maybe look at /var/log/Xorg.0.log before you give up..

---

### Post by TheFu on 2024-11-02
```
Device-1: AMD Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
    vendor: Hightech Information System **driver: radeon** v: kernel
```

Says you don't have **Glorto Radeon HD 5450 1GB GPUs**  - so the prior information was incorrect.  I have no idea what a Radeon HD 6450/7450/8450 is or how old they are.  Never owned one.  The Radeon driver is already being selected. We see that above too.

[https://www.techpowerup.com/gpu-specs/radeon-r5-230-oem.c2504](https://www.techpowerup.com/gpu-specs/radeon-r5-230-oem.c2504) says the R5 230 OEM was released in Dec 2013 > Display outputs include: 1x DVI, 1x HDMI 1.3a, 1x VGA. according to that link. If both your GPUs don't match those outputs, they might be fakes.

---

### Post by Yellow Pasque on 2024-11-03
> **TheFu said:**
> I have no idea what a Radeon HD 6450/7450/8450 is or how old they are.  Never owned one.
I never owned one either, but I can take 2 seconds to look at a list: [https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units#Radeon_HD_6000_series](https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units#Radeon_HD_6000_series)
The 6450 was one generation later than the 5450 and came out a year later in 2011. (Who would've guessed?!)

> the R5 230 OEM was released in Dec 2013  according to that link.
The R5 230 was just a rebadged 6450 that came out 2-3 years later.

> If both your GPUs don't match those outputs, they might be fakes.
Why would anyone fake a 5450 with a 6450? That seems backwards, like someone needs to go back to con artist school.

---

### Post by TheFu on 2024-11-03
Doubtful this was a fake.  The fakes I'd seen where all nvidia and usually changed a low-end GT 7xx to a higher-end GT 7xx or the next level higher (whatever that was).  This was all happening when Nvidia GPUs were selling at 2x list price and being abused for crypto-currency mining.  Seems like nVidia has been effective at reducing the dual-use capabilities of their gaming GPUs for mining, so that entire effort to get any nvidia GPU for mining has dried up.

My 5450 was in an APU for a AMD E-350. The entire computer was $100 - $50 for the case + $50 for the MB+APU when I got it.  The Radeon driver on Linux at the time handled hidef, but then a new kernel line and the driver wasn't updated for the older Radeons.  I think a few years later, it was updated again, but by that point, I'd switched to a Pentium G3258, again for $100 all-in, which had a much, much, faster CPU and onboard Intel iGPU.

As for trusting what Wikipedia says, that's a judgement call.  Everywhere I worked, we were clearly told never to trust 2nd or 3rd party sources for information. Sure, we do that all the time now, but for things like GPU specs, I was unable to find the AMD spec pages with a websearch - at least not for the older GPUs.

None of this matters. Just thought my process of thought could be helpful. Perhaps not.

---

### Post by Yellow Pasque on 2024-11-04
> **TheFu said:**
> Doubtful this was a fake.  The fakes I'd seen where all nvidia and usually changed a low-end GT 7xx to a higher-end GT 7xx or the next level higher (whatever that was).
Yeah, that's makes sense. I don't think "fake" was the term you were looking for here. More like seller confusion.

> As for trusting what Wikipedia says, that's a judgement call.  Everywhere I worked, we were clearly told never to trust 2nd or 3rd party sources for information.
And you cited techpowerup, which is...??

---

### Post by TheFu on 2024-11-04
> **Yellow Pasque said:**
>  And you cited techpowerup, which is...??

Point taken. You are correct.  techpowerup and all those sorts of websites seem a little untrustworthy and prone to mistakes in their spec information. It is easy to blame a website for inaccurate data, though I also suspect that the HW they are given may be engineering variants and the design wasn't fixed when they were creating a review.  Then add in all the possible different configurations and it is a mess that needs a 4 page table to show all the possible options.

I know exactly where to find nVidia GPU specs and Intel iGPU specs on their websites even for very old hardware.

I feel bad for the OP.  I've avoided buying any GPUs since around 2018 by getting Ryzen APUs (5600G) and Raspberry Pi v4/v5 SBCs. Those won't work for everyone for a number of reasons.  I have no plans currently to replace any of them - at least not in the next 5 yrs.

---

### Post by him610 on 2024-11-06
```
... Graphics:
  Device-1: AMD Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
    vendor: Hightech Information System driver: radeon v: kernel
    bus-ID: 01:00.0
  Device-2: AMD Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
    vendor: Hightech Information System driver: radeon v: kernel
    bus-ID: 02:00.0... 
```
Looks as if there are two identical GFX cards installed. 
Could there be some sort of contention between the two?

---

### Post by Skaperen on 2024-11-06
"misinformation": they accidentally tell you the wrong speed for the chip when certain software is loaded and certain action is performed.

"disinformation": they intentionally tell you the wrong speed for the chip in the hope that you will buy many old graphics cards they still have laying around collecting dust.

if you want the latest and great speed be sure to buy cards with the latest and greatest chip, or close to that if you don't need to do all the magic that new chip can do.

---

