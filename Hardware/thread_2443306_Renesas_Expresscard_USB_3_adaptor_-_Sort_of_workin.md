---
title: "Renesas Expresscard USB 3 adaptor - Sort of working..."
date: 2020-05-14
forum: Hardware
---

### Post by michasrichter on 2020-05-14
Hey there

This is my first post, but I've been a lurker for some time.

I've got an old HP EliteBook 2760p with Ubuntu 18.04 installed. I'm using it as a plex server, but are having issues with my external drive due to the laptop only having native USB 2 ports. Luckily it has an Expresscard Gen II slot (32mm) so I bought a Renesas 2-port USB 3 adaptor ([https://www.ebay.com.au/itm/251547100204](https://www.ebay.com.au/itm/251547100204)) after finding that many have had success with that.

I prepared myself to follow instructions as directed here:
[https://help.ubuntu.com/community/ExpressCard](https://help.ubuntu.com/community/ExpressCard)
[https://askubuntu.com/questions/812372/usb-3-0-express-card](https://askubuntu.com/questions/812372/usb-3-0-express-card)

or even troubleshooting:
[https://unix.stackexchange.com/questions/440741/install-usb-3-0-express-card-under-linux-arch-linux-tried-adding-kernel-param](https://unix.stackexchange.com/questions/440741/install-usb-3-0-express-card-under-linux-arch-linux-tried-adding-kernel-param)
[https://bugzilla.kernel.org/show_bug.cgi?id=199627](https://bugzilla.kernel.org/show_bug.cgi?id=199627)


When I received the card I plugged it in, not having any expectations that it'd work out of the box. But what do you know... It instantly recognised both my USB pen drive as well as my external media drive (Seagate 4TB- STEB4000300). Excellent! ... Or so I thought. The first thing I tried was to transfer a 40GB file from the external drive to my home folder. At first it went well - got the first gig through in a little over five seconds. When FileManager started showing the transfer rate it displayed 185MB/s - That is consistent with the rates I get on windows. But then, with about 1.8GB transferred, the rate started slowing. And not only that, the mouse started lagging as well making the desktop interface basically unusable.

The rate steadily decreased to sub-usb2 speeds, "stabilizing" at around 20-25 MB/s, all the while holding up the system. This happens both when reading from and writing to the usb 3 media at high speeds. It also happened with a HDD in a dock, so it's not the Seagate drive which is at fault. It also happens using any of the two ports in the Expresscard adaptor.

Here's what I've done to try and fix it the quick-n-dirty way:
[LIST]
[*]Updated BIOS - From the very old F02 BIOS from 2011 to version F67 updated in 2016.
[LIST]
[*]This actually improved the issue a little bit. It now takes a couple more seconds before the "lag" sets in. The end result is the same though...
[/LIST]

[*]Changed the BIOS setting to only run at ExpressCard version 1 speeds.
[LIST]
[*]This had no effect at all on the issue except for lowering the initial transfer speed a bit.
[/LIST]

[*]Disabled compatibility for Legacy USB in the BIOS
[LIST]
[*]Again, no change.
[/LIST]
[/LIST]

I have not attempted to install any drivers yet as it seems the card is working, just not well...


To troubleshoot the issue I tried running "lspci -nnk | grep -A2 USB" and got the following output:
```
michas@server:~$ lspci -nnk | grep -A2 USB
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family USB Enhanced Host Controller [103c:162a]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
--
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Hewlett-Packard Company 6 Series/C200 Series Chipset Family USB Enhanced Host Controller [103c:162a]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation QM67 Express Chipset LPC Controller [8086:1c4f] (rev 04)
--
02:00.0 USB controller [0c03]: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller [1912:0015] (rev 02)
    Kernel driver in use: xhci_hcd
23:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380] (rev 30)
```
I'm not really sure how to interpret the output other than the Renesas adaptor is working and using the xhci_hcd driver. Doesn't really tell me anything.

Running "dmesg" doesn't bring up any errors when transferring, but then I don't really know what to look for. Let me know if you'd like me to reboot, complete a transfer and then run dmesg and post the (rather large) output somewhere.

Some more general output:
```
michas@server:~$ inxi -Fxz
System:    Host: server Kernel: 5.3.0-51-generic x86_64 bits: 64 gcc: 7.5.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.4 LTS
Machine:   Device: laptop System: Hewlett-Packard product: HP EliteBook 2760p v: A0005E02 serial: N/A
           Mobo: Hewlett-Packard model: 162A v: KBC Version 05.41 serial: N/A
           BIOS: Hewlett-Packard v: 68SOU Ver. F.67 date: 05/31/2018
Battery    BAT0: charge: 33.2 Wh 95.8% condition: 34.6/34.6 Wh (100%)
           model: Hewlett-Packard Primary status: N/A
CPU:       Dual core Intel Core i5-2540M (-MT-MCP-) 
           arch: Sandy Bridge rev.7 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10376
           clock speeds: max: 3300 MHz 1: 2150 MHz 2: 1037 MHz 3: 1127 MHz
           4: 988 MHz
Graphics:  Card: Intel 2nd Generation Core Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.20.5 ) driver: i915
           Resolution: 1280x800@59.98hz
           OpenGL: renderer: Mesa DRI Intel Sandybridge Mobile
           version: 3.3 Mesa 19.2.8 Direct Render: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k5.3.0-51-generic
Network:   Card-1: Intel 82579LM Gigabit Network Connection (Lewisville)
           driver: e1000e v: 3.2.6-k port: 4060 bus-ID: 00:19.0
           IF: enp0s25 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Intel Centrino Advanced-N 6205 [Taylor Peak]
           driver: iwlwifi bus-ID: 24:00.0
           IF: wlo1 state: down mac: <filter>
Drives:    HDD Total Size: 320.1GB (34.8% used)
           ID-1: /dev/sda model: ST320LT007 size: 320.1GB
Partition: ID-1: / size: 292G used: 104G (38%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 57.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 234 Uptime: 1 day Memory: 1442.6/7871.2MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.201) inxi: 2.3.56
```
```
michas@server:~$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 4: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M
        |__ Port 4: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 1: Dev 3, If 0, Class=Vendor Specific Class, Driver=, 12M
        |__ Port 6: Dev 4, If 0, Class=Mass Storage, Driver=usb-storage, 480M
```


What more can I do to actually troubleshoot the issue and find out what is wrong?

Thank you so much for your time :)

---

### Post by michasrichter on 2020-05-16
Any ideas? :)

I found [this link]("https://forum.thinkpads.com/viewtopic.php?t=127819") relating to the Renesas chip and Sandy Bridge CPUs causing system stuttering due to ASPM power management. However, I was unable to improve the problem by deactivating ASPM...

Not sure what's going on exactly, if the link even applies...

---

### Post by gdesilva on 2020-08-30
Hi, I have the same issue - it only delivers max of 480M.

I found this link [https://mjott.de/blog/881-renesas-usb-3-0-controllers-vs-linux/](https://mjott.de/blog/881-renesas-usb-3-0-controllers-vs-linux/) but haven't got around to trying this solution and unlikely that I will be able to try it out soon. Please let me know if you have any success with it.

Thanks

---

### Post by gdesilva on 2020-09-04
Hi, I had a bit of time to check out the above link and had some success.

The blog describes how to do a firmware upgrade to 2.2.0.6 - I downloaded Markus' script and code compiled it and ran it; unfortunately the program failed with an error message stating it cannot identify the vendor and device id. Went through the code and my config but could not find why this error was generated.

Then I used my Win 7 dual boot to do the 2.2.0.6 firmware upgrade and booted back into Ubuntu and now the Renesas card uses the xhci_hcd driver and gets listed under the usb3 root hub.


Also, I found that when I first checked after the firmware update, I got lspci and lsusb outputs almost exactly the same as you posted above - ie lspci said xhci_hcd was the driver for the Renesas card but usb drive was mounted under bus 01 in lsusb. I raised this issue in AskUbuntu and one Terrance pointed out that I have the usb drive plugged into a different usb port and not the Renesas ports. Upon checking I found that this was the case. Unplugged it from USB2 port and plugged into Renesas USB3 port and voila, usb drive was mounted under bus 04 (USB3) root hub. Not saying that yours is the same problem but check it out again for this is a very likely situation.

---

