---
title: "USB's not working"
date: 2014-12-08
forum: Hardware
---

### Post by afrohippie82 on 2014-12-08
After installing ubuntu to an older desktop it will not recognize any usb devices thats plugged in any of the usb ports For example: usb external harddrive lights up and runs but doesn't show anything in files, wireless mouse with dungle lights up but is not recognize what can i do about this i've tried searching for drivers but get nothing.. I'm still new to linux and ubuntu but i have fell in love with it it any help is appreciated. oh fyi The Bios usb setting is enabled....

---

### Post by Reha_Andrew on 2014-12-09
Have you tried it in different pc, only then view can be given.

---

### Post by afrohippie82 on 2014-12-09
all the items work fine on windows and Lubuntu Machines just not on the Ubuntu machine 14.04 LTS

---

### Post by mörgæs on 2014-12-09
Have you tried 14.10? 
Does not have to be a real install, you can do it in a live boot.

---

### Post by afrohippie82 on 2014-12-11
just ran live boot 14.10 still no usb action any more ideas?

---

### Post by afrohippie82 on 2014-12-11
can anyone help me with this problem or direct me in the right direction

---

### Post by Yellow Pasque on 2014-12-12
First, update your PCI/USB id's:
```
sudo update-usbids
sudo update-pciids
```

Next, give output of commands:
```
sudo dmidecode -t system -t bios
lspci
dmesg | grep -i usb
```

Last, try connecting a USB device or two and looking at lsusb and dmesg:
```
lsusb
dmesg | tail -n 30
```

---

### Post by afrohippie82 on 2014-12-13
Thanks [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594") for your help. After running the comands this what i came back with.

when I tried to run **sudo update-pciiids** i got [COLOR=#ff0000](command not found)[/COLOR]

when t tried to run **lsusb** i got ([COLOR=#ff0000]unable to initialize libusb: -99[/COLOR])
here is the rest....


                        [COLOR=#0000ff](**sudo dmidecode -t system -t bios**)

 
 # dmidecode 2.12

 SMBIOS 2.4 present.

 
 
 Handle 0x0000, DMI type 0, 24 bytes

 BIOS Information

         Vendor: Phoenix Technologies, LTD

         Version:  3.08

         Release Date: 09/13/2005
         Address: 0xE0000
         Runtime Size: 128 kB
         ROM Size: 512 kB

         Characteristics:
                 ISA is supported
                 PCI is supported
                 PNP is supported
                 APM is supported
                 BIOS is upgradeable
                 BIOS shadowing is allowed

                 Boot from CD is supported

                 Selectable boot is supported

                 BIOS ROM is socketed

                 EDD is supported
                 5.25"/360 kB floppy services are supported (int 13h)
                 5.25"/1.2 MB floppy services are supported (int 13h)
                 3.5"/720 kB floppy services are supported (int 13h)
                 3.5"/2.88 MB floppy services are supported (int 13h)
                 Print screen service is supported (int 5h)
                 8042 keyboard services are supported (int 9h)

                 Serial services are supported (int 14h)

                 Printer services are supported (int 17h)

                 CGA/mono video services are supported (int 10h)

                 ACPI is supported
                 USB legacy is supported
                 AGP is supported
                 LS-120 boot is supported
                 ATAPI Zip drive boot is supported
                 BIOS boot specification is supported
                 Function key-initiated network boot is supported
                 Targeted content distribution is supported
         BIOS Revision: 3.8
 
 
 Handle 0x0001, DMI type 1, 27 bytes

 System Information

         Manufacturer: Compaq Presario 061

         Product Name: SR1611NX 

         Version: 0nx1411RE101AMBEM00

         Serial Number: 

         UUID: 80B57749-4CC0-1010-B16A-AFE9B81174ED

         Wake-up Type: Power Switch

         SKU Number:  

         Family:   
 
 
 Handle 0x2000, DMI type 0, 32 bytes
 BIOS Information
         Vendor: Not Specified
         Version: <BAD INDEX>
         Release Date: <BAD INDEX>
         ROM Size: 1600 kB
         Characteristics:
                 BIOS ROM is socketed
                 Boot from PC Card (PCMCIA) is supported
                 Print screen service is supported (int 5h)
                 Targeted content distribution is supported
         BIOS Revision: 4.4

         Firmware Revision: 4.7

 
 
 Handle 0x0027, DMI type 13, 22 bytes

 BIOS Language Information

         Language Description Format: Long

         Installable Languages: 3

                 n|US|iso8859-1

                 n|US|iso8859-1

                 r|CA|iso8859-1

         Currently Installed Language: n|US|iso8859-1
 
 
 Handle 0x0032, DMI type 32, 11 bytes
 System Boot Information
         Status: No errors detected
 [/COLOR]
 
 
 [COLOR=#daa520]
 **(lspci)**

 
 
 00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)

 00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
 00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller
 00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
 00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
 00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller
 00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 11)

 00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller
 00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
 00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge
 00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 02)
 00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
 00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
 00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
 00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
 01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480 [Radeon Xpress 200 Series]
 02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)

 02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)[/COLOR][COLOR=#00ff00]

 [/COLOR]
 
 **(dmesg | grep -i usb)**

 
 
 [    0.313832] usbcore: registered new interface driver usbfs

 [    0.313853] usbcore: registered new interface driver hub

 [    0.313868] usbcore: registered new device driver usb

 [    2.280264] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver

 [    2.280436] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
 [    2.280692] uhci_hcd: USB Universal Host Controller Interface driver
 
 
 [COLOR=#800080]**(dmesg | tail -n 30)**
 
 
 [ 8380.059419] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8434.062796] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8446.063617] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8494.066545] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8506.067304] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8656.076669] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8680.078171] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8728.081171] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

 [ 8740.081922] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8800.085667] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8830.087546] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8842.088296] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8854.089046] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8866.089808] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8914.092794] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 8926.093544] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9136.106672] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9148.107436] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9160.108182] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9400.123172] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9460.126918] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9766.146044] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9790.147544] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9802.148299] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9814.149045] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9826.149797] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9868.152431] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9886.153604] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [11146.232295] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [11180.592035] perf interrupt took too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 50000[/COLOR]

