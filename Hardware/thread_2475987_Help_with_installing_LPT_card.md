---
title: "Help with installing LPT card?"
date: 2022-06-13
forum: Hardware
---

### Post by peyre on 2022-06-13
I have some old LPT devices I want to be able to access, so I picked up an X-MEDIA XM-PEX-1P PCI-E 1-Port DB25 Parallel PCI Express PCIe Card ([https://www.amazon.com/dp/B08MY7564C?psc=1&ref=ppx_yo2ov_dt_b_product_details](https://www.amazon.com/dp/B08MY7564C?psc=1&ref=ppx_yo2ov_dt_b_product_details)).  One of the reviewers says he plugged it into his Mint machine and it detected his LPT zip drive immediately, so I thought this has to be the model to try.  However, it doesn't see my zip drive.  lspci gives:

```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 Display controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon 540/540X/550/550X / RX 540X/550/550X] (rev c7)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]
03:00.0 Serial controller: Device 1c00:3050 (rev 10)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
05:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

The card comes with a driver disk that includes Linux drivers, with a halfhearted readme for how to install.  It says only:

```
1. open "Terminal"
2. cd "driver" directory
3. compile the driver using "make", you will see the module "wch.ko" if successful
4. "insmod wch.ko" to load the driver dynamically
5. "make install" to make the driver work permanently
```

"sudo make" of course returns "No targets. Stop."  The files in the driver directory are:
Makefile
wch_common.h
wch_devtable.c
wch_main.c
wch_serial.c

"sudo make wch_devtable" returns:
```
cc     wch_devtable.c   -o wch_devtable
In file included from /usr/include/linux/signal.h:5,
                 from wch_common.h:43,
                 from wch_devtable.c:2:
/usr/include/x86_64-linux-gnu/asm/signal.h:103:9: error: unknown type name ‘size_t’
  103 |         size_t ss_size;
      |         ^~~~~~
In file included from wch_devtable.c:2:
wch_common.h:45:10: fatal error: linux/tty_flip.h: No such file or directory
   45 | #include <linux/tty_flip.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make: *** [<builtin>: wch_devtable] Error 1
```

"sudo make wch_main" returns:
```
cc     wch_main.c   -o wch_main
In file included from /usr/include/linux/signal.h:5,
                 from wch_common.h:43,
                 from wch_main.c:61:
/usr/include/x86_64-linux-gnu/asm/signal.h:103:9: error: unknown type name ‘size_t’
  103 |         size_t ss_size;
      |         ^~~~~~
In file included from wch_main.c:61:
wch_common.h:45:10: fatal error: linux/tty_flip.h: No such file or directory
   45 | #include <linux/tty_flip.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make: *** [<builtin>: wch_main] Error 1
```

"sudo make wch_serial" returns:
```
cc     wch_serial.c   -o wch_serial
In file included from /usr/include/linux/signal.h:5,
                 from wch_common.h:43,
                 from wch_serial.c:3:
/usr/include/x86_64-linux-gnu/asm/signal.h:103:9: error: unknown type name ‘size_t’
  103 |         size_t ss_size;
      |         ^~~~~~
In file included from wch_serial.c:3:
wch_common.h:45:10: fatal error: linux/tty_flip.h: No such file or directory
   45 | #include <linux/tty_flip.h>
      |          ^~~~~~~~~~~~~~~~~~
compilation terminated.
make: *** [<builtin>: wch_serial] Error 1
```

Much as I love *buntu, it's at times like these that I miss Windows' Device Manager.

---

### Post by Yellow Pasque on 2022-06-13
Before trying to compile some outdated vendor driver, check if a kernel module is already loaded for it:
```
lspci -k -s 3:00
```

---

### Post by peyre on 2022-06-14
It returns:

```
03:00.0 Serial controller: Device 1c00:3050 (rev 10)
	Subsystem: Device 1c00:3050
	Kernel driver in use: parport_pc
	Kernel modules: parport_pc, parport_serial

```

---

### Post by Yellow Pasque on 2022-06-14
So do you have /dev/lp0 and such? Also, Do you have a high quality EPP parallel cable?

---

### Post by peyre on 2022-06-14
I'll check the contents of /dev when I get home.  I'm using the parallel cable that came with the zip drive, so it's an OEM one.  I have another I could try.

Edit:  Ok, I shut down and plugged in the first zip drive again, fired it up, and the Serial controller is back in lspci.  There is also one lp file in /dev, lp0.

---

### Post by peyre on 2022-06-14
Interesting.  I replaced most everything: I reseated the card into the other PCIe slot and have hooked up a different Zip drive with its own set of cables.  The only difference I see in lspci now is that the Serial controller line is missing.  There are now no lp* files in /dev, so it sounds like whatever I just did just made it worse.

Plugging in the first (100MB) zip drive instead, the Serial controller line is now back, though it still doesn't recognize the disks when I insert them.

---

### Post by peyre on 2022-06-16
Following the instructions at [https://www.linux.org/threads/solved-unable-to-find-parallel-port-of-ch382_2s1p-on-linuxcnc-as-parport.24355/](https://www.linux.org/threads/solved-unable-to-find-parallel-port-of-ch382_2s1p-on-linuxcnc-as-parport.24355/), I tried adding lines to [FONT=Courier New]/etc/modprobe.d/alsa-base.conf[/FONT].

lspci -v shows IRQ 18 and I/O ports at d000 and d100, so I added 

```
# LPC parport to PCI-E card
alias parport_low level parport_pc
options parport_pc io=0xd100 irq=18,auto
```

and rebooted, but no good.  So I changed it to 0xd000 and rebooted again, but it still won't see the zip drive.  :(

---

### Post by rsteinmetz70112 on 2022-06-17
Can you try is in a Windows PC? Just to check to see if it works.

---

### Post by peyre on 2022-06-17
Well...Windows 7 and above don't support LPT zip drives, so that wouldn't work.

I do have an old computer in the garage I could drag out and hook up, boot into XP from a live disk, but it almost certainly won't have drivers for this LPT card, and I'm not certain it has a PCIe slot I could plug into it.  I could plug it into the built-in LPT port on the machine itself, just to verify that the drive still works.  Is that what you have in mind?

---

### Post by rsteinmetz70112 on 2022-06-17
Verifying all of the hardware works seems to be a good step. I've used LPT cards on some Linux computers and they always just worked.

---

### Post by peyre on 2022-06-17
I'll give it a try, though it isn't that long since I used these drives.

---

### Post by peyre on 2022-06-19
Well I'll be d***ed.  I pulled out a couple old machines from the garage with built-in LPT ports and booted from live disks, and neither could see either zip drive.  I tried with live Win7 and XP (the UBCD for Windows), and a Xubuntu disk.  None of them could see either drive on either computer.  I guess they must have both died about the same time.  That's very odd, but it does happen.  Looks like it was a good idea to have me check!

---

