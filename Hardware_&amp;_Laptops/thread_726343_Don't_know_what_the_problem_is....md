---
title: "Don't know what the problem is..."
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by Rabb on 2008-03-16
So, on Tuesday of March 11th, my computer was not able to load anything to do with Direct3d. Games such as Americas Army and Call of Duty 4 will load then when it's about to go to the main menu it will bring my computer to a black screen and my monitor will say "No signal". The only way I can get out of this is by manually restarting my computer by holding the button down until it shuts off. Days have gone by of me and people I know trying to fix this, I have done a lot of different things. Everything that involves direct3d will not work, I can preform a stability test in my nvidia control panel - as soon as I start it up it will bring me to the black screen with "No Signal" and I have to turn it off by holding the button down, just like how I do when I load one of those 2 games up. It's the same exact thing. Earlier I was in my control panel and I was just looking at my settings with direct3d (Not moving the mouse or anything) and my computer crashed and did the same thing with the black screen and "No Signal". Also, in my dxdiag I go to test my direct3d and it will do the black screen with "No Signal" automatically causing it to fail, everything else in dxdiag will pass though. I have tried to fix this by:

-Testing Power supply by taking out my sound card to see if the PSU was not giving enough power out.
-Moved around RAM sticks
-Changed video cards
-Anti-Virus
-Anti-Spyware
-Updated mobo chipset drivers
-Updated bios
-Tried many driver versions of my video card (Including most recent)
-Tried only 1 stick of RAM instead of 2.
-Reinstalled directx 9.0c
-Installed Directx 9.0C with both disc and the internet
-I read somewhere that mouse drivers might fix it, so I got the most updated mouse drivers as well
-Updated sound drivers
-I used driver cleaner and reinstalled certain ones
-I even have reformatted my computer and after a reformat, the problem still exists.


I attached my dxdiag. I'm not sure if it will save my results from the test since when I run a test on direct3d it crashes my computer and brings me to the black screen which makes me restart my computer..

Any help would be greatly appreciated.

---

### Post by Rabb on 2008-03-16
I couldn't attach my dxdaig so here it is:
(Sorry for double post)

