---
title: "No sound on Linux 10.7"
date: 2011-03-17
forum: Hardware
---

### Post by Abernesmagt on 2011-03-17
Hallo as the topic says i don't have sound on my ubuntu. 
very simple. . 
i have dual boot with windows 7 (home premium) and my sound works fine.. 
but when i start up ubuntu i have no sound. . even at the startup, i don't hear a noise. .

info about system:

Sound Devices
-------------
          BIOS: BIOS Date: 09/23/09 11:58:43 Ver: 08.00.10
          Processor: Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz (4 CPUs), ~2.5GHz
             Memory: 4096MB RAM
Available OS Memory: 3950MB RAM
          Page File: 1921MB used, 59

            Hardware ID:      HDAUDIO\FUNC_01&VEN_10EC&DEV_0269&SUBSYS_104D4600&REV_1000
        Manufacturer ID: 1
             Product ID: 100  
                   Type: WDM
            Driver Name: RTKVHD64.sys
         Driver Version: 6.00.0001.6098 (English)
      Driver Attributes: Final Retail


Thanks in advance :D

---

### Post by dabl on 2011-03-17
Even though it is dated, this is still good basic sound troubleshooting guidance:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Questions:

1. Did/does sound work when you boot a Ubuntu Live CD?

2. Did sound ever work with Ubuntu on this system?

3. Have you checked the ALSA project database to determine which driver (if any) is appropriate for your sound chip?

[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by Abernesmagt on 2011-03-18
i installed Ubuntu inside windows -wubi-install(with CD)When i tried to install linux to boot up the CD, it failed in some why, but can i run the CD now  as Repair or something like that?

---

