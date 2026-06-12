---
title: "Sound wont work on my hp dv6000 laptop"
date: 2008-03-13
forum: Hardware &amp; Laptops
---

### Post by chelover23 on 2008-03-13
i installed ubuntu 7.10 gutsy, then everything was ok
except for the sound, i dont have audio and i dont know why :confused:, im a super noob when it comes to these things so a step by step detailed answer would be great, what could be causing this?  how can i get my audio to run? here is my laptop specs.

thank u for all those who would answer. :)

Product Name: dv6663cl.
US Product Number: GS804UA.
Microprocessor: 2.20 GHz Intel Centrino Duo processor technology featuring Intel Core 2 Duo processor T7500 4 MB L2 cache.
Memory: 2048MB DDR2 System Memory (2 Dimm).
Video Graphics: NVIDIA GeForce 8400M GS with up to total graphics memory with dedicated (e).
Hard Drive: 200 GB (4200 RPM) Hard Drive (SATA).
Multimedia Drive: Super Multi 8X DVD+/-R/RW with Double Layer Support.
Display: 15.4" WXGA High-Definition BrightView Widescreen (1280 x 800) Display.
Fax/Modem: High speed 56k modem.
Network Card: Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector).
Wireless Connectivity: Intel PRO/Wireless 4965AGN Network Connection.
Sound: Altec Lansing.
Keyboard: 101-key compatible & 2 Quick Launch Buttons- HP Quick Play Menu and DVD.
Pointing Device: Touch Pad with On/Off button and dedicated vertical scroll Up/Down pad.
PC Card Slots: 1 ExpressCard/54 Slot (also supports ExpressCard/34).

---

### Post by balaknair on 2008-03-14
Hi Chelover23
A little more info would help others to understand your problem better
Could you please type in
aplay -l
lspci -v

in a terminal and post the output(Terminal= Applications>Accessories>Terminal)

---

### Post by chelover23 on 2008-03-14
Hi to you also balaknair
heres the info u wanted me to paste.
sorry i took so long :)

miah@MoinkChoink:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
and

miah@MoinkChoink:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c4000000-c6ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00004000-00007fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00008000-0000bfff
        Memory behind bridge: bc000000-bfffffff
        Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f8000000-f80fffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: f8100000-f81fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: medium devsel, IRQ 10
        Memory at 88100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at c000 [size=256]
        Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at f8100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

here they are thanks for your reply on my post. :)

---

### Post by balaknair on 2008-03-14
OK thanks
Sorry for the delay, I'm at work and was a bit busy.

You might want to check these guides-
A detailed step by step guide to troubleshoot sound issues in ubuntu.
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

guide on hda-intel
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

A simpler fix for hda-intel modules(based on what worked for me from both the above links)
open a terminal and enter the following commands

```
cat /proc/asound/card0/codec#* | grep Codec
```

this will tell you what codec your sound card type needs
for eg my card returned "Codec: Analog Devices AD1986A"
so the card I use is AD1986A
Next find your card configuration by checking the following link
[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

in that page find your card model and check the details given
eg
```
AD1986A
919 6stack 6-jack, separate surrounds (default)
920 3stack 3-stack, shared surrounds
921 laptop 2-channel only (FSC V2060, Samsung M50)
922 laptop-eapd 2-channel with EAPD (Samsung R65, ASUS A6J)
923 ultra 2-channel with EAPD (Samsung Ultra tablet PC)
```

select the description that best matches your system(eg a 5.1 surround system with 6 audio-out channels/ports would be 6stack).

then go back to the terminal and type
```
sudo gedit /etc/modprobe.d/alsa-base
```

Paste this into the last line of the file

```
options snd-hda-intel model=MODEL
```

replace MODEL with your model(6stack, 3stack, laptop etc.)
Save and exit
Reboot.

If this doesn't work you can also edit the probemask(look at the hda-intel howto page, it's towards the end)

If this too doesn't work you can compile the latest alsa kernel from source
Download the Alsa packages and save them to a folder named 'downloads' in your home folder
(the folder name is case sensitive)
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2)
[ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.16.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.16.tar.bz2)

Extract the archives in the 'downloads' folder

Open a terminal
 Install the tools to compile the kernel and remove the old alsa packages
