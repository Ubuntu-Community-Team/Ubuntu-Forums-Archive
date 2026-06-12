---
title: "ubuntu 10.10 / catalyst 10.10 / crossfire / configuration"
date: 2010-11-16
forum: Hardware
---

### Post by rootfairy on 2010-11-16
hi all,

i am using ubuntu 10.10 32 bit with catalyst 10.10. i am also using crossfire with a 5750 & 5770. i think i succesfully installed the driver and created and activated a crossfire chain. but im wondering about the some parts of the configuration.

fglrxinfo:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string: 4.0.10243 Compatibility Profile Context

is it ok that only one adapter is shown here and not two, because im using crossfire and therefore 2 gfx-cards?

what is the command "aticonfig --adapter=all --initial" doing? after the installation i only issued "aticonfig --initial". is this the reason why it only shows one display here?

aticonfig --lsch:
> CrossFire chain for adapter 0, status: enabled
  0. 01:00.0 ATI Radeon HD 5700 Series
  1. 02:00.0 ATI Radeon HD 5700 Series 


my xorg conf looks like this:
> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection



what can i change about this conf to make some performance tweaks, etc.? is it properly configured for crossfire, i think one device is missing?

---

### Post by rootfairy on 2010-11-16
aticonfig --lscs shows me
> Candidate Combination: 
    Master: 1:0:0 
    Slave: 2:0:0 
    CrossFire is disabled on current device
    CrossFire Diagnostics:
    CrossFire can work with P2P mapping through GART
    Dongle Capabilities: support PASSTHROUGH |INTERLINK_SW_AFR | INTERLINK_AUTO_AFR | INTERLINK_BLACKING | INTERLINK_SUPERAA 


the slave candidate is not in xorg.conf file. if it is initiated with aticonfig --adapter=all --initial it will be put into xorg.conf as another master adapter. and i got it all doubled. do i need a special command for making it slave?

---

