---
title: "Transport NX Laptop"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by SteelValor on 2005-12-16
Hey all,

 I would really love to Ubuntu this p.o.s., but the Xircom Cardbus and my alternate Linksys Wireless G USB adapter will not work with Ubuntu to the best of my knowledge. Does anyone have any pointers??

Here's my dxdiag output.

------------------
System Information
------------------
Time of this report: 12/16/2005, 08:03:42
       Machine name: 
   Operating System: Windows 2000 Professional (5.0, Build 2195) Service Pack 4
           Language: English (Regional Setting: English)
System Manufacturer: Micron Electronics,Inc
       System Model: Transport NX
               BIOS: Default System BIOS
          Processor: Intel Pentium II processor, ~400MHz
             Memory: 320MB RAM
          Page File: 191MB used, 167MB available
        Windows Dir: C:\WINNT
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.0001.0904 32bit Unicode

---------------
Display Devices
---------------
        Card name: ATI Technologies Inc. 3D RAGE LT PRO AGP 2X
     Manufacturer: ATI Technologies Inc.
        Chip type: ATI 3D RAGE LT PRO AGP 2X (A2U2)
         DAC type: ATI Internal DAC
       Device Key: Enum\PCI\VEN_1002&DEV_4C42&SUBSYS_00000000&REV_DC
   Display Memory: 8.0 MB
     Current Mode: 1024 x 768 (16 bit) (60Hz)
          Monitor: Generic Television
  Monitor Max Res: 640,480
      Driver Name: atidrab.dll
   Driver Version: 5.00.2180.0001 (English)
      DDI Version: 7
Driver Attributes: Final Retail
 Driver Date/Size: 12/7/1999 11:43:28, 135184 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: atimpab.sys
    Mini VDD Date: 11/10/1999 10:34:08, 71632 bytes
Device Identifier: {D7B71EE2-0F02-11CF-B163-842873C2C835}
        Vendor ID: 0x1002
        Device ID: 0x4C42
        SubSys ID: 0x00000000
      Revision ID: 0x00DC
      Revision ID: 0x00DC
      Video Accel: 
 Deinterlace Caps: n/a
         Registry: OK
     DDraw Status: Enabled
       D3D Status: Enabled
       AGP Status: Not Available
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

-------------
Sound Devices
-------------
            Description: ESS Maestro
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: PCI\VEN_125D&DEV_1968&SUBSYS_0001125D&REV_00
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: maestro.sys
         Driver Version: 5.00.2187.0001 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 11/22/1999 11:01:42, 48368 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Standard
              Cap Flags: 0xF5F
    Min/Max Sample Rate: 5000, 48000
Static/Strm HW Mix Bufs: 12, 11
 Static/Strm HW 3D Bufs: 0, 0
              HW Memory: 0
       Voice Management: No
 EAX(tm) 2.0 Listen/Src: No, No
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No
               Registry: OK
      Sound Test Result: Not run

---------------------
Sound Capture Devices
---------------------
            Description: ESS Maestro
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: maestro.sys
         Driver Version: 5.00.2187.0001 (English)
      Driver Attributes: Final Retail
          Date and Size: 11/22/1999 11:01:42, 48368 bytes
              Cap Flags: 0x40
           Format Flags: 0xFFF

-----------
USB Devices
-----------
+ USB Root Hub
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 6/19/2003 14:05:04, 40176 bytes
| 
+-+ Generic USB Hub
| | Vendor/Product ID: 0x0416, 0x5518
| | Location: USB HUB 
| | Matching Device ID: usb\class_09
| | Service: usbhub
| | Driver: usbhub.sys, 6/19/2003 14:05:04, 40176 bytes
| | 
| +-+ USB Human Interface Device
| | | Vendor/Product ID: 0x045E, 0x0029
| | | Location: Microsoft IntelliMouse® Optical
| | | Matching Device ID: usb\class_03&subclass_01
| | | Service: HidUsb
| | | Driver: hidclass.sys, 6/19/2003 14:05:04, 24752 bytes
| | | Driver: hidparse.sys, 6/19/2003 14:05:04, 23056 bytes
| | | Driver: hid.dll, 6/19/2003 14:05:04, 18192 bytes
| | | Driver: hidusb.sys, 12/7/1999 08:00:00, 13904 bytes
| | | Driver: pid.dll, 10/30/2001 08:10:00, 31744 bytes
| | | 
| | +-+ HID-compliant mouse
| | | | Vendor/Product ID: 0x045E, 0x0029
| | | | Matching Device ID: hid_device_system_mouse
| | | | Service: mouhid
| | | | Driver: mouhid.sys, 6/19/2003 14:05:04, 11632 bytes
| | | | Driver: mouclass.sys, 6/19/2003 14:05:04, 21776 bytes

