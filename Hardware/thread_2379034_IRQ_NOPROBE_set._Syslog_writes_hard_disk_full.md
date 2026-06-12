---
title: "IRQ_NOPROBE set. Syslog writes hard disk full"
date: 2017-11-30
forum: Hardware
---

### Post by shizow on 2017-11-30
UPDATE:
Is this a hard disk problem?
here is the SMART report:
[ATTACH]278304[/ATTACH]


Hey

I have some issues on my laptop. I use Kubuntu 17.10. Sometimes I get this error message in syslog and kern.log and this error message is immediately repeated and syslog writes the hard disk full. Also in this moment wifi doesnt work properly anymore. Not sure how these are related

I have an Dell Inspiron 11 3162 
The bios is now updated to newest version 2.2.0


Nov 18 16:32:02 system kernel: [30974.233517] irq 115, desc: ffff890efa766800, depth: 1, count: 0, unhandled: 0
Nov 18 16:32:02 system kernel: [30974.233528] ->handle_irq():  ffffffffa80e5b60, 
Nov 18 16:32:02 system kernel: [30974.233552] handle_bad_irq+0x0/0x230
Nov 18 16:32:02 system kernel: [30974.233554] ->irq_data.chip(): ffffffffa8f711a0, 
Nov 18 16:32:02 system kernel: [30974.233559] chv_gpio_irqchip+0x0/0x120
Nov 18 16:32:02 system kernel: [30974.233561] ->action():           (null)
Nov 18 16:32:02 system kernel: [30974.233563]    IRQ_NOPROBE set
Nov 18 16:32:02 system kernel: [30974.233566] unexpected IRQ trap at vector 73


user@system:/var/log$ lspci
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 35)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 35)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 35)
00:10.0 SD Host controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series MMC Controller (rev 35)
00:13.0 SATA controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SATA Controller (rev 35)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 35)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 35)
00:1b.0 Audio device: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series High Definition Audio Controller (rev 35)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 35)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 35)
00:1f.3 SMBus: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx SMBus Controller (rev 35)
01:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
user@system:/var/log$

---

