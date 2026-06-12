---
title: "[Solved] Ubuntu will not recognize the hardware on my HP-15-DY200"
date: 2021-08-11
forum: Hardware
---

### Post by conwayphelps on 2021-08-11
I just bought a new HP laptop, just off the line from China this month. When I try installing the 21.04 version it will not recognize the monitor, the keyboard, and the touchpad. I tried posting this in the AskUbuntu and I was directed here. Here is the information from HWiNFO relevant to this question. HWiNFO does not recognize the monitor listing it as only [FONT=inherit]"BOE [Unknown Model: BOE0780]" but the keyboard and mouse are listed as basic PS/2, so they should be recognized out of the box. [/FONT]This would seem to me that there is a problem with recognizing the motherboard, but I'm just not sure. I tried the live USB on earlier versions, what I checked was 19.10 and 20.10, and they worked fine, recognizing all the hardware, so something changed from 20.04 to 20.10 that made it so this is not recognized. I'm scratching my head.[FONT=inherit]

[/FONT]```
[Current Computer]
  Computer Brand Name:                    HP HP Laptop 15t-dy200
 [Operating System]

Central Processor(s) ------------------------------------------------------

 [CPU Unit Count]
  Number Of Processor Packages (Physical): 1
  Number Of Processor Cores:              4
  Number Of Logical Processors:           8

Intel Core i7-1165G7 ------------------------------------------------------

 [General Information]
  Processor Name:                         Intel Core i7-1165G7
  Original Processor Frequency:           2800.0 MHz
  Original Processor Frequency [MHz]:     2800
  CPU ID:                                 (deleted)
  CPU Brand Name:                         11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz
  CPU Vendor:                             GenuineIntel
  CPU Stepping:                           B1
  CPU Code Name:                          Tiger Lake-UP3
  CPU Technology:                         10 nm
  CPU S-Spec:                             SRK01, SRK02, SRK1D, SRK1E
  CPU Thermal Design Power (TDP):         28.0 W
  CPU Power Limits (Max):                 Power = Unlimited, Time = Unlimited
  CPU Power Limit 1 - Long Duration:       (18.75 W) (32.00 sec) [Unlocked]
  CPU Power Limit 2 - Short Duration:      (40.00 W) (2.44 ms) [Unlocked]
  Configurable TDP Level 1 (Down):        12.00 W (Unlimited range), 1200 MHz
  Configurable TDP Level 2 (Up):          15.00 W (Unlimited range), 1700 MHz
  Current Configurable TDP Level:         Nominal [Unlocked]
  CPU Max. Junction Temperature (Tj,max): 100 °C
  CPU Type:                               Production Unit
  CPU Platform:                           BGA1449
  Microcode Update Revision:              8A
  Number of CPU Cores:                    4
  Number of Logical CPUs:                 8

Motherboard ---------------------------------------------------------------

 [Computer]
  Computer Brand Name:                    HP HP Laptop 15t-dy200
 [Motherboard]
  Motherboard Model:                      HP 87FE
  Motherboard Chipset:                    Intel Tiger Lake-UP3 PCH-LP
  Motherboard Slots:                      1xPCI Express x16
  USB Version Supported:                  v3.1
 [BIOS]
  BIOS Manufacturer:                      AMI
  BIOS Date:                              07/22/2021
  BIOS Version:                           F.13
  UEFI BIOS:                              Capable
  Super-IO/LPC Chip:                      Unknown
  Trusted Platform Module (TPM) Chip:     Hardware TPM, version v2.0

ACPI Devices --------------------------------------------------------------

Standard PS/2 Keyboard ----------------------------------------------------

  Device Name:                            Standard PS/2 Keyboard
 [Assigned Resources]
  I/O Port:                               0060
  I/O Port:                               0000
 [Alternative 1]
  I/O Port:                               0060
  I/O Port:                               0064
  IRQ:                                    1

Intel(R) Serial IO GPIO Host Controller - INT34C5 -------------------------

  Device Name:                            Intel(R) Serial IO GPIO Host Controller - INT34C5
 [Assigned Resources]
  IRQ:                                    14
 [Alternative 1]
  Memory Location:                        FD6E0000
  Memory Location:                        FD6D0000
  Memory Location:                        FD6A0000
  Memory Location:                        FD690000
  IRQ:                                    14

Microsoft ACPI-Compliant Embedded Controller ------------------------------

  Device Name:                            Microsoft ACPI-Compliant Embedded Controller
 [Assigned Resources]
  I/O Port:                               0062
 [Alternative 1]
  I/O Port:                               0062
  I/O Port:                               0066

BIOS ----------------------------------------------------------------------

  BIOS Vendor:                            AMI
  BIOS Version:                           F.13
  BIOS Release Date:                      07/22/2021
  BIOS Start Segment:                     F000
  BIOS Size:                              8 MBytes
  System BIOS Version:                    15.13
  Embedded Controller Firmware Version:   57.18
  ISA Support:                            Not Present
  MCA Support:                            Not Present
  EISA Support:                           Not Present
  PCI Support:                            Present
  PC Card (PCMCIA) Support:               Not Present
  Plug-and-Play Support:                  Not Present
  APM Support:                            Not Present
  Flash BIOS:                             Present
  BIOS Shadow:                            Present
  VL-VESA Support:                        Not Present
  ESCD Support:                           Not Present
  Boot from CD:                           Present
  Selectable Boot:                        Present
  BIOS ROM Socketed:                      Not Present
  Boot from PC Card:                      Not Present
  EDD Support:                            Present
  NEC PC-98 Support:                      Not Present
  ACPI Support:                           Not Present
  USB Legacy Support:                     Not Present
  AGP Support:                            Not Present
  I2O Boot Support:                       Not Present
  LS-120 Boot Support:                    Not Present
  ATAPI ZIP Drive Boot Support:           Not Present
  IEE1394 Boot Support:                   Not Present
  Smart Battery Support:                  Present
  BIOS Boot Specification Support:        Present
  Function key-initiated Network Service Boot Support: Present
  Targeted Content Distribution Support:  Present
  UEFI Specification Support:             Present
  Virtual Machine:                        Not Present

System --------------------------------------------------------------------

  System Manufacturer:                    HP
  Product Name:                           HP Laptop 15t-dy200
  Product Version:                        
  Product Serial Number:                  (deleted)
  UUID:                                   {31444335-3033-4734-4B56-564730334435}
  SKU Number:                             2D117AV
  Family:                                 103C_5335KV HP Notebook

Mainboard -----------------------------------------------------------------

  Mainboard Manufacturer:                 HP
  Mainboard Name:                         87FE
  Mainboard Version:                      57.18
  Mainboard Serial Number:                (deleted)
  Asset Tag:                              Base Board Asset Tag
  Location in chassis:                    Base Board Chassis Location

System Enclosure ----------------------------------------------------------

  Manufacturer:                           HP
  Case Type:                              Notebook
  Version:                                Chassis Version
  Serial Number:                          (deleted)
  Asset Tag Number:                       

Management Device ---------------------------------------------------------

  Device Description:                     LM78-1
  Device Type:                            National Semiconductor LM78
  Device Address:                         I/O: 0


On Board Device -----------------------------------------------------------

  Device Description:                      Onboard IGD
  Device Type:                            Video Adapter
  Device Status:                          Enabled

Firmware Version Information ----------------------------------------------

  Reference Code - CPU                    10.0.42.50
  uCode Version                           0.0.0.138
  TXT ACM version                         1.14.8.0

Firmware Version Information ----------------------------------------------

  Reference Code - ME                     10.0.42.50
  MEBx version                            0.0.0.0
  ME Firmware Version                     Consumer SKU

Firmware Version Information ----------------------------------------------

  Reference Code - PCH                    10.0.42.50
  PCH-CRID Status                         Disabled
  PCH-CRID Original Value                 0x20
  PCH-CRID New Value                      0x20
  OPROM - RST - RAID                      2.70.0.0
  PCH Hsio Version                        4.0.0.0

Firmware Version Information ----------------------------------------------

  Reference Code - SA - System Agent      10.0.42.50
  Reference Code - MRC                    1.0.0.0
  SA - PCIe Version                       10.0.42.50
  SA-CRID Status                          Disabled
  SA-CRID Original Value                  0.0.0.1
  SA-CRID New Value                       0.0.0.1
  OPROM - VBIOS                           
  IO Manageability Engine FW Version      17.1.0.0
  PHY Build Version                       0.0.0.0
  Thunderbolt(TM) FW Version              0.0.0.0
  System Agent Manageability Engine FW Version 

Firmware Version Information ----------------------------------------------

  FSP Binary Version                      4.0.0.0

Processor -----------------------------------------------------------------

  Processor Manufacturer:                 Intel(R) Corporation
  Processor Version:                      11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz
  External Clock:                         100 MHz
  Maximum Clock Supported:                4700 MHz
  Current Clock:                          2800 MHz
  CPU Socket:                             Populated
  CPU Status:                             Enabled
  Processor Type:                         Central Processor
  Processor Voltage:                      0.8 V
  Processor Upgrade:                      Unknown (1)
  Socket Designation:                     U3E1

Intel vPro ----------------------------------------------------------------

  CPU VT-x Support:                       Supported
  CPU VT-x Status:                        Enabled
  CPU VT-x2 Support:                      Not Supported
  CPU VT-x2 Status:                       Disabled
  CPU TXT Support:                        Not Supported
  CPU TXT Status:                         Disabled
  CPU VMX Status:                         Enabled
  CPU SMX Status:                         Disabled
  Intel ME Status:                        Enabled
  Intel OST Firmware Support:             Not Supported
  Intel ASF Firmware Support:             Not Supported
  Intel AMT Pro Firmware Support:         Not Supported
  Intel AMT Basic Firmware Support:       Not Supported
  Intel TPM Firmware Support:             Not Supported
  Intel Castle Peak Support:              Not Supported
  Intel WoX Support:                      Not Supported
  Intel Virtualization Engine Support:    Not Supported
  Intel Anti-Theft Technology Support:    Not Supported
  TPM On-board:                           Not Supported
  Intel Anti-Theft Technology Enrolled:   Not Supported
  Intel ME Version:                       v15.0, Build 1776, Hotfix 30
  BIOS VT-x Support:                      Not Supported
  BIOS VT-d Support:                      Supported
  BIOS TXT Support:                       Not Supported
  BIOS TPM Support:                       Not Supported
  BIOS ME Support:                        Not Supported
  BIOS VA Extensions Support:             Supported
  Intel AT PBA For Recovery Support:      Not Supported
  Intel AT WWAN Support:                  Not Supported

On Board Device -----------------------------------------------------------

  Device Description:                     Intel Wi-Fi 6 AX201 + BT
  Device Type:                            Unknown
  Device Status:                          Enabled

Keyboard Port -------------------------------------------------------------

  Port Type:                              Keyboard Port
  Internal Reference:                     Keyboard
  Internal Connector Type:                None
  External Reference:                     Keyboard
  External Connector Type:                PS/2

Video Port ----------------------------------------------------------------

  Port Type:                              Video Port
  Internal Reference:                     HDMI
  Internal Connector Type:                None
  External Reference:                     HDMI
  External Connector Type:                None

Intel ME ------------------------------------------------------------------

 [ME Host Status]
  ME Current Working State:               Normal
  Manufacturing Mode:                     Not Active
  ME Current Operation Mode:              Normal
  Boot Guard Status:                      Enabled
  Boot Guard Verified Boot Policy:        Enabled
  Boot Guard Measured Boot Policy:        Enabled
 [Intel Manageability Engine Features]
  Intel ME Version:                       15.0, Build 1776, Hot Fix 30
  Intel ME Recovery Image Version:        15.0, Build 1776, Hot Fix 30
  Intel ME FITC Version:                  15.0, Build 1377, Hot Fix 2
 [ME Firmware Platform Type]
  Platform Target Usage Type:             Mobile
  SKU:                                    Regular SKU
  ME Firmware Image Type:                 Consumer SKU Firmware
  Platform Brand:                         None
  Host ME Region Flash Protection Override (HMRFPO) Status: Locked

Memory --------------------------------------------------------------------

 [General information]
  Total Memory Size:                      32 GBytes
  Total Memory Size [MB]:                 32768
 [Current Performance Settings]
  Maximum Supported Memory Clock:         1600.0 MHz
  Current Memory Clock:                   1562.7 MHz
  Current Timing (tCAS-tRCD-tRP-tRAS):    22-22-22-52
  Memory Channels Supported:              2
  Memory Channels Active:                 2
  Command Rate:                           2T
  Read to Read Delay (tRDRD_SG/TrdrdScL) Same Bank Group: 8T
  Read to Read Delay (tRDRD_DG/TrdrdScDlr) Different Bank Group: 4T
  Read to Read Delay (tRDRD_SD) Same DIMM: 8T
  Read to Read Delay (tRDRD_DD) Different DIMM: 8T
  Write to Write Delay (tWRWR_SG/TwrwrScL) Same Bank Group: 8T
  Write to Write Delay (tWRWR_DG/TwrwrScDlr) Different Bank Group: 4T
  Write to Write Delay (tWRWR_SD) Same DIMM: 10T
  Write to Write Delay (tWRWR_DD) Different DIMM: 10T
  Read to Write Delay (tRDWR_SG/TrdwrScL) Same Bank Group: 12T
  Read to Write Delay (tRDWR_DG/TrdwrScDlr) Different Bank Group: 12T
  Read to Write Delay (tRDWR_SD) Same DIMM: 12T
  Read to Write Delay (tRDWR_DD) Different DIMM: 12T
  Write to Read Delay (tWRRD_SG/TwrrdScL) Same Bank Group: 40T
  Write to Read Delay (tWRRD_DG/TwrrdScDlr) Different Bank Group: 30T
  Write to Read Delay (tWRRD_SD) Same DIMM: 6T
  Write to Read Delay (tWRRD_DD) Different DIMM: 6T
  RAS# to RAS# Delay (tRRD):              8T
  Row Cycle Time (tRC):                   74T
  Refresh Cycle Time (tRFC):              560T
  Four Activate Window (tFAW):            34T

Intel Tiger Lake-UP3 - GT2 Integrated Graphics ----------------------------

 [General Information]
  Device Name:                            Intel Tiger Lake-UP3 - GT2 Integrated Graphics
  Original Device Name:                   Intel Tiger Lake-UP3 - GT2 Integrated Graphics
  Device Class:                           VGA Compatible Adapter
  Revision ID:                            1
  PCI Address (Bus:Device:Function) Number: 0:2:0
  PCI Latency Timer:                      0
  Hardware ID:                            PCI\VEN_8086&DEV_9A49&SUBSYS_87FE103C&REV_01
 [PCI Express]
  Version:                                2.0
  Current Link Width:                     Not negotiated
  Maximum Link Speed:                     5.0 GT/s
  Device/Port Type:                       Root Complex Integrated Endpoint
  Slot Implemented:                       No
  Emergency Power Reduction:              Not Supported
  Active State Power Management (ASPM) Support: None
  Active State Power Management (ASPM) Status: Disabled
  L0s Exit Latency:                       < 64 ns
  L1 Exit Latency:                        < 1 us
  Maximum Payload Size Supported:         128 bytes
  Maximum Payload Size:                   128 bytes
  Resizable BAR Support:                  Not Supported
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          INTA#
  Memory Base Address 0                   6002000000
  Memory Base Address 2                   4000000000
  I/O Base Address 4                      3000
 [Features]
  Bus Mastering:                          Enabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable
 [Driver Information]
  Driver Manufacturer:                    Intel Corporation
  Driver Description:                     Intel(R) Iris(R) Xe Graphics
  Driver Provider:                        Intel Corporation
  Driver Version:                         30.0.100.9684
  Driver Date:                            08-Jul-2021
  DCH/UWD Driver:                         Not Capable
  DeviceInstanceId                        PCI\VEN_8086&DEV_9A49&SUBSYS_87FE103C&REV_01\3&11583659&2&10
  Location Paths                          PCIROOT(0)#PCI(0200)

Intel Tiger Lake - Gaussian Mixture Model (GNA) ---------------------------

 [General Information]
  Device Name:                            Intel Tiger Lake - Gaussian Mixture Model (GNA)
  Original Device Name:                   Intel Tiger Lake - Gaussian Mixture Model (GNA)
  Device Class:                           Unknown Peripheral Device
  Revision ID:                            1
  PCI Address (Bus:Device:Function) Number: 0:8:0
  PCI Latency Timer:                      0
  Hardware ID:                            PCI\VEN_8086&DEV_9A11&SUBSYS_87FE103C&REV_01
 [System Resources]
  Interrupt Line:                         N/A
  Interrupt Pin:                          INTA#
  Memory Base Address 0                   7FFFEF6000
 [Features]
  Bus Mastering:                          Disabled
  Running At 66 MHz:                      Not Capable
  Fast Back-to-Back Transactions:         Not Capable
 [Driver Information]
  Driver Manufacturer:                    Intel Corporation
  Driver Description:                     Intel(R) GNA Scoring Accelerator module
  Driver Provider:                        Intel Corporation
  Driver Version:                         2.0.0.1097
  Driver Date:                            29-Oct-2020
  DeviceInstanceId                        PCI\VEN_8086&DEV_9A11&SUBSYS_87FE103C&REV_01\3&11583659&2&40
  Location Paths                          PCIROOT(0)#PCI(0800)

Intel Iris Xe Graphics ----------------------------------------------------

 [Video chipset]
  Video Chipset:                          Intel Iris Xe Graphics
  Video Chipset Codename:                 Tiger Lake-UP3 GT2
  Video Memory:                           1024 MBytes of DDR4 
 [Video Card]
  Video Card:                             Intel Tiger Lake-UP3 - GT2 Integrated Graphics [Hewlett-Packard]
  Video Bus:                              Integrated
  Video RAMDAC:                           Internal
 [Performance]
  Graphics Processor Clock:               97.7 MHz
  Graphics Memory Clock:                  1562.0 MHz (Effective 3124.0 MHz)
  Graphics Memory Bus Width:              128-bit
  Number Of ALUs (cores):                 768
  Number Of EUs (Execution Units):        96
  Resizable BAR Support:                  Not Supported
  Hardware ID:                            PCI\VEN_8086&DEV_9A49&SUBSYS_87FE103C&REV_01
  PCI Location (Bus:Dev:Fnc):             0:02:0
 [Driver Information]
  Driver Manufacturer:                    Intel Corporation
  Driver Description:                     Intel(R) Iris(R) Xe Graphics
  Driver Provider:                        Intel Corporation
  Driver Version:                         30.0.100.9684
  Driver Date:                            08-Jul-2021
  DCH/UWD Driver:                         Not Capable
  DeviceInstanceId                        PCI\VEN_8086&DEV_9A49&SUBSYS_87FE103C&REV_01\3&11583659&2&10
  Location Paths                          PCIROOT(0)#PCI(0200)

Monitor -------------------------------------------------------------------

BOE [Unknown Model: BOE0780] ----------------------------------------------

 [General information]
  Monitor Name:                           BOE [Unknown Model: BOE0780]
  Serial Number:                          Unknown
  Date Of Manufacture:                    Week: 1, Year: 2017
  Monitor Hardware ID:                    Monitor\BOE0780
  Max. Vertical Size:                     19 cm
  Max. Horizontal Size:                   34 cm
 [Advanced parameters]
  Input Signal:                           Digital
  Color Bit Depth:                        6 Bits per Primary Color
  Digital Video Interface Standard Supported: DisplayPort
  Gamma Factor:                           2.20
 [DPMS Modes]
  Standby:                                Not Supported
  Suspend:                                Not Supported
  Active Off:                             Not Supported
  Standard Colour Space (sRGB) Default:   Not Supported
  Preferred Timing Mode:                  Supported
  Default GTF (Continuous Frequency):     Not Supported
  DFP 1.x Compatible:                     Yes
 [Supported Video Modes]
  1920 x 1080                             344 x 194 mm, Pixel Clock 141.40 MHz
  1920 x 1080                             344 x 194 mm, Pixel Clock 98.10 MHz
```

