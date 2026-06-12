---
title: "Help ! Computer boots in black screen - AMD/Intel hybrid graphics."
date: 2012-04-26
forum: Hardware
---

### Post by brshadow on 2012-04-26
Hello,

I have a HP Pavillion g7-1205ev laptop and I just installed Precice Pangolin.

In order to boot into ubuntu I have to go into nomodeset or else my sceen is black

I cannot install the graphics drivers as it tells me “Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log.”

My graphics card is an intergrated VESA: Intel®Sandybridge Mobile Graphics.

What can I do to install he drivers ? I tried the "sudo apt-get install fglrx-updates fglrx-amdcccle-updates" and it did nothing.

Can someone PLEASE help me ?

---

### Post by brshadow on 2012-04-27
Hello,

I have a HP Pavillion g7-1205ev laptop and I just installed Precice Pangolin.

In order to boot into ubuntu I have to go into nomodeset or else my sceen is black

I cannot install the graphics drivers as it tells me “Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log.”

My graphics card is an intergrated VESA: Intel®Sandybridge Mobile Graphics.

What can I do to install he drivers ? I tried the "sudo apt-get install fglrx-updates fglrx-amdcccle-updates" and it did nothing.

Can someone PLEASE help me ?

---

### Post by coffeecat on 2012-04-27
Hi - I've merged the two threads you started. Please don't start multiple threads on the same problem. You may bump a thread after 24 hours if you don't get a response.

To your problem - if you have Intel graphics, installing fglrx packages will not help. They are for the proprietary driver for AMD/ATI graphics chipsets. So we can be sure which graphics you have, open a terminal and post the output of this command:

```
lspci | grep VGA

```

If you highlight the output with the mouse you can right-click to copy for pasting into your post. With this information someone should be able to help you.

---

### Post by brshadow on 2012-04-27
**After command**** lspci -nn**

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express root Port [8086:0101] (rev 09)
00:02.0  VGA compatible controller [0300]: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0  Communication controller [0780]: Intel Corporation 6 Series/C200 Series  Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB  controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family  USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio  device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family  High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express root Port 1 [8086:1c10] (rev b5)
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express root Port 2 [8086:1c12] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express root Port 3 [8086:1c14] (rev b5)
00:1d.0  USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset  Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
00:1f.2  SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset  Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] [1002:6760]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  05)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)

**After command lspci | grep VGA**

00:02.0  VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]

**My system is:**

Computer -----------> Laptop HP Pavillion g7-1205ev
Processor ----------> Intel® Core&#8482; i5-2430M CPU @ 2.40GHz × 4 
Graphics ------------> VESA: Intel®Sandybridge Mobile Graphics
Operating  ---------- > Ubuntu 12.04 Precise Pangolin 64bit

**Please help me as soon as possible**

---

### Post by coffeecat on 2012-04-27
You have Intel/AMD hybrid graphics:

> **brshadow said:**
> 
**After command lspci | grep VGA**

00:02.0  VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series]

Hybrid graphics can be problematic in Linux and I'm afraid I have no experience of them. I've found this thread which may help you:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) 

I'll also edit your thread title to include AMD/Intel hybrid graphics which may attract someone with experience of this.

---

### Post by brshadow on 2012-04-29
> **coffeecat said:**
> You have Intel/AMD hybrid graphics:



Hybrid graphics can be problematic in Linux and I'm afraid I have no experience of them. I've found this thread which may help you:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) 

I'll also edit your thread title to include AMD/Intel hybrid graphics which may attract someone with experience of this.

I tried this guide but when I type ```
sudo dpkg -i fglrx*.deb
```

I get some errors. if you would like me to post the errors i can format again and try to follow the guide again.

I also dont know if i have MUXED card as te guide says, and how to find out. 

I followed all the steps to the guide ( even after the errors I mentioned before) and now when my computer boots here is what i get.

[IMG]http://i49.tinypic.com/2z4woyc.jpg[/IMG]

After i Press ok

[IMG]http://i49.tinypic.com/2aep1t.jpg[/IMG]

After I choose "Just for this session"

[IMG]http://i50.tinypic.com/30n858i.jpg[/IMG]

A user has told me to type

> **miatawnt2b said:**
> login as you
sudo -s
cd /path_to_amd-driver-installer
./amd-driver-installer-12-xxx.run
keep pressing enter through the installer
when installer exits, type 'amdconfig -i'
shutdown -r now

And i dont know what is the path to amd driver...

Can someone please help me ? I need my computer...

Thank you

---

### Post by ubuntu27 on 2012-04-29
> **brshadow said:**
> 

A user has told me to type



And i dont know what is the path to amd driver...

Can someone please help me ? I need my computer...

Thank you

Did you download the driver? Wherever you saved, it is there. Perhaps it is in your home directory (/home/username) or your download directory (/home/username/Downloads)

Did you [do this]("http://ubuntuforums.org/showpost.php?p=11712748&postcount=1")?

```
cd ~/; mkdir catalyst12.3; cd catalyst12.3/
```
```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-3-x86.x86_64.run
```
```
chmod +x amd-driver-installer-12-3-x86.x86_64.run
```

---

