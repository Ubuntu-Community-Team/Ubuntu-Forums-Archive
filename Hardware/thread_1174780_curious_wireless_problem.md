---
title: "curious wireless problem"
date: 2009-05-31
forum: Hardware
---

### Post by ahusain on 2009-05-31
So I'm having an interesting problem with Ubuntu 9.04 on my home wireless network. I say home because I use the same machine at school and no such issue exists. 

When I am browsing or sending/receiving emails my internet connection will periodically die. The network manager still displays full bars but websites that are being loaded will cease and video that I am buffering will freeze. Its only down for approximately a minute and pretty annoying to deal with. Again this only happens at home and since I've upgraded to 9.04. This leads me to believe it has more to do with hardware support for my particular wireless router than anything else. Nevertheless the standard diagnostic information is included below. I've scoured the forums for people with similar problems and came up short. Any suggestions on where to start?

release: Ubuntu 9.04
machine: HP Pavilion dv5
router: TP-Link TL-WR941ND Wireless N Router - 300Mbps, 802.11n/g/b, 4 Port
wireless card: Intel WiFi Link 5300 IEEE 802.11a/b/g/Draft-N Wireless Network Adapters 533ANMMWW

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Fusion Systems"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:0F:BF:48:B6   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-50 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

lshw -C Network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:6a:98:1e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.101 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:25:e8:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: aa:e9:cd:72:ad:dd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

lspci: 
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

