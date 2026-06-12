---
title: "Debugging NVIDIA NVRM Xid Errors"
date: 2009-05-19
forum: Hardware
---

### Post by stderr on 2009-05-19
Has anyone had any joy in trying to debug these? Plus I want to get an idea how many others are suffering from NVIDIA's Xid errors.

Since I bought an Asus 9800GT, I've been having a series of (entirely) unpredictable hard crashes. Under my previous 7600GS, I had no issues. They can occur from doing anything: switching between 3D applications and other video-intensive tasks, to having almost no screen/cpu activity. Crashes typically involve a loss of all forms of KB control: magic keys do not work, but typically you'll still be able to move the cursor (to no effect). Some syslog examples:

(driver: NVIDIA 177.82)

```
Mar 28 02:02:01 ace1 kernel: [177343.453159] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001458 00000006 00000100

Mar 31 05:03:49 ace1 kernel: [262758.392403] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001458 00000006 00000100

May 16 05:50:36 ace1 kernel: [2189363.352569] NVRM: Xid (0001:00): 8, Channel 00000001
May 16 05:51:46 ace1 kernel: [2189428.300501] BUG: soft lockup - CPU#1 stuck for 61s! [Xorg:6006]
May 16 05:51:46 ace1 kernel: [2189428.300501] Pid: 6006, comm: Xorg Tainted: P          (2.6.27-11-generic #1)
May 16 05:51:46 ace1 kernel: [2189428.300501] EIP: 0060:[<f943e440>] EFLAGS: 00203293 CPU: 1
May 16 05:51:46 ace1 kernel: [2189428.300501] EIP is at _nv009108rm+0x197/0x1a0 [nvidia]
May 16 05:51:46 ace1 kernel: [2189428.300501] EAX: 5132d9f1 EBX: 00000000 ECX: f6215d94 EDX: 00046a00
May 16 05:51:46 ace1 kernel: [2189428.300501] ESI: f6215dc8 EDI: 00000000 EBP: f6215d90 ESP: f5437cb4
May 16 05:51:46 ace1 kernel: [2189428.300501]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
May 16 05:51:46 ace1 kernel: [2189428.300501] CR0: 8005003b CR2: a6760000 CR3: 35ff5000 CR4: 00000690
May 16 05:51:46 ace1 kernel: [2189428.300501] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
May 16 05:51:46 ace1 kernel: [2189428.300501] DR6: ffff0ff0 DR7: 00000400
*[soft lockup message + reg dump repeats every 60s until reboot]*

May 19 00:52:28 ace1 kernel: [  598.580534] NVRM: Xid (0001:00): 8, Channel 00000003
May 19 00:52:41 ace1 kernel: [  611.584531] NVRM: Xid (0001:00): 8, Channel 00000001
```

Given I can appear to go for long periods of time (months) without any Xids, this makes debugging these problems terribly difficult. At the moment I'm back on my 7600GS following the 16th May hard crash, which I initially put down to HDD failure due to the extent of the crash and messages from the mobo. Now, however, after some (frantic) coaxing, the HDD is back up and running, and reporting A-OK from SMART status to surface scans and fs checks. Then I found the original Xid in the log (listed above) which caused the crash. Why my motherboard continues to warn of SMART failure on the HDD in question every X boots, I'm not sure. Perhaps the Xid dealt more damage than I can trace, as of yet.

All NVIDIA seems to say, and all they ever ask for & complain about people not doing, is to run **nvidia-bug-report.sh**, which is of no real help. It just takes some log entires and other hw info such as loaded modules, and sticks all the data in a file. The most useful thing in it is the Xid value(s) which are in syslog (& normally kern.log) anyway. If anyone can offer any advice that *doesn't* involve nvidia-bug-report, I'd be very grateful. 

Otherwise, I'll be returning my 9800GT: I have no use for hardware+driver combinations that either a) wreck my system or b) fail to provide 3d accn. 

Bottom line: _not_ impressed with my move to NVIDIA. Will likely return to ATI shortly.

---

### Post by many_boomers on 2009-06-05
Damn. Similar problems on similar channels. I'm running a BFG 6200oc PCI card on a desk top.

dmesg | grep -i nv returns

```
[    0.000000]  BIOS-e820: 000000007fe70000 - 000000007fe72000 (ACPI NVS)
[   17.531820] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   32.742260] nvidia: module license 'NVIDIA' taints kernel.
[   33.665918] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[  877.468540] NVRM: Xid (0001:00): 8, Channel 00000003
[  983.579839] NVRM: Xid (0001:00): 8, Channel 00000003

```

---

### Post by screig on 2009-06-15
I have an Asus P5N7A-VM with NVIDIA 9300

I get the same, freezes, must reboot

Jun 15 20:07:20 NightFlyer NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jun 15 20:07:20 NightFlyer NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 15 20:07:20 NightFlyer ntpdate[4114]: adjust time server 91.189.94.4 offset 0.433523 sec
Jun 15 20:07:26 NightFlyer kernel: [   54.536036] wlan0: no IPv6 routers present
Jun 15 20:08:36 NightFlyer kernel: [  123.868071] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:08:36 NightFlyer kernel: [  123.884637] NVRM: Xid (0003:00): 13, 0003 00000000 00008397 00001408 00000001 00000040
Jun 15 20:08:37 NightFlyer kernel: [  124.945726] NVRM: Xid (0003:00): 13, 0003 00000000 00008397 000015e0 00000000 00000040
Jun 15 20:08:37 NightFlyer kernel: [  124.960615] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:08:37 NightFlyer kernel: [  125.106931] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:09:53 NightFlyer syslogd 1.5.0#5ubuntu3: restart.
Jun 15 20:09:53 NightFlyer kernel: Inspecting /boot/System.map-2.6.29-020629-generic
Jun 15 20:09:53 NightFlyer kernel: Cannot find map file.
Jun 15 20:09:53 NightFlyer kernel: Loaded 82768 symbols from 52 modules.
Jun 15 20:09:53 NightFlyer kernel: [    0.000000] Initializing cgroup subs

---

### Post by marcus.kempe on 2009-07-06
I'm also experiencing this, on a Dell Precision M4400 Laptop.
Graphics adapter: nVidia Corporation Quadro FX 770M

Sometimes I get the complete kernel panic, with keyboard leds blinking. Then nothing in the logs. Sometimes I get these kind of soft porblems as below, when the graphics driver just seems to crash, and then recover after a while (no reboot involved in the below):



