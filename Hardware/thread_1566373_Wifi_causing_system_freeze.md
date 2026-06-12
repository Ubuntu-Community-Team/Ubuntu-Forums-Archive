---
title: "Wifi causing system freeze"
date: 2010-09-02
forum: Hardware
---

### Post by axyelp on 2010-09-02
I've noticed this since the time i bought this laptop(thats about two weeks back) that the system freezes when i try to enable/disable the wifi service(ifconfig wlan0 down). and now that i've got a wifi network, the freezes are just too frequent.

To make the laptop run a bit faster and the battery last longer, i've disabled a number of services and startup programs!
i believe that's causing the problem, since it subsequently decreased the memory usage!

here's my list of running services:
$service --status-all
[http://pastebin.com/mZXTXPMZ](http://pastebin.com/mZXTXPMZ)

$ uname -a
Linux zed 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid


thanks!

---

### Post by axyelp on 2010-09-05
bump!!!

---

### Post by axyelp on 2010-09-07
ummmm, bump???

---

### Post by axyelp on 2010-09-10
please help!

the machine freezes nearly 8 to 10 times a day!
a single suspend can ask the wifi to reconnect and it hangs up!

its just unbearable!

---

### Post by hsoulen on 2010-09-10
Hi there.

A bit more info might help:


[LIST=1]
[*]Brand and model of the laptop
[*]Output of "lspci" so we can see what WiFi card you are working with
[/LIST]

Cheers,

Hank

---

### Post by axyelp on 2010-09-11
here's my lspci:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```


and $lshw -short
```
H/W path           Device      Class          Description
=========================================================
                       system         0578HNQ
/0                             bus            0578HNQ
/0/0                           memory         117KiB BIOS
/0/4                           processor      Intel(R) Core(TM) i5 CPU       M 450  @ 2.40GHz
/0/4/5                         memory         32KiB L1 cache
/0/4/6                         memory         256KiB L2 cache
/0/4/7                         memory         3MiB L3 cache
/0/1b                          memory         2GiB System Memory
/0/1b/0                        memory         2GiB SODIMM Synchronous 1066 MHz (0.9 ns)
/0/1b/1                        memory         SODIMM Synchronous [empty]
/0/100                         bridge         Core Processor DRAM Controller
/0/100/2                       display        Core Processor Integrated Graphics Controller
/0/100/16                      communication  5 Series/3400 Series Chipset HECI Controller
/0/100/1a                      bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1b                      multimedia     5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                      bridge         5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c.1                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 2
/0/100/1c.1/0      wlan0       network        Realtek Semiconductor Co., Ltd.
/0/100/1c.2                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 3
/0/100/1c.3                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 4
/0/100/1c.4                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 5
/0/100/1c.5                    bridge         5 Series/3400 Series Chipset PCI Express Root Port 6
/0/100/1c.5/0      eth0        network        RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1d                      bus            5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1f                      bridge         Mobile 5 Series Chipset LPC Interface Controller
/0/100/1f.2        scsi0       storage        5 Series/3400 Series Chipset 4 port SATA IDE Controller
/0/100/1f.2/0      /dev/sda    disk           500GB FUJITSU MJA2500B
/0/100/1f.2/0/1    /dev/sda1   volume         40GiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume         29GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume         395GiB Extended partition
/0/100/1f.2/0/3/5  /dev/sda5   volume         169GiB HPFS/NTFS partition
/0/100/1f.2/0/3/6  /dev/sda6   volume         79GiB HPFS/NTFS partition
/0/100/1f.2/0/3/7  /dev/sda7   volume         70GiB HPFS/NTFS partition
/0/100/1f.2/0/3/8  /dev/sda8   volume         29GiB Linux filesystem partition
/0/100/1f.2/0/3/9  /dev/sda9   volume         20GiB Linux filesystem partition
/0/100/1f.2/0/3/a  /dev/sda10  volume         23GiB Linux filesystem partition
/0/100/1f.2/0/3/b  /dev/sda11  volume         2047MiB Linux swap / Solaris partition
/0/100/1f.2/1      /dev/cdrom  disk           DVD RW AD-7700H
/0/100/1f.3                    bus            5 Series/3400 Series Chipset SMBus Controller
/0/100/1f.6                    generic        5 Series/3400 Series Chipset Thermal Subsystem
/0/101                         bridge         Core Processor QuickPath Architecture Generic Non-core Registers
/0/102                         bridge         Core Processor QuickPath Architecture System Address Decoder
/0/103                         bridge         Core Processor QPI Link 0
/0/104                         bridge         Core Processor QPI Physical 0
/0/105                         bridge         Core Processor Reserved
/0/106                         bridge         Core Processor Reserved
/0/1               scsi2       storage        
/0/1/0.0.0         /dev/sdb    disk           SCSI Disk

```

wifi runs pretty well, it just reboots a bit too frequently at reconnections or while turning wifi on/off (up/down using ifconfig)!
do i need to install the drivers? i got them from realtek's website, but i fear it might turn the already working wifi dead.

---

### Post by hsoulen on 2010-09-13
Hi There,

I have an RTL8192 and had similar problems with Wireless.

Although your 8172 is supported native in the 10.04 2.6.x kernels (mine was not but running regressed kernels for 10.10 work... Mostly) you may have better luck with the drivers from Realtek.

I run the Realtek driver because it is simply more reliable for me, I rarely have any drops anymore and I connect to several networks (WEP/WPA/2 Personal/enterprise as well as a corporate network using certificates).

Best advice I can provide is try the driver from Realtek, worst case it does not work well for you so you simply run "sudo make uninstall" and reboot, back to the stock kernel driver.

Just keep in mind that if you do choose the Realtek driver you will need to re-compile and install for every major kernel update, this can be a bit of a hassle but for me is worth the stability.

Good luck!

Hank

---

### Post by axyelp on 2010-09-14
> **hsoulen said:**
> Hi There,

I have an RTL8192 and had similar problems with Wireless.

Although your 8172 is supported native in the 10.04 2.6.x kernels (mine was not but running regressed kernels for 10.10 work... Mostly) you may have better luck with the drivers from Realtek.

I run the Realtek driver because it is simply more reliable for me, I rarely have any drops anymore and I connect to several networks (WEP/WPA/2 Personal/enterprise as well as a corporate network using certificates).

Best advice I can provide is try the driver from Realtek, worst case it does not work well for you so you simply run "sudo make uninstall" and reboot, back to the stock kernel driver.

Just keep in mind that if you do choose the Realtek driver you will need to re-compile and install for every major kernel update, this can be a bit of a hassle but for me is worth the stability.

Good luck!

Hank

Thanks! I plan to do that.
But what did you mean by recompiling kernel updates? just recompiling the same generic kernel right? I'd be doing it for the first time now, so wanted to know!

p.s your signature's,.. elegant!!!

---

### Post by hsoulen on 2010-09-16
No worries,

What I meant was that you will need to recompile the wireless driver for the kernel (build the kernel module) for each new kernel release, not the kernel itself.

Just some tips below:

[LIST=1]
[*] Make sure you have kernel headers installed (just check in Synaptic "linux-headers-generic") This should be the default in Ubuntu but you never know...
[*] Check the Realtek site for the most recent driver
[*] Do not unpack the driver archive to the desktop as this causes problems with compiling the driver, unpack it to something like "~/Drivers" then run the following from the terminal:
[*] cd rtl8192se_linux_2.6.0015.0127.2010 (or whatever the driver folder name you unpacked the driver to)
[*] sudo su (to become "Super user")
[*] make
[*] make install
[/LIST]

You can also remove the driver with "make uninstall" from the same directory should you need to.

You will need to re-make the driver every time you install a new kernel (bit of a pain) but wireless works very well with this driver.

Cheers,

Hank

---

### Post by axyelp on 2010-10-28
wohow!
its been a month! and not a single crash due to wifi!
seems to work perfect!

Thanks a lot Hank

---

### Post by hsoulen on 2010-11-04
> **axyelp said:**
> wohow!
its been a month! and not a single crash due to wifi!
seems to work perfect!

Thanks a lot Hank

Cool, glad to help!

Hank

---

