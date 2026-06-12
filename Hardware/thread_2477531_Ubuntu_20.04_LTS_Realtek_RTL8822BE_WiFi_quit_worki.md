---
title: "Ubuntu 20.04 LTS Realtek RTL8822BE WiFi quit working with Kernel Update to 5.15.0-41"
date: 2022-07-28
forum: Hardware
---

### Post by DWade on 2022-07-28
Upon the update to the latest Kernel in July; 5.15.0-41-generic; The Wifi quit working. As soon as wifi is accessed it disconnects, then starts trying to reconnect, then errors out removing all WiFi Network information.

As of now, I have searched the Forum, I have searched Google, I have tried past Realtek RTL8822BE fixes, I reloaded the Realtek drivers I have reloaded the Kernel. Nothing that I have tried works.

With automatic Kernel install and deinstall of the oldest kernel, I am not sure where to go. The last working kernel is "Kernel Linux 5.13.0-52-generic x86_64".  I have that selected to use since the other won't allow the Wifi to work and, that is How I get internet.

My notebook is an HP - Pavilion - 15-CS2083
intel I7 8th generation
8 GB memory
512 SSD

Dual EFI secure boot, Windows 11 and Ubuntu Linux Release 20.04.4 LTS (Focal Fossa) 64-bit.

---

### Post by #&amp;thj^% on 2022-07-28
Can you show us this, to better help you:
```
sudo dkms status

```
and:
```
lsmod | grep 8822BE
```

---

### Post by DWade on 2022-07-29
Here dkms status
[david@david-HP-Pavilion-15-cs2083:~$ sudo dkms status
8812au, 5.6.4.2_35491.20191025, 5.15.0-41-generic, x86_64: installed
virtualbox, 6.1.34, 5.13.0-52-generic, x86_64: installed
virtualbox, 6.1.34, 5.15.0-41-generic, x86_64: installed
virtualbox, 6.1.34, 5.4.0-122-generic, x86_64: installed]

here is lsmod
[david@david-HP-Pavilion-15-cs2083:~$ lsmod | grep 8822BE
david@david-HP-Pavilion-15-cs2083:~$ ]

 bash Commands I have done before posting;
sudo apt-get install -f
sudo apt update --fix-missing
dpkg --configure -a
sudo dpkg --configure -a
sudo apt-get install -f
ubuntu-drivers list-oem
hwe-support-status --verbose
sudo apt-get install --install-recommends linux-generic-hwe-20.04
sudo apt-get install --reinstall linux-image-generic linux-image
sudo apt-get install --reinstall-recommends linux-generic-hwe-20.04
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get install --reinstall linux-image-generic linux-image
sudo apt-get install --reinstall-recommends linux-generic-hwe-20.04
sudo apt-get install --install-recommends linux-generic-hwe-20.04
sudo apt-get install &#8211;-reinstall linux-image-generic linux-generic-hwe-20.04
sudo apt-get install --install-recommends linux-generic-hwe-20.04
sudo apt-get install --reinstall linux-image-generic linux-image-5.15.0-41-generic
sudo apt-get install --install-recommends linux-generic-hwe-20.04

sudo systemctl status networking
sudo /etc/init.d/networking restart
sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start
sudo systemctl restart networking
netplan apply
sudo netplan apply
sudo systemctl restart networking
sudo systemctl restart wi-fi
sudo systemctl restart wifi

sudo apt-get install linux-headers-generic
lspci
lspci -vv -s 01:00.0
sudo apt update
sudo apt install net-tools
ip a
ip a | grep -A 1 "wlo1"
sudo ifconfig wlo1 up
sudo ifconfig wlo1 down
sudo ifconfig wlo1 up
sudo systemctl restart NetworkManager.service
ip a | grep -A 1 "wlo1"
sudo apt update

