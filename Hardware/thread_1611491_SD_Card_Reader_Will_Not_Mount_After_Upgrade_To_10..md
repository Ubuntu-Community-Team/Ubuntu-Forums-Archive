---
title: "SD Card Reader Will Not Mount After Upgrade To 10.10"
date: 2010-11-01
forum: Hardware
---

### Post by nodrog1952iii on 2010-11-01
I have a Dell Precision M6300 Laptop on which I have been running Ubuntu for over 2 years. I ran 8.04 Hardy for two years and then 10.04 Lucid for the past 6 months. Everything worked great including my SD card reader on both 8.04 and 10.04 until yesterday when I performed a distribution upgrade to 10.10 Maverick.  Now, after the upgrade, my SD card reader will not mount. Dmesg gives the following dialog when I insert an SD card:

[  120.602656] r852: detected xD writeable card in slot
[  120.910163] No NAND device found.

Prior to installing 10.10, the SD card would mount and a dialog would begin automatically when I inserted a SD card.  Now, nothing happens.

I would appreciate any advice as to how to trouble shoot and solve this problem.  I have a dual boot machine and Windows mounts the card without a problem so I am fairly certain that its not a hardware problem.

Thanks,

Gordon

---

### Post by wilee-nilee on 2010-11-01
Can you see the card in gparted in linux is there a flag on it if so, that right clicking on the card and the info might give a explanation.

Personally if these sd cards are the same formatting as a hd or thumb, just empty the data and reformat it. It must be a fat16 or fat32 partition I would think.

This is a internal or plug-in reader?

---

### Post by nodrog1952iii on 2010-11-02
The SD card reader does not show up in gparted.  Also, it does not show up if you run "sudo fdisk -lu" from the command line.  I have tried two different SD cards that worked in the past and that currently work from the Windows partition. Neither work with the Ubuntu 10.10 distribution upgrade.

The SD card reader is an internal reader that came with my Dell Precision M6300.

Any ideas???

Thanks,

Gordon

---

### Post by wilee-nilee on 2010-11-02
I would boot a live cd of Maverick and see if this plays out the same. I have used a sd card on my acer aspire one using maverick. If your computer has been distro upgraded from hardy to lucid to maverick that may be part of the problem.

We don't know of what you have done to customize your setup, and I suspect you only remember some if your like the rest of us. Yo cab tweak your setup to the point of upgrades can be compromised.

---

### Post by phelge on 2010-11-06
I had the same problem, and I solved it by blacklisting r852. 
In /etc/modprobe.d/blacklist.conf file, add at the end:
blacklist r852
and reboot

---

### Post by nodrog1952iii on 2010-11-06
Hi phelge,

Thanks for the reply!

However, your solution to blacklist r852 didn't work for me....  FWIW, I tried it with several different kernels including the stock Maverick 2.6.35-22 kernel as well as the 2.6.37-999 development kernel referenced below in this post.

Also, as an FYI, I found a bug report on launchpad about this at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208/+index?comments=all)

I found an improved solution to this problem...  But its not a complete fix.  That is, I installed the current development kernel:

linux-headers-2.6.37-999-generic_2.6.37-999.201011041120_amd64.deb

from the daily builds here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-11-04-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-11-04-maverick/)

Everything appeared to work perfectly.  However, It turns out this kernel does not completely fix the Ricoh reader problem. That is, with the new kernel, the SD reader will work for a while (about 5-10 minutes) after you boot the computer and then it will stop working again. So, while this situation is better, its not totally fixed yet.  However, this is an improvement...

Thanks again,

Gordon

---

### Post by phelge on 2010-11-07
Hi nodrog1952iii

I have a different laptop (HP 8710W), I had exactly the same traces in /var/log/messages.

kernel: [16141.192067] r852: detected xD writeable card in slot
kernel: [16141.496115] No NAND device found.

In /var/log/syslog I had at the same time the following :

