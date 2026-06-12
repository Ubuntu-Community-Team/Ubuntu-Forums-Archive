---
title: "Impossible to install Intel Driver Graphics in Ubuntu 16.04 LTS"
date: 2016-11-04
forum: Hardware
---

### Post by migrainepill on 2016-11-04
I've been trying to update my graphic drivers with the Intel Tool in Ubuntu but I keep getting the same errors over and over and I'm not quite sure how it could be solved. The graphics installed right now are not the correct ones either.

My processor is: Intel® Core&#8482; i3-2328M CPU @ 2.20GHz × 4 

Graphics Installed: Intel® Sandybridge Mobile 

[http://image.prntscr.com/image/0aece6960dbe474ca703035fdd3abdaf.png](http://image.prntscr.com/image/0aece6960dbe474ca703035fdd3abdaf.png)
[http://image.prntscr.com/image/d5226334568642e7941768e7baf244a9.png](http://image.prntscr.com/image/d5226334568642e7941768e7baf244a9.png)

[HR][/HR]
Is there any way I can update the drivers to the correct ones? 
Thanks in advance!

---

### Post by ajgreeny on 2016-11-04
Do you actually have a problem with graphics on the machine and what driver is it using at present?
```
lspci -k
``` command will tell us all if you are not sure, but in most circumstances Intel hardware is fully supported out of the box, particularly in recent Ubuntu versions such as 16.04 as you're using.

---

### Post by oldfred on 2016-11-04
Please attach screen shots, not post in line.
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

It looks like you still have the CD-ROM (which now must be DVD or flash drive) option checked as a repository.
Go to System Settings, Software & updates, first tab. Uncheck the CD-Rom. Make sure the source (Download from:) for software is a local repository. It probably has default, but if you click on it, then you can choose to let it find better one. It only uses ping times so may not be optimal for download speed.

Screen shot is older, but still pretty current.

---

### Post by mc4man on 2016-11-04
While I'm not sure you'd gain any advantage (and other ways to get newer driver),  you'd need to bypass the weak digest. In a terminal run this which should allow the install - 
```
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-4 -O - | sudo apt-key add -
```
Wait until it finishes, (" written to stdout [1751/1751]" ),  see screen 1, then go ctrl+c to exit action &  return to prompt.

Now open up Intel tools & it should work, see screens 2 & 3

---

### Post by coffeecat on 2016-11-05
Not a Multimedia Software question.

*Thread moved to **Hardware**.*

@migrainepill, I've reduced your huge inline images to links. Please consider those with bandwidth restrictions and those using mobile devices when posting images. Please see oldfred's post for how to attach a thumbnail image.

---

### Post by migrainepill on 2016-11-05
Thanks to all who offered a bit of their time! My apologies about posting the images tho.

> **ajgreeny said:**
> Do you actually have a problem with graphics on the machine and what driver is it using at present?
```
lspci -k
``` command will tell us all if you are not sure, but in most circumstances Intel hardware is fully supported out of the box, particularly in recent Ubuntu versions such as 16.04 as you're using.

The code gave me these results:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)        Subsystem: ASUSTeK Computer Inc. 2nd Generation Core Processor Family DRAM Controller
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
        Subsystem: ASUSTeK Computer Inc. 2nd Generation Core Processor Family Integrated Graphics Controller
        Kernel driver in use: i915
        Kernel modules: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. 7 Series/C210 Series Chipset Family USB xHCI Host Controller
        Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
        Subsystem: ASUSTeK Computer Inc. 7 Series/C210 Series Chipset Family MEI Controller
        Kernel driver in use: mei_me
        Kernel modules: mei_me
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
        Subsystem: ASUSTeK Computer Inc. 7 Series/C210 Series Chipset Family USB Enhanced Host Controller
        Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. 7 Series/C210 Series Chipset Family High Definition Audio Controller
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
        Subsystem: ASUSTeK Computer Inc. 7 Series/C210 Series Chipset Family USB Enhanced Host Controller
        Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
        Subsystem: ASUSTeK Computer Inc. HM76 Express Chipset LPC Controller
        Kernel driver in use: lpc_ich
        Kernel modules: lpc_ich
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
        Subsystem: ASUSTeK Computer Inc. 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
        Kernel driver in use: ahci
        Kernel modules: ahci                                                                                                   
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)                                 
        Subsystem: ASUSTeK Computer Inc. 7 Series/C210 Series Chipset Family SMBus Controller                                   
        Kernel modules: i2c_i801                                                                                                
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
        Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe
        Kernel driver in use: rt2800pci
        Kernel modules: rt2800pci
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader (rev 01)
        Subsystem: ASUSTeK Computer Inc. RTL8411 PCI Express Card Reader
        Kernel driver in use: rtsx_pci
        Kernel modules: rtsx_pci
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
        Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
        Kernel driver in use: r8169
        Kernel modules: r8169 
