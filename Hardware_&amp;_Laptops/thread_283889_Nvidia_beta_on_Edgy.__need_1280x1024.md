---
title: "Nvidia beta on Edgy.  need 1280x1024"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by BillGod on 2006-10-24
I just installed edgy from a clean install.  I cannot seem to get 1280x1024 resolution. I have tried nvidia-configure and was able to get 1280x800 at the login but as soon as gnome loads it reverses back to 1024x768.  I manually modified xorg.conf and removed all options but 1280x1024 and still cannot get the resolution.  I even set xorg.conf to 800x600 and it changed to 800x600.  I am running the beta driver for nvidia on edgy with beryl.  Here is my conf file.  if you see anything out of wack please let me know.

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Gateway"
    ModelName      "CRT-0"
    #HorizSync       28.0 - 51.0
    #VertRefresh     43.0 - 60.0
    HorizSync       35.0 - 60.0
    VertRefresh     50.0 - 70.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
         Modes      "1280x1024"
       # Modes      "800x600"
    EndSubSection
EndSection

---

### Post by Raphraphou on 2006-10-25
The is a problem with beta drivers, some resolutions cannot work. I have the same problem with the 1400*900. If you look at your log viewer, you can see that Ubuntu with Nvidia bypasses some resolutions even if you have put them in your xorg.conf...

---

### Post by Bachstelze on 2006-10-25
I was considering upgrading to Edgy but I guess I won't then, you guys spared me a lot of lost hair :D

---

### Post by tronica on 2006-10-25
> **HymnToLife said:**
> I was considering upgrading to Edgy but I guess I won't then, you guys spared me a lot of lost hair :D

As said above its with the drivers, not edgy. I run the beta drivers on edgy at 1280x1024 with not problems.

---

### Post by BillGod on 2006-11-01
I still do not have this working.  If anyone has an nvidia video card with 1280x1024 resolution working can you please post your xorg.conf file for me.

Thanks
Bill

---

### Post by BillGod on 2006-11-02
If anyone can even tell me if this is possible or not.  All I want is 1280 X 1024 resolution.  I have an nvidia 5200 and a 21 inch gateway crt.  I was running just fine on Dapper but the beta driver in Edgy does not seem to want it to happen.  I am getting this error in my xorg.0.log file "no valid modes for 1280x1024"  I have tried just about everything I can think of in my xorg.conf file but all i get is either 1024x768 or a blank screen.

---

### Post by BillGod on 2006-11-02
after looking on other forums I decided to keep playing with the refresh settings under monitor.  Bumped them up some more.. and shwablamo..  1280x1024

---

### Post by nan0dog on 2006-11-04
Could you post your working xorg.conf.  I can't get above 1024 x 768 for love nor money.  Tried modeline, altering xorg.conf, etc.  Very frustrating.  Exactly the same result for 8776 and beta proprietary nvidia drivers.  It works fine with the open source "nv" driver.  My lcd  monitors "natural" resolution is 1280x1024 and lower resolutions looks rubbish.  I think dccprobe or whatever the nvidia driver uses to scan the monitor is giving the wrong resolutions.

---

### Post by BillGod on 2006-11-09
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Gateway"
    ModelName      "VX1100"
    HorizSync       50.0 - 75.0
    VertRefresh     60.0 - 85.0
    Option         "DPMS"

EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    Option "AddARGBGLXVisuals" "True"

Option "UseEDID" "0"
Option "UseEDIDFreqs" "0"


EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
         Modes      "1280x1024_60"
     EndSubSection

---

### Post by Turgon on 2006-11-27
The Option "UseEDIDFreqs" "0" line did the tric for me.

Thank you!

---

### Post by Turpin on 2006-12-30
Same here.  Monitor's native res 1280x1024, with a NVidia 6800, but it won't go above 1024x768.  How do I get permissions to edit my xorg.conf file? It is the one in etc\x11, right?

---

### Post by tommcd on 2006-12-30
Bill God, 
why are you using nvidia's beta drivers with a nvidia 5200? You could just use the driver from the repos and it should work fine. I used to use a  nvidia 5200 in my Asus socket 754 rig and the driver from the repos gave me 1280x1024 resolution on my Samsung 930B LCD. I don't use Beryl though. Have you tried the driver from the repos?

---

