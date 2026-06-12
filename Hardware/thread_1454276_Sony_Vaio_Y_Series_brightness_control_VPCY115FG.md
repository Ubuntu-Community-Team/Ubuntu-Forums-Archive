---
title: "Sony Vaio Y Series brightness control VPCY115FG"
date: 2010-04-14
forum: Hardware
---

### Post by mr.p on 2010-04-14
I am trying to get the brightness controls working in Ubuntu.  I am currently using the most up to date Lucid Lynx.  At the moment I am unable to adjust the brightness which is killing my battery life! :)

Where should I start?

```
nathan@crunch:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
```

---

### Post by dunghopper on 2010-04-24
This [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/524967") includes a workaround.  It isn't perfect but it should get you by until a real fix is made.

---

### Post by ultiva on 2010-04-24
Hmm this looks like very similar problem on my VPCEB1S1E. On 10.04 brightness control stopped working. I can change it by adding permission +w to the file /proc/acpi/video/VGA/LCD/brightness and writing to this file one of allowed values (which can be obtained by "cat" on this file).

---

### Post by mecrip on 2010-05-01
I have the very same issue on my vaio VPC Y11S1E.
In the default configuration of lucid I also have some screen flickering and no audio or microphone working.

I'm also looking for a solution

---

### Post by mecrip on 2010-05-01
Ok, i've tryed the patch proposed and it worked for the F5/F6 keys but it doesen't allow gnome power manager to control backlight.

---

### Post by ff670099 on 2010-05-08
> **ultiva said:**
> Hmm this looks like very similar problem on my VPCEB1S1E. On 10.04 brightness control stopped working. I can change it by adding permission +w to the file /proc/acpi/video/VGA/LCD/brightness and writing to this file one of allowed values (which can be obtained by "cat" on this file).

Hello, what did you do exactly?

Thank's

---

### Post by low-res on 2010-05-12
> **ultiva said:**
> Hmm this looks like very similar problem on my VPCEB1S1E. On 10.04 brightness control stopped working. I can change it by adding permission +w to the file /proc/acpi/video/VGA/LCD/brightness and writing to this file one of allowed values (which can be obtained by "cat" on this file).

Sony VAIO VPCY11S1E Ubuntu 10.04.

My /proc/acpi/video looks like this. I don't have VGA dir: 

bla@vaio:/proc/acpi/video/OVGA$ ls -la
total 0
dr-xr-xr-x 7 root root 0 2010-05-12 12:45 .
dr-xr-xr-x 3 root root 0 2010-05-12 12:45 ..
dr-xr-xr-x 2 root root 0 2010-05-12 12:46 DD01
dr-xr-xr-x 2 root root 0 2010-05-12 12:46 DD02
dr-xr-xr-x 2 root root 0 2010-05-12 12:46 DD03
dr-xr-xr-x 2 root root 0 2010-05-12 12:46 DD04
dr-xr-xr-x 2 root root 0 2010-05-12 12:46 DD05
-rw-r--r-- 1 root root 0 2010-05-12 12:46 DOS
-r--r--r-- 1 root root 0 2010-05-12 12:46 info
-rw-r--r-- 1 root root 0 2010-05-12 12:46 POST
-r--r--r-- 1 root root 0 2010-05-12 12:46 POST_info
-r--r--r-- 1 root root 0 2010-05-12 12:46 ROM
bla@vaio:/proc/acpi/video/OVGA$

---

### Post by li0nix on 2010-06-10
Hello,
i'm fedora user and i've solved it on my Sony VPCY11S1E in this way:
run this command with sudo or su -c : setpci -s 00:02.0 F4.B=50
Change 50 with a number from 00 (lower) to FF (upper) to set screen brightness.
Sorry for my english

---

### Post by etrams on 2010-08-29
What driver/kernel/ configuration are you using to get the graphic card to work? I just bought a Series Y and I am having a really hard time to make it work properly. What about your sound card?

Thanks.

---

### Post by Zilioum on 2010-10-06
> **li0nix said:**
> Hello,
i'm fedora user and i've solved it on my Sony VPCY11S1E in this way:
run this command with sudo or su -c : setpci -s 00:02.0 F4.B=50
Change 50 with a number from 00 (lower) to FF (upper) to set screen brightness.
Sorry for my english
That worked for me too. Using Ubuntu 10.10 Beta on a Sony VPCY11S1E. Any way to make this permanent? Otherwise I would just put it in a startup script or add it to the panel.

---

