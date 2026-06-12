---
title: "Constant ATA Errors on Primary Drive"
date: 2009-06-04
forum: Hardware
---

### Post by rfdeshon on 2009-06-04
Hey all, I just picked up an MSI EX630 and installed ubuntu 9.04 on it. Everything runs smoothly but I noticed that my hard drive LED is almost always blinking even when it's just sitting idle. So I checked dmesg and found that I'm getting the following messages at a fairly constant rate.

```
[ 3701.211313] ata2.00: qc timeout (cmd 0xa0)
[ 3701.211349] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3701.211361] ata2.00: irq_stat 0x40000001
[ 3701.211384] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 3701.211388]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3701.211393]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 3701.211405] ata2.00: status: { DRDY ERR }
[ 3701.211421] ata2: hard resetting link
[ 3701.692073] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 3701.720135] ata2.00: configured for PIO0
[ 3701.720676] ata2: EH complete
[ 3729.292072] ata2.00: qc timeout (cmd 0xa0)
[ 3729.292105] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3729.292117] ata2.00: irq_stat 0x40000001
[ 3729.292141] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 3729.292145]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3729.292150]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 3729.292162] ata2.00: status: { DRDY ERR }
[ 3729.292178] ata2: hard resetting link
[ 3729.776109] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 3729.804138] ata2.00: configured for PIO0
[ 3729.804726] ata2: EH complete
[ 3749.056073] ata2.00: qc timeout (cmd 0xa0)
[ 3749.056107] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3749.056119] ata2.00: irq_stat 0x40000001
[ 3749.056145] ata2.00: cmd a0/00:00:00:fe:00/00:00:00:00:00/a0 tag 0 pio 16640 in
[ 3749.056150]          cdb 12 01 00 00 fe 00 00 00  00 00 00 00 00 00 00 00
[ 3749.056155]          res 51/54:03:00:fe:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 3749.056167] ata2.00: status: { DRDY ERR }
[ 3749.056183] ata2: hard resetting link
[ 3749.540095] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 3749.567953] ata2.00: configured for PIO0
[ 3749.568517] ata2: EH complete

```
From lshw:
```
     *-storage
          description: SATA controller
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi0
          logical name: scsi1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm msi ht bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
        *-disk
             description: ATA Disk
             product: WDC WD2500BEVT-2
             vendor: Western Digital
             physical id: 0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 11.0
             serial: WD-WXEZ08V74428
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=6dfd59f0

```
lspci:
```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: nVidia Corporation Device 0ad5 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:15.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:16.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:17.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9100M G (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
06:00.0 Network controller: RaLink RT2860
07:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
07:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
07:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
07:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

I've been googling for hours and, while I've found people getting similar messages often with DVD burners, haven't found any answers as to how to stop this. I'm sure it can't be good for the drive to have this happening and I imagine it's killing the battery life as well. Please, if anyone has any ideas I'd be grateful.

---

### Post by pastalavista on 2009-06-04
Try rebooting in recovery mode and open a root terminal and run ```
e2fsck
``` which is a file system check. Be sure you have backups of your important stuff before you run it. It usually doesn't lose anything, but if it's too messed up, it can.

---

### Post by rfdeshon on 2009-06-04
> **pastalavista said:**
> Try rebooting in recovery mode and open a root terminal and run ```
e2fsck
``` which is a file system check. Be sure you have backups of your important stuff before you run it. It usually doesn't lose anything, but if it's too messed up, it can.

Thanks for the suggestion... I'll give it a try but highly doubt it will work. I did a fresh reinstall of Ubuntu and formatted all partitions yet the problem persisted. I'll give it a go anyway though.

=Edit=
I've run both a manual fsck, and touched /forcefsck to run an automatic one on reboot. Neither found any problems with any filesystems and I'm still getting the same errors. This is making me consider going back to *shudders* Windows... which I do not want to do.

---

### Post by agne on 2009-06-04
I have the same problem but I get it when I stress my disk a little. And its really annoying. Have you any idea about what this is.

---

### Post by rfdeshon on 2009-06-04
I've not been able to find a solution still. I've opened a bug report for it though.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383632](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/383632)

I didn't know what else to do. I rather wish ahci had remained a module instead of being built into the kernel. I'm pretty sure, from some digging around, that the problem lies there and that blacklisting that module (if it were still actually a module) would probably fix it.

---

### Post by EddievV on 2009-06-04
Hi,

I have these errors already for one and a half year. I reported about them on this forum two days ago but received no answers until now. I even changed my harddisk half a year ago but that made no difference. So I suspect the motherboard now (Asus P5KC). I have no idea how I could check this further.

I posted this also on other forums but received no serious information about what is going on. I mainly use my PC in recovery mode and got a tip to prevent the messages to mess up the screen: 'dmesg -n1'. That works, but it is by no means a solution. 

Kind regards,
Eddie

---

### Post by EddievV on 2009-06-04
Hi,

Just found an interesting thread: [http://ubuntuforums.org/showthread.php?t=598837](http://ubuntuforums.org/showthread.php?t=598837) . Several persons report that the errors disappeared after changing the cable. So, I will try it soon and tell what happened.

---

### Post by rfdeshon on 2009-06-04
Yeah, I had read that one. Unfortunately the computer I'm having this issue on is a laptop so I highly doubt it's a problem with the cable. Normally laptops don't really use cables, the connector is generally soldered directly to the motherboard. Of course, I haven't taken this one apart to check so I could be wrong.

---

### Post by agne on 2009-06-04
I'll try switch my cables in the morning. What setup are u guys using, raid or anything?

---

### Post by EddievV on 2009-06-07
Hello Agne,

Yesterday I tried five different SATA cables, all the different versions I could find. The cables look very much alike but the connectors were quite different, from very loose to very tight. Anyway it did not make a difference, the error messages came in the very same way. It takes on average ten minutes before the first message shows up, then they come with a rate of several per minute, mostly in bunches of 2 or 3. Sometimes, if the computer is on for several hours, they come at a rate of about one per second.

At the shop where I bought the computer I obtained one of the five cables. They told me that it would not be the cable and asked me to bring the computer for a test. They now have a Linux-expert so I will see what that brings. It will probably take a week or so before I can tell the results here.

My setup is simple: ASUS P5KC motherboard with Intel chipset and a 650 GB Samsung harddisk. Initially I had a WD 500 GB which had the same problem, the messages came at even higher rate.

---

### Post by grakhul on 2009-06-14
I have the msi gx630 and I am having the exact same problems. I am using 64bit ubuntu 9.04.

```
Jun 14 21:14:05 deathstar kernel: [ 4763.771620] ata3.00: configured for PIO0
Jun 14 21:14:05 deathstar kernel: [ 4763.772106] ata3: EH complete
Jun 14 21:14:13 deathstar kernel: [ 4771.904084] ata3.00: qc timeout (cmd 0xa0)
Jun 14 21:14:13 deathstar kernel: [ 4771.904205] ata3: hard resetting link
Jun 14 21:14:14 deathstar kernel: [ 4772.388075] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 14 21:14:14 deathstar kernel: [ 4772.415688] ata3.00: configured for PIO0
Jun 14 21:14:14 deathstar kernel: [ 4772.416164] ata3: EH complete
Jun 14 21:14:24 deathstar kernel: [ 4783.104089] ata3.00: qc timeout (cmd 0xa0)
Jun 14 21:14:24 deathstar kernel: [ 4783.104211] ata3: hard resetting link
Jun 14 21:14:25 deathstar kernel: [ 4783.588087] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 14 21:14:25 deathstar kernel: [ 4783.615864] ata3.00: configured for PIO0
Jun 14 21:14:25 deathstar kernel: [ 4783.616376] ata3: EH complete
Jun 14 21:14:38 deathstar kernel: [ 4796.788092] ata3.00: qc timeout (cmd 0xa0)
Jun 14 21:14:38 deathstar kernel: [ 4796.788219] ata3: hard resetting link
Jun 14 21:14:38 deathstar kernel: [ 4797.272090] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 14 21:14:38 deathstar kernel: [ 4797.299945] ata3.00: configured for PIO0
Jun 14 21:14:38 deathstar kernel: [ 4797.300446] ata3: EH complete
```

trying to figure this one out, but so far no luck.

---

### Post by grakhul on 2009-06-16
I don't think this has anything to do with the MSI GX630.  This may be a known kernel issue.

---

### Post by grakhul on 2009-06-16
Well I am happy to report that this is not my harddrive.

I have isolated it to the dvd drive which makes me feel better.  If I pop in a cd or keep the drive bay open the messages stop.  If I close the dvd drive bay (without a cd in the drive) the message appear.

Still trying to figure this one out, but I am glad I won't be experiencing any corruption of my harddrive.

---

### Post by rfdeshon on 2009-06-16
> **grakhul said:**
> Well I am happy to report that this is not my harddrive.

I have isolated it to the dvd drive which makes me feel better.  If I pop in a cd or keep the drive bay open the messages stop.  If I close the dvd drive bay (without a cd in the drive) the message appear.

Still trying to figure this one out, but I am glad I won't be experiencing any corruption of my harddrive.

This is excellent news! I'll have to update the bug report that I have open with this information. I'm actually a bit upset at myself for not trying this considering I had seen a number of reports of similar errors being related to optical drives, not hard drives. Thanks!

---

### Post by rfdeshon on 2009-06-16
I can confirm that these errors stop when I have media in my DVD burner. Unlike your case, however, the errors continue when the drive is open. Also, your error messages reference ata3 whereas mine reference ata2... I'm assuming this is because your laptop is the gx and mine is the ex.

---

### Post by EddievV on 2009-07-05
Hello all,

Maybe a little late but I promised to give the results of my tests. First I tried five different cables, the main difference appeared to be in the connectors. Some were attached quite loose, others very rigid. The result: all cables kept giving me the ata-errors.

A collegue told me that occasionally these errors seem to appear when the 5-volt of the power supply is not stable. This is not the case with my mobo. His final proposal: upgrade the BIOS. Good idea because when I bought my P5KC it was on the market for only one week. It took me quite some time before I dared to do it because if it goes wrong the mobo is wasted. Anyway I managed but the result: no change, the errors keep coming.

A completely different test for a change: I installed the beta-version of Windows-7. This was very straightforward and everything worked immediately: the screen resolution was correct, internet worked and I even had sound from my Toslink output. Under Ubuntu this had cost me several weeks. (I must add that the sound quality of Windows Media Player was very poor, so I really need to stay with real time Linux). I did a lot of checks under Windows-7, including copying 150 GB of wav-files at once. Everything worked OK, I read all the log files I could find and there was no indication whatsoever of hard disk errors. 

My conclusion therefore remains: the ata-errors are somehow caused by the combination of mobo and Linux. Unfortunately after almost two years I still found nobody that can give me any clue on how and why. My next try: buy a new computer and hope that this error stays away.

---

### Post by gehzumteufel on 2009-07-30
I get similar irq_stat errors constantly. I have no media drive....

I am going back to Windows because it is to slow also.

---

