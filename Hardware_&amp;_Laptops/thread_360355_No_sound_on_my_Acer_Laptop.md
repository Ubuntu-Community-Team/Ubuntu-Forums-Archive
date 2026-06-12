---
title: "No sound on my Acer Laptop"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by gingerj on 2007-02-13
Hi all, I installed Ubuntu about 2 months ago and I decided this weekend to get sound and mp3 support working, but nothing seems to play via my Ubuntu partition.

I've read a couple of threads and I'm completely lost via my results.

Could someone please help me?

> 
******@******-laptop:~$ **aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
******@******-laptop:~$



> 
******@******-laptop :~$ **lspci -v**
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: c8100000-c81fffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d7f00000
        Capabilities: <available only to root>

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: 52000000-520fffff
        Capabilities: <available only to root>

0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <available only to root>

0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <available only to root>

0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 66
        I/O ports at 1800 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 193
        I/O ports at 1820 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at 1840 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 169
        I/O ports at 1860 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 66
        Memory at c8004000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=56
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c8300000-c83fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000051f00000
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0
        Capabilities: <available only to root>

0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 0, IRQ 185
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1880 [size=16]

0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7149 (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at c8100000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at c8120000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)        Subsystem: Intel Corporation: Unknown device 1001
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at 52000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at 3000 [size=256]
        Memory at c8300000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:0a:09.0 CardBus bridge: Texas Instruments: Unknown device 8039
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 168, IRQ 201
        Memory at c8301000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=0a, secondary=0b, subordinate=0e, sec-latency=176
        Memory window 0: 50000000-51fff000 (prefetchable)
        Memory window 1: 54000000-55fff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

0000:0a:09.2 Mass storage controller: Texas Instruments: Unknown device 803b
        Subsystem: Acer Incorporated [ALI]: Unknown device 0102
        Flags: bus master, medium devsel, latency 57, IRQ 10
        Memory at c8302000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:0a:09.3 0805: Texas Instruments: Unknown device 803c (prog-if 01)
        Subsystem: Acer Incorporated [ALI]: Unknown device 0094
        Flags: bus master, medium devsel, latency 57, IRQ 201
        Memory at c8300400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>


---

### Post by renzokuken on 2007-02-13
i had trouble with ALC883 too, all appeared to work but nothing ever came out of my speakers.

to fix it i simply compiled that latest alsa-driver from source, rebooted and had perfect working sound.

if you need help doing this let me know

---

### Post by gingerj on 2007-02-13
Ahh thank you for replying :D

can i grab the latest drivers from like a sudo apt-get command? Or do I have to download stuff and then recompile? If so I'd appreciate any help given to me cos I'm clueless when it comes to that stuff my learning curve hasn't reduced yet it's still steep. :)

---

### Post by renzokuken on 2007-02-13
nope, sadly apt-get doesnt have the latest drivers which support quite alot of new hardware

download this file [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc2.tar.bz2) to your Desktop

then run the following commands from the terminal

```

cd Desktop
tar xjvf alsa-driver-1.0.14rc2.tar.bz2
cd alsa*
./configure
make
sudo make install

```

reboot and see what happens. if still nothing, play around with alsamixer again

---

### Post by gingerj on 2007-02-13
Hiya, I downloaded that driver tar file and then extracted it and made a directory on my desktop. then navigated into it, and then did the ./configure command in it. But I get this error message:

> 
******@******-laptop:~/Desktop/alsa-driver-1.0.14rc2$ ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


I checked the config.log file but it doesn't notify me as to what's wrong, in plain english.

I don't actually know what the ./configure command does and when I did man ./configure I got an awful error message.

Sorry to ask so many questions but my lack of knowledge regarding debugging stuff seems to have hampered my progress yet again.

---

### Post by renzokuken on 2007-02-14
ok, you need the "tools" to compile with, simply run

```
sudo apt-get install build-essential
```

then try again

---

