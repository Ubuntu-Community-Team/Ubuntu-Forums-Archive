---
title: "recommendations for graphic card needed (old hardware)"
date: 2021-02-13
forum: Hardware
---

### Post by ATSC on 2021-02-13
Good evening!

1.: I'm fairly satisfied with my stone-age computer but the graphics card lags a bit. Unfortunately, my knowledge about  hardware is almost as old as the computer itself - hence the need for suggestions. I really don't need anything fancy - I use the machine mostly for surfing, a bit of office  work etc.. If possible,  it should be a card that I can buy used for little money.
2.: The current one is an onboard graphics card. Is there anything I have to keep in mind when I put a 2nd one in?

Here are some technical specs - I hope this helps?
```
inxi -Fxz
System:
  Host: benni-M2NS-NVM Kernel: 4.15.0-135-generic x86_64 bits: 64 
  compiler: gcc v: 7.5.0 Desktop: MATE 1.22.2 Distro: Linux Mint 19.3 Tricia 
  base: Ubuntu 18.04 bionic 
Machine:
  Type: Desktop Mobo: ASUSTeK model: M2NS-NVM v: 1.XX serial: <filter> 
  BIOS: Phoenix v: ASUS M2NS-NVM Revision 0401 date: 09/28/2006 
CPU:
  Topology: Dual Core model: AMD model unknown bits: 64 type: MCP 
  arch: K8 rev.F+ rev: 2 L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 svm bogomips: 4018 
  Speed: 1000 MHz min/max: 1000/3100 MHz Core speeds (MHz): 1: 1000 2: 1000 
Graphics:
  Device-1: NVIDIA C61 [GeForce 6100 nForce 405] vendor: ASUSTeK 
  driver: nouveau v: kernel bus ID: 00:0d.0 
  Display: server: X.Org 1.19.6 driver: nouveau 
  unloaded: fbdev,modesetting,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: NV4C v: 2.1 Mesa 20.0.8 direct render: Yes 
Audio:
  Device-1: NVIDIA MCP61 High Definition Audio vendor: ASUSTeK 
  driver: snd_hda_intel v: kernel bus ID: 00:05.0 
  Sound Server: ALSA v: k4.15.0-135-generic 
Network:
  Device-1: NVIDIA MCP61 Ethernet vendor: ASUSTeK type: network bridge 
  driver: forcedeth v: kernel port: ec00 bus ID: 00:07.0 
  IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 931.51 GiB used: 70.04 GiB (7.5%) 
  ID-1: /dev/sda vendor: Toshiba model: HDWD110 size: 931.51 GiB 
Partition:
  ID-1: / size: 18.21 GiB used: 11.61 GiB (63.8%) fs: ext4 dev: /dev/sda1 
  ID-2: /home size: 889.27 GiB used: 58.43 GiB (6.6%) fs: ext4 
  dev: /dev/sda6 
  ID-3: swap-1 size: 9.31 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 40.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 163 Uptime: 2h 29m Memory: 7.76 GiB used: 2.34 GiB (30.2%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.5.0 Shell: bash v: 4.4.20 
  inxi: 3.0.32 


```
```
sudo dmidecode -t 9
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.3 present.

Handle 0x002C, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x002D, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x002E, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIEX16
    Type: x16 PCI Express
    Current Usage: Available
    Length: Short
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x002F, DMI type 9, 13 bytes
System Slot Information
    Designation: PCIEX1_1
    Type: x1 PCI Express
    Current Usage: Available
    Length: Short
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported


```

```
sudo lspci -vv | grep -E 'PCI bridge|LnkCap'
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
    Capabilities: [b8] Subsystem: NVIDIA Corporation MCP61 PCI bridge
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        LnkCap:    Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <512ns, L1 <4us
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        LnkCap:    Port #1, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <512ns, L1 <4us
00:0c.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
        LnkCap:    Port #2, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <512ns, L1 <4us


```
```
sudo dmidecode | grep "PCI"
        PCI is supported
    Designation: PCI1
    Type: 32-bit PCI
    Designation: PCI2
    Type: 32-bit PCI
    Designation: PCIEX16
    Type: x16 PCI Express
    Designation: PCIEX1_1
    Type: x1 PCI Express


```

Any help is much appreciated! :-)

---

### Post by TheFu on 2021-02-13
What's the budget?  
Even cheap cards run $80 and a system upgrade that comes with an onboard GPU will probably be less than $200 total on the low end have a nice iGPU.
I couldn't figure out the CPU model you actually have.  /proc/cpuinfo should have the exact model name inside it.  Please check that out.

For people like you and me, iGPUs that come with the CPU are best.  AMD makes some A6 APUs and I've seen used/refurbished systems for between $50 and $130.

