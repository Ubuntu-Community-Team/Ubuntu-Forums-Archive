---
title: "sudo lshw -C power doesn't show battery"
date: 2012-09-24
forum: Hardware
---

### Post by Wer Bn on 2012-09-24
Hello guys.
I have this problem.
Title is self-explanatory.


[http://i.imgur.com/JIAXm.png](http://i.imgur.com/JIAXm.png)

[http://i.imgur.com/kzQtI.png](http://i.imgur.com/kzQtI.png)


I noticed it because the battery icon doesn't show at the top bar.

Don't know what's happening.
Waiting help.

Thanks in advance.

---

### Post by Wer Bn on 2012-09-25
Btw, it's an ACER Extensa 5635G
Ubuntu 12.04

No problem at all in Windows 7. Fully works with icon.

---

### Post by Wer Bn on 2012-09-26
Hello??!!

---

### Post by matt_symes on 2012-09-26
Hi

Try this from the terminal

```
sudo apt-get install acpitool
```

```
acpitool -B
```

Captial B.

lshw returns nothing on my laptop either
```

matthew-Aspire-7540:/home/matthew % sudo lshw -C power   
matthew-Aspire-7540:/home/matthew %
```

Kind regards

---

### Post by Wer Bn on 2012-09-28
Sorry.
The title should be sudo lshw -short doens't show my battery.

Well.... thanks. it works
Guess I'll have to do that.
It shows the baterry remaining capacity. But it doesn't show the remaining time :(

Why the baterry icon still doens't show up?

---

### Post by matt_symes on 2012-09-28
Hi

> **Wer Bn said:**
> Why the baterry icon still doens't show up?

Take a look at this post. It's for 11.10 but i assume it will still hold for 12.04.

[http://askubuntu.com/questions/68445/no-battery-status-icon](http://askubuntu.com/questions/68445/no-battery-status-icon)

Kind regards

---

### Post by newb85 on 2012-09-28
Sorry, Wer Bn, I may have misled you.

matt_symes, are you saying that lshw doesn't list your battery at all, or only that your battery isn't categorized as "power"?

---

### Post by matt_symes on 2012-09-29
Hi

@newb85. It does not list my battery at all.
```

H/W path        Device       Class       Description
====================================================
                             system      Aspire 7540 ()
/0                           bus         JV71TR
/0/0                         memory      112KiB BIOS
/0/4                         processor   AMD Athlon(tm) II Dual-Core M300
/0/4/5                       memory      256KiB L1 cache
/0/4/6                       memory      1MiB L2 cache
/0/19                        memory      3GiB System Memory
/0/19/0                      memory      1GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/19/1                      memory      2GiB DIMM DDR2 Synchronous 667 MHz (1.5 ns)
/0/100                       bridge      RS880 Host Bridge
/0/100/1                     bridge      AMD RS780/RS880 PCI to PCI bridge (int gfx)
/0/100/1/5                   display     RS880M [Mobility Radeon HD 4200 Series]
/0/100/1/5.1                 multimedia  RS880 HDMI Audio [Radeon HD 4200 Series]
/0/100/4                     bridge      RS780/RS880 PCI to PCI bridge (PCIE port 0)
/0/100/4/0      eth0         network     NetLink BCM5784M Gigabit Ethernet PCIe
/0/100/5                     bridge      RS780/RS880 PCI to PCI bridge (PCIE port 1)
/0/100/5/0      wlan0        network     AR928X Wireless Network Adapter (PCI-Express)
/0/100/11                    storage     SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
/0/100/12                    bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.1                  bus         SB7x0 USB OHCI1 Controller
/0/100/12.2                  bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                    bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.1                  bus         SB7x0 USB OHCI1 Controller
/0/100/13.2                  bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                    bus         SBx00 SMBus Controller
/0/100/14.2                  multimedia  SBx00 Azalia (Intel HDA)
/0/100/14.3                  bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4                  bridge      SBx00 PCI to PCI Bridge
/0/101                       bridge      Family 10h Processor HyperTransport Configuration
/0/102                       bridge      Family 10h Processor Address Map
/0/103                       bridge      Family 10h Processor DRAM Controller
/0/104                       bridge      Family 10h Processor Miscellaneous Control
/0/105                       bridge      Family 10h Processor Link Control
/0/1            scsi0        storage     
/0/1/0.0.0      /dev/sda     disk        320GB WDC WD3200BEVT-2
/0/1/0.0.0/1    /dev/sda1    volume      10001MiB EXT4 volume
/0/1/0.0.0/2    /dev/sda2    volume      10001MiB EXT4 volume
/0/1/0.0.0/3    /dev/sda3    volume      10001MiB EXT4 volume
/0/1/0.0.0/4    /dev/sda4    volume      268GiB Extended partition
/0/1/0.0.0/4/5  /dev/sda5    volume      10001MiB Linux filesystem partition
/0/1/0.0.0/4/6  /dev/sda6    volume      10001MiB Linux filesystem partition
/0/1/0.0.0/4/7  /dev/sda7    volume      10001MiB Linux filesystem partition
/0/1/0.0.0/4/8  /dev/sda8    volume      10001MiB Linux filesystem partition
/0/1/0.0.0/4/9  /dev/sda9    volume      10001MiB Linux filesystem partition
/0/1/0.0.0/4/a  /dev/sda10   volume      219GiB Linux filesystem partition
/0/2            scsi1        storage     
/0/2/0.0.0      /dev/cdrom1  disk        DVD RW AD-7585H
```

Think i need a new laptop as well :)

Kind regards

---

### Post by Wer Bn on 2012-09-29
Nothing worked from that 11.04 topic  :(

---

### Post by Wer Bn on 2012-09-30
Hello.
No ideas?

---

### Post by Wer Bn on 2012-10-01
Hey. Anyone?

---

