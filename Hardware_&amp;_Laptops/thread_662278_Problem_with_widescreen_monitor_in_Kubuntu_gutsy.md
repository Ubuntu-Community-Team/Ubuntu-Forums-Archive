---
title: "Problem with widescreen monitor in Kubuntu gutsy"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by tospo on 2008-01-08
Hi,

I know this has been discussed a couple of times but none of the solutions I could find so far worked for me.
I bought a HP w2007v widescreen TFT monitor and on my dual boot machine it runs fine under Windows XP but I can't get the correct resolution in Kubuntu Gutsy.
My video card is an ATI Radeon x1650.

Among others (can't remember exactly everything I have tried now) I followed the instructions on the ATI Linux drivers wiki [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Specifically I did this as suggested:
```
sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

Then:

```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

as suggested.
I restarted the x server but I still get the same low resolution of 640 x 480 (and in the system settings menu I can only select 800 x 600 as an alternative).

The ATI driver seems to work according to fglrxinfo:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7170 Release
```

I tried to manually configure xorg.conf but that didn't help either. I tried three ways of getting the correct settings for my monitor from this website: [http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA)]("http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_(WSXGA)"):
Basically, first I got the settings from my Xorg.0.log file:

```
(II) fglrx(0): Connected Display1: CRT on secondary DAC [crt2]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: HWP  Model: 26a6  Serial#: 2147483648
(II) fglrx(0): Year: 2007  Week: 32
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
(II) fglrx(0): blueX: 0.150 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
(II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) fglrx(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 146.2 MHz   Image Size:  433 x 271 mm
(II) fglrx(0): h_active: 1680  h_sync: 1960  h_sync_end 2136 h_blank_end 2240 h_border: 0
(II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) fglrx(0): Ranges: V min: 55  V max: 76 Hz, H min: 24  H max: 83 kHz, PixClock max 170 MHz
(II) fglrx(0): Monitor name: HP w2007
(II) fglrx(0): Serial No: CNN7323SJ9
```

I changed the "Monitor" section of my xorg.conf file, adding this line derived from the "supported additional video modes" in the log file:

```
ModeLine        "1680x1050" 146.2 1680 1960 2136 2240 1050 1053 1059 1089
```

Rebooted and still got the same low resolution (and the correct options were still missing from the system settings GUI.

Than I downloaded read-edid to retrieve the information from the monitor and this is what I got:

```
$ sudo get-edid | parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0xc0250 "ATI ATOMBIOS"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call successful

parse-edid: EDID checksum passed.

        # EDID version 1 revision 3
Section "Monitor"
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "HP w2007"
        VendorName "HWP"
        ModelName "HP w2007"
        # Block type: 2:0 3:fd
        HorizSync 24-83
        VertRefresh 55-76
        # Max dot clock (video bandwidth) 170 MHz
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
        # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

        Mode    "1680x1050"     # vfreq 59.954Hz, hfreq 65.290kHz
                DotClock        146.250000
                HTimings        1680 1704 1880 2240
                VTimings        1050 1053 1059 1089
                Flags   "+HSync" "-VSync"
        EndMode
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:ff
EndSection
```

So I replaced the "Monitor" section in xorg.conf with the bit from Section "Monitor" to EndSection in the output and restarted - this time I got a black screen and I had to use recovery mode to change xorg.conf file back.
The last method was to calculate the values using gtf:

```
$ gtf 1680 1050 60

  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

```

and exchanging the Modeline in xorg.conf for the above. Again only the low resolution.

I am running out of things to try and would be very happy for any suggestions! The videocard and monitor work very well together in XP, so I really hope that it can be done in Gutsy too. Thanks in advance!

---

### Post by Dracheschreck on 2008-01-11
I have the SAME EXACT problems!!! Ati 9800pro.

I have a VW222S 22 inch screen. Native resolution is 1680x1050, and i CANT GET IT TO WORK! No matter what i try. Upon installation, Resolution was OK but the image was offset like 300 pixels to the right, so i had a black column to the left. It was weird.

After installing the ATI drivers (which report correctly when using fglrxinfo), resolution is totally stuck at 1600x1200, even after deleting every mode from xorg.conf except from 1680x1050. I dont know where does it get the 1600x1200 value from!.

If i try to configure my resolution using the screen properties dialog from KDE, (by choosing widescreen), it will change my xorg.conf a lot, and, after a reboot, it will show a black screen, (Since it adds a modeline line, just like tospo did.)

This is very strange and didnt happen on 7.04  >_<

---

### Post by Dracheschreck on 2008-01-11
I found the problem!

It's quite simple and we wouldn't have ever fixed: **Latest ATI drivers (7.12) wont work at these resolutions!!! **

Check the release notes:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_712_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_712_linux.html)


" Connecting a display device that supports 1680x1050 to a system running Linux may result in a maximum display resolution of 1280x1024 only being available "


**Download the previous version (7.11): **[http://ati.amd.com/support/drivers/linux/previous/linux-r-cat711.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-cat711.html)

---

### Post by tospo on 2008-01-11
Dracheschreck, you're a STAR!!!! :KS:KS:KS

I did what you suggested - after uninstalling the old (well actually the newer) ATI-drivers I downloaded the old version 7.11 from the URL you posted and chose automatic installation.
Then I ran these commands as root:
```
aticonfig --install
aticonfig --resolution=0,1680x1050

```
I rebooted and now when I go to the ATI-Catalyst control center I DO have the 1680 x 1050 option and the display is great. Now I only have one problem - the settings from the ATI Catalyst Control Center are not permanent, i.e. it reverts back to 640 x 480, which is still (along with 800 x 600) the only option that comes up in System Settings -> Monitor and Display.

My xorg.conf file looks like this now:
```
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1680x1050"
        EndSubSection
EndSection

```
which looks fine to me - why is this not loaded when the system starts up? :confused:

Thanks for your help!!!!

---

### Post by tospo on 2008-01-14
Just wanted to mention that the problem with having to reset the resolution is now solved. Please have a look at this thread:
[http://ubuntuforums.org/showthread.php?p=4135047#post4135047](http://ubuntuforums.org/showthread.php?p=4135047#post4135047)

In case the link doesn't work: I basically had to choose the "ATI Radeon (vesa)" driver and choose "Proprietary". This then gave me the option to select the correct screen resolution in the KDE Monitor & Display menu rather than in the ATI control center. These settings are now permanent.

---

