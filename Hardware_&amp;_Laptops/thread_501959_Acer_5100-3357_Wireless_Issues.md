---
title: "Acer 5100-3357 Wireless Issues"
date: 2007-07-16
forum: Hardware &amp; Laptops
---

### Post by arewhyfour on 2007-07-16
I'm new to linux and new to Ubuntu. I decided to take the plunge again and put Ubuntu on my laptop, however my wireless isn't working. I don't know if the wireless card is even being detected as I do a "lspci -nn" and all I get is a wired connection and seemingly the dialup modem

This laptop supposedly uses the broadcom wireless chip, but Ubuntu isn't detecting it and I've tried using different tutorial on this forum, but with no help.

The laptop details are below, but I've been unsuccessful in finding what exact chipset it's using.

Acer Aspire 15.4" Widescreen Notebook PC (5100-3357)
ACA AS51003357

Please help?

---

### Post by linuxwizard on 2007-07-16
More info maybe someone will be able to help you

To determine what wireless card/chipset you have, open up a terminal and type the following.

lspci -v | less


[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Twintop on 2007-07-17
It looks like your laptop is part of the Aspire 5100 series, which is supported by a project called acer_acpi. acer_acpi enables wifi/bluetooth/G3/monitor brightness/hotkeys through a kernel module and the /proc filesystem (though this is going to be revamped soon I hear). You can download it at [http://code.google.com/p/aceracpi](http://code.google.com/p/aceracpi) .

---

### Post by jdunn on 2007-07-20
TwinTop,
I just downloaded and tried the Aceracpi.  Again, I get no errors in Makefile but no driver associated with the Atheros Controller.  However, there is now a /proc/acpi/acer directory and the 'wireless' attribute is set to one.

---

### Post by Twintop on 2007-07-20
Unfortunately I'm at work right now, jdunn, and don't have my laptop with me, so I can't post my 'turn on and scan' script (I will tonight when I get home, though). Do this for me, if you can:

```
$ sudo depmod -a
$ sudo modprobe acer_acpi
$ sudo chmod 0777 /proc/acpi/acer/*
$ echo 0 > /proc/acpi/acer/wireless
$ echo 1 > /proc/acpi/acer/wireless
$ lsmod | grep ath
$ sudo iwconfig
```

When you echo 1, your wireless light should turn on or blink, etc. Now, you need to scan for nearby wireless networks:

```
$ sudo iwlist ath0 scan
```

And you should be able to select a wireless network from the network icon up by your clock. Again, I'll post my full script when I get home,a nd this is just what I remember being parts of it.

---

### Post by jdunn on 2007-07-20
Nope.  I just tried what you suggested and it shows no wireless networks.  I know there are wireless connections in the area.  Once more, there is no driver associated with the hardware.

lshw -C network

* - network UNCLAIMED
description:  Ethernet controller
product:  Atheros Communications, Inc.

---

### Post by jdunn on 2007-07-20
Arewhyfor,
I have the exact same laptop you have, the 5100-3357.  If you manage to get wireless networking to work, let me know.  I'm having the same problem.

---

### Post by Twintop on 2007-07-21
jdunn: randomish question for you: do you have Atheros Hardware Access Layer (HAL) enabled under the Restricted Drivers Manager?

---

### Post by jdunn on 2007-07-21
I don't know.  How would I find out?

---

### Post by Twintop on 2007-07-21
> **jdunn said:**
> I don't know.  How would I find out?

Go to System->Administration->Restricted Drivers Manager

In there you should see a couple options (probably for Atheros HAL and your graphics card). Make sure there's a checkmark in 'Enabled' and it says the status is 'In Use'. If it isn't, then enable it, reboot, and look again. Once it's enabled then acer_acpi should work...

---

### Post by jdunn on 2007-07-21
I'm using Kubuntu, not Ubuntu.

---

### Post by Twintop on 2007-07-21
Try installing it and see if you can find it on KDE's menus:

```
sudo apt-get install restricted-manager
```

---

### Post by jdunn on 2007-07-21
Synaptic is installed.

There are no options for restricted drivers

---

### Post by jdunn on 2007-07-21
Forget this idea.  Synaptic is for Ubuntu.  Adept is for Kubuntu.  I've heard of people using Synaptic on Kubuntu and completely messing up their installs.  I'm removing it.  I don't see what you're asking me to find anyway.

---

### Post by Twintop on 2007-07-21
You know, if you're going to be jumpy and whiny when things  aren't working and people are trying to help you, perhaps Linux isn't the thing for you right now. I pulled the idea of installing the restricted drivers manager from  [here]("http://ubuntuforums.org/showthread.php?t=491468") and didn't say to use Synaptic, though Synaptic is a GUI front end to aptitude. Furthermore, programs for Ubuntu (Gnome) can and do work on Kubuntu (KDE), and vise-versa if you have the right libraries installed. if you don't have the right libraries installed they get installed by aptitude automatically when you go to install a program.

So I'll say it again in simple terms: I'm trying to help you, and if you want to get your WiFi working open a terminal and type in:

```
sudo apt-get install restricted-manager
```

And tell me if it installed it or gave you an error.

---

### Post by jdunn on 2007-07-21
You're confusing me with a common stereotype on these forums.  I'm not being jumpy and whiny.  However, it was rude that I forgot to thank you for your efforts.  Sorry.  I appreciate your help.

I've been using Linux distros for years...However, this is my first Linux notebook PC and my first experience with Wireless.  I need wireless on this notebook by the end of the weekend, so time is a factor.  I've been monitoring at least 4 threads with users instructing me to install 3 detailed and highly experiemental drivers.  Obviously, I can only do one at a time and I don't have all weekend to do this (I have a date, homework, and must study for a midterm).  I've already tried the NDISwrapper, MadWifi and aceracpi drivers without success.  I haven't exhausted these options but I'm running out of time and I've already had to completely reinstall Kubuntu from scratch once.  I need wireless running on the laptop for my Java course next week.  I figure the best approach for me now is to purchase a wireless PCCard adapter that will work with Linux Out-of-the-box.  Don't you agree?  Now I just need some recommendations.  Could you please recommend any adapters?

---

### Post by Twintop on 2007-07-21
jdunn: your laptop should be able to use madwifi (and acer_acpi) with no problems (according to [here]("http://code.google.com/p/aceracpi/wiki/SupportedHardware")). Can you (re)install the madwifi drivers (if you have removed them) and in a console run:

```
$ sudo modprobe ath_pci
```

and then run 

```
$ dmesg
```

and post the end of dmesg here?


Also, can you check if you have linux-restricted-modules-$(uname -r) installed? That might also be the reason why  we can get in to the restricted drivers manager.

I'm going to download Kubuntu 7.04 and see if I can find it from the live CD.

As for a recommendation on a PCIMIA wireless card, [this]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") would be a good listing to look at. I haven't had to use an external card before, so I can't really suggest a good one, other than try to buy a large-brand and not a cheap 3rd party one.

---

### Post by jdunn on 2007-07-22
21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.516000] hda_codec: invalid dep_range_val 0:7fff
[   21.676000] fuse init (API version 7.8)
[   21.700000] hda_codec: num_steps = 0 for NID=0xd
[   21.700000] hda_codec: num_steps = 0 for NID=0xd
[   21.704000] hda_codec: num_steps = 0 for NID=0xd
[   21.704000] hda_codec: num_steps = 0 for NID=0x18
[   21.704000] hda_codec: num_steps = 0 for NID=0x19
[   21.704000] hda_codec: num_steps = 0 for NID=0x9
[   21.756000] hda_codec: num_steps = 0 for NID=0x19
[   21.756000] hda_codec: num_steps = 0 for NID=0x19
[   21.760000] hda_codec: num_steps = 0 for NID=0x19
[   21.764000] hda_codec: num_steps = 0 for NID=0x19
[   21.768000] hda_codec: num_steps = 0 for NID=0x19
[   21.772000] hda_codec: num_steps = 0 for NID=0x19
[   21.776000] hda_codec: num_steps = 0 for NID=0x19
[   21.776000] hda_codec: num_steps = 0 for NID=0x19
[   21.780000] hda_codec: num_steps = 0 for NID=0x19
[   21.784000] hda_codec: num_steps = 0 for NID=0x19
[   21.788000] hda_codec: num_steps = 0 for NID=0x19
[   21.792000] hda_codec: num_steps = 0 for NID=0x19
[   21.796000] hda_codec: num_steps = 0 for NID=0x19
[   21.800000] hda_codec: num_steps = 0 for NID=0x19
[   21.800000] hda_codec: num_steps = 0 for NID=0x19
[   21.804000] hda_codec: num_steps = 0 for NID=0x19
[   21.808000] hda_codec: num_steps = 0 for NID=0x19
[   21.812000] hda_codec: num_steps = 0 for NID=0x19
[   21.816000] hda_codec: num_steps = 0 for NID=0x19
[   21.820000] hda_codec: num_steps = 0 for NID=0x19
[   21.824000] hda_codec: num_steps = 0 for NID=0x19
[   21.824000] hda_codec: num_steps = 0 for NID=0x19
[   21.828000] hda_codec: num_steps = 0 for NID=0x19
[   21.832000] hda_codec: num_steps = 0 for NID=0x19
[   21.836000] hda_codec: num_steps = 0 for NID=0x19
[   21.840000] hda_codec: num_steps = 0 for NID=0x19
[   21.844000] hda_codec: num_steps = 0 for NID=0x19
[   21.848000] hda_codec: num_steps = 0 for NID=0x19
[   21.852000] hda_codec: num_steps = 0 for NID=0x19
[   21.852000] hda_codec: num_steps = 0 for NID=0x19
[   21.856000] hda_codec: num_steps = 0 for NID=0x19
[   21.860000] hda_codec: num_steps = 0 for NID=0x19
[   21.864000] hda_codec: num_steps = 0 for NID=0xd
[   21.864000] hda_codec: num_steps = 0 for NID=0xd
[   21.868000] hda_codec: num_steps = 0 for NID=0xd
[   21.868000] hda_codec: num_steps = 0 for NID=0x18
[   21.868000] hda_codec: num_steps = 0 for NID=0x19
[   21.868000] hda_codec: num_steps = 0 for NID=0x9
[   21.880000] lp: driver loaded but no devices found
[   21.900000] Adding 2265124k swap on /dev/disk/by-uuid/d74fb9ee-f0ab-4a44-95e6-e32406e1dcce.  Priority:-1 extents:1 across:2265124k
[   22.048000] EXT3 FS on sda1, internal journal
[   23.488000] NET: Registered protocol family 17
[   26.176000] eth0: no IPv6 routers present
[   27.552000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   27.552000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   27.712000] ACPI: Battery Slot [BAT1] (battery present)
[   27.764000] No dock devices found.
[   27.776000] Using specific hotkey driver
[   27.800000] ibm_acpi: ec object not found
[   27.864000] ACPI: AC Adapter [ACAD] (on-line)
[   27.908000] input: Power Button (FF) as /class/input/input5
[   27.912000] ACPI: Power Button (FF) [PWRF]
[   27.940000] input: Lid Switch as /class/input/input6
[   27.940000] ACPI: Lid Switch [LID]
[   27.968000] input: Power Button (CM) as /class/input/input7
[   27.972000] ACPI: Power Button (CM) [PWRB]
[   28.000000] input: Sleep Button (CM) as /class/input/input8
[   28.004000] ACPI: Sleep Button (CM) [SLPB]
[   28.028000] wmi_add device=eef16000
[   28.028000] calling WQBA
[   28.052000] pcc_acpi: loading...
[   28.220000] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-38 processors (version 2.00.00)
[   28.220000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xb
[   28.220000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xd
[   28.220000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xf
[   28.220000] powernow-k8:    3 : fid 0x8 (1600 MHz), vid 0x11
[   28.220000] powernow-k8:    4 : fid 0x0 (800 MHz), vid 0x18
[   31.824000] ppdev: user-space parallel port driver
[   32.652000] apm: BIOS not found.
[   33.200000] Bluetooth: Core ver 2.11
[   33.200000] NET: Registered protocol family 31
[   33.200000] Bluetooth: HCI device and connection manager initialized
[   33.200000] Bluetooth: HCI socket layer initialized
[   33.232000] Bluetooth: L2CAP ver 2.8
[   33.232000] Bluetooth: L2CAP socket layer initialized
[   33.316000] Bluetooth: RFCOMM socket layer initialized
[   33.316000] Bluetooth: RFCOMM TTY layer initialized
[   33.316000] Bluetooth: RFCOMM ver 1.8
[   91.952000] hda_codec: num_steps = 0 for NID=0x19
[   92.792000] hda_codec: num_steps = 0 for NID=0x19
[   93.072000] hda-intel: Invalid position buffer, using LPIB read method instead.

---

### Post by jdunn on 2007-07-22
It seems the ring buffer is flooded with those hda_codec messages.  I assume that relates to the SATA hard drive?  I'm not sure why....My hard drive seems to be working fine.  Anyway that is my dmesg output.  Is there a way to have those messages ignored from the boot logger? Obviously, it makes analyzing any other problems difficult.  

 I will give this wireless thing another go, I suppose.

---

### Post by jdunn on 2007-07-22
Twintop,
I believe Kubuntu tries out madwifi during the OS install when evaluating my hardware.

jdunn@jdunn-laptop:/lib/modules/2.6.20-16-generic$ pwd
/lib/modules/2.6.20-16-generic
jdunn@jdunn-laptop:/lib/modules/2.6.20-16-generic$ ls
build    modules.alias        modules.inputmap   modules.seriomap
initrd   modules.ccwmap       modules.isapnpmap  modules.symbols
kernel   modules.dep          modules.ofmap      modules.usbmap
madwifi  modules.ieee1394map  modules.pcimap     volatile

Notice the madwifi driver directory.  There are drivers in there.

jdunn@jdunn-laptop:/lib/modules/2.6.20-16-generic/madwifi$ ls
ath_pci.ko        ath_rate_sample.ko  wlan.ko           wlan_tkip.ko
ath_rate_amrr.ko  wlan_acl.ko         wlan_scan_ap.ko   wlan_wep.ko
ath_rate_onoe.ko  wlan_ccmp.ko        wlan_scan_sta.ko  wlan_xauth.ko

The linux restricted drivers for my kernel version ARE installed.  I've checked in Adept package manager.  I'm sure of it.  Here is a description for the package in Adept:

This package provides restricted modules for Linux version 2.6.20 on x86/x86_64.
Currently the following modules are included: 
madwifi (Atheros) 
fglrx (ATI) 
nvidia 
fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
These modules are "restricted" because they are not available under a completely Free licence

---

