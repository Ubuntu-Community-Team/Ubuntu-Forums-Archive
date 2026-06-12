---
title: "Installed Lubuntu on laptop and now things don't get work/detected"
date: 2018-08-27
forum: Hardware
---

### Post by thenflux on 2018-08-27
Hello everyone, I'm new to Linux and I just installed Lubuntu on my Laptop (REDFOX Wizbook Cloud) and a few things didn't really work well.

To start off, I'd like everyone to know that the laptop came preinstalled with windows8 and was working fine. I upgraded the OS to windows 10 and things didn't work but I found a solution by installing different updates. Then, I installed Lubuntu and I encountered the same problems again.

Here are the list of problems:

1. Trackpad - It functions when you do specific gestures like: swiping left from the edges or 3-finger-gesture. BUT using it as a mouse (mouse pointing/left click/righclick) does not work.
2. Sound - Sound drivers didn't install. I have no idea how to fix it,
3. Bluetooth - The system tells me that there's no Bluetooth adapter found. (I'm pretty sure that the bluetooth works on windows10)
4. Graphics - Looks fine but there's a lot of stuttering during videos. I don't think the graphics drivers are up to date
[s]5. WiFi - Tells me that there's no network adapter[/s] Solved.

Tell me what I need to do so I can help you guys help me. 

Thanks!

---

### Post by yancek on 2018-08-27
Start by posting more detailed information here.  Run the command from a terminal:  inxi -F
Post the output here.  If you get a message that it is not installed, install it and run the command again.

---

### Post by thenflux on 2018-08-28
This is what > inxi -F shows
```
System:    Host: paolo-WB-Z8140 Kernel: 4.15.0-33-generic x86_64 bits: 64
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: Insyde product: WB-Z8140 serial: N/A
           Mobo: Insyde model: Type2 - Board Product Name v: Type2 - Board Version serial: N/A
           UEFI: INSYDE v: REDFOXx.WT314.NBNN01 date: 09/03/2016
CPU:       Quad core Intel Atom x5-Z8300 (-MCP-) cache: 1024 KB
           clock speeds: max: 1840 MHz 1: 480 MHz 2: 544 MHz 3: 1371 MHz
           4: 1319 MHz
Graphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics (Cherrytrail)
           version: 4.5 Mesa 18.0.5
Audio:     Card Intel HDMI/DP LPE Audio driver: HdmiLpeAudio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-33-generic
Network:   Card: Failed to Detect Network Card!
Drives:    HDD Total Size: NA (-)
           ID-1: /dev/mmcblk0 model: N/A size: 31.0GB
Partition: ID-1: / size: 28G used: 9.3G (35%) fs: ext4 dev: /dev/mmcblk0p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 180 Uptime: 1 day Memory: 901.0/1900.8MB
           Client: Shell (bash) inxi: 2.3.56 


```

---

### Post by thenflux on 2018-09-03
Can anyone help a guy out?

---

### Post by thenflux on 2018-09-12
Help?

---

