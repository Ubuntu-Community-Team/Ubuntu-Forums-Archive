---
title: "lack of driver (probably) is causing waves on my screen but i don't remember"
date: 2020-02-21
forum: Hardware
---

### Post by ronjjjg8885 on 2020-02-21
how to install the graphic card driver.
doesn't it has to be automatically installed?

it is confusing.

anyhow this is the output of lspci. i've heard it is needed for helping me with the driver installation
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 2187 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 1aeb (rev a1)
01:00.2 USB controller: NVIDIA Corporation Device 1aec (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation Device 1aed (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 USB controller: VIA Technologies, Inc. VL805 USB 3.0 Host Controller (rev 01)

```

please don't write me complicated instructions because i don't understand.. and if you are angry at me don't help

thank you!

ubuntu 19.10

---

### Post by CelticWarrior on 2020-02-21
> **ronjjjg8885 said:**
> how to install the graphic card driver.
doesn't it has to be automatically installed?

It depends.

[LIST]
[*]**Intel Graphics** are supported by open-source drivers, included in the installation, no user actions required. (this is applicable in your case). 
[*]**AMD Graphics** are now also typically supported by open-source drivers. However, some models may require and additional PPA for better results (This NOT aaplicable in your case) 
[*]**Nvidia Graphics** need manual installation (this is applicable in your case) 
[/LIST]

Considering the aforementioned situations we know:
[LIST=1]
[*]Drivers for your IGPU (integrated) Intel are already installed. 
[*]In order to install the drivers fort your Nvidia Graphics please open Additional Drivers, select and install the recommended version. (Disable SEcure Boot in UEFI if applicable). Reboot. 
[/LIST]

it can't be simpler than that :P
Enjoy.


PS - I'm not mad at you but, honestly... You're asking the exact same question repeatedly and after other people tried to help with the same information I just gave and links, etc. not even once you gave feedback or thanked who were helping you. I'm sure you agree this isn't proper.

---

### Post by him610 on 2020-02-21
Looks as if you have two graphics chips. Don't know if that is your issue or not. Not familiar with Nvidia Device 2187.
```

....
00:02.0 VGA compatible controller: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06)
....
01:00.0 VGA compatible controller: NVIDIA Corporation Device 2187 (rev a1)
....

```
How about showing the results of* inxi -Fxz* between the code tags.

---

### Post by ronjjjg8885 on 2020-02-22
thank you for assisting!

[ATTACH=CONFIG]285067[/ATTACH]{there where no opions to choose from in 'Additional Drivers'.}

i've installed inxi after being asked to and this is the results.
```
inxi -Fxz
System:
  Host: ron-DESKTOP Kernel: 5.3.0-40-generic x86_64 bits: 64 compiler: gcc 
  v: 9.2.1 Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Desktop Mobo: Gigabyte model: H81M-S2H v: x.x serial: <filter> 
  UEFI: American Megatrends v: F1 date: 08/19/2014 
CPU:
  Topology: Dual Core model: Intel Core i3-4160 bits: 64 type: MT MCP 
  arch: Haswell rev: 3 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 28735 
  Speed: 2019 MHz min/max: 800/3600 MHz Core speeds (MHz): 1: 1611 2: 1604 
  3: 1566 4: 1590 
Graphics:
  Device-1: Intel 4th Generation Core Processor Family Integrated Graphics 
  vendor: Gigabyte driver: i915 v: kernel bus ID: 00:02.0 
  Device-2: NVIDIA vendor: Gigabyte driver: nouveau v: kernel 
  bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.5 driver: nouveau 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: llvmpipe (LLVM 9.0 256 bits) v: 3.3 Mesa 19.2.8 
  direct render: Yes 
Audio:
  Device-1: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio 
  driver: snd_hda_intel v: kernel bus ID: 00:03.0 
  Device-2: Intel 8 Series/C220 Series High Definition Audio 
  vendor: Gigabyte driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-3: NVIDIA vendor: Gigabyte driver: snd_hda_intel v: kernel 
  bus ID: 01:00.1 
  Sound Server: ALSA v: k5.3.0-40-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Gigabyte driver: r8169 v: kernel port: d000 bus ID: 03:00.0 
  IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.14 TiB used: 10.01 GiB (0.9%) 
  ID-1: /dev/sda vendor: Crucial model: CT250BX100SSD1 size: 232.89 GiB 
  temp: 26 C 
  ID-2: /dev/sdb vendor: Seagate model: ST1000DM003-1ER162 size: 931.51 GiB 
  temp: 30 C 
Partition:
  ID-1: / size: 149.13 GiB used: 9.98 GiB (6.7%) fs: ext4 dev: /dev/sda6 
Sensors:
  System Temperatures: cpu: 36.0 C mobo: N/A gpu: nouveau temp: 29 C 
  Fan Speeds (RPM): N/A gpu: nouveau fan: 1544 
Info:
  Processes: 265 Uptime: 1d 11h 47m Memory: 7.66 GiB used: 3.57 GiB (46.5%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.2.1 Shell: bash v: 5.0.3 
  inxi: 3.0.36 


```

by the way. i forgotten that i've asked a similar question. i wanted to mention that there is a chance i've asked but remembered to do so too late at night.

please keep being simple because i'm not very good with the terminal and linux installations
i don't want to be given too many ideas because it can be confusing

---

### Post by CelticWarrior on 2020-02-22
Can you please check, in the "Ubuntu Software" tab, that you have all the options (software repositories) checked? Source code isn't required though. I suspect you are missing one or more.

And also, before further troubleshooting, please open the UEFI ("BIOS") settings and disable Secure Boot.

---

### Post by ronjjjg8885 on 2020-02-22
i've entered to "Ubuntu Software" but there was no such thing as "repositories" there so i entered to "software and updates".
i'm uploading a screenshot.
do you mean that i need to activate the checkbox in the picture?[ATTACH=CONFIG]285069[/ATTACH]

i will try to enter the bios now for the UEFI setting that you have metioned,

:)

---

### Post by ronjjjg8885 on 2020-02-22
i've entered to the bios but could not figure out where does the UEFI setting is located.
here is a screenshot of the bios categories. i guess it's not being done in this box, right?[ATTACH=CONFIG]285070[/ATTACH]

---

### Post by CelticWarrior on 2020-02-22
All the option in Ubuntu Software as well as in Other Software are software repositories. I told you to open Ubuntu Software in order to check if all of them except source code were selected and if not, to select them. The repository in Other Software is optional but there's no harm in selecting it, but it has nothing to do with your missing drivers in Additional Drivers.

Another thing you should learn is that UEFI replaced the 40 years old BIOS a long time ago. Unfortunately many vendors still mention BIOS and it is confusing for no good reason except the familiarity with the old and now wrong terminology.

Like the old BIOS, the new UEFI is also vendor specific, there's no standard. Knowing your way around your hardware should be your homework. We can tell you what to as I did but how and where to do it is for you to find out. But I did it for you anyway... According to the page 24 of your user manual there's a few settings not shown in your screenshot. Scrolling down you should find **Windows 8 Features** and the value there should be **Other OS** (this is a weird way to say "disable Secure Boot"). Again, Secure Boot should be disabled because it prevents loading certain drivers even if correctly installed. I see also Fast Boot enabled. Generally it's recommended to disable that as well.

---

### Post by him610 on 2020-02-23
There is a setting in your Bios/Euve where you can select the PCIE graphics device over the integrated graphics device. You should locate that setting, and change as desired. This is from page 27 of your GA-H81M-S2H User's Manual Rev. 1002 12ME-H81M2H-1002R,
> Initial Display Output
Specifies the first initiation of the monitor display from the installed PCI Express graphics card or the onboard
graphics.
IGFX Sets the onboard graphics as the first display.
PCIe 1 Slot Sets the graphics card on the PCIEX16 slot as the first display. (Default)

---

### Post by ronjjjg8885 on 2020-02-23
oh
this icon also called ubuntu software (see attached image) so i got confused.

and yes. they were enabled (see the second image)

thanks for the explanation about the UEFI.
i was actually did tried to you a search engine but didn't find the answer as like you have mentioned... it is different in each model. and i didn't knew my exact model. i thought that all gygabye motherboards are similar.

now i will reboot and try your suggestions and [**him610**]("https://ubuntuforums.org/member.php?u=248298")'s suggestion too.
thank you!

edit:
i will update you later on.

---

### Post by CelticWarrior on 2020-02-23
Excellent, you're on the right track.

Pay special attention to him610's suggestion as this is something I forgot and is likely to be the main reason* why no drivers where suggested in Additional Drivers.

Why did I forget such important detail? Well, the vast majority of cases requiring help with Nvidias are laptops with hybrid graphics. In those, regardless of the graphics in use, both the iGPU and the dGPU (Nvidia) are always presented to the system. But in desktops is different: Unless a very specific option for multi-monitor or similar is present and active, only the selected (in BIOS/UEFI) graphics will show up, the other will simply be ignored and not started by firmware (again, I mean BIOS or UEFI), so the OS won't see it.



* ... but it shouldn't be unless you changed the default which according to the manual is the add-on card:

> IGFX Sets the onboard graphics as the first display.
**PCIe** 1 Slot Sets the graphics card on the **PCIEX16** slot as the first display. (**Default**) 			 		

---

### Post by ronjjjg8885 on 2020-02-25
so..
 Windows 8 Features was already set to 'Other OS'
 
and and as for the PCIE graphics device over the integrated graphics device - it is in PCIE mode.

i've added images

---

### Post by Yellow Pasque on 2020-02-25
> Not familiar with Nvidia Device 2187.
Geforce GTX 1650 Super ( [https://pci-ids.ucw.cz/read/PC/10de/2187](https://pci-ids.ucw.cz/read/PC/10de/2187) )
That's probably why nothing shows up in Additional Drivers GUI. The card is newer than the database it uses.

So it was me, I would:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-driver-440
```

---

### Post by CelticWarrior on 2020-02-26
> **Yellow Pasque said:**
> Geforce GTX 1650 Super ( [https://pci-ids.ucw.cz/read/PC/10de/2187](https://pci-ids.ucw.cz/read/PC/10de/2187) )
That's probably why nothing shows up in Additional Drivers GUI. The card is newer than the database it uses.

So it was me, I would:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-driver-440
```

+1

Exactly. Brand new Nvidia cards often need newer driver version that may not be available yet in the official repositories, reason why we add the additional, semi-official, PPA.

---

### Post by ronjjjg8885 on 2020-02-27
thank you i will try it later when i'm on the desktop computer!

---

### Post by ronjjjg8885 on 2020-02-28
seems as the wave disappeared after doing your suggestion

i also included the additional drivers window. this is how it should be set?

anything else that needs to be done?

by the way. all the error messages also gone after i rebooted

thanks

---

### Post by CelticWarrior on 2020-02-28
It seems fine to me. If the problem is gone and no error messages I would say well done. ):P

Note down this requirements if you need to reinstall.

---

### Post by ronjjjg8885 on 2020-03-03
thank you all

it was very helping

---

### Post by Yellow Pasque on 2020-03-04
You're welcome. If you upgrade to 20.04, remember to remove the PPA before upgrading. I don't think you'll need it for 20.04 anyway.

---

### Post by ronjjjg8885 on 2020-03-05
:KS good

---