Last Sept, AMD Ryzen for desktops was cheap, but since then all computer stuff has been overpriced.  We can thank the price of bitcoin, I suppose for all the shortages. GPUs are how normal people mine bitcoins.  I have a low-end nvidia GPU - a GT 1030. It is $80 today, which is what I paid for it 2 yrs ago. Actually, I paid $70 then.  Now is not the time to buy computer stuff - except SSD and flash storage.

The problem buying older GPUs that are less, is that the proprietary drivers lose support.  I had an nvidia GPU that was still working, but when I moved to 16.04, the drivers to support the native resolution of my 1200p monitor weren't available.  The support ended.  So, if I were doing this again, I wouldn't buy an nvidia GPU if you plan to have it for a decade.  You'll be stuck using the F/LOSS drivers which may not support any resolution higher than 1024p.

---

### Post by ATSC on 2021-02-14
> **TheFu said:**
> What's the budget?  

Hmm, perhaps 10-20€?

> **TheFu said:**
> Please check that out.


```
cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Processor model unknown
stepping    : 2
cpu MHz        : 1800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl cpuid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv
bugs        : fxsave_leak sysret_ss_attrs null_seg swapgs_fence amd_e400 spectre_v1 spectre_v2
bogomips    : 3616.83
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 107
model name    : AMD Processor model unknown
stepping    : 2
cpu MHz        : 1800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good nopl cpuid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch vmmcall lbrv
bugs        : fxsave_leak sysret_ss_attrs null_seg swapgs_fence amd_e400 spectre_v1 spectre_v2
bogomips    : 3616.83
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps


```

Many thanks for your support. :-)

---

### Post by Autodave on 2021-02-14
That is weird that the CPU is identified.  I really don't know if a GPU is going to help much seeing the slow speed of that processor: you may be wasting your money.

---

### Post by TheFu on 2021-02-14
> **Autodave said:**
> That is weird that the CPU is identified.  I really don't know if a GPU is going to help much seeing the slow speed of that processor: you may be wasting your money.

Agreed. A used chromebook from 2012 running Linux would be faster and have a fine iGPU, but not within the budget.
I've never seen any GPU, used or new, for less than 30€ -ish.  EVER.

---

### Post by rsteinmetz70112 on 2021-02-16
I think the CPU is an AMD Athlon64 X2 I think the board will take an AMD FX, but not sure how fast.

---

### Post by CelticWarrior on 2021-02-16
The motherboard has
> 1 x PCI-Express x16
Theoretically it can support any PCI-E graphics. Any ~8-10 years old card will be a noticeable improvement and at the same time a not so imbalanced hardware mix.
That said I doubt you can find any within budget.

---

### Post by MartyBuntu on 2021-02-16
I'd save my money up.

---

### Post by mastablasta on 2021-02-17
get an RTX or RX... you can always upgrade the rest later on. just kidding. yeah it's not good to buy CPU or GPU. prices are way too high in most cases. due to problems in manufacturing of new versions the old ones kept their prices high.

nvidia GT1030 - arround 80 EUR; you might be able to get older model GT730 for less, but it's already in legacy and support will likely stop with 20.04 default kernel (5.4) or maybe it will go up to 22.04, but probably not. anyway these can easily handle even some light gaming.
nvidia GT 1010 - new should be around 40 EUR- 50 EUR, but i haven't see it here yet. the older GT710 model goes for 40-45 EUR. these are meant mostly for media, browsing, some office work. the 710 has same issue as 730 with support. though they might extend it since they are reselling older cards now due to lack of new ones.

i too have an old AMD form that era. mine is single core. i had an AMD card and opensource support was good for it, but the card died. so i got GT730. it was good purchase, just wish it had longer support or good opensource driver support. anyway with desktop PC, you can keep the card if you ever decide to replace the CPU and motherboard, so it pays to invest a bit more if you are doing an upgrade. in your case (and if you want to keep current motherboard and CPU) i would go with GT1030 or equivalent AMD card for about 80-100 EUR.

---

### Post by him610 on 2021-02-17
I see your BIOS dates from 2006. I once had a Shuttle (Athlon64 X2 5600+) from that time period which had one slot for a video card where I installed a NVIDIA G86 [GeForce 8500 GT]. I used that machine for about ten years before I replaced it. That particular card can be found on Ebay for around $30 US. The thing about old hardware is sometimes the vendors, or even the open source community quits supporting them, or the current drivers do not work with them. You might consider a card made a few years later similar to the GT730 suggested in #9. 
Did you consider saving your Euros and shopping for a used, newer model computer on Ebay or whatever online markets exist in Germany (EU)?

---

