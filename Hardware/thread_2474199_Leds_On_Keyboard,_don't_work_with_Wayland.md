---
title: "Leds On Keyboard, don't work with Wayland"
date: 2022-04-23
forum: Hardware
---

### Post by patrikrufino on 2022-04-23
Hi everyone, I'm new here.

I have a small problem regarding my keyboard and its incompatibility with the Wayland graphics server.

I was used to using Xorg, and in the past with the command ```
xset led 3
```, I was able to turn on my leds.

I could even add the command **/usr/bin/ xset led 3,** on Ubuntu boot.

But now with the change from the graphic server to Wayland, I can't get the same result.

I would like to understand why this happens, and get a solution other than simply switching to Xorg.

After all, wayland seems to be the future.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290329&stc=1[/IMG]

---

### Post by Autodave on 2022-04-23
Some more info would be helpful: make and model of PC and make and model of keyboard please.

---

### Post by TheFu on 2022-04-23
Commands that begin with x, tend to be for x/windows, not wayland. They are different display servers, so expect they don't work the same and have all the same features.
Google found this from 2018: [https://askubuntu.com/questions/967373/wayland-equivalent-to-xset-led](https://askubuntu.com/questions/967373/wayland-equivalent-to-xset-led)
A fedora forum from 2022 had a similar solution under wayland.

---

### Post by patrikrufino on 2022-04-24
This solution works in parts.

When I press the CAPS LOCK key, the LEDs turn off, and when restarting, both the LEDs and the command stop working.

What happens is that the input input changes on every attempt.

Ex:

In a moment you are:
input8::scrolllock

After the command attempt it becomes:

input9::scrolllock

And it continues to rise with each new command.

And the keyboard response is just a blink.

---

### Post by patrikrufino on 2022-04-24
So when you say more info I'm not sure if that would be it.

This is the output of the lshw command.

I apologize if it wasn't what you expected. I'm new to this forum stuff =)
```

acer-ubuntu
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 12GiB
     *-cpu
          product: Intel(R) Core(TM) i3-6006U CPU @ 2.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.78.3
          size: 1396MHz
          capacity: 2GHz
          width: 64 bits
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht  tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon  pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni  pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr  pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave  avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb  invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept  vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx  rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves  dtherm arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear  flush_l1d cpufreq
          configuration: microcode=234
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Skylake GT2 [HD Graphics 520]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             logical name: /dev/fb0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom fb
             configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
             resources: irq:130 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:4000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:127 memory:b1310000-b131ffff
        *-generic:0
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:b132a000-b132afff
        *-generic:1
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #0
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:b132b000-b132bfff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:129 memory:b132c000-b132cfff
        *-sata
             description: SATA controller
             product: Sunrise Point-LP SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: sata ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
              resources: irq:126 memory:b1328000-b1329fff memory:b132f000-b132f0ff  ioport:4080(size=8) ioport:4088(size=4) ioport:4060(size=32)  memory:b132d000-b132d7ff
        *-pci:0
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:5000(size=4096) memory:90100000-902fffff ioport:90300000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 ioport:3000(size=4096) memory:b1200000-b12fffff
           *-generic
                description: MMC Host
                product: RTL8411B PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: mmc0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom
                configuration: driver=rtsx_pci latency=0
                resources: irq:125 memory:b1205000-b1205fff memory:b1210000-b121ffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0.1
                bus info: pci@0000:02:00.1
                logical name: enp2s0f1
                version: 12
                serial: 98:29:a6:e2:28:23
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=5.15.0-25-generic firmware=rtl8411-2_0.0.1 07/08/13  latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 ioport:3000(size=256) memory:b1204000-b1204fff memory:b1200000-b1203fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:b1000000-b11fffff
           *-network
                description: Wireless interface
                product: QCA9377 802.11ac Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 31
                serial: 5c:c9:d3:ba:80:5e
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                 configuration: broadcast=yes driver=ath10k_pci  driverversion=5.15.0-25-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1  ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:131 memory:b1000000-b11fffff
        *-isa
             description: ISA bridge
             product: Sunrise Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
           *-pnp00:00
                product: PnP device PNP0c02
                physical id: 0
                capabilities: pnp
                configuration: driver=system
           *-pnp00:01
                product: PnP device PNP0c02
                physical id: 1
                capabilities: pnp
                configuration: driver=system
           *-pnp00:02
                product: PnP device PNP0c02
                physical id: 2
                capabilities: pnp
                configuration: driver=system
           *-pnp00:03
                product: PnP device PNP0b00
                physical id: 3
                capabilities: pnp
                configuration: driver=rtc_cmos
           *-pnp00:04
                product: PnP device INT3f0d
                physical id: 4
                capabilities: pnp
                configuration: driver=system
           *-pnp00:05
                product: PnP device PNP0303
                physical id: 5
                capabilities: pnp
                configuration: driver=i8042 kbd
           *-pnp00:06
                product: PnP device PNP0c02
                physical id: 6
                capabilities: pnp
                configuration: driver=system
           *-pnp00:07
                product: PnP device PNP0c02
                physical id: 7
                capabilities: pnp
                configuration: driver=system
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:b1324000-b1327fff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             logical name: card0
             logical name: /dev/snd/controlC0
             logical name: /dev/snd/hwC0D0
             logical name: /dev/snd/hwC0D2
             logical name: /dev/snd/pcmC0D0c
             logical name: /dev/snd/pcmC0D0p
             logical name: /dev/snd/pcmC0D10p
             logical name: /dev/snd/pcmC0D3p
             logical name: /dev/snd/pcmC0D7p
             logical name: /dev/snd/pcmC0D8p
             logical name: /dev/snd/pcmC0D9p
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:132 memory:b1320000-b1323fff memory:b1300000-b130ffff
           *-input:0
                product: HDA Intel PCH Front Headphone
                physical id: 0
                logical name: input19
                logical name: /dev/input/event15
           *-input:1
                product: HDA Intel PCH HDMI/DP,pcm=3
                physical id: 1
                logical name: input20
                logical name: /dev/input/event16
           *-input:2
                product: HDA Intel PCH HDMI/DP,pcm=7
                physical id: 2
                logical name: input21
                logical name: /dev/input/event17
           *-input:3
                product: HDA Intel PCH HDMI/DP,pcm=8
                physical id: 3
                logical name: input22
                logical name: /dev/input/event18
           *-input:4
                product: HDA Intel PCH HDMI/DP,pcm=9
                physical id: 4
                logical name: input23
                logical name: /dev/input/event19
           *-input:5
                product: HDA Intel PCH HDMI/DP,pcm=10
                physical id: 5
                logical name: input24
                logical name: /dev/input/event20
        *-serial
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: driver=i801_smbus latency=0
             resources: irq:16 memory:b132e000-b132e0ff ioport:4040(size=32)
  *-input:0
       product: Power Button
       physical id: 1
       logical name: input0
       logical name: /dev/input/event0
       capabilities: platform
  *-input:1
       product: Sleep Button
       physical id: 2
       logical name: input1
       logical name: /dev/input/event1
       capabilities: platform
  *-input:2
       product: USB USB Keyboard System Control
       physical id: 3
       logical name: input10
       logical name: /dev/input/event9
       capabilities: usb
  *-input:3
       product: SIGMACHIP Usb Mouse
       physical id: 4
       logical name: input11
       logical name: /dev/input/event10
       logical name: /dev/input/mouse2
       capabilities: usb
  *-input:4
       product: Acer Wireless Radio Control
       physical id: 5
       logical name: input12
       logical name: /dev/input/event11
       capabilities: platform
  *-input:5
       product: SYNA7DB5:00 06CB:7DB7 Mouse
       physical id: 6
       logical name: input13
       logical name: /dev/input/event5
       logical name: /dev/input/mouse0
       capabilities: i2c
  *-input:6
       product: SYNA7DB5:00 06CB:7DB7 Touchpad
       physical id: 7
       logical name: input14
       logical name: /dev/input/event6
       logical name: /dev/input/mouse1
       capabilities: i2c
  *-input:7
       product: Acer WMI hotkeys
       physical id: 8
       logical name: input16
       logical name: /dev/input/event12
       capabilities: platform
  *-input:8
       product: VGA WebCam: VGA WebCam
       physical id: 9
       logical name: input17
       logical name: /dev/input/event13
       capabilities: usb
  *-input:9
       product: Video Bus
       physical id: a
       logical name: input18
       logical name: /dev/input/event14
       capabilities: platform
  *-input:10
       product: Lid Switch
       physical id: b
       logical name: input2
       logical name: /dev/input/event2
       capabilities: platform
  *-input:11
       product: Power Button
       physical id: c
       logical name: input3
       logical name: /dev/input/event3
       capabilities: platform
  *-input:12
       product: AT Translated Set 2 keyboard
       physical id: d
       logical name: input4
       logical name: /dev/input/event4
       logical name: input4::capslock
       logical name: input4::numlock
       logical name: input4::scrolllock
       capabilities: i8042
  [B]*-input:13
       product: USB USB Keyboard
       physical id: e
       logical name: input8
       logical name: /dev/input/event7
       logical name: input8::capslock
       logical name: input8::numlock
       logical name: input8::scrolllock
       capabilities: usb[/B]
  *-input:14
       product: USB USB Keyboard Consumer Control
       physical id: f
       logical name: input9
       logical name: /dev/input/event8
       capabilities: usb
```