---

### Post by tea for one on 2021-08-11
> **conwayphelps said:**
> I tried the live USB on earlier versions, what I checked was 19.10 and 20.10, and they worked fine, recognizing all the hardware, so something changed from 20.04 to 20.10 that made it so this is not recognized. I'm scratching my head.

Did you not try Ubuntu  20.04 LTS?

---

### Post by conwayphelps on 2021-08-11
Yes, and it seems to work just fine. The new version of Ubuntu, 21.04 will not work. I have the same problem with Linux Mint.

---

### Post by conwayphelps on 2021-08-12
Whatever the problem was isn't in the 21.04 that I just downloaded and tried. Although, when I am loading Ubuntu I get the following errors flashing on the screen very quickly. I was able to use the slow motion on my camera to get a shot of what the errors and the codes are:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288948&stc=1[/IMG]

I am not sure if this will help. Aside from these errors posting I don't see any of the problems any more that I was experiencing before.

---

### Post by tea for one on 2021-08-12
> CPU Brand Name:                         11th Gen Intel(R) Core(TM) i7-1165G7 @ 2.80GHz
Usually this CPU would need a newish kernel such as supplied with Ubuntu 21.04.
However, you report that 21.04 doesn't work, yet earlier versions are fine.
It's a bit baffling for me and I do not know what to suggest other than use 20.04 LTS.

