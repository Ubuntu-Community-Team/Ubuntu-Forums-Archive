---
title: "Dell XPS 9550 - low resolution on external monitor"
date: 2017-07-12
forum: Hardware
---

### Post by white00lightning on 2017-07-12
Hi there!

I have a Dell XPS 9550. It has a 4K screen, which works great on Ubuntu. However, when I plug in an external 4K monitor (specifically, a [Kogan 28" 4K LED Monitor]("https://www.kogan.com/au/buy/kogan-28-ultra-hd-4k-led-monitor-ultra-hd/")), the highest resolution available is only 1920x1200. :(

Some info:


[LIST]
[*]Running Ubuntu 17.10 with kernel 4.10.0-26-generic
[*]Using HDMI cable that came with monitor
[*]Using nvidia-375.66 drivers
[/LIST]

I tried the steps outlined in [this AskUbuntu answer]("https://askubuntu.com/questions/448045/how-to-make-my-maximum-screen-resolution-to-be-detected-by-ubuntu/448113#448113"). A similar answer was also outlined [here]("https://askubuntu.com/questions/73007/cant-set-a-higher-screen-resolution-in-a-external-display-in-a-dell-mini-10v-la").[FONT=Ubuntu][COLOR=#111111]

[/COLOR][/FONT]Here's what I tried:

```
$ cvt 3840 2160
# 3840x2160 59.98 Hz (CVT 8.29M9) hsync: 134.18 kHz; pclk: 712.75 MHz
Modeline "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync
$ xrandr --newmode "3840x2160_60.00"  712.75  3840 4160 4576 5312  2160 2163 2168 2237 -hsync +vsync
$ xrandr --addmode HDMI-1-1 3840x2160_60.00
$ xrandr
Screen 0: minimum 8 x 8, current 5760 x 2160, maximum 16384 x 16384
eDP-1-1 connected 3840x2160+1920+0 (normal left inverted right x axis y axis) 346mm x 194mm
   3840x2160     60.00*+
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   1920x1200     59.95  
   1920x1080     59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
DP-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 880mm x 510mm
   1920x1200     59.95* 
   1920x1080     60.00  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    59.94  
   720x400       70.08  
   3840x2160_60.00  59.98  
DP-1-2 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 disconnected (normal left inverted right x axis y axis)
  3840x2160_60.00 (0x25f) 712.750MHz -HSync +VSync
        h: width  3840 start 4160 end 4576 total 5312 skew    0 clock 134.18KHz
        v: height 2160 start 2163 end 2168 total 2237           clock  59.98Hz

```[FONT=Ubuntu][COLOR=#111111]
[/COLOR][/FONT]
However when I try to select 3840x2160, my laptop screen becomes very stretched, and both the external & laptop screen start turning on/off repeatedly.

You can see what this looks like in [this image]("https://i.stack.imgur.com/pycDz.jpg").

I tried the **nouveau **drivers but they did not work either.

I also tried crying a little bit but that didn't help.

Any help on this would be greatly appreciated! :) If you need any more information please feel free to let me know. Thanks!

---

### Post by DuckHook on 2017-07-12
Welcome to the forums, white00lightning,

I am unfamiliar with your video specs, but if your HDMI port is anything less than v 1.2, it will not support 4K video. HDMI did not start supporting 4K until version 1.2. Your internal screen would not have any problems because it is not connected via HDMI.

To find what version your HDMI is, look at your documentation.

Connecting through DisplayPort will solve this issue.

---

### Post by white00lightning on 2017-07-12
Mate, you are an absolute GEM!

I was not aware of this. I did not think a high-end laptop with a 4K display of its own would not support 4K over HDMI!

The laptop doesn't have DisplayPort, however it does have USB Type-C so I've ordered an adapter off of eBay :)

---

### Post by DuckHook on 2017-07-13
Before springing for more equipment, make sure that the limitation is, indeed, the HDMI version. I would hate to see you buy something if the HDMI port is already version 1.2 and the problem is elsewhere. Also, I am unfamiliar with USB Type-C, but there may be issues with Linux support for this relatively new technology. You may wish to do some Googling and other research before springing for it.

---

### Post by vasa1 on 2017-07-13
> **DuckHook said:**
> ... Also, I am unfamiliar with USB Type-C, but there may be issues with Linux support for this relatively new technology. You may wish to do some Googling and other research before springing for it.
Nice to see you back :)

I recently bought a cheapo Dell laptop with Ubuntu pre-installed. It has two USB type C ports. So far, I don't have any USB device of that sort but sincerely hope that there's support for type C! Now to google!

---

### Post by white00lightning on 2017-07-13
> **DuckHook said:**
> Before springing for more equipment, make sure that the limitation is, indeed, the HDMI version. I would hate to see you buy something if the HDMI port is already version 1.2 and the problem is elsewhere. Also, I am unfamiliar with USB Type-C, but there may be issues with Linux support for this relatively new technology. You may wish to do some Googling and other research before springing for it.

I read a few forums online and this does seem to be the case:


[LIST]
[*][http://forum.notebookreview.com/threads/xps-9550-trouble-with-external-monitor-4k-60hz.801646/](http://forum.notebookreview.com/threads/xps-9550-trouble-with-external-monitor-4k-60hz.801646/)
[*][http://forum.notebookreview.com/threads/xps-15-9550-hdmi-2-0.786509/](http://forum.notebookreview.com/threads/xps-15-9550-hdmi-2-0.786509/)
[/LIST]

Unfortunately it does seem like it's a bit hit and miss getting an adapter to work with Linux, based on [this AskUbuntu answer]("https://askubuntu.com/questions/900517/usb-c-to-hdmi-and-ethernet-adaptors-how-to-evaluate-before-purchase-dell-xps"). Apparently the Hootoo shuttle works well

---

### Post by white00lightning on 2017-07-17
Just an update in case it's useful for posterity

I purchased the [Satechi Slim Aluminum Type-C Multi-Port Adapter]("https://www.ebay.com.au/itm/272598580352") off of eBay. I'm able to get 4k@30hz off of this in Ubuntu, but not 4k@60hz. This is a real bummer, however fortunately I just stare at lines of code all day long so it's still usable. I should thank my lucky stars it at least works!

Hopefully this will be fixed in a future update of the Nvidia drivers or Linux kernel. Usb Type C and 4K monitors are only getting more and more common

---

