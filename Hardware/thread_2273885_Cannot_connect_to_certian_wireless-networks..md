---
title: "Cannot connect to certian wireless-networks."
date: 2015-04-16
forum: Hardware
---

### Post by moritz3 on 2015-04-16
Hello, 

I have problems with my Ubuntu 14.04 laptop to connect to certain wlan-networks. What works: 

* My home network
* Mobile hotspot of my cellphone

What doesn't work: 

* Any network of my university (even the unencrypted ones)

The weird thing is that they work from time to time - but other times not. Same lecture hall I can connect to any wlan, later that day I can't. Most of the time it's impossible. I'm 100% certain that it's *not* a problem with the university wlan, since I can connect just fine from my cellphone, non of the other people on the campus have the problem. 

[COLOR=#333333][FONT=Helvetica][TABLE="class: lines highlight"]
[TR]
[TD="class: line-data"][sudo] password for moritz: 
PCI (sysfs)  

H/W path         Device      Class          Description

=======================================================

                             system         P15SM (Not Applicable)

/0                           bus            P15SM

/0/0                         memory         64KiB BIOS

/0/14                        processor      Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz

/0/14/15                     memory         1MiB L2 cache

/0/14/16                     memory         256KiB L1 cache

/0/14/17                     memory         6MiB L3 cache

/0/18                        memory         16GiB System Memory

/0/18/0                      memory         8GiB SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)

/0/18/1                      memory         DIMM [empty]

/0/18/2                      memory         8GiB SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)

/0/18/3                      memory         DIMM [empty]

/0/100                       bridge         Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller

/0/100/1                     bridge         Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller

/0/100/1/0                   generic        Illegal Vendor ID

/0/100/2                     display        4th Gen Core Processor Integrated Graphics Controller

/0/100/3                     multimedia     Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller

/0/100/14                    bus            8 Series/C220 Series Chipset Family USB xHCI

/0/100/16                    communication  8 Series/C220 Series Chipset Family MEI Controller #1

/0/100/1a                    bus            8 Series/C220 Series Chipset Family USB EHCI #2

/0/100/1b                    multimedia     8 Series/C220 Series Chipset High Definition Audio Controller

/0/100/1c                    bridge         8 Series/C220 Series Chipset Family PCI Express Root Port #1

/0/100/1c.1                  bridge         8 Series/C220 Series Chipset Family PCI Express Root Port #2

/0/100/1c.1/0                bridge         XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express]

/0/100/1c.1/0/0              bus            XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express]

/0/100/1c.2                  bridge         8 Series/C220 Series Chipset Family PCI Express Root Port #3

/0/100/1c.2/0                generic        Realtek Semiconductor Co., Ltd.

/0/100/1c.2/0.2  eth0        network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller

/0/100/1c.3                  bridge         8 Series/C220 Series Chipset Family PCI Express Root Port #4

/0/100/1c.3/0    wlan0       network        Wireless 7260

/0/100/1d                    bus            8 Series/C220 Series Chipset Family USB EHCI #1

/0/100/1f                    bridge         HM87 Express LPC Controller

/0/100/1f.2                  storage        8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]

/0/100/1f.3                  bus            8 Series/C220 Series Chipset Family SMBus Controller

/0/1             scsi0       storage        

/0/1/0.0.0       /dev/sda    disk           1TB HGST HTS721010A9

/0/1/0.0.0/1     /dev/sda1   volume         558GiB EFI partition

/0/1/0.0.0/2     /dev/sda2   volume         2GiB EXT4 volume

/0/1/0.0.0/3     /dev/sda3   volume         370GiB EXT4 volume

/0/2             scsi3       storage        

/0/2/0.0.0       /dev/cdrom  disk           DVD-RAM writer

/0/3             scsi5       storage        

/0/3/0.0.0       /dev/sdb    disk           240GB Crucial_CT240M50

/0/3/0.0.0/1     /dev/sdb1   volume         285MiB EXT4 volume

/0/3/0.0.0/2     /dev/sdb2   volume         149GiB EFI partition

/0/3/0.0.0/3     /dev/sdb3   volume         29GiB EFI partition[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica][TABLE="class: lines highlight"]
[TR]
[TD="class: line-data"]$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)

00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)

00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)

00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)

00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)

00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)

00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)

00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)

00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5)

00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)

00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)

00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)

00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)

00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)

00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)

01:00.0 VGA compatible controller: NVIDIA Corporation GK104M [GeForce GTX 780M] (rev ff)

03:00.0 PCI bridge: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express] (rev 01)

04:00.0 FireWire (IEEE 1394): Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express] (rev 01)

05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)

05:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)

06:00.0 Network controller: Intel Corporation Wireless 7260 (rev 73)[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]

When I connect: 
[COLOR=#333333][FONT=Helvetica][TABLE="class: lines highlight"]
[TR]
[TD="class: line-data"]$ sudo tail -f -n 0 /var/log/syslog
Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0) starting connection 'vpn/web/belwue'

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> NetworkManager state is now CONNECTING

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0/wireless): connection 'vpn/web/belwue' requires no security.  No secrets needed.

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Config: added 'ssid' value 'vpn/web/belwue'

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Config: added 'scan_ssid' value '1'

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Config: added 'key_mgmt' value 'NONE'

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

