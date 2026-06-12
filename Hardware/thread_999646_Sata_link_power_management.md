---
title: "Sata link power management"
date: 2008-12-02
forum: Hardware
---

### Post by Alexis Phoenix on 2008-12-02
Hi folks

I have a Dell Inspiron 1501 with AMD turion 64bit dual core cpu, kernel 2.6.27.4, Ubuntu Hardy Heron.

I've been trying to save some power, and the thing in particular I can't do is enable sata link power management.  I've tried:
```
sudo su
<password>
echo "min_power" > /sys/class/scsi_host/host0/link_power_management_policy

```
(permission denied to do sudo <echo ....>)
but it refuses to change, even though the permissions are rw.  I hope someone can shed some light on this, because it's really, really bugging me now.  It doesn't work with the generic kernel either, not even using powertop.

Many thanks
Alexis Phoenix

---

### Post by iggykoopa on 2008-12-02
try:
sudo sh -c "echo 'min_power' > /sys/class/scsi_host/host0/link_power_management_policy"
and let me know if it works.

---

### Post by Alexis Phoenix on 2008-12-03
Hi, many thanks for the response.

I tried that, and it doesn't work.  Whaaaa!

Could this be something related to the amd/ati combo?  The chipset is ati sb600 - my lspci output:
```

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

```

Hope this helps you (or others) to help me!

Cheers
Alexis

---

### Post by iggykoopa on 2008-12-03
hmmm that's weird, it's working for me on intrepid 64bit. I can try looking around a little more, I never did find out in the first place why you had to go to a root terminal instead of just sudo.

---

### Post by Alexis Phoenix on 2008-12-03
Mmm, maybe I should just upgrage to Intrepid...

Many thanks, at least you have confirmed that it *can* work!

It looks as if the echo command is successful, but it get changed back by something unknown, almost immediately.

Alexis

---

### Post by hexeroby on 2009-01-09
I'm having the same problem as Alexis.

Example:

$ for i in {0..5}; do echo host$i result:; sudo sh -c "echo 'min_power' > /sys/class/scsi_host/host$i/link_power_management_policy"; cat /sys/class/scsi_host/host$i/link_power_management_policy; done
host0 result:
max_performance
host1 result:
max_performance
host2 result:
min_power
host3 result:
min_power
host4 result:
max_performance
host5 result:
max_performance

Sometimes, while experimenting, I've sometimes seen host0 at min_power immediately after setting it with echo but a second cat results in max_performance:

$ sudo sh -c "echo 'min_power' > /sys/class/scsi_host/host0/link_power_management_policy"
$ cat /sys/class/scsi_host/host0/link_power_management_policy
min_power
$ cat /sys/class/scsi_host/host0/link_power_management_policy
max_performance

How do I know under which host my internal hard drive is connected? I'd imagine it's host0, but how can I check?

For the record, I have a Dell Studio 15 laptop.

lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Thanks for any help,
Hex

---

### Post by .primus on 2009-03-22
hi All,

i was just wondering if there had been a resolution to this problem.

to summarize, when running the following we see:

```
sudo sh -c "echo 'min_power' > /sys/class/scsi_host/host0/link_power_management_policy"
```

```
cat /sys/class/scsi_host/host0/link_power_management_policy
```

```
max_performance
```

The expected result is

```
min_power
```

i am running kernel 2.6.27-11-generic

thanks!

---

### Post by Arlanthir on 2009-12-05
I'm having this problem too on Karmic64bits on an Acer Timeline 4810t.

Edit: bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/427925](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/427925)

---

### Post by Alexis Phoenix on 2009-12-05
I was looking into this again recently - it looks as though some hardware simply doesn't support it.  Apparently Intel does, ymmv with anything else (I have amd/ati hardware (inspiron 1501 dual core turion 64bit) sb600 ide/sata inside).

At the moment, it looks like Intel is the way to go.  Other companies may suck orbs of various kinds.

Alexis

---

### Post by Arlanthir on 2009-12-05
> **Alexis Phoenix said:**
> I was looking into this again recently - it looks as though some hardware simply doesn't support it.  Apparently Intel does, ymmv with anything else (I have amd/ati hardware (inspiron 1501 dual core turion 64bit) sb600 ide/sata inside).

At the moment, it looks like Intel is the way to go.  Other companies may suck orbs of various kinds.

Alexis

I'd say this is Intel, how can I know for sure?

---

### Post by Chrigi on 2010-01-02
I had no problem changing the value on my ThinPad x200 through PowerTop.

Is it possible that my laptop will automatically change to min_power when running on battery and max_performance when plugged in?

---

### Post by F for Fragging on 2010-03-01
After following the instructions in post #7 in [this topic]("http://www.uluga.ubuntuforums.org/showthread.php?t=1157408#7"), I noticed that laptop-mode didn’t enable SATA ALPM link power management. I had configured laptop-mode to do SATA power saving however. 

No matter what I tried with manual commands to change it or the various power saving scripts I found, */sys/class/scsi_host/host0/link_power_management_policy* would always stay at *max_performance*. Just like Chrigi I noticed that only PowerTOP seems to be able to change it.

It makes a huge difference in power consumption for me, and I hate having to start PowerTOP every time I start up my notebook to make SATA ALPM link power management take effect.

I also read [bug #427925]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/427925") which was mentioned earlier in this topic, but there’s no fix or workaround to be found there either. I’m using an Acer TimeLine 3810T (it’s near-identical variant, the Travelmate TimeLine 8371, to be exact).

Last comment in this topic was on 2 January, has any progress been made? Is there any solution to let the SATA ALPM link power management take effect without any intervention on the user’s part?

---

### Post by Walther -FI- on 2010-12-09
*Bump*

Same problem here, on Samsung N510. Powertop can't enable min_power, and it is impossible to enable from terminal, too. (echo min_power > file and tee min_power tried. On tee, the command never finishes.)

--
Walther

---

### Post by antiquity on 2011-03-05
On my machine, I first use ```
sudo su
``` to change to root privilege.
and then use ```
echo -n xx > filename
```. 
You can try that.

---

### Post by abhijeetnayak on 2011-10-26
Hello,

I have added this to .HDD_power.sh and added the script to the start
up applications.

#!/bin/bash -x
sudo su
<password>
echo -n "min_power" > /sys/class/scsi_host/host0/link_power_management_policy

Still when I am opening the powertop, it is showing SATA link has BAD performance.

I have tried all the tools but non of them working.

Please provide some fix.

---

### Post by antiquity on 2011-10-27
You just need simply put the following 
> echo -n "min_power" > /sys/class/scsi_host/host0/link_power_management_policy
into /etc/rc.local. This script will run as root when the system boot up.

---

