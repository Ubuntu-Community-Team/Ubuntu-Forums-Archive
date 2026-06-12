---
title: "Does this hardware works with linux"
date: 2016-11-23
forum: Hardware
---

### Post by sed_faster on 2016-11-23
Hello folks,

I pretend acquire this hardware:

1-Motherboard Asus Skt1151 - H110M-A/M.2 ([https://www.asus.com/pt/Motherboards/H110M-A-M-2/specifications/);](https://www.asus.com/pt/Motherboards/H110M-A-M-2/specifications/);)
2-Intel i5 6400 2.7Ghz QuadCore Skt1151;
or
2-Intel i5 6500 3.2Ghz QuadCore Skt1151;
3-Dimm 8GB DDR4 Kingston CL15 2133Mhz;

Obvious I pretend use penguin :) I use Lubuntu 16.04 LTS, because I like simplicity and I like save resource hardware to another tasks. I questioned if this setup it is totally compatible with Linux (debian, ubuntu, etc)

Thanks

---

### Post by sed_faster on 2016-11-24
Hello,

Any idea about how I should google it? Because I researched this "Asus Skt1151 - H110M-A/M.2 compatible with ubuntu" and I didn't get a good results!

thanks

---

### Post by slickymaster on 2016-11-24
Have you already check the [Ubuntu Certified Hardware]("https://certification.ubuntu.com/") list?

---

### Post by sed_faster on 2016-11-24
I don't know this website.

This mean which cpu it is compatibility with linux: [https://certification.ubuntu.com/catalog/search/?query=i5+6500](https://certification.ubuntu.com/catalog/search/?query=i5+6500) ??
I should researched about motherboard or if the cpu it is compatibility I don't need research the motherboard?

thanks

---

### Post by slickymaster on 2016-11-24
The certification is only provided for the complete systems listed.

---

### Post by Yellow Pasque on 2016-11-25
It is probably better to look at individual chipsets/components on the motherboard than trying to search the model name. I'd also recommend using the word 'linux' instead of 'ubuntu' because Ubuntu is just one of many Linux distributions.

Skylake GPU - I don't personally have experience with it
H110 chipset - should work
Realtek ALC887 audio chip - the chipset itself has worked with Linux for a long time. Unless Asus connects the output in an odd manner, it should work.
Intel I219V - I know of one minor issue folks experience with it: [http://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop](http://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop)

---

### Post by sed_faster on 2016-12-08
> **Temüjin said:**
> It is probably better to look at individual chipsets/components on the motherboard than trying to search the model name. I'd also recommend using the word 'linux' instead of 'ubuntu' because Ubuntu is just one of many Linux distributions.

Skylake GPU - I don't personally have experience with it
H110 chipset - should work
Realtek ALC887 audio chip - the chipset itself has worked with Linux for a long time. Unless Asus connects the output in an odd manner, it should work.
Intel I219V - I know of one minor issue folks experience with it: [http://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop](http://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop)

But this type of questions should not be normally and community has section and process better for resolve this questions? I am not complain, but I am having many problem to know if this board, or this pieces, works on linux.

My English it isn't better, possible this is slowing me down, but I though which type of this questions it was normally.
I found this website: [https://01.org/community](https://01.org/community) and [http://www.intel.com/content/www/us/en/support/graphics-drivers/000005520.html](http://www.intel.com/content/www/us/en/support/graphics-drivers/000005520.html) but I don't know if I need this!
Thanks to your all help

I found this websites:

[http://www.linux-hardware-guide.com/](http://www.linux-hardware-guide.com/)
[http://www.linux-drivers.org/](http://www.linux-drivers.org/)
[https://www.phoronix.com/forums/](https://www.phoronix.com/forums/)

This website is good?
Do you have experience with this website?

---

### Post by sully101 on 2016-12-31
Found this [https://www.asus.com/websites/global/aboutASUS/OS/Linux1606.pdf](https://www.asus.com/websites/global/aboutASUS/OS/Linux1606.pdf) Hope it helps :)

---

### Post by sed_faster on 2017-01-01
> **sully101 said:**
> Found this [https://www.asus.com/websites/global/aboutASUS/OS/Linux1606.pdf](https://www.asus.com/websites/global/aboutASUS/OS/Linux1606.pdf) Hope it helps :)

Thanks for your help. I found the N/A to Ubuntu on H110M-A, this means which the board is incompatible with Ubuntu and only is compatible with opensuse 13.1? Or haven't yet been tested to ubuntu?

---

### Post by sully101 on 2017-01-01
I think it means it hasn't been tested, or wont be. I'm guessing.... but maybe they only test the workstation/server boards with opensuse/redhat and desktops with ubuntu. I have a P8Z68-V Gen3 and its not even on the list but happily running mint 18.1 kernel 4.4.0-57-generic. I would love to hear how you get on as I'm looking at the H110M-A/M.2 motherboard

---

### Post by sed_faster on 2017-01-01
> **sully101 said:**
> I think it means it hasn't been tested, or wont be. I'm guessing.... but maybe they only test the workstation/server boards with opensuse/redhat and desktops with ubuntu. I have a P8Z68-V Gen3 and its not even on the list but happily running mint 18.1 kernel 4.4.0-57-generic. I would love to hear how you get on as I'm looking at the H110M-A/M.2 motherboard

My english it isn't very advanced and I can't understand this phrase "I would love to hear how you get on as I'm looking at the H110M-A/M.2 motherboard" Can be expressed in another way?

I am freak out about this subject matter. Because I need a new pc and this pc should be connect two screen, a through hdmi and another through vga! I am afraid which I can't take full advantage of the graphic card onboard! :(
Thanks

---

### Post by sully101 on 2017-01-01
> I would love to hear how you get on as I'm looking at the H110M-A/M.2 motherboard
I want to buy one too. Please let me know if you buy one.

I am worried about the m.2 ssd drive as it is shared between the sata6_1 drive. I have seen posts where the windows os has to be installed in raid mode with this motherboard.

---

### Post by sed_faster on 2017-01-01
When do you plan to buy your motherboard?
I don't will need this option, the m.2 ssd, for this I will buy this version ([https://www.asus.com/Motherboards/H110M-A-D3/](https://www.asus.com/Motherboards/H110M-A-D3/))
I am newbie on this stuff, and I only repair on this version after googled a lot about this :)

I like the board and brand Asus. It is my favorite brand. I want only power and versatile option connection hdmi and vga on same board! This is awesome! I don't intend play on this pc. But maybe, once time I will install windows 7 on dualboot with linux, I will play a little on windows :)

But to the run windows 7, to run autocad, eplan, photoshop and another property software, and run the greatest Lubuntu I think this board and setup it is good! Let me know if you have the same opinion about this subject matter.

Yes, When I buy this board I will report. I intend help community with my report and benchmark!

---

### Post by sully101 on 2017-01-02
This page has specifications for the Intel 530 graphics [https://communities.intel.com/external-link.jspa?url=http%3A%2F%2Fwww.intel.com%2Fcontent%2Fwww%2Fus%2Fen%2Fprocessors%2Fcore%2F6th-gen-core-family-mobile-h-processor-lines-datasheet-vol-1.html](https://communities.intel.com/external-link.jspa?url=http%3A%2F%2Fwww.intel.com%2Fcontent%2Fwww%2Fus%2Fen%2Fprocessors%2Fcore%2F6th-gen-core-family-mobile-h-processor-lines-datasheet-vol-1.html)

The motherboard should support the modes and resolutions listed there but Asus may have also decided to disable features on their board. ( unlikely but possible ).

Both the H110M-A and H110M-A/M.2 Support two displays.

The difference where the H110M-A has passed with OpenSUSE 13.1 kernel 3.11 and H110M-A/M.2 passed with Ubuntu 15.10 kernel 4.2 could be the fact that they have different network chips. As [Temüjin pointed out]("https://ubuntuforums.org/showthread.php?t=2344216&p=13574781#post13574781") the Intel® I219V chipset did not work with the kernel 3.3 > I tried using the latest version 3.3.4 of e1000e, but the error was the same: "The NVM Checksum Is Not Valid."

There are other differences between the motherboards that you may be interested in such as the H110M-A having ..... Supports Intel® InTru™ 3D, Quick Sync Video, Clear Video HD Technology, Insider™. I don't care about that as I have a GPU

> This page has specifications for the Intel 530 graphics [https://communities.intel.com/extern...eet-vol-1.html](https://communities.intel.com/extern...eet-vol-1.html)

note sections 

2.5.6 Multiple Display Configurations (Dual Channel DDR)
2.5.7 Multiple Display Configurations (Single Channel DDR)

---

### Post by sed_faster on 2017-01-02
Humm, this means in my case the best option is buy H110M-A/M.2? At least this version has support to ubuntu 15.10, I never and not intend use OpenSuse (nothing against OpenSuse :)
I found this video: [https://www.youtube.com/watch?v=MT-Z30Dr2fM](https://www.youtube.com/watch?v=MT-Z30Dr2fM) and this article: [https://mjg59.dreamwidth.org/41713.html](https://mjg59.dreamwidth.org/41713.html)

I am real freak out about this topic :( Because I feel totally lost about this subject. And my English level not the best! But let's go!

About displays I think if the board has three ports: hdmi, vga and dvi, it is supposed the board can connect all of them! My afraid is if the linux support the drives of this SkyLake GPU and this will run on good condition with two displays.

Note: Maybe I need read this book: [http://www.dummies.com/store/product/Build-Your-Own-PC-Do-It-Yourself-For-Dummies.productCd-0470196114,navId-322449.html](http://www.dummies.com/store/product/Build-Your-Own-PC-Do-It-Yourself-For-Dummies.productCd-0470196114,navId-322449.html) first of all I buy or try to build the computer to linux :)

---

### Post by sully101 on 2017-01-02
I have just ordered one :p. For best results install 2 sticks of memory at the highest speed the board supports as the GPU shares that memory. What resolution are your monitors ?

---

### Post by sed_faster on 2017-01-02
Nice, Plese give me a review about this board with ubuntu or lubuntu. 
Where do you buy board? online or physical shop?
I am think use 8GB DDR4 Kingston CL15 2133Mhz, on only one sticks. But why is it better use 2 sticks that one?

---

### Post by sully101 on 2017-01-02
In dual channel mode the memory will operate at twice the speed. In single channel it will operate at single speed and the Intel 530 GPU will be slower also.

Here's a video of it in action [https://www.youtube.com/watch?v=g2ljwgCw0Vs](https://www.youtube.com/watch?v=g2ljwgCw0Vs)

What do you want to use the computer for?

---

### Post by sed_faster on 2017-01-02
I intend use the computer to use with dual boot with windows 7 and Lubuntu (Or in the future with another distribution). 
On windows 7 I intend run autocad, eplan, photoshop, office 2010 and another proprietary software. On Lubuntu I intend run to developer web (html5, js, C, shellscript, etc) and do all stuff common on pc.
Basically I need windows 7 to run proprietary software. Because I love Linux and I won't change my SO :)

My displays are:
HDMI 1920x1080 VE228H Asus:[https://www.asus.com/Monitors/VE228H/](https://www.asus.com/Monitors/VE228H/)
Dell 17", through 1024x768

Where do you bought your motherboard?

---

### Post by sully101 on 2017-01-02
As you intend to rely on the on board gpu I would recommend getting two 4Gb sticks of ram as a matched pair. The cost should be the same, but the performance will be almost double when doing gpu tasks. If you already have 1x8Gb stick, then try it.

I am not familiar with eplan.
Autocad will probably see an improvement from using two sticks if you model in 3d
database applications will probably improve with dual channel ( mysql etc )
video encoding will probably improve with dual channel ( handbrake ffmpeg etc )
virtual machines will probably improve with dual channel ( vmware etc )
games will improve with dual channel :)

If you plan to upgrade your monitors to a higher resolution or add more then get two 4 Gb sticks
I think it is important to note that the ram is exactly the same but the motherboard uses it better when two sticks are installed.
There may be compatibility issues if you plan on upgrading later to 2x8Gb ram and they are not "matched"

It is important to realize that there are a lot of people will say that there is little benefit in installing memory in dual channel. They are correct when we look at gaming benchmarks that have a pcie gpu, but the difference here is that you are using the on board gpu and that gpu is sharing the system memory. It all depends on your upgrade plan and use case.

Will it work with 1x8Gb ram = yes
Will it work better with 2x4Gb ram = yes
How much better = I don't know. ( your monitor resolutions are quite low so you may see no real benefit )
Also note that opensuse is now at kernel 4.2 so the intel network chipset probably works now with opensuse.

I hope all this translates well. I'll post back here when I get it up and running. I will be installing mint 18.1, mythtv and steam. I could try a live usb stick if you have a particular distribution in mind.

---

### Post by sully101 on 2017-01-02
> I don't will need this option, the m.2 ssd, for this I will buy this version ([https://www.asus.com/Motherboards/H110M-A-D3/](https://www.asus.com/Motherboards/H110M-A-D3/))

That is a ddr3 version :( if you buy that you will need ddr3 ram not ddr4

---

### Post by sed_faster on 2017-01-02
> **sully101 said:**
> That is a ddr3 version :( if you buy that you will need ddr3 ram not ddr4

Hey, the ddr4 ram it was to version A/M.2
But maybe I will buy this version. Because the ddr4 it is more better of the ddr3 and I will get the more recently version!

---

### Post by sed_faster on 2017-01-02
> **sully101 said:**
> As you intend to rely on the on board gpu I would recommend getting two 4Gb sticks of ram as a matched pair. The cost should be the same, but the performance will be almost double when doing gpu tasks. If you already have 1x8Gb stick, then try it.

I am not familiar with eplan.
Autocad will probably see an improvement from using two sticks if you model in 3d
database applications will probably improve with dual channel ( mysql etc )
video encoding will probably improve with dual channel ( handbrake ffmpeg etc )
virtual machines will probably improve with dual channel ( vmware etc )
games will improve with dual channel :)

If you plan to upgrade your monitors to a higher resolution or add more then get two 4 Gb sticks
I think it is important to note that the ram is exactly the same but the motherboard uses it better when two sticks are installed.
There may be compatibility issues if you plan on upgrading later to 2x8Gb ram and they are not "matched"

It is important to realize that there are a lot of people will say that there is little benefit in installing memory in dual channel. They are correct when we look at gaming benchmarks that have a pcie gpu, but the difference here is that you are using the on board gpu and that gpu is sharing the system memory. It all depends on your upgrade plan and use case.

Will it work with 1x8Gb ram = yes
Will it work better with 2x4Gb ram = yes
How much better = I don't know. ( your monitor resolutions are quite low so you may see no real benefit )
Also note that opensuse is now at kernel 4.2 so the intel network chipset probably works now with opensuse.

I hope all this translates well. I'll post back here when I get it up and running. I will be installing mint 18.1, mythtv and steam. I could try a live usb stick if you have a particular distribution in mind.

Excellent report :) Thanks buddy!
In general I thinks which this setup will be good to my requires. Ok, maybe I will spend a little time with games on Windows :) (maybe the assassins creed :) hehe
But I won't spend much money with this setup! The main goal it is work, and the work I velocity, environment multi tasks and lightness. Because I like Lubuntu, on empty system, without software run, this distro spend 280 mb - this is awesome!

Remember me, but which version of the motherboard Asus H110M you bought?

---

### Post by sully101 on 2017-01-02
I have bought 
ASUS H110M-A/M.2
Intel Core i3 6100
CORSAIR 8GB (2x4GB)
WD Green 120GB M.2

I already have fractal design define mini c, 2Tb HD, gtx 660ti, 500w psu. I hope the m.2 ssd works but if it doesnt my son will find a use for it.

---

### Post by sed_faster on 2017-01-07
> **sully101 said:**
> I have bought 
ASUS H110M-A/M.2
Intel Core i3 6100
CORSAIR 8GB (2x4GB)
WD Green 120GB M.2

I already have fractal design define mini c, 2Tb HD, gtx 660ti, 500w psu. I hope the m.2 ssd works but if it doesnt my son will find a use for it.

Hooo, Why did you choose this CPU? I think which the best solution is i5 or i7 with this motherboard!
I never had experience with disk through M.2 connection. Between ssh, through obvious sata :) or connection M.2 which of them is better? Make up for the trade?

Did you tested this motherboard with Linux? Which distribution did you choose? And what experience did you have?

thanks

---

### Post by jphip on 2017-01-14
> **sully101 said:**
> I have bought ASUS H110M-A/M.2Does integrated network card I219V work without problems?

---

### Post by sully101 on 2017-01-15
The network adapter seems to work well. no extra configuration needed. Tested with linux mint 18.1 kernel 4.4

---

### Post by sully101 on 2017-01-15
The short answer.

Dual Display support: No

Intel network adapter: Yes

I tried getting the two displays to work with no luck in kernel 4.4 so then installed kernel 4.8. They seemed to work once I added a mode to my tv which was connected through the VGA, The other monitor was connected to HDMI. ```
xrandr --addmode DP1 1920x1080
```. Everything seemed to work ok sometimes but I would get random lockups/screen corruption and would have to [ctrl]+[alt]+[back space] to get to the login screen.

dmesg.txt
```
.........
[    1.113718] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[    1.184907] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 70:8b:cd:53:fd:4b
[    1.184908] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.185019] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    1.185080] ata4: SATA link down (SStatus 4 SControl 300)
[    1.185138] ata3: SATA link down (SStatus 4 SControl 300)
[    1.185161] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.185178] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[COLOR="#FF0000"][    1.185333] [drm:i915_gem_init_stolen [i915]] *ERROR* conflict detected with stolen region: [0x88000000 - 0xc8000000][/COLOR]
[    1.185335] [drm] Memory usable by graphics device = 4096M
[    1.185337] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[    1.185337] fb: switching to inteldrmfb from EFI VGA
[    1.185355] Console: switching to colour dummy device 80x25
[    1.185404] [drm] Replacing VGA console driver
[    1.185567] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[    1.186103] ata2.00: ATA-8: WDC WD1600AAJS-75B4A0, 01.03A01, max UDMA/133
[    1.186104] ata2.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.187166] ata2.00: configured for UDMA/133
[    1.189236] ata1.00: ATA-9: WDC WDS120G1G0B-00RC30, Z3311000, max UDMA/133
[    1.189237] ata1.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.191533] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.191534] [drm] Driver supports precise vblank timestamp query.
[    1.197440] [drm] Finished loading i915/skl_dmc_ver1_26.bin (v1.26)
[    1.197921] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.198696] ata1.00: configured for UDMA/133
[    1.198813] scsi 0:0:0:0: Direct-Access     ATA      WDC WDS120G1G0B- 1000 PQ: 0 ANSI: 5
[    1.206980] [drm] GuC firmware load skipped
[    1.249227] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.249235] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[    1.249350] sd 0:0:0:0: [sda] Write Protect is off
[    1.249351] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.249389] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.250568] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-7 3A01 PQ: 0 ANSI: 5
[    1.250786]  sda: sda1 sda2 sda3
[    1.251057] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.252773] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.252932] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.253039] [drm] Initialized i915 1.6.0 20160711 for 0000:00:02.0 on minor 0
[    1.255080] random: fast init done
[    1.256572] usb 1-7: New USB device found, idVendor=413c, idProduct=2105
[    1.256578] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.256578] usb 1-7: Product: Dell USB Keyboard
[    1.256579] usb 1-7: Manufacturer: Dell
[    1.274369] usbcore: registered new interface driver usbhid
[    1.274373] usbhid: USB HID core driver
[    1.275462] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:413C:2105.0001/input/input7
[    1.290330] fbcon: inteldrmfb (fb0) is primary device
[    1.290365] Console: switching to colour frame buffer device 128x48
[    1.290373] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.293343] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.293356] sd 1:0:0:0: [sdb] 312500000 512-byte logical blocks: (160 GB/149 GiB)
[    1.293465] sd 1:0:0:0: [sdb] Write Protect is off
[    1.293466] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.293494] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.333338] hid-generic 0003:413C:2105.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:14.0-7/input0
[    1.345656]  sdb: sdb1
[    1.346013] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.633179] tsc: Refined TSC clocksource calibration: 3696.004 MHz
[    1.633185] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x6a8d2d9b023, max_idle_ns: 881590978302 ns
[COLOR="#FF0000"][    1.640767] ------------[ cut here ]------------
[    1.640786] WARNING: CPU: 2 PID: 267 at /build/linux-hwe-edge-V64a3L/linux-hwe-edge-4.8.0/drivers/gpu/drm/i915/intel_display.c:4434 skylake_pfit_enable+0x14a/0x160 [i915]
[    1.640786] WARN_ON(crtc->config->scaler_state.scaler_id < 0)
[    1.640787] Modules linked in:
[    1.640787]  dm_mirror dm_region_hash dm_log hid_generic usbhid mxm_wmi i915 i2c_algo_bit drm_kms_helper psmouse e1000e syscopyarea sysfillrect sysimgblt fb_sys_fops drm ptp ahci pps_core libahci wmi video i2c_hid pinctrl_sunrisepoint hid pinctrl_intel fjes
[    1.640800] CPU: 2 PID: 267 Comm: plymouthd Not tainted 4.8.0-34-generic #36~16.04.1-Ubuntu
[    1.640802] Hardware name: System manufacturer System Product Name/H110M-A/M.2, BIOS 1801 05/17/2016
[    1.640804]  0000000000000286 00000000174921e2 ffffa0cd65bd7910 ffffffffb4a2d7b3
[    1.640806]  ffffa0cd65bd7960 0000000000000000 ffffa0cd65bd7950 ffffffffb468313b
[    1.640807]  00001152174921e2 ffffa0cd64f0e000 ffffa0cd65580000 0000000000000001
[    1.640809] Call Trace:
[    1.640811]  [<ffffffffb4a2d7b3>] dump_stack+0x63/0x90
[    1.640813]  [<ffffffffb468313b>] __warn+0xcb/0xf0
[    1.640814]  [<ffffffffb46831bf>] warn_slowpath_fmt+0x5f/0x80
[    1.640827]  [<ffffffffc0464b6a>] skylake_pfit_enable+0x14a/0x160 [i915]
[    1.640839]  [<ffffffffc047b644>] haswell_crtc_enable+0x314/0x850 [i915]
[    1.640851]  [<ffffffffc0476d36>] intel_update_crtc+0x56/0xf0 [i915]
[    1.640862]  [<ffffffffc0476f9e>] skl_update_crtcs+0x14e/0x190 [i915]
[    1.640872]  [<ffffffffc0477582>] intel_atomic_commit_tail+0x372/0x10a0 [i915]
[    1.640884]  [<ffffffffc04804e9>] ? intel_prepare_plane_fb+0x149/0x280 [i915]
[    1.640894]  [<ffffffffc04786f0>] intel_atomic_commit+0x440/0x570 [i915]
[    1.640904]  [<ffffffffc02c86c7>] ? drm_atomic_check_only+0x187/0x610 [drm]
[    1.640911]  [<ffffffffc02c91e7>] ? drm_atomic_set_crtc_for_connector+0x97/0x100 [drm]
[    1.640918]  [<ffffffffc02c8b87>] drm_atomic_commit+0x37/0x60 [drm]
[    1.640922]  [<ffffffffc03c0dc1>] drm_atomic_helper_set_config+0x81/0xc0 [drm_kms_helper]
[    1.640929]  [<ffffffffc02b6e45>] drm_mode_set_config_internal+0x65/0x110 [drm]
[    1.640935]  [<ffffffffc02bbce9>] drm_mode_setcrtc+0x469/0x560 [drm]
[    1.640940]  [<ffffffffc02add67>] drm_ioctl+0x1e7/0x4c0 [drm]
[    1.640946]  [<ffffffffc02bb880>] ? drm_mode_setplane+0x1c0/0x1c0 [drm]
[    1.640948]  [<ffffffffb48325b0>] ? new_sync_read+0xd0/0x120
[    1.640949]  [<ffffffffb4847861>] do_vfs_ioctl+0xa1/0x5f0
[    1.640951]  [<ffffffffb4832e03>] ? vfs_read+0x123/0x140
[    1.640951]  [<ffffffffb4847e29>] SyS_ioctl+0x79/0x90
[    1.640953]  [<ffffffffb4e96576>] entry_SYSCALL_64_fastpath+0x1e/0xa8
[    1.640954] ---[ end trace 060d61fac4e4d2ce ]---
[    1.640966] [drm:skylake_pfit_enable [i915]] *ERROR* Requesting pfit without getting a scaler first
[    1.664338] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in output_types (expected 0x00000400, found 0x00000080)
[    1.664353] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in pch_pfit.enabled (expected 1, found 0)
[    1.664365] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in pch_pfit.size (expected 0x04000300, found 0x00000000)
[    1.664377] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in base.adjusted_mode.crtc_clock (expected 270000, found 64999)
[    1.664377] ------------[ cut here ]------------
[    1.664390] WARNING: CPU: 2 PID: 267 at /build/linux-hwe-edge-V64a3L/linux-hwe-edge-4.8.0/drivers/gpu/drm/i915/intel_display.c:13158 intel_atomic_commit_tail+0xdaa/0x10a0 [i915]
[    1.664390] pipe state doesn't match!
[    1.664391] Modules linked in: raid6_pq(+) dm_mirror dm_region_hash dm_log hid_generic usbhid mxm_wmi i915 i2c_algo_bit drm_kms_helper psmouse e1000e syscopyarea sysfillrect sysimgblt fb_sys_fops drm ptp ahci pps_core libahci wmi video i2c_hid pinctrl_sunrisepoint hid pinctrl_intel fjes
[    1.664400] CPU: 2 PID: 267 Comm: plymouthd Tainted: G        W       4.8.0-34-generic #36~16.04.1-Ubuntu
[    1.664401] Hardware name: System manufacturer System Product Name/H110M-A/M.2, BIOS 1801 05/17/2016
[    1.664401]  0000000000000286 00000000174921e2 ffffa0cd65bd7a68 ffffffffb4a2d7b3
[    1.664403]  ffffa0cd65bd7ab8 0000000000000000 ffffa0cd65bd7aa8 ffffffffb468313b
[    1.664404]  00003366c046ca4f ffffa0cd64f0e000 ffffa0cd6dd1a800 ffffa0cd6dc90800
[    1.664405] Call Trace:
[    1.664408]  [<ffffffffb4a2d7b3>] dump_stack+0x63/0x90
[    1.664410]  [<ffffffffb468313b>] __warn+0xcb/0xf0
[    1.664411]  [<ffffffffb46831bf>] warn_slowpath_fmt+0x5f/0x80
[    1.664424]  [<ffffffffc0477fba>] intel_atomic_commit_tail+0xdaa/0x10a0 [i915]
[    1.664425]  [<ffffffffb46c74d0>] ? wake_atomic_t_function+0x60/0x60
[    1.664437]  [<ffffffffc04786f0>] intel_atomic_commit+0x440/0x570 [i915]
[    1.664447]  [<ffffffffc02c86c7>] ? drm_atomic_check_only+0x187/0x610 [drm]
[    1.664455]  [<ffffffffc02c91e7>] ? drm_atomic_set_crtc_for_connector+0x97/0x100 [drm]
[    1.664462]  [<ffffffffc02c8b87>] drm_atomic_commit+0x37/0x60 [drm]
[    1.664467]  [<ffffffffc03c0dc1>] drm_atomic_helper_set_config+0x81/0xc0 [drm_kms_helper]
[    1.664474]  [<ffffffffc02b6e45>] drm_mode_set_config_internal+0x65/0x110 [drm]
[    1.664480]  [<ffffffffc02bbce9>] drm_mode_setcrtc+0x469/0x560 [drm]
[    1.664486]  [<ffffffffc02add67>] drm_ioctl+0x1e7/0x4c0 [drm]
[    1.664492]  [<ffffffffc02bb880>] ? drm_mode_setplane+0x1c0/0x1c0 [drm]
[    1.664494]  [<ffffffffb48325b0>] ? new_sync_read+0xd0/0x120
[    1.664495]  [<ffffffffb4847861>] do_vfs_ioctl+0xa1/0x5f0
[    1.664496]  [<ffffffffb4832e03>] ? vfs_read+0x123/0x140
[    1.664497]  [<ffffffffb4847e29>] SyS_ioctl+0x79/0x90
[    1.664499]  [<ffffffffb4e96576>] entry_SYSCALL_64_fastpath+0x1e/0xa8
[    1.664500] ---[ end trace 060d61fac4e4d2cf ]---[/COLOR]
[    1.721145] raid6: sse2x1   gen()  9451 MB/s
[    1.789145] raid6: sse2x1   xor()  6664 MB/s
..........
[    5.368787] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[    5.368791] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO
[    5.368876] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
..........
```

sysinfo.txt
```
System:    Host: mythtv Kernel: 4.8.0-34-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.2.7 (Gtk 3.18.9-1ubuntu3.1) dm: mdm Distro: Linux Mint 18.1 Serena
Machine:   Mobo: ASUSTeK model: H110M-A/M.2 v: Rev X.0x
           Bios: American Megatrends v: 1801 date: 05/17/2016
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 14784
           clock speeds: min/max: 800/3700 MHz 1: 799 MHz 2: 901 MHz 3: 3599 MHz 4: 800 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics bus-ID: 00:02.0 chip-ID: 8086:1912
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.00hz, 1024x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3 chip-ID: 8086:a170
           Sound: Advanced Linux Sound Architecture v: k4.8.0-34-generic
Network:   Card: Intel Ethernet Connection (2) I219-V
           driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6 chip-ID: 8086:15b8
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 280.0GB (5.1% used)
           ID-1: /dev/sda model: WDC_WDS120G1G0B size: 120.0GB serial: 164595403184
           ID-2: /dev/sdb model: WDC_WD1600AAJS size: 160.0GB serial: WD-WMAT21860726
Partition: ID-1: / size: 103G used: 6.7G (7%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 7.44GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Repos:     Active apt sources in file: /etc/apt/sources.list.d/official-package-repositories.list
           deb http: //mirror.aarnet.edu.au/pub/linuxmint-packages serena main upstream import backport
           deb http: //nz.archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
           deb http: //nz.archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
           deb http: //nz.archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
           deb http: //security.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
           deb http: //archive.canonical.com/ubuntu/ xenial partner
Info:      Processes: 207 Uptime: 1 min Memory: 433.1/6904.2MB
           Init: systemd v: 229 runlevel: 5 default: 2 Gcc sys: 5.4.0
Client: Unknown python2.7 client inxi: 2.2.35
```

---

### Post by sully101 on 2017-01-15
The short answer.

Dual Display support: No

Intel network adapter: Yes

I tried getting the two displays to work with no luck in kernel 4.4 so then installed kernel 4.8. They seemed to work once I added a mode to my tv which was connected through the VGA, The other monitor was connected to HDMI. ```
xrandr --addmode DP1 1920x1080
```. Everything seemed to work ok sometimes but I would get random lockups/screen corruption and would have to [ctrl]+[alt]+[back space] to get to the login screen.

dmesg.txt
```
.........
[    1.113718] e1000e 0000:00:1f.6 0000:00:1f.6 (uninitialized): registered PHC clock
[    1.184907] e1000e 0000:00:1f.6 eth0: (PCI Express:2.5GT/s:Width x1) 70:8b:cd:53:fd:4b
[    1.184908] e1000e 0000:00:1f.6 eth0: Intel(R) PRO/1000 Network Connection
[    1.185019] e1000e 0000:00:1f.6 eth0: MAC: 12, PHY: 12, PBA No: FFFFFF-0FF
[    1.185080] ata4: SATA link down (SStatus 4 SControl 300)
[    1.185138] ata3: SATA link down (SStatus 4 SControl 300)
[    1.185161] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.185178] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[COLOR="#FF0000"][    1.185333] [drm:i915_gem_init_stolen [i915]] *ERROR* conflict detected with stolen region: [0x88000000 - 0xc8000000][/COLOR]
[    1.185335] [drm] Memory usable by graphics device = 4096M
[    1.185337] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[    1.185337] fb: switching to inteldrmfb from EFI VGA
[    1.185355] Console: switching to colour dummy device 80x25
[    1.185404] [drm] Replacing VGA console driver
[    1.185567] e1000e 0000:00:1f.6 enp0s31f6: renamed from eth0
[    1.186103] ata2.00: ATA-8: WDC WD1600AAJS-75B4A0, 01.03A01, max UDMA/133
[    1.186104] ata2.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.187166] ata2.00: configured for UDMA/133
[    1.189236] ata1.00: ATA-9: WDC WDS120G1G0B-00RC30, Z3311000, max UDMA/133
[    1.189237] ata1.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.191533] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.191534] [drm] Driver supports precise vblank timestamp query.
[    1.197440] [drm] Finished loading i915/skl_dmc_ver1_26.bin (v1.26)
[    1.197921] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.198696] ata1.00: configured for UDMA/133
[    1.198813] scsi 0:0:0:0: Direct-Access     ATA      WDC WDS120G1G0B- 1000 PQ: 0 ANSI: 5
[    1.206980] [drm] GuC firmware load skipped
[    1.249227] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.249235] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[    1.249350] sd 0:0:0:0: [sda] Write Protect is off
[    1.249351] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.249389] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.250568] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-7 3A01 PQ: 0 ANSI: 5
[    1.250786]  sda: sda1 sda2 sda3
[    1.251057] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.252773] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.252932] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    1.253039] [drm] Initialized i915 1.6.0 20160711 for 0000:00:02.0 on minor 0
[    1.255080] random: fast init done
[    1.256572] usb 1-7: New USB device found, idVendor=413c, idProduct=2105
[    1.256578] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.256578] usb 1-7: Product: Dell USB Keyboard
[    1.256579] usb 1-7: Manufacturer: Dell
[    1.274369] usbcore: registered new interface driver usbhid
[    1.274373] usbhid: USB HID core driver
[    1.275462] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/0003:413C:2105.0001/input/input7
[    1.290330] fbcon: inteldrmfb (fb0) is primary device
[    1.290365] Console: switching to colour frame buffer device 128x48
[    1.290373] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.293343] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.293356] sd 1:0:0:0: [sdb] 312500000 512-byte logical blocks: (160 GB/149 GiB)
[    1.293465] sd 1:0:0:0: [sdb] Write Protect is off
[    1.293466] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.293494] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.333338] hid-generic 0003:413C:2105.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:14.0-7/input0
[    1.345656]  sdb: sdb1
[    1.346013] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.633179] tsc: Refined TSC clocksource calibration: 3696.004 MHz
[    1.633185] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x6a8d2d9b023, max_idle_ns: 881590978302 ns
[COLOR="#FF0000"][    1.640767] ------------[ cut here ]------------
[    1.640786] WARNING: CPU: 2 PID: 267 at /build/linux-hwe-edge-V64a3L/linux-hwe-edge-4.8.0/drivers/gpu/drm/i915/intel_display.c:4434 skylake_pfit_enable+0x14a/0x160 [i915]
[    1.640786] WARN_ON(crtc->config->scaler_state.scaler_id < 0)
[    1.640787] Modules linked in:
[    1.640787]  dm_mirror dm_region_hash dm_log hid_generic usbhid mxm_wmi i915 i2c_algo_bit drm_kms_helper psmouse e1000e syscopyarea sysfillrect sysimgblt fb_sys_fops drm ptp ahci pps_core libahci wmi video i2c_hid pinctrl_sunrisepoint hid pinctrl_intel fjes
[    1.640800] CPU: 2 PID: 267 Comm: plymouthd Not tainted 4.8.0-34-generic #36~16.04.1-Ubuntu
[    1.640802] Hardware name: System manufacturer System Product Name/H110M-A/M.2, BIOS 1801 05/17/2016
[    1.640804]  0000000000000286 00000000174921e2 ffffa0cd65bd7910 ffffffffb4a2d7b3
[    1.640806]  ffffa0cd65bd7960 0000000000000000 ffffa0cd65bd7950 ffffffffb468313b
[    1.640807]  00001152174921e2 ffffa0cd64f0e000 ffffa0cd65580000 0000000000000001
[    1.640809] Call Trace:
[    1.640811]  [<ffffffffb4a2d7b3>] dump_stack+0x63/0x90
[    1.640813]  [<ffffffffb468313b>] __warn+0xcb/0xf0
[    1.640814]  [<ffffffffb46831bf>] warn_slowpath_fmt+0x5f/0x80
[    1.640827]  [<ffffffffc0464b6a>] skylake_pfit_enable+0x14a/0x160 [i915]
[    1.640839]  [<ffffffffc047b644>] haswell_crtc_enable+0x314/0x850 [i915]
[    1.640851]  [<ffffffffc0476d36>] intel_update_crtc+0x56/0xf0 [i915]
[    1.640862]  [<ffffffffc0476f9e>] skl_update_crtcs+0x14e/0x190 [i915]
[    1.640872]  [<ffffffffc0477582>] intel_atomic_commit_tail+0x372/0x10a0 [i915]
[    1.640884]  [<ffffffffc04804e9>] ? intel_prepare_plane_fb+0x149/0x280 [i915]
[    1.640894]  [<ffffffffc04786f0>] intel_atomic_commit+0x440/0x570 [i915]
[    1.640904]  [<ffffffffc02c86c7>] ? drm_atomic_check_only+0x187/0x610 [drm]
[    1.640911]  [<ffffffffc02c91e7>] ? drm_atomic_set_crtc_for_connector+0x97/0x100 [drm]
[    1.640918]  [<ffffffffc02c8b87>] drm_atomic_commit+0x37/0x60 [drm]
[    1.640922]  [<ffffffffc03c0dc1>] drm_atomic_helper_set_config+0x81/0xc0 [drm_kms_helper]
[    1.640929]  [<ffffffffc02b6e45>] drm_mode_set_config_internal+0x65/0x110 [drm]
[    1.640935]  [<ffffffffc02bbce9>] drm_mode_setcrtc+0x469/0x560 [drm]
[    1.640940]  [<ffffffffc02add67>] drm_ioctl+0x1e7/0x4c0 [drm]
[    1.640946]  [<ffffffffc02bb880>] ? drm_mode_setplane+0x1c0/0x1c0 [drm]
[    1.640948]  [<ffffffffb48325b0>] ? new_sync_read+0xd0/0x120
[    1.640949]  [<ffffffffb4847861>] do_vfs_ioctl+0xa1/0x5f0
[    1.640951]  [<ffffffffb4832e03>] ? vfs_read+0x123/0x140
[    1.640951]  [<ffffffffb4847e29>] SyS_ioctl+0x79/0x90
[    1.640953]  [<ffffffffb4e96576>] entry_SYSCALL_64_fastpath+0x1e/0xa8
[    1.640954] ---[ end trace 060d61fac4e4d2ce ]---
[    1.640966] [drm:skylake_pfit_enable [i915]] *ERROR* Requesting pfit without getting a scaler first
[    1.664338] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in output_types (expected 0x00000400, found 0x00000080)
[    1.664353] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in pch_pfit.enabled (expected 1, found 0)
[    1.664365] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in pch_pfit.size (expected 0x04000300, found 0x00000000)
[    1.664377] [drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in base.adjusted_mode.crtc_clock (expected 270000, found 64999)
[    1.664377] ------------[ cut here ]------------
[    1.664390] WARNING: CPU: 2 PID: 267 at /build/linux-hwe-edge-V64a3L/linux-hwe-edge-4.8.0/drivers/gpu/drm/i915/intel_display.c:13158 intel_atomic_commit_tail+0xdaa/0x10a0 [i915]
[    1.664390] pipe state doesn't match!
[    1.664391] Modules linked in: raid6_pq(+) dm_mirror dm_region_hash dm_log hid_generic usbhid mxm_wmi i915 i2c_algo_bit drm_kms_helper psmouse e1000e syscopyarea sysfillrect sysimgblt fb_sys_fops drm ptp ahci pps_core libahci wmi video i2c_hid pinctrl_sunrisepoint hid pinctrl_intel fjes
[    1.664400] CPU: 2 PID: 267 Comm: plymouthd Tainted: G        W       4.8.0-34-generic #36~16.04.1-Ubuntu
[    1.664401] Hardware name: System manufacturer System Product Name/H110M-A/M.2, BIOS 1801 05/17/2016
[    1.664401]  0000000000000286 00000000174921e2 ffffa0cd65bd7a68 ffffffffb4a2d7b3
[    1.664403]  ffffa0cd65bd7ab8 0000000000000000 ffffa0cd65bd7aa8 ffffffffb468313b
[    1.664404]  00003366c046ca4f ffffa0cd64f0e000 ffffa0cd6dd1a800 ffffa0cd6dc90800
[    1.664405] Call Trace:
[    1.664408]  [<ffffffffb4a2d7b3>] dump_stack+0x63/0x90
[    1.664410]  [<ffffffffb468313b>] __warn+0xcb/0xf0
[    1.664411]  [<ffffffffb46831bf>] warn_slowpath_fmt+0x5f/0x80
[    1.664424]  [<ffffffffc0477fba>] intel_atomic_commit_tail+0xdaa/0x10a0 [i915]
[    1.664425]  [<ffffffffb46c74d0>] ? wake_atomic_t_function+0x60/0x60
[    1.664437]  [<ffffffffc04786f0>] intel_atomic_commit+0x440/0x570 [i915]
[    1.664447]  [<ffffffffc02c86c7>] ? drm_atomic_check_only+0x187/0x610 [drm]
[    1.664455]  [<ffffffffc02c91e7>] ? drm_atomic_set_crtc_for_connector+0x97/0x100 [drm]
[    1.664462]  [<ffffffffc02c8b87>] drm_atomic_commit+0x37/0x60 [drm]
[    1.664467]  [<ffffffffc03c0dc1>] drm_atomic_helper_set_config+0x81/0xc0 [drm_kms_helper]
[    1.664474]  [<ffffffffc02b6e45>] drm_mode_set_config_internal+0x65/0x110 [drm]
[    1.664480]  [<ffffffffc02bbce9>] drm_mode_setcrtc+0x469/0x560 [drm]
[    1.664486]  [<ffffffffc02add67>] drm_ioctl+0x1e7/0x4c0 [drm]
[    1.664492]  [<ffffffffc02bb880>] ? drm_mode_setplane+0x1c0/0x1c0 [drm]
[    1.664494]  [<ffffffffb48325b0>] ? new_sync_read+0xd0/0x120
[    1.664495]  [<ffffffffb4847861>] do_vfs_ioctl+0xa1/0x5f0
[    1.664496]  [<ffffffffb4832e03>] ? vfs_read+0x123/0x140
[    1.664497]  [<ffffffffb4847e29>] SyS_ioctl+0x79/0x90
[    1.664499]  [<ffffffffb4e96576>] entry_SYSCALL_64_fastpath+0x1e/0xa8
[    1.664500] ---[ end trace 060d61fac4e4d2cf ]---[/COLOR]
[    1.721145] raid6: sse2x1   gen()  9451 MB/s
[    1.789145] raid6: sse2x1   xor()  6664 MB/s
..........
[    5.368787] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[    5.368791] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO
[    5.368876] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
..........
```

sysinfo.txt
```
System:    Host: mythtv Kernel: 4.8.0-34-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.2.7 (Gtk 3.18.9-1ubuntu3.1) dm: mdm Distro: Linux Mint 18.1 Serena
Machine:   Mobo: ASUSTeK model: H110M-A/M.2 v: Rev X.0x
           Bios: American Megatrends v: 1801 date: 05/17/2016
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 14784
           clock speeds: min/max: 800/3700 MHz 1: 799 MHz 2: 901 MHz 3: 3599 MHz 4: 800 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics bus-ID: 00:02.0 chip-ID: 8086:1912
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1024x768@60.00hz, 1024x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3 chip-ID: 8086:a170
           Sound: Advanced Linux Sound Architecture v: k4.8.0-34-generic
Network:   Card: Intel Ethernet Connection (2) I219-V
           driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6 chip-ID: 8086:15b8
           IF: enp0s31f6 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 280.0GB (5.1% used)
           ID-1: /dev/sda model: WDC_WDS120G1G0B size: 120.0GB serial: 164595403184
           ID-2: /dev/sdb model: WDC_WD1600AAJS size: 160.0GB serial: WD-WMAT21860726
Partition: ID-1: / size: 103G used: 6.7G (7%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 7.44GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      System: supported: N/A
           No RAID devices: /proc/mdstat, md_mod kernel module present
           Unused Devices: none
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: 0
Repos:     Active apt sources in file: /etc/apt/sources.list.d/official-package-repositories.list
           deb http: //mirror.aarnet.edu.au/pub/linuxmint-packages serena main upstream import backport
           deb http: //nz.archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
           deb http: //nz.archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
           deb http: //nz.archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
           deb http: //security.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
           deb http: //archive.canonical.com/ubuntu/ xenial partner
Info:      Processes: 207 Uptime: 1 min Memory: 433.1/6904.2MB
           Init: systemd v: 229 runlevel: 5 default: 2 Gcc sys: 5.4.0
Client: Unknown python2.7 client inxi: 2.2.35
```

---

### Post by sully101 on 2017-01-15
I have just noticed that the bios was not updated, so have updated to  "H110M-A/M.2 BIOS 2003" by selecting on line update in the BIOS. That with a ~/.config/monitors.xml as follows seems to have made everything much better
```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DP1">
      <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="HDMI1">
      </output>
      <output name="HDMI2">
          <vendor>SAM</vendor>
          <product>0x07d4</product>
          <serial>0x5a525a44</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>1920</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
  </configuration>
</monitors>
```

I havn't tried games or anything other than youtube videos

even with the updated BIOS dmesg still gives the errors same as above.

The latest BIOS  "H110M-A/M.2 BIOS 3016" may have additional benefits but I havn't tested it.

So my recommendation for this motherboard is to run the latest kernel you can with at least the version 2003 BIOS and configure the monitors.xml manually as the system-config seemed to be getting things scrambled.

---

