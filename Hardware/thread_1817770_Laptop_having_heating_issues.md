---
title: "Laptop having heating issues"
date: 2011-08-03
forum: Hardware
---

### Post by tkn4everb on 2011-08-03
I ended up reinstalling Ubuntu via wubi after a couple years because in general it runs better, but since then I've been having issues with my system and heating. When I use a laptop cooler on to cool off my laptop when running windows 7 then the temperature will stay at a constant 39C. If I'm not using one then it will hover around 45C. Using my cooler for Ubuntu keeps it at around 49C and without it's been at around 55C. I have no idea why it's like that. My laptop only gets that hot in windows 7 if I'm playing a a game. Ubuntu is less stressful on my hardware than Windows 7. You would think it would run a lot cooler. 

Anyone else have this issue/ know how I can resolve it? :confused:

---

### Post by Mr. Shannon on 2011-08-03
If you are using Unity, or even regular Gnome with Compiz then you can expect it to run a little hot.  To reduce some of the temperature buildup you could try using Ubuntu Classic (no effects).

I use Metacity as my window manager in Gnome, and I set it to be a compositing window manager and my CPU is at 52 degrees C, my video card is at 51 degrees C, and my hard drive is at 49 degrees C right now.  I too would welcome any suggestions to bring the temperature down.

---

### Post by tkn4everb on 2011-08-04
I'll try that next time I boot up Ubuntu. 

Shortly after I wrote that post yesterday I booted up Windows 7 and checked Speedfan to see what my readings were and it turned out that even my CPUs which normally stay around 26C were blazing at 55C.

---

### Post by tkn4everb on 2011-08-05
Alright how do you go into classic Ubuntu? I thought it was just under the appearance settings. I also tried out Linux Mint to see if that worked better and if was a driver issue, but the results were basically the same. 

I may try out a lighter desktop, but I don't understand why I'm having this issue to begin with.

---

### Post by Toz on 2011-08-05
If you have kernel 2.6.38 (ubuntu 11.04), might be related to a power regression. See: [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html").

---

### Post by tkn4everb on 2011-08-05
I'm running Ubuntu 10.4 since it was the most stable at the moment. Could it be related to drivers? I checked for them and it said no propietary ones were installed.

---

### Post by Toz on 2011-08-05
Perhaps. Can you give us some more info about your computer? Make/model?

Also, open a terminal window, type in the following command, and post back the results (using code blocks):
```
sudo lspci -vnn
```
enter your password when prompted.

---

### Post by tkn4everb on 2011-08-05
Alright I'll post my system info since I'm booted in W7 right now and post the rest once I boot into Ubuntu:

Model: HP G60

Windows 7 32 Bit
Processor: Pentium Dual Core T4200 @2.00 Ghz
GPU: Mobile Intel 4 Series Express Chipset Family
Ram: 3 Gigs
Sound Card: Conexant High Definition Smart Audio 221
Storage Controllers: Al74I6E5 IDE Controller
Disk: 250 GB Samsung HM251JI ATA Device
Wi-fi: Atheros AR5006X 

Let me know is there is anything else. I'll post the results from the other thing in a few moments.

---

### Post by tkn4everb on 2011-08-05
Also I forgot to add that my battery is in a state where it has to be connected all the time if that makes any difference.

Here's the code:

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5110 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, fast devsel, latency 0
	Memory at d2500000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3

00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 50e0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 50c0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 50a0 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d4705c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00004fff
	Memory behind bridge: d3700000-d46fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d14fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:360b]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2600000-d36fffff
	Prefetchable memory behind bridge: 00000000d1500000-00000000d24fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Device [103c:360b]
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [180] Root Complex Link <?>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 5080 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 5060 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 5040 [size=32]
	Capabilities: [50] PCIe advanced features <?>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at d4705800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCIe advanced features <?>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: [50] Subsystem: Hewlett-Packard Company Device [103c:360b]

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 5108 [size=8]
	I/O ports at 511c [size=4]
	I/O ports at 5100 [size=8]
	I/O ports at 5118 [size=4]
	I/O ports at 5020 [size=32]
	Memory at d4705000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA <?>
	Capabilities: [b0] PCIe advanced features <?>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: medium devsel, IRQ 11
	Memory at d4706000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: fast devsel, IRQ 11
	Memory at d4704000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:360b]
	Flags: bus master, fast devsel, latency 0, IRQ 26
	I/O ports at 3000 [size=256]
	Memory at d0410000 (64-bit, prefetchable) [size=4K]
	Memory at d0400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d0420000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [cc] Vital Product Data <?>
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 00-00-ff-ff-00-00-00-01
	Kernel driver in use: r8169
	Kernel modules: r8169

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:137a]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [60] Express Legacy Endpoint, MSI 00
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Virtual Channel <?>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

Hope this helps.

---

### Post by Toz on 2011-08-06
Any processes running out of control? When you notice it hot, run the following command and post back results:
```
top -b | head -20
```

And what kernel version are you running?
```
uname -r
```

EDIT: One other thing you can try is to force the kernel to manage acpi events (like cpu & fan controls). You can do this by using the **acpi_osi=\"Linux\"** kernel parameter.

---

