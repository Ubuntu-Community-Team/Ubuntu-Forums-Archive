---
title: "Critical error while Installation"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by mindos on 2009-08-20
Hi. I have been having issues while trying to use Live CDs **as well as with** Alternative CDs.
Problem is common, any action chosen at the initial bootup screen ceases to continue and gives just a blank screen with a blinking cursor.

While using the Alternative CD for Ubuntu, I noted the commands until the installation stops responding. Below are the last few lines that show up on the screen..

```
[  1.097636]  isapnp: Scanning for PnP cards..
[  1.451707]  isapnp: No Plug & Play device found
[  1.453857]  Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[  1.454009]  serial 8250: ttys0 at I/O 0x3f8 (irq = 4) is a 16550A
[  1.454568]  00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  1.454745]  serial 0000:03:04.0 PCI INT A -> GSI 17 (level , low) -> IRQ 17
_
```PC Configuration :
Quite an old PC with Pentium P4 2.4 Ghz, 512 MB RAM and built-in graphics support. 
Additional details on configuration may be see below :


System Information
------------------
Time of this report: 8/20/2009, 03:55:25
       Machine name: XP
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_rtm.040803-2158)
           Language: English (Regional Setting: English)
System Manufacturer: INTEL
       System Model: P4I45Gx_PE,
               BIOS: Version 1.00
          Processor: Intel(R) Pentium(R) 4 CPU 2.40GHz
             Memory: 504MB RAM
          Page File: 268MB used, 1153MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode


---------------
Display Devices
---------------
        Card name: Intel(R) 82845G/GL Graphics Controller
     Manufacturer: Intel Corporation
        Chip type: Intel(R) 82845G/GL Chip
         DAC type: Internal
       Device Key: Enum\PCI\VEN_8086&DEV_2562&SUBSYS_25621849&REV_03
   Display Memory: 48.0 MB
     Current Mode: 1024 x 768 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: ialmrnt5.dll
   Driver Version: 6.13.0001.3095 (English)
      DDI Version: 8
Driver Attributes: Final Retail
 Driver Date/Size: 5/6/2002 13:41:02, 29184 bytes
      WHQL Logo'd: n/a
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: ialmnt5.sys
    Mini VDD Date: 5/6/2002 13:40:06, 77373 bytes
Device Identifier: {D7B78E66-6622-11CF-EE77-6305A1C2CB35}
        Vendor ID: 0x8086
        Device ID: 0x2562
        SubSys ID: 0x25621849
      Revision ID: 0x0003
      Revision ID: 0x0003
      Video Accel: ModeMPEG2_B ModeMPEG2_A ModeMPEG2_C ModeMPEG2_D 
 Deinterlace Caps: n/a
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Enabled
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

-------------
Sound Devices
-------------
            Description: C-Media Wave Device
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: PCI\VEN_8086&DEV_24C5&SUBSYS_434D1849&REV_02
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: cmuda.sys
         Driver Version: 5.12.0001.0041 (English)
      Driver Attributes: Final Debug
            WHQL Logo'd: n/a
          Date and Size: 1/8/2004 10:07:02, 812416 bytes
            Other Files: 
        Driver Provider: C-Media Inc.
         HW Accel Level: Full
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: Yes, Yes
   I3DL2(tm) Listen/Src: Yes, Yes
Sensaura(tm) ZoomFX(tm): Yes
               Registry: OK
      Sound Test Result: Not run

---

### Post by running_rabbit07 on 2009-08-20
What speed did you burn the disks at? (It is recommended to burn at 4x)

Are you using the 64-bit ISO or 32-bit?

Are you trying to install Ubuntu, Kubuntu, or Xubuntu?

Which release are you trying to install, 8.04 Hardy, 8.10 Intrepid, 9.04 Jaunty, or 9.10 Karmic?

---

### Post by mindos on 2009-08-21
I tried Ubuntu 8.10, Ubuntu 9.04 and Kubuntu 8.10. 
All disks checked multiple times for consistency and successfully passed the tests. (Burnt at 16x) 
[B]
Important UPDATE[/B] : I finally managed to successfully install Ubuntu 9.04 though the Alternate CD.
_**The issue still persists**_. After installation, I went to "Recovery Mode" and checked why the system hanged while showing "Starting Up...".
The messages that I've shown above were exactly the same as I noticed this time.
The system hangs after that last line of the message..

What problem could this be?

---

### Post by running_rabbit07 on 2009-08-21
I don't know why it is doing that.

Does anyone have any insight on this?

---