---

### Post by TheFu on 2022-04-24
Would be really helpful if you quoted a bit of the prior post that you are responding.  Otherwise, we can't tell easily what is being responded about.  I read/reply to about 20 posts a day and often toggle back and forth between multiple. Sometimes I get confused. I've seen where others do to. Humans. We are easily confused. /s  No need to quote the entire thing - just enough with the question that was asked.

---

### Post by him610 on 2022-04-24
> After all, wayland seems to be the future.
Oftentimes there are bumps, ruts, broken bridges, and detours on the road to the future.

---

### Post by patrikrufino on 2022-04-26
> **TheFu said:**
> Would be really helpful if you quoted a bit of the prior post that you are responding.  Otherwise, we can't tell easily what is being responded about.  I read/reply to about 20 posts a day and often toggle back and forth between multiple. Sometimes I get confused. I've seen where others do to. Humans. We are easily confused. /s  No need to quote the entire thing - just enough with the question that was asked.

I'm sorry, I'm getting the hang of it here, you're right, the answers are loose.


In the case of the command that I had previously given, I did, but I didn't quite understand the sense.

---

### Post by patrikrufino on 2022-04-26
> **him610 said:**
> Oftentimes there are bumps, ruts, broken bridges, and detours on the road to the future.

Indeed.


We need to go through this, to make more progress.


But let's face it, it's too boring when the bumps appear

---