Apr 13 16:19:14 mnbtux NetworkManager[1389]: <info> Config: set interface ap_scan to 1

Apr 13 16:19:14 mnbtux wpa_supplicant[1667]: message repeated 7 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]

Apr 13 16:19:15 mnbtux wpa_supplicant[1667]: wlan0: SME: Trying to authenticate with a0:d3:c1:9f:ef:33 (SSID='vpn/web/belwue' freq=2462 MHz)

Apr 13 16:19:15 mnbtux kernel: [ 2143.880888] wlan0: authenticate with a0:d3:c1:9f:ef:33

Apr 13 16:19:15 mnbtux kernel: [ 2143.883034] wlan0: direct probe to a0:d3:c1:9f:ef:33 (try 1/3)

Apr 13 16:19:15 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: scanning -> authenticating

Apr 13 16:19:15 mnbtux kernel: [ 2144.086080] wlan0: direct probe to a0:d3:c1:9f:ef:33 (try 2/3)

Apr 13 16:19:15 mnbtux kernel: [ 2144.292138] wlan0: direct probe to a0:d3:c1:9f:ef:33 (try 3/3)

Apr 13 16:19:15 mnbtux kernel: [ 2144.493724] wlan0: authentication with a0:d3:c1:9f:ef:33 timed out

Apr 13 16:19:15 mnbtux wpa_supplicant[1667]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="vpn/web/belwue" auth_failures=1 duration=10

Apr 13 16:19:15 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: authenticating -> disconnected

Apr 13 16:19:25 mnbtux wpa_supplicant[1667]: wlan0: CTRL-EVENT-SCAN-STARTED 

Apr 13 16:19:25 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: disconnected -> scanning

Apr 13 16:19:26 mnbtux wpa_supplicant[1667]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="vpn/web/belwue"

Apr 13 16:19:26 mnbtux wpa_supplicant[1667]: wlan0: SME: Trying to authenticate with a0:d3:c1:9f:df:b3 (SSID='vpn/web/belwue' freq=2412 MHz)

Apr 13 16:19:26 mnbtux kernel: [ 2154.657487] wlan0: authenticate with a0:d3:c1:9f:df:b3

Apr 13 16:19:26 mnbtux kernel: [ 2154.660160] wlan0: direct probe to a0:d3:c1:9f:df:b3 (try 1/3)

Apr 13 16:19:26 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: scanning -> authenticating

Apr 13 16:19:26 mnbtux kernel: [ 2154.863892] wlan0: direct probe to a0:d3:c1:9f:df:b3 (try 2/3)

Apr 13 16:19:26 mnbtux kernel: [ 2155.067376] wlan0: direct probe to a0:d3:c1:9f:df:b3 (try 3/3)

Apr 13 16:19:26 mnbtux kernel: [ 2155.270477] wlan0: authentication with a0:d3:c1:9f:df:b3 timed out

Apr 13 16:19:26 mnbtux wpa_supplicant[1667]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="vpn/web/belwue" auth_failures=2 duration=20

Apr 13 16:19:26 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: authenticating -> disconnected

Apr 13 16:19:36 mnbtux wpa_supplicant[1667]: wlan0: CTRL-EVENT-SCAN-STARTED 

Apr 13 16:19:36 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: disconnected -> scanning

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <warn> Activation (wlan0/wireless): association took too long, failing activation.

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <info> NetworkManager state is now DISCONNECTED

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <warn> Activation (wlan0) failed for connection 'vpn/web/belwue'

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <info> (wlan0): deactivating device (reason 'none') [0]

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: scanning -> inactive

Apr 13 16:19:40 mnbtux NetworkManager[1389]: <info> (wlan0): supplicant interface state: inactive -> scanning
[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
Other information: 

[TABLE="class: lines highlight"]
[TR]
[TD="class: line-data"]moritz@mnbtux:~$ uname -a

Linux mnbtux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

 

moritz@mnbtux:~$ ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:90:f5:ef:2d:92  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:65536  Metric:1

          RX packets:859 errors:0 dropped:0 overruns:0 frame:0

          TX packets:859 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:184765 (184.7 KB)  TX bytes:184765 (184.7 KB)

 

wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:dc:c0:44  

          inet addr:192.168.43.157  Bcast:192.168.43.255  Mask:255.255.255.0

          inet6 addr: fe80::e8b:fdff:fedc:c044/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:3505 errors:0 dropped:0 overruns:0 frame:0

          TX packets:3104 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2604947 (2.6 MB)  TX bytes:639866 (639.8 KB)[/TD]
[/TR]
[/TABLE]


If you need any more information, please say so. Thank you very much for your help!

---

### Post by dino99 on 2015-04-16
you may ask your university support; maybe some restrictions are in the place ):P

---

### Post by moritz3 on 2015-04-16
As I mentioned I can connect from time to time - it's just sometimes not possible. 

From time to time it works better when I kill wpa_supplicant. 

Others using a similar setup (ubuntu, same settings) can connect

It also works with my smartphone. It also works with my old notebook.

---

### Post by moritz3 on 2015-04-17
Just an additional information: I simply walked in the lecture hall this morning, now it works again without problems. So my settings weren't wrong.

---

### Post by moritz3 on 2015-04-19
Since I couldn't figure out the rules about bumping even after reading the code of conduct and I can't find any rules regarding this topic, I'll bump this thread.

---

