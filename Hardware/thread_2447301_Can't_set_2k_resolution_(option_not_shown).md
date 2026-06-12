---
title: "Can't set 2k resolution (option not shown)"
date: 2020-07-16
forum: Hardware
---

### Post by tomasch2 on 2020-07-16
Dear Ubuntu Community,

few weeks ago, I bought a new monitor. It is a BenQ PD2500Q. This screen has a WQHD resolution. My problem is, that my system only shows FHD as highest resolution possible (using Mini Display-Port). What can I do, to use the full resources of the monitor?

**My system:**
Notebook:
T430 (2349D17)
(external Monitor up to 2560×1600@60Hz [https://support.lenovo.com/us/en/solutions/pd024705](https://support.lenovo.com/us/en/solutions/pd024705))

CPU:
i5 3320M

GPU:
Nvidia NVS 5400M
Driver used: 
nvidia-diver-390.138

OS:
Ubuntu 20.04

I would be very grateful, if anyone could help my to solve this issue!
Thomas

---

### Post by Autodave on 2020-07-16
Where did you get the driver from?

---

### Post by tomasch2 on 2020-07-16
I'm using the driver which is proposed by ubuntu (software & Updates / Additional Drivers).

---

### Post by Autodave on 2020-07-16
Does the system recognize the monitor correctly when connected?  Have you tried another cable?

---

### Post by tomasch2 on 2020-07-16
Yes I tried to another cable, but nothing changed and ubuntu recognizes the monitor (e.g. Xorg.0.log)


May be there are some useful information in this ouput:
 xrandr --prop:```
tomas@tomas-ThinkPad-T430:~$ xrandr --prop
Screen 0: minimum 8 x 8, current 3520 x 1284, maximum 16384 x 16384
LVDS-0 connected primary 1600x900+0+384 (normal left inverted right x axis y axis) 309mm x 174mm
    _MUTTER_PRESENTATION_OUTPUT: 0
    EDID:
        00ffffffffffff0006af3e2100000000
        21140104901f11780261959c59528f26
        21505400000001010101010101010101
        010101010101f82a409a61840c30402a
        330035ae10000018a51c409a61840c30
        402a330035ae10000018000000fe0041
        554f0a202020202020202020000000fe
        004231343052573032205631200a00d0
    BorderDimensions: 4
        supported: 4
    Border: 0 0 0 0
        range: (0, 65535)
    SignalFormat: LVDS
        supported: LVDS
    ConnectorType: Panel
    ConnectorNumber: 0
    _ConnectorLocation: 0
    non-desktop: 0
        supported: 0, 1
   1600x900      60.01*+  40.00  
DP-0 disconnected (normal left inverted right x axis y axis)
    BorderDimensions: 4
        supported: 4
    Border: 0 0 0 0
        range: (0, 65535)
    SignalFormat: TMDS
        supported: TMDS
    ConnectorType: DisplayPort
    ConnectorNumber: 2
    _ConnectorLocation: 2
    non-desktop: 0
        supported: 0, 1
DP-1 disconnected (normal left inverted right x axis y axis)
    BorderDimensions: 4
        supported: 4
    Border: 0 0 0 0
        range: (0, 65535)
    SignalFormat: TMDS
        supported: TMDS
    ConnectorType: DisplayPort
    ConnectorNumber: 3
    _ConnectorLocation: 3
    non-desktop: 0
        supported: 0, 1
DP-2 disconnected (normal left inverted right x axis y axis)
    BorderDimensions: 4
        supported: 4
    Border: 0 0 0 0
        range: (0, 65535)
    SignalFormat: TMDS
        supported: TMDS
    ConnectorType: DisplayPort
    ConnectorNumber: 4
    _ConnectorLocation: 4
    non-desktop: 0
        supported: 0, 1
DP-3 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 550mm x 310mm
    _MUTTER_PRESENTATION_OUTPUT: 0
    EDID:
        00ffffffffffff0009d12a8045540000
        0f1e0104a5371f783e4455a9554d9d26
        0f5054256b80d1c0b300a9c081808100
        81c001010101565e00a0a0a029502f20
        350029372100001a000000ff0039344c
        30303239353031510a20000000fd0032
        4c1e5a19000a202020202020000000fc
        0042656e5120504432353030510a0159
        020323f150901f222120051404131211
        0302010706230907078301000065030c
        002000011d007251d01e206e28550029
        372100001e8c0ad08a20e02d10103e96
        002937210000188c0ad090204031200c
        4055002937210000188c0ad090204031
        200c4055002937210000180000000000
        000000000000000000000000000000e8
    BorderDimensions: 4
        supported: 4
    Border: 0 0 0 0
        range: (0, 65535)
    SignalFormat: DisplayPort
        supported: DisplayPort
    ConnectorType: DisplayPort
    ConnectorNumber: 2
    _ConnectorLocation: 2
    non-desktop: 0
        supported: 0, 1
   1920x1080     60.00 +  59.94*   50.00    29.97    25.00    23.98  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DP-4 disconnected (normal left inverted right x axis y axis)
    BorderDimensions: 4
        supported: 4
    Border: 0 0 0 0
        range: (0, 65535)
    SignalFormat: DisplayPort
        supported: DisplayPort
    ConnectorType: DisplayPort
    ConnectorNumber: 3
    _ConnectorLocation: 3
    non-desktop: 0
        supported: 0, 1
DP-5 disconnected (normal left inverted right x axis y axis)
    BorderDimensions: 4
        supported: 4
    Border: 0 0 0 0
        range: (0, 65535)
    SignalFormat: DisplayPort
        supported: DisplayPort
    ConnectorType: DisplayPort
    ConnectorNumber: 4
    _ConnectorLocation: 4
    non-desktop: 0
        supported: 0, 1

```

---

### Post by Holger_Gehrke on 2020-07-16
You might want to take a look at what the monitor has to say about itself. Install the package 'read-edid' and run 'get-edid|parse-edid'. This should tell you what the monitor tells the system about itself.

Holger

Edit: I believe you need to be a member of the group 'i2c' for read-edid to work ...

---

### Post by Yellow Pasque on 2020-07-16
Make sure the BenQ is set to DisplayPort 1.1 standard

---

### Post by tomasch2 on 2020-07-17
THANK YOU!!! 

The DisplayPort 1.1 standard is the solution of my issue! Default there was set the 1.2 standard. As soon I changed this setting at the BenQ, the 2560×1440 resolution was shown as option. Thank you very much to all of you who supported me!!!

Thomas

---

