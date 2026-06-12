---
title: "Dell Inspiron 1525, Intel Wireless Card Problems"
date: 2008-05-13
forum: Hardware
---

### Post by Neurosynapse on 2008-05-13
Evening everyone!

I'm having a problem using my local wireless internet connection though Ubuntu installation I just installed this morning, I am 90% sure it's due to a driver problem.

The card I'm using is an Intel Wireless WiFi Link 4965AGN.

I'm a total newbie to Linux and Ubuntu, so while I may understand most of the tech speak, I might be a bit slow on the Linux commands and such!

Any help is appreciated,
Neuro

---

### Post by ghindo on 2008-05-14
What sort of trouble are you having?  Are you getting any error messages, or is just nothing showing up?

---

### Post by Neurosynapse on 2008-05-14
Ghindo, and I, spoke over IRC and were unable to come up with a solution, I have no error messages, but my laptop just simply cannot find any sort of wireless network, when I know there is one in range, as I'm sitting right next to it.

I am pretty sure it's a hardware problem, but I can't find any solutions to my card specifically! Help! :confused:

---

### Post by balagosa on 2008-05-14
you say you are new? from one site i read (forgot what), i saw that only a bunch of WiFi Cards will work out-of-the-box

then please post us a detailed information about your system.

one would be:
please post the output of this:
```
lspci
```
AND
```
lshw -C network
``` <---for some reason this only works in ubuntu. i tried it on my Sys. Admin's Fedora 8 and it didnt work? can someone please clarify this.

also tell us the full specs of your laptop/desktop. what ubuntu you are running, version. kernel(optional)

---

### Post by Neurosynapse on 2008-05-14
> **balagosa said:**
> you say you are new? from one site i read (forgot what), i saw that only a bunch of WiFi Cards will work out-of-the-box

then please post us a detailed information about your system.

one would be:
please post the output of this:
```
lspci
```
AND
```
lshw -C network
``` <---for some reason this only works in ubuntu. i tried it on my Sys. Admin's Fedora 8 and it didnt work? can someone please clarify this.

also tell us the full specs of your laptop/desktop. what ubuntu you are running, version. kernel(optional)

Hi Balagosa! Thanks for responding!

My lspci readout:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
```

My lshw -C network:
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:5a:f2:bb
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.1.102 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:5f:3e:a7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.101 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

```

I'm using Hardy Heron, 8.04, and This is a Dell Inspiron 1525, Intel Duo Core 2 2.0GHz, Sporting 4 gigs of RAM, blue tooth adapter, and standard Intel chipset graphics, the wireless card is on my first post! The kernal I have NO idea about.

Cheers,
Neuron

---

### Post by Neurosynapse on 2008-05-15
Bump for a solution!

---

### Post by jbrice on 2008-05-18
Sorry if this is blindingly obvious - but it's easily overlooked!

Have you got the Wireless Off/On/Scan Switch (right-hand side, towards front) in the "On" position?

JB

---

### Post by Neurosynapse on 2008-05-18
> **jbrice said:**
> Sorry if this is blindingly obvious - but it's easily overlooked!

Have you got the Wireless Off/On/Scan Switch (right-hand side, towards front) in the "On" position?

JB

I have, it is on ;) I have even tested it, turning it off and on again.

---

### Post by industrytool on 2008-05-18
having the same problem with my dv6000, i think you'll need the 80211 module, wifi ag4965 dirvers and the kernel sources if its a new ubuntu insall. gonna figure it out next week, i'll post if i solve it.

---

### Post by ASULutzy on 2008-05-18
Paste these two things```
iwconfig
``` and ```
sudo iwlist wlan0 scanning
```

---

### Post by industrytool on 2008-05-18
Running on a HP Laptop (DV6885se) with a 4965AGN wifi card and Unbuntu v2.6.24-15-generic.

Intel Core2 Duo Moble 2.1GHz, 3GB RAM, 250GB HD, NVIDIA GeForce 8400M GS 256MB


