---
title: "Ubuntu 7.10 cannot install on HP Pavillion n5210"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by taa23 on 2008-03-12
Hello all,

I have an HP n5210 Pavillion laptop which I am tring to install Ubuntu 7.10 Desktop on to.  I have tried all the Safe/VGA modes, and all I ever get is the orange splash screen with the mouse pointer inactive in the middle of it.

Does anyone know of a blacklist or any other command I can add to the initial install to get a completed install?

---

### Post by Fire_Chief on 2008-03-12
Are you getting the screen when attemping to boot the Live CD or after install? It would also help to have more details about your laptop (video card, RAM, CPU, etc.).

---

### Post by taa23 on 2008-03-12
Sorry, more detail is better.  I do not have it here with me to relay the specifications, but let me give you the symptoms.  It has Windows XP now.  I can insert the LiveCD and browse the content, and I can see the initial boot with the LiveCD.  Depending on on what options I select, I can see part of the splash/install screen with Ubuntu and the progress bar.  I then get to an orange desktop with my mouse, which will eventually stop responding.  There is no indication of any bars across the top or bottom, just orange desktop and an immobile mouse.  I have tried Ubuntu 6.04 6.10 7.04 7.10 with no success.

I will post the laptop's specifications later today.  Thanks!

---

### Post by taa23 on 2008-03-14
Because I cannot get Ubuntu installed on it (yet) here is the MS Diagnostic tool output:

------------------
System Information
------------------
Time of this report: 3/14/2008, 07:28:29
       Machine name: USER-1L60WSCFJD
   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.050301-1519)
           Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
       System Model: HP Pavilion Notebook PC
               BIOS: PhoenixBIOS 4.0 Release 6.0     
          Processor: Intel Celeron, ~640MHz
             Memory: 192MB RAM
          Page File: 219MB used, 247MB available
        Windows Dir: C:\WINDOWS
    DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
     DxDiag Version: 5.03.2600.2180 32bit Unicode

------------
DxDiag Notes
------------
  DirectX Files Tab: No problems found.
      Display Tab 1: Hardware-accelerated Direct3D 9 is not available because the display driver does not support it.  You may be able to get a newer driver from the hardware manufacturer.
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
        Card name: S3 Graphics Savage/IX HP
     Manufacturer: S3 Graphics, Inc.
        Chip type: S3 Savage/IX
         DAC type: S3 SDAC
       Device Key: Enum\PCI\VEN_5333&DEV_8C12&SUBSYS_0014103C&REV_11
   Display Memory: 4.0 MB
     Current Mode: 800 x 600 (32 bit) (60Hz)
          Monitor: Generic Television
  Monitor Max Res: 640,480
      Driver Name: s3gsavmx.dll
   Driver Version: 6.13.0010.7013 (English)
      DDI Version: 7
Driver Attributes: Final Retail
 Driver Date/Size: 8/24/2001 17:28:48, 258464 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: n/a
              VDD: n/a
         Mini VDD: s3gsavm.sys
    Mini VDD Date: 8/24/2001 17:29:02, 79296 bytes
Device Identifier: {D7B75DD3-CF52-11CF-E968-1E20B3C2CB35}
        Vendor ID: 0x5333
        Device ID: 0x8C12
        SubSys ID: 0x0014103C
      Revision ID: 0x0011
      Revision ID: 0x0011
      Video Accel: 
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
            Description: ESS Allegro
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: PCI\VEN_125D&DEV_1988&SUBSYS_0012103C&REV_12
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: es198x.sys
         Driver Version: 5.01.2526.0000 (English)
      Driver Attributes: Final Retail
            WHQL Logo'd: Yes
          Date and Size: 8/17/2001 04:19:48, 174464 bytes
            Other Files: 
        Driver Provider: Microsoft
         HW Accel Level: Full
              Cap Flags: 0xF5F
    Min/Max Sample Rate: 4800, 48000
Static/Strm HW Mix Bufs: 1, 0
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
            Description: ESS Allegro
  Default Sound Capture: Yes
  Default Voice Capture: Yes
            Driver Name: es198x.sys
         Driver Version: 5.01.2526.0000 (English)
      Driver Attributes: Final Retail
          Date and Size: 8/17/2001 04:19:48, 174464 bytes
              Cap Flags: 0x41
           Format Flags: 0xFFF

