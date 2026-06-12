---
title: "Can't generate xorg.conf"
date: 2011-04-15
forum: Hardware
---

### Post by ctshiner on 2011-04-15
This seems like something that would have been a 10 second fix in the old days but has been a HUGE pain in my *** for the last 3 hours now.

Anyway, I'm on Ubuntu 11.04 and so have no xorg.conf.  If I try to generate one using
```
sudo xorg -configure
```its gives the error "Number of created screens does not match number of detected devices. Configuration failed"

All I want to do is add a few extra lines to my video card drivers to get World of Warcraft working. Can I manually create xorg.conf and ONLY add the lines I need or do I need the complete file?  How do I know the name of the drivers I am using so I can do it manually? I will end up with something like this according to Wine's wiki:

```
Section "Device"   
  Identifier  "aticonfig-Device[Amity wine]]ver      "fglrx"
  Option       "Capabilities" "0x00000800" 
  Option       "UseFastTLS" "off"   
  Option       "KernelModuleParm" "locked-userpages=0" 
EndSection
```

---

### Post by Yellow Pasque on 2011-04-15
EDIT: just noticed the example you used was not from your computer.
Post your ./var/log/Xorg.0.log

---

### Post by ctshiner on 2011-04-17
Thanks for the reply, I got frustrated through and went back to 10.10, all is well now :)  Running the same xorg edgers drivers in both version, must be a bug

---

### Post by bodmerocity on 2011-05-28
Bump. Having exact same problem as this guy only I'm trying to get my mouse to work. Any other way to create xorg.conf?

[QUOTE=ctshiner;10681387]This seems like something that would have been a 10 second fix in the old days but has been a HUGE pain in my *** for the last 3 hours now.

Anyway, I'm on Ubuntu 11.04 and so have no xorg.conf.  If I try to generate one using
```
sudo xorg -configure
```its gives the error "Number of created screens does not match number of detected devices. Configuration failed"

---

### Post by asd1618033 on 2011-05-28
xorg.conf is deprecated

new config files:
```
/etc/X11/xorg.conf.d/10-evdev.conf
/etc/X11/xorg.conf.d/10-monitor.conf
/etc/X11/xorg.conf.d/10-synaptics.conf
```

evdev.conf stores input informations, like keyboard and mouse
monitor.conf stores infos about video driver and monitor specs
synaptics.conf stores info about synaptics touchpad.

@ thread starter: create 10-monitor.conf (generally it doesn't exist beacuse kernel uses KMS, if I am not wrong) and insert your video drivers / monitor / screen infos.

example of 10-monitor.conf:
```
Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "Device"
    Identifier    "Device0"
    Driver        "fglrx" #Choose the driver used for this monitor
EndSection

Section "Screen"
    Identifier    "Screen0"  #Collapse Monitor and Device section to Screen section
    Device        "Device0"
    Monitor       "Monitor0"
    DefaultDepth  16 #Choose the depth (16||24)
    SubSection "Display"
        Depth     16
        Modes     "1024x768" #Choose the resolution
    EndSubSection
EndSection
```

---

### Post by bodmerocity on 2011-05-28
So how do I add my mouse?

I try touch /etc/X11/xorg.conf.d/10-evdev.conf and it says 'no such file or directory'.

---

### Post by sdowney717 on 2011-08-19
those folders and files dont exist
maybe they should exist, but maybe not, no one really knows
If they are not showing there then IMO they are not there.
I have an xorg.conf
Did you ever solve your problem?

---

### Post by mpollmeier on 2011-09-03
maybe a bit late now, but for other users: the xorg config  files are now located in /usr/share/X11/xorg.conf.d

also see [http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04](http://askubuntu.com/questions/37761/xorg-conf-in-ubuntu-natty-11-04)

---

### Post by desiph3r on 2012-02-08
I can't find monitor.conf file on my 11.04 system and I'm trying to configure extended desktop on my ait Radeon X300SE PCI card. 


./usr/share/man/man5/xorg.conf.5.gz
./usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
./usr/share/X11/xorg.conf.d
./usr/share/X11/xorg.conf.d/10-evdev.conf
./usr/share/X11/xorg.conf.d/50-wacom.conf
./usr/share/X11/xorg.conf.d/50-vmmouse.conf
./usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
./usr/share/X11/xorg.conf.d/11-evdev-quirks.conf
./usr/share/X11/xorg.conf.d/50-synaptics.conf

When I configure the extended desktop screen 2 gets all pixels meshed together.

---

### Post by desiph3r on 2012-02-08
Here are my specs on the graphics card.

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]


*-display:0             
       description: VGA compatible controller
       product: RV370 5B60 [Radeon X300 (PCIE)]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:dc000000-ddffffff memory:dfde0000-dfdeffff ioport:dc00(size=256) memory:dfe00000-dfe1ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV370 [Radeon X300SE]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:dfdf0000-dfdfffff

---

