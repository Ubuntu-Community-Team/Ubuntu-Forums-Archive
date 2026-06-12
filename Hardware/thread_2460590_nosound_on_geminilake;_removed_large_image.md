---
title: "nosound on geminilake; removed large image"
date: 2021-04-14
forum: Hardware
---

### Post by jfdesign on 2021-04-14
Hello,

I installed xubuntu groovy 20.10 on my Gemini Lake laptop with N4020 Intel CPU. it recognized everything including wifi  and bluetooth, but the problem is I haven't had audio at all. (same also with daily build hirsute xubuntu with kernel 5.11.0-13). Dead  silent.
```
[FONT=monospace][COLOR=#54ff54]**user@geminilake-4020**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ inxi -Fz  [/COLOR]
[COLOR=#5454ff]**System:    Kernel:**[/COLOR][COLOR=#000000] 5.8.0-25-generic x86_64 [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**Desktop:**[/COLOR][COLOR=#000000] Xfce 4.14.2 [/COLOR][COLOR=#5454ff]**Distro:**[/COLOR][COLOR=#000000] Ubuntu 20.10 (Groovy Gorilla)  [/COLOR]
[COLOR=#5454ff]**Machine:   Type:**[/COLOR][COLOR=#000000] Laptop [/COLOR][COLOR=#5454ff]**System:**[/COLOR][COLOR=#000000] Axioo [/COLOR][COLOR=#5454ff]**product:**[/COLOR][COLOR=#000000] Mybook 14_G [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Mobo:**[/COLOR][COLOR=#000000] N/A [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] P401 [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454ff]**UEFI:**[/COLOR][COLOR=#000000] American Megatrends [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] $(AMI_ROM_NAME)_T$(2021)$(02)$(26)$(15)$(08)  [/COLOR]
           [COLOR=#5454ff]**date:**[/COLOR][COLOR=#000000] 02/26/2021  [/COLOR]
[COLOR=#5454ff]**Battery:   ID-1:**[/COLOR][COLOR=#000000] BAT0 [/COLOR][COLOR=#5454ff]**charge:**[/COLOR][COLOR=#000000] 34.2 Wh [/COLOR][COLOR=#5454ff]**condition:**[/COLOR][COLOR=#000000] 34.2/34.2 Wh (100%)  [/COLOR]
[COLOR=#5454ff]**CPU:       Info:**[/COLOR][COLOR=#000000] Dual Core [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] Intel Celeron N4020 [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] MCP [/COLOR][COLOR=#5454ff]**L2 cache:**[/COLOR][COLOR=#000000] 4096 KiB  [/COLOR]
           [COLOR=#5454ff]**Speed:**[/COLOR][COLOR=#000000] 1133 MHz [/COLOR][COLOR=#5454ff]**min/max:**[/COLOR][COLOR=#000000] 800/2800 MHz [/COLOR][COLOR=#5454ff]**Core speeds (MHz):**[/COLOR][COLOR=#5454ff]**1:**[/COLOR][COLOR=#000000] 1083 [/COLOR][COLOR=#5454ff]**2:**[/COLOR][COLOR=#000000] 983  [/COLOR]
[COLOR=#5454ff]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] Intel UHD Graphics 605 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] i915 [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] icSpring icspring camera [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] uvcvideo  [/COLOR]
           [COLOR=#5454ff]**Display:**[/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.9 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] modesetting [/COLOR][COLOR=#5454ff]**unloaded:**[/COLOR][COLOR=#000000] fbdev,vesa [/COLOR][COLOR=#5454ff]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~60Hz  [/COLOR]
           [COLOR=#5454ff]**OpenGL:**[/COLOR][COLOR=#5454ff]**renderer:**[/COLOR][COLOR=#000000] llvmpipe (LLVM 11.0.0 128 bits) [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 4.5 Mesa 20.2.1  [/COLOR]
[COLOR=#5454ff]**Audio:     Device-1:**[/COLOR][COLOR=#000000] Intel Celeron/Pentium Silver Processor High Definition Audio [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] sof-audio-pci  [/COLOR]
           [COLOR=#5454ff]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] k5.8.0-25-generic  [/COLOR]
[COLOR=#5454ff]**Network:   Message:**[/COLOR][COLOR=#000000] No Device data found.  [/COLOR]
           [COLOR=#5454ff]**Device-1:**[/COLOR][COLOR=#000000] Realtek RTL8152 Fast Ethernet Adapter [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] r8152  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] enx00e04c6d543b [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] Realtek RTL8723BU 802.11b/g/n WLAN Adapter [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] btusb,rtl8xxxu  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] wlx3420036fa193 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
[COLOR=#5454ff]**Drives:    Local Storage:**[/COLOR][COLOR=#5454ff]**total:**[/COLOR][COLOR=#000000] 465.76 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 7.24 GiB (1.6%)  [/COLOR]
           [COLOR=#5454ff]**ID-1:**[/COLOR][COLOR=#000000] /dev/sda [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Western Digital [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] WD5000LQVX-22K6RT0 [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 465.76 GiB  [/COLOR]
[COLOR=#5454ff]**Partition: ID-1:**[/COLOR][COLOR=#000000] / [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 456.96 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 7.24 GiB (1.6%) [/COLOR][COLOR=#5454ff]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#5454ff]**dev:**[/COLOR][COLOR=#000000] /dev/sda2  [/COLOR]
[COLOR=#5454ff]**Swap:      ID-1:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] file [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 2.00 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 0 KiB (0.0%) [/COLOR][COLOR=#5454ff]**file:**[/COLOR][COLOR=#000000] /swapfile  [/COLOR]
[COLOR=#5454ff]**Sensors:   System Temperatures:**[/COLOR][COLOR=#5454ff]**cpu:**[/COLOR][COLOR=#000000] 52.0 C [/COLOR][COLOR=#5454ff]**mobo:**[/COLOR][COLOR=#000000] N/A  [/COLOR]
           [COLOR=#5454ff]**Fan Speeds (RPM):**[/COLOR][COLOR=#000000] N/A  [/COLOR]
[COLOR=#5454ff]**Info:      Processes:**[/COLOR][COLOR=#000000] 178 [/COLOR][COLOR=#5454ff]**Uptime:**[/COLOR][COLOR=#000000] 50m [/COLOR][COLOR=#5454ff]**Memory:**[/COLOR][COLOR=#000000] 7.59 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 928.8 MiB (11.9%) [/COLOR][COLOR=#5454ff]**Shell:**[/COLOR][COLOR=#000000] Bash [/COLOR][COLOR=#5454ff]**inxi:**[/COLOR][COLOR=#000000] 3.1.07[/COLOR]
[/FONT]
```

