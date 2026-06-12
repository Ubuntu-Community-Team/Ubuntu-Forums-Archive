---
title: "Making a server install on a laptop(!) usable"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by dutch_gecko on 2007-04-21
Before I start the meat:

Yes I know I'm utterly mad.


I have here in my hands an Iridium Starbook 510, complete with 1GHz Pentium 3, and 128MB of RAM. It's a bit of an old bugger, and liking a challenge I decided to go for a stripped down install without a desktop environment. Since only the server install comes without one, I went with that and hoped for the best.

I managed to set up most things for the Feisty install as I went along. X works, GDM works, Blackbox is up and smooth as anything. I have firefox (and flash 9!). Sound works with Alsa. Got myself rxvt-unicode as a very lightweight terminal. GTK 2 works. I've got most of the apps I want.

What bothers me at the moment is that the thing still isn't mobile. I've managed to install ACPI, and it's reporting data to my docker app (wmbattery), but at the moment the thing still runs hot and the hard drive is pretty inefficient, since its speed-up and slow-down is managed by the BIOS without any kind of optimisation.

I don't really know where to turn from here. I've been trying to understand laptop-mode but I don't think I do. Also, I'm unable to scale the CPU speed.

After this I'm hoping to get suspend to RAM and perhaps even hibernate working.


I've also installed the generic kernel instead of the server kernel, can't say I notice any differences though.

So, to summarise:
CPU frequency scaling
Hard drive control
Integrate into laptop-mode or similar
Suspend
Hibernate


And now for some rather large pastes from the command line.

```
gecko@craptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 630 Host (rev 31)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0a.0 CardBus bridge: Texas Instruments PCI4410 PC card Cardbus Controller (rev 02)
00:0a.1 FireWire (IEEE 1394): Texas Instruments PCI4410 FireWire Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)

```

```
gecko@craptop:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 10
cpu MHz         : 997.005
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1995.28
clflush size    : 32

```