----------------
Gameport Devices
----------------
+ ESS Maestro2 PCI AudioDrive (WDM)
| Location: PCI bus 0, device 10, function 0
| Matching Device ID: pci\ven_125d&dev_1968
| Service: maestro
| Driver: portcls.sys, 6/19/2003 14:05:04, 148208 bytes
| Driver: stream.sys, 7/9/2004 04:27:28, 48512 bytes
| Driver: wdmaud.drv, 6/19/2003 14:05:04, 21264 bytes
| Driver: maestro.sys, 11/22/1999 11:01:42, 48368 bytes
| Driver: ksuser.dll, 12/12/2002 00:14:32, 4096 bytes
| 
+-+ Standard Game Port
| | Matching Device ID: *pnpb02f
| | Service: gameenum
| | Driver: gameenum.sys, 6/19/2003 14:05:04, 9808 bytes

------------
PS/2 Devices
------------
+ Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| Driver: i8042prt.sys, 6/19/2003 14:05:04, 46992 bytes
| Driver: kbdclass.sys, 6/19/2003 14:05:04, 24528 bytes
| 
+ PS/2 Compatible Mouse
| Matching Device ID: *pnp0f13
| Service: i8042prt
| Driver: i8042prt.sys, 6/19/2003 14:05:04, 46992 bytes
| Driver: mouclass.sys, 6/19/2003 14:05:04, 21776 bytes


-------------------
DirectPlay Adapters
-------------------
DirectPlay8 Modem Service Provider: Xircom Cardbus Ethernet 100 + Modem 56 (Modem Interface)
DirectPlay8 Serial Service Provider: COM1
DirectPlay8 Serial Service Provider: COM3
DirectPlay8 TCP/IP Service Provider: Linksys Wireless-G USB Network Adapter with SpeedBooster - 

-----------------------
DirectPlay Voice Codecs
-----------------------
Voxware VR12 1.4kbit/s
Voxware SC06 6.4kbit/s
Voxware SC03 3.2kbit/s
MS-PCM 64 kbit/s
MS-ADPCM 32.8 kbit/s
Microsoft GSM 6.10 13 kbit/s
TrueSpeech(TM) 8.6 kbit/s

------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 3.7 GB
Total Space: 5.7 GB
File System: NTFS
      Model: IBM-DARA-206000

      Drive: D:
      Model: TEAC CD-224E
     Driver: c:\winnt\system32\drivers\cdrom.sys, 5.00.2195.6655 (English), 6/19/2003 14:05:04, 27984 bytes

--------------
System Devices
--------------
     Name: Intel 82443BX Pentium(r) II Processor to AGP Controller
Device ID: PCI\VEN_8086&DEV_7191&SUBSYS_00000000&REV_03\3&61AAA01&0&08
   Driver: C:\WINNT\system32\DRIVERS\AGP440.SYS, 5.00.2195.6655 (English), 6/19/2003 14:05:04, 21008 bytes

     Name: Intel 82443BX Pentium(r) II Processor to PCI Bridge
Device ID: PCI\VEN_8086&DEV_7190&SUBSYS_00000000&REV_03\3&61AAA01&0&00
   Driver: n/a

     Name: Intel 82371AB/EB PCI to USB Universal Host Controller
Device ID: PCI\VEN_8086&DEV_7112&SUBSYS_00000000&REV_01\3&61AAA01&0&3A
   Driver: C:\WINNT\system32\drivers\uhcd.sys, 5.00.2195.6655 (English), 6/19/2003 14:05:04, 32848 bytes
   Driver: C:\WINNT\system32\drivers\usbd.sys, 5.00.2195.6658 (English), 6/19/2003 14:05:04, 20688 bytes
   Driver: C:\WINNT\system32\drivers\usbhub.sys, 5.00.2195.6689 (English), 6/19/2003 14:05:04, 40176 bytes
   Driver: C:\WINNT\system32\usbui.dll, 5.00.2134.0001 (English), 11/30/1999 18:39:50, 59664 bytes

     Name: Intel(r) 82371AB/EB PCI Bus Master IDE Controller