the pavucontrol shows only dummy output, the vumeter below the volume  slider is dancing when i play some audio but there is no sound at all  from the speaker.

[ATTACH=CONFIG]288315[/ATTACH]

the ouput from aplay -l shows card0 as all HDMI :
```

$ aplay -l
**** List of PLAYBACK Hardware Devices **** card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

the output from proc/asound shows :
```
$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xa1110000 irq 133
cat /proc/asound/card0/codec#2 | grep -i codec
Codec: Intel Geminilake HDMI
```

and lspci only show this for audio :
```
lspci -nn | grep -i audio
00:0e.0 Multimedia audio controller [0401]: Intel Corporation Celeron/Pentium Silver Processor High Definition Audio [8086:3198] (rev 06)

```

So far everything I tried from searching the solution is to no avail.
I already tried to set options for snd-hda-intel on etc/modprobe.d/alsa-base.conf with :
```
options snd-hda-intel dmic_detect=0
```

and blacklisting the snd_soc_skl on etc/modprobe.d/blacklist.conf
```
blacklist snd_soc_skl
```

do a reboot but still no sound from speaker and got dummy output at pavucontrol.

I also tried to set the vid/pid from lspci data above :
```
options snd-hda-intel index=0 model=auto vid=8086 pid=3198

```
still got dummy output as well

but when I change the primary to PCH then HDMI :

```
options snd-hda-intel id=PCH,HDMI enable=0,1
```

there is some slight change on aplay -l output as these : 
```
**** List of PLAYBACK Hardware Devices ****
card 0: sofhdadsp [sof-hda-dsp], device 1: HDMI1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 2: HDMI2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: sofhdadsp [sof-hda-dsp], device 3: HDMI3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
but unfortunately, still no sound, the pavucontrol still shows dummy output.

Furthermore,
The most confusing part is, when I tried asking the vendor about the audio driver, even though they don't have the linux driver, they gave me the audio driver for Windows platform, which says that the soundcard is ES8336 from everest audio.
I cannot grab the string es8336 or es8316 output at all from dmesg or lsmod. It brings me more headache ... :)


I've run out of an idea. Anybody here care to help ? Thank you very much in advance.

---

### Post by CelticWarrior on 2021-04-14
Welcome.