didnt see anything i plugged in on this. I hope this added info helps somone help me hopefully i can return the favor to someone eles when i learn more I love linux.

---

### Post by mörgæs on 2014-12-13
There was a typo in post #7. Fixed now.

If you add CODE tags to the terminal output it's easier to read.

---

### Post by afrohippie82 on 2014-12-13
what are code tags

---

### Post by afrohippie82 on 2014-12-13
ok i ran the commands again, they are color coded to help differentiate the command and results of each item. what do you guy think is going on im still not seeing a usb harddrive or mouse or anything they just light up and thats about it.  software? hardware? or both? idk thanks for the help in advance.

  	 	 	 	   [COLOR=#333333]**Command: (sudo update-usbids)**[/COLOR]
 [COLOR=#333333]--2014-12-13 17:46:31--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)[/COLOR]
 [COLOR=#333333]Resolving [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org](www.linux-usb.org))... 216.34.181.97[/COLOR]
 [COLOR=#333333]Connecting to [www.linux-usb.org](www.linux-usb.org) ([www.linux-usb.org)|216.34.181.97|:80](www.linux-usb.org)|216.34.181.97|:80)... connected.[/COLOR]
 [COLOR=#333333]HTTP request sent, awaiting response... 200 OK[/COLOR]
 [COLOR=#333333]Length: 536447 (524K) [text/plain][/COLOR]
 [COLOR=#333333]Saving to: &#8216;/var/lib/usbutils/usb.ids.new&#8217;[/COLOR]
 
 
 [COLOR=#333333]100%[======================================>] 536,447      298KB/s   in 1.8s   [/COLOR] 
 
 
 [COLOR=#333333]2014-12-13 17:46:33 (298 KB/s) - &#8216;/var/lib/usbutils/usb.ids.new&#8217; saved [536447/536447][/COLOR]
 
 
 [COLOR=#333333]Done.[/COLOR]
 
 
 [COLOR=#ff00cc] **Command: (sudo update-pciids)**[/COLOR]
 [COLOR=#ff00cc]Downloaded daily snapshot dated 2014-12-13 03:15:02[/COLOR]
 
 
 [COLOR=#336666]  **[COLOR=#006600]Command: [/COLOR][COLOR=#006600]([/COLOR][COLOR=#006600]sudo dmidecode -t system -t bios[/COLOR][COLOR=#006600])[/COLOR]**[/COLOR]
 [COLOR=#006600]# dmidecode 2.12[/COLOR]
 [COLOR=#006600]SMBIOS 2.4 present.[/COLOR]
 
 
 [COLOR=#006600]Handle 0x0000, DMI type 0, 24 bytes[/COLOR]
 [COLOR=#006600]BIOS Information[/COLOR]
 [COLOR=#006600]        Vendor: Phoenix Technologies, LTD[/COLOR]
 [COLOR=#006600]        Version:  3.08[/COLOR]
 [COLOR=#006600]        Release Date: 09/13/2005[/COLOR]
 [COLOR=#006600]        Address: 0xE0000[/COLOR]
 [COLOR=#006600]        Runtime Size: 128 kB[/COLOR]
 [COLOR=#006600]        ROM Size: 512 kB[/COLOR]
 [COLOR=#006600]        Characteristics:[/COLOR]
 [COLOR=#006600]                ISA is supported[/COLOR]
 [COLOR=#006600]                PCI is supported[/COLOR]
 [COLOR=#006600]                PNP is supported[/COLOR]
 [COLOR=#006600]                APM is supported[/COLOR]
 [COLOR=#006600]                BIOS is upgradeable[/COLOR]
 [COLOR=#006600]                BIOS shadowing is allowed[/COLOR]
 [COLOR=#006600]                Boot from CD is supported[/COLOR]
 [COLOR=#006600]                Selectable boot is supported[/COLOR]
 [COLOR=#006600]                BIOS ROM is socketed[/COLOR]
 [COLOR=#006600]                EDD is supported[/COLOR]
 [COLOR=#006600]                5.25"/360 kB floppy services are supported (int 13h)[/COLOR]
 [COLOR=#006600]                5.25"/1.2 MB floppy services are supported (int 13h)[/COLOR]
 [COLOR=#006600]                3.5"/720 kB floppy services are supported (int 13h)[/COLOR]
 [COLOR=#006600]                3.5"/2.88 MB floppy services are supported (int 13h)[/COLOR]
 [COLOR=#006600]                Print screen service is supported (int 5h)[/COLOR]
 [COLOR=#006600]                8042 keyboard services are supported (int 9h)[/COLOR]
 [COLOR=#006600]                Serial services are supported (int 14h)[/COLOR]
 [COLOR=#006600]                Printer services are supported (int 17h)[/COLOR]
 [COLOR=#006600]                CGA/mono video services are supported (int 10h)[/COLOR]
 [COLOR=#006600]                ACPI is supported[/COLOR]
 [COLOR=#006600]                USB legacy is supported[/COLOR]
 [COLOR=#006600]                AGP is supported[/COLOR]
 [COLOR=#006600]                LS-120 boot is supported[/COLOR]
 [COLOR=#006600]                ATAPI Zip drive boot is supported[/COLOR]
 [COLOR=#006600]                BIOS boot specification is supported[/COLOR]
 [COLOR=#006600]                Function key-initiated network boot is supported[/COLOR]
 [COLOR=#006600]                Targeted content distribution is supported[/COLOR]
 [COLOR=#006600]        BIOS Revision: 3.8[/COLOR]
 
 
 [COLOR=#006600]Handle 0x0001, DMI type 1, 27 bytes[/COLOR]
 [COLOR=#006600]System Information[/COLOR]
 [COLOR=#006600]        Manufacturer: Compaq Presario 061[/COLOR]
 [COLOR=#006600]        Product Name:  SR1611NX[/COLOR]
 [COLOR=#006600]        Version: 0nx1411RE101AMBEM00[/COLOR]
 [COLOR=#006600]        Serial Number: [/COLOR] 
 [COLOR=#006600]        UUID: 80B57749-4CC0-1010-B16A-AFE9B81174ED[/COLOR]
 [COLOR=#006600]        Wake-up Type: Power Switch[/COLOR]
 [COLOR=#006600]        SKU Number:  [/COLOR] 
 [COLOR=#006600]        Family:  [/COLOR] 
 
 
 [COLOR=#006600]Handle 0x2000, DMI type 0, 32 bytes[/COLOR]
 [COLOR=#006600]BIOS Information[/COLOR]
 [COLOR=#006600]        Vendor: Not Specified[/COLOR]
 [COLOR=#006600]        Version: <BAD INDEX>[/COLOR]
 [COLOR=#006600]        Release Date: <BAD INDEX>[/COLOR]
 [COLOR=#006600]        ROM Size: 1600 kB[/COLOR]
 [COLOR=#006600]        Characteristics:[/COLOR]
 [COLOR=#006600]                BIOS ROM is socketed[/COLOR]
 [COLOR=#006600]                Boot from PC Card (PCMCIA) is supported[/COLOR]
 [COLOR=#006600]                Print screen service is supported (int 5h)[/COLOR]
 [COLOR=#006600]                Targeted content distribution is supported[/COLOR]
 [COLOR=#006600]        BIOS Revision: 4.4[/COLOR]
 [COLOR=#006600]        Firmware Revision: 4.7[/COLOR]
 
 
 [COLOR=#006600]Handle 0x0027, DMI type 13, 22 bytes[/COLOR]
 [COLOR=#006600]BIOS Language Information[/COLOR]
 [COLOR=#006600]        Language Description Format: Long[/COLOR]
 [COLOR=#006600]        Installable Languages: 3[/COLOR]
 [COLOR=#006600]                n|US|iso8859-1[/COLOR]
 [COLOR=#006600]                n|US|iso8859-1[/COLOR]
 [COLOR=#006600]                r|CA|iso8859-1[/COLOR]
 [COLOR=#006600]        Currently Installed Language: n|US|iso8859-1[/COLOR]
 
 
 [COLOR=#006600]Handle 0x0032, DMI type 32, 11 bytes[/COLOR]
 [COLOR=#006600]System Boot Information[/COLOR]
 [COLOR=#006600]        Status: No errors detected[/COLOR]
 
 
 [COLOR=#cc9900]**Command:  (lspci)**[/COLOR]
 [COLOR=#cc9900]00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)[/COLOR]
 [COLOR=#cc9900]00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx][/COLOR]
 [COLOR=#cc9900]00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller[/COLOR]
 [COLOR=#cc9900]00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller[/COLOR]
 [COLOR=#cc9900]00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller[/COLOR]
 [COLOR=#cc9900]00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller[/COLOR]
 [COLOR=#cc9900]00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 11)[/COLOR]
 [COLOR=#cc9900]00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller[/COLOR]
 [COLOR=#cc9900]00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge[/COLOR]
 [COLOR=#cc9900]00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge[/COLOR]
 [COLOR=#cc9900]00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 02)[/COLOR]
 [COLOR=#cc9900]00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/COLOR]
 [COLOR=#cc9900]00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map[/COLOR]
 [COLOR=#cc9900]00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller[/COLOR]
 [COLOR=#cc9900]00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/COLOR]
 [COLOR=#cc9900]01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480 [Radeon Xpress 200 Series][/COLOR]
 [COLOR=#cc9900]02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)[/COLOR]
 [COLOR=#cc9900]02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)[/COLOR]
 
 
 [COLOR=#000000] **Command: (dmesg | grep -i usb)**[/COLOR]
 [COLOR=#000000][    0.313832] usbcore: registered new interface driver usbfs[/COLOR]
 [COLOR=#000000][    0.313853] usbcore: registered new interface driver hub[/COLOR]
 [COLOR=#000000][    0.313868] usbcore: registered new device driver usb[/COLOR]
 [COLOR=#000000][    2.280264] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver[/COLOR]
 [COLOR=#000000][    2.280436] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver[/COLOR]
 [COLOR=#000000][    2.280692] uhci_hcd: USB Universal Host Controller Interface driver[/COLOR]
 
 
 [COLOR=#ff3333]**Command:  (lsusb)**[/COLOR]
 [COLOR=#ff3333]unable to initialize libusb: -99[/COLOR]
 
 
 [COLOR=#0000cc]**Command: (dmesg | tail -n 30)**[/COLOR]
 [COLOR=#0000cc][ 9766.146044] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][ 9790.147544] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][ 9802.148299] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][ 9814.149045] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][ 9826.149797] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][ 9868.152431] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][ 9886.153604] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][11146.232295] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][11180.592035] perf interrupt took too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 50000[/COLOR]
 [COLOR=#0000cc][12982.347067] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][12994.347824] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][13546.382295] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][13726.394249] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][13948.407429] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][14056.414171] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][14068.414924] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][14764.238969] systemd-hostnamed[6570]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname![/COLOR]
 [COLOR=#0000cc][15154.482793] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][15436.500438] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][15886.528544] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16330.556295] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16342.557043] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16354.557794] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16366.558747] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16414.561546] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16426.562298] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16456.564170] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16474.565297] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16486.566045] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]
 [COLOR=#0000cc][16762.583318] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1[/COLOR]

---

### Post by sudodus on 2014-12-13
> **afrohippie82 said:**
> what are code tags

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

-o-

There is an easy way: Click on the red button '**Go Advanced**' below the editing window. Then you will get more tools above the new editing window. One of them is illustrated with a **#** icon.

Mark the text you want within code tags. Then click on the **#** icon, to get it within code tags. Click on the red button **'Preview Post**' too see the processed result and finally '**Submit Reply**'

---

### Post by afrohippie82 on 2014-12-13
```
[COLOR=#333333]**sudo update-usbids**[/COLOR]
 [COLOR=#333333]--2014-12-13 17:46:31--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)[/COLOR]
 [COLOR=#333333]Resolving [www.linux-usb.org]("http://www.linux-usb.org") ([www.linux-usb.org]("http://www.linux-usb.org"))... 216.34.181.97[/COLOR]
 [COLOR=#333333]Connecting to [www.linux-usb.org]("http://www.linux-usb.org") ([www.linux-usb.org)|216.34.181.97|:80]("http://www.linux-usb.org%29%7C216.34.181.97%7C:80")... connected.[/COLOR]
 [COLOR=#333333]HTTP request sent, awaiting response... 200 OK[/COLOR]
 [COLOR=#333333]Length: 536447 (524K) [text/plain][/COLOR]
 [COLOR=#333333]Saving to: ‘/var/lib/usbutils/usb.ids.new’[/COLOR]
 
 
 [COLOR=#333333]100%[======================================>] 536,447      298KB/s   in 1.8s   [/COLOR] 
 
 
 [COLOR=#333333]2014-12-13 17:46:33 (298 KB/s) - ‘/var/lib/usbutils/usb.ids.new’ saved [536447/536447][/COLOR]
 
 
 [COLOR=#333333]Done.[/COLOR]
```

```
**sudo update-pciids**
 Downloaded daily snapshot dated 2014-12-13 03:15:02
```

  ```
**sudo dmidecode -t system -t bios**
 # dmidecode 2.12
 SMBIOS 2.4 present.
 
 
 Handle 0x0000, DMI type 0, 24 bytes
 BIOS Information
         Vendor: Phoenix Technologies, LTD
         Version:  3.08
         Release Date: 09/13/2005
         Address: 0xE0000
         Runtime Size: 128 kB
         ROM Size: 512 kB
         Characteristics:
                 ISA is supported
                 PCI is supported
                 PNP is supported
                 APM is supported
                 BIOS is upgradeable
                 BIOS shadowing is allowed
                 Boot from CD is supported
                 Selectable boot is supported
                 BIOS ROM is socketed
                 EDD is supported
                 5.25"/360 kB floppy services are supported (int 13h)
                 5.25"/1.2 MB floppy services are supported (int 13h)
                 3.5"/720 kB floppy services are supported (int 13h)
                 3.5"/2.88 MB floppy services are supported (int 13h)
                 Print screen service is supported (int 5h)
                 8042 keyboard services are supported (int 9h)
                 Serial services are supported (int 14h)
                 Printer services are supported (int 17h)
                 CGA/mono video services are supported (int 10h)
                 ACPI is supported
                 USB legacy is supported
                 AGP is supported
                 LS-120 boot is supported
                 ATAPI Zip drive boot is supported
                 BIOS boot specification is supported
                 Function key-initiated network boot is supported
                 Targeted content distribution is supported
         BIOS Revision: 3.8
 
 
 Handle 0x0001, DMI type 1, 27 bytes
 System Information
         Manufacturer: Compaq Presario 061
         Product Name:  SR1611NX
         Version: 0nx1411RE101AMBEM00
         Serial Number:  
         UUID: 80B57749-4CC0-1010-B16A-AFE9B81174ED
         Wake-up Type: Power Switch
         SKU Number:   
         Family:   
 
 
 Handle 0x2000, DMI type 0, 32 bytes
 BIOS Information
         Vendor: Not Specified
         Version: <BAD INDEX>
         Release Date: <BAD INDEX>
         ROM Size: 1600 kB
         Characteristics:
                 BIOS ROM is socketed
                 Boot from PC Card (PCMCIA) is supported
                 Print screen service is supported (int 5h)
                 Targeted content distribution is supported
         BIOS Revision: 4.4
         Firmware Revision: 4.7
 
 
 Handle 0x0027, DMI type 13, 22 bytes
 BIOS Language Information
         Language Description Format: Long
         Installable Languages: 3
                 n|US|iso8859-1
                 n|US|iso8859-1
                 r|CA|iso8859-1
         Currently Installed Language: n|US|iso8859-1
 
 
 Handle 0x0032, DMI type 32, 11 bytes
 System Boot Information
         Status: No errors detected
```

```
**(lspci)**
 00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)
 00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
 00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller
 00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
 00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
 00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller
 00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 11)
 00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller
 00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
 00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge
 00:14.5 Multimedia audio controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB400 AC'97 Audio Controller (rev 02)
 00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
 00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
 00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
 00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
 01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS480 [Radeon Xpress 200 Series]
 02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
 02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
```
```

[COLOR=#000000]**dmesg | grep -i usb**[/COLOR]
 [COLOR=#000000][    0.313832] usbcore: registered new interface driver usbfs[/COLOR]
 [COLOR=#000000][    0.313853] usbcore: registered new interface driver hub[/COLOR]
 [COLOR=#000000][    0.313868] usbcore: registered new device driver usb[/COLOR]
 [COLOR=#000000][    2.280264] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver[/COLOR]
 [COLOR=#000000][    2.280436] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver[/COLOR]
 [COLOR=#000000][    2.280692] uhci_hcd: USB Universal Host Controller Interface driver[/COLOR]
```

```

**lsusb**
 unable to initialize libusb: -99
```

```
**dmesg | tail -n 30**
 [ 9766.146044] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9790.147544] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9802.148299] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9814.149045] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9826.149797] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9868.152431] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [ 9886.153604] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [11146.232295] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [11180.592035] perf interrupt took too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
 [12982.347067] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [12994.347824] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [13546.382295] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [13726.394249] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [13948.407429] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [14056.414171] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [14068.414924] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [14764.238969] systemd-hostnamed[6570]: Warning:  nss-myhostname is not installed. Changing the local hostname might make  it unresolveable. Please install nss-myhostname!
 [15154.482793] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [15436.500438] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [15886.528544] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16330.556295] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16342.557043] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16354.557794] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16366.558747] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16414.561546] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16426.562298] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16456.564170] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16474.565297] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16486.566045] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
 [16762.583318] 8139too 0000:02:03.0 eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```

thanks sudodus

---

### Post by sudodus on 2014-12-13
You are welcome :-)

Let us wait for [**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594"), who asked for the output of those commands, to analyze the results.

---

### Post by afrohippie82 on 2014-12-13
Cool beans [**[COLOR=#C61919][B]sudodus **[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021")!

---

### Post by afrohippie82 on 2014-12-19
I now have usb's that work I simply went out and bought a multi port usb 2.0 pci card with 5 ports and problem solved. Cost less than 10 dollars. I will be upgrading to usb 3.0 soon....

---

### Post by sudodus on 2014-12-19
I'm glad you found a solution :-)

USB3 will probably work to connect drives for file transfer, but it might be harder to boot from (when not a built-in USB 3 system) compared to a USB 2 system. It can be the same problem with USB3 hubs.

---

### Post by Yellow Pasque on 2014-12-19
Sorry I did not read this sooner. It seems odd that the correct kernel modules load, but lsusb doesn't work. I would suspect a hardware issue, but you said that the ports works on Windows.

```
unable to initialize libusb: -99
```

---

