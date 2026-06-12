---
title: "Card Reader (RTS5116 ) Problem.."
date: 2012-09-29
forum: Hardware
---

### Post by pyrokinetic on 2012-09-29
The only issue I have with my Ubuntu install is my INTERNAL card reader not working (Thought I'd state this first, in case anybody decided to tell me to unplug it and plug it back in :P )

When I type in lspci this is what I get..

```
pyrokinetic@pyrokinetic:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```

I'm running Ubuntu 12.04 LTS, it's installed and NOT on a dual boot (I only have Ubuntu).....worked perfectly with WIndows 7 but can't be recognized here. I found a post somewhere on a Gentoo forum (I think) with someone complaining of the exact same problem and it was suggested that perhaps a kernel upgrade was in order. Not sure if that's the case here though..

Your thoughts? :D

---

### Post by ahallubuntu on 2012-09-29
Please post the output of "lsusb" so we might see the device ID of your card reader...

---

### Post by pyrokinetic on 2012-09-29
> **ahallubuntu said:**
> Please post the output of "lsusb" so we might see the device ID of your card reader...

Sure thing, but you won't see anything because it's not a USB card reader, it's internal (as I stated in my first post)....I'm on a laptop.

```
pyrokinetic@pyrokinetic:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05c8:021e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 004: ID 046d:08ca Logitech, Inc. Mic (Fusion)

```

---

### Post by ahallubuntu on 2012-09-29
Sorry - I see it now in your lspci list after all.  Both of my laptops have their internal card readers listed under lsusb, because that's how many of them are connected (as if they were plugged into a USB port).

This suggests that your card reader was fixed in version 3.4 of the kernel:

[https://bbs.archlinux.org/viewtopic.php?id=131791](https://bbs.archlinux.org/viewtopic.php?id=131791)

which I suppose you could try to install in Ubuntu 12.04 .

Someone also pointed to this Realtek driver:

[http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false)

It's possible that building out RTS5229 or RTS5209 from that page may give you a module that will work.  Realtek part numbers are confusing; sometimes different part numbers refer to the same product and it's not clear why.

---

### Post by pyrokinetic on 2012-09-30
> **ahallubuntu said:**
> Sorry - I see it now in your lspci list after all.  Both of my laptops have their internal card readers listed under lsusb, because that's how many of them are connected (as if they were plugged into a USB port).

This suggests that your card reader was fixed in version 3.4 of the kernel:

[https://bbs.archlinux.org/viewtopic.php?id=131791](https://bbs.archlinux.org/viewtopic.php?id=131791)

which I suppose you could try to install in Ubuntu 12.04 .

Someone also pointed to this Realtek driver:

[http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false)

It's possible that building out RTS5229 or RTS5209 from that page may give you a module that will work.  Realtek part numbers are confusing; sometimes different part numbers refer to the same product and it's not clear why.

Ahhh yeah, I found that post earlier too and have tried the available Linux driver and followed all instructions in the readme.txt and got no errors but it still didn't work. I'm a bit reluctant to try a different kernel if the driver that is SUPPOSED to work with it doesn't work, if that makes sense..

---

### Post by srikanth1986 on 2012-12-08
I have the exact same issue for the same card. But I am on Kubuntu 12.10. I even installed the driver from realtek site but it din't help. Any suggestions?

srikanth@srikanth-pc:~$ sudo lspci
[sudo] password for srikanth: 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Ralink corp. Device 539b
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

### Post by ranjan_mg on 2013-01-03
Any luck on this ? I have same card (RTS5116) and same result. SD card reader wont' work
I tried the driver from realtek web site, but no luck there either,

---

### Post by mmelzalabany on 2013-01-16
Hey. I had the same problem with my new hp Pavilion g4 laptop and I have just fixed it. I am using Ubuntu 12.10 32 bits. Here is what I did:

1. Follow this link to know the exact model of your card reader. mine was RealTek smth smth.

[http://askubuntu.com/questions/20100/how-can-i-find-out-what-kind-of-card-reader-i-have](http://askubuntu.com/questions/20100/how-can-i-find-out-what-kind-of-card-reader-i-have) 

and the output before the solution was like this:

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)

2. Download the suitable driver from this site:

[http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false)

3. Extract the zipped archive, then again extract the tar archive, then cd into the final directory, open the reademe file and follow the instructions.

4. After reboot, it simply worked :)

5. Note that I didn't notice a change in the output after the solution.

---

### Post by paradoxcy on 2013-07-05
> **mmelzalabany said:**
> Hey. I had the same problem with my new hp Pavilion g4 laptop and I have just fixed it. I am using Ubuntu 12.10 32 bits. Here is what I did:

2. Download the suitable driver from this site:

[http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false)

3. Extract the zipped archive, then again extract the tar archive, then cd into the final directory, open the reademe file and follow the instructions.

4. After reboot, it simply worked :)

5. Note that I didn't notice a change in the output after the solution.

Hi. Sorry for replying to an old thread, but I am facing the same problem. I downloaded the drivers from the link you mentioned using chromium. Then extracted the files at the same location and read the readme file. But I am not clear how to proceed with the build steps. 

I am sure I have not understood your reply from 'then cd into the final directory', I suspect I am doing something wrong from that step onwards.

Any help will be appreciated.

---