It has to be a very weird onboard audio device to not be recognized by the current Ubuntu. But there are other problems, at least the HDMI audio output should work, it's totally independent and part of the standard and fully open source supported Intel Graphics. Still, pavucontrol shows a dummy output only.

The above suggests incorrect settings at UEFI and/or problems during the SO installation. Have you by any chance installed in Legacy mode?

---

### Post by jfdesign on 2021-04-14
Hello,

yes, it's weird and yes, i'm installing at legacy mode. is that make any difference for the audio output result ?
thank you for reply CelticWarrior.

At the mean time, i stumbled across this post for es8316 by user shuncey :
[https://ubuntuforums.org/showthread.php?t=2391606](https://ubuntuforums.org/showthread.php?t=2391606)
and try to apply on my current install, it does compiled and finished, but it doesn't bring any smile. Looks like I have to get some rest now. :-)

---

### Post by CelticWarrior on 2021-04-14
> [COLOR=#000000]is that make any difference for the audio output result ?[/COLOR]
It may. 
Modern UEFI hardware requires UEFI mode for correct hardware initialization. Using Legacy in 2021 is an absurd. Why did you think it was a good idea? Legacy mode is for old BIOS machines.
This entry level Celerons usually need 1) UEFI mode, 2) Secure Boot disabled (optional but recommended), 3) Fast Boot disabled (optional but highly recommended), 4) OS selection, if present, set to "Linux", "Android", "Other", etc., anything but Windows 8/10... And, of course, assure that all onboard hardware enabled.

---

### Post by jfdesign on 2021-04-14
Okay,

I'll try after this with uefi mode.
Secure boot and Fastboot already set disabled, and for number 4. OS Selection also already set to Linux. 
HD-Audio configuration part that exist on Chipset -> South Cluster Configuration also already set to enabled.

Cheers

---

### Post by jfdesign on 2021-04-14
Hello again,

I have to reinstall somehow because I want to work from fresh install for this post. It's on uefi now, here is the fstab :

```
[FONT=monospace][COLOR=#000000]root@geminilake-4020:/home/user# cat /etc/fstab  [/COLOR]
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/sda2 during installation 
UUID=47660a94-c8c4-4008-a1d1-455eac2c7352 /               ext4    errors=remount-ro 0       1 
# /boot/efi was on /dev/sda1 during installation 
UUID=8A44-056D  /boot/efi       vfat    umask=0077      0       1 
/swapfile                                 none            swap    sw              0       0 
root@geminilake-4020:/home/user#
[/FONT]
```

but no luck on the audio, still show dummy output only on pavucontrol.

Cheers

---

### Post by schievel2 on 2021-07-31
Got the same problem with a new Jumper EZBook S5 with the same Intel N4020 Processor.
```
System:
  Kernel: 5.13.7-051307-generic x86_64 bits: 64 Desktop: GNOME 3.38.4 
  Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop System: Jumper product: EZbook v: N/A serial: <filter> 
  Mobo: Jumper model: N/A serial: <filter> UEFI: American Megatrends 
  v: GN10BV02 date: 02/04/2021 
Battery:
  ID-1: BAT0 charge: 26.6 Wh condition: 35.5/35.5 Wh (100%) 
CPU:
  Info: Dual Core model: Intel Celeron N4020 bits: 64 type: MCP 
  L2 cache: 4 MiB 
  Speed: 781 MHz min/max: 800/2800 MHz Core speeds (MHz): 1: 781 2: 784 
Graphics:
  Device-1: Intel GeminiLake [UHD Graphics 600] driver: i915 v: kernel 
  Device-2: Nebraska Furniture Mart USB 2.0 PC cam type: USB 
  driver: uvcvideo 
  Display: x11 server: X.Org 1.20.11 driver: loaded: modesetting 
  unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 600 (GLK 2) v: 4.6 Mesa 21.0.1 
Audio:
  Device-1: Intel Celeron/Pentium Silver Processor High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.13.7-051307-generic 
Network:
  Message: No Device data found. 
  Device-1: Realtek RTL8723BU 802.11b/g/n WLAN Adapter type: USB 
  driver: btusb,rtl8xxxu 
  IF: wlxa09f101057f6 state: up mac: <filter> 
Bluetooth:
  Device-1: Realtek RTL8723BU 802.11b/g/n WLAN Adapter type: USB 
  driver: btusb,rtl8xxxu 
  Report: ID: hci0 state: up running bt-v: 2.1 address: <filter> 
Drives:
  Local Storage: total: 236.24 GiB used: 17.12 GiB (7.2%) 
  ID-1: /dev/mmcblk0 vendor: Generic model: UY7CS0 size: 117 GiB 
  ID-2: /dev/sda vendor: Faspeed model: K7N-128GH size: 119.24 GiB 
Partition:
  ID-1: / size: 90.66 GiB used: 17.07 GiB (18.8%) fs: ext4 dev: /dev/sda4 
  ID-2: /boot/efi size: 96 MiB used: 48.8 MiB (50.8%) fs: vfat 
  dev: /dev/mmcblk0p1 
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 58.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 224 Uptime: 2h 33m Memory: 11.51 GiB used: 3.08 GiB (26.8%) 
  Shell: Bash inxi: 3.3.01 


```

