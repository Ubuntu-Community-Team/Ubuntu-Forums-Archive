---
title: "Ubuntu 8.04 (hardy) 64 and HP Deskjet F2430 Scanning problems."
date: 2009-11-27
forum: Hardware
---

### Post by dawolf123 on 2009-11-27
I just got the HP Deskjet F2430 from Black Friday sales and went to set it up on my Ubuntu Desktop PC and loaded the new HPLIP 3.9.10 Drivers from the HP site which it says supports the Deskjet F2430. I am able to print without problems. However, when I try to scan with XSANE the scanner begins to scan (as in a can here the scan head moving) but when it appears to get to the part of scanning it locks up and XSANE says the device is unavaliable. 
Here is lspci dump:
```
garret@hal2001:/$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Primary)
03:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT (PCIE)] (Secondary)
04:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
garret@hal2001:/$ 

```uname -a dump ```
garret@hal2001:/$ uname -a
Linux hal2001 2.6.24-25-generic #1 SMP Tue Oct 20 06:49:12 UTC 2009 x86_64 GNU/Linux

```This is the error I am recieving from XSANE in my syslog
```
Nov 27 12:45:31 hal2001 xsane: io/hpmud/dot4.c 231: unable to read Dot4ReverseReply header: Resource temporarily unavailable bytesRead=0 
Nov 27 12:45:31 hal2001 xsane: io/hpmud/dot4.c 659: invalid Dot4CloseChannelReply: cmd=2, result=4 
Nov 27 12:45:35 hal2001 xsane: io/hpmud/dot4.c 231: unable to read Dot4ReverseReply header: Resource temporarily unavailable bytesRead=0 
Nov 27 12:45:35 hal2001 xsane: io/hpmud/dot4.c 368: invalid DOT4ExitReply: cmd=8, result=4 
Nov 27 12:45:36 hal2001 xsane: sane_hpaio_cancel: already cancelled! 
``` I have spent about an hour googling this problem with no real leads. I did find a bug that was patched in older release of ubuntu but did not want to try it since they stated that it should be corrected in the next major release (which I am using). 
Any help will be much appreciated. Thanks in advance.

---

### Post by dawolf123 on 2009-11-27
I believe I might have posted this in incorrect thread. This is a desktop/printer issue not laptop related. Please move if possible. Thanks... sorry for the mixup.

---

### Post by dawolf123 on 2009-11-27
CORRECTION:: The XSANE error is not device is unavaliable. It is Error during device I/O please see screenshot. [http://picasaweb.google.com/lh/sredir?uname=gdewulf&target=PHOTO&id=5408852543039585362&aid=5408852487510821809&authkey=Gv1sRgCNqLlfung_Tp_QE&feat=email](http://picasaweb.google.com/lh/sredir?uname=gdewulf&target=PHOTO&id=5408852543039585362&aid=5408852487510821809&authkey=Gv1sRgCNqLlfung_Tp_QE&feat=email)
_[IMG]http://picasaweb.google.com/lh/sredir?uname=gdewulf&target=PHOTO&id=5408852543039585362&aid=5408852487510821809&authkey=Gv1sRgCNqLlfung_Tp_QE&feat=email[/IMG]_[IMG]http://picasaweb.google.com/gdewulf/XSANEError#5408852543039585362[/IMG]

---