kernel: [  869.948889] mmc0: Got data interrupt 0x00200000 even though no data operation was in progress.
kernel: [  869.948891] sdhci: ============== REGISTER DUMP ==============
kernel: [  869.948895] sdhci: Sys addr: 0x30e81000 | Version:  0x00000400
kernel: [  869.948898] sdhci: Blk size: 0x00007200 | Blk cnt:  0x00000000
kernel: [  869.948902] sdhci: Argument: 0x00000000 | Trn mode: 0x00000033
kernel: [  869.948905] sdhci: Present:  0x01ff0000 | Host ctl: 0x00000003
kernel: [  869.948909] sdhci: Power:    0x0000000f | Blk gap:  0x00000000
kernel: [  869.948913] sdhci: Wake-up:  0x00000000 | Clock:    0x00000107
kernel: [  869.948916] sdhci: Timeout:  0x00000009 | Int stat: 0x00000003
kernel: [  869.948920] sdhci: Int enab: 0x02ff00cb | Sig enab: 0x02ff00cb
kernel: [  869.948923] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
kernel: [  869.948927] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
kernel: [  869.948929] sdhci: ===========================================

I tried as well 999 kernels end of October with no success.

Apparently some users had success by add a file:
/etc/modprobe.d/sdhci with content:
options sdhci debug_quirks=1
But that didn't work for me.

The r852 module is for xD card, and I don't have, so it's not an issue for me to blacklist it.

I found this workaround while playing with lsmod, rmmod and modprobe. Try it: Keep inserted in an SD card in the card reader, and start with :
sudo rmmod sdhci_pci sdhci r852
then try to 
sudo modprobe sdhci_pci
see what happens in messages and syslog

Good luck

---

### Post by nodrog1952iii on 2010-11-07
Hi Phelge,

I tried both of your recommendations, however, with out success.

I really appreciate your spending the time to offer suggestions!  Thanks!!!

For now, I am just running the 999 kernel since the card reader will then work for a while immediately after a reboot. I don't really like this solution since it is so like Microsoft to have to reboot to make something work.  Nevertheless, its the best solution that I have found so far.  Hopefully, somebody else will come forward with a permanent solution.

Gordon

---

### Post by victoitor on 2010-11-17
I'm having the same problem with no solution. I'll try to install the new driver later and report what happened.

---

### Post by victoitor on 2010-11-17
I wonder if this is related to this bug.

If you notice below, the driver for the SD card reader is sdhci-pci.

```

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Device 01bd
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at ef9fd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```

The driver for an xD card is r852.

```

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
	Subsystem: Dell Device 01bd
	Flags: medium devsel, IRQ 18
	Memory at ef9fd700 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: r852
	Kernel modules: r852

```

Since we're inserting an SD card, the driver that should be used is the sdhci-pci driver.

If dmesg returns:
```

r852: detected xD writeable card in slot

```

then it seems the card was detected incorrectly as an xD card and the incorrect driver was loaded. Does this make sense?

---

### Post by victoitor on 2010-11-17
Since I could not find this specific bug anywhere else, I've just filed it here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/676752](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/676752)

Hope we can get some help.

---

### Post by nodrog1952iii on 2010-11-19
Hi victoitor,

I had filed a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/670181?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/670181?comments=all)

And I later found an earlier bug filed here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208)

I don't know if we need to mark ours as duplicates or not. What do you think?

FYI,

Gordon

---

### Post by victoitor on 2010-11-22
> **nodrog1952iii said:**
> Hi victoitor,

I had filed a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/670181?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/670181?comments=all)

And I later found an earlier bug filed here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208)

I don't know if we need to mark ours as duplicates or not. What do you think?

FYI,

Gordon

I don't think that earlier bug is related to ours.

I mean this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/238208)

