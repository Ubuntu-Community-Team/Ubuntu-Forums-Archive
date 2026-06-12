---
title: "Monitor Unknown Problem"
date: 2010-12-16
forum: Hardware
---

### Post by thisisme0610 on 2010-12-16
Team,

**Issue**: Display preferences shows "Unknown Monitor" and I can't increase resolution above 800x600.

**System and Hardware details**: 
Ubuntu : v10.10
Display Driver: Intel Corporation 845G Integrated Graphics Controller
Monitor : Samsung

**Details**: the resolution i am using is too small. i want to increase the resolution. when i am pressing the "Detect Monitors" it shows "unknown Monitor" also the resolution is restricted to 800x600.

Please help as I am new to Ubuntu!

---

### Post by Fafler on 2010-12-16
It sounds like a problem with the EDID data the monitor sends to the PC. Try another cable. Cheap cables sometimes doesn't work. If it doesn't corrects the problem, try making a Xorg.conf with this command:

```
sudo X -configure
sudo cp xorg.conf.new   /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf

```Edit the file and change Monitor and Screen sections to include this:

```
Section "Monitor"
    Identifier    "Generic Monitor"
HorizSync    30-71
    VertRefresh    50-160
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" 
    EndSubSection
EndSection
```

You can also include any other resolutions your monitor supports.

---

### Post by thisisme0610 on 2010-12-17
@Fafler
My monitor works fine in XP! So there is no issue of cheap cables!

I ran the first command as you suggested , I got the following error:
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

---

### Post by theasprint on 2010-12-17
Er, you may want to try getting the driver from Intel's website.

Get the Linux version of your driver from Intel's website,
then go off your Graphics mode by executing:

sudo /etc/init.d/gdm stop

and then go and install your driver by using 

sudo bash < the driver location>

and after everything's done, go and turn on your Graphics mode by executing:

sudo /etc/init.d/gdm start

Hopes this works.

*I had also a graphics problem on my Nvidia laptop with the resolution really low. All I did was to get my driver from the original website of your graphic card's producer and install the driver with the Graphics mode (gdm) turned off.

---

### Post by complience on 2010-12-17
I've got the same problem - only with the added benfit that im trying to run dual monitors.

The 2nd monitor is identified okay but the first primary monitor always comes up as unknown. 

so whenever I plug in the 2nd monitor its resolution configuration settings saved in Xorg are applied to the primary 'unknown' monitor as well..

Does anyone know how I can get xorg to apply the correct settings even to an unknown monitor.

help

---

### Post by IcarusR on 2010-12-17
Like Fafler said in an earlier post 

> It sounds like a problem with the EDID data the monitor sends to the PC

I had similar problem. Ext monitor would not work at highest supported resolutions. Logs are full of 

> kernel: [167596.361057] [drm:edid_is_valid] *ERROR* EDID checksum is invalid, remainder is 248
kernel: [167596.361064] [drm:edid_is_valid] *ERROR* Raw EDID:

I use xrandr via script to check if monitor is connected, if so creates correct resolution & switches to it after I login.
Still get error but monitor works @ 1280x1024

As for installing latest version of 'driver' from Intel website, I think you'll find that Xorg uses the latest stable version any way.
Nvidia drivers are very different, due to licensing Ububtu can not include them, hence the need to use 'Restricted Drivers' package .

---

### Post by markbl on 2010-12-17
I am getting this same problem as of today. "The EDID read for display device DFP-1 is invalid" in my Xorg log. My first screen is fine but the second screen is the same model as the first. This must be an nvidia driver regression?

---

### Post by markbl on 2010-12-19
> **markbl said:**
> I am getting this same problem as of today. "The EDID read for display device DFP-1 is invalid" in my Xorg log. My first screen is fine but the second screen is the same model as the first. This must be an nvidia driver regression?
PS Followup: Actually, I put my monitor on a windows box and it did not work there either. So it seems the monitor has suffered a hardware failure. I have another of the same monitor, so I exported the EDID from both using the nvidia-settings utility and noticed about 5 bytes of the 128 which seem corrupt (as the checksum now fails). I did a parse-edid on both but the printed output is exactly the same so I figured that whatever the corruption is, it must be trivial. I also found the same bytes were corrupted each time so it was a "consistent" failure. Also, if I boot with the good monitor, then swap it with the bad monitor after X is running, then the bad monitor works ok at native 1920x1200. Given this analysis, I merely added am option "IgnoreEDIDChecksum" DFP-1" to the Screen section of my twinview xorg.conf, and now my monitor is working ok :)

---