```
sudo apt-get install linux-headers-$(uname -r) build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev

```
```
sudo apt-get remove --purge alsa-base alsa-tools
```
Navigate to the downloads folder and install the new driver, libraries, tools and firmware
```
cd ~/downloads/alsa-driver-1.0.16
sudo make clean
sudo make mrproper
./configure --with-oss=yes --with-cards=hda-intel 
sudo make
sudo make install
```
```
cd ~/downloads/alsa-lib-1.0.16
sudo make clean
./configure
sudo make
sudo make install
```
```
cd ~/downloads/alsa-utils-1.0.16
./configure
sudo make clean
sudo make 
sudo make install
```
```
cd ~/downloads/alsa-firmware-1.0.16
./configure
sudo make clean
sudo make 
sudo make install
```

Now you've installed the latest stable alsa drivers. You might need to reboot the system to load the new drivers. If you still have no sound, try the steps I mentioned earlier(editing modprobe.d and adding the hda-intel line at the end) and reboot again.

If your problem is fixed, please reply and post just what worked for you, and please don't forget to mark the thread as solved so that it's easier for others to find it.

Wishing you luck

---

### Post by chelover23 on 2008-03-14
this is what i got when i typed in that codec code
and i think im suppose to look for the Si3054 right?
but i couldnt seem to locate it in the link u gave me.. 

miah@MoinkChoink:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 268
Codec: Motorola Si3054

il still be reading the other links u gave but i just want to know why :)
sorry about my question disturbing ur work. thanks for taking the time to answer :)

---

### Post by balaknair on 2008-03-14
ALC268
	  3stack	       3-stack model
	  toshiba	      Toshiba A205
	  acer	      Acer laptops
	  auto	      auto-config reading BIOS (default)

This might be what you need.

---

### Post by balaknair on 2008-03-14
Before you recompile the kernel ther's something else you ought to try for your card(ICH8 family Intel HDA card)
Get the newer version of Ubuntu generic linux kernel
Here's how:
Enable gutsy backports in Software Sources 
(System>Adiminstration>Software Sources--->Updates--->Unsupported Updates(gutsy-backports))
Exit

Then open a terminal and enter
sudo apt-get install linux-backports-modules-generic

Restart system
Sound is muted by default, you might have to unmute(check the troubleshooting guide for detailed instructions)

Sorry for any confusion this might cause, I should have thought of this before

---

### Post by AndyTheGeeky on 2008-03-14
Hello, balaknair.
I've got the same series laptop, and the same problem and symptoms. Running Ubuntu Gutsy x86-64.

I don't know where to find most of the info posted in OP(besides BIOS), but:
Product#: dv6700
RAM: ~3GB
I think the CPU is faster.
I believe/assume the rest is the same.

Console results:
```
andy@xxxxxx:~$ sudo aplay -l
aplay: device_list:207: no soundcards found...    :(
# lspci shows me my soundcard though :-/ Here's the card, I'll post the rest if necessary.
andy@xxxxxx:~$ sudo lspci -v

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
```I also don't have a /proc/asound/card0 folder, though I have /proc/asound:
```
andy@xxxxxx:~$ dir --color=auto /proc/asound
cards  devices  modules  **[COLOR=DarkSlateBlue]oss[/COLOR]**  pcm  **[COLOR=DarkSlateBlue]seq[/COLOR]**  timers  version
```I'm only slightly less newb-ish than OP, and still require step-by-step instructions.
Following the guide you linked in your second post seemed to run correctly, nothing seems different after reboot.

---

### Post by balaknair on 2008-03-14
Hi Andy
You've got an ICH8 family audio card.
 The easiest way I know of to fix sound in the ICH8 is what I've described in the 7th post in this thread- to upgrade the kernel modules to gutsy-backports modules.

Another thing is you might eed to make sure sound is not muted(it's muted by default) by fiddling with the volume controls.
Could you please give that a try and post a reply here how it went?
Thanks

---

### Post by AndyTheGeeky on 2008-03-15
:biggrin: Upgrading the kernel worked right out :biggrin:

Thanks!

---

### Post by Yellow Pasque on 2008-03-15
Upgrading to ALSA 1.0.16 also seems to fix the issue for those not interested in messing with the kernel. The process is outlined above, but most people will probably find it quicker/easier to run the scripts here: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by andradx on 2008-03-18
A friend a mine had a similar problem on the same laptop.
After installing all the alsa-drivers et al
on /etc/modprobe.d/alsa-base try adding the line snd-hda-intel model=toshiba

worked for him

---

