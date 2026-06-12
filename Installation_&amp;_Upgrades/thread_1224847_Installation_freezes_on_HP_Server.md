---
title: "Installation freezes on HP Server"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by mrmozer on 2009-07-27
Hi all,

I'm trying to install ubuntu or fedora on my dedicated HP Server that I recently purchased. I'm a newb and have the basic understanding of Linux systems.

My HP ProLiant Hardware information is below, I am suspecting that the installation freezes because of a hardware conflict or something? Because installing Fedora 10 freezes at "Detecting Hardware".

------------------
System Information
------------------
Time of this report: 7/14/2009, 14:38:01
       Machine name: AYSERVER
   Operating System: Windows Server 2003 Standard x64 Edition (5.2, Build 3790) Service Pack 2 (3790.srv03_sp2_gdr.090319-1204)
           Language: English (Regional Setting: English)
System Manufacturer: HP
       System Model: ProLiant ML150 G5
               BIOS: Default System BIOS
          Processor: Intel(R) Pentium(R) III Xeon processor (4 CPUs), ~2.3GHz
             Memory: 2046MB RAM
          Page File: 370MB used, 4616MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.3790.3959 32bit Unicode

------------
DxDiag Notes
------------
  DirectX Files Tab: No problems found.
      Display Tab 1: No problems found. Direct3D functionality not available.  You should verify that the driver is a final version from the hardware manufacturer.
        Sound Tab 1: No sound card was found.  If one is expected, you should install a sound driver provided by the hardware manufacturer.
          Music Tab: No DirectMusic ports were found.
          Input Tab: No problems found.
        Network Tab: No problems found.

--------------------
DirectX Debug Levels
--------------------
Direct3D:    0/4 (n/a)
DirectDraw:  0/4 (retail)
DirectInput: 0/5 (n/a)
DirectMusic: 0/5 (n/a)
DirectPlay:  0/9 (retail)
DirectSound: 0/5 (retail)
DirectShow:  0/6 (retail)

---------------
Display Devices
---------------
        Card name: Matrox G200e (ServerEngines) - English
     Manufacturer: Matrox Graphics
        Chip type: Matrox G200e
         DAC type: Integrated, 175 MHz
       Device Key: Enum\PCI\VEN_102B&DEV_0522&SUBSYS_0000103C&REV_02
   Display Memory: n/a
     Current Mode: 1024 x 768 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: G200ed.dll
   Driver Version: 6.12.0001.1959 (English)
      DDI Version: unknown
Driver Attributes: Final Retail
 Driver Date/Size: 4/13/2007 15:13:26, 207872 bytes
      WHQL Logo'd: n/a
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: G200em.sys
    Mini VDD Date: 4/13/2007 15:13:26, 236032 bytes
Device Identifier: {D7B71ECB-4662-11CF-2B74-0120A1C2CB35}
        Vendor ID: 0x102B
        Device ID: 0x0522
        SubSys ID: 0x0000103C
      Revision ID: 0x0002
      Revision ID: 0x0002
      Video Accel: 
 Deinterlace Caps: n/a
         Registry: OK
     DDraw Status: Not Available
       D3D Status: Not Available
       AGP Status: Not Available
DDraw Test Result: Not run
 D3D7 Test Result: Not run
 D3D8 Test Result: Not run
 D3D9 Test Result: Not run

-------------
Sound Devices
-------------
            Description: 
 Default Sound Playback: No
 Default Voice Playback: No
            Hardware ID: 
        Manufacturer ID: 
             Product ID: 
                   Type: 
            Driver Name: 
         Driver Version: 
      Driver Attributes: 
            WHQL Logo'd: 
          Date and Size: 
            Other Files: 
        Driver Provider: 
         HW Accel Level: Emulation Only
              Cap Flags: 0x0
    Min/Max Sample Rate: 0, 0
Static/Strm HW Mix Bufs: 0, 0
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
-------------------
DirectInput Devices
-------------------
      Device Name: Mouse
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

      Device Name: Keyboard
         Attached: 1
    Controller ID: n/a
Vendor/Product ID: n/a
        FF Driver: n/a

Poll w/ Interrupt: No
         Registry: OK

-----------
USB Devices
-----------
+ USB Root Hub
| Vendor/Product ID: 0x8086, 0x2935
| Matching Device ID: usb\root_hub
| Service: usbhub

----------------
Gameport Devices
----------------

------------
PS/2 Devices
------------
+ HID Keyboard Device
| Matching Device ID: hid_device_system_keyboard
| Service: kbdhid
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| 
+ HID-compliant mouse
| Matching Device ID: hid_device_system_mouse
| Service: mouhid
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD

----------------------------
DirectPlay Service Providers
----------------------------
DirectPlay8 Modem Service Provider - Registry: OK, File: dpnet.dll (5.03.3790.3959)
DirectPlay8 Serial Service Provider - Registry: OK, File: dpnet.dll (5.03.3790.3959)
DirectPlay8 IPX Service Provider - Registry: OK, File: dpnet.dll (5.03.3790.3959)
DirectPlay8 TCP/IP Service Provider - Registry: OK, File: dpnet.dll (5.03.3790.3959)

DirectPlay Voice Wizard Tests: Full Duplex: , Half Duplex: , Mic: 
DirectPlay Test Result: Not run
Registry: OK

-------------------
DirectPlay Adapters
-------------------
DirectPlay8 Serial Service Provider: COM1
DirectPlay8 TCP/IP Service Provider: Local Area Connection - IPv4 - 

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

-------------------------
DirectPlay Lobbyable Apps
-------------------------

------------------------
Disk & DVD/CD-ROM Drives
------------------------
      Drive: C:
 Free Space: 135.0 GB
Total Space: 152.4 GB
File System: NTFS
      Model: ADAPTEC RAID 1 SCSI Disk Device

      Drive: D:
      Model: HL-DT-ST DVD-RAM GH15L
     Driver: c:\windows\system32\drivers\cdrom.sys, , 0 bytes

Any help is deeply appreciated to get my Linux up and running. I want to setup Apache Server once installed.

---

