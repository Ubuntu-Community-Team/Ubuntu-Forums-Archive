---
title: "Adding a large ASUS monitor resolution"
date: 2013-06-22
forum: Hardware
---

### Post by abramdemski on 2013-06-22
I am trying to set up this monitor:

[http://commercial.asus.com/product/detail/vs247h-p-lcd-monitor](http://commercial.asus.com/product/detail/vs247h-p-lcd-monitor)

I am able to connect the monitor and use it in various screen configurations, but have not yet been able to set it to the correct 1:1 resolution.

The resolution listed for this monitor is 1920 x 1080. This does not appear as an option in the "Displays" GUI when I plug in a VGA cable. So, I attempted to follow the instructions here for adding resolutions:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

My attempt:

$ cvt 1920 1080

# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz Modeline "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync

$ xrandr --newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync

$ xrandr --addmode CRT1 1920x1080_60.00X Error of failed request: BadMatch (invalid parameter attributes) Major opcode of failed request: 156 (RANDR) Minor opcode of failed request: 18 (RRAddOutputMode) Serial number of failed request: 29 Current serial number in output stream: 30

The same thing happened with two different laptops.

In case it helps, this is what the output of xrandr looks like (for one of the laptops):

$ xrandr Screen 0: minimum 320 x 200, current 1366 x 768, maximum 1600 x 1600 LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm 1366x768 60.0*+ 1360x768 60.0
1280x768 60.0
1280x720 60.0
1024x768 60.0
1024x600 60.0
800x600 60.0
800x480 60.0
640x480 60.0
DFP1 disconnected (normal left inverted right x axis y axis) CRT1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm 1600x1200 60.0 + 1400x1050 60.0
1600x900 60.0
1280x1024 60.0
1440x900 59.9
1280x960 60.0
1360x768 60.0* 1280x800 59.8
1152x864 60.0
1280x768 59.9
1280x720 60.0
1024x768 60.0
1024x600 60.0
800x600 60.3
800x480 60.0
720x480 60.0
640x480 59.9
1920x1080_60.00 (0xef) 173.0MHz h: width 1920 start 2048 end 2248 total 2576 skew 0 clock 67.2KHz v: height 1080 start 1083 end 1088 total 1120 clock 60.0Hz

The "Displays" GUI gives the following error when I attempt to set up dual-monitor arrangements which would create virtual screens larger than 1600x1600:

"The selected configuration for displays could not be applied: requested position/size for CRTC 148 is outside the allowed limit: position=(1366, 0), size=(1360, 768), maximum=(1600, 1600)"

A maximum of 1600x1600 would rule out the correct resolution, so perhaps this has to do with the problem.

Any suggestions appreciated!

---

### Post by jp734 on 2013-06-23
My experience with this issue in the past is that I had to specify the HorizSync and VertRefresh rates on my xorg.conf file. Hope this will do the trick for you.

---