I installed the newest mainline kernel because I thought maybe this one has the required drivers. But no luck.

So if someone has a solution, I would be really grateful.

---

### Post by rebu90 on 2021-11-24
Hi, i've got the same issue on a Teclast F5 (Intel Gemini Lake - N4100) running Ubuntu 21.10

Here's my Inxi output:
```
$ inxi -Fz
System:
  Kernel: 5.13.0-21-generic x86_64 bits: 64 Desktop: GNOME 40.5 
  Distro: Ubuntu 21.10 (Impish Indri) 
Machine:
  Type: Convertible System: TECLAST product: F5 v: N/A serial: <filter> 
  Mobo: TECLAST model: F5 serial: <filter> UEFI: TECLAST v: tPAD3.02 
  date: 04/25/2021 
Battery:
  ID-1: BAT0 charge: 22.1 Wh (83.1%) condition: 26.6/26.6 Wh (100.0%) 
CPU:
  Info: Quad Core model: Intel Celeron N4100 bits: 64 type: MCP cache: 
  L2: 4 MiB 
  Speed: 662 MHz min/max: 800/2400 MHz Core speeds (MHz): 1: 662 2: 756 
  3: 779 4: 959 
Graphics:
  Device-1: Intel GeminiLake [UHD Graphics 600] driver: i915 v: kernel 
  Device-2: SunplusIT MTD camera type: USB driver: uvcvideo 
  Display: wayland server: X.Org 1.21.1.2 driver: loaded: i915 
  note: n/a (using device driver) resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel UHD Graphics 600 (GLK 2) v: 4.6 Mesa 21.2.2 
Audio:
  Device-1: Intel Celeron/Pentium Silver Processor High Definition Audio 
  driver: snd_hda_intel 
  Sound Server-1: ALSA v: k5.13.0-21-generic running: yes 
  Sound Server-2: PulseAudio v: 15.0 running: yes 
  Sound Server-3: PipeWire v: 0.3.32 running: yes 
Network:
  Device-1: Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter 
  driver: rtw_8821ce 
  IF: wlp1s0 state: up mac: <filter> 
Bluetooth:
  Device-1: Realtek Bluetooth Radio type: USB driver: btusb 
  Report: hciconfig ID: hci0 state: up address: <filter> bt-v: 2.1 
Drives:
  Local Storage: total: 238.47 GiB used: 15.58 GiB (6.5%) 
  ID-1: /dev/sda vendor: Teclast model: BD256GB SLCB-2242 size: 238.47 GiB 
Partition:
  ID-1: / size: 233.18 GiB used: 15.57 GiB (6.7%) fs: ext4 dev: /dev/sda2 
  ID-2: /boot/efi size: 511 MiB used: 8.4 MiB (1.6%) fs: vfat dev: /dev/sda1 
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile 
Sensors:
  System Temperatures: cpu: 37.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 284 Uptime: 11m Memory: 7.6 GiB used: 3.13 GiB (41.2%) 
  Shell: Bash inxi: 3.3.06

```

Here's my aplay -l output:

```
$ aplay -l**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: PCH [HDA Intel PCH], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 9: HDMI 3 [HDMI 3]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: PCH [HDA Intel PCH], dispositivo 10: HDMI 4 [HDMI 4]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```


Even modifying the /etc/modprobe.d/alsa-base.conf file, it says "Dummy Output".

Setting the "options snd-hda-intel model=generic", aplay -l shows a slightly different configuration, HDMI/DisplayPort output seems to work but no analog at all (nor built-in speakers nor headphones). Same for analog input(s).

I'm getting sound only over Bluetooth or USB-C docking station (with 3.5mm jack) 

Thanks

Andrea

---

### Post by bobbysixkiller on 2021-11-28
Teclast F5, Same. ThX 4 BT. BT work. 
Speaker No.

Blacklist.conf 
          Blacklist snd_soc_skl
Alsabase.conf 
          Options snd-hda-intel model=auto

---