### Post by tkn4everb on 2011-08-06
This is Ubuntu when it first starts up. I'll post again in 30 minutes since it'll be hotter by then.

```
top - 11:14:11 up 3 min,  2 users,  load average: 0.64, 0.37, 0.14
Tasks: 178 total,   1 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.8%us,  5.4%sy,  0.3%ni, 76.5%id, 10.9%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   3027664k total,  1636292k used,  1391372k free,   582272k buffers
Swap:   261112k total,        0k used,   261112k free,   744900k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1091 root      20   0 66664  23m  11m S    2  0.8   0:08.58 Xorg               
 1753 root      20   0  2544 1100  800 R    2  0.0   0:00.02 top                
    1 root      20   0  2804 1660 1204 S    0  0.1   0:00.44 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset  
```

Kernal:

```
2.6.32-33-generic

```

I'll try that suggestion after I post again in 30 minutes so at least then we'll have seen if processes are the issue.

---

### Post by tkn4everb on 2011-08-06
```
top - 11:48:41 up 37 min,  2 users,  load average: 0.22, 0.20, 0.25
Tasks: 160 total,   1 running, 159 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.8%us,  1.8%sy,  1.4%ni, 91.4%id,  2.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3027664k total,  2206844k used,   820820k free,   756144k buffers
Swap:   261112k total,        0k used,   261112k free,  1078488k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                    
 2015 root      20   0  2544 1088  800 R    4  0.0   0:00.03 top                                                                                                        
    1 root      20   0  2804 1660 1204 S    0  0.1   0:00.45 init                                                                                                       
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                   
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                
    4 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/0                                                                                                
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                 
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                
    7 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1                                                                                                
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                 
    9 root      20   0     0    0    0 S    0  0.0   0:00.03 events/0                                                                                                   
   10 root      20   0     0    0    0 S    0  0.0   0:00.01 events/1                                                                                                   
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                     
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper  
```

---

### Post by tkn4everb on 2011-08-06
Alright I tried using the 

```
acpi_osi=\"Linux\" 
```

In the terminal a moment ago, but I do not know if anything happened since it just went to the next line and that was it.

---

### Post by Toz on 2011-08-06
> **tkn4everb said:**
> Alright I tried using the 

```
acpi_osi=\"Linux\" 
```

In the terminal a moment ago, but I do not know if anything happened since it just went to the next line and that was it.

acpi_osi=\"Linux\" a kernel parameter. You need to add it to the kernel line at boot, like this:

1. Edit /etc/default/grub
```
gksudo gedit /etc/default/grub
```

2. Locate the line starting: 
> GRUB_CMDLINE_LINUX_DEFAULT
and add, inside the last quote, the following:
```
acpi_osi=\"Linux\"
```

So that it looks something like this (yours may be different):
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"Linux\""
```

3. Save the file.

4. Update grub:
```
sudo update-grub
```

5. Reboot

---

### Post by tkn4everb on 2011-08-06
Alright, how do I edit the line at boot? USually when I start up it goes past the screen with command lines and into the ubuntu log in.

---

### Post by IcarusR on 2011-08-06
Follow Toz instructions (post 14) to edit /etc/default/grub file then reboot & system will use that kernel parameter.

---

### Post by tkn4everb on 2011-08-06
Alright this came up after I was done. Just posting it to make sure I'm doing it right:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-33-generic
Found initrd image: /boot/initrd.img-2.6.32-33-generic
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done

```

---

### Post by tkn4everb on 2011-08-06
Alright I'm trying it right now to see if there is any difference. I'm using GKrellm to do some monitoring:

sda(which I believe is the HDD) is still at 48C which isn't bad.
sg0 is at 48
TZS0 is at 55
TZS1 is also at 55

btw what are the last three(sg0,tsz0 &1?)


Edit:

It's at

54
54
57
57

---

### Post by Toz on 2011-08-06
> Alright I'm trying it right now to see if there is any difference. I'm using GKrellm to do some monitoring:

sda(which I believe is the HDD) is still at 48C which isn't bad.
sg0 is at 48
TZS0 is at 55
TZS1 is also at 55
So, still running hotter? How about trying to change the cpu governor? See this article for information about the different governors ([http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/index.jsp?topic=/liaai/cpufreq/TheCPUFreqGovernors.htm]("http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/index.jsp?topic=/liaai/cpufreq/TheCPUFreqGovernors.htm")). The default on ubuntu is "ondemand". You can try changing it to conservative to see if it helps. Here's how:

1. Edit the ondemand script
```
gksudo gedit /etc/init.d/ondemand
```

2. Change the line that reads:
> echo -n ondemand > $CPUFREQ
...to:
```
echo -n conservative > $CPUFREQ
```

3. Save the file and reboot.

> btw what are the last three(sg0,tsz0 &1?)
Not sure about sg0, but TZ0 and TZ1 are thermal zones - they are specific to each computer and depends on where the sensors are within the hardware.

---

### Post by tkn4everb on 2011-08-15
Sorry I havent been on in a while, been busy with something.


I did it, but dont have enough time to test it out so i'll report when I do get back on to see if it made a difference. If it doesn't do you think the issue has to do with it not being a propietary driver? I'm also thinking about trying xubuntu to see if that changes anything.

---