ip a | grep -A 1 "wlo1"
ip a
lspci -vv -s 01:00.0
sudo apt install git dkms
git clone [https://github.com/aircrack-ng/rtl8812au.git](https://github.com/aircrack-ng/rtl8812au.git)
cd rtl8812au
sudo make dkms_install
lspci -vv -s 01:00.0
ip -a
lspci -vv -s 01:00.0

No good
Lucky my internet has network connectors
For me to send this

---

### Post by DWade on 2022-07-29
bash commands before posting means before posting to this forum and making this thread...

---

### Post by SeijiSensei on 2022-07-29
It's a driver problem. [https://askubuntu.com/questions/1263141/rtl8822be-driver-for-ubuntu-18-04-and-20-04](https://askubuntu.com/questions/1263141/rtl8822be-driver-for-ubuntu-18-04-and-20-04)

I had to compile the recommended RTL8812au driver for a wifi device and it works flawlessly. The solution proposed in that article worked for me.
```

sudo apt install git dkms
git clone https://github.com/aircrack-ng/rtl8812au.git
cd rtl8812au
sudo make dkms_install

```
I usually create a directory in which to run git. So create a directory, under your home directory is fine, with something like 
```

cd ~
mkdir Build
cd Build

```
and then follow the steps above.

---

### Post by #&amp;thj^% on 2022-07-29
Thanks for posting some of the things you've done, helps save time in repeated questions.
Dwade was this the last *known* working driver for your machine? >> 8812au, 5.6.4.2_35491.20191025, 5.15.0-41-generic, x86_64: installed....This does not sound right.
```

lsmod | grep -i wifi
rfkill list
```
Ninja-ed by SeijiSensei

---

### Post by DWade on 2022-07-29
No; the last working driver is in Kernel Linux 5.13.0-52-generic x86_64. Which I boot too, unless I am trying something to make wifi work. or as you asked for what tools list.
Which means I  restart and go to kernel 5.15
I will check the to commands and see if they are the same in each kernel.

And to answer senijisensei, I already did those commands. didn't work.

---

### Post by #&amp;thj^% on 2022-07-29
> **DWade said:**
> 
And to answer senijisensei, I already did those commands. didn't work.
That was my suspicion, wrong driver...I'm to the point now where I just can't in good standing, recommend RealTek anything any more.
I'll wait to see your outcomes on the commands..

---

### Post by DWade on 2022-07-29
ok, both the same.  Plus some extra commands

david@david-HP-Pavilion-15-cs2083:~$ lsmod | grep -i wifi
david@david-HP-Pavilion-15-cs2083:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
david@david-HP-Pavilion-15-cs2083:~$ 

david@david-HP-Pavilion-15-cs2083:~$ lspci -vv -s 01:00.0
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter (rev ff) (prog-if ff)
	DeviceName: Realtek RTL8822BE 802.11 bgn 1x1 WiFi + BT 4.2 Combo Adapter 
	!!! Unknown header type 7f
	Kernel driver in use: rtw_8822be
	Kernel modules: rtw88_8822be


david@david-HP-Pavilion-15-cs2083:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 80:e8:2c:25:1c:71 brd ff:ff:ff:ff:ff:ff
    altname enp2s0
3: wlo1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether c0:b5:d7:6a:57:7b brd ff:ff:ff:ff:ff:ff
    altname wlp1s0

david@david-HP-Pavilion-15-cs2083:~$ sudo lshw -C network
[sudo] password for david: 
  *-generic                 
       description: Wireless interface
       product: RTL8822BE 802.11a/b/g/n/ac WiFi adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlo1
       version: ff
serial: c0:b5:d7:6a:57:7b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822be driverversion=5.15.0-41-generic firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11
       resources: irq:139 ioport:4000(size=256) memory:a1300000-a130ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eno1
       version: 15
       serial: 80:e8:2c:25:1c:71
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-41-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 ioport:3000(size=256) memory:a1204000-a1204fff memory:a1200000-a1203fff

---

### Post by DWade on 2022-07-29
If I don't find anything soon, I will back up and reload. also may try 22.04 maybe.

It could be this 2020 laptop is too Old.

That will force the hard drive upgrade I have that I haven't put in. Faster bigger SSD.

---

### Post by #&amp;thj^% on 2022-07-29
I'm just throwing this out as a last ditch effort:
```
sudo modprobe -r rtw_8822be
sudo modprobe rtw_8822be
```
I find sometimes a good shut down and pause, has better results than a warm reboot.

---

### Post by DWade on 2022-07-29
I did the modprobe did not work. I even rebooted.  and shut down and waited a minute to turn back on.

david@david-HP-Pavilion-15-cs2083:~$ sudo modprobe -r rtw_8822be
[sudo] password for david: 
david@david-HP-Pavilion-15-cs2083:~$ sudo modprobe rtw_8822be
david@david-HP-Pavilion-15-cs2083:~$

I checked with 5.13 kernel and the driver is:
[Kernel driver in use: rtw_8822be]
[Kernel modules: rtw88_8822be]

5.15.0-41 kernel,
it booted up with this;
david@david-HP-Pavilion-15-cs2083:~$ lspci -vv -s 01:00.0
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
	DeviceName: Realtek RTL8822BE 802.11 bgn 1x1 WiFi + BT 4.2 Combo Adapter 
	Subsystem: Hewlett-Packard Company Realtek RTL8822BE 802.11ac 2 × 2 Wi-Fi + Bluetooth 4.2 Combo Adapter (MU-MIMO supported)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 140
	Region 0: I/O ports at 4000 [size=256]
	Region 2: Memory at a1300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: rtw_8822be
	Kernel modules: rtw_8822be

 then as soon as wifi accessed:

david@david-HP-Pavilion-15-cs2083:~$ lspci -vv -s 01:00.0
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter (rev ff) (prog-if ff)
	DeviceName: Realtek RTL8822BE 802.11 bgn 1x1 WiFi + BT 4.2 Combo Adapter 
	!!! Unknown header type 7f
	Kernel driver in use: rtw_8822be
	Kernel modules: rtw_8822be

So I have no Idea.
I went to GetHub found the RTL8822BE updated drivers
Removed the RTL8812 drivers
then installed the new drivers no workie.

So I will probably go from HWE kernel to the GA kernel.  Everything worked good with the 5.4 kernels, and the 5.13 kernels are not long-term supported.
So in essence I will go back from 20.04.5 & 20.04.4 to 20.04.1 unless a new kernel comes out supporting the Realtek wifi. the strange thing is the bluetooth works.  

I have downloaded the 20.04.1 ISO to reload should the 
Following not work right:

sudo apt install --install-recommends linux-generic
and if all works
remove HWE kernels
sudo apt remove --purge linux-generic-hwe-20.04 linux-oem-20.04 linux-hwe-* linux-oem-* linux-modules-5.1* linux-modules-5.8.0-* linux-modules-5.6.0-* 


Althought I will wait for a kernel update before going this far. and I will use the 5.13 kernel

---

### Post by DWade on 2022-07-30
I found it's a completely done deal.
By installing the standard kernel [sudo apt install --install-recommends linux-generic]
and by removing the 5.15.0-41 kernel [sudo apt remove linux-image-5.15.0-41-generic]
it installs the unsigned 5.15.0-41 kernel. which when EFI secure boot is disabled and booted into
the unsigned 5.15.0-41 kernel does not work either.
By removing the 5.15.0-41 unsigned kernel, it then reinstalls the signed 5.15.0-41 kernel, but by removing the signed kernel again
which again installs the unsigned kernel and then by removing the unsigned kernel, 
then it completely removes the 5.15.0.41 kernel from the system

I still have the 5.13.0-52 kernel installed.  

I will have to manually update while in the 5.4.0-122 kernel, because when in the 5.4.0-122 kernel, the system wants to remove the 5.13.0-52 kernel.  I want to keep that kernel for a bit.

So, in essence, this is done until they come out with a new kernel, that will have a RealTek RTL-8822BE driver for wifi. Or someone creates a driver.
OR... This laptop is done for newer kernels.  Someday I will check 22.04 and see what it does. Or if it has the same problem.
As in the old bugs bunny cartoon...  Tha Tha that's all Folks!

---

### Post by DWade on 2022-08-10
Update:  I loaded linux-generic-hwe-20.04 kernel 5.15.0-46 the latest 5.15.0 Kernel. It has the same problem with the Realtek WiFi module RTL8822BE.
So it looks like RealTek will have to make a proprietary driver for Linux going forward for the 5.15.0 Kernel or maybe someone in Open Source.

I will check the 5.15.0 Kernels when there are more updates. But otherwise this may be mute, until a driver is created.

---

### Post by azyx-kmg on 2022-12-17
> **DWade said:**
> Update:  I loaded linux-generic-hwe-20.04 kernel 5.15.0-46 the latest 5.15.0 Kernel. It has the same problem with the Realtek WiFi module RTL8822BE.
So it looks like RealTek will have to make a proprietary driver for Linux going forward for the 5.15.0 Kernel or maybe someone in Open Source.

I will check the 5.15.0 Kernels when there are more updates. But otherwise this may be mute, until a driver is created.

Hello DWade, I saw your topic and created this account cause maybe this could help.
My mobo is the z370-e and it uses the same chipset 8822be, I've managed to install this driver and it's working fine, maybe it'll work for you too:
[https://github.com/lwfinger/rtw88](https://github.com/lwfinger/rtw88)

---

### Post by DWade on 2022-12-23
I want to thankyou for the information.

But I got a new faster and larger SSD and when copying from drive to drive didn't work correctly. I had that problem before I think it has something to do with the TPM chip.

It took awhile to fix and ending up putting a new copy of Ubuntu on the computer.

I decided not to mess with the newer chips, after that so again thanks

---