```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```
AND
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:5f:2e:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:68:4b:9e:54
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s 
```

Downloaded all the kernel sources, but i'm still getting a ..
Kernel Makefile not found at '/lib/modules/2.6.24-16-generic/source/'
when i try to install the 80211 module and wifi card drivers

---

### Post by rathin88 on 2008-05-24
i have the intel 3945 wi-fi card in mine..it did work fine when i used it along with gutsy gibbon..but now having upgraded to Hardy Heron i am not able to use it..can anybody possibly provide a solution for it..

---

### Post by dicecca112 on 2008-05-24
run this command in the terminal and post the results 

lsmod | grep ndis
lsmod | grep iwl
sudo cat /var/log/messages | grep switch

---

### Post by rathin88 on 2008-05-25
lsmod |grep ndis dint get me any result..
lsmod |grep iwl got me 
iwl3945               100468  0 
iwlwifi_mac80211      251876  1 iwl3945
cfg80211               17680  1 iwlwifi_mac80211
sudo cat /var/log/messages | grep switch 
May 22 12:43:31 rathin-laptop kernel: [ 4205.238087] SMP alternatives: switching to UP code
May 22 12:43:31 rathin-laptop kernel: [ 4206.578195] SMP alternatives: switching to SMP code
May 22 16:56:14 rathin-laptop kernel: [   12.958628] SMP alternatives: switching to UP code
May 22 16:56:14 rathin-laptop kernel: [   13.497805] SMP alternatives: switching to SMP code
May 22 16:56:14 rathin-laptop kernel: [   31.902400] Kill switch must be turned off for wireless networking to work.
May 22 21:44:27 rathin-laptop kernel: [    9.511693] SMP alternatives: switching to UP code
May 22 21:44:27 rathin-laptop kernel: [   10.049395] SMP alternatives: switching to SMP code
May 22 21:44:27 rathin-laptop kernel: [   28.344770] Kill switch must be turned off for wireless networking to work.
May 23 02:16:56 rathin-laptop kernel: [   12.180079] SMP alternatives: switching to UP code
May 23 02:16:56 rathin-laptop kernel: [   12.718626] SMP alternatives: switching to SMP code
May 23 02:16:56 rathin-laptop kernel: [   30.698568] Kill switch must be turned off for wireless networking to work.
May 23 09:36:43 rathin-laptop kernel: [    7.249205] SMP alternatives: switching to UP code
May 23 09:36:43 rathin-laptop kernel: [    7.787140] SMP alternatives: switching to SMP code
May 23 09:36:43 rathin-laptop kernel: [   26.115775] Kill switch must be turned off for wireless networking to work.
May 23 13:15:13 rathin-laptop kernel: [   16.051994] SMP alternatives: switching to UP code
May 23 13:15:13 rathin-laptop kernel: [   16.590328] SMP alternatives: switching to SMP code
May 23 13:15:13 rathin-laptop kernel: [   34.780399] Kill switch must be turned off for wireless networking to work.
May 23 17:31:12 rathin-laptop kernel: [    6.270305] SMP alternatives: switching to UP code
May 23 17:31:12 rathin-laptop kernel: [    6.809602] SMP alternatives: switching to SMP code
May 23 17:31:12 rathin-laptop kernel: [   25.607842] Kill switch must be turned off for wireless networking to work.
May 23 21:30:01 rathin-laptop kernel: [    8.222939] SMP alternatives: switching to UP code
May 23 21:30:01 rathin-laptop kernel: [    8.761478] SMP alternatives: switching to SMP code
May 23 21:30:01 rathin-laptop kernel: [   26.509772] Kill switch must be turned off for wireless networking to work.
May 24 02:03:41 rathin-laptop kernel: [   16.482835] SMP alternatives: switching to UP code
May 24 02:03:41 rathin-laptop kernel: [   17.021090] SMP alternatives: switching to SMP code
May 24 02:03:41 rathin-laptop kernel: [   35.040789] Kill switch must be turned off for wireless networking to work.
May 24 08:22:38 rathin-laptop kernel: [    6.193563] SMP alternatives: switching to UP code
May 24 08:22:38 rathin-laptop kernel: [    6.733722] SMP alternatives: switching to SMP code
May 24 08:22:38 rathin-laptop kernel: [   25.462846] Kill switch must be turned off for wireless networking to work.
May 24 13:49:04 rathin-laptop kernel: [ 9889.214527] Kill switch must be turned off for wireless networking to work.
May 24 14:14:50 rathin-laptop kernel: [   17.728975] SMP alternatives: switching to UP code
May 24 14:14:50 rathin-laptop kernel: [   18.268185] SMP alternatives: switching to SMP code
May 24 14:14:50 rathin-laptop kernel: [   36.998404] Kill switch must be turned off for wireless networking to work.
May 24 15:42:00 rathin-laptop kernel: [    8.649121] SMP alternatives: switching to UP code
May 24 15:42:00 rathin-laptop kernel: [    9.187179] SMP alternatives: switching to SMP code
May 24 15:42:00 rathin-laptop kernel: [   28.258942] Kill switch must be turned off for wireless networking to work.
May 24 17:07:20 rathin-laptop kernel: [    8.261932] SMP alternatives: switching to UP code
May 24 17:07:20 rathin-laptop kernel: [    8.800436] SMP alternatives: switching to SMP code
May 24 17:07:20 rathin-laptop kernel: [   27.339436] Kill switch must be turned off for wireless networking to work.
May 24 21:32:18 rathin-laptop kernel: [    6.882842] SMP alternatives: switching to UP code
May 24 21:32:18 rathin-laptop kernel: [    7.422121] SMP alternatives: switching to SMP code
May 24 21:32:18 rathin-laptop kernel: [   25.256276] Kill switch must be turned off for wireless networking to work.
May 25 00:28:42 rathin-laptop kernel: [    6.183185] SMP alternatives: switching to UP code
May 25 00:28:42 rathin-laptop kernel: [    6.721598] SMP alternatives: switching to SMP code
May 25 00:28:42 rathin-laptop kernel: [   25.275660] Kill switch must be turned off for wireless networking to work.
May 25 01:07:09 rathin-laptop kernel: [ 1428.144414] Kill switch must be turned off for wireless networking to work.
May 25 01:22:40 rathin-laptop kernel: [ 1895.931265] Kill switch must be turned off for wireless networking to work.
Nov 30 00:41:57 rathin-laptop kernel: [    7.517727] SMP alternatives: switching to UP code
Nov 30 00:41:57 rathin-laptop kernel: [    8.055598] SMP alternatives: switching to SMP code
Nov 30 00:41:57 rathin-laptop kernel: [   26.293718] Kill switch must be turned off for wireless networking to work.
May 25 10:04:41 rathin-laptop kernel: [    7.033935] SMP alternatives: switching to UP code
May 25 10:04:41 rathin-laptop kernel: [    7.572478] SMP alternatives: switching to SMP code
May 25 10:04:41 rathin-laptop kernel: [   26.548659] Kill switch must be turned off for wireless networking to work.
Aug  8 10:18:08 rathin-laptop kernel: [    9.939420] SMP alternatives: switching to UP code
Aug  8 10:18:08 rathin-laptop kernel: [   10.478916] SMP alternatives: switching to SMP code
Aug  8 10:18:08 rathin-laptop kernel: [   28.456260] Kill switch must be turned off for wireless networking to work.

---

### Post by debs_basu on 2008-06-04
I had the same problem when I updated my kernel.
kernel 2.6.22.14 kernel was working for me before. but not any newer kernels

I think it may be because the driver changed from iwl3945 to ipw3945
once I black listed ipw3945 and loaded iwl3945 wireless started back again ( I'm still using the older kernel)

---

### Post by yarn on 2008-10-01
> **debs_basu said:**
> 
I think it may be because the driver changed from iwl3945 to ipw3945
once I black listed ipw3945 and loaded iwl3945 wireless started back again ( I'm still using the older kernel)    how do u switch drivers....i have the broadco 3945 also and my wireless wont work either.

---

### Post by Yellow Pasque on 2008-10-01
```
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
                Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
```
If you have this, try telling it what network you want to connect to:
```
sudo iwconfig wlan0 essid <yournetworkname>
```

---

### Post by toddaroo on 2009-12-03
I am also having similar problems - being a newbie to UBUNTU myself, I'm finding the suggested solutions a little difficult to understand. I also haven't had any success getting the touchpad working on the same Dell even under Jaunty. Any suggestions that I could understand?

---

### Post by toddaroo on 2009-12-03
I am also having similar problems - being a newbie to UBUNTU myself, I'm finding the suggested solutions a little difficult to understand. I also haven't had any success getting the touchpad working on the same Dell even under Jaunty. Any suggestions that I could understand?
Found this link [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421662](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421662) but still trying to understand if there's a solution or if its ongoing

---

### Post by sgtwill09 on 2009-12-03
i was having a similar issue with mine until i started using jaunty, it worked out of the box.  one thing u can try to do is use ndiswrapper, do a quick search on it in the forums and u should see a ton of threads on it.

---