lsusb: 
```
Bus 002 Device 002: ID 064e:c107 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by ahusain on 2009-06-14
bump

---

### Post by Mo-Bility on 2009-06-14
Hi, this Mo
I just saw ur problem and I believe it has something to do with ur cable signal if ur using a broadband connection or ur router is too far away from the system 
Start with Checking the signal on the ISP modem and take it from there

Good Luck!!!!!!!!!!!!

---

### Post by shizumasa14 on 2009-06-14
I do not believe that ^^ is correct.  Sorry if this is rude but... that was really a noobish guessing answer.

I'm not sure, but you should check out the hardware compadibility list.  Very unlikely but maybe you need to install a driver?

---

### Post by ahusain on 2009-06-26
i don't know if thats the issue because i have another hp laptop that works fine

---

### Post by Ayuthia on 2009-06-26
Have you checked dmesg from the Terminal?  It might tell you what is happening.  It could be an issue with the wireless module or possibly an issue with NetworkManager.

Does your HP have the same wireless card?

---

### Post by evil-noxx on 2009-07-23
i seem to have a similar problem with my hp dv3000.

my wireless cards is detected as a PRO/Wireless 5100 AGN [Shiloh] Network Connection from Intel Corporation wich is fairly similar to yours.
however my router is an SMC...

The wireless worked out of the box with ubuntu 9.04 exept for this issue.

As a work around, instead of waiting a minute, i use "sudo /etc/init.d/networking restart" and it stars working again...

---

### Post by evil-noxx on 2009-08-12
my first bump...

---

### Post by BlueElk on 2009-08-13
What happens if you:

1) close & disable the wireless connection

2) $ sudo rmmod iwlagn

3) $ sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

4) enable the wireless (if needed, don't remember)

---

### Post by evil-noxx on 2009-08-13
I'm sorry to say that didn't help... After about 10/15 min of transferring data ate around 2mb/s wireless networking stopped working.

don't really know if it helps but here is the dmesg | tail output right after wireless stoped working

noxx@noxx-laptop:~$ cat dmesg_tail_output_after_wl_fail 
[11396.249057] iwlagn: Error setting new RXON (-28)
[11396.249062] iwlagn: No space for Tx
[11396.249065] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[11516.247829] iwlagn: No space for Tx
[11516.247837] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[11516.247850] iwlagn: No space for Tx
[11516.247854] iwlagn: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[11516.247857] iwlagn: Error setting new RXON (-28)
[11516.247862] iwlagn: No space for Tx
[11516.247865] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
noxx@noxx-laptop:~$ 


Honestly I can't make heads nor tails of what it says but it mentions a iwlagn...

---

### Post by BlueElk on 2009-08-13
Sorry, then I don't know. You might wanna check out this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352228](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352228)

The message logs look similar.

---

### Post by dca on 2009-08-13
Are you running 64bit Ubuntu 9.04?

---

### Post by evil-noxx on 2009-08-13
i'm running ubuntu 32bit...

After reading a few posts on from that bug report i found a possible work around. I'm still testing it as i type this reply but it seems to be working.

So, for anyone with the same problem that might stumble upon this thread, what I did was:
 - Enable Pre-released updates in the software sources application.
 - sudo apt-get install linux-backports-modules-jaunty
 - then i ran update manager and installed all those updates
 - reboot and pray it works

Thank you all for your help and if it doesn't work i'll bother you again :P

---

### Post by rodrigo.toste.gomes on 2009-09-03
> **evil-noxx said:**
> i'm running ubuntu 32bit...

After reading a few posts on from that bug report i found a possible work around. I'm still testing it as i type this reply but it seems to be working.

So, for anyone with the same problem that might stumble upon this thread, what I did was:
 - Enable Pre-released updates in the software sources application.
 - sudo apt-get install linux-backports-modules-jaunty
 - then i ran update manager and installed all those updates
 - reboot and pray it works

Thank you all for your help and if it doesn't work i'll bother you again :P

Hello.
Although it seems this has worked (I'll test it right now also), since you didn't say anything else, this is a bug that happens only on N networks (if you could change your router to only use b/g networks, you wouldn't have this bug), and I've been experiencing it since ubuntu 8.10.
I hope this works, because it limits other devices I have at home, to need to use g networking :/.
Anyway, I posted this for anyone who was curious about what triggered this bug.

EDIT: Tried the solution described above, and it became worse :/
Now, instead of the N network crashing ocasionally, it wasn't working at all (I'd connect but have no access to the network).
But I got it to work. I found this post of a person with exactly the same problem:
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2009-05/msg00180.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2009-05/msg00180.html)
The solution is simple. For those who don't have a lot of knowledge about Linux, I'll tell you what you have to do:

Open a terminal.
Type this command in:
> sudo apt-get install iw
This installs the package iw, which allows you to have more control over your wireless card.
After that, use this command:
> sudo iw reg set PT
Attention! Where it says PT, it refers to my country, so you have to replace that so that it refers to yours (for example, for france it would be FR, not sure about the others, but it's probably not hard to figure out).
To finnish, you have to set the working frequencies you'll use, with these two commands:
> sudo iw dev wlan0 set freq 2412
sudo iw dev wlan0 set freq 5180
And after that wireless N is working (althoug regretably I believe it is in lower speeds than it should be, because it says 60Mb/s, when it should be able to get 300Mb/s but it may be some limitation with the card. Anyway, for me, the wireless speed isn't very important, since having to use G wasn't harming the use of my computer, but of other devices).

I'm not sure however if this would work without the process described by evil-noxx, but you're welcome to try. Please post feedback in that case, since it may help other users.

---

### Post by evil-noxx on 2009-09-04
I'm not sure but i think all i did was get a more recent kernel... however that fixed the "no space for TX" problem and created a new one. Something reported on dmesg as losing AP beacon or something and the work arrounds for that new problem are also related to desabling N support.
I've also tryed  			 				"sudo iw reg set PT" but didn't seem to help. What i didn't try was:
     sudo iw dev wlan0 set freq 2412
     sudo iw dev wlan0 set freq 5180

Anyway, are those frequencies specific to Portugal, random, or what?

---

### Post by rodrigo.toste.gomes on 2009-09-04
The frequencies are specific to N networking.
What you should have changed was PT to another countries code.

---

### Post by evil-noxx on 2009-09-04
I'm from portugal too...


edit:
     sudo iw dev wlan0 set freq 5180 returned and error saying invalid argument -20
but changing my router to only operate in b and g seams to have worked.
Thanks rodrigo!

---

### Post by rodrigo.toste.gomes on 2009-09-08
> **evil-noxx said:**
> I'm from portugal too...

oops, than you had it right xD

> **evil-noxx said:**
> edit:
     sudo iw dev wlan0 set freq 5180 returned and error saying invalid argument -20
but changing my router to only operate in b and g seams to have worked.
Thanks rodrigo!

Well, I'd like to correct my last post, the frequencies aren't specific to N networking, but yes to the channels where you transmit the wireless communication (channel 1 = 2412mhz ...), so when setting the frequencies, you have to have into account the channels (although the computer usually does it correctly automatically).

I get the same error when trying to set the frequency to 5180, and after checking iw list, I believe it's because my card doesn't support it.

Right now I'm using a N network, and having no problems with it, so the comand that seems to have fixed it was:
iw reg set PT

Anyway, in the future they should release a solution within the drivers so N networking works ... and until then, if it works in b/g for you, and if you have no special reason to use N (as streaming HD video, or something like that over the network), than you probably should stick with it, until N is functional.

---