-----------
DirectMusic
-----------
        DLS Path: C:\WINDOWS\SYSTEM32\drivers\GM.DLS
     DLS Version: 1.00.0016.0002
    Acceleration: n/a
           Ports: Microsoft Synthesizer, Software (Not Kernel Mode), Output, DLS, Internal, Default Port
                  ESS Allegro, Software (Kernel Mode), Output, DLS, Internal
                  Microsoft MIDI Mapper [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
                  Microsoft GS Wavetable SW Synth [Emulated], Hardware (Not Kernel Mode), Output, No DLS, Internal
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
| Vendor/Product ID: 0x8086, 0x7112
| Matching Device ID: usb\root_hub
| Service: usbhub
| Driver: usbhub.sys, 8/3/2004 22:08:44, 57600 bytes
| Driver: usbd.sys, 8/23/2001 07:00:00, 4736 bytes

----------------
Gameport Devices
----------------

------------
PS/2 Devices
------------
+ Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
| Matching Device ID: *pnp0303
| Service: i8042prt
| Driver: i8042prt.sys, 8/3/2004 22:14:38, 52736 bytes
| Driver: kbdclass.sys, 8/3/2004 21:58:34, 24576 bytes
| 
+ Terminal Server Keyboard Driver
| Matching Device ID: root\rdp_kbd
| Upper Filters: kbdclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 00:01:08, 40840 bytes
| Driver: kbdclass.sys, 8/3/2004 21:58:34, 24576 bytes
| 
+ PS/2 Compatible Mouse
| Matching Device ID: *pnp0f13
| Service: i8042prt
| Driver: i8042prt.sys, 8/3/2004 22:14:38, 52736 bytes
| Driver: mouclass.sys, 8/3/2004 21:58:34, 23040 bytes
| 
+ Terminal Server Mouse Driver
| Matching Device ID: root\rdp_mou
| Upper Filters: mouclass
| Service: TermDD
| Driver: termdd.sys, 8/4/2004 00:01:08, 40840 bytes
| Driver: mouclass.sys, 8/3/2004 21:58:34, 23040 bytes

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
DirectPlay8 Modem Service Provider: ESS ES56CVM-PI Data Fax Voice Modem
DirectPlay8 Serial Service Provider: COM1
DirectPlay8 Serial Service Provider: COM3
DirectPlay8 TCP/IP Service Provider: Wireless Network Connection 3 - IPv4 - 

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
 Free Space: 4.6 GB
Total Space: 9.6 GB
File System: NTFS
      Model: IBM-DJSA-210

      Drive: D:
      Model: _NEC CD-2800D
     Driver: c:\windows\system32\drivers\cdrom.sys, 5.01.2600.2180 (English), 8/3/2004 21:59:54, 49536 bytes

--------------
System Devices
--------------
     Name: Intel 82443BX Pentium(R) II Processor to AGP Controller
Device ID: PCI\VEN_8086&DEV_7191&SUBSYS_00000000&REV_03\3&61AAA01&0&08
   Driver: C:\WINDOWS\system32\DRIVERS\AGP440.SYS, 5.01.2600.2180 (English), 8/3/2004 22:07:42, 42368 bytes

     Name: Intel 82443BX Pentium(r) II Processor to PCI Bridge
Device ID: PCI\VEN_8086&DEV_7190&SUBSYS_00000000&REV_03\3&61AAA01&0&00
   Driver: n/a

     Name: Intel(r) 82371AB/EB PCI to USB Universal Host Controller
Device ID: PCI\VEN_8086&DEV_7112&SUBSYS_00000000&REV_01\3&61AAA01&0&3A
   Driver: n/a

     Name: Intel(r) 82371AB/EB PCI Bus Master IDE Controller
Device ID: PCI\VEN_8086&DEV_7111&SUBSYS_00000000&REV_01\3&61AAA01&0&39
   Driver: n/a

     Name: Intel 82371AB/EB PCI to ISA bridge (ISA mode)
Device ID: PCI\VEN_8086&DEV_7110&SUBSYS_00000000&REV_02\3&61AAA01&0&38
   Driver: C:\WINDOWS\system32\DRIVERS\isapnp.sys, 5.01.2600.0000 (English), 8/23/2001 07:00:00, 35840 bytes

     Name: S3 Graphics Savage/IX HP
Device ID: PCI\VEN_5333&DEV_8C12&SUBSYS_0014103C&REV_11\4&415A68E&0&0808
   Driver: C:\WINDOWS\system32\DRIVERS\s3gsavm.sys, 6.13.0010.7013 (English), 8/24/2001 17:29:02, 79296 bytes
   Driver: C:\WINDOWS\system32\s3gsavmx.dll, 6.13.0010.7013 (English), 8/24/2001 17:28:48, 258464 bytes
   Driver: C:\WINDOWS\system32\s3hotkey.exe, 1.00.0000.0004 (English), 6/21/2001 11:33:44, 40960 bytes
   Driver: C:\WINDOWS\system32\Mxicd.dll, 2.10.0061.0000 (English), 8/28/2001 15:05:04, 700416 bytes
   Driver: C:\WINDOWS\help\S3Duoenu.hlp, 7/16/2001 11:41:54, 18605 bytes
   Driver: C:\WINDOWS\help\S3Duodan.hlp, 7/16/2001 11:41:54, 18890 bytes
   Driver: C:\WINDOWS\help\S3Duonld.hlp, 7/16/2001 11:41:56, 18944 bytes
   Driver: C:\WINDOWS\help\S3Duofra.hlp, 7/16/2001 11:41:56, 19412 bytes
   Driver: C:\WINDOWS\help\S3Duodeu.hlp, 7/16/2001 11:41:56, 19685 bytes
   Driver: C:\WINDOWS\help\S3Duoita.hlp, 7/16/2001 11:41:56, 18897 bytes
   Driver: C:\WINDOWS\help\S3Duojpn.hlp, 7/16/2001 11:41:56, 19484 bytes
   Driver: C:\WINDOWS\help\S3Duonor.hlp, 7/16/2001 11:41:58, 18859 bytes
   Driver: C:\WINDOWS\help\S3Duoptb.hlp, 7/16/2001 11:41:58, 18805 bytes
   Driver: C:\WINDOWS\help\S3Duochs.hlp, 7/16/2001 11:41:58, 18320 bytes
   Driver: C:\WINDOWS\help\S3Duocht.hlp, 7/16/2001 11:41:58, 18509 bytes
   Driver: C:\WINDOWS\help\S3Duoesp.hlp, 7/16/2001 11:41:58, 19361 bytes
   Driver: C:\WINDOWS\help\S3Duosve.hlp, 7/16/2001 11:41:58, 18655 bytes
   Driver: C:\WINDOWS\system32\S3DuoVue.dll, 1.00.0050.0710 (English), 7/16/2001 11:41:46, 221184 bytes
   Driver: C:\WINDOWS\system32\S3DuoVue.cfg, 7/16/2001 11:42:00, 49137 bytes
   Driver: C:\WINDOWS\system32\S3trayhp.exe, 2.00.0010.0706 (English), 7/16/2001 11:41:54, 73728 bytes
   Driver: C:\WINDOWS\help\S3Gamenu.hlp, 3/26/2001 13:06:56, 9140 bytes
   Driver: C:\WINDOWS\help\S3Gamdan.hlp, 3/26/2001 13:06:56, 9304 bytes
   Driver: C:\WINDOWS\help\S3Gamnld.hlp, 3/26/2001 13:06:58, 9235 bytes
   Driver: C:\WINDOWS\help\S3Gamfra.hlp, 3/26/2001 13:06:58, 9373 bytes
   Driver: C:\WINDOWS\help\S3Gamdeu.hlp, 3/26/2001 13:06:56, 9359 bytes
   Driver: C:\WINDOWS\help\S3Gamita.hlp, 3/26/2001 13:06:58, 9348 bytes
   Driver: C:\WINDOWS\help\S3Gamjpn.hlp, 3/26/2001 13:06:58, 9443 bytes
   Driver: C:\WINDOWS\help\S3Gamnor.hlp, 3/26/2001 13:06:58, 9197 bytes
   Driver: C:\WINDOWS\help\S3Gamptb.hlp, 3/26/2001 13:07:00, 9299 bytes
   Driver: C:\WINDOWS\help\S3Gamchs.hlp, 3/26/2001 13:06:56, 9238 bytes
   Driver: C:\WINDOWS\help\S3Gamcht.hlp, 3/26/2001 13:06:56, 9171 bytes
   Driver: C:\WINDOWS\help\S3Gamesp.hlp, 3/26/2001 13:07:00, 9284 bytes
   Driver: C:\WINDOWS\help\S3Gamsve.hlp, 3/26/2001 13:07:00, 9266 bytes
   Driver: C:\WINDOWS\system32\S3Gamma.dll, 1.02.0013.0326 (English), 3/26/2001 11:01:06, 135168 bytes
   Driver: C:\WINDOWS\S3Gamma.cfg, 3/26/2001 13:07:04, 9022 bytes
   Driver: C:\WINDOWS\system32\S3uninst.exe, 1.00.0007.0115 (English), 1/15/2001 16:10:32, 61440 bytes

     Name: Airlink101 802.11g CardBus Adapter #2
Device ID: PCI\VEN_1814&DEV_0301&SUBSYS_001217F9&REV_00\4&2C9BC48C&0&0021
   Driver: C:\WINDOWS\system32\DRIVERS\RT61.sys, 1.00.0003.0000 (English), 10/27/2005 14:06:30, 356096 bytes

     Name: ESS ES56CVM-PI Data Fax Voice Modem
Device ID: PCI\VEN_125D&DEV_1989&SUBSYS_0012103C&REV_12\3&61AAA01&0&41
   Driver: n/a

     Name: ESS Allegro PCI Audio (WDM)
Device ID: PCI\VEN_125D&DEV_1988&SUBSYS_0012103C&REV_12\3&61AAA01&0&40
   Driver: n/a

     Name: Texas Instruments PCI-1420 CardBus Controller
Device ID: PCI\VEN_104C&DEV_AC51&SUBSYS_0014103C&REV_00\3&61AAA01&0&21
   Driver: C:\WINDOWS\system32\DRIVERS\pcmcia.sys, 5.01.2600.2180 (English), 8/3/2004 22:07:48, 119936 bytes

     Name: Texas Instruments PCI-1420 CardBus Controller
Device ID: PCI\VEN_104C&DEV_AC51&SUBSYS_0014103C&REV_00\3&61AAA01&0&20
   Driver: C:\WINDOWS\system32\DRIVERS\pcmcia.sys, 5.01.2600.2180 (English), 8/3/2004 22:07:48, 119936 bytes

------------------
DirectX Components
------------------
   ddraw.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 266240 bytes
 ddrawex.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 27136 bytes
   dxapi.sys: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 10496 bytes
    d3d8.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:42 1179648 bytes
 d3d8thk.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:42 8192 bytes
    d3d9.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:42 1689088 bytes
   d3dim.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 436224 bytes
d3dim700.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:42 825344 bytes
 d3dramp.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 590336 bytes
   d3drm.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 350208 bytes
  d3dxof.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 47616 bytes
d3dpmesh.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 34816 bytes
   dplay.dll: 5.00.2134.0001 English Final Retail 8/23/2001 07:00:00 33040 bytes
  dplayx.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 229888 bytes
dpmodemx.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 23552 bytes
 dpwsock.dll: 5.00.2134.0001 English Final Retail 8/23/2001 07:00:00 42768 bytes
dpwsockx.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 57344 bytes
dplaysvr.exe: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:50 30208 bytes
  dpnsvr.exe: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:50 18432 bytes
   dpnet.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 375296 bytes
dpnlobby.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:04 3584 bytes
 dpnaddr.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:04 3584 bytes
 dpvoice.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 212480 bytes
dpvsetup.exe: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:50 83456 bytes
  dpvvox.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 116736 bytes
  dpvacm.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 21504 bytes
dpnhpast.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 35328 bytes
dpnhupnp.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 60928 bytes
dpserial.dll: 5.00.2134.0001 English Final Retail 8/23/2001 07:00:00 53520 bytes
  dinput.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 159232 bytes
 dinput8.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 181760 bytes
   dimap.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 44032 bytes
diactfrm.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 394240 bytes
     joy.cpl: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:58 68608 bytes
   gcdef.dll: 5.01.2600.0000 English Final Retail 8/23/2001 07:00:00 76800 bytes
     pid.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:46 35328 bytes
  dsound.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 367616 bytes
dsound3d.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 1294336 bytes
  dswave.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 19456 bytes
   dsdmo.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 181760 bytes
dsdmoprp.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 71680 bytes
  dmusic.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 104448 bytes
  dmband.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 28672 bytes
dmcompos.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 61440 bytes
   dmime.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 181248 bytes
dmloader.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 35840 bytes
 dmstyle.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 105984 bytes
 dmsynth.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 103424 bytes
dmscript.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 82432 bytes
   dx7vb.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 619008 bytes
   dx8vb.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 1227264 bytes
 dxdiagn.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 2113536 bytes
   mfc40.dll: 4.01.0000.6140 English Final Retail 8/23/2001 07:00:00 924432 bytes
   mfc42.dll: 6.02.4131.0000 English Final Retail 8/3/2004 23:56:44 1028096 bytes
 wsock32.dll: 5.01.2600.2180 English Final Retail 8/3/2004 23:56:48 22528 bytes
amstream.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:42 70656 bytes
 devenum.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:44 59904 bytes
  dxmasf.dll: 6.04.0009.1133 English Final Retail 8/22/2006 04:05:26 498742 bytes
mciqtz32.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:44 35328 bytes
 mpg2splt.ax: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:58 148992 bytes
   msdmo.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:44 14336 bytes
  encapi.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 20480 bytes
    qasf.dll: 9.00.0000.3250 English Final Retail 8/3/2004 23:56:46 237568 bytes
    qcap.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:46 192512 bytes
     qdv.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:46 279040 bytes
    qdvd.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:46 385024 bytes
   qedit.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:46 562176 bytes
qedwipes.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:26 733696 bytes
  quartz.dll: 6.05.2600.2749 English Final Retail 8/29/2005 19:54:26 1287168 bytes
 strmdll.dll: 4.01.0000.3936 English Final Retail 8/21/2006 09:52:08 246814 bytes
 iac25_32.ax: 2.00.0005.0053 English Final Retail 8/3/2004 23:56:58 199680 bytes
  ir41_32.ax: 4.51.0016.0003 English Final Retail 8/3/2004 23:56:58 848384 bytes
 ir41_qc.dll: 4.30.0062.0002 English Final Retail 8/3/2004 23:56:44 120320 bytes
ir41_qcx.dll: 4.30.0064.0001 English Final Retail 8/3/2004 23:56:44 338432 bytes
 ir50_32.dll: 5.2562.0015.0055 English Final Retail 8/3/2004 23:56:44 755200 bytes
 ir50_qc.dll: 5.00.0063.0048 English Final Retail 8/3/2004 23:56:44 200192 bytes
ir50_qcx.dll: 5.00.0064.0048 English Final Retail 8/3/2004 23:56:44 183808 bytes
   ivfsrc.ax: 5.10.0002.0051 English Final Retail 8/3/2004 23:56:58 154624 bytes
mswebdvd.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:46 204288 bytes
      ks.sys: 5.03.2600.2180 English Final Retail 8/3/2004 22:15:22 140928 bytes
  ksproxy.ax: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:58 130048 bytes
  ksuser.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:44 4096 bytes
  stream.sys: 5.03.2600.2180 English Final Retail 8/3/2004 22:08:04 48640 bytes
mspclock.sys: 5.03.2600.2180 English Final Retail 8/3/2004 21:58:40 5376 bytes
   mspqm.sys: 5.01.2600.2180 English Final Retail 8/3/2004 21:58:42 4992 bytes
 mskssrv.sys: 5.03.2600.2180 English Final Retail 8/3/2004 21:58:42 7552 bytes
  swenum.sys: 5.03.2600.2180 English Final Retail 8/3/2004 21:58:42 4352 bytes
mpeg2data.ax: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:58 118272 bytes
msvidctl.dll: 6.05.2600.2180 English Final Retail 8/3/2004 23:56:44 1428480 bytes
  vbisurf.ax: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:58 30720 bytes
   msyuv.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:46 17408 bytes
wstdecod.dll: 5.03.2600.2180 English Final Retail 8/3/2004 23:56:48 50688 bytes

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
Full Screen Renderer,0x00200000,1,0,quartz.dll,6.05.2600.2749
DV Muxer,0x00400000,0,0,qdv.dll,6.05.2600.2180
Color Space Converter,0x00400001,1,1,quartz.dll,6.05.2600.2749
WM ASF Reader,0x00400000,0,0,qasf.dll,9.00.0000.3250
AVI Splitter,0x00600000,1,1,quartz.dll,6.05.2600.2749
WMT AudioAnalyzer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VGA 16 Color Ditherer,0x00400000,1,1,quartz.dll,6.05.2600.2749
Indeo® video 5.10 Compression Filter,0x00200000,1,1,ir50_32.dll,5.2562.0015.0055
Windows Media Audio Decoder,0x00800001,1,1,msadds32.ax,8.00.0000.4487
AC3 Parser Filter,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
WMT Format Conversion,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
StreamBufferSink,0x00200000,0,0,sbe.dll,
WMT Black Frame Generator,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MJPEG Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2749
Indeo® video 5.10 Decompression Filter,0x00640000,1,1,ir50_32.dll,5.2562.0015.0055
WMT Screen Capture filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
Microsoft Screen Video Decompressor,0x00800000,1,1,msscds32.ax,8.00.0000.4487
MPEG-I Stream Splitter,0x00600000,1,2,quartz.dll,6.05.2600.2749
SAMI (CC) Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
MPEG Layer-3 Decoder,0x00810000,1,1,l3codecx.ax,1.05.0000.0050
MPEG-2 Splitter,0x005fffff,1,0,mpg2splt.ax,6.05.2600.2180
ACELP.net Sipro Lab Audio Decoder,0x00800001,1,1,acelpdec.ax,1.04.0000.0000
Internal Script Command Renderer,0x00800001,1,0,quartz.dll,6.05.2600.2749
MPEG Audio Decoder,0x03680001,1,1,quartz.dll,6.05.2600.2749
File Source (Netshow URL),0x00400000,0,1,wmpasf.dll,9.00.0000.3250
WMT Import Filter,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
DV Splitter,0x00600000,1,2,qdv.dll,6.05.2600.2180
Bitmap Generate,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Video Decoder,0x00800000,1,1,wmvds32.ax,8.00.0000.4487
Video Mixing Renderer 9,0x00200000,1,0,quartz.dll,
Windows Media Video Decoder,0x00800000,1,1,wmv8ds32.ax,8.00.0000.4000
WMT VIH2 Fix,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Record Queue,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Multiplexer,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASX file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ASX v.2 file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.3250
NSC file Parser,0x00600000,1,1,wmpasf.dll,9.00.0000.3250
ACM Wrapper,0x00600000,1,1,quartz.dll,6.05.2600.2749
Windows Media source filter,0x00600000,0,2,wmpasf.dll,9.00.0000.3250
Video Renderer,0x00800001,1,0,quartz.dll,6.05.2600.2749
Frame Eater,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
MPEG-2 Video Stream Analyzer,0x00200000,0,0,sbe.dll,
Line 21 Decoder,0x00600000,1,1,qdvd.dll,6.05.2600.2180
Video Port Manager,0x00600000,2,1,quartz.dll,6.05.2600.2749
WST Decoder,0x00600000,1,1,wstdecod.dll,5.03.2600.2180
Video Renderer,0x00400000,1,0,quartz.dll,6.05.2600.2749
WM ASF Writer,0x00400000,0,0,qasf.dll,9.00.0000.3250
WMT Sample Information Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
VBI Surface Allocator,0x00600000,1,1,vbisurf.ax,5.03.2600.2180
Microsoft MPEG-4 Video Decompressor,0x00800000,1,1,mpg4ds32.ax,8.00.0000.4487
File writer,0x00200000,1,0,qcap.dll,6.05.2600.2180
WMT Log Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Virtual Renderer,0x00200000,1,0,wmm2filt.dll,2.01.4026.0000
DVD Navigator,0x00200000,0,2,qdvd.dll,6.05.2600.2180
Overlay Mixer2,0x00400000,1,1,qdvd.dll,6.05.2600.2180
AVI Draw,0x00600064,9,1,quartz.dll,6.05.2600.2749
.RAM file Parser,0x00600000,1,0,wmpasf.dll,9.00.0000.3250
WMT DirectX Transform Wrapper,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
G.711 Codec,0x00200000,1,1,g711codc.ax,5.01.2600.0000
MPEG-2 Demultiplexer,0x00600000,1,1,mpg2splt.ax,6.05.2600.2180
DV Video Decoder,0x00800000,1,1,qdv.dll,6.05.2600.2180
Indeo® audio software,0x00500000,1,1,iac25_32.ax,2.00.0005.0053
Windows Media Update Filter,0x00400000,1,0,wmpasf.dll,9.00.0000.3250
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
WMT Virtual Source,0x00200000,0,1,wmm2filt.dll,2.01.4026.0000
MPEG-2 Sections and Tables,0x005fffff,1,0,mpeg2data.ax,
IVF source filter,0x00600000,0,1,ivfsrc.ax,5.10.0002.0051
WMT Interlacer,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
StreamBufferSource,0x00200000,0,0,sbe.dll,
Smart Tee,0x00200000,1,2,qcap.dll,6.05.2600.2180
Overlay Mixer,0x00200000,0,0,qdvd.dll,6.05.2600.2180
AVI Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2749
Uncompressed Domain Shot Detection Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
AVI/WAV File Source,0x00400000,0,2,quartz.dll,6.05.2600.2749
QuickTime Movie Parser,0x00600000,1,1,quartz.dll,6.05.2600.2749
Wave Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
MIDI Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
Multi-file Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
Lyric Parser,0x00400000,1,1,quartz.dll,6.05.2600.2749
File stream renderer,0x00400000,1,1,quartz.dll,6.05.2600.2749
XML Playlist,0x00400000,1,0,wmpasf.dll,9.00.0000.3250
AVI Mux,0x00200000,1,0,qcap.dll,6.05.2600.2180
Line 21 Decoder 2,0x00600002,1,1,quartz.dll,6.05.2600.2749
File Source (Async.),0x00400000,0,1,quartz.dll,6.05.2600.2749
File Source (URL),0x00400000,0,1,quartz.dll,6.05.2600.2749
WMT DV Extract,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Switch Filter,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
WMT Volume,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Stretch Video,0x00200000,1,1,wmm2filt.dll,2.01.4026.0000
Windows Media Pad VU Data Grabber,0x00600000,1,0,wmmfilt.dll,1.01.2427.0000
Infinite Pin Tee Filter,0x00200000,1,1,qcap.dll,6.05.2600.2180
QT Decompressor,0x00600000,1,1,quartz.dll,6.05.2600.2749
ShotBoundaryDet,0x00200000,1,1,wmmfilt.dll,1.01.2427.0000
MPEG Video Decoder,0x40000001,1,1,quartz.dll,6.05.2600.2749
Indeo® video 4.4 Decompression Filter,0x00640000,1,1,ir41_32.ax,4.51.0016.0003
Indeo® video 4.4 Compression Filter,0x00200000,1,1,ir41_32.ax,4.51.0016.0003

WDM Streaming Data Transforms:
Microsoft Kernel Acoustic Echo Canceller,0x00200000,2,2,,5.03.2600.2180
Microsoft Kernel GS Wavetable Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DLS Synthesizer,0x00200000,1,1,,5.03.2600.2180
Microsoft Kernel DRM Audio Descrambler,0x00200000,1,1,,5.03.2600.2180

Video Compressors:
WMVideo Encoder DMO,0x00600800,1,1,,
MSScreen encoder DMO,0x00600800,1,1,,
WMVideo9 Encoder DMO,0x00600800,1,1,,
MSScreen 9 encoder DMO,0x00600800,1,1,,
DV Video Encoder,0x00200000,0,0,qdv.dll,6.05.2600.2180
Indeo® video 5.10 Compression Filter,0x00100000,1,1,ir50_32.dll,5.2562.0015.0055
MJPEG Compressor,0x00200000,0,0,quartz.dll,6.05.2600.2749
Cinepak Codec by Radius,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel 4:2:0 Video V2.50,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo(R) Video R3.2,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel Indeo® Video 4.5,0x00200000,1,1,qcap.dll,6.05.2600.2180
Indeo® video 5.10,0x00200000,1,1,qcap.dll,6.05.2600.2180
Intel IYUV codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.261 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft H.263 Video Codec,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft MPEG-4 Video Codec V2,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft MPEG-4 Video Codec V1,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft RLE,0x00200000,1,1,qcap.dll,6.05.2600.2180
Microsoft Video 1,0x00200000,1,1,qcap.dll,6.05.2600.2180

Audio Compressors:
WM Speech Encoder DMO,0x00600800,1,1,,
WMAudio Encoder DMO,0x00600800,1,1,,
IAC2,0x00200000,1,1,quartz.dll,6.05.2600.2749
IMA ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.2749
PCM,0x00200000,1,1,quartz.dll,6.05.2600.2749
Microsoft ADPCM,0x00200000,1,1,quartz.dll,6.05.2600.2749
ACELP.net,0x00200000,1,1,quartz.dll,6.05.2600.2749
DSP Group TrueSpeech(TM),0x00200000,1,1,quartz.dll,6.05.2600.2749
Windows Media Audio V1,0x00200000,1,1,quartz.dll,6.05.2600.2749
Windows Media Audio V2,0x00200000,1,1,quartz.dll,6.05.2600.2749
GSM 6.10,0x00200000,1,1,quartz.dll,6.05.2600.2749
Microsoft G.723.1,0x00200000,1,1,quartz.dll,6.05.2600.2749
CCITT A-Law,0x00200000,1,1,quartz.dll,6.05.2600.2749
CCITT u-Law,0x00200000,1,1,quartz.dll,6.05.2600.2749
MPEG Layer-3,0x00200000,1,1,quartz.dll,6.05.2600.2749

Audio Capture Sources:
ESS Allegro,0x00200000,0,0,qcap.dll,6.05.2600.2180

Midi Renderers:
Default MidiOut Device,0x00800000,1,0,quartz.dll,6.05.2600.2749
Microsoft GS Wavetable SW Synth,0x00200000,1,0,quartz.dll,6.05.2600.2749

WDM Streaming Capture Devices:
ESS Allegro,0x00200000,2,2,,5.03.2600.2180

WDM Streaming Rendering Devices:
ESS Allegro,0x00200000,2,2,,5.03.2600.2180

BDA Transport Information Renderers:
MPEG-2 Sections and Tables,0x00600000,1,0,mpeg2data.ax,

WDM Streaming Mixer Devices:
Microsoft Kernel Wave Audio Mixer,0x00200000,2,2,,5.03.2600.2180

BDA CP/CA Filters:
Decrypt/Tag,0x00600000,1,0,encdec.dll,
Encrypt/Tag,0x00200000,0,0,encdec.dll,
XDS Codec,0x00200000,0,0,encdec.dll,

Audio Renderers:
ESS Allegro,0x00200000,1,0,quartz.dll,6.05.2600.2749
Default DirectSound Device,0x00800000,1,0,quartz.dll,6.05.2600.2749
Default WaveOut Device,0x00200000,1,0,quartz.dll,6.05.2600.2749
DirectSound: ESS Allegro,0x00200000,1,0,quartz.dll,6.05.2600.2749

WDM Streaming System Devices:
ESS Allegro,0x00200000,22,2,,5.03.2600.2180

---

### Post by sandysandy on 2008-03-14
have u tried the ubuntu alternate CD.

here is the link to download it

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

i could never install with Ubuntu live CD on desktop (Intel Pentium D 3.00 GHz machine).

but was successful with alternate CD.

regards

---

### Post by smurphy_it on 2008-03-14
Yes I'd recommend trying the alternate CD as well.  When it comes to installing it though, if you stats were picked up properly in Windows, you have 192MB RAM and 633+ Celeron processor.

With those specs i'd probably try a lower end Desktop Manager like XFCE, Fluxbox etc....

If you install Xubuntu that has the XFCE interface in it by default.

---

### Post by taa23 on 2008-03-15
The xubuntu cd seems to install correctly, thank you for the idea!  Now I need to get the awlc3026t wireless card working.

Thank you all for the assistance!

---

