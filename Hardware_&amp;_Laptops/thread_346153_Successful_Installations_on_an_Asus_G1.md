---
title: "Successful Installations on an Asus G1"
date: 2007-01-25
forum: Hardware &amp; Laptops
---

### Post by Fascination on 2007-01-25
Hi there,

Just wondering if theres been any success stories regarding installing 6.10 on an Asus G1 laptop? The specs are as follows:

[LIST]
[*]Intel® Core™2 Duo Processor T 7200 (2.0 GHz, 64 bit) 
[*]SATA HDD 160 GB ( 5400 RPM) 
[*]15.4" (WSXGA) Colour Shine (1680 x 1050) 
[*]NVidia GeForce 7700 512MB on board VRAM 
[*]DVD Super Multi Double Layer 
[*]2048 Mb DDR2 667 (1024 x2) 
[*]3 x USB 2.0, 1xIEEE 1394 
[*]Video Camera built-in (1.3 million pixels) 
[*]In-Built Bluetooth
[/LIST]

Its only really the processor I have concerns about, though Ive read issues regarding the sound card on a gentoo installation.

---

### Post by vincent_stamour on 2007-02-05
Hello,

We just bought 2 Asus G1 Laptop with 2 Gigs of Ram.

They work fine under ubuntu edgy. 

Except for the capture of sound.  Neither the line in or the mic is able to record.

We have not tested the integrated web cam.

The specs for those machine are great.  But the casing is made of a black plastic that gets scratched very easely.

Here is the output of the pci (lspci -v) For your information.

I still trying to record with the mic.  This is again, the only draw back we are having for the moment.  The graphics are great, thanks to NVidia cards ! 

Regards,

Vincent.


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1237
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: f9f00000-fdffffff
        Prefetchable memory behind bridge: 00000000bdf00000-00000000dde00000
        Capabilities: [88] #0d [0000]
        Capabilities: [80] Power Management version 2
        Capabilities: [90] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1339
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe000000-fe0fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: fe100000-fe1fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1237
        Flags: bus master, medium devsel, latency 0, IRQ 233
        I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1237
        Flags: bus master, medium devsel, latency 0, IRQ 177
        I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1237
        Flags: bus master, medium devsel, latency 0, IRQ 50
        I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1237
        Flags: bus master, medium devsel, latency 0, IRQ 58
        I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1237
        Flags: bus master, medium devsel, latency 0, IRQ 233
        Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=08, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fe200000-feafffff
        Prefetchable memory behind bridge: 00000000ddf00000-00000000dfe00000
        Capabilities: [50] #0d [0000]

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1237
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 185
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at ffa0 [size=16]
        Capabilities: [70] Power Management version 2

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0397 (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1442
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at bc00 [size=128]
        [virtual] Expansion ROM at fbfe0000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 11f5
        Flags: bus master, fast devsel, latency 0, IRQ 169
        I/O ports at c800 [size=256]
        Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
        Expansion ROM at fe0e0000 [disabled] [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1000
        Flags: bus master, fast devsel, latency 0, IRQ 185
        Memory at fe1ff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Legacy Endpoint IRQ 0

04:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1437
        Flags: bus master, medium devsel, latency 168, IRQ 193
        Memory at fe200000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=04, secondary=05, subordinate=08, sec-latency=176
        Memory window 0: 88000000-89fff000 (prefetchable)
        Memory window 1: 8a000000-8bfff000
        I/O window 0: 0000d000-0000d0ff
        I/O window 1: 0000d400-0000d4ff
        16-bit legacy interface ports at 0001

04:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1437
        Flags: bus master, medium devsel, latency 64, IRQ 58
        Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

04:01.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1437
        Flags: bus master, medium devsel, latency 64, IRQ 58
        Memory at feaff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

04:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1437
        Flags: medium devsel, IRQ 3
        Memory at feaff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

---

### Post by Fascination on 2007-02-06
Thanks for taking the time to respond, Vincent - its just what I wanted to hear! :)

---

### Post by specialbuddy on 2007-02-24
I have an Asus G1 as well.  I was wondering if you have played any games or used glxgears at all.  The frames end up skipping every 3 seconds or so.  I have used Beryl and have had no problems but games and other graphics of that sort skip every 3 seconds and it's really annoying.

---

### Post by Topinambur on 2007-03-08
After 2 weeks of struggling with Mic and Line-in on my Asus G1 I finally made them work! As many people from this forum have already mentioned, you'll need to reinstall the Alsa driver from [http://www.alsa-project.org/](http://www.alsa-project.org/)

I went through different Alsa driver packs, and the only one which worked for me was:
Driver: 1.0.14rc3
Library: 1.0.14rc3
Utilities: 1.0.14rc2

Just follow the procedure:
1) Unpack the driver, then execute
./configure --with-cards=hda-intel
make
sudo make install

2) Unpack the library, execute
./configure
make
sudo make install

3) Unpack the utulities, execute
./configure
make
sudo make install

At the end of the /etc/modprob.d/alsa-base add a line:
options snd-hda-intel model=laptop

Reboot

After that my alsamixer showed me a full range of devices, including Front Mic, Mic, Mic Boost, Line, and some other stuff... Both internal and external mics work just perfectly :)

---

### Post by Fascination on 2007-03-11
Ah, thats excellent - worked a treat :D Many thanks :p

---

### Post by gaea on 2007-03-19
> **Topinambur said:**
> 
3) Unpack the utulities, execute
./configure
make
sudo make install


Hello,

Here I get a problem after successful compiling and installing the first 2 packages (driver and library)

The error mesage is after $./configure:

checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

What *exactly* should I install?
There are so many packages with 'curses'...

BTW, I'm doing this on an Asus A7T laptop with 64 bit Kubuntu Edgy  to get some sound.

TIA,

Gerard

---

### Post by Mr.Kuchinawa on 2007-03-30
Excately what do I have to type if the driver, utils and lib are on my desktop?

---

### Post by thetrav on 2007-04-25
following the advice from some people on the forums I installed libncurses5-dev which got me past the configure stage, unfortunately I got error's in the make.
```

Making all in include
make[1]: Entering directory `/home/travis/downloads/alsa-utils-1.0.14rc2/include'
make  all-am
make[2]: Entering directory `/home/travis/downloads/alsa-utils-1.0.14rc2/include'
make[2]: Leaving directory `/home/travis/downloads/alsa-utils-1.0.14rc2/include'
make[1]: Leaving directory `/home/travis/downloads/alsa-utils-1.0.14rc2/include'
Making all in alsactl
make[1]: Entering directory `/home/travis/downloads/alsa-utils-1.0.14rc2/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
        then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \
        then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/home/travis/downloads/alsa-utils-1.0.14rc2/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/travis/downloads/alsa-utils-1.0.14rc2/alsaconf'
Making all in po
make[2]: Entering directory `/home/travis/downloads/alsa-utils-1.0.14rc2/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/travis/downloads/alsa-utils-1.0.14rc2/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/travis/downloads/alsa-utils-1.0.14rc2/alsaconf'
make: *** [all-recursive] Error 1
travis@travis-g1:~/downloads/alsa-utils-1.0.14rc2$ 


```

---

### Post by StarsBravo on 2007-05-06
Hello what nvidia driver and how to install it? i have like a month with the "nv" Driver..

Help pleeeaseeee

---