### Post by Yellow Pasque on 2017-11-30
[http://lkml.iu.edu/hypermail/linux/kernel/1610.2/03039.html](http://lkml.iu.edu/hypermail/linux/kernel/1610.2/03039.html)

Try updating your BIOS first.

---

### Post by shizow on 2017-12-11
Thank you.
I updated the Bios to the latest version 2.2.0
The problem is still happening

---

### Post by Habitual on 2017-12-12
Check disk space wrt: **inodes** using
```
df -i
```

inodes could be "full" and you could still have disk space "free"
Other techniques shown at [https://askubuntu.com/questions/231585/running-out-of-inodes](https://askubuntu.com/questions/231585/running-out-of-inodes)

---

### Post by shizow on 2017-12-13
> **Habitual said:**
> Check disk space wrt: **inodes** using
```
df -i
```

inodes could be "full" and you could still have disk space "free"
Other techniques shown at [https://askubuntu.com/questions/231585/running-out-of-inodes](https://askubuntu.com/questions/231585/running-out-of-inodes)

df -i
Filesystem                    Inodes  IUsed   IFree IUse% Mounted on
udev                          485499    486  485013    1% /dev
tmpfs                         492404    736  491668    1% /run
/dev/mapper/kubuntu--vg-root 7528448 339316 7189132    5% /
tmpfs                         492404    379  492025    1% /dev/shm
tmpfs                         492404      6  492398    1% /run/lock
tmpfs                         492404     18  492386    1% /sys/fs/cgroup
/dev/sda1                     124928    320  124608    1% /boot
tmpfs                         492404     28  492376    1% /run/user/1000

---

### Post by shizow on 2018-01-07
The problem still happens. Anyone?

---

### Post by shizow on 2018-01-07
```

$ cat /sys/kernel/debug/pinctrl/INT33FF:*/pins
registered pins: 55
pin 0 (MF_PLT_CLK0) GPIO 0x00118300 0x05c00000
pin 1 (PWM1) GPIO 0x00118102 0x05c00000
pin 2 (MF_PLT_CLK1) GPIO 0x00118300 0x05c00000
pin 3 (MF_PLT_CLK4) GPIO 0x00118000 0x05c00000
pin 4 (MF_PLT_CLK3) GPIO 0x00118300 0x05c00000
pin 5 (PWM0) GPIO 0x00118100 0x05c00000
pin 6 (MF_PLT_CLK5) GPIO 0x00138000 0x05c00000
pin 7 (MF_PLT_CLK2) GPIO 0x18118200 0x05c00004
pin 15 (SDMMC2_D3_CD_B) mode 1 0x00910301 0x05c00000
pin 16 (SDMMC1_CLK) mode 1 0x00110300 0x05c00000
pin 17 (SDMMC1_D0) mode 1 0x00910301 0x05c00000
pin 18 (SDMMC2_D1) GPIO 0x00008200 0x05c00000
pin 19 (SDMMC2_CLK) mode 1 0x00110300 0x05c00000
pin 20 (SDMMC1_D2) mode 1 0x00910301 0x05c00000
pin 21 (SDMMC2_D2) GPIO 0x00008200 0x05c00000
pin 22 (SDMMC2_CMD) mode 1 0x00910301 0x05c00000
pin 23 (SDMMC1_CMD) mode 1 0x00910301 0x05c00000
pin 24 (SDMMC1_D1) mode 1 0x00910301 0x05c00000
pin 25 (SDMMC2_D0) GPIO 0x00008200 0x05c00000
pin 26 (SDMMC1_D3_CD_B) mode 1 0x00910301 0x05c00000
pin 30 (SDMMC3_D1) GPIO 0x08918200 0x05c00004
pin 31 (SDMMC3_CLK) GPIO 0x00118000 0x05c00000
pin 32 (SDMMC3_D3) mode 1 0x00910301 0x05c00000
pin 33 (SDMMC3_D2) mode 1 0x00910301 0x05c00000
pin 34 (SDMMC3_CMD) GPIO 0x00918100 0x05c00000
pin 35 (SDMMC3_D0) mode 1 0x00910301 0x05c00000
pin 45 (MF_LPC_AD2) mode 1 0x00910301 0x05c00000
pin 46 (LPC_CLKRUNB) mode 1 0x00910301 0x05c00000
pin 47 (MF_LPC_AD0) mode 1 0x00910301 0x05c00000
pin 48 (LPC_FRAMEB) mode 1 0x00910301 0x05c00000
pin 49 (MF_LPC_CLKOUT1) mode 1 0x00110300 0x05c00000
pin 50 (MF_LPC_AD3) mode 1 0x00910301 0x05c00000
pin 51 (MF_LPC_CLKOUT0) mode 1 0x00010300 0x05c00000
pin 52 (MF_LPC_AD1) mode 1 0x00910301 0x05c00000
pin 60 (SPI1_MISO) mode 1 0x00910301 0x05c00000
pin 61 (SPI1_CSO_B) GPIO 0x00918100 0x05c00000
pin 62 (SPI1_CLK) GPIO 0x00918100 0x05c00000
pin 63 (MMC1_D6) mode 1 0x00910381 0x05c00000
pin 64 (SPI1_MOSI) GPIO 0x00918102 0x05c00000
pin 65 (MMC1_D5) mode 1 0x00910301 0x05c00000
pin 66 (SPI1_CS1_B) mode 1 0x00910301 0x05c00000
pin 67 (MMC1_D4_SD_WE) mode 1 0x00910301 0x05c00000
pin 68 (MMC1_D7) mode 1 0x00910381 0x05c00000
pin 69 (MMC1_RCLK) mode 1 0x00110300 0x05c00000
pin 75 (USB_OC1_B) mode 1 0x00910301 0x05c00000
pin 76 (PMU_RESETBUTTON_B) mode 1 0x00910301 0x05c00000
pin 77 (GPIO_ALERT) GPIO 0x28918201 0x05c00044
pin 78 (SDMMC3_PWR_EN_B) mode 1 0x00110301 0x05c00000
pin 79 (ILB_SERIRQ) mode 1 0x00910301 0x05c00000
pin 80 (USB_OC0_B) mode 1 0x00910301 0x05c00000
pin 81 (SDMMC3_CD_B) GPIO 0x00918100 0x05c00000
pin 82 (SPKR) mode 1 0x00910300 0x05c00000
pin 83 (SUSPWRDNACK) mode 1 0x00110300 0x05c00000
pin 84 (SPARE_PIN) mode 1 0x00110300 0x05c00000
pin 85 (SDMMC3_1P8_EN) mode 1 0x00110300 0x05c00000

```

```

$ cat /proc/interrupts 
            CPU0       CPU1       CPU2       CPU3       
   0:         18          0          0          0   IO-APIC    2-edge      timer
   1:         18        864        429        439   IO-APIC    1-edge      i8042
   8:          0          0          1          0   IO-APIC    8-fasteoi   rtc0
   9:         59       1310        532        558   IO-APIC    9-fasteoi   acpi
  12:        175     144211      72346      72373   IO-APIC   12-edge      i8042
  16:         13         12         13         14   IO-APIC   16-fasteoi   mmc0
 170:          0          0          0          0   PCI-MSI 458752-edge      PCIe PME
 171:         75         96        108         88   PCI-MSI 327680-edge      xhci_hcd
 172:       3496      67474       3504       3504   PCI-MSI 311296-edge      ahci[0000:00:13.0]
 173:          0          0          0          0   PCI-MSI 180224-edge      proc_thermal
 174:          6          7          6          5   PCI-MSI 425984-edge      mei_txe
 175:         46         48         42      31756   PCI-MSI 524288-edge      iwlwifi
 176:        104        231        162        171   PCI-MSI 442368-edge      snd_hda_intel:card0
 NMI:         44         42         45         41   Non-maskable interrupts
 LOC:     187409     165318     170840     163182   Local timer interrupts
 SPU:          0          0          0          0   Spurious interrupts
 PMI:         44         42         45         41   Performance monitoring interrupts
 IWI:          0          0          1          0   IRQ work interrupts
 RTR:          0          0          0          0   APIC ICR read retries
 RES:      63027      56182      58308      57198   Rescheduling interrupts
 CAL:      35862      37824      48456      50646   Function call interrupts
 TLB:      31586      33912      30480      31035   TLB shootdowns
 TRM:          0          0          0          0   Thermal event interrupts
 THR:          0          0          0          0   Threshold APIC interrupts
 DFR:          0          0          0          0   Deferred Error APIC interrupts
 MCE:          0          0          0          0   Machine check exceptions
 MCP:          4          4          4          4   Machine check polls
 ERR:          1
 MIS:          0
 PIN:          0          0          0          0   Posted-interrupt notification event
 NPI:          0          0          0          0   Nested posted-interrupt event
 PIW:          0          0          0          0   Posted-interrupt wakeup event

```

---

### Post by Yellow Pasque on 2018-01-08
Even if you can't stop the spamming error messages, there are still actions you can take to keep your logs from taking up too much space: [https://wiki.archlinux.org/index.php/Systemd#Journal_size_limit](https://wiki.archlinux.org/index.php/Systemd#Journal_size_limit)

---

### Post by Yellow Pasque on 2018-01-08
It's worth noting that another BIOS update is available, though I don't see anything indicating this issue is fixed: [http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=1F2PX](http://www.dell.com/support/home/us/en/19/Drivers/DriversDetails?driverId=1F2PX)

---

### Post by shizow on 2018-01-16
Updated to newest Bios 2.3.0

---

### Post by shizow on 2018-01-16
anyone can help, please?

---

### Post by shizow on 2018-01-24
perhaps it is a problem with the hard disk
the hard disk is an SSD
SSDR, 128G, S3, 7, TOSHIBA, SG5C

how can I test this?

---

### Post by shizow on 2018-01-24
Here is the smart report from the harddisk

[ATTACH]278303[/ATTACH]

---

### Post by anuar45 on 2018-02-03
Exact same problem

---

### Post by shizow on 2018-02-06
Could anyone please help up?

---

### Post by Yellow Pasque on 2018-02-07
[https://bugzilla.kernel.org/show_bug.cgi?id=194945#c84](https://bugzilla.kernel.org/show_bug.cgi?id=194945#c84)
In other words, try the latest mainline kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15.1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15.1/)

---

### Post by shizow on 2018-02-24
> **Temüjin said:**
> [https://bugzilla.kernel.org/show_bug.cgi?id=194945#c84](https://bugzilla.kernel.org/show_bug.cgi?id=194945#c84)
In other words, try the latest mainline kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15.1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.15.1/)

it worked! Thank you so much!

---