```
gecko@craptop:/proc$ cat modules
freq_table 5792 0 - Live 0xc8049000
sis 8576 2 - Live 0xc8035000
drm 81044 3 sis, Live 0xc8097000
tc1100_wmi 8068 0 - Live 0xc802c000
pcc_acpi 13184 0 - Live 0xc8012000
sony_acpi 6284 0 - Live 0xc800c000
dev_acpi 12292 0 - Live 0xc801b000
video 16388 0 - Live 0xc8022000
battery 10756 0 - Live 0xc8017000
container 5248 0 - Live 0xc800f000
sbs 15652 0 - Live 0xc7cf9000
button 8720 0 - Live 0xc8008000
i2c_ec 5888 1 sbs, Live 0xc8005000
dock 10268 0 - Live 0xc7ee2000
ac 6020 0 - Live 0xc7edf000
asus_acpi 17308 0 - Live 0xc7ee6000
backlight 7040 1 asus_acpi, Live 0xc7edc000
ipv6 268704 14 - Live 0xc8054000
fuse 46612 1 - Live 0xc7f07000
sbp2 23812 0 - Live 0xc7e81000
parport_pc 36388 0 - Live 0xc7e63000
lp 12452 0 - Live 0xc7e5e000
parport 36936 2 parport_pc,lp, Live 0xc7ed1000
joydev 10816 0 - Live 0xc7ecd000
snd_trident 44548 0 - Live 0xc7e9f000
gameport 16520 2 snd_trident, Live 0xc7e99000
snd_ac97_codec 98336 1 snd_trident, Live 0xc7eed000
ac97_bus 3200 1 snd_ac97_codec, Live 0xc7cde000
snd_pcm_oss 44544 0 - Live 0xc7ec1000
snd_mixer_oss 17408 1 snd_pcm_oss, Live 0xc7e93000
snd_pcm 79876 3 snd_trident,snd_ac97_codec,snd_pcm_oss, Live 0xc7eac000
snd_page_alloc 10888 2 snd_trident,snd_pcm, Live 0xc7e17000
snd_util_mem 5760 1 snd_trident, Live 0xc7e39000
snd_mpu401_uart 9472 1 snd_trident, Live 0xc7e7d000
snd_seq_dummy 4740 0 - Live 0xc7e36000
snd_seq_oss 32896 0 - Live 0xc7e89000
pcmcia 39212 0 - Live 0xc7e53000
snd_seq_midi 9600 0 - Live 0xc7e32000
snd_rawmidi 25472 2 snd_mpu401_uart,snd_seq_midi, Live 0xc7e4b000
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi, Live 0xc7e1b000
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xc7e6f000
serio_raw 7940 0 - Live 0xc7bc5000
snd_timer 23684 2 snd_pcm,snd_seq, Live 0xc7e2b000
snd_seq_device 9100 6 snd_trident,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xc7e13000
snd 54020 11 snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xc7e3c000
pcspkr 4224 0 - Live 0xc7cf6000
psmouse 38920 0 - Live 0xc7e20000
yenta_socket 27532 1 - Live 0xc7e00000
rsrc_nonstatic 14080 1 yenta_socket, Live 0xc7dfb000
pcmcia_core 40852 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xc7e08000
soundcore 8672 1 snd, Live 0xc7cf0000
shpchp 34324 0 - Live 0xc7df1000
pci_hotplug 32576 1 shpchp, Live 0xc7dd7000
sis_agp 9604 1 - Live 0xc7cda000
agpgart 35400 2 drm,sis_agp, Live 0xc7dcd000
i2c_sis630 8588 0 - Live 0xc7be8000
i2c_core 22784 2 i2c_ec,i2c_sis630, Live 0xc7ce9000
af_packet 23816 2 - Live 0xc7ce2000
tsdev 8768 0 - Live 0xc7be4000
evdev 11008 0 - Live 0xc7be0000
reiserfs 247680 1 - Live 0xc7cfe000
sg 36252 0 - Live 0xc7c48000
sr_mod 17060 0 - Live 0xc7c24000
cdrom 37664 1 sr_mod, Live 0xc7c31000
sd_mod 23428 3 - Live 0xc7c1d000
generic 5124 0 [permanent], Live 0xc7bcb000
sis5513 14856 0 [permanent], Live 0xc7c10000
ohci1394 36528 0 - Live 0xc7bd1000
ieee1394 299448 2 sbp2,ohci1394, Live 0xc7c6d000
ohci_hcd 22532 0 - Live 0xc7871000
usbcore 134280 2 ohci_hcd, Live 0xc7bee000
sis900 24704 0 - Live 0xc7869000
mii 6528 1 sis900, Live 0xc785d000
pata_sis 14220 2 - Live 0xc7858000
ata_generic 9092 0 - Live 0xc783e000
libata 125720 2 pata_sis,ata_generic, Live 0xc7ba5000
scsi_mod 142348 5 sbp2,sg,sr_mod,sd_mod,libata, Live 0xc7b81000
thermal 14856 0 - Live 0xc7844000
processor 31048 1 thermal, Live 0xc7849000
fan 5636 0 - Live 0xc783b000
capability 5896 0 - Live 0xc782a000
commoncap 8192 1 capability, Live 0xc7827000
vesafb 9220 1 - Live 0xc7819000
fbcon 42656 72 - Live 0xc782f000
tileblit 3584 1 fbcon, Live 0xc7821000
font 9216 1 fbcon, Live 0xc781d000
bitblit 6912 1 fbcon, Live 0xc7802000
softcursor 3200 1 bitblit, Live 0xc7805000

```

