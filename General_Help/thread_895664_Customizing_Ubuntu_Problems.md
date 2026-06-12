---
title: "Customizing Ubuntu Problems"
date: 2008-08-20
forum: General Help
---

### Post by swappo1 on 2008-08-20
Hello,

I am trying to customize my desktop using the following guide:

[http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)

I have installed GTK 2.x from gnome-look.org.  I set the opacity value to 90 in the opacity settings in the CompizConfig Settings Manager as in the tutorial.  When I click on a menu it is not transparent.  Not sure what the problem is.

I also have another problem.  when I click on appearance preferences and try to change the visual effects to Extra, I get a message saying The composite extension is not available.  At that point the Visual Effects box just freezes and I can't even close it.  I have Compiz Advanced Desktop Effects Settings installed.

I am using Ubuntu 8.04 and need help customizing my desktop.  Thanks for any help.

---

### Post by Genius314 on 2008-08-20
You don't have to enable "Extra" animations. You can just activate the features you want using CCSM.

To make menus transparent, in CCSM, go to General Options, and click on the Opacity tab.
Click "New" and type in the box:
> (type=Menu | PopupMenu | DropdownMenu)
And set the opacity to about 90. This will make menus a little bit transparent. You can also add "Tooltip" to that if you want.

---

### Post by swappo1 on 2008-08-20
OK, I added the text as you specified and I am still not getting any transparency on my drop down lists.  After entering the info, is there an OK or done button that I have to click for the changes to take effect?  Sorry if I was unclear on my post, but the Appearance Preferance was a second unrelated question.  I edited the post for clarity.  Thanks for the help

---

### Post by Kevbert on 2008-08-20
What is your display card ? Also go to Applications-Accessories-Terminal and enter the following command:
```
lspci
```
Please post the output here.

---

### Post by swappo1 on 2008-08-20
Here is the result of lspci
```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by Kevbert on 2008-08-22
Try running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check"), that may help.

---