```
Jul  6 12:09:24 nibbler Synergy 1.3.1: NOTE: CClientProxy1_0.cpp,221: client "kempe" is dead
Jul  6 12:09:27 nibbler kernel: [45533.372670] NVRM: Xid (0001:00): 8, Channel 00000003
Jul  6 12:09:27 nibbler Synergy 1.3.1: NOTE: CClientListener.cpp,127: accepted client connection
Jul  6 12:09:27 nibbler Synergy 1.3.1: NOTE: CServer.cpp,278: client "kempe" has connected
Jul  6 12:10:01 nibbler /USR/SBIN/CRON[22437]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  6 12:10:59 nibbler kernel: [45625.388711] NVRM: Xid (0001:00): 8, Channel 00000001
Jul  6 12:10:59 nibbler kernel: [45625.427060] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000f04 00000000 00000040
Jul  6 12:10:59 nibbler kernel: [45625.428235] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00000f04 00000000 00000040
Jul  6 12:10:59 nibbler kernel: [45625.650573] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 000015e0 00000000 00000040
Jul  6 12:11:15 nibbler kernel: [45641.988185] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 000015e0 00000000 00000040
Jul  6 12:11:16 nibbler kernel: [45642.269826] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 000015e0 00000000 00000040
Jul  6 12:11:36 nibbler kernel: [45662.649087] NVRM: Xid (0001:00): 13, 0003 00000000 00008297 00001310 00000000 00000040
Jul  6 12:13:02 nibbler Synergy 1.3.1: NOTE: CClientProxy1_0.cpp,221: client "kempe" is dead
Jul  6 12:13:06 nibbler Synergy 1.3.1: NOTE: CClientListener.cpp,127: accepted client connection
Jul  6 12:13:06 nibbler Synergy 1.3.1: NOTE: CServer.cpp,278: client "kempe" has connected
Jul  6 12:13:58 nibbler acpid: client 3186[0:0] has disconnected 
Jul  6 12:13:58 nibbler acpid: client 3186[0:0] has disconnected 
Jul  6 12:16:00 nibbler acpid: client connected from 3186[0:0] 
Jul  6 12:16:01 nibbler acpid: client connected from 3186[0:0] 
Jul  6 12:17:01 nibbler /USR/SBIN/CRON[22996]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  6 12:20:01 nibbler /USR/SBIN/CRON[23197]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
```

---

### Post by Ostomizer on 2009-08-18
I'm running Ubuntu 9.04 Jaunty Jackalope on an EVGA nForce 680i motherboard with 2x2 GB SLI-ready Corsair Dominator RAM, an Intel Q9400 Core 2 Quad @ 2.66 GHz and a single EVGA 8800GTS nvidia card, and this is my story.

I had a stable Ubuntu 9.04 system running until sometime around mid July.  I'm not sure if the problems were due to an automatic update to the Ubuntu kernels, but I didn't actively change the configuration in any way that would cause my system to begin crashing.  I am experiencing similar symptoms to the previous posters; specifically, my screen would corrupt, crash, and require a reboot.  I have tried a few things in an attempt to fix the situation, including:

- reinstalling the nvidia 185.18.29 drivers
- installing the nvidia 185.18.31 drivers
- installing the nvidia 190.10 drivers
- reinstalling xorg
- reverting nvidia drivers back to 185.18.29
- reverting the nvidia drivers back to 180.60
- adding 'Option "NvAGP" "1"' to my xorg.conf file
- changing 'Option "NvAGP" "1"' to 'Option "NvAGP" "0"' (system won't boot)

Currently, my system is meta-stable, in that it will run for extended periods of time with only the occasional screen flicker (which might be a re-upload of the kernel to the graphics card?).  The split-second blackscreens are usually accompanied by an entry of the form NVRM: Xid 6 / 13 in the kern.log file.  Does anyone have any leads on how to pinpoint the cause of these failures?  I've been troubleshooting this for days now with seemingly no progress.  For completeness' sake, below are some useful outputs, in case anyone can understand the error codes contained within, or happens to notice a problematic statement with the configuration.  Any leads or help would be greatly appreciated.  Again, the system was stable, with no active changes on my part, until "something happened".  I did install the CUDA libraries around that time, and run some examples, but I can imagine that any of that could have actually changed the configuration of the GPU kernel.

xorg.conf device section:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "NvAGP" "1"
EndSection

cat /var/log/Xorg.0.log | grep -i agp:

(**) NVIDIA(0): Option "NvAGP" "1"
(**) Aug 18 10:42:52 NVIDIA(0): Use of NVIDIA internal AGP requested

cat /var/log/Xorg.0.log | grep -i gart:

(II) Aug 18 10:42:54 NVIDIA(0): Initialized GPU GART.

cat /var/log/kern.log | grep -i nv: (multiple instances similar to the following):

[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000]  modified: 000000007fef0000 - 000000007fef3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000F7FA0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEF3040, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 7FEF30C0, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: DSDT 7FEF3180, 541D (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: HPET 7FEF8700, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: WDRT 7FEF8780, 0047 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: MCFG 7FEF8840, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 7FEF8600, 0098 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    1.561597] sata_nv 0000:00:0e.0: version 3.5
[    1.561838] sata_nv 0000:00:0e.0: PCI INT A -> Link[ASA0] -> GSI 21 (level, low) -> IRQ 21
[    1.561840] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.562044] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.562163] scsi0 : sata_nv
[    1.562249] scsi1 : sata_nv
[    3.026587] sata_nv 0000:00:0e.1: PCI INT B -> Link[ASA1] -> GSI 20 (level, low) -> IRQ 20
[    3.026590] sata_nv 0000:00:0e.1: Using SWNCQ mode
[    3.026614] sata_nv 0000:00:0e.1: setting latency timer to 64
[    3.026696] scsi2 : sata_nv
[    3.026734] scsi3 : sata_nv
[    4.758723] sata_nv 0000:00:0e.2: PCI INT C -> Link[ASA2] -> GSI 21 (level, low) -> IRQ 21
[    4.758725] sata_nv 0000:00:0e.2: Using SWNCQ mode
[    4.758749] sata_nv 0000:00:0e.2: setting latency timer to 64
[    4.758832] scsi4 : sata_nv
[    4.758902] scsi5 : sata_nv
[    6.668360] ata7: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[    6.668363] ata7: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x1f)
[    6.800136] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    6.958988] nv_probe: set workaround bit for reversed mac addr
[    7.478772] nv_probe: set workaround bit for reversed mac addr
[    9.961987] generic-usb 0003:051D:0002.0003: hiddev96,hidraw2: USB HID v1.10 Device [American Power Conversion Back-UPS XS 1500 LCD FW:837.H5 .D USB FW:H5 ] on usb-0000:00:0b.0-3/input0
[   24.831822] nvidia: module license 'NVIDIA' taints kernel.
[   25.084172] nvidia 0000:01:00.0: PCI INT A -> Link[AXV5] -> GSI 16 (level, low) -> IRQ 16
[   25.084177] nvidia 0000:01:00.0: setting latency timer to 64

