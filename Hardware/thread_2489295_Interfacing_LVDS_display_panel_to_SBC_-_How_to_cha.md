---
title: "Interfacing LVDS display panel to SBC - How to change mapping from VESA to JEIDA 18"
date: 2023-07-25
forum: Hardware
---

### Post by mmiterli on 2023-07-25
First Ubuntu 22.04 install, please forgive me if I ask something stupid. 
I have an SBC with AMD GX424CC Soc processor. SBC has one HDMI, one VGA and one LVDS interface.  I tried to install a Nexus 7  1st gen LCD panel (800x1280) to the SBC's LVDS port. 

From HW point of view the install was OK. 

To complete the SW installation I need help. I was able to manage to get the resolutions right using xrandr command. 
Unfortunately the colors are not right, the full LCD screen is greenish, the texts are barely visible, see the attached picture.  
I suspect the pixel mapping used by the radeon driver by default is VESA and this LCD needs JEIDA 18 bit mapping. Worth to note the system is not recognize the LCD panel as LVDS panel, it recognize as DisplayPort-0. I am a bit sceptical about finding other driver: the default installed radeon driver is the right one for the AMD R5/R4 graphics system implemented in the SoC. If somebody has any suggestion how to proceed forward than please share with me. If you need more data please ask and I try to provide.  Thank you!

Data from the graphics subsystem:

.xrandr -q
Screen 0: minimum 320 x 200, current 2720 x 1280, maximum 16384 x 16384jpg
HDMI-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-0 connected 800x1280+1920+0 (normal left inverted right x axis y axis) 518mm x 333mm
   1280x800      59.91 +  49.92  
   800x1280_60.00  59.93* 
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     59.93*+
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x800      59.81  
   1024x768      60.00  
   800x600       60.32    56.25  
   640x480       59.94  


sudo lshw -c video
[sudo] password for mmiterli: 
  *-display                 
       description: VGA compatible controller
       product: Mullins [Radeon R4/R5 Graphics]-c video-c video-c video
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       logical name: /dev/fb0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=radeon latency=0 resolution=1920,1080
       resources: irq:51 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:fea00000-fea3ffff memory:c0000-dffff

glxinfo -B

name of display: :1
display: :1  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: AMD (0x1002)
    Device: KABINI (, LLVM 15.0.7, DRM 2.50, 5.19.0-50-generic) (0x9851)
    Version: 22.2.5
    Accelerated: yes
    Video memory: 512MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 4.5
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
Memory info (GL_ATI_meminfo):
    VBO free memory - total: 62 MB, largest block: 62 MB
    VBO free aux. memory - total: 2011 MB, largest block: 2011 MB
    Texture free memory - total: 62 MB, largest block: 62 MB
    Texture free aux. memory - total: 2011 MB, largest block: 2011 MB
    Renderbuffer free memory - total: 62 MB, largest block: 62 MB
    Renderbuffer free aux. memory - total: 2011 MB, largest block: 2011 MB
Memory info (GL_NVX_gpu_memory_info):
    Dedicated video memory: 512 MB
    Total available memory: 2555 MB
    Currently available dedicated video memory: 62 MB
OpenGL vendor string: AMD
OpenGL renderer string: KABINI (, LLVM 15.0.7, DRM 2.50, 5.19.0-50-generic)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 22.2.5-0ubuntu0.1~22.04.3
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile

OpenGL version string: 4.5 (Compatibility Profile) Mesa 22.2.5-0ubuntu0.1~22.04.3
OpenGL shading language version string: 4.50
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 22.2.5-0ubuntu0.1~22.04.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

---

### Post by mmiterli on 2023-07-25
Further data from X11 log:

   122.246] (II) RADEON(0): EDID for output DisplayPort-0
