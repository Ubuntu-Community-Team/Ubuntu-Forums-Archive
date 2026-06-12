---
title: "ThunderBolt 3 dock triple display"
date: 2019-11-06
forum: Hardware
---

### Post by fmaste on 2019-11-06
I have an [Intel® NUC Kit NUC8i7BEH]("https://ark.intel.com/content/www/us/en/ark/products/126140/intel-nuc-kit-nuc8i7beh.html") with an [Elgato Thunderbolt 3 Mini Dock]("https://www.elgato.com/en/dock/thunderbolt-3-mini") and I can't make it work with three simultaneous displays. The NUC says it supports three displays and the dock says that it supports two at the same time using a DisplayPort and an HDMI port.

I can only use two displays at the same time, the integrated HDMI of the NUC and only one of the ports of the dock, when I unplug one display from the dock the other becomes active instantaneously.

I am using Ubuntu 18.04.3 LTS with Linux 5.0.0-32-generic and the latests Intel BIOS.

The ThunderBolt device is active and in insecure/legacy mode on the BIOS (Dock's USB port works OK):

```

> sudo boltctl list
     &#9679; Elgato Systems Thunderbolt 3 Mini Dock
       &#9500;&#9472; type:          peripheral
       &#9500;&#9472; name:          Thunderbolt 3 Mini Dock
       &#9500;&#9472; vendor:        Elgato Systems
       &#9500;&#9472; uuid:          99999999-9999-9999-ffff-ffffffffffff
       &#9500;&#9472; status:        authorized
       &#9474;  &#9500;&#9472; domain:     domain0
       &#9474;  &#9492;&#9472; authflags:  none
       &#9500;&#9472; authorized:    Mon 01 Jan 2019 02:47:00 AM UTC
       &#9500;&#9472; connected:     Mon 01 Jan 2019 02:47:00 AM UTC
       &#9492;&#9472; stored:        Mon 01 Jan 2019 07:34:26 PM UTC
          &#9500;&#9472; policy:     manual
          &#9492;&#9472; key:        no

```

Xrandr has the same output with or without the dock plugged and output DP-2 is always the active display that is connected to the dock, even if it is using the HDMI port:

```

> xrandr
    Screen 0: minimum 320 x 200, current 3840 x 1200, maximum 8192 x 8192
    DP-1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 582mm x 364mm
       1920x1200     59.95*+
       1600x1200     60.00  
       1280x1024     75.02    60.02  
       1152x864      75.00  
       1024x768      75.03    60.00  
       800x600       75.00    60.32  
       640x480       75.00    59.94  
       720x400       70.08  
    DP-2 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 509mm x 286mm
       1920x1080     60.00*+
       1600x900      60.00  
       1280x1024     75.02    60.02  
       1152x864      75.00  
       1024x768      75.03    60.00  
       800x600       75.00    60.32  
       640x480       75.00    59.94  
       720x400       70.08  
    HDMI-1 disconnected (normal left inverted right x axis y axis)

```

Please any hint, advice is welcomed, I searched everywhere but I can't make it work. 

Thanks!!!

---