[   25.084304] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.18  Wed Jul 22 18:30:32 PDT 2009
[ 2754.441266] NVRM: Xid (0001:00): 6, PE0001
[ 2893.097535] NVRM: Xid (0001:00): 13, 0003 00000000 00005097 000019c4 00040000 00000005
[ 2893.101190] NVRM: Xid (0001:00): 13, 0003 00000000 00005097 000019c4 00040000 00000005
[ 2893.899461] NVRM: Xid (0001:00): 13, 0001 00000000 00005097 00000200 000c0000 0000000c
[ 2893.903119] NVRM: Xid (0001:00): 13, 0001 00000000 00005097 00000200 000c0000 0000000c
[ 3129.872050] NVRM: Xid (0001:00): 13, 0001 00000000 00005097 00001458 00ff0001 00000003
[ 3129.875691] NVRM: Xid (0001:00): 13, 0001 00000000 00005097 00001458 00ff0001 00000003
[ 3301.118756] NVRM: Xid (0001:00): 6, PE0003

---

### Post by Ostomizer on 2009-08-24
In case anyone is having this problem, I suspect it may be related to voltage supplied to the video card.  To recap, the computer experiencing the display corruption / "nvrm xid" errors is composed of:
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16811156062"]
[/URL]
[LIST]
[*][RAIDMAX SMILODON ATX-612WBP Black 1.0mm SECC Steel ATX Mid Tower Foldout MB Computer Case With 500W Power Supply]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811156062")
[/LIST]

