---
title: "Screen flickering - Acer Switch 5"
date: 2019-11-07
forum: Hardware
---

### Post by DarrenO on 2019-11-07
Hi Friendly Ubuntu Users!

This problem has been dogging me for about 10 months now. The problem comes and goes but lately it has been worse so it is time to post and seek help.

I have an Acer Switch 5 which is a touch screen laptop. The screen has been flickering on me. Sometimes to the point that the computer is unusable. But normally it is tolerable.

I have tried mostly used Ubuntu 19.04 and more recently 19.10 but I have also tried Linux Mint (most recent) and the same thing happens. This is a video I took showing what it is like with Linux Mint but it is the same with Ubuntu. Mint is based on Ubuntu, so this is not surprising.

[https://photos.app.goo.gl/rCw2bBV9S3EALCxR8](https://photos.app.goo.gl/rCw2bBV9S3EALCxR8)

It is not always this bad.

I don't know a lot about the hardware, but this is what lspci shows:

```
lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:05.0 Multimedia controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit (rev 01)
00:13.0 Non-VGA unclassified device: Intel Corporation Sunrise Point-LP Integrated Sensor Hub (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:14.3 Multimedia controller: Intel Corporation Device 9d32 (rev 01)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:15.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #2 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #7 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Intel(R) 100 Series Chipset Family LPC Controller/eSPI Controller - 9D4E (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Non-Volatile memory controller: Intel Corporation Device f1a5 (rev 03)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)
```

I suspect I have a driver issue. The Additional Drivers tab in Software and Updates does not show a proprietary driver available.

I have no idea if I had the issues with stock Windows because I went straight to a dedicated Ubuntu install.

It only affects the built in touch screen. The external monitor is fine via the USB C port. 

Looking for any tips on things I can try.

Thanks!

---

### Post by DarrenO on 2019-11-12
```

inxi -F
System:    Host: darreno Kernel: 5.3.0-19-generic x86_64 bits: 64 Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:   Type: Tablet System: Acer product: Switch SW512-52 v: V1.09 serial: <root required> 
           Mobo: KBL model: Guam_KL v: V1.09 serial: <root required> UEFI: Insyde v: 1.09 date: 12/21/2018 
Battery:   ID-1: BAT0 charge: 36.8 Wh condition: 36.8/39.0 Wh (94%) 
CPU:       Topology: Dual Core model: Intel Core i5-7200U bits: 64 type: MT MCP L2 cache: 3072 KiB 
           Speed: 800 MHz min/max: 400/3100 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 801 
Graphics:  Device-1: Intel HD Graphics 620 driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.5 driver: i915 resolution: 2160x1440~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2) v: 4.5 Mesa 19.2.1 
Audio:     Device-1: Intel Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit driver: ipu3-imgu 
           Device-2: Intel driver: ipu3-cio2 
           Device-3: Intel Sunrise Point-LP HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.3.0-19-generic 
Network:   Device-1: Intel Wireless 7265 driver: iwlwifi 
           IF: wlp2s0 state: up mac: 7c:2a:31:02:80:0f 
           Device-2: Realtek RTL8153 Gigabit Ethernet Adapter type: USB driver: r8152 
           IF: enx00e04c003a00 state: up speed: 100 Mbps duplex: full mac: 00:e0:4c:00:3a:00 
Drives:    Local Storage: total: 238.47 GiB used: 12.12 GiB (5.1%) 
           ID-1: /dev/nvme0n1 vendor: Intel model: SSDPEKKW256G7 size: 238.47 GiB 
RAID:      Hardware-1: Intel 82801 Mobile SATA Controller [RAID mode] driver: ahci 
Partition: ID-1: / size: 233.24 GiB used: 12.12 GiB (5.2%) fs: ext4 dev: /dev/nvme0n1p2 
Sensors:   System Temperatures: cpu: 32.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 282 Uptime: 4m Memory: 7.54 GiB used: 2.27 GiB (30.1%) Shell: bash inxi: 3.0.36

```

---

### Post by DarrenO on 2019-11-17
Whoa. 2 views in a week. Tough crowd :)

I am trying to figure out if this is a hardware or a software issue. If it is hardware, I am under warranty for another month and I can try to get Acer to look at it. I would rather not have to install Windows to confirm that it is a hardware issue, but that is the only way I can think of doing it. 

My flickering issue is very random. It will be totally fine one day then the next day flickering away. I tried installing Debian with Gnome, Ubuntu (my prefered OS), and Mint but they all exhibit the same behaviour. 

I wondered if it is related to my wifi adapter and some interference issue. Currently using the computer with Wifi disabled to see if that helps. I guess this would be a hardware issue if it works.

I can't figure out this screen for Wifi. Is it using a proprietary driver or not? It says my wifi is not working, but if I "turn it on" it works fine (this screen does not change).
Edit: images not displaying.
Under software and updates in the menu it says:
Intel Corporation Wireless 7265 (Dual Band Wireless-AC 7265)
  This device is not working.
  {unchecked and greyed out} Using iwlwifi driver backport in DKMS format from backport-iwlwifi-dkms (open-source)
  {unchecked} Continue using a manually installed driver
  {checked and greyed out} Do not use this device

Then underneath it says "No proprietary drivers are in use".

This wifi stuff is a long shot, but no flickers on the display so far.

Thanks!

---

### Post by mörgæs on 2019-11-18
Maybe besides the point: Number of views is always equal to number of posts in the thread. An old bug.  
I don't think it helps with your main problem but I at least I'm now raising your number of views by one.

---

### Post by CatKiller on 2019-11-18
> **DarrenO said:**
> The Additional Drivers tab in Software and Updates does not show a proprietary driver available.

The Intel graphics drivers are all open source. As far as I'm aware Intel's network drivers are all open source, too. 

I've not experienced the issue you're having: the touchscreen I have just worked out of the box.

A mechanism that might cause the issue you're having might be that the refresh rate for the display is unexpected - perhaps to save power - and that's causing the graphics stack to get confused about when the screen blanks should happen. That's largely guesswork, though, and I don't know how one would fix it other than BIOS updates and looking into how Intel / Mesa are handling refresh rates. There have been changes there, with variable refresh rates and so on, but I don't know the details because it's not something I've had to deal with.

---

### Post by DarrenO on 2019-11-18
@mörgæs. Thanks for helping me feel less alone in the Linux wilderness.

@CatKiller. Interesting points. I have night light turned on. Wonder if that might have something to do with it, or perhaps automatic brightness adjustments. I'll disable both and see what happens. Maybe I can disable power saving modes. I'll have a look.

This problem is completely random and I can go a day without any issues, but then it is back the next day. 

I'll keep probing.

---

### Post by itaibh on 2019-11-21
I also have the same problem of not seeing anything in the proprietary drivers tab.

This is the output of my lspci:

```

lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family KT Controller (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
03:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)

```
Computer seems to work fine, but some software that needs the GPU can't access it.

---

### Post by DarrenO on 2019-11-23
I am starting to think my issue is due to poor heat management in the tablet. I think I will run a little script to monitor and record CPU temperature and see if the screen flickering corresponds to a rise in CPU temp.

I called ACER today and as soon as I said I had screen flickering issues, they said to bring it into the repair shop which happens to be close to where I live.

Thx!

---

### Post by DarrenO on 2019-12-05
Just want to close the loop on this. Got computer back from Acer. They replaced the LCD model (screen). Not sure if that deserves a Captain Holt "vindication" response. So far so good. Will monitor.

---

