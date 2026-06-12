---
title: "Radeon R7 M260 on Catalyst drivers"
date: 2014-08-17
forum: Hardware
---

### Post by revberaldo on 2014-08-17
I recently bought a Dell Inspiron 5547 and installed Ubuntu 14.04 on it. Almost everything worked great out of the box. This laptop comes with two graphic cards, an Intel HD Graphics 4400 and an AMD R7 M260. The Intel card works as expected, apart from the occasional tear when scrolling or moving a window around.

Here's the output from [FONT=courier new]lspci[/FONT]:

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
03:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260] (rev ff)
```

I was able to install AMD's Catalyst following [these instructions from the AMD Linux Communit's wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide"). I was able to get the driver to work, and I can even switch between the two cards. However, the performance is terrible with the AMD card. Moving windows around cause *a lot* of tearing, resizing windows is slow and even scrolling down a page on Firefox is slow. Dota 2 runs at a low FPS and ugly, whereas I can run it perfectly using the Intel 4400, which is much less powerful.

I tried many workarounds, such as [FONT=courier new]amdconfig --sync-video=on[/FONT] and other [FONT=courier new]xorg.conf[/FONT] options I found on the Arch Linux wiki. Nothing worked, and the graphics card always performed poorly. Here's my current [FONT=courier new]xorg.conf[/FONT]:

```
Section "ServerLayout"
    Identifier "amd-layout"
    Screen 0 "amd-screen" 0 0
EndSection

Section "Device"
    Identifier "intel"
    Driver "intel"
    Option "AccelMethod" "uxa"
    BusID "PCI:0@0:2:0"
EndSection

Section "Device"
    Identifier "amd-device"
    Driver "fglrx"
    BusID "PCI:3:0:0"
EndSection

Section "Monitor"
    Identifier "amd-monitor"
    Option "VendorName" "ATI Proprietary Driver"
    Option "ModelName" "Generic Autodetecting Monitor"
    Option "DPMS" "true"
EndSection

Section "Screen"
    Identifier "amd-screen"
    Device "amd-device"
    Monitor "amd-monitor"
    DefaultDepth 24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

[NotebookCheck has some interesting information]("http://www.notebookcheck.net/AMD-Radeon-R7-M260.122208.0.html") on my graphics card:

> Just like the older Radeon HD 8700M and 8600M series, it is based on the Mars chip (28nm GCN architecture) with 384 shader cores, 24 TMUs and 8 ROPs.

According to [this page]("http://wiki.cchtml.com/index.php/Hardware"), all RadeonHD 7000-series and 8000-series are supported by the Catalyst. Since the R7 M260 is newer than the 8000-series (or so it seems), I assume it is supported by Catalyst. On the other hand, the card may be just too new and not yet supported on Linux (wouldn't surprise me). [According to Wikipedia]("http://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units#Radeon_.28Rx_200.29_Series"), the R7 M260 was launched in June 2014.

Is there anything I'm overlooking or could try to get a better performance out of the card? Have you had any similar problems? If you need more information, please let me know and I'll update this post.

---

### Post by JDorfler on 2014-08-17
You have to install the newest Catalyst driver's manually.  Download and unzip the contents to a folder in your home.  Then go [here]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD").  Just make sure you change the code to the file you have downloaded and openned.

---

### Post by revberaldo on 2014-08-21
> **JDorfler said:**
> You have to install the newest Catalyst driver's manually.  Download and unzip the contents to a folder in your home.  Then go [here]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD").  Just make sure you change the code to the file you have downloaded and openned.

Hi JDorfler, thank you for the answer. That's exactly what I did. I followed [these instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Trusty_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL") to install the lastest beta drivers *and* also followed the instructions for the stable drivers, but the performance was the same on both versions.

---

### Post by QIII on 2014-08-21
Hi!

There is a lot of your pain going around.

I have learned to not get the absolute, up to the minute offerings from graphics adapter OEMs because drivers that will work with Linux are often not immediately available.

The OEMs spend their effort on Windows, where the money is, and get around to Linux when they have a chance.

Just a reality in the Linux world.

---