Your screen shot shows ACPI BIOS error - have you explored all the UEFI settings?

When you test the various versions, do you boot in UEFI mode?

---

### Post by conwayphelps on 2021-08-12
I was a little early to say that it "worked", it did to a point. After loading the program into the computer the Driver Manager pops up and says that a video driver could not be found, that I am using just the default, and that I needed to download the driver. Once I click on the button to check for new drivers, it says that it can't find any drivers that are compatible for my system and leaves it at that. 

Does Ubuntu support the new Intel Tiger Lake-UP3 Intel Iris XE?

---

### Post by tea for one on 2021-08-13
> **conwayphelps said:**
> Does Ubuntu support the new Intel Tiger Lake-UP3 Intel Iris XE?

I would be surprised if Intel Hardware lacked support in future versions.
New hardware recognition generally means a recent kernel or even a kernel still being developed.

Have you tried a 21.10 (in development) release?

More info here [https://ubuntuforums.org/showthread.php?t=2452659](https://ubuntuforums.org/showthread.php?t=2452659)

---

### Post by conwayphelps on 2021-08-13
After much looking and searching I found a simple solution. 

apt install linux-oem-20.04 && sudo reboot 0

After the reboot everything worked just fine and the Iris XE drivers were installed.

Answer found at [http://askubuntu.com/questions/1299067/ubuntu-20-04-no-driver-loaded-for-intel-iris-xe-graphics](http://askubuntu.com/questions/1299067/ubuntu-20-04-no-driver-loaded-for-intel-iris-xe-graphics) at the bottom of the page.

---

