---
title: "HP 6715s Laptop problem...."
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by Darthter on 2007-07-12
Folks,

I'm a bit of a linux noobie, but I'm keen to get to grips with the system.

Problem is, I've just got a new laptop at work - HP 6715s - with the following spec:
    AMD Turion 64 x2
    1Gb Ram
    ATI Radeon Express 1270 graphics 
    120Gb H/D

When I try to run the 7.04 live CD, the system gets just past the menu then hangs.

If I try to run it using Virtual software (Virtual box or MS), I end up getting problems with graphics half way through the boot process.

Anyone got any ideas /pointers which might assist.  Appologies for not having more details on the actual error messages.  I'll see if I can get them noted.

Thanks
Alistair

---

### Post by srd on 2007-07-12
download ATI drivers here
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.38.6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.38.6-x86.x86_64.run)
copy to cd

download alternate cd , burn install

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

start safe mode 
insert cdrom with ati drivers
  mount  /media/cdrom0
  cd /media/cdrom0
  cp ati*     /home/username
  cd /home/username/
  sh /home/username/ati*****.sh
  aticonfig --initial
  depmod -a
reboot

another problem is  ethernet
wirless working with ndiswrapper

look for this link 
[http://forum.ubuntu-fr.org/viewtopic.php?id=77045](http://forum.ubuntu-fr.org/viewtopic.php?id=77045)

sorry for my english

---

### Post by Darthter on 2007-07-12
Thanks for the reply....

I'll give it a go & see if it works.

---

### Post by srd on 2007-07-12
for MP BIOS BUG
sudo gedit /boot/grub/menu.lst
add this
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=63c94a67-7051-4dcd-8f1b-fd6d8d140aa7 ro quiet splash** noapic**

i have hp6715b
wireless is broadcom 4311-4312
ethernet is  broadcom netlink bcm5787M

---

### Post by Darthter on 2007-07-13
Thanks for the help....managed to get it installed!!!!

---

### Post by srd on 2007-07-13
does your ethernet working
i have problem with tg3 drivers or with dhclient
I don`t now witch one
here is main: lshw -C network

   *-network               
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@10:00.0
       logical name: eth0
       version: 02
       serial: 00:17:a4:e3:16:be
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.72 latency=0 multicast=yes
       resources: iomemory:d0000000-d000ffff irq:10
  *-network
       description: Wireless interface
       product: BCM4310 UART
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@30:00.0
       logical name: wlan1
       version: 02
       serial: 00:1a:73:4e:53:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,10/12/2006, 4.100.15.5 ip=192.168.1.185 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:c8000000-c8003fff irq:11



Please write this in console : lshw -C network
post yours resault here

---

### Post by Darthter on 2007-07-14
My ethernet connection appears to be working fine.

Not really sure about the wireless....not had too much time to play about

I'll try the command suggested and post the results - won't be until Tuesday though

---

### Post by crete_des_izards on 2007-08-13
I've also got a 6715s, after much fiddling about I finally got (what appears to be) 3D acceleration working by following [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C"). However - the 'acceleration' is hopless! I get about 340 fps on glxgears. Anbody got any ideas on how too improve things?

Thanks

---

### Post by gefa on 2007-09-19
> start safe mode
There is no safe mode on altenative cd only instal to hdd or oem install :confused:

I've got 6715s,and my version have Sempron 3600+/1gb ram/80Gb hdd and i have been try install Edgy/Feisty/Gutsy several times on it and every time its freeze.

Llive Cd dont do nothing and alternatives hang on 33%, when doing disk partition at start of installing.

Also i have been try option Apicoff,its seems to do nothing,exept installer is much slower than whitout it.

32 and 64 bit version of ubuntus do the same thing no differens at all.

So i think, its only that 64 bit cpu version, where is possibility to install debian based Linux at all.

Mandriva works at fine on it...but wlan and ethernetcard are not workin on it so thats not solve a proplem   to put linux on this laptop...

---

### Post by david.wahlstedt on 2007-09-19
> **srd said:**
> for MP BIOS BUG
sudo gedit /boot/grub/menu.lst
add this
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=63c94a67-7051-4dcd-8f1b-fd6d8d140aa7 ro quiet splash** noapic**

i have hp6715b
wireless is broadcom 4311-4312
ethernet is  broadcom netlink bcm5787M

I have the same laptop. I have installed ubuntu 7.04, but there are a lot of errors, and long timeouts, and no X. To the question: If one turns off apic on a laptop, will it still work well ?
Isn't this needed for battery management and so on ?

Best, David W

---

### Post by david.wahlstedt on 2007-09-19
Have *anyone* got a successful ubuntu installation on the hp 6715s ?

On my machine it is really painful, it is not only the graphics not working, but also the hard drive and the cd/dvd seems to be extremely slow. Furthermore there is a repeated error message echoed to the console (all of them, not only no.1) about some broadcom 43xx driver, with some feature that is unsupported.


  David

---

### Post by gromada on 2007-09-23
> **david.wahlstedt said:**
> Have *anyone* got a successful ubuntu installation on the hp 6715s ?

On my machine it is really painful, it is not only the graphics not working, but also the hard drive and the cd/dvd seems to be extremely slow. Furthermore there is a repeated error message echoed to the console (all of them, not only no.1) about some broadcom 43xx driver, with some feature that is unsupported.


  David

Here is how I did it (not yet completed):
1) download ATI drivers (some ati-driver-installer....blabla...x86_64.run)
2) save it on USB stick
3) boot with (k|x)ubuntu CD
4) computer will stop in the moment where it's time to start x-windows system
5) then go to shell (ctrl+alt+F1 or F2-F6)
6) type: 'sudo su -' (to became a root)
7) put USB memory stick into the USB socket
8) you'll see the notice so you can see what drive will it be (in my case: 'sdb')
9) type: 'mount /dev/sdb /mnt'
10) type: 'cd /mnt'
11) type: 'cp ati<tab> /home/ubuntu/Desktop'
12) type: 'cd /home/ubuntu/Desktop'
13) type: 'sh ati<tab>'
14) type: 'apt-get update'
15) type: 'apt-get install xorg-driver-fglrx'
16) after installation process hase done, type: 'aticonfig --initial'
17) type: 'exit' to stop being root
18) type: 'startx'
19) You'll see Install icon on your Desktop...

Now we need more steps for audio..
For wirelless, you'l need to install bcm43xx-fwcutter, but you'll have to have bcm43xx.sys because it's mising where it should be...

[Sory for very bad english...]

---

### Post by gefa on 2007-09-24
Download Daily version 24.9-07 or later and install: [http://cdimage.ubuntu.com/kubuntu/daily/20070924/gutsy-alternate-amd64.iso]("http://cdimage.ubuntu.com/kubuntu/daily/20070924/gutsy-alternate-amd64.iso")
Don,t install any language support, just that default english version.
Turn off Wlan .
There is no X server after reboot, so login at that texmode (sorry abt my bad english)
Then type follow commands:

sudo -s
killall gdm (kdm)
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
gdm (kdm) start

If ur got erro messa like there is no xorg.conf file or somethin like that

Type dpkg-reconfigure xserver-xorg, and when its ask ur card just use ati or radeon, when ur have done that xorg.conf file type aticonfig --initial and
gdm (kdm) start again...



Thats it...

Even 3D works...

ur must use 64bit version of (K)Ubuntu, 32 bit version will crash at install, even if ur have 32 bit  Sempron version of 6715s .

---

### Post by Mindphaser on 2007-09-25
I managed to get X working with the ati drivers like mentioned above.
Gutsy seems to run tsable with the "noapic" kernel command... so far so good !

WLAN works well with ndiswrapper !

the only thing that realy realy sucks: HDD/CD (even USB) performance ! It needs 1:30mins to boot (measured with bootchart) ... if its finaly running, its running well, but bigger programs like OpenOffice need even longer than expected to start...

hdparm -tT /dev/sda is telling me that 
buffered reads are only ~5MB/s (EXTREMELY slow)
... but cached reads are around 600MB/s (which sounds normal)

I hope someone find a fix for this :-(

---

### Post by david.wahlstedt on 2007-09-29
> **gefa said:**
> Download Daily version 24.9-07 or later and install: [http://cdimage.ubuntu.com/kubuntu/daily/20070924/gutsy-alternate-amd64.iso]("http://cdimage.ubuntu.com/kubuntu/daily/20070924/gutsy-alternate-amd64.iso")
Don,t install any language support, just that default english version.
Turn off Wlan .
There is no X server after reboot, so login at that texmode (sorry abt my bad english)
Then type follow commands:

sudo -s
killall gdm (kdm)
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
gdm (kdm) start

If ur got erro messa like there is no xorg.conf file or somethin like that

Type dpkg-reconfigure xserver-xorg, and when its ask ur card just use ati or radeon, when ur have done that xorg.conf file type aticonfig --initial and
gdm (kdm) start again...



Thats it...

Even 3D works...

ur must use 64bit version of (K)Ubuntu, 32 bit version will crash at install, even if ur have 32 bit  Sempron version of 6715s .


Hi, thanks for your answer ! I have the sempron version...
Do you mean I should use the 64bit version on a 32 bit machine ? Is that possible ?
And if possible, is it good ? I mean, it would allocate double memory size ?
Does your computer perform well after this fix ?

 David

---

### Post by Mindphaser on 2007-09-29
No, his fix is only possible for the 64bit Version of this Notebook.

I have the 32bit only Semperon version too, with the "noapic" kernel parameter gutsy runs stable but the HDD slowdown is still present...
but I only feel it at boot time (und during installation), if its running its performing well, but because of noapic Hibernate/Sleep istn working, but AFAIK is this a upstream fixed bug and I hope it went into gutsy ASAP.

---

### Post by david.wahlstedt on 2007-09-30
Hi, I installed gutsy today, it took 10 hours. Only creating the ext3 partition took about 2 hours...
The system is now so slow that i dont know if x works or not: either it refuses to start, or  it havent got enough time to start. I tried the noapic boot option, but the hard rive is painfully slow, not only in the boot process, but also in all read operations. i have a quite fast broadband, and its almost faster than the hard disk ! Something very basic must be broken if the hard drive is that slow.
It seems that the system waits for something that will never happen between every disk access ?
 One should write a bug report !

David

---

### Post by Mindphaser on 2007-10-01
there is a bug report on launchpad for this, but wasnt recognised util now (2 months or so .. -.-)
maybe if more people confirm this bug, the earlier someone take a look at it... lets have a try ^^

---

### Post by david.wahlstedt on 2007-10-02
> **Mindphaser said:**
> there is a bug report on launchpad for this, but wasnt recognised util now (2 months or so .. -.-)
maybe if more people confirm this bug, the earlier someone take a look at it... lets have a try ^^

Yes, there seems to be a problem with the SATA driver. The hard drive works fine in open suse, so at least there is linux support. the kernel in suse had version number 2.6.18.2-34-default. The gusty kernel was 2.6.22... I will try open suse for a while.

 David

---

### Post by Mindphaser on 2007-10-02
> **david.wahlstedt said:**
> Yes, there seems to be a problem with the SATA driver. The hard drive works fine in open suse, so at least there is linux support. the kernel in suse had version number 2.6.18.2-34-default. The gusty kernel was 2.6.22... I will try open suse for a while.

 David

Hmmm... does it run on that kernel because of a patch in suses patchset, or is our problem a upstream regression ?
However, I would try to get the SuSE Kernel running on gutsy, and if that works try to find the patch which fixes the bug. But im not familiar with suse, where I can find the right source package for hat kernel ?

Edit: found it... now it would be helpfull to know which of all these patches if for our problem...

---

### Post by david.wahlstedt on 2007-10-07
> **Mindphaser said:**
> Hmmm... does it run on that kernel because of a patch in suses patchset, or is our problem a upstream regression ?
However, I would try to get the SuSE Kernel running on gutsy, and if that works try to find the patch which fixes the bug. But im not familiar with suse, where I can find the right source package for hat kernel ?

Edit: found it... now it would be helpfull to know which of all these patches if for our problem...

Hi, sorry for answering late. I have spent some time on my new open suse 10.2 installation, it works reasonably well with the hardware, but thats all. The software package environment is not at all comfortable compared with ubuntu. 
I send a copy of my dmesg, if that helps.

Unfortunately I dont know enough to answer your questions about the suse kernel source package.
It would be really nice if ubuntu could use the hardware support of suse---the *only* reason for me to run suse is that it works with my hardware.

---

### Post by david.wahlstedt on 2007-10-07
Here is the dmesg output:

Linux version 2.6.18.8-0.5-default (geeko@buildhost) (gcc version 4.1.2 20061115 (prerelease) (SUSE Linux)) #1 SMP Fri Jun 22 12:17:53 UTC 2007
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000037fb0000 (usable)
 BIOS-e820: 0000000037fb0000 - 0000000037fc8000 (reserved)
 BIOS-e820: 0000000037fc8000 - 0000000037fe7fb8 (ACPI NVS)
 BIOS-e820: 0000000037fe7fb8 - 0000000040000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
 BIOS-e820: 00000000ffbc0000 - 00000000ffcc0000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
895MB LOWMEM available.
On node 0 totalpages: 229296
  DMA zone: 4096 pages, LIFO batch:0
  Normal zone: 225200 pages, LIFO batch:31
DMI 2.4 present.
Using APIC driver default
IO/L-APIC allowed because system is MP or new enough
ACPI: RSDP (v002 HP                                    ) @ 0x000fe0b0
ACPI: XSDT (v001 HPQOEM SLIC-MPC 0x00000001 HP   0x00000001) @ 0x37fc81bc
ACPI: FADT (v004 HP     0944     0x00000003 HP   0x00000001) @ 0x37fc8084
ACPI: SLIC (v001 HPQOEM SLIC-MPC 0x00000001 HP   0x00000001) @ 0x37fc8220
ACPI: EPTH (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x37fc8398
ACPI: MADT (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x37fc83d0
ACPI: MCFG (v001 HP     0944     0x00000001 HP   0x00000001) @ 0x37fc8434
ACPI: TCPA (v002 HP     0944     0x00000001 HP   0x00000001) @ 0x37fc8470
ACPI: SSDT (v001 HP       HPQNLP 0x00000001 MSFT 0x03000001) @ 0x37fd98db
ACPI: SSDT (v001 HP     PSSTBLID 0x00000001 HP   0x00000001) @ 0x37fd9934
ACPI: DSDT (v001 HP        SB400 0x00010000 MSFT 0x03000001) @ 0x00000000
ATI board detected. Disabling timer routing over 8254.
ACPI: PM-Timer IO Port: 0x8008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:12 APIC version 16
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
Detected 1993.878 MHz processor.
Built 1 zonelists.  Total pages: 229296
Kernel command line: root=/dev/sda6 vga=0x314 resume=/dev/sda5 splash=silent
bootsplash: silent mode.
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Console: colour dummy device 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 902024k/917184k available (1697k kernel code, 14540k reserved, 1000k data, 196k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 3999.53 BogoMIPS (lpj=7999061)
Security Framework v1.0.0 initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
CPU: After vendor identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 16k freed
checking if image is initramfs... it is
Freeing initrd memory: 3211k freed
ACPI: Core revision 20060707
CPU0: AMD Mobile AMD Sempron(tm) Processor 3600+ stepping 02
Total of 1 processors activated (3999.53 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
..MP-BIOS bug: 8254 timer not connected to IO-APIC
...trying to set up timer (IRQ0) through the 8259A ...  failed.
...trying to set up timer as Virtual Wire IRQ... works.
Brought up 1 CPUs
migration_cost=0
HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: Using MMCONFIG
PCI: No mmconfig possible on 0:18
Setting up standard PCI resources
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [C08B] (0000:00)
PCI: Probing PCI hardware (bus 00)
ACPI: Assume root bridge [\_SB_.C08B] bus is 0
PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
Boot video device is 0000:01:05.0
PCI: Transparent bridge - 0000:00:14.4
PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#03) (try 'pci=assign-busses')
Please report the result to linux-kernel to fix this permanently
ACPI: PCI Interrupt Routing Table [\_SB_.C08B._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C08C._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.C08B.C0FC._PRT]
ACPI: Power Resource [C171] (off)
ACPI: Embedded Controller [C172] (gpe 17) interrupt mode.
ACPI: Power Resource [C24C] (on)
ACPI: PCI Interrupt Link [C145] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [C146] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [C147] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [C148] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [C149] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [C14A] (IRQs 9) *0, disabled.
ACPI: PCI Interrupt Link [C14B] (IRQs 10 11) *0, disabled.
ACPI: PCI Interrupt Link [C14C] (IRQs 10 11) *0, disabled.
ACPI: Power Resource [C395] (off)
ACPI: Power Resource [C396] (off)
ACPI: Power Resource [C397] (off)
ACPI: Power Resource [C398] (off)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 11 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
PCI: Cannot allocate resource region 0 of device 0000:00:14.2
pnp: 00:08: ioport range 0x40b-0x40b has been reserved
pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:09: ioport range 0x8000-0x802f could not be reserved
pnp: 00:09: ioport range 0x8100-0x811f could not be reserved
PCI: Ignore bogus resource 6 [0:0] of 0000:01:05.0
PCI: Bridge: 0000:00:01.0
  IO window: 4000-4fff
  MEM window: d0200000-d03fffff
  PREFETCH window: c0000000-c7ffffff
PCI: Bridge: 0000:00:04.0
  IO window: disabled.
  MEM window: d0000000-d00fffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:05.0
  IO window: 2000-3fff
  MEM window: cc000000-cfffffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:06.0
  IO window: disabled.
  MEM window: c8000000-c80fffff
  PREFETCH window: disabled.
PCI: Bus 3, cardbus bridge: 0000:02:04.0
  IO window: 00001000-000010ff
  IO window: 00001400-000014ff
  PREFETCH window: 50000000-51ffffff
  MEM window: 54000000-55ffffff
PCI: Bridge: 0000:00:14.4
  IO window: 1000-1fff
  MEM window: d0100000-d01fffff
  PREFETCH window: 50000000-51ffffff
PCI: Setting latency timer of device 0000:00:04.0 to 64
PCI: Setting latency timer of device 0000:00:05.0 to 64
PCI: Setting latency timer of device 0000:00:06.0 to 64
ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 169
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
Machine check exception polling timer started.
apm: BIOS not found.
audit: initializing netlink socket (disabled)
audit(1191760159.192:1): initialized
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
PCI: Setting latency timer of device 0000:00:04.0 to 64
pcie_portdrv_probe->Dev[7914:1002] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:04.0:pcie00]
Allocate Port Service[0000:00:04.0:pcie03]
PCI: Setting latency timer of device 0000:00:05.0 to 64
pcie_portdrv_probe->Dev[7915:1002] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:05.0:pcie00]
Allocate Port Service[0000:00:05.0:pcie03]
PCI: Setting latency timer of device 0000:00:06.0 to 64
pcie_portdrv_probe->Dev[7916:1002] has invalid IRQ. Check vendor BIOS
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:06.0:pcie00]
Allocate Port Service[0000:00:06.0:pcie03]
vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 3750k, total 16384k
vesafb: mode is 800x600x16, linelength=1600, pages=16
vesafb: protected mode interface info at c000:9f30
vesafb: pmi: set display start = c00c9fba, set palette = c00ca078
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
bootsplash 3.1.6-2004/03/31: looking for picture...<6> silentjpeg size 82985 bytes,<6>...found (800x600, 49016 bytes, v3).
Console: switching to colour frame buffer device 96x33
fb0: VESA VGA frame buffer device
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Floppy drive(s): fd0 is 1.44M
floppy0: no floppy controllers found
RAMDISK driver initialized: 16 RAM disks of 64000K size 1024 blocksize
PNP: PS/2 Controller [PNP0303:C249,PNP0f13:C24A] at 0x60,0x64 irq 1,12
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
input: PC Speaker as /class/input/input0
md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
md: bitmap version 4.39
NET: Registered protocol family 1
Using IPI No-Shortcut mode
ACPI: (supports S0 S3 S4<6>Time: tsc clocksource has been installed.
 S5)
Freeing unused kernel memory: 196k freed
input: AT Translated Set 2 keyboard as /class/input/input1
synaptics reset failed
synaptics reset failed
synaptics reset failed
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SCSI subsystem initialized
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
ACPI: Processor [C000] (supports 8 throttling states)
ACPI Exception (acpi_processor-0681): AE_NOT_FOUND, Processor Device is not present [20060707]
ACPI: Getting cpuindex for acpiid 0x2
ACPI: Thermal Zone [TZ1] (36 C)
libata version 2.00 loaded.
ahci 0000:00:12.0: version 2.0
ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 209
Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
serio: Synaptics pass-through port at isa0060/serio4/input0
input: SynPS/2 Synaptics TouchPad as /class/input/input2
Time: acpi_pm clocksource has been installed.
ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
ahci 0000:00:12.0: flags: 64bit ncq ilck pm led clo pio slum part 
ata1: SATA max UDMA/133 cmd 0xF8D20100 ctl 0x0 bmdma 0x0 irq 209
ata2: SATA max UDMA/133 cmd 0xF8D20180 ctl 0x0 bmdma 0x0 irq 209
ata3: SATA max UDMA/133 cmd 0xF8D20200 ctl 0x0 bmdma 0x0 irq 209
ata4: SATA max UDMA/133 cmd 0xF8D20280 ctl 0x0 bmdma 0x0 irq 209
scsi0 : ahci
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: ATA-7, max UDMA/100, 156301488 sectors: LBA48 
ata1.00: ata1: dev 0 multi count 16
ata1.00: configured for UDMA/100
scsi1 : ahci
ata2: SATA link down (SStatus 0 SControl 0)
scsi2 : ahci
ata3: SATA link down (SStatus 0 SControl 0)
scsi3 : ahci
ata4: SATA link down (SStatus 0 SControl 0)
  Vendor: ATA       Model: TOSHIBA MK8037GS  Rev: DL23
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
 sda: sda1 sda2 sda3 < sda5 sda6 >
sd 0:0:0:0: Attached scsi disk sda
SB600_PATA: IDE controller at PCI slot 0000:00:14.1
ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 209
sd 0:0:0:0: Attached scsi generic sg0 type 0
SB600_PATA: chipset revision 0
SB600_PATA: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x5040-0x5047, BIOS settings: hda:DMA, hdb:pio
Probing IDE interface ide0...
hda: HL-DT-ST DVDRAM GSA-T20L, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
ACPI: Transitioning device [C399] to D3
ACPI: Transitioning device [C399] to D3
ACPI: Fan [C399] (off)
ACPI: Transitioning device [C39A] to D3
ACPI: Transitioning device [C39A] to D3
ACPI: Fan [C39A] (off)
ACPI: Transitioning device [C39B] to D3
ACPI: Transitioning device [C39B] to D3
ACPI: Fan [C39B] (off)
ACPI: Transitioning device [C39C] to D3
ACPI: Transitioning device [C39C] to D3
ACPI: Fan [C39C] (off)
BIOS EDD facility v0.16 2004-Jun-25, 1 devices found
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3 FS on sda6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ndiswrapper version 1.25 loaded (preempt=no,smp=yes)
ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
ACPI: PCI Interrupt 0000:30:00.0[A] -> GSI 18 (level, low) -> IRQ 217
PCI: Setting latency timer of device 0000:30:00.0 to 64
ndiswrapper: using IRQ 217
wlan0: vendor: ''
wlan0: ethernet device 00:1a:73:78:84:79 using NDIS driver bcmwl5, 14E4:4312.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
usbcore: registered new driver ndiswrapper
Linux agpgart interface v0.101 (c) Dave Jones
ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 23 (level, low) -> IRQ 225
ohci_hcd 0000:00:13.0: OHCI Host Controller
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:13.0: irq 225, io mem 0xd0401000
usb usb1: new device found, idVendor=0000, idProduct=0000
usb usb1: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: OHCI Host Controller
usb usb1: Manufacturer: Linux 2.6.18.8-0.5-default ohci_hcd
usb usb1: SerialNumber: 0000:00:13.0
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 233
ohci_hcd 0000:00:13.1: OHCI Host Controller
ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:13.1: irq 233, io mem 0xd0402000
usb usb2: new device found, idVendor=0000, idProduct=0000
usb usb2: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb2: Product: OHCI Host Controller
usb usb2: Manufacturer: Linux 2.6.18.8-0.5-default ohci_hcd
usb usb2: SerialNumber: 0000:00:13.1
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 17 (level, low) -> IRQ 233
ohci_hcd 0000:00:13.2: OHCI Host Controller
ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
ohci_hcd 0000:00:13.2: irq 233, io mem 0xd0403000
usb 1-2: new full speed USB device using ohci_hcd and address 2
hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
Uniform CD-ROM driver Revision: 3.20
usb usb3: new device found, idVendor=0000, idProduct=0000
usb usb3: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb3: Product: OHCI Host Controller
usb usb3: Manufacturer: Linux 2.6.18.8-0.5-default ohci_hcd
usb usb3: SerialNumber: 0000:00:13.2
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 233
ohci_hcd 0000:00:13.3: OHCI Host Controller
ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
ohci_hcd 0000:00:13.3: irq 233, io mem 0xd0404000
usb 1-2: new device found, idVendor=03f0, idProduct=171d
usb 1-2: new device strings: Mfr=1, Product=2, SerialNumber=0
usb 1-2: Product: HP Integrated Module
usb 1-2: Manufacturer: Broadcom Corp
usb 1-2: configuration #1 chosen from 1 choice
usb usb4: new device found, idVendor=0000, idProduct=0000
usb usb4: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb4: Product: OHCI Host Controller
usb usb4: Manufacturer: Linux 2.6.18.8-0.5-default ohci_hcd
usb usb4: SerialNumber: 0000:00:13.3
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 17 (level, low) -> IRQ 233
ohci_hcd 0000:00:13.4: OHCI Host Controller
ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
ohci_hcd 0000:00:13.4: irq 233, io mem 0xd0405000
usb usb5: new device found, idVendor=0000, idProduct=0000
usb usb5: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb5: Product: OHCI Host Controller
usb usb5: Manufacturer: Linux 2.6.18.8-0.5-default ohci_hcd
usb usb5: SerialNumber: 0000:00:13.4
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 23 (level, low) -> IRQ 225
ehci_hcd 0000:00:13.5: EHCI Host Controller
ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
ehci_hcd 0000:00:13.5: debug port 1
ehci_hcd 0000:00:13.5: irq 225, io mem 0xd0406000
ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb6: new device found, idVendor=0000, idProduct=0000
usb usb6: new device strings: Mfr=3, Product=2, SerialNumber=1
usb usb6: Product: EHCI Host Controller
usb usb6: Manufacturer: Linux 2.6.18.8-0.5-default ehci_hcd
usb usb6: SerialNumber: 0000:00:13.5
usb usb6: configuration #1 chosen from 1 choice
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 10 ports detected
usb 1-2: USB disconnect, address 2
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 209
ohci_hcd 0000:00:13.0: wakeup
Bluetooth: Core ver 2.10
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
[fglrx] Maximum main memory to use for locked dma buffers: 804 MBytes.
[fglrx] module loaded - fglrx 8.36.5 [Apr 17 2007] on minor 0
Bluetooth: HCI USB driver ver 2.9
usbcore: registered new driver hci_usb
usb 1-2: new full speed USB device using ohci_hcd and address 3
Yenta: CardBus bridge found at 0000:02:04.0 [103c:30c2]
Yenta: ISA IRQ mask 0x0cb8, PCI irq 169
Socket status: 30000006
Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
pcmcia: parent PCI bridge I/O window: 0x1000 - 0x1fff
cs: IO port probe 0x1000-0x1fff: clean.
pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
usb 1-2: new device found, idVendor=03f0, idProduct=171d
usb 1-2: new device strings: Mfr=1, Product=2, SerialNumber=0
usb 1-2: Product: HP Integrated Module
usb 1-2: Manufacturer: Broadcom Corp
usb 1-2: configuration #1 chosen from 1 choice
pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
cs: IO port probe 0x100-0x3af: clean.
cs: IO port probe 0x3e0-0x4ff: clean.
cs: IO port probe 0x820-0x8ff: clean.
cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
cs: IO port probe 0xa00-0xaff: clean.
Adding 2104472k swap on /dev/sda5.  Priority:-1 extents:1 across:2104472k
device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: [email]dm-devel@redhat.com[/email]
loop: loaded (max 8 devices)
AppArmor: AppArmor initialized
audit(1191760200.827:2): AppArmor initialized

ACPI: AC Adapter [C1EB] (on-line)
ACPI: Battery Slot [C1ED] (battery present)
ACPI: Battery Slot [C1EC] (battery absent)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [C28D]
ACPI: Lid Switch [C265]
powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3600+ processors (version 2.00.00)
powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x12
powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
powernow-k8: ph2 null fid transition 0xc
audit(1191753035.496:3): audit_pid=3164 old=0 by auid=4294967295
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
IPv6 over IPv4 tunneling driver
ADDRCONF(NETDEV_UP): wlan0: link is not ready
bootsplash: status on console 0 changed to on
ACPI: PCI Interrupt 0000:01:05.0[B] -> GSI 19 (level, low) -> IRQ 50
[fglrx] Maximum main memory to use for locked dma buffers: 804 MBytes.
[fglrx] total      GART = 130023424
[fglrx] free       GART = 114032640
[fglrx] max single GART = 114032640
[fglrx] total      LFB  = 134217728
[fglrx] free       LFB  = 119828480
[fglrx] max single LFB  = 119828480
[fglrx] total      Inv  = 0
[fglrx] free       Inv  = 0
[fglrx] max single Inv  = 0
[fglrx] total      TIM  = 0
hda-intel: Invalid position buffer, using LPIB read method instead.
NET: Registered protocol family 17
ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wlan0: no IPv6 routers present
ACPI: Transitioning device [C39B] to D0
ACPI: Transitioning device [C39B] to D0
ACPI: Unable to turn cooling device [dffdc748] 'on'
st: Version 20050830, fixed bufsize 32768, s/g segs 256
ACPI: Transitioning device [C39C] to D0
ACPI: Transitioning device [C39C] to D0
ACPI: Unable to turn cooling device [dffdc6f8] 'on'
ACPI: Transitioning device [C39A] to D0
ACPI: Transitioning device [C39A] to D0
ACPI: Unable to turn cooling device [dffdec48] 'on'

---

### Post by Mindphaser on 2007-10-13
I had no luck with the Suse Kernels...I was able to apply the suse-patchset and compiled it, but running it made everything even slower, at least on the current 2.6.18 kernel... the Suse 10.3 Kernel (2.6.22.something) runs exactly good/bad like the current Gutsy Ubuntu kernel...

I` ve also tried 2.6.23-rc8 (vanilla) without luck... runs good but with the usual problems :-(

---

### Post by david.wahlstedt on 2007-10-19
> **Mindphaser said:**
> I had no luck with the Suse Kernels...I was able to apply the suse-patchset and compiled it, but running it made everything even slower, at least on the current 2.6.18 kernel... the Suse 10.3 Kernel (2.6.22.something) runs exactly good/bad like the current Gutsy Ubuntu kernel...

I` ve also tried 2.6.23-rc8 (vanilla) without luck... runs good but with the usual problems :-(

Hi, 
strange... and disssapoinitng :(
So, what part of the suse kernel deals with SATA ? Maybe it is just a matter of settings ?
As I said, I don't knoe that much linux, but I can try to find out.

 David

---

### Post by Mindphaser on 2007-12-04
Some SUCCESS !!

I compiled kernel 2.6.24-rc4... since rc2 (or rc3, dont know) it boots without the noapic kernel parameter... but sooner or later the system hangs with a black scrren as usual.

Now with rc4, IF I come far enough without noapic, HDD performance is NORMAL !!
Hdparm says ~38 MB/s where it was up to 4 MB/s previously.... with noapic its slow than before, so it looks like that the apic-issue have something to do with sata-performance ... hell, its nice to see the system boot in less than one minute ^^

Another thing i figured out, is that if I have "bootchart" installed, the system actually boots faster than without... strange strange ...

Well, lets hope they fix it ASAP, but at least there is some progress in that issue

---

### Post by torpe0 on 2007-12-06
Only trouble with mine is wireless. Driver installed in ndiswrapper, and reporting hardware present, but it just doesn't find any network. I use the bcml5 driver, right?

..Tor Arne

---

### Post by mbolbroe on 2008-01-13
> **gefa said:**
> Download Daily version 24.9-07 or later and install: [http://cdimage.ubuntu.com/kubuntu/daily/20070924/gutsy-alternate-amd64.iso]("http://cdimage.ubuntu.com/kubuntu/daily/20070924/gutsy-alternate-amd64.iso")
Don,t install any language support, just that default english version.
Turn off Wlan .
There is no X server after reboot, so login at that texmode (sorry abt my bad english)
Then type follow commands:

sudo -s
killall gdm (kdm)
apt-get install xorg-driver-fglrx
depmod -a
aticonfig --initial
gdm (kdm) start

If ur got erro messa like there is no xorg.conf file or somethin like that

Type dpkg-reconfigure xserver-xorg, and when its ask ur card just use ati or radeon, when ur have done that xorg.conf file type aticonfig --initial and
gdm (kdm) start again...



Thats it...

Even 3D works...

ur must use 64bit version of (K)Ubuntu, 32 bit version will crash at install, even if ur have 32 bit  Sempron version of 6715s .
Success!!
I w a s the former sad owner of one particular HP6715s 2.2 GHz Sempron Laptop. 
But after this little trick I now have Ubuntu 7.10 running.

Thank You - so much!

ps. By the way I found out that the correct syntax for the aticonfig  is following(also stated in the help file):

aticonfig --initial --input=/etc/X11/xorg.conf

---

### Post by gefa on 2008-01-14
> **david.wahlstedt said:**
> Have *anyone* got a successful ubuntu installation on the hp 6715s ?

On my machine it is really painful, it is not only the graphics not working, but also the hard drive and the cd/dvd seems to be extremely slow. Furthermore there is a repeated error message echoed to the console (all of them, not only no.1) about some broadcom 43xx driver, with some feature that is unsupported.


  David
***Here is complete installation for this laptop***

Install from 64 bit version of Ubuntu Gutsy, even if you have 32 bit Sempron version, 32 bit Ubuntus do not work on this one.

To avoid number of errors,turn off wlan while install.

After reboot you have only console mode, cause missing ati driver.

Push CTRL+ALT+F4 to login in consolemode.*

 
Ati Driver Installation in console mode: 

killall gdm

apt-get install xorg-driver-fglrx

depmod -a

aticonfig --initial
  

Reboot



BCM4312 Wlan Installation: 
 Step 1: All BCM43xx - Install NDISWrapper and Blacklist Native Driver

Open Console: 

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx



 

 Step 2: sp34152 Driver Download/Extraction



sudo apt-get install cabextract 

wget [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)  

cabextract sp34152.exe

 

Configure NDISWrapper 

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

 

Reboot 

 

 

 *Don't allow any updates to Ubuntu,before you have install  Nidiswrapper for Wlan.

---

### Post by foxyfoxtrot on 2008-02-20
> **srd said:**
> download ATI drivers here
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.38.6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.38.6-x86.x86_64.run)
copy to cd

download alternate cd , burn install

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

start safe mode 
insert cdrom with ati drivers
  mount  /media/cdrom0
  cd /media/cdrom0
  cp ati*     /home/username
  cd /home/username/
  sh /home/username/ati*****.sh
  aticonfig --initial
  depmod -a
reboot

another problem is  ethernet
wirless working with ndiswrapper

look for this link 
[http://forum.ubuntu-fr.org/viewtopic.php?id=77045](http://forum.ubuntu-fr.org/viewtopic.php?id=77045)

sorry for my english
I get as far as cd/home/usename but with the line sh /home/username/ati*****.sh I get the message : sh Can't open /home ......

---

### Post by ashrack on 2008-03-18
> **Mindphaser said:**
> Some SUCCESS !!

I compiled kernel 2.6.24-rc4... since rc2 (or rc3, dont know) it boots without the noapic kernel parameter... but sooner or later the system hangs with a black scrren as usual.

Now with rc4, IF I come far enough without noapic, HDD performance is NORMAL !!
Hdparm says ~38 MB/s where it was up to 4 MB/s previously.... with noapic its slow than before, so it looks like that the apic-issue have something to do with sata-performance ... hell, its nice to see the system boot in less than one minute ^^

Another thing i figured out, is that if I have "bootchart" installed, the system actually boots faster than without... strange strange ...

Well, lets hope they fix it ASAP, but at least there is some progress in that issue
did you fix this problems?
I am expirencing very slow disk performance with Feisty. HDPARM reports about 600KB/s buffered disk read.
With Hardy it halts during installation saying it can not read from the CD. When trying with the UNNET method which install Hardy direct from the net it freezes with black screen during install in text mode

---

### Post by Biodrome on 2008-05-02
Hi to all........!!! Earlier I was using Ubuntu widout a single glitch on my desktop which had an Intel P4 processor and 845GVS motherboard. But then I got HP Compaq 6715s laptop with AMD Turion 64 X2 processor and ATI Radeon X1250 graphics processor. I downloaded the 64-bit edition of Ubuntu and also ordered the fre CDs but something juzz getz stuck up after the loading screen and I think there is some problem with the graphics driver. I really love Ubuntu. Plz plz sumone tell me how to get it up and running on my current PC. Thanx a ton in advance to the one who solves this problem of mine. And neone owning the same laptop, cud u juzz tell if it is fit for any other linux......??? M really repenting on buyin this one..... missing Linux all da tym.......... Plz help me.:confused:

---

### Post by ashrack on 2008-05-02
I got it working by appending the following to the kernel of the alternate CD:
```
acpi=off pnpbios=off
```
and after the install is successful you have to install the property FGLRX driver probably from text mode.

With the acpi=off you should note that you will receive no power saving on the notebook and when you will shut down Ubuntu it will not shutdown the machine automaticly but you will have to do it manually.

---

