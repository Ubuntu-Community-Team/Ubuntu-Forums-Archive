---
title: "Intel video card"
date: 2008-10-18
forum: Hardware
---

### Post by Pinejoker on 2008-10-18
Intel Corporation
82915G/GV/910GL Integrated Graphics Controller


I need to know if how can i download a latest version for my graphics and to upgrade it XD any1 can help me please.. asap!!:confused::confused:

---

### Post by ardvark71 on 2008-10-18
> **Pinejoker said:**
> Intel Corporation
82915G/GV/910GL Integrated Graphics Controller


I need to know if how can i download a latest version for my graphics and to upgrade it XD any1 can help me please.. asap!!:confused::confused:

Hi...

Does this thread help?

[http://ubuntuforums.org/archive/index.php/t-391105.html](http://ubuntuforums.org/archive/index.php/t-391105.html)

Specifically, this post...

"There is 915resolution driver in the repos. You need to enable both universe & multiverse in /etc/apt/sources.list first.

http://www.psychocats.net/ubuntu/sources"

There is also this site...

[http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)

Intel's site has these drivers but they appear a bit too old...

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1764&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1764&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

Best Regards...

---

### Post by Pinejoker on 2008-10-18
do you know how to fix the driver loader error?

---

### Post by Pinejoker on 2008-10-18
2008-10-17 23:03:37,565 ERROR got an error from dpkg for pkg: 'driverloader': 'subprocess post-installation script returned error exit status 1
'
2008-10-17 23:03:37,597 ERROR got an error from dpkg for pkg: 'driverloader': 'subprocess post-installation script returned error exit status 1
'
2008-10-17 23:08:10,916 WARNING no activity on terminal for 240 seconds (Configuring scrollkeeper)
2008-10-17 23:20:01,226 ERROR SystemError from cache.commit(): installArchives() failed

---

### Post by Perfect Storm on 2008-10-18
Thread moved.

Thread title changed. Please use proper Thread title next time, thanks.


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by ardvark71 on 2008-10-18
> **Pinejoker said:**
> do you know how to fix the driver loader error?

Hi...

Not sure if I can help on that one. :confused:

What are you trying to do specifically and what version of Ubuntu/Kubuntu/Xubuntu etc., are you running.

Also, please post the results of this command...

```
lspci
```

Best Regards...

---

### Post by Pinejoker on 2008-10-18
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller
 Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated
Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Ex
press Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                    B UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                    B UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                    B UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                    B UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) US                    B2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Brid                    ge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE                     Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Control                    ler (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contr                    oller (rev 04)
03:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
03:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LO                    M) Ethernet Controller (rev 04)

---

### Post by ardvark71 on 2008-10-18
Hi...

Ok, thank you but I still need an answer to the first question. ;)

Can you also post the contents of your xorg.conf file?

Thanks!

---

### Post by Pinejoker on 2008-10-18
> **ardvark71 said:**
> Hi...

Ok, thank you but I still need an answer to the first question. ;)

Can you also post the contents of your xorg.conf file?

Thanks!

xorg.conf what is that???

---

### Post by Perfect Storm on 2008-10-18
> **Pinejoker said:**
> xorg.conf what is that???

To see your xorg.conf;

```
cat /etc/X11/xorg.conf
```

---

### Post by Pinejoker on 2008-10-18
here sir..


   Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x                              400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x                              400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