Device ID: PCI\VEN_8086&DEV_7111&SUBSYS_00000000&REV_01\3&61AAA01&0&39
   Driver: C:\WINNT\system32\DRIVERS\intelide.sys, 5.00.2195.6666 (English), 6/19/2003 14:05:04, 4624 bytes
   Driver: C:\WINNT\system32\DRIVERS\pciidex.sys, 5.00.2195.6672 (English), 6/19/2003 14:05:04, 22064 bytes
   Driver: C:\WINNT\system32\DRIVERS\atapi.sys, 5.00.2195.6699 (English), 6/19/2003 14:05:04, 86672 bytes

     Name: Intel 82371AB/EB PCI to ISA bridge (EIO mode)
Device ID: PCI\VEN_8086&DEV_7110&SUBSYS_00000000&REV_02\3&61AAA01&0&38
   Driver: C:\WINNT\system32\DRIVERS\isapnp.sys, 5.00.2195.6655 (English), 6/19/2003 14:05:04, 46992 bytes

     Name: ESS Maestro2 PCI AudioDrive (WDM)
Device ID: PCI\VEN_125D&DEV_1968&SUBSYS_0001125D&REV_00\3&61AAA01&0&50
   Driver: C:\WINNT\system32\drivers\portcls.sys, 5.00.2195.6655 (English), 6/19/2003 14:05:04, 148208 bytes
   Driver: C:\WINNT\system32\drivers\stream.sys, 5.03.0001.0904 (English), 7/9/2004 04:27:28, 48512 bytes
   Driver: C:\WINNT\system32\wdmaud.drv, 5.00.2195.6673 (English), 6/19/2003 14:05:04, 21264 bytes
   Driver: C:\WINNT\system32\drivers\maestro.sys, 5.00.2187.0001 (English), 11/22/1999 11:01:42, 48368 bytes
   Driver: C:\WINNT\system32\ksuser.dll, 5.03.0000.0900 (English), 12/12/2002 00:14:32, 4096 bytes

     Name: O2Micro/ROHM OZ6836/6860 CardBus Controller
Device ID: PCI\VEN_1217&DEV_6836&SUBSYS_68360983&REV_62\3&61AAA01&0&49
   Driver: C:\WINNT\system32\DRIVERS\pcmcia.sys, 5.00.2195.6664 (English), 6/19/2003 14:05:04, 109584 bytes

     Name: O2Micro/ROHM OZ6836/6860 CardBus Controller
Device ID: PCI\VEN_1217&DEV_6836&SUBSYS_68360983&REV_62\3&61AAA01&0&48
   Driver: C:\WINNT\system32\DRIVERS\pcmcia.sys, 5.00.2195.6664 (English), 6/19/2003 14:05:04, 109584 bytes

     Name: Xircom Cardbus Ethernet 100 + Modem 56 (Modem Interface)
Device ID: PCI\VEN_115D&DEV_0103&SUBSYS_1181115D&REV_03\4&C695F28&0&0148
   Driver: n/a

     Name: Xircom CardBus Ethernet 100 + Modem 56 (Ethernet Interface)
Device ID: PCI\VEN_115D&DEV_0003&SUBSYS_1181115D&REV_03\4&C695F28&0&0048
   Driver: C:\WINNT\system32\DRIVERS\cben5.sys, 3.14.0013.0000 (English), 2/26/2002 17:10:48, 50498 bytes

     Name: ATI Technologies Inc. 3D RAGE LT PRO AGP 2X
Device ID: PCI\VEN_1002&DEV_4C42&SUBSYS_00000000&REV_DC\4&415A68E&0&0008
   Driver: C:\WINNT\system32\DRIVERS\atimpab.sys, 5.00.2179.0001 (English), 11/10/1999 10:34:08, 71632 bytes
   Driver: C:\WINNT\system32\atidrab.dll, 5.00.2180.0001 (English), 12/7/1999 11:43:28, 135184 bytes

---