That one is related to memory stick and it might use a different driver than for an SD card (even though it's the same hardware).

Our bug reports seem pretty similar, but I read somewhere that hardware problems should be filed separately because two people do not necessarily have the same hardware and the problems might be different. Even with that said and looking at the fact that we have different hardware (even the revision of the sd card reader is different), I think it IS the same problem so we could mark our bug reports as duplicate. Just one problem though... this is the first bug report I have ever filed and I wouldn't know how to do so.

---

### Post by UncleBoxy on 2010-11-24
I'm having issues with my reader also.  The IRQ of my reader is set to 255, and I'm not sure how to set it to something different.  ACPI isn't setting it correctly.  Here's my relavent stuff:

```
lspci -vv

00:0e.0 Mass storage controller: Winbond Electronics Corp Device 8481 (rev 01)
	Subsystem: Winbond Electronics Corp Device 1050
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at e0005000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at e0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0e.1 Mass storage controller: Winbond Electronics Corp Device 8482 (rev 01)
	Subsystem: Winbond Electronics Corp Device 1050
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 255
	Region 0: Memory at e0007000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at e0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>


```

```
cat /proc/interrupts 
           CPU0       
  0:         27   IO-APIC-edge      timer
  1:      13307   IO-APIC-edge      i8042
  7:          1   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
 10:        163   IO-APIC-fasteoi   acpi
 12:       2720   IO-APIC-edge      i8042
 14:      21042   IO-APIC-edge      pata_via
 15:      22078   IO-APIC-edge      pata_via
 16:     138088   IO-APIC-fasteoi   yenta, 0000:02:00.0
 17:          2   IO-APIC-fasteoi   firewire_ohci
 18:      49117   IO-APIC-fasteoi   radeon
 19:      11819   IO-APIC-fasteoi   eth0
 21:     586798   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4
 22:       1262   IO-APIC-fasteoi   VIA82XX-MODEM, VIA8233
NMI:          0   Non-maskable interrupts
LOC:     458605   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         15   Machine check polls
ERR:          1
MIS:          0

```

```
ls -1 /sys/devices/pci0000\:00/
0000:00:00.0
0000:00:01.0
0000:00:06.0
0000:00:08.0
0000:00:0c.0
0000:00:0e.0
0000:00:0e.1
0000:00:10.0
0000:00:10.1
0000:00:10.2
0000:00:10.3
0000:00:11.0
0000:00:11.1
0000:00:11.5
0000:00:11.6
0000:00:18.0
0000:00:18.1
0000:00:18.2
0000:00:18.3
firmware_node
pci_bus
power
uevent

```

```
cat /sys/devices/pci0000\:00/0000\:00\:*/irq
0
0
17
19
16
255
255
21
21
21
21
0
23
22
22
0
0
0
0

```

I've tried

```
sudo rmmod sdhci-pci
sudo modprobe sdhci
```

and the driver loads without a problem, but no IRQ gets assigned.

---

### Post by UncleBoxy on 2010-11-24
Well, I made some progress.  My device now has an IRQ assigned to it - specifically IRQ 5.  Here are the steps I took, all of which were done in the BIOS:

[LIST=1]
[*]Changed the OS selection from "Other" to "Win2k/XP" (those are the only 2 options).  I'm guessing "Other" means "Don't use ACPI" and "Win2k/XP" means "Let OS Decide".
[*]Set Reset Configuration Data to "Yes"
[*]Save Changes and Exit (causes a reboot)
[/LIST]

Upon reboot I fired up a terminal and did a ```
lspci -vv
``` which gave the following output for the relevant sections

```
00:0e.0 Mass storage controller: Winbond Electronics Corp Device 8481 (rev 01)
	Subsystem: Winbond Electronics Corp Device 1050
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at e0005000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at e0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:0e.1 Mass storage controller: Winbond Electronics Corp Device 8482 (rev 01)
	Subsystem: Winbond Electronics Corp Device 1050
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at e0007000 (32-bit, non-prefetchable) [size=4K]
	Region 1: Memory at e0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

```

It still doesn't read my (mmc) card though.  The card works fine on another computer (Asus EEEPC 900 netbook), so I can rule that out.

Gonna keep on troubleshooting this.

Oh and I forgot to post my specs:
Clevo D470K Laptop
BIOS Revision 2.04

---

### Post by iconoclast hero on 2011-04-17
Was there a solution for this? 

The card reader was working before I had to reinstall 10.10 onto an SD card acting as my boot HDD.

Here is my lspci -vv
```

08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Hewlett-Packard Company Device 30cd
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 18
    Region 0: Memory at f4400800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cd
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 10
    Region 0: Memory at f4400c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-

08:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cd
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 18
    Region 0: Memory at f4401000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [80] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
    Kernel driver in use: r852
    Kernel modules: r852

```basically all I've done so far except for adding "tifm_sd" to my/etc/modules file.

---

### Post by iconoclast hero on 2011-04-17
I can see it in gparted and fdisk -lu

```
Disk /dev/mmcblk0: 2045 MB, 2045247488 bytes
47 heads, 46 sectors/track, 1847 cylinders, total 3994624 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             247     3994623     1997188+   6  FAT16

```

I did run a system test on the SD card and it spit out a report.  Don't know what it means or what to post.

---

### Post by kedmond on 2011-06-08
I'm having the same problem.  SD Card slot in a Dell Latitude E6400.  It worked perfectly before 10.10.  The card reader doesn't exist according to Ubuntu.  Maybe the BIOS turned it off???

Hope someone can fix this.

---

### Post by Areia on 2011-06-23
Same problem here. I have two netbooks at home, one Acer (AspireOne) and one Asus(eeepc1001HA), on the Aspire running Maverick, the SD card of my camera works, but on the Asus(with the same Maverick) wen I insert the SD card... nothing happen.
Some solution out there?

---

### Post by CoolDreamZ on 2011-08-06
I have the same problem on my Dell Precision M6300, I am running Linux Mint 11 (Kernel 2.6.38-8-generic #42-Ubuntu).

I can get the card reader to work if I reboot the laptop with an SD card already in the reader. However, once I remove the card it no longer works when I (re)insert a card.

---

### Post by pdv99 on 2012-01-15
Same problem on Dell Vostro 1310 with internal card reader - It worked fine this morning reading ,jpg files from my 16Gb SDHC card under 10.04.

Upgraded to 11.10 this afternoon and I get mmc0 Error -110 when I insert the card. GParted can't see the card, but Disk Utility correctly identifies the card's capacity and identifies it as mmcblk0 if the card is present at boot but  can't identify partitioning and still   can't read it. If card is removed and re-inserted, Disk utility doesn't find it.

---

### Post by degarb on 2012-03-13
Any fix?  I am unsure by researching this and this thread if anyone had luck on this problem.   I am downloading gparted and old iso for preparing xp dual boot.  Though, I really need to wait until

Help, I don't wish to do this!  Only my card reader is on the linux machine.

------------------------
Short list of Linux complaints: No sd card, cannot see network very often while it serves fine, wireless network cards don't work, no authotkey macro program, no dos with 100's of thousands of old 80's helper coms and exes, linux command line is too abbreviated and non humanly readable for my taste, I personally never liked the linux alpha circa 1980s file system, my printers don't work and cannot get workings, no voice recognition, no natural sounding att like text to mp3 built in ap, open libra memory issues, Os growing and my dollars cannot keep up, , never can get wine to work, no playon.tv, lack of basic  guis that take about 1 hour for a good coder in basic things like starting and stopping samba, too risky for a non programmer to edit configs, no rollback of system files and configs, forced upgrades (thankfully 12.04 is 5 years), upgrading can wipe out installed program and data, too much loss in cpu in xp under virtual box to be practical (I haven't been able to get vbox support for a few weeks now, anyway).

My list xp/ms complaints: windows wishes us to buy a new computer every 2 years, while I believe every 10-15 years is sufficient; anything below sp3 is bad; not supporting new HD unless you go win7 bloat; the win upgrades don't include fixes, only bloat; I am not a fan of security software, as they slow system; don't like paying $100 per machine for OS since every house needs 5 computers now days. 

This list doesn't cover: Don't like Bill Gate's haircut in the 1970s; moreover, unsure who to pick on, since he left the company. Yes, and Apple commercials have really cool music.

---

### Post by ordealbyfire83 on 2012-06-03
I can't remember where I found this, but the following works for me. Insert the SD card and then type

```
sudo modprobe -r r852 ; sudo modprobe -r sdhci_pci ; sudo modprobe r852 ; sudo modprobe sdhci_pci
```

Make sure the card is inserted though. Otherwise it won't work. I'm running 12.04 with MATE, so after typing this, the card shows up in the "Places" menu and then it's browsable in Caja (Nautilus).

---

