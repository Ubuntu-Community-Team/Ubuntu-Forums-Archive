---
title: "Compiz not working with VIA KM400/A"
date: 2008-09-19
forum: General Help
---

### Post by roger_1960 on 2008-09-19
Hi all

When I try to run compiz from the GUI I get the 

"Desktop effects could not be enabled", message.

When I try using terminal I get this:

roger@acer2laptop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

This is on a Acer 1353LC laptop with Hardy 8.04.1 (up to date) with openchrome driver installed ( not sure if its running - how do I check).

I have tried to run compiz-check, but it wont run.  In terminal I see it start to give output then it goes straight to the Ubuntu login screen before I can do anything!

This is the relevant bit of output from lshw
 *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8235 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: VT8378 [S3 UniChrome] Integrated Video
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=64 mingnt=2

This is the device section from xorg.conf

Section "Device"
	Identifier	"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Hoping that someone can help, I've spent several hours looking at the sticky info, google searches etc but seem to be going in circles.  If this will never work because of hardware, thats fine, but if it should work, does anyone know how to set it up?

---

### Post by northern lights on 2008-09-19
The Via/S3 Unichrome chipset and direct rendering under linux have been problematic for Lord knows how long.

If there is one, [https://help.ubuntu.com/community/UniChrome]("https://help.ubuntu.com/community/UniChrome") most likely yields a solution.

---

### Post by roger_1960 on 2008-09-19
Hi

Thanks for that, its useful to know.  At the moment the Ubuntu Unichrome site links to drivers on [www.viaarena.com](www.viaarena.com) (for my chipset!!) which should work with Gutsy.  They dont install under Hardy.  I live in hope that they will be updated one day and I can try again.  For now, unless I go back to Gutsy, no Compiz, no Stellarium.............unless anyone knows otherwise!

---

### Post by northern lights on 2008-09-19
If in Gutsy, the drivers work to the point where you get direct rendering, you should be able to run compiz.

Run```
glxinfo | grep rendering
```to check

---