------------------
System Information
------------------
Time of this report: 3/16/2008, 13:50:16
       Machine name: JOE
   Operating System: Windows XP Home Edition (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
           Language: English (Regional Setting: English)
System Manufacturer: GBT___
       System Model: NVDAACPI
               BIOS: Award Modular BIOS v6.00PG
          Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+,  MMX,  3DNow (2 CPUs), ~2.2GHz
             Memory: 1024MB RAM
          Page File: 339MB used, 2122MB available
        Windows Dir: H:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

------------
DxDiag Notes
------------
  DirectX Files Tab: No problems found.
      Display Tab 1: No problems found.
        Sound Tab 1: No problems found.
          Music Tab: No problems found.
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
        Card name: NVIDIA GeForce 7900 GS
     Manufacturer: NVIDIA
        Chip type: GeForce 7900 GS
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0292&SUBSYS_22181682&REV_A1
   Display Memory: 256.0 MB
     Current Mode: 1280 x 1024 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: nv4_disp.dll
   Driver Version: 6.14.0010.9371 (English)
      DDI Version: 9 (or higher)
Driver Attributes: Final Retail
 Driver Date/Size: 10/22/2006 12:22:00, 4527488 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: nv4_mini.sys
    Mini VDD Date: 10/22/2006 12:22:00, 3994624 bytes
Device Identifier: {D7B71E3E-41D2-11CF-A951-120200C2CB35}
        Vendor ID: 0x10DE
        Device ID: 0x0292
        SubSys ID: 0x22181682
      Revision ID: 0x00A1
      Revision ID: 0x00A1
      Video Accel: ModeMPEG2_A ModeMPEG2_B ModeMPEG2_C ModeMPEG2_D ModeWMV9_B ModeWMV9_A 
 Deinterlace Caps: {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YUY2,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(UYVY,YUY2) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(YV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
                   {212DC724-3235-44A4-BD29-E1652BBCC71C}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_PixelAdaptive 
                   {335AA36E-7884-43A4-9C91-7F87FAF3E37E}: Format(In/Out)=(NV12,0x3231564e) Frames(Prev/Fwd/Back)=(0,0,0) Caps=VideoProcess_YUV2RGB VideoProcess_StretchX VideoProcess_StretchY DeinterlaceTech_BOBVerticalStretch 
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
            Description: SB Audigy 2 Audio [9000]
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: PCI\VEN_1102&DEV_0008&SUBSYS_10011102&REV_00
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: ctaud2k.sys
         Driver Version: 5.12.0001.0522 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 4/28/2004 23:01:00, 374000 bytes
            Other Files: 
        Driver Provider: Creative
         HW Accel Level: Full
              Cap Flags: 0xF5F
    Min/Max Sample Rate: 4000, 192000
Static/Strm HW Mix Bufs: 64, 62
 Static/Strm HW 3D Bufs: 64, 62
              HW Memory: 0
       Voice Management: Yes
 EAX(tm) 2.0 Listen/Src: Yes, Yes
   I3DL2(tm) Listen/Src: No, No
Sensaura(tm) ZoomFX(tm): No
               Registry: OK
      Sound Test Result: Not run

---------------------
Sound Capture Devices
---------------------
            Description: SB Audigy 2 Audio [9000]
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: ctaud2k.sys
         Driver Version: 5.12.0001.0522 (English)
      Driver Attributes: Final Retail
          Date and Size: 4/28/2004 23:01:00, 374000 bytes
              Cap Flags: 0x41
           Format Flags: 0xFFF

            Description: AK5370          
  Default Sound Capture: No
  Default Voice Capture: No
            Driver Name: usbaudio.sys
         Driver Version: 5.01.2600.2180 (English)
      Driver Attributes: Final Retail
          Date and Size: 8/3/2004 19:07:56, 59264 bytes
              Cap Flags: 0x41
           Format Flags: 0x444

-----------
DirectMusic
-----------
        DLS Path: H:\WINDOWS\SYSTEM32\drivers\GM.DLS
     DLS Version: 1.00.0016.0002
    Acceleration: Enabled
           Ports: SB Audigy 2 DirectMusic Synthesizer [9000], Hardware (Kernel Mode), Output, DLS, Internal, Default Port
                  SB Audigy 2 Audio [9000], Software (Kernel Mode), Output, DLS, Internal
                  Microsoft MIDI Mapper [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 Synth A [9000] [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 Sw Synth [9000] [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  SB Audigy 2 Synth B [9000] [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  Microsoft GS Wavetable SW Synth [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  Microsoft Synthesizer, Software (Not Kernel Mode), Output, DLS, Internal
        Registry: OK
     Test Result: Not run

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
| Vendor/Product ID: 0x10DE, 0x005A
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 10/8/2004 08:01:47, 57600 bytes
| Driver: usbd.sys, 10/8/2004 08:01:47, 4736 bytes
| 
+-+ Logitech USB G3 (MX518) Optical Mouse
| | Vendor/Product ID: 0x046D, 0xC01E
| | Location: USB-PS/2 Optical Mouse
| | Matching Device ID: usb\vid_046d&pid_c01e
| | Lower Filters: LUsbFilt
| | Service: HidUsb
| | Driver: hidusb.sys, 8/17/2001 15:02:20, 9600 bytes
| | Driver: hidclass.sys, 8/4/2004 00:08:20, 36224 bytes
| | Driver: hidparse.sys, 8/4/2004 00:08:18, 24960 bytes
| | Driver: hid.dll, 10/8/2004 08:01:47, 20992 bytes
| | Driver: LUsbFilt.sys, 11/29/2007 03:18:12, 28432 bytes
| | Driver: WdfCoInstaller01005.dll, 6/22/2007 12:34:02, 1419232 bytes
| | 
| +-+ Logitech HID-compliant G3/MX518 Optical Mouse
| | | Vendor/Product ID: 0x046D, 0xC01E
| | | Matching Device ID: hid\vid_046d&pid_c01e
| | | Upper Filters: LMouFilt
| | | Lower Filters: LHidFilt
| | | Service: mouhid
| | | Driver: mouhid.sys, 8/17/2001 14:48:00, 12160 bytes
| | | Driver: mouclass.sys, 8/3/2004 23:58:34, 23040 bytes
| | | Driver: LHidFilt.Sys, 11/29/2007 03:17:48, 35088 bytes
| | | Driver: LMouFilt.Sys, 11/29/2007 03:17:56, 36368 bytes
| | | Driver: KHALMNPR.Exe, 11/29/2007 03:17:20, 55824 bytes
| | | Driver: WdfCoInstaller01005.dll, 6/22/2007 12:34:02, 1419232 bytes

----------------
Gameport Devices
----------------

------------
PS/2 Devices
------------
+ PS/2 Keyboard
| Matching Device ID: *pnp0303
| Upper Filters: L8042Kbd
| Service: i8042prt
| Driver: i8042prt.sys, 8/4/2004 00:14:38, 52736 bytes
| Driver: kbdclass.sys, 8/3/2004 23:58:34, 24576 bytes
| Driver: L8042Kbd.sys, 11/29/2007 03:17:28, 20240 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 02:01:08, 40840 bytes
| Driver: kbdclass.sys, 8/3/2004 23:58:34, 24576 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 02:01:08, 40840 bytes
| Driver: mouclass.sys, 8/3/2004 23:58:34, 23040 bytes

----------------------------
DirectPlay Service Providers
----------------------------
DirectPlay8 Modem Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 Serial Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 IPX Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
DirectPlay8 TCP/IP Service Provider - Registry: OK, File: dpnet.dll (5.03.2600.2180)
Internet TCP/IP Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
IPX Connection For DirectPlay - Registry: OK, File: dpwsockx.dll (5.03.2600.2180)
Modem Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)
Serial Connection For DirectPlay - Registry: OK, File: dpmodemx.dll (5.03.2600.2180)

DirectPlay Voice Wizard Tests: Full Duplex: Not run, Half Duplex: Not run, Mic: Not run
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
      Drive: H:
 Free Space: 144.9 GB
Total Space: 157.1 GB
File System: NTFS
      Model: HDT722516DLA380

      Drive: G:
      Model: SONY DVD-ROM DDU1615
     Driver: h:\windows\system32\drivers\cdrom.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 49536 bytes

--------------
System Devices
--------------
     Name: Creative SB Audigy 2 (WDM)
Device ID: PCI\VEN_1102&DEV_0008&SUBSYS_10011102&REV_00\4&13699180&0&4048
   Driver: H:\WINDOWS\system32\ksuser.dll, 5.03.2600.2180 (English), 8/4/2004 04:56:44, 4096 bytes
   Driver: H:\WINDOWS\system32\ksproxy.ax, 5.03.2600.2180 (English), 8/4/2004 04:56:58, 130048 bytes
   Driver: H:\WINDOWS\system32\drivers\ks.sys, 5.03.2600.2180 (English), 8/4/2004 03:15:22, 140928 bytes
   Driver: H:\WINDOWS\system32\drivers\drmk.sys, 5.01.2600.2180 (English), 8/4/2004 03:08:00, 60288 bytes
   Driver: H:\WINDOWS\system32\drivers\portcls.sys, 5.01.2600.2180 (English), 8/4/2004 03:15:50, 145792 bytes
   Driver: H:\WINDOWS\system32\drivers\stream.sys, 5.03.2600.2180 (English), 8/4/2004 03:08:04, 48640 bytes
   Driver: H:\WINDOWS\system32\wdmaud.drv, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 23552 bytes
   Driver: H:\WINDOWS\system32\drivers\ctac32k.sys, 5.12.0001.0521 (English), 4/6/2004 04:24:54, 646128 bytes
   Driver: H:\WINDOWS\system32\drivers\ctaud2k.sys, 5.12.0001.0522 (English), 4/28/2004 23:01:00, 374000 bytes
   Driver: H:\WINDOWS\system32\drivers\ctoss2k.sys, 5.12.0001.0520 (English), 3/15/2004 22:36:44, 178736 bytes
   Driver: H:\WINDOWS\system32\drivers\ctprxy2k.sys, 5.12.0001.0520 (English), 3/15/2004 22:36:54, 6096 bytes
   Driver: H:\WINDOWS\system32\drivers\ctsfm2k.sys, 5.12.0001.0520 (English), 3/15/2004 22:37:12, 130384 bytes
   Driver: H:\WINDOWS\system32\drivers\emupia2k.sys, 5.12.0001.0520 (English), 3/15/2004 22:37:26, 147088 bytes
   Driver: H:\WINDOWS\system32\drivers\ha10kx2k.sys, 5.12.0001.0524 (English), 6/15/2004 21:47:10, 952144 bytes
   Driver: H:\WINDOWS\system32\drivers\haP16v2k.sys, 5.12.0001.0522 (English), 5/3/2004 01:48:56, 150160 bytes
   Driver: H:\WINDOWS\system32\drivers\pfmodnt.sys, 3.00.0000.0003 (English), 3/5/2003 16:19:28, 15840 bytes
   Driver: H:\WINDOWS\system32\drivers\haP17v2k.sys, 5.12.0001.0524 (English), 5/3/2004 01:49:54, 147696 bytes
   Driver: H:\WINDOWS\system32\ctdlang.dat, 7/1/2004 04:05:04, 132415 bytes
   Driver: H:\WINDOWS\system32\ctstatic.dat, 5/3/2004 02:10:04, 313207 bytes
   Driver: H:\WINDOWS\system32\ctdaught.dat, 5/3/2004 02:08:20, 53932 bytes
   Driver: H:\WINDOWS\system32\a3d.dll, 80.00.0000.0003 (English), 3/15/2004 22:29:58, 65536 bytes
   Driver: H:\WINDOWS\system32\commonfx.dll, 5.12.0001.0520 (English), 3/15/2004 22:37:44, 118868 bytes
   Driver: H:\WINDOWS\system32\ctaudfx.dll, 5.12.0001.0520 (English), 3/15/2004 22:38:16, 692306 bytes
   Driver: H:\WINDOWS\system32\ctsblfx.dll, 5.12.0001.0520 (English), 3/15/2004 22:39:18, 606208 bytes
   Driver: H:\WINDOWS\system32\sfman32.dll, 5.12.0001.0130 (English), 8/17/2001 02:35:46, 36864 bytes
   Driver: H:\WINDOWS\system32\ctbas2w.dat, 7/1/2004 04:05:02, 140643 bytes
   Driver: H:\WINDOWS\system32\ctsbas2w.dat, 7/1/2004 04:04:56, 264724 bytes
   Driver: H:\WINDOWS\system32\SBAudigy.ico, 8/17/2001 00:42:28, 7406 bytes
   Driver: H:\WINDOWS\system32\Audigy.bmp, 11/12/2001 21:48:20, 1912 bytes
   Driver: H:\WINDOWS\system32\ctcoinst.dll, 3.00.0000.0005 (English), 3/15/2004 22:41:48, 73728 bytes
   Driver: H:\WINDOWS\system32\ctdvinst.dll, 0.00.0000.0012 (English), 3/15/2004 22:42:06, 147456 bytes
   Driver: H:\WINDOWS\system32\drivers\ctdvda2k.sys, 5.13.0001.0431 (English), 3/15/2004 05:25:06, 337056 bytes

     Name: NVIDIA GeForce 7900 GS
Device ID: PCI\VEN_10DE&DEV_0292&SUBSYS_22181682&REV_A1\4&243D7BD0&0&0070
   Driver: H:\WINDOWS\system32\DRIVERS\nv4_mini.sys, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 3994624 bytes
   Driver: H:\WINDOWS\system32\nv4_disp.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 4527488 bytes
   Driver: H:\WINDOWS\system32\nvsvc32.exe, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 159810 bytes
   Driver: H:\WINDOWS\system32\nvhwvid.dll, 6.14.0010.9371 (), 10/22/2006 12:22:00, 581632 bytes
   Driver: H:\WINDOWS\system32\nvapi.dll, 6.14.0010.9371 (), 10/22/2006 12:22:00, 212992 bytes
   Driver: H:\WINDOWS\system32\nvoglnt.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 5644288 bytes
   Driver: H:\WINDOWS\system32\nvcpl.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 7700480 bytes
   Driver: H:\WINDOWS\system32\nvmctray.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 86016 bytes
   Driver: H:\WINDOWS\system32\nvwddi.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 81920 bytes
   Driver: H:\WINDOWS\system32\nvnt4cpl.dll, 6.14.0010.11060 (English), 10/22/2006 12:22:00, 286720 bytes
   Driver: H:\WINDOWS\system32\nvmccs.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 229376 bytes
   Driver: H:\WINDOWS\system32\nvdisps.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 5619712 bytes
   Driver: H:\WINDOWS\system32\nvdispsr.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 5255168 bytes
   Driver: H:\WINDOWS\system32\nvgames.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 3047424 bytes
   Driver: H:\WINDOWS\system32\nvgamesr.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 3203072 bytes
   Driver: H:\WINDOWS\system32\nvmccss.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 188416 bytes
   Driver: H:\WINDOWS\system32\nvmccssr.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 458752 bytes
   Driver: H:\WINDOWS\system32\nvmobls.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 888832 bytes
   Driver: H:\WINDOWS\system32\nvmoblsr.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 2859008 bytes
   Driver: H:\WINDOWS\system32\nvvitvs.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 2924544 bytes
   Driver: H:\WINDOWS\system32\nvvitvsr.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 2973696 bytes
   Driver: H:\WINDOWS\system32\nvwss.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 1236992 bytes
   Driver: H:\WINDOWS\system32\nvwssr.dll, 6.14.0010.9371 (English), 10/22/2006 12:22:00, 1732608 bytes
   Driver: H:\WINDOWS\help\nvcpl.hlp, 10/22/2006 12:22:00, 177897 bytes
   Driver: H:\WINDOWS\help\nvwcplen.hlp, 10/22/2006 12:22:00, 55444 bytes
   Driver: H:\WINDOWS\system32\nvcod.dll, 1.00.0000.0035 (English), 10/22/2006 12:22:00, 35840 bytes
   Driver: H:\WINDOWS\system32\nvcodins.dll, 1.00.0000.0035 (English), 10/22/2006 12:22:00, 35840 bytes

     Name: PCI Memory Controller
Device ID: PCI\VEN_10DE&DEV_005E&SUBSYS_50001458&REV_A3\3&2411E6FE&0&00
   Driver: n/a

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_005D&SUBSYS_00000000&REV_A3\3&2411E6FE&0&70
   Driver: H:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 68224 bytes

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_005D&SUBSYS_00000000&REV_A3\3&2411E6FE&0&68
   Driver: H:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 68224 bytes

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_005D&SUBSYS_00000000&REV_A3\3&2411E6FE&0&60
   Driver: H:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 68224 bytes

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_005D&SUBSYS_00000000&REV_A3\3&2411E6FE&0&58
   Driver: H:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 68224 bytes

     Name: PCI standard PCI-to-PCI bridge
Device ID: PCI\VEN_10DE&DEV_005C&SUBSYS_00000000&REV_A2\3&2411E6FE&0&48
   Driver: H:\WINDOWS\system32\DRIVERS\pci.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 68224 bytes

     Name: Standard Enhanced PCI to USB Host Controller
Device ID: PCI\VEN_10DE&DEV_005B&SUBSYS_50041458&REV_A3\3&2411E6FE&0&11
   Driver: H:\WINDOWS\system32\drivers\usbehci.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 26624 bytes
   Driver: H:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 142976 bytes
   Driver: H:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/3/2004 20:56:48, 74240 bytes
   Driver: H:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 57600 bytes
   Driver: H:\WINDOWS\system32\hccoin.dll, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 7168 bytes

     Name: Standard OpenHCD USB Host Controller
Device ID: PCI\VEN_10DE&DEV_005A&SUBSYS_50041458&REV_A2\3&2411E6FE&0&10
   Driver: H:\WINDOWS\system32\drivers\usbohci.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 17024 bytes
   Driver: H:\WINDOWS\system32\drivers\usbport.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 142976 bytes
   Driver: H:\WINDOWS\system32\usbui.dll, 5.01.2600.2180 (English), 8/3/2004 20:56:48, 74240 bytes
   Driver: H:\WINDOWS\system32\drivers\usbhub.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 57600 bytes

     Name: NVIDIA Network Bus Enumerator
Device ID: PCI\VEN_10DE&DEV_0057&SUBSYS_E0001458&REV_A3\3&2411E6FE&0&50
   Driver: H:\WINDOWS\system32\DRIVERS\nvnetbus.sys, 1.00.0000.5011 (English), 9/30/2005 00:52:22, 13056 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\nvnrm.sys, 1.00.0000.5011 (English), 9/30/2005 00:52:04, 301312 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\nvsnpu.sys, 1.00.0000.5011 (English), 9/30/2005 00:51:50, 222464 bytes
   Driver: H:\WINDOWS\system32\bdco1.dll, 1.00.0000.0000 (English), 9/30/2005 00:51:02, 9728 bytes
   Driver: H:\WINDOWS\system32\bdco1ins.dll, 1.00.0000.0000 (English), 9/30/2005 00:51:02, 9728 bytes
   Driver: H:\WINDOWS\system32\nvconrm.dll, 1.00.0000.0033 (English), 9/29/2005 12:24:16, 34304 bytes

     Name: NVIDIA nForce4 Serial ATA Controller
Device ID: PCI\VEN_10DE&DEV_0055&SUBSYS_B0031458&REV_F3\3&2411E6FE&0&40
   Driver: H:\WINDOWS\system32\DRIVERS\nvata.sys, 5.10.2600.0666 (English), 4/24/2006 20:52:28, 100736 bytes
   Driver: H:\WINDOWS\system32\idecoi.dll, 1.00.0000.0001 (English), 4/24/2006 20:52:30, 289792 bytes
   Driver: H:\WINDOWS\system32\idecoiins.dll, 1.00.0000.0001 (English), 4/24/2006 20:52:30, 289792 bytes
   Driver: H:\WINDOWS\system32\NVCOI.DLL, 1.00.0000.0035 (English), 4/14/2006 17:01:20, 35840 bytes

     Name: NVIDIA nForce4 Serial ATA Controller
Device ID: PCI\VEN_10DE&DEV_0054&SUBSYS_B0031458&REV_F3\3&2411E6FE&0&38
   Driver: H:\WINDOWS\system32\DRIVERS\nvata.sys, 5.10.2600.0666 (English), 4/24/2006 20:52:28, 100736 bytes
   Driver: H:\WINDOWS\system32\idecoi.dll, 1.00.0000.0001 (English), 4/24/2006 20:52:30, 289792 bytes
   Driver: H:\WINDOWS\system32\idecoiins.dll, 1.00.0000.0001 (English), 4/24/2006 20:52:30, 289792 bytes
   Driver: H:\WINDOWS\system32\NVCOI.DLL, 1.00.0000.0035 (English), 4/14/2006 17:01:20, 35840 bytes

     Name: Standard Dual Channel PCI IDE Controller
Device ID: PCI\VEN_10DE&DEV_0053&SUBSYS_50021458&REV_F2\3&2411E6FE&0&30
   Driver: H:\WINDOWS\system32\DRIVERS\pciidex.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 25088 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\atapi.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 95360 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\pciide.sys, 5.01.2600.0000 (English), 10/8/2004 08:01:47, 3328 bytes

     Name: SM Bus Controller
Device ID: PCI\VEN_10DE&DEV_0052&SUBSYS_0C111458&REV_A2\3&2411E6FE&0&09
   Driver: n/a

     Name: PCI standard ISA bridge
Device ID: PCI\VEN_10DE&DEV_0050&SUBSYS_00000000&REV_A3\3&2411E6FE&0&08
   Driver: H:\WINDOWS\system32\DRIVERS\isapnp.sys, 5.01.2600.0000 (English), 10/8/2004 08:01:47, 35840 bytes

     Name: Texas Instruments OHCI Compliant IEEE 1394 Host Controller
Device ID: PCI\VEN_104C&DEV_8024&SUBSYS_10001458&REV_00\4&13699180&0&5048
   Driver: H:\WINDOWS\system32\DRIVERS\ohci1394.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 61056 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\1394bus.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 53248 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\nic1394.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 61824 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\arp1394.sys, 5.01.2600.2180 (English), 10/8/2004 08:01:47, 60800 bytes
   Driver: H:\WINDOWS\system32\DRIVERS\enum1394.sys, 5.01.2600.0000 (English), 8/17/2001 09:46:40, 6400 bytes

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1103&SUBSYS_00000000&REV_00\3&2411E6FE&0&C3
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1102&SUBSYS_00000000&REV_00\3&2411E6FE&0&C2
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1101&SUBSYS_00000000&REV_00\3&2411E6FE&0&C1
   Driver: n/a

     Name: PCI standard host CPU bridge
Device ID: PCI\VEN_1022&DEV_1100&SUBSYS_00000000&REV_00\3&2411E6FE&0&C0
   Driver: n/a

------------------
DirectX Components
------------------
   ddraw.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 266240 bytes
 ddrawex.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 27136 bytes
   dxapi.sys: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 10496 bytes
    d3d8.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 1179648 bytes
 d3d8thk.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 8192 bytes
    d3d9.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 1689088 bytes
   d3dim.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 436224 bytes
d3dim700.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 825344 bytes
 d3dramp.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 590336 bytes
   d3drm.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 350208 bytes
  d3dxof.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 47616 bytes
d3dpmesh.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 34816 bytes
   dplay.dll: 5.00.2134.0001 English Final Retail 10/8/2004 08:01:47 33040 bytes
  dplayx.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 229888 bytes
dpmodemx.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 23552 bytes
 dpwsock.dll: 5.00.2134.0001 English Final Retail 10/8/2004 08:01:47 42768 bytes
dpwsockx.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 57344 bytes
dplaysvr.exe: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 30208 bytes
  dpnsvr.exe: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 18432 bytes
   dpnet.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 375296 bytes
dpnlobby.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 3584 bytes
 dpnaddr.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 3584 bytes
 dpvoice.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 212480 bytes
dpvsetup.exe: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 83456 bytes
  dpvvox.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 116736 bytes
  dpvacm.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 21504 bytes
dpnhpast.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 35328 bytes
dpnhupnp.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 60928 bytes
dpserial.dll: 5.00.2134.0001 English Final Retail 10/8/2004 08:01:47 53520 bytes
  dinput.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 159232 bytes
 dinput8.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 181760 bytes
   dimap.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 44032 bytes
diactfrm.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 394240 bytes
     joy.cpl: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 68608 bytes
   gcdef.dll: 5.01.2600.0000 English Final Retail 10/8/2004 08:01:47 76800 bytes
     pid.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 35328 bytes
  dsound.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 367616 bytes
dsound3d.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 1294336 bytes
  dswave.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 19456 bytes
   dsdmo.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 181760 bytes
dsdmoprp.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 71680 bytes
  dmusic.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 104448 bytes
  dmband.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 28672 bytes
dmcompos.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 61440 bytes
   dmime.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 181248 bytes
dmloader.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 35840 bytes
 dmstyle.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 105984 bytes
 dmsynth.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 103424 bytes
dmscript.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 82432 bytes
Microsoft.DirectX.Direct3D.dll: 9.05.0132.0000 English Final Retail 3/15/2008 18:22:46 473600 bytes
Microsoft.DirectX.Direct3DX.dll: 5.04.0000.3900 English Final Retail 3/15/2008 18:22:44 2676224 bytes
Microsoft.DirectX.Direct3DX.dll: 9.04.0091.0000 English Final Retail 3/15/2008 18:22:44 2846720 bytes
Microsoft.DirectX.Direct3DX.dll: 9.05.0132.0000 English Final Retail 3/15/2008 18:22:44 563712 bytes
Microsoft.DirectX.Direct3DX.dll: 9.06.0168.0000 English Final Retail 3/15/2008 18:22:44 567296 bytes
Microsoft.DirectX.Direct3DX.dll: 9.07.0239.0000 English Final Retail 3/15/2008 18:22:45 576000 bytes
Microsoft.DirectX.Direct3DX.dll: 9.08.0299.0000 English Final Retail 3/15/2008 18:22:45 577024 bytes
Microsoft.DirectX.Direct3DX.dll: 9.09.0376.0000 English Final Retail 3/15/2008 18:22:45 577536 bytes
Microsoft.DirectX.Direct3DX.dll: 9.10.0455.0000 English Final Retail 3/15/2008 18:22:45 577536 bytes
Microsoft.DirectX.Direct3DX.dll: 9.11.0519.0000 English Final Retail 3/15/2008 18:22:46 578560 bytes
Microsoft.DirectX.DirectDraw.dll: 5.04.0000.2904 English Final Retail 3/15/2008 18:22:46 145920 bytes
Microsoft.DirectX.DirectInput.dll: 5.04.0000.2904 English Final Retail 3/15/2008 18:22:46 159232 bytes
Microsoft.DirectX.DirectPlay.dll: 5.04.0000.2904 English Final Retail 3/15/2008 18:22:46 364544 bytes
Microsoft.DirectX.DirectSound.dll: 5.04.0000.2904 English Final Retail 3/15/2008 18:22:46 178176 bytes
Microsoft.DirectX.AudioVideoPlayback.dll: 5.04.0000.2904 English Final Retail 3/15/2008 18:22:46 53248 bytes
Microsoft.DirectX.Diagnostics.dll: 5.04.0000.2904 English Final Retail 3/15/2008 18:22:46 12800 bytes
Microsoft.DirectX.dll: 5.04.0000.2904 English Final Retail 3/15/2008 18:22:45 223232 bytes
   dx7vb.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 619008 bytes
   dx8vb.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 1227264 bytes
 dxdiagn.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 2113536 bytes
   mfc40.dll: 4.01.0000.6140 English Final Retail 10/8/2004 08:01:47 924432 bytes
   mfc42.dll: 6.02.4131.0000 English Final Retail 10/8/2004 08:01:47 1028096 bytes
 wsock32.dll: 5.01.2600.2180 English Final Retail 10/8/2004 08:01:47 22528 bytes
amstream.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 70656 bytes
 devenum.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 59904 bytes
  dxmasf.dll: 6.04.0009.1133 English Final Retail 8/22/2006 05:05:26 498742 bytes
mciqtz32.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 35328 bytes
 mpg2splt.ax: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 148992 bytes
   msdmo.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 14336 bytes
  encapi.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 20480 bytes
    qasf.dll: 9.00.0000.3250 English Final Retail 10/8/2004 08:01:47 237568 bytes
    qcap.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 192512 bytes
     qdv.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 279040 bytes
    qdvd.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 385024 bytes
   qedit.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 562176 bytes
qedwipes.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 733696 bytes
  quartz.dll: 6.05.2600.3243 English Final Retail 10/29/2007 18:43:03 1287680 bytes
 strmdll.dll: 4.01.0000.3936 English Final Retail 8/21/2006 10:52:08 246814 bytes
 iac25_32.ax: 2.00.0005.0053 English Final Retail 10/8/2004 08:01:47 199680 bytes
  ir41_32.ax: 4.51.0016.0003 English Final Retail 10/8/2004 08:01:47 848384 bytes
 ir41_qc.dll: 4.30.0062.0002 English Final Retail 10/8/2004 08:01:47 120320 bytes
ir41_qcx.dll: 4.30.0064.0001 English Final Retail 10/8/2004 08:01:47 338432 bytes
 ir50_32.dll: 5.2562.0015.0055 English Final Retail 10/8/2004 08:01:47 755200 bytes
 ir50_qc.dll: 5.00.0063.0048 English Final Retail 10/8/2004 08:01:47 200192 bytes
ir50_qcx.dll: 5.00.0064.0048 English Final Retail 10/8/2004 08:01:47 183808 bytes
   ivfsrc.ax: 5.10.0002.0051 English Final Retail 10/8/2004 08:01:47 154624 bytes
mswebdvd.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 204288 bytes
      ks.sys: 5.03.2600.2180 English Final Retail 8/4/2004 03:15:22 140928 bytes
  ksproxy.ax: 5.03.2600.2180 English Final Retail 8/4/2004 04:56:58 130048 bytes
  ksuser.dll: 5.03.2600.2180 English Final Retail 8/4/2004 04:56:44 4096 bytes
  stream.sys: 5.03.2600.2180 English Final Retail 8/4/2004 03:08:04 48640 bytes
mspclock.sys: 5.03.2600.2180 English Final Retail 8/3/2004 18:58:40 5376 bytes
   mspqm.sys: 5.01.2600.2180 English Final Retail 8/3/2004 18:58:42 4992 bytes
 mskssrv.sys: 5.03.2600.2180 English Final Retail 8/3/2004 18:58:42 7552 bytes
  swenum.sys: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 4352 bytes
mpeg2data.ax: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 118272 bytes
msvidctl.dll: 6.05.2600.2180 English Final Retail 10/8/2004 08:01:47 1428480 bytes
  vbisurf.ax: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 30720 bytes
   msyuv.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 17408 bytes
wstdecod.dll: 5.03.2600.2180 English Final Retail 10/8/2004 08:01:47 50688 bytes

------------------
DirectShow Filters
------------------

DirectShow Filters:
WMAudio Decoder DMO,0x00800800,1,1,,
WMSpeech Decoder DMO,0x00600800,1,1,,
Mpeg4s Decoder DMO,0x00800001,1,1,,
WMV Screen decoder DMO,0x00800001,1,1,,
WMVideo Decoder DMO,0x00800001,1,1,,
Mpeg43 Decoder DMO,0x00800001,1,1,,
Mpeg4 Decoder DMO,0x00800001,1,1,,
WMT MuxDeMux Filter,0x00200000,0,0,wmm2filt.dll,2.01.4026.0000
Creative LiveRecording Filter,0x00400000,0,1,LiveRec.ax,2.01.0001.0000
Full Screen Renderer,0x00200000,1,0,quartz.dll,6.05.2600.3243
Creative Wave Writer,0x00200000,1,0,WavWrite.ax,2.00.0001.0000
DV Muxer,0x00400000,0,0,qdv.dll,6.05.2600.2180
Creative MLP Source Filter,0x00400000,0,1,MlpSrc.ax,2.00.0000.0000
Color Space Converter,0x00400001,1,1,quartz.dll,6.05.2600.3243
WM ASF Reader,0x00400000,0,0,qasf.dll,9.00.0000.3250
Creative NVF Filter,0x00400000,0,1,NvfSrc.ax,1.00.0006.0000
AVI Splitter,0x00600000,1,1,quartz.dll,6.05.2600.3243
BPM Metadata,0x001fffff,1,1,MetaBPM.ax,1.00.0003.0000
WMT AudioAnalyzer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VGA 16 Color Ditherer,0x00400000,1,1,quartz.dll,6.05.2600.3243
Indeo® video 5.10 Compression Filter,0x00200000,1,1,ir50_32.dll,5.2562.0015.0055
Windows Media Audio Decoder,0x00800001,1,1,msadds32.ax,8.00.0000.4487
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
CT Null Render Filter,0x00200000,1,0,NullRndr.ax,1.00.0001.0000
WMT Format Conversion,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
CT Time-Scaling filter,0x00100000,1,1,TimeScal.ax,2.02.0000.0000
StreamBufferSink,0x00200000,0,0,sbe.dll,6.05.2600.2180
WMT Black Frame Generator,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MJPEG Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.3243
Indeo® video 5.10 Decompression Filter,0x00640000,1,1,ir50_32.dll,5.2562.0015.0055
WMT Screen Capture filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
SVM Metadata,0x001fffff,1,1,MetaSVM.ax,1.00.0006.0000
Microsoft Screen Video Decompressor,0x00800000,1,1,msscds32.ax,8.00.0000.4487
MPEG-I Stream Splitter,0x00600000,1,2,quartz.dll,6.05.2600.3243
SAMI (CC) Parser,0x00400000,1,1,quartz.dll,6.05.2600.3243
MPEG Layer-3 Decoder,0x00810000,1,1,l3codecx.ax,1.05.0000.0050
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,6.05.2600.2180
ACELP.net Sipro Lab Audio Decoder,0x00800001,1,1,acelpdec.ax,1.04.0000.0000
WMS Filter,0x00400000,0,1,CTWMSFLT.DLL,1.12.0001.0000
Internal Script Command Renderer,0x00800001,1,0,quartz.dll,6.05.2600.3243
MPEG Audio Decoder,0x03680001,1,1,quartz.dll,6.05.2600.3243
File Source (Netshow URL),0x00400000,0,1,wmpasf.dll,9.00.0000.3250
WMT Import Filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
DV Splitter,0x00600000,1,2,qdv.dll,6.05.2600.2180
Bitmap Generate,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Video Decoder,0x00800000,1,1,wmvds32.ax,8.00.0000.4487
Video Mixing Renderer 9,0x00200000,1,0,quartz.dll,6.05.2600.3243
Windows Media Video Decoder,0x00800000,1,1,wmv8ds32.ax,8.00.0000.4000
WMT VIH2 Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
PCM to EXT,0x00200000,0,0,Pcm2Ext.ax,5.00.0000.0000
Record Queue,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
CT Karaoke filter,0x00100000,1,1,Karaoke.ax,2.00.0000.0003
Creative MP3 Source Filter,0x00400000,0,1,Mp3Src.ax,2.00.0004.0000
Windows Media Multiplexer,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASX file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASX v.2 file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.3250
NSC file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ACM Wrapper,0x00600000,1,1,quartz.dll,6.05.2600.3243
Windows Media source filter,0x00600000,0,2,wmpasf.dll,9.00.0000.3250
Video Renderer,0x00800001,1,0,quartz.dll,6.05.2600.3243
Peak Follower Filter,0x001fffff,1,1,PassPeak.ax,1.00.0000.0003
Frame Eater,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,6.05.2600.2180
Line 21 Decoder,0x00600000,1,1,qdvd.dll,6.05.2600.2180
Video Port Manager,0x00600000,2,1,quartz.dll,6.05.2600.3243
WST Decoder,0x00600000,1,1,wstdecod.dll,5.03.2600.2180
Video Renderer,0x00400000,1,0,quartz.dll,6.05.2600.3243
Creative AC3 Source Filter,0x00400000,0,1,AC3Src.ax,1.01.0000.0000
CT SmartVolumeManagement filter,0x00100000,1,1,DSCompr.ax,1.00.0000.0001
WM ASF Writer,0x00400000,0,0,qasf.dll,9.00.0000.3250
WMT Sample Information Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,5.03.2600.2180
Creative MP3 Writer,0x00200000,1,0,MP3Write.ax,1.02.0001.0000
Microsoft MPEG-4 Video Decompressor,0x00800000,1,1,mpg4ds32.ax,8.00.0000.4487
File writer,0x00200000,1,0,qcap.dll,6.05.2600.2180
AudSkip Filter,0x001fffff,1,1,AudSkip.ax,1.00.0000.0003
WMT Log Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Virtual Renderer,0x00200000,1,0,wmm2filt.dll,2.01.4026.0000
DVD Navigator,0x00200000,0,2,qdvd.dll,6.05.2600.2180
Overlay Mixer2,0x00400000,1,1,qdvd.dll,6.05.2600.2180
AVI Draw,0x00600064,9,1,quartz.dll,6.05.2600.3243
.RAM file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.3250
WMT DirectX Transform Wrapper,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
G.711 Codec,0x00200000,1,1,g711codc.ax,5.01.2600.0000
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
DV Video Decoder,0x00800000,1,1,qdv.dll,6.05.2600.2180
Creative MP3 Source Filter,0x00400000,0,1,CTMP3SFT.DLL,1.00.0010.0000
Indeo® audio software,0x00500000,1,1,iac25_32.ax,2.00.0005.0053
Windows Media Update Filter,0x00400000,1,0,wmpasf.dll,9.00.0000.3250
Noise Reduction,0x00100000,1,1,NoisRedu.ax,3.00.0000.0002
ASF DIB Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF ACM Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF ICM Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF URL Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF JPEG Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF DJPEG Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASF embedded stuff Handler,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
9x8Resize,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WIA Stream Snapshot Filter,0x00200000,1,1,wiasf.ax,1.00.0000.0000
Allocator Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
SampleGrabber,0x00200000,1,1,qedit.dll,6.05.2600.2180
Null Renderer,0x00200000,1,0,qedit.dll,6.05.2600.2180
Creative WMA Writer,0x00200000,1,0,WMAWrite.ax,2.01.0001.0000
WMT Virtual Source,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
WMT Interlacer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
StreamBufferSource,0x00200000,0,0,sbe.dll,6.05.2600.2180
Smart Tee,0x00200000,1,2,qcap.dll,6.05.2600.2180
Creative WMA Source Filter,0x00400000,0,1,WmaSrc.ax,2.00.0004.0000
Overlay Mixer,0x00200000,0,0,qdvd.dll,6.05.2600.2180
AVI Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.3243
Uncompressed Domain Shot Detection Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
AVI/WAV File Source,0x00400000,0,2,quartz.dll,6.05.2600.3243
QuickTime Movie Parser,0x00600000,1,1,quartz.dll,6.05.2600.3243
Wave Parser,0x00400000,1,1,quartz.dll,6.05.2600.3243
MIDI Parser,0x00400000,1,1,quartz.dll,6.05.2600.3243
Multi-file Parser,0x00400000,1,1,quartz.dll,6.05.2600.3243
File stream renderer,0x00400000,1,1,quartz.dll,6.05.2600.3243
XML Playlist,0x00400000,1,0,wmpasf.dll,9.00.0000.3250
NVF Filter,0x00400000,0,1,CTNVFFLT.DLL,1.00.0000.0000
AVI Mux,0x00200000,1,0,qcap.dll,6.05.2600.2180
Line 21 Decoder 2,0x00600002,1,1,quartz.dll,6.05.2600.3243
File Source (Async.),0x00400000,0,1,quartz.dll,6.05.2600.3243
File Source (URL),0x00400000,0,1,quartz.dll,6.05.2600.3243
WMT DV Extract,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Creative CDDA Source Filter,0x00400000,0,1,CDDA.ax,2.01.0001.0000
WMT Switch Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Volume,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Stretch Video,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Infinite Pin Tee Filter,0x00200000,1,1,qcap.dll,6.05.2600.2180
QT Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.3243
MPEG Video Decoder,0x40000001,1,1,quartz.dll,6.05.2600.3243
Indeo® video 4.4 Decompression Filter,0x00640000,1,1,ir41_32.ax,4.51.0016.0003
Indeo® video 4.4 Compression Filter,0x00200000,1,1,ir41_32.ax,4.51.0016.0003

WDM Streaming Data Transforms:
Microsoft Kernel Acoustic Echo Canceller,0x00000000,0,0,,
Microsoft Kernel GS Wavetable Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DLS Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DRM Audio Descrambler,0x00200000,1,1,,5.03.2600.2180

Video Compressors:
MSScreen encoder DMO,0x00600800,1,1,,
DV Video Encoder,0x00200000,0,0,qdv.dll,6.05.2600.2180
Indeo® video 5.10 Compression Filter,0x00100000,1,1,ir50_32.dll,5.2562.0015.0055
MJPEG Compressor,0x00200000,0,0,quartz.dll,6.05.2600.3243
Cinepak Codec by Radius,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel 4:2:0 Video V2.50,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo(R) Video R3.2,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo® Video 4.5,0x00200000,1,1,qcap.dll,6.05.2600.2180
Indeo® video 5.10,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel IYUV codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.261 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.263 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft RLE,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft Video 1,0x00200000,1,1,qcap.dll,6.05.2600.2180
Xfire Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180

Audio Compressors:
IAC2,0x00200000,1,1,quartz.dll,6.05.2600.3243
IMA ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.3243
PCM,0x00200000,1,1,quartz.dll,6.05.2600.3243
Microsoft ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.3243
ACELP.net,0x00200000,1,1,quartz.dll,6.05.2600.3243
DSP Group TrueSpeech(TM),0x00200000,1,1,quartz.dll,6.05.2600.3243
Windows Media Audio V1,0x00200000,1,1,quartz.dll,6.05.2600.3243
Windows Media Audio V2,0x00200000,1,1,quartz.dll,6.05.2600.3243
GSM 6.10,0x00200000,1,1,quartz.dll,6.05.2600.3243
Microsoft G.723.1,0x00200000,1,1,quartz.dll,6.05.2600.3243
CCITT A-Law,0x00200000,1,1,quartz.dll,6.05.2600.3243
CCITT u-Law,0x00200000,1,1,quartz.dll,6.05.2600.3243
MPEG Layer-3,0x00200000,1,1,quartz.dll,6.05.2600.3243

Audio Capture Sources:
SB Audigy 2 Audio [9000],0x00200000,0,0,qcap.dll,6.05.2600.2180
AK5370          ,0x00200000,0,0,qcap.dll,6.05.2600.2180

Midi Renderers:
Default MidiOut Device,0x00800000,1,0,quartz.dll,6.05.2600.3243
Microsoft GS Wavetable SW Synth,0x00200000,1,0,quartz.dll,6.05.2600.3243
SB Audigy 2 Sw Synth [9000],0x00200000,1,0,quartz.dll,6.05.2600.3243
SB Audigy 2 Synth A [9000],0x00200000,1,0,quartz.dll,6.05.2600.3243
SB Audigy 2 Synth B [9000],0x00200000,1,0,quartz.dll,6.05.2600.3243

WDM Streaming Capture Devices:
SB Audigy 2 Audio [9000],0x00200000,3,2,,5.03.2600.2180
USB Audio Device,0x00200000,1,1,,5.03.2600.2180

WDM Streaming Rendering Devices:
SB Audigy 2 DirectMusic Synthesizer [9000],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Sw Synth [9000],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Synth A [9000],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Synth B [9000],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Audio [9000],0x00200000,3,2,,5.03.2600.2180

WDM Streaming Mixer Devices:
Microsoft Kernel Wave Audio Mixer,0x00000000,0,0,,

BDA CP/CA Filters:
Decrypt/Tag,0x00600000,1,0,encdec.dll,6.05.2600.2180
Encrypt/Tag,0x00200000,0,0,encdec.dll,6.05.2600.2180
XDS Codec,0x00200000,0,0,encdec.dll,6.05.2600.2180

Audio Renderers:
SB Audigy 2 Audio [9000],0x00200000,1,0,quartz.dll,6.05.2600.3243
Default DirectSound Device,0x00800000,1,0,quartz.dll,6.05.2600.3243
Default WaveOut Device,0x00200000,1,0,quartz.dll,6.05.2600.3243
DirectSound: SB Audigy 2 Audio [9000],0x00200000,1,0,quartz.dll,6.05.2600.3243

WDM Streaming System Devices:
SB Audigy 2 DirectMusic Synthesizer [9000],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Sw Synth [9000],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Synth A [9000],0x00200000,9,2,,5.03.2600.2180
SB Audigy 2 Synth B [9000],0x00200000,1,1,,5.03.2600.2180
SB Audigy 2 Audio [9000],0x00200000,11,2,,5.03.2600.2180
USB Audio Device,0x00200000,1,1,,5.03.2600.2180

---

### Post by hazza96 on 2008-04-05
It's really funny that you think that anyone here, except you, care about your Windows problems.

Here's a solution! Delete the Windows grub entry and format the Windows partition!

---

### Post by tamoneya on 2008-04-05
Then install Ubuntu Gusty Gibbon of course
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Dark_X on 2008-04-05
I know this is an Ubuntu forum but you guys sound like trolls.

---

### Post by chewearn on 2008-04-05
1. If you have simple Windows problem, most of the time, someone will help you in this forum.  That's the friendly spirit of this community.  However, for such complicated DirectX problem, it is very likely nobody here will know anything.

2. The post is extremely long, with the attached debug output; the OP didn't border to enclose them with code tags.  This is bad news, as most people will just read the first few sentences, skip the rest, and move on to the next thread.

3. If you don't feel like it, don't have the knowledge to help someone, or don't want to help someone's problem with <insert name> company product, please skip to the next thread.

:cool:

---