[LIST]
[*][EVGA 122-CK-NF68-A1 LGA 775 NVIDIA nForce 680i SLI ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813188013")
[/LIST]

[LIST]
[*][EVGA 640-P2-N821-AR GeForce 8800 GTS 640MB 320-bit GDDR3 PCI Express x16 HDCP Ready SLI Supported Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130071")
[/LIST]

[LIST]
[*][Intel Core2 Quad Q9400 2.66GHz 6MB L2 Cache LGA 775 95W Quad-Core Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115131")
[/LIST]

[LIST]
[*][CORSAIR Dominator 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory Model TWIN2X2048-8500C5D]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820145043")
[/LIST]

[LIST]
[*][Creative Sound Blaster X-Fi XtremeGamer 7.1 Channels 24-bit 96KHz PCI Interface Sound Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102006")
[/LIST]

[LIST]
[*]7200 RPM 320 GB and 1.5 TB Seagate Barracuda drives
[/LIST]

I hadn't experienced any display corruption on this computer until after I had 1) installed Ubuntu and 2) upgraded my core 2 duo to a core 2 quad.  I've recently noticed that the large amount of noise coming from my power supply is actually a periodic high-pitched whining / beating noise, and that it only begins to make this noise after the computer has been on for at least a short while, after having been off for a long time.  If I soft reboot the computer, the noise does not go away.  Based on the Newegg reviews of the case & power supply combo I bought about 2 years ago, the power supply seems to be bad quality.  I have just ordered a [CORSAIR CMPSU-620HX 620W ATX12V v2.2]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817139002"), and will report back on whether or not this solves my display corruption issue.  I have never known much about, or discriminated much among available power supplies, but after having read some threads elsewhere about GPU undervoltage causing graphical display corruption, "bad power supply" seems like a plausible root cause.  For anyone actually stumbling across this thread trying to solve the same problem, I'll report back here after the new supply arrives.

---

### Post by Ostomizer on 2009-08-31
Installed the new supply today.  No more beeping, runs smooth as butter.

---

### Post by Ostomizer on 2009-09-03
Unfortunately,

Sep  3 08:42:42 desktop kernel: [231637.717161] NVRM: Xid (0001:00): 2, CCMDs 00000003 00005072 00000174 04700438 00000006
Sep  3 08:44:23 desktop kernel: [231739.444257] NVRM: Xid (0001:00): 6, PE0003 
Sep  3 08:44:23 desktop kernel: [231739.452618] NVRM: Xid (0001:00): 6, PE0001 
Sep  3 08:53:35 desktop kernel: [232291.393932] NVRM: Xid (0001:00): 6, PE0001 
Sep  3 08:53:40 desktop kernel: [232295.678599] NVRM: Xid (0001:00): 6, PE0003 
Sep  3 09:34:19 desktop kernel: [234734.771551] NVRM: Xid (0001:00): 6, PE0003 
Sep  3 09:35:26 desktop kernel: [234802.323266] NVRM: Xid (0001:00): 13, 0003 00000000 00005097 0000192c 00d80001 0000000c
Sep  3 09:35:26 desktop kernel: [234802.326910] NVRM: Xid (0001:00): 13, 0003 00000000 00005097 0000192c 00d80001 0000000c

new power supply didn't fix the problem.  It only occurs after the computer's been up and running for a while (1+ days), so maybe it's a heating issue.  Any suggestions would be mighty welcome.

---

### Post by gianluca.pettinello on 2009-09-06
I have the same problem since some days. Mainly the error comes when I'm running sdlmame and I try to go to fullscreen. Could be that it is linked to sdl layer.
I tried NvAGP = 1, 2 or 3 but in /proc/driver/nvidia/registry the NvAGP option is always set to 3 that is the system try to open the kernel AGP GART and if not successful it opens the NVIDIA GART.
I'm stuck

Gianluca

---

### Post by Ostomizer on 2009-09-06
I found more information in forums through googling that pointed to dual-channel RAM causing this type of problem.  I went into my BIOS, disabled the "SLI-ENABLED" setting, and I haven't had the problem since.  Do you have SLI memory / dual channel setup?

---

### Post by koma77 on 2009-11-22
I'm also having this problem with an NVidia 260.
My setup has run fine until I installed 9.10.

However, I suspect that some faulty HW could be involved since sometimes at boot my motherboard gives me the "VGA not found"-beeps.

Strange thing is that everything seems stable in XP even when running GPU intensitive games.

My freeze is always started with a split second black screen. After that I can only move my mouse pointer. There is also a black small square at center top of the screen.

If I log into the computer using SSH I can see that Xorg takes all CPU.

Doing a "killall Xorg" gets me back to gdm and all works fine again.

The error message I get in the log is:
NVRM: Xid (0001:00): 13, 0001 00000000 00000000 00000000 00000000 00000080

Does anyone know what Xid 13 is?

---

### Post by wilderwind on 2009-11-23
Hi all! Sorry for my english, I'm from Russia :p
Well, I have the same bug with NVRM xid 13, on my laptop Asus Pro58VN. Ubuntu 9.10 32bit, NVIDIA 190.42 video driver, 9650m GT graphic card. I've been lookong for the way to fix this awful bug since I have Ubuntu, but I coudn't find this one. Google can't help me too ((( But in one beautiful moment I disable PowerMizer in NVIDIA X Server settings (set option "Prefer maximum performance"), and now I have no bugs with NVRM xid at all! Maybe, xid13-bug appears when video card use nvram function (1Gb VRAM for my 9650m GT card, for example) and increase/decrease GPU core frequency (if PowerMizer option is enabled)? IMHO, bug is not in linux kernel or hardware, but in NVIDIA graphic driver, in realization of PowerMizer option (aka GPU scaling) and using additional RAM.
P.S. It's not good to disable PowerMizer for powersaving and laptop battery, but it works and xid bugs not appears... Waiting for new NVIDIA driver now.

---

### Post by kcox5342 on 2009-11-23
I'm experiencing similar issues.  I have an X-Blade setup which came pre-built except for disk drives, with NVidia graphics, running 8.04.  It was fine for a while but now certain things make it crash pretty reliably, while other things don't.  Open Arena makes the system lock up pretty quickly, other 3D games quit to the desktop, but even FTPing large files over the LAN from my Mac will make it go wonky.  I'm not sure what the technical term for it is, but when you say "the screen locked up", are you talking about something like this?

[[IMG]http://img684.imageshack.us/img684/7227/1001762.th.jpg[/IMG]](http://img684.imageshack.us/i/1001762.jpg/)

---

### Post by koma77 on 2009-11-23
That is not how my system looks when the screen locks up.
My system shows a perfectly normal image, but it is completely static (except the mouse pointer).

---

### Post by kcox5342 on 2009-11-23
I just ran Envy, which switched my NVIDIA drivers.  I suppose I should also mention this machine is running mythtv-backend and Apache.  As a server, it is rock solid - these crashes only occur when I'm actually sitting at the machine itself.  And Envy says my chipset is an NVIDIA GEforce 7025.

After running Envy, it still locks up.  None of them have involved that mess in the picture, though.  So I guess that's an improvement, although not much.

Open Arena crashed by stopping accepting any inputs.  I ran into a corner, the bots continued their mayhem for another 20-30 seconds, then everything locked.  Rebooted, but forgot to inspect syslog.

Mythtv-frontend is another frequent crasher.  I was watching some TV and had to reboot twice, which produced weirdly different results in syslog, even though they both appeared to me, the user, to be a full freeze.

First syslog output:
```

Nov 23 12:24:50 mythbox mysqld[6891]: 091123 12:24:50 - mysqld got signal 11;
Nov 23 12:24:50 mythbox mysqld[6891]: This could be because you hit a bug. It is also possible that this binary
Nov 23 12:24:50 mythbox mysqld[6891]: or one of the libraries it was linked against is corrupt, improperly built,
Nov 23 12:24:50 mythbox mysqld[6891]: or misconfigured. This error can also be caused by malfunctioning hardware.
Nov 23 12:24:50 mythbox mysqld[6891]: We will try our best to scrape up some info that will hopefully help diagnose
Nov 23 12:24:50 mythbox mysqld[6891]: the problem, but since we have already crashed, something is definitely wrong
Nov 23 12:24:50 mythbox mysqld[6891]: and this may fail.
Nov 23 12:24:50 mythbox mysqld[6891]: 
Nov 23 12:24:50 mythbox mysqld[6891]: key_buffer_size=16777216
Nov 23 12:24:50 mythbox mysqld[6891]: read_buffer_size=131072
Nov 23 12:24:50 mythbox mysqld[6891]: max_used_connections=6
Nov 23 12:24:50 mythbox mysqld[6891]: max_connections=100
Nov 23 12:24:50 mythbox mysqld[6891]: threads_connected=6
Nov 23 12:24:50 mythbox mysqld[6891]: It is possible that mysqld could use up to 
Nov 23 12:24:50 mythbox mysqld[6891]: key_buffer_size + (read_buffer_size + sort_buffer_size)*max_connections = 4944383 K
Nov 23 12:24:50 mythbox mysqld[6891]: bytes of memory
Nov 23 12:24:50 mythbox mysqld[6891]: Hope that's ok; if not, decrease some variables in the equation.
Nov 23 12:24:50 mythbox mysqld[6891]: 
Nov 23 12:24:50 mythbox mysqld[6891]: thd=(nil)
Nov 23 12:24:50 mythbox mysqld[6891]: Attempting backtrace. You can use the following information to find out
Nov 23 12:24:50 mythbox mysqld[6891]: where mysqld died. If you see no messages after this, something went
Nov 23 12:24:50 mythbox mysqld[6891]: terribly wrong...
Nov 23 12:24:50 mythbox mysqld[6891]: frame pointer is NULL, did you compile with
Nov 23 12:24:50 mythbox mysqld[6891]: -fomit-frame-pointer? Aborting backtrace!
Nov 23 12:24:50 mythbox mysqld[6891]: The manual page at http://www.mysql.com/doc/en/Crashing.html contains
Nov 23 12:24:50 mythbox mysqld[6891]: information that should help you find out what is causing the crash.
Nov 23 12:24:50 mythbox mysqld_safe[8810]: Number of processes running now: 0
Nov 23 12:24:50 mythbox mysqld_safe[8812]: restarted
Nov 23 12:24:50 mythbox mysqld[8816]: InnoDB: The log sequence number in ibdata files does not match
Nov 23 12:24:50 mythbox mysqld[8816]: InnoDB: the log sequence number in the ib_logfiles!
Nov 23 12:24:50 mythbox mysqld[8816]: 091123 12:24:50  InnoDB: Database was not shut down normally!
Nov 23 12:24:50 mythbox mysqld[8816]: InnoDB: Starting crash recovery.
Nov 23 12:24:50 mythbox mysqld[8816]: InnoDB: Reading tablespace information from the .ibd files...
Nov 23 12:24:50 mythbox mysqld[8816]: InnoDB: Restoring possible half-written data pages from the doublewrite
Nov 23 12:24:50 mythbox mysqld[8816]: InnoDB: buffer...
Nov 23 12:24:50 mythbox mysqld[8816]: 091123 12:24:50  InnoDB: Started; log sequence number 0 87003
Nov 23 12:24:50 mythbox mysqld[8816]: 091123 12:24:50 [Note] /usr/sbin/mysqld: ready for connections.
Nov 23 12:24:50 mythbox mysqld[8816]: Version: '5.0.51a-3ubuntu5.4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
```

Whereas the second is much shorter:

```
Nov 23 12:37:22 mythbox kernel: [  517.402253] mythfrontend.re[8511] trap stack segment rip:7f54e4aa8101 rsp:44b5e840 error:0
```

The first time, the video froze.  The second time, I was quit back to my desktop, except the windows didn't look quite right, and I could only move the mouse.  Alt-F2 did nothing.

---

### Post by koma77 on 2009-11-23
I cannot find the option to disable the powermizer feature... How did you do that?

---

### Post by wilderwind on 2009-11-23
> **koma77 said:**
> I cannot find the option to disable the powermizer feature... How did you do that?

Not to disable permanently, but set to "Prefer maximum performance". If you decide to disable PowerMizer, do one of the following: 

[http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)
[http://ubuntuforums.org/showthread.php?t=855400](http://ubuntuforums.org/showthread.php?t=855400)
[http://ubuntuforums.org/showthread.php?t=1128260](http://ubuntuforums.org/showthread.php?t=1128260)

There's 100% bug in GPU scaling function of NVIDIA driver, I think...


YEAH! Problem 50% solved. To disable automatic GPU scaling in PowerMizer option of NVIDIA X Server Settings, do this:

Run in terminal:
**sudo gedit /etc/modprobe.d/nvidia.conf**
Write in the open window:
**options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"**
Save and reboot.

After reboot, open NVIDIA X Server Settings in PowerMizer parameter. You will see that Preferred Mode is set to Adaptive, but NV Clock and Memory Clock will be freezed on level 3 - Maximum Performance.

Enjoy! No more NVRM xid bugs. But it is a wrong way to disable GPU scaling, and I hope that NVIDIA will fix this bug in next video driver release.

---

### Post by finomeno on 2009-11-24
I'm not quite sure if my bug is the same. I was running smoothly until recently without any tinkering from my part I started having these screen freezes with only the mouse moving and no reaction to clicks or key presses. A random key press revealed that PrintScreen makes the system respond again as if nothing happened. And a dialog for saving the screengrab does actually appear.

These freezes happen every time I stop my screensaver (not locking the screen). Cannot reproduce in screensaver testing mode.

---

### Post by wilderwind on 2009-11-25
Video card uses GPU scaling when screensaver is running or is in starting/stopping status (for example, GL screensaver pack based on OpenGL and video card uses switching from 2D to 3D mode with these screensavers). Try to disable PowerMizer as it is written above, reboot and test non-scaling mode. If screen freezes will not disappear - simply enable PowerMizer again and search other way to solve your problem...

---

### Post by finomeno on 2009-11-26
&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;, &#1087;&#1086;&#1087;&#1088;&#1086;&#1073;&#1091;&#1102;.
&#1061;&#1086;&#1090;&#1103; &#1085;&#1077; &#1093;&#1086;&#1090;&#1077;&#1083;&#1086;&#1089;&#1100; &#1073;&#1099;, &#1087;&#1086;&#1090;&#1086;&#1084;&#1091; &#1082;&#1072;&#1082; &#1074;&#1089;&#1105; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1083;&#1086; &#1086;&#1090;&#1083;&#1080;&#1095;&#1085;&#1086;, &#1072; &#1087;&#1086;&#1090;&#1086;&#1084; &#1074;&#1076;&#1088;&#1091;&#1075; &#1085;&#1072;&#1095;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1089;&#1083;&#1077; &#1082;&#1072;&#1082;&#1086;&#1075;&#1086;-&#1090;&#1086; &#1072;&#1087;&#1076;&#1077;&#1081;&#1090;&#1072; &#1080; &#1073;&#1077;&#1079; &#1084;&#1086;&#1077;&#1075;&#1086; &#1074;&#1084;&#1077;&#1096;&#1072;&#1090;&#1077;&#1083;&#1100;&#1089;&#1090;&#1074;&#1072; &#1074; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1091;.

---

### Post by wilderwind on 2009-11-26
> **finomeno said:**
> &#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;, &#1087;&#1086;&#1087;&#1088;&#1086;&#1073;&#1091;&#1102;.
&#1061;&#1086;&#1090;&#1103; &#1085;&#1077; &#1093;&#1086;&#1090;&#1077;&#1083;&#1086;&#1089;&#1100; &#1073;&#1099;, &#1087;&#1086;&#1090;&#1086;&#1084;&#1091; &#1082;&#1072;&#1082; &#1074;&#1089;&#1105; &#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1083;&#1086; &#1086;&#1090;&#1083;&#1080;&#1095;&#1085;&#1086;, &#1072; &#1087;&#1086;&#1090;&#1086;&#1084; &#1074;&#1076;&#1088;&#1091;&#1075; &#1085;&#1072;&#1095;&#1072;&#1083;&#1086;&#1089;&#1100; &#1087;&#1086;&#1089;&#1083;&#1077; &#1082;&#1072;&#1082;&#1086;&#1075;&#1086;-&#1090;&#1086; &#1072;&#1087;&#1076;&#1077;&#1081;&#1090;&#1072; &#1080; &#1073;&#1077;&#1079; &#1084;&#1086;&#1077;&#1075;&#1086; &#1074;&#1084;&#1077;&#1096;&#1072;&#1090;&#1077;&#1083;&#1100;&#1089;&#1090;&#1074;&#1072; &#1074; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1091;. Probably it begins after video driver updates. Check if any of proprietary NVIDIA drivers is enabled in System - Administration - Hardware drivers (I don't use this option at all) and disable this one, or try to roll back to the older video driver version then is currently in use on your system. There's perfect site [www.nvidia.com](www.nvidia.com) to download official and recommended NVIDIA drivers, sometimes with WHQL certification. You can select version of driver for your Linux there. Please write your results here if you will try to disable PowerMizer. 
&#1042; &#1086;&#1073;&#1097;&#1077;&#1084;, &#1087;&#1086;-&#1072;&#1085;&#1075;&#1083;&#1080;&#1081;&#1089;&#1082;&#1080; &#1103; &#1085;&#1077; &#1086;&#1095;&#1077;&#1085;&#1100; &#1075;&#1086;&#1074;&#1086;&#1088;&#1102;, &#1087;&#1086;&#1101;&#1090;&#1086;&#1084;&#1091; &#1074;&#1099;&#1089;&#1082;&#1072;&#1078;&#1091; &#1089;&#1074;&#1086;&#1077; &#1086;&#1082;&#1086;&#1085;&#1095;&#1072;&#1090;&#1077;&#1083;&#1100;&#1085;&#1086;&#1077; &#1084;&#1085;&#1077;&#1085;&#1080;&#1077; &#1085;&#1072; &#1088;&#1091;&#1089;&#1089;&#1082;&#1086;&#1084; )) &#1048;&#1052;&#1061;&#1054;, &#1074;&#1082;&#1083;&#1102;&#1095;&#1077;&#1085;&#1080;&#1077; &#1087;&#1088;&#1086;&#1087;&#1088;&#1080;&#1077;&#1090;&#1072;&#1088;&#1085;&#1099;&#1093; &#1076;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088;&#1086;&#1074; &#1089; &#1087;&#1086;&#1084;&#1086;&#1097;&#1100;&#1102; &#1089;&#1072;&#1084;&#1086;&#1075;&#1086; &#1051;&#1080;&#1085;&#1091;&#1082;&#1089;&#1072; &#1095;&#1072;&#1097;&#1077; &#1074;&#1089;&#1077;&#1075;&#1086; &#1087;&#1088;&#1080;&#1074;&#1086;&#1076;&#1080;&#1090; &#1082; &#1088;&#1072;&#1079;&#1085;&#1086;&#1086;&#1073;&#1088;&#1072;&#1079;&#1085;&#1099;&#1084; &#1073;&#1072;&#1075;&#1072;&#1084; &#1089; &#1080;&#1082;&#1089;&#1072;&#1084;&#1080; &#1080; &#1074;&#1086;&#1086;&#1073;&#1097;&#1077; &#1089; &#1074;&#1080;&#1076;&#1077;&#1086;, &#1087;&#1086;&#1101;&#1090;&#1086;&#1084;&#1091; &#1083;&#1091;&#1095;&#1096;&#1077; &#1101;&#1090;&#1086;&#1081; &#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1077;&#1081; &#1085;&#1077; &#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1090;&#1100;&#1089;&#1103;, &#1072; &#1082;&#1072;&#1095;&#1072;&#1090;&#1100; &#1080; &#1089;&#1090;&#1072;&#1074;&#1080;&#1090;&#1100; &#1090;&#1086;&#1083;&#1100;&#1082;&#1086; &#1086;&#1092;&#1080;&#1094;&#1080;&#1072;&#1083;&#1100;&#1085;&#1099;&#1077; &#1076;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088;&#1072; &#1089; &#1089;&#1072;&#1081;&#1090;&#1072; &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1103;. &#1054;&#1085;&#1080;, &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1090;&#1086;&#1078;&#1077; &#1080;&#1084;&#1077;&#1102;&#1090; &#1073;&#1072;&#1075; &#1089; &#1080;&#1079;&#1084;&#1077;&#1085;&#1077;&#1085;&#1080;&#1077;&#1084; &#1095;&#1072;&#1089;&#1090;&#1086;&#1090; &#1103;&#1076;&#1088;&#1072; &#1080; &#1087;&#1072;&#1084;&#1103;&#1090;&#1080; &#1074;&#1080;&#1076;&#1077;&#1086;&#1082;&#1072;&#1088;&#1090;&#1099;... &#1054;&#1090;&#1087;&#1080;&#1096;&#1080;&#1090;&#1077;&#1089;&#1100;, &#1087;&#1086;&#1078;&#1072;&#1083;&#1091;&#1081;&#1089;&#1090;&#1072;, &#1087;&#1088;&#1086;&#1073;&#1086;&#1074;&#1072;&#1083;&#1080; &#1083;&#1080; &#1042;&#1099; &#1086;&#1090;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1100; PowerMizer &#1080; &#1095;&#1090;&#1086; &#1080;&#1079; &#1101;&#1090;&#1086;&#1075;&#1086; &#1087;&#1086;&#1083;&#1091;&#1095;&#1080;&#1083;&#1086;&#1089;&#1100;. &#1045;&#1089;&#1083;&#1080; &#1087;&#1088;&#1077;&#1076;&#1087;&#1086;&#1083;&#1072;&#1075;&#1072;&#1077;&#1084;&#1099;&#1081; &#1084;&#1085;&#1086;&#1081; &#1073;&#1072;&#1075; &#1073;&#1091;&#1076;&#1077;&#1090; &#1087;&#1086;&#1076;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085; - &#1085;&#1072;&#1076;&#1086; &#1087;&#1080;&#1089;&#1072;&#1090;&#1100; &#1074; &#1089;&#1072;&#1087;&#1087;&#1086;&#1088;&#1090; &#1053;&#1042;&#1080;&#1076;&#1080;&#1080;.

---

### Post by kcox5342 on 2009-11-28
Well, whatever's plaguing my system, a new power supply did not remedy it.  Neither did Envy - I still get the weird crash screen.

Here's one crash report from syslog - I'm playing mythtv on the frontend when it dies and puts me back at the login screen:

```
Nov 28 07:58:46 mythbox kernel: [26181.382204] mythbackend[7654]: segfault at 7f5006fa4fba rip 7f5006fa4fba rsp 411b5658 error 14
Nov 28 07:58:55 mythbox kernel: [26189.943630] Xorg[7666]: segfault at 7fffdd72b740 rip 7ff9a82aba16 rsp 7fffdd68de80 error 4
Nov 28 07:58:55 mythbox kernel: [26190.384429] mythfrontend.re[25406]: segfault at 931850 rip 931850 rsp 46252628 error 15
Nov 28 07:58:56 mythbox gdm[7662]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
```

There are certain things which, as I have said, are guaranteed to make it crash after a few minutes.  Watching mythtv.  Playing Open Arena.  And, oddly enough, large (>2GB) FTP transfers from my Mac, using Nautilus (the Mac is the FTP server) - but large HTTP transfers the other way, using Apache serving from the mythbox, don't crash it at all.  And VLC Media Player never seems to crash it, even when I'm watching 1080p Quicktimes.  Does this make any sense to anyone else?

---

### Post by martini1179 on 2009-12-28
> **Ostomizer said:**
> I'm running Ubuntu 9.04 Jaunty Jackalope on an EVGA nForce 680i motherboard with 2x2 GB SLI-ready Corsair Dominator RAM, an Intel Q9400 Core 2 Quad @ 2.66 GHz and a single EVGA 8800GTS nvidia card, and this is my story.

I had a stable Ubuntu 9.04 system running until sometime around mid July.  I'm not sure if the problems were due to an automatic update to the Ubuntu kernels, but I didn't actively change the configuration in any way that would cause my system to begin crashing.  I am experiencing similar symptoms to the previous posters; specifically, my screen would corrupt, crash, and require a reboot.  I have tried a few things in an attempt to fix the situation, including:

- reinstalling the nvidia 185.18.29 drivers
- installing the nvidia 185.18.31 drivers
- installing the nvidia 190.10 drivers
- reinstalling xorg
- reverting nvidia drivers back to 185.18.29
- reverting the nvidia drivers back to 180.60
- adding 'Option "NvAGP" "1"' to my xorg.conf file
- changing 'Option "NvAGP" "1"' to 'Option "NvAGP" "0"' (system won't boot)


Out of curiosity, what driver version were you running when you started having these problems?

---

### Post by ADI64 on 2010-02-10
I also had the problem with an AMD Phenom x4 9550, geforce 9600GT system.
Although I am NOT running Ubuntu (Arch Linux), I followed this topic a long time because I got similar (if not the same) problems.
```
    kernel: NVRM: Xid (0002:00): 6, PE0001

    kernel: hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

    kernel: NVRM: Xid (0002:00): 6, PE0001

    kernel: NVRM: Xid (0002:00): 6, PE0001

    kernel: NVRM: Xid (0002:00): 6, PE0001
```
and sometimes
```
    kernel: NVRM: Xid (0002:00): 8, Channel 00000002

    kernel: NVRM: Xid (0002:00): 13, 0002 00000000 00005039 00000328 00000000 00000002

    kernel: NVRM: Xid (0002:00): 13, 0002 00000000 00005039 00000328 00000000 00000002

    kernel: NVRM: Xid (0002:00): 13, 0002 00000000 00005039 00000328 00000000 00000002

    kernel: NVRM: Xid (0002:00): 13, 0002 00000000 00005039 00000328 00000000 00000002

    kernel: NVRM: Xid (0002:00): 13, 0002 00000000 00005039 00000328 00000000 00000002

    kernel: NVRM: Xid (0002:00): 13, 0002 00000000 00005039 00000328 00000000 00000002

    kernel: NVRM: Xid (0002:00): 13, 0002 00000000 00005039 00000328 00000000 00000002

    kernel: X[4009]: segfault at 8 ip 00007f7e6cdae4bf sp 00007fff6b14e130 error 4 in nvidia_drv.so[7f7e6cd64000+3ac000]
```
I sent my card back and they acknowledged that the card was broken and I got my money back.
Right now I am only using the chipset graphics (nvidia geforce 8200gt) which is enough for videos and stuff.
I plan to buy a geforce gt240, but I'm not sure yet.
Although ATI/AMD offers better cards for the same money, I've heard of a lot trouble running their cards under linux so I think I will stick to nVidia.
I don't know the driver version I used in Linux the past months, but I always upgraded to the newest available driver in hope for a fix.

---

### Post by lexe-cc on 2010-02-16
I'm having the same problem. First i thought it was my power supply. After replacing it with a more powerful one, i got the crash quite fast. I sure hope its not my graphics card ..

Anyone has a fix for this?

thx

---

### Post by koma77 on 2010-03-17
I'm starting to think that I have a hardware problem as well. Either the gfx-card is broken or there is something wrong with the motherboard (or interopability).

The reason is that I now also have a problem in Windows. It used to be only Linux (Xid 13). I ran a GPU stress test software in Windows and sure enough: the whole computer froze.

It also crashes some of the games in Windows, but not all. (Not Call of Duty 6 for example...)

I don't know what to do really besides buying another card...

---

### Post by lakakid on 2010-03-17
Iam new to ubuntu!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by KIAaze on 2010-03-26
I've been having the same problem since last year.
But it seems to only happen when desktop effects are enabled.

I get messages like these in /var/log/syslog:
```
Mar 26 17:21:46 my-desktop kernel: [ 2714.595869] NVRM: Xid (0001:00): 13, 0001 00000000 00000000 00000000 00000000 00000080
Mar 26 17:21:52 my-desktop kernel: [ 2720.718343] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 000015e0 00000000 00000040
Mar 26 17:21:52 my-desktop kernel: [ 2720.741738] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 00000538 3f800000 00000040
Mar 26 17:21:52 my-desktop kernel: [ 2720.760177] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 00000538 3f800000 00000040
Mar 26 17:21:52 my-desktop kernel: [ 2720.802030] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 000015e0 00000000 00000040
Mar 26 17:21:52 my-desktop kernel: [ 2720.825575] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 00000538 3f800000 00000040
Mar 26 17:21:59 my-desktop kernel: [ 2727.853704] NVRM: Xid (0001:00): 13, 0004 00000000 00008397 00000f08 00000000 00000040
Mar 26 17:21:59 my-desktop kernel: [ 2728.180598] NVRM: Xid (0001:00): 13, 0003 00000000 00008397 00001310 00000000 00000040

```

It doesn't really freeze. It just garbles the screen. Music continues to run, virtual consoles are still accessible.

---

### Post by koma77 on 2010-03-28
I got a new batch of Xids today, they look a lot like KIAaze's:

[ 4297.745025] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 00000f04 3f800000 00000080
[ 4311.541807] NVRM: Xid (0001:00): 8, Channel 00000003
[ 4311.547909] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 0000194c 00000000 00000100
[ 4311.565426] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 0000194c 00000000 00000040
[ 4311.582778] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 00000538 3f800000 00000040
[ 4311.600954] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 0000194c 00000000 00000100
[ 4311.620672] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 0000194c 00000000 00000040
[ 4311.641178] NVRM: Xid (0001:00): 13, 0001 00000000 00008397 00000100 00000000 00000100

I tried stressing the card by playing openarena, but that works OK.
Does anyone know if there is another way of stressing the graphics card in linux?

---

### Post by rookcifer on 2010-09-07
Here I go resurrecting this thread, but I am having the same problem on Lucid with an Nvidia GTS 250 with the latest Ubuntu repo Nvidia driver.  What happens is my screen will go black and I am logged out of X automatically.  This only happens when I am scrolling my mouse (with the wheel) inside of a browser, so there is definitely some bug in the way Xorg handles mouse scrolling input along with the Nvidia drivers.

 Here's the only error I could find in the logs:

```
kernel: [495014.043715] NVRM: Xid (0002:00): 6, PE0001 
```

Obviously reporting a bug on launchpad wont do any good since Canonical has no control over Nvidia and their binary blob drivers, but I thought I'd vent anyway.

---

### Post by grappler on 2010-09-16
Running maverick 64bit on a thinkpad 410 with discrete (nvidia) graphics.  

I'm not sure if this is related but I'm getting random freezes of the cursor, of the (button) mouse,  and of ability to input to a text window from the keyboard. It seems that X freezes for periods of up to about a minute.  

tail /var/log/messages shows the following message repeated about fairly frequently - especially after opening a new window.

NVRM: os_raise_smp_barrier(), invalid context!

This is making the machine essentially unusable.

---

### Post by waperboy on 2010-09-20
I just had this bug start happening to me yesterday.
(Yesterday I built a new computer)

My old computer:
MB: Asus P5W DH Deluxe
CPU: Core 2 Duo E6600
RAM: 4x1 Gb Corsair whatever
Asus nvidia 8800GT card

New computer:
MB: Asus P6T SE
CPU: Core i7 930
RAM: 6x2Gb Corsair XMS3 1333MHz
Same Asus nvidia 8800GT card

Same ubuntu 9.10 64-bit installation on same HD, thus obviously same nvidia driver too, (185.18.36).

On the old, everything worked fine. Getting the NVRM Xid logs with black screen and frozen computer with the new setup. Same nvidia card.

Forced it to happen now by playing QuakeLive.
In syslog:

kernel: [11144.963412] NVRM: Xid (0002:00): 6, PE007f 
kernel: [11144.965148] NVRM: Xid (0002:00): 7, Ch 0000007f M 00001ffc D ffffffff intr ffffffff
kernel: [11144.966874] NVRM: Xid (0002:00): 26, Ch 0000007f M 00001ffc D ffffffff intr ffffffff
kernel: [11144.968600] NVRM: Xid (0002:00): 4, Ch 00000005 acquireValue 11111111 dmaPut 2004be6c dmaGet 2004be6c 

Here the game paused for a second, then continued. After 25 seconds, full lockup, screen goes black. Syslog:

kernel: [11170.422373] NVRM: Xid (0002:00): 6, PE007f 
kernel: [11170.425820] NVRM: Xid (0002:00): 7, Ch 0000007f M 00001ffc D ffffffff intr ffffffff
kernel: [11170.429223] NVRM: Xid (0002:00): 26, Ch 0000007f M 00001ffc D ffffffff intr ffffffff
kernel: [11181.488364] NVRM: Xid (0002:00): 8, Channel 00000005

So something with the new MB/CPU combo causing the lockups.

---

### Post by waperboy on 2010-09-20
Switching the cpu to only 1 core (by disabling ACPI in BIOS) made the problem go away, but not exactly a solution...

EDIT: Not really, it just didn't freeze during QuakeLive or glxgears. Glxgears would crash it almost immediately with all cores enabled, time after time, but ran fine with 1 core.
Now with 1 core it started finally to slow down then freeze when scrolling in web browser :(

---

### Post by waperboy on 2010-09-21
Enabling "Sync to VBlank" in nvidia-settings OpenGL Settings seems to have removed the problem. Running Starcraft II in a window (in Wine), glxgears, and playing a video simultaneously now for 30 minutes, plus playing QuakeLive, and switching desktops with Compiz Fusion 3D cube like crazy, with nothing in the syslog and no problems.

EDIT: Prior to this, I had updated the nVidia driver to 256.53, and still had problems (glxgears always forced it to manifest)

---

### Post by waperboy on 2010-10-02
The freezes still occured after that.

Replaced the 8800GT with a GTX 460, and the problem is now completely gone!

(I did also replace the power supply unit - the old one only had the 4-pin 12V motherboard connector, the new one has the 8-pin one)

---

### Post by Sergio_1212 on 2010-10-05
hello, I have de same problem, but a few diferente. My Xubuntu Lucid (xfce) give me similar syslog and freeze

```
Oct  5 22:46:36 ERRi kernel: [ 2399.644043] NVRM: Xid (0001:00): 8, Channel 00000000
Oct  5 22:46:37 ERRi kernel: [ 2400.644032] NVRM: Xid (0001:00): 16, Head 00000000 Count 00045648
Oct  5 22:46:45 ERRi kernel: [ 2408.643954] NVRM: Xid (0001:00): 8, Channel 0000001e
Oct  5 22:46:45 ERRi kernel: [ 2408.647633] NVRM: Xid (0001:00): 16, Head 00000000 Count 00045649
```My problem began when I installed the sound card  Asus Xonar DX in the pci-express, before, no problems, but now it freeze and I reboot with REISUB. Mi grafic are Nvidia 7300GS. Curiosly, the system work perfect in the backup what I create whit remastersys in July, a few month before, my system doesn't freeze, but when I [COLOR=#000000]update[/COLOR] the system slowly, when I instaled the packages listed below, [COLOR=#000000]the problem appears again

[/COLOR]```
bogofilter_1.2.1-0ubuntu1.1_i386.deb
bogofilter-bdb_1.2.1-0ubuntu1.1_i386.deb
bogofilter-common_1.2.1-0ubuntu1.1_all.deb
bzip2_1.0.5-4ubuntu0.1_i386.deb
fglrx-modaliases_2%3a8.771-0ubuntu0sarvatt~lucid_i386.deb
gimp_2.6.11-1~getdeb1_i386.deb
gimp-data_2.6.11-1~getdeb1_all.deb
icedtea-6-jre-cacao_6b18-1.8.1-0ubuntu1_i386.deb
icedtea6-plugin_6b18-1.8.1-0ubuntu1_i386.deb
lftp_4.0.2-1ubuntu0.1_i386.deb
libbz2-1.0_1.0.5-4ubuntu0.1_i386.deb
libfreetype6_2.3.11-1ubuntu2.2_i386.deb
libgimp2.0_2.6.11-1~getdeb1_i386.deb
libldap-2.4-2_2.4.21-0ubuntu5.3_i386.deb
libpcsclite1_1.5.3-1ubuntu4.1_i386.deb
libservlet2.5-java_6.0.24-2ubuntu1.3_all.deb
libsmbclient_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb
libssl0.9.8_0.9.8k-7ubuntu8.1_i386.deb
linux-libc-dev_2.6.32-25.44_i386.deb
openjdk-6-jre_6b18-1.8.1-0ubuntu1_i386.deb
openjdk-6-jre-headless_6b18-1.8.1-0ubuntu1_i386.deb
openjdk-6-jre-lib_6b18-1.8.1-0ubuntu1_all.deb
openssl_0.9.8k-7ubuntu8.1_i386.deb
thunderbird_3.0.8+build2+nobinonly-0ubuntu0.10.04.1_i386.deb

```I speak Spanish, my English is short but sufficient for understand the respons. Thanks for the compression. i will wite in xorg this
[http://www.nvnews.net/vbulletin/showpost.php?p=1215445&postcount=7](http://www.nvnews.net/vbulletin/showpost.php?p=1215445&postcount=7)
, if that is the solution I will write again

---

### Post by koma77 on 2010-10-06
I can just add that my problems were hardware related as well.
So these Xid freezes is likely to be hardware related problems.

In my case, my graphics card was in contact with another part of the computer case. The physical contact made this problem appear at times.
Changing the computer case made the problem go away completely.

---

### Post by waperboy on 2010-10-06
> **koma77 said:**
> I can just add that my problems were hardware related as well.
So these Xid freezes is likely to be hardware related problems.

In my case, my graphics card was in contact with another part of the computer case. The physical contact made this problem appear at times.
Changing the computer case made the problem go away completely.

Funny I was quite convinced that the problem was with the nVidia driver the whole time, but I guess I was wrong - one factor could have been the bad state of the fan on the 8800GT - it was hard to turn and spun very slowly.

---

### Post by Sergio_1212 on 2010-10-06
My xonar DX have a PCI Express-to-PCI Bridge,  grafic and Xonar are together. If my problem doesn't disappear i will remove the Xonar and I will observe if the problem persist

---

### Post by Sergio_1212 on 2010-10-06
if the driver Nouveau have the the same problem, the problem i belive what no depend of the driver, but yes depend of the other packages. In my case with the two drivers I had the same error. When I update the packages listed above, the problem appear, before the problems not appeared .I reinstall my custom ubuntu and will observe

---

### Post by tiz29 on 2010-10-11
"NVRM: os_raise_smp_barrier(), invalid context!"
10.10 with Nvidia gt320
I solve if i set powermizer in nvidia server settings to "Prefer Maximum Performance".
The problem: change lost after reboot:(

---

### Post by Sergio_1212 on 2010-10-13
in debian lenny no problems with the latest drivers, i confirm this, the problem i belive what no depend of the driver

---

