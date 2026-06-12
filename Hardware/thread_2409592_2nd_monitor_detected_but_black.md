---
title: "2nd monitor detected but black"
date: 2019-01-04
forum: Hardware
---

### Post by gionzi on 2019-01-04
Hello,

I know probably the question has been already posted other times, but none of the solutions I found worked for me.

I have Ubuntu 16.04 LTS with kernel 4.4.0-141-generic .

So, the problem is that when I connect a second monitor to my notebook,  it's detected and connected, but it stays totally black (some monitors  give back some "no signal" messages). So if I go to System Setings ->  Displays I can see it's here, and effectively I can move the pointer of  my mouse on the other screen and even drag things from a screen to the  other only that the second stays always black. If I printscreen I see  both screens perfectly

From time to time (so absolutely not always) it works properly but only following these steps:
- I delete the ~/.config/monitors.xml 
- I reboot
- I connect the monitor after the log-in

If I disconnect the monitor and re-connect it again it doesn't work anymore.

Also it works when I set the lowest resolution possible for the second screen (but that's pretty annoying)

I strongly believe it's a software issue, because I tried to change  monitor, cable, way of connecting etc. but it's always the same. Also,  with the same hardware, it stopped working properly from a day to  another.

I report the xrandr output

```
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 294mm x 165mm
   1920x1080     60.00*+  59.93    48.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1368x768      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1280x720      60.00  
   1024x768      60.00  
   1024x576      60.00  
   960x540       60.00  
   800x600       60.32    56.25  
   864x486       60.00  
   640x480       59.94  
   720x405       60.00  
   640x360       60.00  
DP1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1440x900      74.98    59.89  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

and the ~/.config/monitors.xml 

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="eDP1">
          <vendor>SHP</vendor>
          <product>0x1484</product>
          <serial>0x00000000</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="DP1">
          <vendor>PHL</vendor>
          <product>0x08bb</product>
          <serial>0x00006758</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>1920</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DP2">
      </output>
      <output name="HDMI1">
      </output>
      <output name="HDMI2">
      </output>
      <output name="VIRTUAL1">
      </output>
  </configuration>
</monitors>
```

Whatever other output it's needed just ask and I'll provide it.

---

### Post by slickymaster on 2019-01-04
Thread moved to **Hardware** for a better fit

---

### Post by adrian-b on 2019-06-07
Hi

I'm having the same/similar issue. 
I have two dell 2715h monitors in mst mode, displayport1.2 enabled.

A fullscreen screenshot / printscreen will show both desktops, however the second monitor remains black.

Turning the second monitor on and off is correctly recognised without error however it always remains black....

xrandr:
```
Screen 0: minimum 320 x 200, current 5120 x 1440, maximum 16384 x 16384
DisplayPort-2 disconnected (normal left inverted right x axis y axis)
HDMI-A-2 disconnected (normal left inverted right x axis y axis)
DVI-D-2 disconnected (normal left inverted right x axis y axis)
DisplayPort-3 connected 2560x1440+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
   2048x1152     60.00  
   1920x1200     59.88  
   1920x1080     60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1200x960      59.99  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DisplayPort-4 connected 2560x1440+2560+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
   2048x1152     60.00  
   1920x1200     59.88  
   1920x1080     60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     75.02    60.02  
   1200x960      59.99  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  


```

some relevant dmesg outputs
```

[ 2109.473928] [drm] DELL U3818DW: [Block 0] 
[ 2109.473933] [drm] DELL U3818DW: [Block 1] 
[  2109.473939] [drm] dc_link_detect: manufacturer_id = AC10, product_id =  A0F3, serial_number = 3036474C, manufacture_week = 52, manufacture_year  = 27, display_name = DELL U3818DW, speaker_flag = 1, audio_mode_count =  1
[ 2109.473942] [drm] dc_link_detect: mode number = 0, format_code = 1, channel_count = 2, sample_rate = 7, sample_size = 7
[ 2109.489972] [drm] {3840x1600, 4000x1646@395000Khz}

```

uname -r
```
 4.15.0-51-generic
```

lspci for video cards
```
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Lexa PRO [Radeon RX 550/550X] (rev c7)
```


I'm starting to suspect the cable between the primary and secondary monitor might be the issue.... 

Is there anything obvious i'm missing?

Thanks

---

