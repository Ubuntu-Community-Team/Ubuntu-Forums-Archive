---
title: "Nvidia gtx 780 + 13.04"
date: 2013-07-10
forum: Hardware
---

### Post by rlockwood88 on 2013-07-10
Hi guys, first time coming back to Ubuntu in a few years and really confused.

Firstly I have a few identical systems with an Intel 3770k and 2x NVIDIA GTX 780s. The cards are used purely for GPGPU under windows and everything has been working okayish.

I decided to give Linux a try as I thought it would be a bit more stable when running compared to the Win8 installation which crashes and restarts every 48 hours while running GPGPU.

Now The monitor is plugged into the on-bored Intel GPU and Linux installs fine, I get to the desktop and start setting what I need up but there's no NVIDIA drivers listed under "Additional Drivers" like there used to be. If I run lscpi I can see all my cards identified although incorrectly (GK110 NVIDIA TITAN) so I assume the system knows they're there. I need drivers though to actually be able to run calculations on them.

However, when I install the NVIDIA drivers either from the offical .run file or 
```

sudo add-apt-repository ppa:xorg-edgers/ppasudo apt-get update
sudo apt-get install nvidia-319

```

The installation goes fine but when the system reboots I have no GUI... just the desktop image. CTRL+ALT+T works to bring up the terminal but I'm at a loss on what to do from there... Unity or whatever it is just seems to suck and can't realise that although I have the NVIDIA drivers installed I want display output through the Intel GPU.

I've tried a handful of random Googled solutions but none of them seem to work... can you guys offer any assistance? Win8 costs me every time it crashes!

---

### Post by Cavsfan on 2013-07-11
> **rlockwood88 said:**
> Hi guys, first time coming back to Ubuntu in a few years and really confused.

Firstly I have a few identical systems with an Intel 3770k and 2x NVIDIA GTX 780s. The cards are used purely for GPGPU under windows and everything has been working okayish.

I decided to give Linux a try as I thought it would be a bit more stable when running compared to the Win8 installation which crashes and restarts every 48 hours while running GPGPU.

Now The monitor is plugged into the on-bored Intel GPU and Linux installs fine, I get to the desktop and start setting what I need up but there's no NVIDIA drivers listed under "Additional Drivers" like there used to be. If I run lscpi I can see all my cards identified although incorrectly (GK110 NVIDIA TITAN) so I assume the system knows they're there. I need drivers though to actually be able to run calculations on them.

However, when I install the NVIDIA drivers either from the offical .run file or 
```

sudo add-apt-repository ppa:xorg-edgers/ppasudo apt-get update
sudo apt-get install nvidia-319

```

The installation goes fine but when the system reboots I have no GUI... just the desktop image. CTRL+ALT+T works to bring up the terminal but I'm at a loss on what to do from there... Unity or whatever it is just seems to suck and can't realise that although I have the NVIDIA drivers installed I want display output through the Intel GPU.

I've tried a handful of random Googled solutions but none of them seem to work... can you guys offer any assistance? Win8 costs me every time it crashes!

You have a typo for starters:

```
sudo add-apt-repository ppa:xorg-edgers/ppasudo apt-get update
sudo apt-get install nvidia-319
```

Should be 
```
sudo add-apt-repository ppa:xorg-edgers/ppa  
sudo apt-get update 
sudo apt-get install nvidia-319 nvidia-settings-319 nvidia-persistenced libvdpau1
```

You need the driver (nvidia-319) as well as the Tool for configuring the NVIDIA graphics driver (nvidia-settings-319). The 2 files go hand in hand and the other 2 are dependencies.
This should be what you need. Just enter these command and reboot and you should be good to go. 

If you don't like unity and want to install gnome fallback just enter this:

```
sudo apt-get install gnome-session-fallback
```

Then when you login click on the circle and change it from Ubuntu (default) to Gnome Fallback.

