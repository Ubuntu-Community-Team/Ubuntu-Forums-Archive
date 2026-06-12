---
title: "Unable to install drivers for amd radeon 8570m on 14.04 64 bit."
date: 2014-10-12
forum: Hardware
---

### Post by risva on 2014-10-12
Hello all,

i ve taken a new Lenovo G50-45 80E300GYIN notebook, it comes with AMD A8-6410proc (inbuilt graphics) and a Radeon HD 8570M graphic card.

ive ofcourse installed ubuntu, 14.04 64bit.

im unable to install drivers for the graphic card and power management

the result of lspci is as under

```

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon APU A4-6000 with R2 Graphics] (rev 05)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun LE [Radeon HD 8550M]
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)



```

also, the integrated graphics with A8-6410 is R5 series, as against R2 drivers installed.

I'm amateur in linux, whatever i write above is from meaning derived from other threads.

please, help me get my new machine running!!

---

### Post by risva on 2014-10-12
the driver for for amd processor is provided by amd at:
[http://support.amd.com/en-us/download/desktop?os=Linux+x86](http://support.amd.com/en-us/download/desktop?os=Linux+x86)

however, sudo sh ./amd-.......xxxxx.run

gives an error,
sh: 0: cant open ./amd-......xxxx.run

---

### Post by Vladlenin5000 on 2014-10-12
Are you sure you're running the script from the folder where you downloaded it? The "./" implies that. If you aren't in the folder where the script is then you need to give the full path instead of "./".

---

### Post by risva on 2014-10-13
Thanx Vladlenin,

probably i was doing something wrong there only. the catalyst driver, is now installed.

However, i'm not sure wether all the components on my machine(Lenovo G50-45 80E300GYIN) have been provided apropriate drivers. can you please suggest any way of checking it.

---

### Post by risva on 2014-10-13
the lspci output now is:

```

risva@risva-Lenovo-G50-45:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon APU A4-6000 with R2 Graphics] (rev 05)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Sun LE [Radeon HD 8550M]
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)


```

---

### Post by Vladlenin5000 on 2014-10-13
If your wireless is working I don't think you need any additional driver. Everything else seems to be pretty standard and natively supported.

---

### Post by risva on 2014-10-14
thank you Vladlenin,
     I assume my machine is totally up and am very happy about it.
 
     Can some one please tell me, if i can make a image of my current system. the aim is, that if i need to format my machine for any rreason, i don't have to start from scratch; installing 14.04 first, then updates, upgrades and then drivers....if i can bring my machine to current state with just one execute, it will be of immense use(time and effort).

---

### Post by Vladlenin5000 on 2014-10-14
I would suggest Clonezilla, a free and reliable tool.

---

### Post by risva on 2014-10-15
thanks!!

---

### Post by wyfsysf on 2014-10-17
&#305; have the same problem.whats the solution ?

---

