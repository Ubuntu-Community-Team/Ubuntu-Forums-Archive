---
title: "Can't get Live CD to work for Demo or Installation"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by mindos on 2009-08-20
**In short** : I boot the CD , choose language, Test memory (results are fine); but other than that, whatever I choose, it just gives me blank screen with a blinking cursor in the top left corner..
**Same results with Ubuntu 9.04, Ubuntu 8.10 and Kubuntu 8.10 Live CDs**
-------------------------
I have been trying to search a solution for this issue, but haven't found one.
Feeling the need to nuke Win XP which is the only OS I have ever used, I need some help here..
-------------------------
(Newbie at installing OSes... Below is the history of these issues..)

I had tried to install Ubuntu 8.10 a few months ago. Installation was going fine, but because of a power failure my PC rebooted. Then if I tried to boot to Ubuntu Live CD, it gave me 'initramfs' errors.
**I finally gave up and completely formatted the whole partition I was trying to install Ubuntu on.**

I have formatted my PC for at least a couple of times since then, and want to make an effort to install Ubuntu.
**My PC has issues with booting directly from CD**, so I recently installed Acronis Disk Director which has a boot manager as well.
I chose to boot with Ubuntu Live CD, saw a screen with Language choices, pressed Enter key. Then, whatever option I choose ("Install Ubuntu", "Check CD for errors" etc.) , it leaves me with a blank screen with a blinking cursor.

Finally, I tried to install it in VirtualBox with Win XP SP2 as Host.
All went fine and every option I chose in the Live CD resulted fine..
[B]
I tried Kubuntu 8.10 a few hours ago. It booted, everything looked fine when I tried to run the Demo Install, it was showing KDE 4.1 and some icons below it were loading, but suddenly it stopped and gave a gibberish screen.
I rebooted and it gave same issues that i am having with Ubuntu.
[/B]
So, can someone diagnose the problem and suggest a way to solve it?


__________________________________________________
PC Configuration :
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

### Post by Mark Phelps on 2009-08-20
Unless someone here has the answer, you should go to the new Acronis forums and post your question there.  According to their documentation, what you're attempting to do should work.

See link below: 

[http://forum.acronis.com/]("http://forum.acronis.com/")

---

### Post by mindos on 2009-08-20
> **Mark Phelps said:**
> Unless someone here has the answer, you should go to the new Acronis forums and post your question there.  According to their documentation, what you're attempting to do should work.

See link below: 

[http://forum.acronis.com/](http://forum.acronis.com/)
I don't think it has anything to do with it. Its job is to help boot, and it did it successfully.

Whatever happened was when Live CD booted successfully and showed blank screen after choosing any of the options ("Install the CD", "Check CD for errors" etc.)

---

### Post by presence1960 on 2009-08-20
[boot options]("https://help.ubuntu.com/community/BootOptions")  scroll down to the section on F4 - & safe graphics mode. That is what you want to try when you boot the Live CD.

If that doesn't work try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

Sounds like your iso or the CD is no good. Do these before the above to verify iso & disk integrity:
[MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") your iso you burned the disk from.

Did you burn the iso as image at no more than 4x speed? If your burner software will not let you choose the burn speed see [this]("https://help.ubuntu.com/9.04/switching/installing-burning.html")

When you boot the Live CD select "check disk for errors"

---

### Post by mindos on 2009-08-21
> **presence1960 said:**
> [boot options]("https://help.ubuntu.com/community/BootOptions")  scroll down to the section on F4 - & safe graphics mode. That is what you want to try when you boot the Live CD.

If that doesn't work try the [alternate text based installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

Sounds like your iso or the CD is no good. Do these before the above to verify iso & disk integrity:
[MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") your iso you burned the disk from.

Did you burn the iso as image at no more than 4x speed? If your burner software will not let you choose the burn speed see [this]("https://help.ubuntu.com/9.04/switching/installing-burning.html")

When you boot the Live CD select "check disk for errors"
Firstly, thanks for your reply presence1960.
I did all of that. I used alternative installer, checked MD5sum, checked disk for errors from the Live CD.. But the problem is still there.

A couple of hours ago, installation completed successfully, but Ubuntu failed to Start up successfully. Giving the following messages in the Recovery mode :
```
[  1.097636]  isapnp: Scanning for PnP cards..
[  1.451707]  isapnp: No Plug & Play device found
[  1.453857]  Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[  1.454009]  serial 8250: ttys0 at I/O 0x3f8 (irq = 4) is a 16550A
[  1.454568]  00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  1.454745]  serial 0000:03:04.0 PCI INT A -> GSI 17 (level , low) -> IRQ 17
_
```

After a few reboots and a successful login and operation of Ubuntu, those commands reappear.

Can someone diagnose the problem here?

---

