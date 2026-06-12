---
title: "Dell Inspiron 6400 - Wifi, ATI Radeon x1400, XGL/Beryl"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by dbott67 on 2006-10-10
[SIZE="4"]**_Feb. 12/07 Update: Edgy Instructions_**[/SIZE]
*(the original Dapper instructions are below)*

_**ATI Driver Installation**_

I did a fresh install of Edgy and ran into issues with Mesa after installing the ATI proprietary drivers as per my original instructions below.  After following **escape's** *HOWTO Fix the MESA Issue *, I still could not get the ATI drivers to load.  After a little searching, I found the answer:

[COLOR="Red"]***Edgy uses Xorg 7.x which has compositing enabled by default.  The ATI drivers (fglrx) will not load while compositing is enabled; in fact, you must explicitly DISABLE it. ***[/COLOR] 
There is excellent documentation on installing ATI drivers in Edgy here: 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I used the "Ubuntu Way" (as opposed to the "Manual Way" / compiling from source)

After adding the following code to end of my **/etc/X11/xorg.conf** file, everything worked:
```

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

_**Beryl Installation**_

Excellect documentation here:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

I had some troubles with Beryl crashing after installing from Beryl's main Ubuntu repository ( deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main ).  After Googling the error message, I found a suggestion to try using the latest SVN repositories (deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn ) and everything works although my theme was messed up and I was missing my **Shutdown & Restart** buttons.

The installation instructions contain some "alternative" methods to start XGL and after modifying my /usr/local/bin/startxgl.sh script to the following, everything works perfectly:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

**_Broadcom 4311 Wireless:_**

I was able to get the wireless card working, however, I needed to blacklist the existing bcm43xx module and use ndiswrapper:

1. Install **build-essential** from Synaptic (for compiling ndiswrapper)

2. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

3. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

4.  Blacklist the bcm43xx module:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

5.  In order to get 'iwlist scanning' to display results, I needed to edit my /etc/network/interfaces file to contain the appropriate settings for my AP:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
[COLOR="Red"]wireless-essid MYSSID
wireless-key s:mysecretwepkey
[/COLOR]
auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

I'm not sure why my wireless card is now using eth1 (it used to be wlan0 in Dapper), but hey, it's working! :)

```
dbott@edgy:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:45
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

[COLOR="Red"]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

**_February 24, 2007 - Wireless Update_**

Regarding the eth1 issue, I believe it was related to an entry in my iftab file that contained the following line:
```
eth1 mac 00:16:ce:31:88:XX arp 1 
```

I changed the file to read:
```
dbott@edgy:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:0c:ad:XX arp 1
[COLOR="Red"]wlan0[/COLOR] mac 00:16:ce:31:88:XX arp 1

```

And then I installed **network-manager-gnome** and it seems to have cured all my problems.  The card is now recognized as **wlan0** and the network manager handles all the settings (WEP, scanning, etc.).

[SIZE="4"]**_Original Post (Oct. 10/06) - Dapper Instructions_**[/SIZE]

This is a bit of a HOW-TO on what I did to get my Dell Inspiron 6400 configured with Ubuntu 6.06.  All of the information has come from the work of others, notably: **djRobbieF** (XGL & Beryl installation), **escape** (Mesa issue) and countless others who contribute to these forums.

**_Specs:_**
- Dell Inspiron 6400
- Intel T2400 Core Duo (1.83 GHz)
- 2 GB RAM
- ATI Radeon x1400
- Broadcom wireless
- 8x DVD-RW
- Card reader

*[COLOR="Red"]Before starting, you may need to enable the additional repositories in Synaptic.[/COLOR]*

1. Install **686 SMP Kernel** from Synaptic (to enable both CPUs).  Do this first, as ndiswrapper is compiled against the kernel.

2. Install **build-essential** from Synaptic (for compiling ndiswrapper)

3. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

4. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

[COLOR="Red"]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

