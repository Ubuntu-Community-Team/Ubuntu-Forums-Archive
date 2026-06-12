---
title: "usb-ports on thunderbolt-3 docking station not working"
date: 2021-04-02
forum: Hardware
---

### Post by Florian_Hanisch on 2021-04-02
Dear Forum, 

I have recently bought an TB3 docking station (i-tec TB3TRIPLEDOCKPD) and trying to use it on kubuntu 20.04, running on a DELL XPS 15 9550.

The HDMI output of the dock worked out of the box but I have not been able to use the usb-ports. The TB3 dock itself is connected, authorized and trusted. I have updated the BIOS to the latest version and also set the security level within the BIOS TB3 setting to "no security". However, that also did not resolve the problem.

Here is the output of dmesg, showing some issue with the usb:

[FONT=monospace][COLOR=#18b218][  304.065071] [/COLOR][COLOR=#b26818]xhci_hcd 0000:0b:00.0[/COLOR][COLOR=#b21818]: Abort failed to stop command ring: -110[/COLOR]
[COLOR=#18b218][  304.065082] [/COLOR][COLOR=#b26818]xhci_hcd 0000:0b:00.0[/COLOR][COLOR=#b21818]: xHCI host controller not responding, assume dead[/COLOR]
[COLOR=#18b218][  304.065086] [/COLOR][COLOR=#b26818]xhci_hcd 0000:0b:00.0[/COLOR][COLOR=#b21818]: HC died; cleaning up[/COLOR]
[COLOR=#18b218][  304.065127] [/COLOR][COLOR=#b26818]xhci_hcd 0000:0b:00.0[/COLOR][COLOR=#b21818]: Error while assigning device slot ID[/COLOR]
[COLOR=#18b218][  304.065154] [/COLOR][COLOR=#b26818]xhci_hcd 0000:0b:00.0[/COLOR][COLOR=#b21818]: Max number of devices this xHCI host supports is 64.[/COLOR]
[COLOR=#18b218][  304.065157] [/COLOR][COLOR=#b26818]usb usb4-port2[/COLOR][COLOR=#b21818]: couldn't allocate usb_device[/COLOR]
[COLOR=#18b218][  304.065202] [/COLOR][COLOR=#b26818]xhci_hcd 0000:0b:00.0[/COLOR][COLOR=#b21818]: Error while assigning device slot ID[/COLOR]
[COLOR=#18b218][  304.065206] [/COLOR][COLOR=#b26818]xhci_hcd 0000:0b:00.0[/COLOR][COLOR=#b21818]: Max number of devices this xHCI host supports is 64.[/COLOR]
[COLOR=#18b218][  304.065208] [/COLOR][COLOR=#b26818]usb usb3-port2[/COLOR][COLOR=#b21818]: couldn't allocate usb_device[/COLOR]

The full dmesg output showing disconnection and reconnection of the dock is here:[/FONT] [ATTACH]288212[/ATTACH][FONT=monospace]

Thanks for any suggestions,

Florian
[/FONT]

---