[   122.246] (II) RADEON(0): Manufacturer: CHR  Model: 7511  Serial#: 880
[   122.247] (II) RADEON(0): Year: 2011  Week: 21
[   122.247] (II) RADEON(0): EDID Version: 1.4
[   122.247] (II) RADEON(0): Digital Display Input
[   122.247] (II) RADEON(0): 6 bits per channel
[   122.247] (II) RADEON(0): Digital interface is DisplayPort
[   122.248] (II) RADEON(0): Indeterminate output size
[   122.248] (II) RADEON(0): Gamma: 2.20
[   122.248] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[   122.248] (II) RADEON(0): Supported color encodings: RGB 4:4:4 
[   122.248] (II) RADEON(0): First detailed timing is preferred mode
[   122.249] (II) RADEON(0): Preferred mode is native pixel format and refresh rate
[   122.249] (II) RADEON(0): redX: 0.674 redY: 0.316   greenX: 0.188 greenY: 0.703
[   122.249] (II) RADEON(0): blueX: 0.146 blueY: 0.062   whiteX: 0.312 whiteY: 0.326
[   122.249] (II) RADEON(0): Manufacturer's mask: 0
[   122.250] (II) RADEON(0): Supported detailed timing:
[   122.250] (II) RADEON(0): clock: 71.0 MHz   Image Size:  518 x 333 mm
[   122.250] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[   122.250] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[   122.250] (II) RADEON(0): Supported detailed timing:
[   122.250] (II) RADEON(0): clock: 59.2 MHz   Image Size:  518 x 333 mm
[   122.251] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[   122.251] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[   122.251] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[   122.252] (II) RADEON(0): Monitor name: CH7511B
[   122.252] (II) RADEON(0): EDID (in hex):
[   122.252] (II) RADEON(0):     00ffffffffffff000d12117570030000
[   122.252] (II) RADEON(0):     1515010495000078e28042ac5130b425
[   122.252] (II) RADEON(0):     10505300000001010101010101010101
[   122.252] (II) RADEON(0):     010101010101bc1b00a0502017303020
[   122.253] (II) RADEON(0):     3600064d2100001a1c1700a050201730
[   122.253] (II) RADEON(0):     30203600064d2100001a000000fd0038
[   122.253] (II) RADEON(0):     4c1e5311000a202020202020000000fc
[   122.253] (II) RADEON(0):     00434837353131420a20202020200057
[   122.254] (II) RADEON(0): Printing probed modes for output DisplayPort-0
[   122.254] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz eP)
[   122.254] (II) RADEON(0): Modeline "1280x800"x49.9   59.16  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (41.1 kHz e)

The LVDS driver IC is CH7511. I assume this IC is responsible for the final color mapping. The LCD resolution can be selected by a DIP Switch. As far as I understood the boot eprom of this IC should be pre programmed with the EDID data of the connected LCD.

Based on these I think the ubuntu side is OK, the CH7511 programming should be investigated.

---

### Post by mmiterli on 2023-07-27
Ok, further info on this project. Hard to find data on the CH7511. Chrontel is really preserving information about this chip. II found the following:

- find CH7511B Utility user guide. This document contains all the necessary information to be able to change all the parameters of the IC
- find the necessary CH7511B-Utility-xxxx.exe program. This is a windows program. Your SBC should be able to run windows. Install Windows and install this program with the drivers.
- the program is able to communicate with the chip via DP AUX. Both intel and AMD is supported.
- the default mode of bitmapping is SPWG. If you need than you can change it OpenLDI. In my case this needs to be done.
- you can define the EDID parameters to your display panel as well
- after do all the configuration steps you can export the code and load the new code to the chip with this utility. Trzy it in windows and modify the code if necessary.
- if it is working well in Windows than you can boot into Ubunu. If you need further adjustment regarding the resolution use xrandr command.

If you have access to CH7511B-Utility-xxxx.exe program please reply me, I was not able to find it by Google.

Good Luck to everyone who walking down on this path!

---

### Post by mmiterli on 2023-08-10
OK, found the problem. Green screen typically caused by broken FCP cables on LCD TVs. Gave an idea to check the cabling. As it turned out one of the LVDS line pair was short to each other. After removing the shorts the panel worked very well. As a saying is telling: can not see the forest because of one tree. How stupid was I am not to check the cabling after the soldering.

---

