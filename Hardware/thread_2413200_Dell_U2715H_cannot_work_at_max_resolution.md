---
title: "Dell U2715H cannot work at max resolution"
date: 2019-02-22
forum: Hardware
---

### Post by WDYSUN on 2019-02-22
Dear All

I am running Ubuntu 14.04 with nVidia GT 740 with proprietary drivers (version 304.137). I have a Dell U2715H connect over a proper HDMI cable. The problem is that the display does not run at full resolution, that is 2560x1440 60Hz.

This is the houtput of xrandr, as you see the max resolution is not recognized

```

**$ xrandr -q**

Screen 0: minimum 8 x 8, current 2048 x 1152, maximum 16384 x 16384
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 2048x1152+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2048x1152      60.0*+
   1920x1080      60.0     59.9     50.0     30.0     25.0     24.0     60.1     60.0     50.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1280x720       60.0     59.9     50.0  
   1200x960       60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     59.9     59.9  

```

The /var/log/Xorg.0.log contains several lines (I just list the tail of the file) where it says that the EDID information is not correct.

```

skipped lines
...
[  4468.238] (WW) NVIDIA(GPU-0): The EDID for DELL U2715H (DFP-1) contradicts itself: mode
[  4468.238] (WW) NVIDIA(GPU-0):     "1920x1080" is specified in the EDID; however, the EDID's
[  4468.238] (WW) NVIDIA(GPU-0):     valid VertRefresh range (56.000-86.000 Hz) would exclude
[  4468.238] (WW) NVIDIA(GPU-0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
[  4468.238] (WW) NVIDIA(GPU-0):     check for mode "1920x1080".

```


Then I tried to genereate a new xrandr mode with 

```

**$ gtf 2560 1440  60**

# 2560x1440 @ 60.00 Hz (GTF) hsync: 89.40 kHz; pclk: 311.83 MHz
Modeline "2560x1440_60.00"  311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync

```


but then it seems there is something wrong with generated parameters:

```

[B]$ xrandr --newmode "2560x1440_60"  311.83  2560 2744 3024 3488  1440 1441 1444 1490  -HSync +Vsync
[/B]
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  33
  Current serial number in output stream:  33

```


Any idea? Any experience like this?

Regards
Pierre

---

### Post by him610 on 2019-02-22
> proprietary drivers (version 304.137) This driver has been deprecated (abandoned) and is no longer included in LTS 18.04

Can not expect to get optimum performance with obsolete drivers (304.137)
Recommend you upgrade to LTS 16.04 or LTS 18.04

You should be using proprietary driver NVIDIA 390.77. I am using GTX 760 and GT 720, both with version 390.77 installed.
You can download more current driver from Settings>Additional Drivers.
You can adjust resolution using Settings>Nvidia X Server Settings.

---

### Post by WDYSUN on 2019-02-23
Hi mates

let me add that I managed to test the monitor connected to a Macbook pro 13 (2017) connected to the Dell U2715H via HDMI with USBC-HDMI Apple adapter. The Macbook synced to the dsiplay at the native max resolution without problmes. Therefore I would exclude that this is a monitor problem.

I hope somebody can help with Linux because this is the system that I use.

Regards
P

---

### Post by WDYSUN on 2019-02-23
Hello him610,

thanks for your reply, I haven't seen your before to post about the macbook test.

> **him610 said:**
> 
Can not expect to get optimum performance with obsolete drivers (304.137)
Recommend you upgrade to LTS 16.04 or LTS 18.04


I plan to install the LTS 18.08, but this machine does server work and I cannot do it before summertime.

> **him610 said:**
> 
You should be using proprietary driver NVIDIA 390.77. I am using GTX 760 and GT 720, both with version 390.77 installed.
You can download more current driver from Settings>Additional Drivers.
You can adjust resolution using Settings>Nvidia X Server Settings.


I'll try to install more recent drivers. Let see what happens.

Best
P

---

### Post by WDYSUN on 2019-02-23
Dear all,

I managed to solve the problem! I think something went wrong with   "ppa:graphics-drivers/ppa" repo. To be honest I was convinced to run the latest driver because I was using the ppa, but thanks to the hints from **him610**, I realized I was using an old obsolete driver. I did the following:

1.  first of all a disabled "ppa:graphics-drivers/ppa". 

2.  in software & updates > Ubuntu software: I made sure "proprietary drivers" was active

3. in software & updates >  Additional drievrs: I set the latest nvidia proprietary driver that reported "(tested)" flag. In my system the latest available was 384.130

4. from command line I removed all nvidia software with ```
**$ sudo apt-get purge nvidia* **
```  

5. from command line I update the package list:  ```
**$ sudo apt-get update **
```  

6. from command line I checked that the driver version 384.* was in the apt list:  ```
**$ sudo apt-cache search nvidia-* **
```  

7. since 6 was positive, then I installed the last driver:  ```
**$ sudo apt-get install nvidia-384**
```  

8. after rebooting I checked that the new driver module was correctly loaded: ```
**$ cat  /proc/driver/nvidia/version**
```

9. I opened the "NVIDIA X server Settings" application, and in "X Server Display Configuration" now the I am able to see max resolution! I set it and saved to the Xorg config file!

Now the display works wonderfully again!

Thanks to all, I hope this report can help future users!

Best 
P

---

