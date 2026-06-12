---
title: "many problems with MSI CX600 laptop"
date: 2009-10-01
forum: Hardware
---

### Post by Khalid Yousif on 2009-10-01
Hello Ubuntuers :)

I purchased a brand new laptop several days ago, it is MSI CX600 laptop, it has Intel Core 2 Duo T6500 processor, 4GB of RAM, and ATi Mobility Radeon HD 4330 graphics adapter.

So I went to install Ubuntu 9.04 (64-bit version), and the first problem I went into was when the Live CD started to load, the computer just froze, following some advice to use noacpi and acpi=off options, the Live CD got loaded, and I started the installation.

The installation went okay, but after that, I realized that the Ethernet adapter isn't working properly, it is a SiS191 adapter, I googled it and noticed many complains about it, there is a workaround of making the MTU to 1492, I tried this workaround but still didn't work, maybe because I am using the 64-bit version of Ubuntu?

Ubuntu didn't recognize the wireless adapter (RaLink 3090), I guess that I have to install some driver for it, not sure how, the Hardware Drivers didn't show it in its list.

Hardware Drivers also didn't show the graphics card, though it did showed it before the installation, also I heard that the ATi drivers that Ubuntu uses are broken or something (not compatible with the specific X.org version that it uses?), and I didn't find drivers for it in AMD website, so I am kind of lost.

The only thing that worked okay is the sound device, unlike the troubles reported about it in Microsoft Windows!

Here is the output of lspci command in the terminal:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
02:00.0 Network controller: RaLink Device 3090
```So I wonder if I have to file a bug report about the Ethernet driver (and how to do so?), or is there any available solution for it?
Also how to find and install the wireless driver?
And if ATi drivers support will get better for the next releases of Ubuntu, is there any hope for my graphics card to work okay with Ubuntu at the moment?

Thanks :)

---

### Post by bell1996 on 2009-10-01
I have the same graphics card (Raedon Mobility 4330) in my HP laptop. I got it to work. Using 8.04. Had to install the ATI drivers from the AMD web site.

---

### Post by Khalid Yousif on 2009-10-01
> **bell1996 said:**
> I have the same graphics card (Raedon Mobility 4330) in my HP laptop. I got it to work. Using 8.04. Had to install the ATI drivers from the AMD web site.

I didn't find anything regarding 4300 series in AMD website => [http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=2.4.2.3.32&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.2&product=2.4.2.3.32&contentType=GPU+Download+Detail&ostype=Linux+x86_64&keywords=&items=20), which series did you install?

---

### Post by DarkZatarra on 2009-10-01
I have a MSI from VX600 series and I have the same problems. First of all my ethernet driver doesn't work, secondly.. the wireless and last but not least the ATI isn`t recognised. If anyone can help at least with the ethernet driver I will be gratefully. Tnx in advande and I hope somebody will manage to deal with those problems.

---

### Post by Khalid Yousif on 2009-10-02
> **DarkZatarra said:**
> I have a MSI from VX600 series and I have the same problems. First of all my ethernet driver doesn't work, secondly.. the wireless and last but not least the ATI isn`t recognised. If anyone can help at least with the ethernet driver I will be gratefully. Tnx in advande and I hope somebody will manage to deal with those problems.

VX600 and CR600 are so similar regarding the hardware, are you using Ubuntu 64-version or the 32-bit one?

If you searched for "sis191 ubuntu" you will find many users complain about it as well, and some advised for a workaround of decreasing the MTU to 1492 and less, it didn't work with me anyway.

For the wireless adapter, check this link => [https://wiki.ubuntu.com/LaptopTestingTeam/MSICR400](https://wiki.ubuntu.com/LaptopTestingTeam/MSICR400)

For the ATi video card, I am really confused, should use the supplied binary with Ubuntu? or download some driver from AMD website? what are the advantages/disadvantages of each one of them :confused:

---

### Post by bell1996 on 2009-10-02
Khalid -

Use the following link to get to the AMD downloads. I don't know why it's so hard to navigate the web site now. something changed, but I book marked the link:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.4&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.4&lang=English)

---

### Post by bell1996 on 2009-10-02
Kahlid -

Don't use the Ubuntu drivers. Used the downloaded AMD drivers.

---

### Post by Khalid Yousif on 2009-10-02
> **bell1996 said:**
> Kahlid -

Don't use the Ubuntu drivers. Used the downloaded AMD drivers.

This is ATi driver version 9.3, shouldn't be more safe to use the latest version 9.9?

---

### Post by DarkZatarra on 2009-10-21
I solved the problem with the internet by reducing MTU to 1024 ;-). Tnx for the replies.

---