[http://www.liberiangeek.net/2013/04/no-unity-here-enable-classic-gnome-in-ubuntu-13-04/](http://www.liberiangeek.net/2013/04/no-unity-here-enable-classic-gnome-in-ubuntu-13-04/)

Edit: nvidia-persistenced and libvdpau1 are also required.

You might want to select nvidia-319 and nvidia-settings-319 through Synaptic as it wll pull in the depenencies. But, the above commands should also work.
I just updated from 310.30 to 319.32 with SPM and those are the files that it installed and it went well.

---

### Post by rlockwood88 on 2013-07-11
Thanks, tried that and other work arounds.

Still boots with nothing but a desktop image whenever nVidia drivers are installed.

I assume it's got a lot to do with me not using the Graphics card output, but instead the integrated output. 

Either way, don't have the patience.

Thanks for your assistance.

---

### Post by Cavsfan on 2013-07-12
> **rlockwood88 said:**
> Thanks, tried that and other work arounds.

Still boots with nothing but a desktop image whenever nVidia drivers are installed.

I assume it's got a lot to do with me not using the Graphics card output, but instead the integrated output. 

Either way, don't have the patience.

Thanks for your assistance.

Yup that integrated video will cause you problems. My son has a pretty decent laptop with an Nvidia GTX 670 and if he plugs it in before bootup it uses the Nvidia card if he doesn't it uses the integrated output.
Maybe plugging it in is all you need to do.

---

### Post by Vivek_Saxena on 2013-08-01
Did using the stock drivers from NVIDIA help you? See [http://www.phoronix.com/scan.php?page=news_item&px=MTM3Nzg](http://www.phoronix.com/scan.php?page=news_item&px=MTM3Nzg).

I've got the same card and have been struggling to get it to work for the past 3 days :confused:

---

### Post by Yellow Pasque on 2013-08-01
> **rlockwood88 said:**
> Still boots with nothing but a desktop image whenever nVidia drivers are installed.

That's because the nvidia drivers use a different libGL than the open-source Intel driver, so installing the nvidia drivers the standard way will bork the intel card's 3D...
There's probably a waay to do what you want, but I'm not sure off the top of my head.

---

### Post by Cavsfan on 2013-08-01
If you bootup a laptop while it's unplugged, it will not use the Nvidia card but the integrated graphics instead.
If you bootup a laptop while it is plugged in, it will use the Nvidia card/drivers. 

It just has to be plugged in upon boot to install any nvidia driver and be able to use it.

---

### Post by Yellow Pasque on 2013-08-01
@Cavsfan, we're discussing desktop cards here. Also, that's not how Optimus works on Linux...

---

### Post by Cavsfan on 2013-08-01
> **Temüjin said:**
> @Cavsfan, we're discussing desktop cards here. Also, that's not how Optimus works on Linux...

My bad. I didn't know a desktop pc could have integrated along with an Nvidia card. I thought the OP had to be talking about a laptop.

---

### Post by Vivek_Saxena on 2013-08-01
> **Vivek_Saxena said:**
> Did using the stock drivers from NVIDIA help you? See [http://www.phoronix.com/scan.php?page=news_item&px=MTM3Nzg](http://www.phoronix.com/scan.php?page=news_item&px=MTM3Nzg).

I've got the same card and have been struggling to get it to work for the past 3 days :confused:

Okay, so I can first tell you that nvidia-325 **will** get your GTX780 to run.

BUT,  if you want to work with CUDA, then any attempt to install it will  prompt you to remove nvidia-325 and install nvidia-304 or  nvidia-current. Is there a fix for this?

---

### Post by fetuspuppet on 2014-02-16
So I was digging through this stuff all morning - I'm on 13.10 with two Nvidia GTX 780 Ti cards, each connected to a single monitor on the HDMI port. Major overkill, but I am going to be doing a ton of rendering soon.

Anyhow I played around all morning and kept having Xinerama errors, problems figuring out which display was correct, black areas where there shouldn't be.

I black listed the nouveau and nvidia drivers provided by ubuntu. I then uninstalled xorg completely and ran the binary installer from nvidia.

Both cards still would not work - so I grabbed a config from sudo nvidia-settings output and started playing with it.

Eventually I came up with this config which has both screens working with gnome-desktop and seems to be functional:

(code)
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 334.16  (buildmeister@swio-display-x64-rhel04-03)  Tue Feb  4 14:50:08 PST 2014

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" Rightof "Screen0" 
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC EA231WMi"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AT3265"
    HorizSync       30.0 - 75.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 780 Ti"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 780 Ti"
    BusID          "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-1"
#    Option         "metamodes" "nvidia-auto-select +0+0"
#    Option         "SLI" "1"
#    Option         "MultiGPU" "1"
    Option         "BaseMosaic" "on"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
#    Option         "metamodes" "nvidia-auto-select +0+0"
#    Option         "SLI" "1"
#    Option         "MultiGPU" "1"
    Option         "BaseMosaic" "on"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


(code)

---

