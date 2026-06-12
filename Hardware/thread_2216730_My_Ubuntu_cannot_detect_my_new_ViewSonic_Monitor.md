---
title: "My Ubuntu cannot detect my new ViewSonic Monitor"
date: 2014-04-13
forum: Hardware
---

### Post by Raghavendra_Ghatag on 2014-04-13
I have a HP xw4400 Workstation with Ubuntu 12.04 installed. 
I seem to have a "Gallium 0.4 on NV44" graphics card.
I used to have a Samsung 15" montior with this PC and it worked fine.
I wanted to replace my small monitor with a bigger one and hence I bought a ViewSonic VA1931wma-LED 19" montor and tried to connect it to my PC.
But the problem is that my Ubuntu is not detecting this monitor at all. My computer starts but there is no display, the screen just shows the error message "No Signal". I search through the internet to find some clue, I could only get to understand that Ubuntu should have detected it by default. Even if the resolution is not proper, there should have been some display. But in my case, the monitor is as if not connected at all. As soon as I disconnect my new monitor and connect the old one, I can see the display on it. But not on the new one.

Please help me to configure this new monitor.

---

### Post by gifford on 2014-04-13
Welcome to the forum!
Could you open your terminal and post the results of this command: [COLOR=#333333]lspci -nn | grep VGA


[/COLOR]

---

### Post by Raghavendra_Ghatag on 2014-04-13
Below is the result of running this command [COLOR=#333333]lspci -nn | grep VGA[/COLOR]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV44 [Quadro NVS 285] [10de:0165] (rev a1)

---

### Post by gifford on 2014-04-14
It looks like you are running the open source driver. Run this command to be sure: [FONT=Ubuntu Mono]lshw -c video
It will indicate what driver you are using.
It may be that you need to install the proprietary driver but it looks like your graphics card is a little underpowered.
It has either 64 or 128mb of memory.

[/FONT]

---

### Post by Raghavendra_Ghatag on 2014-04-15
Hi gifford,
Here is the output of running the command [COLOR=#000000][FONT=Ubuntu Mono]lshw -c video[/FONT][/COLOR]
  *-display               
       description: VGA compatible controller
       product: NV44 [Quadro NVS 285]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:e9000000-e9ffffff memory:e0000000-e7ffffff memory:ea000000-eaffffff memory:e8000000-e801ffff


Please let me know if there is something about my graphics card or it is something else.

---

### Post by bazsound on 2014-04-15
Sounds an unsupported resolution issue.

You can try installing the propriety driver using jockey

If you are back in your GUI open up additiona drivers (usually under system settings)

Let it do its thing searching, and activate the recomended driver.

If your stuck at a command prompt, you can use jockey-text

Once its installed, restart and hopefully the driver will detect the monitor.

If not, you may have to manually edit your /etc/X11/xorg.conf file and change the horizsync and vertrefresh to refect your monitor

---

### Post by Raghavendra_Ghatag on 2014-04-16
Much to my relief, after installing the proprietary drivers, my monitor is getting detected now.
But the XServer doesnt start. Some error occurs while starting the Xserver and it falls back to command prompt.
The error seems to be suggesting that there was no screen found. I think, as suggested by bazsound, I need to manually configure my monitor settings.
I checked the data sheet of my monitor at [http://ap.viewsonic.com/me/product_pdfs/lcd/19/E-VA1931wma-LED.pdf](http://ap.viewsonic.com/me/product_pdfs/lcd/19/E-VA1931wma-LED.pdf)

It supports resolution up 1366×768 and frequency is Fh: 24-82KHz; Fv: 50-75Hz

Please help me in editing this file [COLOR=#000000]/etc/X11/xorg.conf.

[/COLOR]

---

### Post by Raghavendra_Ghatag on 2014-04-17
I search the internet to understand how to edit the xorg.conf file and modified it according to my monitor data sheet.
But it still doesnt work. When I check error log at /var/log/Xorg.0.log file, it shows some errors like "(EE) Failed to assign any connected display devices to X screen 0" and "(EE) Screen(s) found, but none have a usable configuration".

Here I am pasting some of the contents of both the file

/etc/X11/xorg.conf


Section "Monitor"


    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
    Screen          0
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "1366x768"
    EndSubSection
EndSection






/var/log/Xorg.0.log


[    23.936] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    23.936] (==) NVIDIA(0): RGB weight 888
[    23.936] (==) NVIDIA(0): Default visual is TrueColor
[    23.936] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.940] (**) NVIDIA(0): Enabling 2D acceleration
[    24.943] (II) NVIDIA(0): NVIDIA GPU Quadro NVS 285 (NV44GL) at PCI:1:0:0 (GPU-0)
[    24.943] (--) NVIDIA(0): Memory: 131072 kBytes
[    24.943] (--) NVIDIA(0): VideoBIOS: 05.44.02.63.04
[    24.943] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    24.943] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    24.943] (--) NVIDIA(0): Valid display device(s) on Quadro NVS 285 at PCI:1:0:0
[    24.943] (--) NVIDIA(0):     CRT-0
[    24.943] (--) NVIDIA(0):     CRT-1
[    24.943] (--) NVIDIA(0):     DFP-0
[    24.943] (--) NVIDIA(0):     DFP-1
[    24.943] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    24.943] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    24.943] (--) NVIDIA(0): DFP-0: 155.0 MHz maximum pixel clock
[    24.943] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    24.943] (--) NVIDIA(0): DFP-1: 155.0 MHz maximum pixel clock
[    24.943] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    24.943] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0
[    24.943] (EE) NVIDIA(0): Failing initialization of X screen 0
[    25.035] (II) UnloadModule: "nvidia"
[    25.035] (II) Unloading nvidia
[    25.035] (II) UnloadModule: "wfb"
[    25.035] (II) Unloading wfb
[    25.035] (II) UnloadModule: "fb"
[    25.035] (II) Unloading fb
[    25.035] (EE) Screen(s) found, but none have a usable configuration.
[    25.035] 
Fatal server error:
[    25.035] no screens found
[    25.035] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    25.035] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    25.035] 
[    25.036]  ddxSigGiveUp: Closing log
[    25.036] Server terminated with error (1). Closing log file.


Can some body please help me out here.
The problem is X server is not starting. Only text mode is working on this monitor.

---

### Post by ibjsb4 on 2014-04-17
I have not been in your perdicument, but I wonder if it would be possible to just reset xorg.  You could backup the file and give it a try.  Step #2


[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

