---
title: "Using a kubuntu LiveCD to stress test a troublesome Windows system"
date: 2012-07-28
forum: Hardware
---

### Post by brm on 2012-07-28
Please forgive the elementary nature of these questions. A recently-widowed friend has asked me to help troubleshoot her late husband's large and powerful Windows 7 system. I am myself somewhat preoccupied with other matters and am sure that I am missing one (or more) obvious solution(s).

The major constraint is that her late husband was a professional photographer and he has image files everywhere on his system. There is exactly one USB backup drive and so far I have no idea whether the backup is complete (I doubt it) or restorable. I am being careful therefore to limit anything I do to non-destructive testing that does not touch the hard disks until I have time to do an exhaustive search for all his image files and ensure that there are *_multiple_* backups of each. Moreover, I have just learned that he had performed a very expert calibration of his system to a professional colour printer. I have no idea what or where those calibration files are.

Since I almost always use Kubuntu, my primary resource (at the outset) is a CD of Kubuntu amd64 12.04 LTS.

The obvious symptom on the Windows 7 machine is a BSOD (Blue Screen of Death) almost every 20 minutes. This is so frequent as to make the machine unusable.

The first exception code on the BSOD is a memory location of <multiple zeros>1. Her tech support person (owner of a well-known local computer store and fellow photographic expert) says that the single digit in the exception code suggests a hardware failure, probably on the motherboard.

I have been running Kubuntu from the liveCD for over eighteen hours which does not support the defective motherboard hypothesis. But my mind has gone blank on how to stress-test the hardware without writing to any hard disks. Google has not been a friend; on this problem, I have found it surprisingly unhelpful.

So far, I have been running just a browser, a konsole session and glxgears. The latter will put some load on the CPU and more on the graphics subsystem. Google did lead me to a sourceforge utility called systester which at least tests the CPU by attempting to calculate pi to many millions of significant digits. But I cannot get it to run.

So my questions are the following:
1. Does anyone have suggestions on safe non-destructive hardware stress-testing applications? I have no objection to downloading and burning to CD a specialized distro.
2. Is anyone familiar with systester? ( [http://systester.sourceforge.net/about.php](http://systester.sourceforge.net/about.php) ). The sourceforge site provides precompiled generic binaries for both i686 and amd64, both CLI and qt-based GUI versions. I have tried copying the binaries to /usr/local/bin/, chowning the binaries to root: and running as root. But, running off the Kubuntu LiveCD, I get consistent "permission denied" errors. BTW, the LiveCD drops straight to a root prompt when one enters "sudo -s" into a terminal session. There is no password.

The system is an Intel i7 with 8GB of RAM. It is a 2008-vintage Asus P6T motherboard; the catch is that it takes an LGA1366 CPU, which is no longer available. Replacing both the motherboard and CPU will cost north of $500 and my reluctance to recommend that my friend spend that sort of money is heightened by the last 18 hours of evidence that the problem is not with the MB.

The following is the output of lspci. I have tried running hwinfo, but it produced hundreds of lines of output. I will post only if someone finds it potentially useful.

```

root@kubuntu:/usr/local/bin# lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 12)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 12)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 12)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 12)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 12)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 12)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 12)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 12)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 12)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 12)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 12)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4850]
02:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870]
03:00.0 Multimedia controller: Philips Semiconductors SAA7231 (rev aa)
04:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
04:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
05:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 46)
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 04)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 04)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 04)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 04)
root@kubuntu:/usr/local/bin#

```

---

### Post by ahallubuntu on 2012-07-28
What is your actual goal here?  The first goal would probably be backing up any important files he had (that she cares about) such as his pictures.  If you aren't sure if the backup he made is adequate, make another full backup.  You can save just the JPG file if you want.  You can do this with Kubuntu.   You can mount his hard drive and do a "find" (in a terminal) for all JPG files on the drive and copy them to another drive.  Photographers use other formats besides JPG - PNG, TIFF, PSD (Photoshop), etc. are all common formats. 

You can try to backup using the existing computer or even attaching the drive to another computer.  In any event, I'd test the drive's S.M.A.R.T. status (see below) first to see if the drive is failing or close to it, and I'd backup BEFORE doing any kind of stress test.

After you have made a backup of everything, your next task seems to be trying to make this computer functional and reliable again so his widow can use it?

Blue screens in Windows can be caused by a variety of things, hardware and software.  A bad driver or flakey piece of software could cause blue screens.  But a hardware problem is more likely in my opinion.  Generally, my approach is to test the easy components first and rule them out: RAM, power supply, cooling system, and hard drive.  It's possible an add-in card (video card) could be failing and so could the CPU but I highly doubt the CPU itself has failed.  The other things are much more likely.

If you've tested and ruled those obvious things out, it's probably the motherboard, which you can replace of course.  (The board itself isn't worth fixing most likely.)  Or - maybe it's not hardware at all; maybe it is software.  You could rule that out probably by doing a clean install of Windows (or Linux).

The Ultimate Boot CD (UBCD) is a great resource for testing hardware.  Google for it.  It includes utilities for testing most of the components above (except power supply), including a CPU stress test  It also includes a handy little Linux distro called Parted Magic.  Use the SmartControl (smartmontools) feature of Parted Magic after you boot it to check the drive's S.M.A.R.T. status.  Look for any Attributes listed in red.  If there are no attributes listed in red, the hard drive is probably not failing.

---

### Post by ahallubuntu on 2012-07-28
Check that the CPU fan is working, and clean out any dust/dirt that could be causing it to overheat.  That's very common and could certainly cause blue screens.

The average person doesn't have a power supply tester laying around, but trying another good working power supply is one way to rule that out as a possible cause.

---