```
gecko@craptop:/proc/acpi$ ls -l
total 0
dr-xr-xr-x 3 root root 0 2007-04-21 06:19 ac_adapter
-rw-r--r-- 1 root root 0 2007-04-21 06:19 alarm
dr-xr-xr-x 3 root root 0 2007-04-21 06:19 battery
dr-xr-xr-x 4 root root 0 2007-04-21 06:19 button
-r-------- 1 root root 0 2007-04-21 06:19 dsdt
dr-xr-xr-x 3 root root 0 2007-04-21 06:19 embedded_controller
-r-------- 1 root root 0 2007-04-21 04:51 event
-r-------- 1 root root 0 2007-04-21 06:19 fadt
dr-xr-xr-x 2 root root 0 2007-04-21 06:19 fan
-r--r--r-- 1 root root 0 2007-04-21 06:19 info
dr-xr-xr-x 4 root root 0 2007-04-21 06:19 power_resource
dr-xr-xr-x 3 root root 0 2007-04-21 06:19 processor
-rw-r--r-- 1 root root 0 2007-04-21 06:19 sleep
dr-xr-xr-x 2 root root 0 2007-04-21 06:19 sony
dr-xr-xr-x 2 root root 0 2007-04-21 06:19 thermal_zone
dr-xr-xr-x 2 root root 0 2007-04-21 06:19 video
-rw-r--r-- 1 root root 0 2007-04-21 06:19 wakeup
dr-xr-xr-x 2 root root 0 2007-04-21 06:19 wmi

```

```
gecko@craptop:/sys/devices/system/cpu/cpu0$ ls
crash_notes  topology

```

```
gecko@craptop:/proc/acpi/processor/CPU0$ ls
info  limit  power  throttling

```

```
gecko@craptop:/proc/acpi/processor/CPU0$ cat info
processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        yes
throttling control:      yes
limit interface:         yes

```

```
gecko@craptop:/proc/acpi/processor/CPU0$ cat limit
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0

```

```
gecko@craptop:/proc/acpi/processor/CPU0$ cat power
active state:            C2
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 4353 usec
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000460] duration[00000000000000000000]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[002] usage[01425956] duration[00000000019463681581]

```

```
gecko@craptop:/proc/acpi/processor/CPU0$ cat throttling 
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

```



That's what I can think of posting for now... I hope I haven't inundated you with useless information.

So, many thanks in advance for whatever light you can shed on the matter, and I promise never to do something as backwards as this ever again. And in case you're wondering, yes that really is the hostname.

---

### Post by kidders on 2007-04-22
Hi there,

Your post is a little confusing. :confused: You mentioned that you intentionally installed Ubuntu without a graphical environment, but then you seem to describe putting GDM, Firefox, etc. on it. Additionally, I would be frankly horrified if a Linux install designed for use on servers made any attempt whatsoever to use CPU frequency scaling, hibernation, and so on, out of the box.

Perhaps you could describe what you want to achieve. I can try to help you find the best way of getting there.

---

### Post by dutch_gecko on 2007-04-22
Hey

The reason I got the server edition was because it came without an environment, since an environment would drastically bog the laptop down and I never use one anyway (just blackbox). Of course, it comes without a lot of other stuff, but I assumed that with the help of apt I could simply add back everything to turn this into an ordinary laptop.

This has worked fine up to now - I've installed X, followed by blackbox and gdm, and can run any apps I like. Knowing that the server kernel wouldn't support things like frequency scaling I installed and am now running the generic kernel.

Just to clarify, I have no intention of running this as a server - I want it to be a totally mobile laptop.

---

### Post by pelikan on 2007-04-22
I'm going to bump this because I'm in a very similar boat.

---

### Post by kidders on 2007-04-23
> **dutch_gecko said:**
> Of course, it comes without a lot of other stuff, but I assumed that with the help of apt I could simply add back everything to turn this into an ordinary laptop.

> **pelikan said:**
> I'm going to bump this because I'm in a very similar boat.

Turning all the things dutch_gecko mentioned on is basically a matter of following a bunch of HOTWOs (quite a few of them :-( ). I suppose users who want something _between_ a desktop Ubuntu and a server Ubuntu wind up having to decide which approach is easier: Starting with a desktop and getting rid of stuff, or starting with a server and adding stuff on.

In dutch_gecko's case, particularly since he's (by the sound of it) using a custom kernel, enabling features like hibernation & suspension could be a little finicky. Also, laptop users need to be very careful not to damage their hardware, when fiddling with kernels & power-related stuff.

Anyhow, I hate suggesting this, but do either of you suppose it might be easier to start again with a desktop Ubuntu install?

---

