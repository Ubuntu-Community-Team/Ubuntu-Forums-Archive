---
title: "Ubuntu 12.04 Fresh install First Screen 800x600"
date: 2014-02-02
forum: Hardware
---

### Post by ducky108 on 2014-02-02
I use an Nvidia Gtx 660 My first monitor is an HL272HPB 27" 1080p and number 2 is an old acer 1440x1040

The Second monitor works just fine and the first one works in 800X600 and if i use the hdmi is displays the proper resolution and EDID hmm. 

i have managed to get my edid from windows via phoenix but im not exactly sure what to do that that its saved as a .edd file

Code: get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "NVIDIA"

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
    Call failed

The EDID data should not be trusted as the VBE call failed
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

    # EDID version 0 revision 16
Section "Monitor"
    # Block type: 2:9e 3:2
    # Block type: 2:1e 3:1
    # Block type: 2:9e 3:2
    # Block type: 2:1e 3:0
    Identifier "A@R:0104"
    VendorName "A@R"
    ModelName "A@R:0104"
    # Block type: 2:9e 3:2
    # Block type: 2:1e 3:1
    # Block type: 2:9e 3:2
    # Block type: 2:1e 3:0
    # DPMS capabilities: Active off:no  Suspend:no  Standby:yes

    # Block type: 2:9e 3:2
    # Block type: 2:1e 3:1
    # Block type: 2:9e 3:2
    # Block type: 2:1e 3:0
EndSection




Xrandr Is this

Code: Screen 0: minimum 8 x 8, current 2240 x 900, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+
HDMI-0 connected 1440x900+800+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1440x900       75.0*+   59.9  
   1360x765       60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DP-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

---