```

The problem it comes when I try to use a game and the graphics come as bugged (blurry textures, lag, etc.) I filled a JIRA/ticket in the support forums of the said game and they spotted the problem with the graphics, what they said was that my laptop was using OpenSource Graphics instead of the Intel ones, that's why I was trying to update them to the correct ones.


> **oldfred said:**
> It looks like you still have the CD-ROM (which now must be DVD or flash drive) option checked as a repository.
Go to System Settings, Software & updates, first tab. Uncheck the CD-Rom. Make sure the source (Download from:) for software is a local repository. It probably has default, but if you click on it, then you can choose to let it find better one. It only uses ping times so may not be optimal for download speed.

Screen shot is older, but still pretty current.

I looked for the tab you indicated me but this is what I got (see first attachment)

> **mc4man said:**
> While I'm not sure you'd gain any advantage (and other ways to get newer driver), you'd need to bypass the weak digest. In a terminal run this which should allow the install - 
```
wget --no-check-certificate https://download.01.org/gfx/RPM-GPG-KEY-ilg-4 -O - | sudo apt-key add -
```
Wait until it finishes, (" written to stdout [1751/1751]" ), see screen 1, then go ctrl+c to exit action & return to prompt.

Now open up Intel tools & it should work, see screens 2 & 3

I tried doing this a few times and each time I got the same error I posted before (see second attachment)

---

### Post by oldfred on 2016-11-05
What version of Ubuntu are you running?
fred@Z170N:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"


My current version sytem settings screen looks almost the same as the old one posted above?

---

### Post by migrainepill on 2016-11-05
> **oldfred said:**
> What version of Ubuntu are you running?
fred@Z170N:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"


My current version sytem settings screen looks almost the same as the old one posted above?

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial
```

This is what I get when I run lsb_release -a

---

### Post by Yellow Pasque on 2016-11-05
> **migrainepill said:**
> I filled a JIRA/ticket in the support forums of the said game and they spotted the problem with the graphics, what they said was that my laptop was using OpenSource Graphics instead of the Intel ones

That does not make sense. The Intel drivers are open source (Intel doesn't make closed source Linux drivers). Simple glxinfo will tell you:
```
glxinfo | grep string
```
If you see something like:
```

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile
```
..then you have the correct driver and 3D acceleration is working.

---

### Post by migrainepill on 2016-11-05
> **Temüjin said:**
> That does not make sense. The Intel drivers are open source (Intel doesn't make closed source Linux drivers). Simple glxinfo will tell you:
```
glxinfo | grep string
```
If you see something like:
```

OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile
```
..then you have the correct driver and 3D acceleration is working.

After posting the details of the game settings this is what they responded me:

> [COLOR=#333333][FONT=Arial]I see that you're using the default open source drivers, which may be the only thing available for your graphic card. However, you may want to check on Intel's website and see if there is a better driver available, something that supports OpenGL 4.0 or better.[/FONT][/COLOR]

Also I run the command you suggested and I got the same results as you did, so I'm not quite sure what this other person was talking about then...

---

### Post by Yellow Pasque on 2016-11-05
If it's a game that truly requires OpenGL 4.x support, then you are out of luck. Your GPU hardware only supports OpenGL 3.3: [https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Sixth_generation](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Sixth_generation)
Using a different driver is not going to magically allow OpenGL 4.x support.

---

### Post by migrainepill on 2016-11-06
> **Temüjin said:**
> If it's a game that truly requires OpenGL 4.x support, then you are out of luck. Your GPU hardware only supports OpenGL 3.3: [https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Sixth_generation](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units#Sixth_generation)
Using a different driver is not going to magically allow OpenGL 4.x support.

I was using the same game in Windows 8.1 and I never had this problem before. The textures and everything were just fine so I don't know what could have happened or what is causing the bug in Ubuntu, that's why I was trying to update the drivers, either way, thanks all for your time and help.

---

### Post by Yellow Pasque on 2016-11-06
> I was using the same game in Windows 8.1 and I never had this problem before. The textures and everything were just fine so I don't know what could have happened or what is causing the bug in Ubuntu, that's why I was trying to update the drivers

It's possible to update the drivers to more a recent version (you have to resolve your apt issues first though). Perhaps, you actually are experiencing a bug fixed in the latest mesa version.
It's not going to enable support for OpenGL 4.x though, so I'm confused why their tech support mentions it.

---