5. Download & install **ATI drivers** from [http://ati.amd.com/support/drivers/linux/linux-firegl.html](http://ati.amd.com/support/drivers/linux/linux-firegl.html)

After installing drivers & rebooting, run the following command:
```
fglrxinfo
```

You should get (or something similar):
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

6. If **Mesa** drivers still appear, follow this thread: [http://ubuntuforums.org/showthread.php?t=143283](http://ubuntuforums.org/showthread.php?t=143283) (Summarized below)
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

> **escape said:**
> **_The HOWTO Itself - Fixing MESA Issue_**

First, update your package database.
```
sudo apt-get update
```
Now, as mentioned in the original thread, remove the fglrx driver and restricted modules if you have them installed. If you're not sure, you can do these commands anyway; it will just tell you it's not installed.```
sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
```Your xorg file must also be set to be ati, not fglrx now, or else X won't start. To do this, open up /etc/X11/xorg.conf in your favorite text editor with root priveledges, in my case $>sudo emacs -nw /etc/X11/xorg.conf and under the section marked "Device", make sure you have Driver listed as "ati" and not "fglrx". 
Reboot.

Now, ***first install the restricted modules, then install the fglrx driver.*** It may also help to install other things related to fglrx; I also have xserver-xorg-driver-ati installed. fglrx-control is useful but not necessary (meaning I have fglrx working properly without fglrx-control installed).```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
```Go back into your text editor with /etc/X11/xorg.conf, and rechange Driver under "Device" from "ati" to "fglrx". 
Reboot.

Use fglrxinfo (or, if you're running Xgl with the gdm hack (ie running everything on screen 1 in stead of screen 0), do fglrxinfo -display :1.0) should now give something like```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5695 (8.23.7)
```Note: Don't worry about the "Generic" part. If this didn't work, before you go to troubleshooting, double check you have fglrx in Xorg and try  ```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```.



7. Install **Beryl & XGL** (summary of this thread: [http://www.ubuntuforums.org/showthread.php?t=268036](http://www.ubuntuforums.org/showthread.php?t=268036) with nVidia instructions removed for clarity)

Edit /etc/apt/sources.list (sudo gedit /etc/apt/sources.list) to include the following repositories:

```
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx
```

Install the packages:

```
sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
```

Edit the following file:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

and add the following lines just below the [servers] section:
```
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

8. Go to **System &#8211;> Preferences &#8211;> Sessions &#8211;> Startup Programs** and add the following two entries:
```
xmodmap -e "keycode 22 = BackSpace"
beryl-manager
```

9. Reboot.


**_Notes:_**

My Broadcom wi-fi is detected as:
```
dbott@dapperdrake:~$ lspci | grep Broadcom
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
```

I just used the drivers that came with the system.

The card reader now works (you can see it mounted in the 2nd screenshot behind the terminal window).  My original installation of Dapper back in June didn't enable it, but a recent re-install with updated kernel seems to have everything working.

---

### Post by rogosh55 on 2006-10-11
hey just wondering. i have the same laptop but i cant seem to get the wireless network card to work at all. are the driver posted on dell's website?

sorry im totally new to linux entirely. But i could use some help getting this setup if at all possible

thanks

---

### Post by dbott67 on 2006-10-11
Yes, the drivers are posted.  Note that there are a few [different wireless cards]("http://www1.ca.dell.com/content/learnmore/learnmore.aspx?c=ca&cs=19&l=en&ref=CFG&s=dhs&~id=dfamilywireless&~lt=popup&~series=inspn&~tab=details") offered by Dell for the 6400, so you'll need to know which drivers to download.  The 6400 comes in a number of different configurations (ATI vs. Intel GMA video, Solo vs. Duo Core, Broadcom vs. Centrino wifi, etc.) so make sure you have your specs handy.

Mine has the Broadcom chipset and I tried everything to get it going, but the only thing that worked was downloading & compiling the latest NDIS drivers from source.

Just following steps 1 through 4 above (also, Dell has different CPUs for the 6400, ranging from the Core Solo (1 CPU) up to the Core Duo (2 CPUs).  Step 1 above assumes you have the dual-core chip.  If you have the Solo chip, just use the 686 kernel (without SMP support).  

If you post your specs, it would help.  Below are the specs of my Dell 6400 as an example:
```
sudo lshw
```
```
dapper

    description: Portable Computer

    product: MM061

    vendor: Dell Inc.

    serial: B6WVQ91

    width: 32 bits

    capabilities: smbios-2.4 dmi-2.4

    configuration: boot=normal chassis=portable uuid=44454C4C-3600-1057-8056-C2C04F513931

  *-core

       description: Motherboard

       product: 0XD720

       vendor: Dell Inc.

       physical id: 0

       serial: .B6WVQ91.CN4864363G4975.

     *-firmware

          description: BIOS

          vendor: Dell Inc.

          physical id: 0

          version: A03 (03/09/2006)

          size: 64KB

          capacity: 512KB

          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot

     *-cpu:0

          description: CPU

          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz

          vendor: Intel Corp.

          physical id: 400

          bus info: cpu@0

          version: 6.14.8

          serial: 0000-06E8-0000-0000-0000-0000

          slot: Microprocessor

          size: 1GHz

          capacity: 1833MHz

          width: 32 bits

          clock: 133MHz

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr cpufreq

          configuration: id=0

        *-cache:0

             description: L1 cache

             physical id: 700

             size: 8KB

             capacity: 8KB

             capabilities: internal write-back data

        *-cache:1

             description: L2 cache

             physical id: 701

             size: 2MB

             capacity: 2MB

             clock: 66MHz (15ns)

             capabilities: pipeline-burst internal varies unified

        *-logicalcpu:0

             description: Logical CPU

             physical id: 0.1

             width: 32 bits

             capabilities: logical

        *-logicalcpu:1

             description: Logical CPU

             physical id: 0.2

             width: 32 bits

             capabilities: logical

     *-memory

          description: System Memory

          physical id: 1000

          slot: System board or motherboard

          size: 2GB

        *-bank:0

             description: DIMM DDR Synchronous 533 MHz (1.9 ns)

             vendor: AD00000000000000

             physical id: 0

             serial: 00004105

             slot: DIMM_A

             size: 1GB

             width: 64 bits

             clock: 533MHz (1.87617ns)

        *-bank:1

             description: DIMM DDR Synchronous 533 MHz (1.9 ns)

             vendor: AD00000000000000

             physical id: 1

             serial: 00006025

             slot: DIMM_B

             size: 1GB

             width: 64 bits

             clock: 533MHz (1.87617ns)

     *-cpu:1

          product: Genuine Intel(R) CPU           T2400  @ 1.83GHz

          vendor: Intel Corp.

          physical id: 1

          bus info: cpu@1

          version: 6.14.8

          serial: 0000-06E8-0000-0000-0000-0000

          size: 1GHz

          capacity: 1GHz

          width: 32 bits

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pni monitor vmx est tm2 xtpr cpufreq

          configuration: id=0

        *-logicalcpu:0

             description: Logical CPU

             physical id: 0.1

             width: 32 bits

             capabilities: logical

        *-logicalcpu:1

             description: Logical CPU

             physical id: 0.2

             width: 32 bits

             capabilities: logical

     *-pci

          description: Host bridge

          product: Mobile Memory Controller Hub

          vendor: Intel Corporation

          physical id: 100

          bus info: pci@00:00.0

          version: 03

          width: 32 bits

          clock: 33MHz

        *-pci:0

             description: PCI bridge

             product: Mobile PCI Express Graphics Port

             vendor: Intel Corporation

             physical id: 1

             bus info: pci@00:01.0

             version: 03

             width: 32 bits

             clock: 33MHz

             capabilities: pci normal_decode bus_master cap_list

             configuration: driver=pcieport-driver

           *-display

                description: VGA compatible controller

                product: ATI Technologies Inc

                vendor: ATI Technologies Inc

                physical id: 0

                bus info: pci@01:00.0

                version: 00

                size: 256MB

                width: 32 bits

                clock: 33MHz

                capabilities: vga bus_master cap_list

                configuration: driver=fglrx_pci

                resources: iomemory:c0000000-cfffffff ioport:ee00-eeff iomemory:dfdf0000-dfdfffff irq:169

        *-multimedia

             description: Multimedia controller

             product: 82801G (ICH7 Family) High Definition Audio Controller

             vendor: Intel Corporation

             physical id: 1b

             bus info: pci@00:1b.0

             version: 01

             width: 64 bits

             clock: 33MHz

             capabilities: bus_master cap_list

             configuration: driver=HDA Intel

             resources: iomemory:dfffc000-dfffffff irq:233

        *-pci:1

             description: PCI bridge

             product: 82801G (ICH7 Family) PCI Express Port 1

             vendor: Intel Corporation

             physical id: 1c

             bus info: pci@00:1c.0

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: pci normal_decode bus_master cap_list

             configuration: driver=pcieport-driver

           *-network

                description: Wireless interface

                product: Broadcom Corporation

                vendor: Broadcom Corporation

                physical id: 0

                bus info: pci@0b:00.0

                logical name: wlan0

                version: 01

                serial: 00:16:ce:31:88:6f

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list ethernet physical wireless

                configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b

                resources: iomemory:dfcfc000-dfcfffff irq:169

        *-pci:2

             description: PCI bridge

             product: 82801G (ICH7 Family) PCI Express Port 4

             vendor: Intel Corporation

             physical id: 1c.3

             bus info: pci@00:1c.3

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: pci normal_decode bus_master cap_list

             configuration: driver=pcieport-driver

        *-usb:0

             description: USB Controller

             product: 82801G (ICH7 Family) USB UHCI #1

             vendor: Intel Corporation

             physical id: 1d

             bus info: pci@00:1d.0

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: uhci bus_master

             configuration: driver=uhci_hcd

             resources: ioport:bf80-bf9f irq:225

           *-usbhost

                product: UHCI Host Controller

                vendor: Linux 2.6.15-27-686 uhci_hcd

                physical id: 1

                bus info: usb@2

                logical name: usb2

                version: 2.06

                capabilities: usb-1.10

                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

        *-usb:1

             description: USB Controller

             product: 82801G (ICH7 Family) USB UHCI #2

             vendor: Intel Corporation

             physical id: 1d.1

             bus info: pci@00:1d.1

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: uhci bus_master

             configuration: driver=uhci_hcd

             resources: ioport:bf60-bf7f irq:233

           *-usbhost

                product: UHCI Host Controller

                vendor: Linux 2.6.15-27-686 uhci_hcd

                physical id: 1

                bus info: usb@3

                logical name: usb3

                version: 2.06

                capabilities: usb-1.10

                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

              *-usb

                   description: Mouse

                   product: USB Mouse

                   vendor: Logitech

                   physical id: 1

                   bus info: usb@3:1

                   version: 6.10

                   capabilities: usb-1.10

                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s

        *-usb:2

             description: USB Controller

             product: 82801G (ICH7 Family) USB UHCI #3

             vendor: Intel Corporation

             physical id: 1d.2

             bus info: pci@00:1d.2

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: uhci bus_master

             configuration: driver=uhci_hcd

             resources: ioport:bf40-bf5f irq:50

           *-usbhost

                product: UHCI Host Controller

                vendor: Linux 2.6.15-27-686 uhci_hcd

                physical id: 1

                bus info: usb@4

                logical name: usb4

                version: 2.06

                capabilities: usb-1.10

                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

        *-usb:3

             description: USB Controller

             product: 82801G (ICH7 Family) USB UHCI #4

             vendor: Intel Corporation

             physical id: 1d.3

             bus info: pci@00:1d.3

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: uhci bus_master

             configuration: driver=uhci_hcd

             resources: ioport:bf20-bf3f irq:58

           *-usbhost

                product: UHCI Host Controller

                vendor: Linux 2.6.15-27-686 uhci_hcd

                physical id: 1

                bus info: usb@5

                logical name: usb5

                version: 2.06

                capabilities: usb-1.10

                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

        *-usb:4

             description: USB Controller

             product: 82801G (ICH7 Family) USB2 EHCI Controller

             vendor: Intel Corporation

             physical id: 1d.7

             bus info: pci@00:1d.7

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: ehci bus_master cap_list

             configuration: driver=ehci_hcd

             resources: iomemory:ffa80000-ffa803ff irq:225

           *-usbhost

                product: EHCI Host Controller

                vendor: Linux 2.6.15-27-686 ehci_hcd

                physical id: 1

                bus info: usb@1

                logical name: usb1

                version: 2.06

                capabilities: usb-2.00

                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s

        *-pci:3

             description: PCI bridge

             product: 82801 Mobile PCI Bridge

             vendor: Intel Corporation

             physical id: 1e

             bus info: pci@00:1e.0

             version: e1

             width: 32 bits

             clock: 33MHz

             capabilities: pci subtractive_decode bus_master cap_list

           *-network

                description: Ethernet interface

                product: BCM4401-B0 100Base-TX

                vendor: Broadcom Corporation

                physical id: 0

                bus info: pci@03:00.0

                logical name: eth0

                version: 02

                serial: 00:15:c5:0c:ad:05

                size: 10MB/s

                capacity: 100MB/s

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation

                configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s

                resources: iomemory:df9fe000-df9fffff irq:217

           *-firewire

                description: FireWire (IEEE 1394)

                product: Ricoh Co Ltd

                vendor: Ricoh Co Ltd

                physical id: 1

                bus info: pci@03:01.0

                version: 00

                width: 32 bits

                clock: 33MHz

                capabilities: ohci bus_master cap_list

                configuration: driver=ohci1394

                resources: iomemory:df9fd800-df9fdfff irq:177

           *-system:0

                description: Generic system peripheral

                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter

                vendor: Ricoh Co Ltd

                physical id: 1.1

                bus info: pci@03:01.1

                version: 19

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list

                configuration: driver=sdhci

                resources: iomemory:df9fd400-df9fd4ff irq:66

           *-system:1 UNCLAIMED

                description: System peripheral

                product: Ricoh Co Ltd

                vendor: Ricoh Co Ltd

                physical id: 1.2

                bus info: pci@03:01.2

                version: 01

                width: 32 bits

                clock: 33MHz

                capabilities: bus_master cap_list

                resources: iomemory:df9fd500-df9fd5ff irq:9

           *-system:2 UNCLAIMED

                description: System peripheral

                product: R5C592 Memory Stick Bus Host Adapter

                vendor: Ricoh Co Ltd

                physical id: 1.3

                bus info: pci@03:01.3

                version: 0a

                width: 32 bits

                clock: 33MHz

                capabilities: cap_list

                resources: iomemory:df9fd600-df9fd6ff irq:9

           *-system:3 UNCLAIMED

                description: System peripheral

                product: xD-Picture Card Controller

                vendor: Ricoh Co Ltd

                physical id: 1.4

                bus info: pci@03:01.4

                version: 05

                width: 32 bits

                clock: 33MHz

                capabilities: cap_list

                resources: iomemory:df9fd700-df9fd7ff irq:9

        *-isa UNCLAIMED

             description: ISA bridge

             product: 82801GBM (ICH7-M) LPC Interface Bridge

             vendor: Intel Corporation

             physical id: 1f

             bus info: pci@00:1f.0

             version: 01

             width: 32 bits

             clock: 33MHz

             capabilities: isa bus_master cap_list

        *-ide

             description: IDE interface

             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE

             vendor: Intel Corporation

             physical id: 1f.2

             bus info: pci@00:1f.2

             logical name: scsi0

             logical name: scsi1

             version: 01

             width: 32 bits

             clock: 66MHz

             capabilities: ide bus_master cap_list emulated scsi-host

             configuration: driver=ata_piix

             resources: ioport:bfa0-bfaf irq:217

           *-disk

                description: SCSI Disk

                product: FUJITSU MHV2100B

                vendor: ATA

                physical id: 0

                bus info: scsi@0:0.0.0

                logical name: /dev/sda

                version: 0085

                serial: NW08T6326PB6

                size: 91GB

                capabilities: partitioned partitioned:dos

                configuration: ansiversion=5

              *-volume:0

                   description: Dell Utility partition

                   physical id: 1

                   bus info: scsi@0:0.0.0,1

                   logical name: /dev/sda1

                   capacity: 47MB

                   capabilities: primary

              *-volume:1

                   description: HPFS/NTFS partition

                   physical id: 2

                   bus info: scsi@0:0.0.0,2

                   logical name: /dev/sda2

                   capacity: 19GB

                   capabilities: primary bootable

              *-volume:2

                   description: W95 Ext'd (LBA) partition

                   physical id: 3

                   bus info: scsi@0:0.0.0,3

                   logical name: /dev/sda3

                   capacity: 54GB

                   capabilities: primary

           *-cdrom

                description: DVD writer

                product: DVD+-RW DW-Q58A

                vendor: SONY

                physical id: 1

                bus info: scsi@1:0.0.0

                logical name: /dev/cdrom

                logical name: /dev/dvd

                logical name: /dev/scd0

                logical name: /dev/sr0

                version: UDS1

                capabilities: removable audio cd-r cd-rw dvd dvd-r

                configuration: ansiversion=5

              *-disc

                   physical id: 0

                   logical name: /dev/cdrom

        *-serial UNCLAIMED

             description: SMBus

             product: 82801G (ICH7 Family) SMBus Controller

             vendor: Intel Corporation

             physical id: 1f.3

             bus info: pci@00:1f.3

             version: 01

             width: 32 bits

             clock: 33MHz

             resources: ioport:10c0-10df irq:5

  *-battery

       product: DELLUD26063

       vendor: Sanyo

       physical id: 1

       slot: Sys. Battery Bay

       capacity: 78000mWh

       configuration: voltage=11.1V
```


-Dave

Note: I generally recommend turning off WEP/WPA and other security mechanisms on the wireless access point while trying to get wireless going (it eliminates potential trouble spots).  Once you make the connection, then turn on the various security measures you take (one at a time) and try to re-connect your laptop.

---

### Post by rogosh55 on 2006-10-11
Hi thank you for the help

I have the dual core model, 2GB ram .. x1400 etc. 
I can get the smp kernel fine and the graphics drivers fine but the wireless has been very difficult

the wireless card is Dell 1390 wireless but anyhow here is what it spits out when i do lshw

Password:
dan-laptop
    description: Portable Computer
    product: MM061
    vendor: Dell Inc.
    serial: JXFSNB1
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=44454C4C-5800-1046-8053-CAC 04F4E4231
  *-core
       description: Motherboard
       product: 0XD720
       vendor: Dell Inc.
       physical id: 0
       serial: .JXFSNB1.CN486436822576.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A06 (06/09/2006)
          size: 64KB
          capacity: 512KB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect i nt13floppy720 int5printscreen int9keyboard int14serial int17printer int10video a cpi usb agp smartbattery biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: Microprocessor
          size: 800MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pn i monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KB
             capacity: 8KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 2MB
             capacity: 2MB
             clock: 66MHz (15ns)
             capabilities: pipeline-burst internal varies unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: AD00000000000000
             physical id: 0
             serial: 00007174
             slot: DIMM_B
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.87617ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: AD00000000000000
             physical id: 1
             serial: 04008175
             slot: DIMM_A
             size: 1GB
             width: 64 bits
             clock: 533MHz (1.87617ns)
     *-cpu:1
          product: Genuine Intel(R) CPU           T2050  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic  sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pn i monitor est tm2 xtpr cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@01:00.0
                version: 00
                size: 256MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:c0000000-cfffffff ioport:ee00-eeff iomemory: dfdf0000-dfdfffff irq:4
        *-multimedia
             description: Multimedia controller
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:dfffc000-dfffffff irq:233
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0b:00.0
                logical name: wlan0
                version: 01
                serial: 00:18:f3:2d:25:e3
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper driverversion=1. 23 firmware=Broadcom,11/02/2005, 4.10.40.0 link=no multicast=yes wireless=IEEE 8 02.11g
                resources: iomemory:dfcfc000-dfcfffff irq:169
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@00:1c.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf80-bf9f irq:225
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf60-bf7f irq:233
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf40-bf5f irq:50
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Keyboard
                   product: Saitek Eclipse Keyboard
                   vendor: Chicony
                   physical id: 1
                   bus info: usb@3:1
                   version: 1.30
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:bf20-bf3f irq:58
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-27-686 uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: Microsoft 3-Button Mouse with IntelliEye(TM)
                   vendor: Microsoft
                   physical id: 1
                   bus info: usb@4:1
                   version: 3.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:ffa80000-ffa803ff irq:225
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.15-27-686 ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@03:00.0
                logical name: eth0
                version: 02
                serial: 00:15:c5:af:06:68
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10b t-fd 100bt 100bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=b44 drive rversion=0.97 duplex=full ip=192.168.0.107 link=yes multicast=yes port=twisted p air speed=100MB/s
                resources: iomemory:df9fe000-df9fffff irq:217
           *-firewire
                description: FireWire (IEEE 1394)
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@03:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:df9fd800-df9fdfff irq:177
           *-system:0
                description: Generic system peripheral
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@03:01.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:df9fd400-df9fd4ff irq:66
           *-system:1 UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@03:01.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:df9fd500-df9fd5ff irq:9
           *-system:2 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@03:01.3
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd600-df9fd6ff irq:9
           *-system:3 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.4
                bus info: pci@03:01.4
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:df9fd700-df9fd7ff irq:9
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix
             resources: ioport:bfa0-bfaf irq:217
           *-disk
                description: SCSI Disk
                product: Hitachi HTS72101
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MCZO
                serial: MPCZN2Y0GV24EH
                size: 91GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 9632MB
                   capabilities: primary bootable
              *-volume:1
                   description: W95 Ext'd (LBA) partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 77GB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 5373MB
                   capabilities: primary
           *-cdrom
                description: DVD writer
                product: DVD+-RW TS-L632D
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: DE03
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: ioport:10c0-10df irq:5
  *-battery
       product: DELLRD85068
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 78000mWh
       configuration: voltage=11.1V


This is directly after installing and following instructions in this thread (minus graphics because i know how to do that i just need to figure out the wireless):
[http://www.ubuntuforums.org/showthread.php?t=257684](http://www.ubuntuforums.org/showthread.php?t=257684) but now it pauses for about a minute during boot up and it says i have the wlan0 under System>Administration>Networking however it still doesnt work.

Any help would be greatly appreciated. Also im totally new to linux, this is my first week of trying to get this to work.

thanks again

---

### Post by dbott67 on 2006-10-11
It looks like ndiswrapper has loaded the driver.  Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw | grep Broadcom
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
                vendor: Broadcom Corporation
dbott@dapper:~$

```

Can you post the output of **ifconfig**:

```
dbott@dapper:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:05
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:672 (672.0 b)  TX bytes:672 (672.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:6F
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:44517036 (42.4 MiB)  TX bytes:2531971 (2.4 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000

dbott@dapper:~$

```

Using that, determine the name of your wireless interface (typically **wlan0**) and then run **iwlist wlan0 scanning**:

```
dbott@dapper:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:40:05:B2:AF:45
                    ESSID:"bott"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-35 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

dbott@dapper:~$

```

Now, post the output of **cat /etc/network/interfaces:**

```
dbott@dapper:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:secretWEPkey1
dbott@dapper:~$

```

With this information we can try to determine whether or not your card is activated & whether it can see the access point.

The other useful commands are **sudo ifdown wlan0** (deactivates wlan0), **sudo ifup wlan0** (activates wlan0), **sudo dhclient** (obtains IP address from DHCP server).
```
dbott@dapper:~$ sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:16:ce:31:88:6f
Sending on   LPF/wlan0/00:16:ce:31:88:6f
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67


dbott@dapper:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:16:ce:31:88:6f
Sending on   LPF/wlan0/00:16:ce:31:88:6f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 289375 seconds.


dbott@dapper:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:15:c5:0c:ad:05
Sending on   LPF/eth0/00:15:c5:0c:ad:05
Listening on LPF/wlan0/00:16:ce:31:88:6f
Sending on   LPF/wlan0/00:16:ce:31:88:6f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.105 -- renewal in 298048 seconds.
dbott@dapper:~$

```


Please enclose the output using the "code" tags **[ code ] Your output here [ /code ]**, as it makes it easier to read.

Thanks,
Dave

---

### Post by rogosh55 on 2006-10-11
sorry about that didnt know how to put it into code box

here is ipconfig

```
 dan@dan-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:AF:06:68
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feaf:668/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6367586 (6.0 MiB)  TX bytes:402539 (393.1 KiB)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:18:F3:2D:25:E3
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Memory:dfcfc000-dfd00000

dan@dan-laptop:~$


```

when i type in [B]iwlist wlan0 scanning
[/B] this is what comes out

```
 dan@dan-laptop:~$ iwlist wlan0 scanning
wlan0     No scan results 
```

and the others:

cat /etc/network/interfaces

```

dan@dan-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0
dan@dan-laptop:~$

```

sudo ifdown wlan0

```

dan@dan-laptop:~$ sudo ifdown wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:18:f3:2d:25:e3
Sending on   LPF/wlan0/00:18:f3:2d:25:e3
Sending on   Socket/fallback
dan@dan-laptop:~$

```

sudo ifup wlan0

```

dan@dan-laptop:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:18:f3:2d:25:e3
Sending on   LPF/wlan0/00:18:f3:2d:25:e3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
dan@dan-laptop:~$

```

and sudo dhclient

```

dan@dan-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:18:f3:2d:25:e3
Sending on   LPF/wlan0/00:18:f3:2d:25:e3
Listening on LPF/eth0/00:15:c5:af:06:68
Sending on   LPF/eth0/00:15:c5:af:06:68
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.107 -- renewal in 262831 seconds.
dan@dan-laptop:~$

```

does this info help?

thanks
Dan

---

### Post by dbott67 on 2006-10-12
Yes, it helps... we're getting close.  Can you post the output of the following command:

```
ndiswrapper -l
```
```
installed drivers:

bcmwl5		driver installed, hardware (14E4:4324) present (alternate driver: bcm43xx)
```

What kind of access point do you have?  Are you running WEP, WPA or any other encryption?  What about MAC filtering? Any or all of these can cause problems when trying to connect.  Generally, I recommend turing off all security settings while trying to troubleshoot --- then turn them back on one-at-a-time, re-connecting after each time.

Modify the last part of your **/etc/network/interfaces** file to read:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid your_AP_essid
wireless-key s:your_ASCII_wepkey
```

The "your_AP_essid" would be the ESSID of your access point & "your_ASCII_wepkey" is your WEP key.  For example, if your AP was broadcasting it's name as "rogosh55", and your ASCII WEP key was "secretWEPkey1", your **/etc/network/interfaces** should look like this:

```
sudo gedit /etc/network/interfaces
```
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]rogosh55[/COLOR]
wireless-key s:[COLOR="Red"]secretWEPkey1[/COLOR]
```

Then, reboot your computer or type the following from a command line:
```
sudo /etc/init.d/networking restart
```

You can also try the iwlist, ifup/ifdown & dhclient commands as noted previously.

Keep me posted.

-Dave

---

### Post by rogosh55 on 2006-10-12
hey i got this working now and im so happy about it.
after fooling around in the networking area with WEP and restarting network it worked 
thanks a lot for the help!
*side note* such a small world. i live in st. catharines aswell. 
dan

---

### Post by dbott67 on 2006-10-12
Glad to hear it!

Where in St. Catharines are you?

-Dave

---

### Post by rogosh55 on 2006-10-12
hey, actually i live just off Hartzel road. Fir avenue if u know the area.

Total bummer. I get my wireless working then I go try to install XGL/Beryl from your first post and now it crashes on boot. Gives me only text now. 

When i type beryl-manager i get GTK-WARNING **: cannot open display

been searching the forums for a solution but i havent run into anyone with the same problem yet. linux is hard.

Dan

---

### Post by dbott67 on 2006-10-12
I know the area... I'm in the north-end in Port Dalhousie.

My xwindows crashes, too... however, just type 'startx' after logging in at the command prompt & see what happens.  If you get into Gnome after that, open a terminal & type 'beryl-manager'.

As it stands, I have to do this each time I reboot.  I don't know why xwindows crashes, but it's a minor annoyance at this point.

-Dave

---

### Post by rogosh55 on 2006-10-12
ok that definitely got me back to the desktop. however beryl-manager doesnt work. it says XGL not installed then says looking for NVIDIA then says not installed and does nothing.

 I think i might just reinstall a fresh OS so that there is none of this startup stuff as it increases boot time a decent amount.
I might try again in the future but for now it seems like im just burnt out of trying to solve these problems. It has been like 4 days spending every spare moment to this.

But once again thank you for all your help. I really appreciate it.

DAn

---

### Post by dbott67 on 2006-10-12
That's good.

According to your lshw output, you have the same video card as me (an ATI Radeon x1400 with 256 MB RAM)... I don't know why it's looking for Nvidia.  When you recover from burn-out, try a re-install of Dapper (or Edgy in a couple of weeks) and try following the steps in my how-to in order.  Sometimes just installing things out of order can cause crazy things to happen.

-Dave

---

### Post by rogosh55 on 2006-10-13
yeah i was baffled when i saw that it was looking for nVidia
i also found some other guides for installing XGL/beryl for ATI cards so i might give those a try or something. i dunno maybe next week

---

### Post by neobonzi on 2006-11-05
i have a dell e1505 and followed your guide exactly with great results! Awesome guide. 

I'm having some trouble after i type xwin and get into gnome (mine crashes initially also). when i type beryl-manager i get the error "beryl-manager: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by beryl-manager)"

I have an x1400 grarphics card, dual core pentium, 1gig ram. Any ideas? very weird...

---

### Post by dbott67 on 2006-11-06
According to the Beryl site, Dapper Drake uses GLIBC 2.3, while Edgy Eft          uses GLIBC 2.4.  In my case, I am running Dapper and have not upgraded my version of Beryl since I installed it (v.0.1).

According to [this post]("http://forum.beryl-project.org/post-41812#p41812"), you need to upgrade to Edgy.  They don't recommend updating GLIBC 2.3 to 2.4 as it may break stuff in Dapper.

-Dave

---

### Post by davebed on 2006-11-08
Please see next post.

---

### Post by davebed on 2006-11-12
dbott67,

I've got the exact maching as yours and followed your instructions (thanks!).

One thing i can't get passed though - how to make use of DPMS with Beryl? 

Have you found a way to make use of 1.Screen blanking when lid closed and 2. Variable times for screen blanking while on AC or battery?

Please let me know if you've found a workaround as everything I've read so far suggests that XGL cannot support DPMS and all we're left with is to issue a manual command of **DISPLAY=:0 xset dpms 0** to blank the screen (not very automated or convenient).

Thanks.

---

### Post by manubh on 2006-11-16
Hi,

I have a Dell Inspiron with a similar configuration to yours. My question has more to do with the laptop itself than Ubuntu.

While installing Ubuntu, will the hidden Dell partitions be affected in any way? I mean, will MediaDirect work too? :-k 

Thanks,
Manu

---

### Post by davebed on 2006-11-16
Not sure - i mean it shouldn't get touched by anything, just that it's quite hidden and even not visible under windows as I understand. There is quite abit written about it around the web - i remember I looked into it, but mostly so i could reclaim the space (it's about 1.4GB i think).

In any case, always make sure you important data is backed up before any partitioning, but you should be OK.

Gook luck.

---

### Post by manubh on 2006-11-28
HI,

I finally installed Edgy. I installed the ATI drivers, but now my machine just locks up 30 odd seconds into the boot up.

Any idea what might be wrong?

Thanks in advance.

---

### Post by irober02 on 2007-01-11
Can you get a video signal out of the VGA port on your laptop?

I've a Dell Inspiron with the same ATI video card. Since I upgraded to Edgy my graphics are running well and I can watch videos and digital TV programs just fine.

However, I'd like to plug a video projector into the VGA port but it seems to be inactive. 

Any suggestions?

ian

---

### Post by dbott67 on 2007-01-14
[QUOTE=itstabish]Hey mate,

read your forum thread thank you for the help. however, im having a problem. my wlan card doesnt seem to be active. i duno why cuz in the bios its active and so in windows too but it doesnt show up in lwlist or whatever that command was. Any ideas?[/QUOTE]

We need to find out the make & model of your wireless card.  Can you post the output of the following commands:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

and 

```
lspci
```

```
dbott@dapper:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
?000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR="Red"]0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
[/COLOR]
```

-Dave

---

### Post by itstabish on 2007-01-14
0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

mine was exactly the same. I copied this off ur result but mine was exactly the same i remember it.

---

### Post by dbott67 on 2007-01-15
Hopefully, you can get online via wired ethernet (or maybe copy & paste the output to a text file & save it to USB/floppy and bring it over to a working computer).

Can you please post the output of the following commands:

```
cat /etc/network/interfaces
```

Here's mine as an example:

```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```


This command tries to detect wireless access points using each NIC:

```
iwlist scanning
```

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID</size:small?:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

-Dave

---

### Post by Mr_Congeniality on 2007-01-15
Can you help out with Ubuntu 6.10?

---

### Post by dbott67 on 2007-01-15
> **Mr_Congeniality said:**
> Can you help out with Ubuntu 6.10?

I'll try.  What's the problem?

---

### Post by Dr. Faustus on 2007-01-16
I have the 6400 as well.  I am very, very new to Linux and this whole thread has confused the hell out of me.   I'm reading it because I want to adjust the display and can't figure out how to do it.  It's like the picture is stretched wider than it should be.   I was trying to save money, so I think I have some on-board video card.  I can't even remember and I don't know how to find out in ubuntu. 


If you can help me alter the display for this screen I would be infinitely grateful.

---

### Post by dbott67 on 2007-01-16
Can you post the output of the following commands:
```

dbott@thedrake:~$ **sudo lshw -C video**
Password:
  *-display:0
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=fglrx_pci
       resources: iomemory:e0000000-efffffff ioport:d800-d8ff iomemory:bf800000-                                                                                                                     bf80ffff irq:217
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@01:00.1
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       resources: iomemory:c0000000-cfffffff iomemory:bf000000-bf00ffff

```

and your **xorg.conf **file

```
dbott@thedrake:~$ **cat /etc/X11/xorg.conf**

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
        Load "vnc"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "DELL 2007FP"
        VertRefresh  60.0 - 60.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        [COLOR="Red"]Driver      "fglrx"[/COLOR]
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
        Monitor    "DELL 2007FP"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
        Option "SecurityTypes" "VncAuth"
        Option "UserPasswdVerifier" "VncAuth"
        Option "PasswordFile" "/root/.vnc/passwd"
EndSection

Section "DRI"
        Mode         0666
EndSection

```

The values above are from my desktop computer, not my Dell 6400, so your values will definitely be different.  It's quite possible that you have the Intel GMA 950 video chipset or perhaps one of the ATI x1300/1400/1600 series cards.

Just post the output of the above 2 commands and we should be able to get you going.

-Dave

---

### Post by Dr. Faustus on 2007-01-16
Certainly.  I'd be happy to.   

```

*-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@00:02.0
       version: 03
       size: 256MB
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:dff00000-dff7ffff ioport:eff8-efff iomemory:c0000000-cfffffff iomemory:dfec0000-dfefffff irq:169
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@00:02.1
       version: 03
       size: 512KB
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:dff80000-dfffffff

```


For the first and for Xorg

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
# 
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
# 
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
# 
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
# 
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg
# 
# File edited by xorg-edit v07.01.12 at Tue Jan 16 01:57:14 2007

Section "Files"
        # path to defoma fonts
        FontPath "/usr/share/X11/fonts/misc"
        FontPath "/usr/share/X11/fonts/cyrillic"
        FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath "/usr/share/X11/fonts/Type1"
        FontPath "/usr/share/X11/fonts/100dpi"
        FontPath "/usr/share/X11/fonts/75dpi"
        FontPath "/usr/share/fonts/X11/misc"
        FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load "i2c"
        Load "bitmap"
        Load "ddc"
        Load "dri"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "type1"
        Load "vbe"
EndSection

Section "InputDevice"
        Identifier "Generic Keyboard"
        Driver "kbd"
        Option "CoreKeyboard"
        Option "XkbRules" "xorg"
        Option "XkbModel" "pc105"
        Option "XkbLayout" "us"
        Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "ZAxisMapping" "4 5"
        Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "true"
        Option "Device" "/dev/psaux"
        Option "Protocol" "auto-dev"
        Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
        # /dev/input/event
        # for USB
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/wacom" # Change to
        Option "Type" "stylus"
        Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
        # /dev/input/event
        # for USB
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/wacom" # Change to
        Option "Type" "eraser"
        Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
        # /dev/input/event
        # for USB
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/wacom" # Change to
        Option "Type" "cursor"
        Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
        Identifier "Intel Corporation Mobile Integrated Graphics Controller"
        Driver "i810"
        BusID "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier "Generic Monitor"
        DisplaySize 344 222
        Option "DPMS"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device "Intel Corporation Mobile Integrated Graphics Controller"
        Monitor "Generic Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 1
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth 4
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth 8
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth 15
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth 16
                Modes "1280x800"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Default Layout"
        Screen "Default Screen"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
        InputDevice "stylus" "SendCoreEvents"
        InputDevice "cursor" "SendCoreEvents"
        InputDevice "eraser" "SendCoreEvents"
        InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode 0666
EndSection

```



Thanks again.

---

### Post by dbott67 on 2007-01-17
You've got the Intel GMA 945 chipset and you'll need to install a program from the repositories called "915 resolution".

```
sudo apt-get install 915resolution
```

Check these 2 threads for more details:

[http://www.ubuntuforums.org/showthread.php?t=274398&highlight=intel+945](http://www.ubuntuforums.org/showthread.php?t=274398&highlight=intel+945)

[http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/](http://klepas.org/2006/04/09/ubuntu-on-the-inspiron-6400/)

-Dave

---

### Post by Dr. Faustus on 2007-01-17
The fix worked.  Many thanks.

---

### Post by itstabish on 2007-01-18
Dave, my cat/etc/ command doesnt seem to be working. for the second code, ifconfig, heres the result: 

> 
eth0      Link encap:Ethernet  HWaddr 00:15:C5:B4:85:A2  
          inet addr:199.212.79.99  Bcast:199.212.79.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feb4:85a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20078 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:167 txqueuelen:1000 
          RX bytes:3854800 (3.6 MiB)  TX bytes:522711 (510.4 KiB)
          Interrupt:217 

eth1      Link encap:Ethernet  HWaddr 00:16:CF:71:D6:91  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


for the scanning one, heres the result

> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.


---

### Post by itstabish on 2007-01-18
Oh btw, for the sudo thing, here's the result:

```

  *-network DISABLED      
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: eth1
       version: 01
       serial: 00:16:cf:71:d6:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:efcfc000-efcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:b4:85:a2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=half ip=199.212.79.99 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:ef9fe000-ef9fffff irq:217

```

---

### Post by dbott67 on 2007-01-18
> **itstabish said:**
> Dave, my cat/etc/ command doesnt seem to be working.

Sorry, my mistake. I've got a typo in my original post... there should be a *space* between **cat** and **/etc/network/interfaces**:

```
cat /etc/network/interfaces
```

-Dave

---

### Post by Loonux on 2007-01-18
Just wanted to say a quick thanks for the infol.
Have virtually an identical machine and been having problems with getting ATI?Beryl to play ball, so will work through your post tonight and see if i can fix it now!

---

### Post by itstabish on 2007-01-18
for the cat /etc/ thing:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

---

### Post by dbott67 on 2007-01-18
According to the information you've posted, you're wireless card is known as 'eth1' (this comes from the logical name in the output of sudo lshw -C network):
```
*-network **DISABLED**      
       [COLOR="Red"]description: Wireless interface[/COLOR]
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       [COLOR="Red"]logical name: eth1[/COLOR]
       version: 01
       serial: 00:16:cf:71:d6:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:efcfc000-efcfffff irq:169
```
It also indicates that it's disabled.

The **/etc/network/interfaces** file is generally responsible for activating network interfaces (although there are some newer network manager applications that manage the settings separately).  In your case, you are missing the commands that active your wireless card.

If you type the following commands at the command line, it should try to activate your wireless card:
```
sudo ifup eth1
```
If you're using WEP or other encryption on your AP, you may run into difficulties, but right now we just want to activate the card.

After issuing the above command, type:
```
iwlist scanning
```
and post the output here.  If the wireless card is active, you should see some APs listed.

-Dave

---

### Post by itstabish on 2007-01-18
```

tabish@tabish-laptop:~/Desktop/BitchX$ sudo ifup eth1
Password:
Ignoring unknown interface eth1=eth1.

```

```

tabish@tabish-laptop:~/Desktop/BitchX$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

```

Thanks for your help, btw. :)

---

### Post by itstabish on 2007-01-18
Hey man. theres a problem. my ubuntu went all haywire when i did what it said about XGL and Beryl. it starts up with a grey and white grid wit the ubuntu loading sign. then it blinks out and shows me like a typing prompt like DOS. then it does the same thing two times and it ends at that prompt. I dont know what happened. i just removed those lines that u asked to add and stuff and is back to normal. The Emerald Theme Manager and whatever are there on startup but i removed the lines too. help me out bro.

---

### Post by dbott67 on 2007-01-18
At the prompt, login using your regular user account and then type:
```
startx
```

-Dave

---

### Post by dbott67 on 2007-01-18
As for the wireless interface, try downloading & compiling the latest version of ndiswrapper as outlined in my first post (steps 1 through 4).  This is the only method that has worked for me for the Broadcom 4311 card.

-Dave

---

### Post by itstabish on 2007-01-18
btw, i edited my post back there please go and read. thank you sooo much.

---

### Post by Mr_Congeniality on 2007-01-19
> **dbott67 said:**
> I'll try.  What's the problem?

need a set of instructions for 6.10
should i just use this set instead?

---

### Post by dbott67 on 2007-01-19
I haven't tried 6.10 on my laptop yet... still running Dapper.  The only thing that you may have trouble with is Beryl.

-Dave

---

### Post by Mr_Congeniality on 2007-01-25
The link to the ATI support thing is dead.  What now?

---

### Post by dbott67 on 2007-01-25
> **Mr_Congeniality said:**
> The link to the ATI support thing is dead.  What now?

Try here:
[http://ati.amd.com/support/drivers/linux/linux-firegl.html](http://ati.amd.com/support/drivers/linux/linux-firegl.html)

-Dave

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

### Post by Pugwash on 2007-02-01
Dbott67, thanks very much for the guide. I found out I didn't have the ati graphics drivers, all sorted now. Now I can watch movies properly :D .

Cheers

---

### Post by HITMAN39 on 2007-02-03
Hello i have a similar laptop i have the e1705 with a core 2 duo 2.16 ati x1400 and a broacom wireless pren 1500 it is just like your and everyting else works besides wireless i did the ndiswrapper and under -l it shows up as installed but under ifconfig it isnt there can you help me please thanks

---

### Post by dbott67 on 2007-02-12
I have updated my original post to include instructions for Edgy:

[http://www.ubuntuforums.org/showthread.php?p=1601702#post1601702](http://www.ubuntuforums.org/showthread.php?p=1601702#post1601702)

-Dave

---

### Post by markdbd on 2007-02-12
dbott67 thanks for this great thread it helped me a lot to configure my new laptop, a inspiron 6400.

I got all installed and working on my Edgy but Beryl fails. I have followed the steps in Beryl Project Wiki:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

When I start Ubuntu with XGL session, the xgl crashes and don't know why.  I hope somebody can help me, thanks.

Ups, I forget I have a ATI Radeon Movility x1400.

---

### Post by dbott67 on 2007-02-12
I had some troubles with Beryl crashing after installing from Beryl's main Ubuntu repository ( deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main ). After Googling the error message, I found a suggestion to try using the latest SVN repositories (deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn ).

I followed the same instructions as you, however, where there were different options to choose from, these are the selections I made:

1. In Synaptic, I changed my Beryl repositories to:
```
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

2. Imported the gpg key:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add - 
```

3. Updated the Beryl packages:
```
sudo apt-get update
```

4. Installed the latest packages:
```
sudo apt-get install xserver-xgl
```
```
sudo apt-get install beryl emerald-themes
```

5. Re-boot

6. Before logging in, I selected the XGL session

7. After logging in, I opened a terminal window and typed:
```
beryl-manager
```

NOTES:

1. I did not modify my standard login
2. I did not add the Beryl session to startup
3. I did not add Beryl to existing session
4. I did modify the /usr/local/bin/startxgl.sh to:
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

**So, follow the instructions in the Wiki carefully, but use the same settings that I used.**

Hope this helps.

-Dave

---

### Post by markdbd on 2007-02-13
Thanks a lot dbott67, it worked perfect :) I thought it would not work with this ati, but you got it, great work, thanks :)

---

### Post by sacada on 2007-02-26
Hi,

I am a newby to Ubuntu, but I have been managed to install Beryl on a desktop and am now trying to install it on my Inspiron 6400.

I have followed a few different tutes but find that I still cannot get it to execute. When running beryl-manager from the terminal, I get the error...

> ****
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension



I have the lines in my /etc/X11/xorg.conf:

> 
Section "DRI"
        Mode 0666
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

I, at sometime think I may have installed the aiglx and now can't undo it. Thanks for any help.

---

