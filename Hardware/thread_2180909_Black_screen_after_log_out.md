---
title: "Black screen after log out"
date: 2013-10-15
forum: Hardware
---

### Post by mojtabazarei on 2013-10-15
[COLOR=#333333][FONT=UbuntuRegular][SIZE=2][B][FONT=arial]
I have  installed ATI driver and it fully works.
[/FONT][/B][/SIZE][/FONT][/COLOR]
[COLOR=#333333][B][FONT=arial][SIZE=2]All my tests show that my installation was successful. 

every time i try logout laptop it seems monitor get  turnet off 

can't use any tty [/SIZE][SIZE=2]  i can use compiz and work fully [/SIZE]

[SIZE=4]here are the result of some command :
[/SIZE]
[/FONT][/B][B]fglrxinfo
[/B][B][FONT=arial]
[/FONT][/B][/COLOR]
```
mojtaba@mojtaba-N61Jq:~$ fglrxinfo
display: :0  screen: 0 OpenGL
vendor string: Advanced Micro Devices, Inc. OpenGL renderer string:

AMD Radeon HD 6570M/5700 Series OpenGL version string: 4.2.12217
Compatibility Profile Context 12.104
```

[B]xorg.conf
[/B]
```
Section "ServerLayout"  Identifier     "aticonfig Layout"   Screen      0  "aticonfig-Screen[0]-0" 0 0 EndSection

Section "Module" 
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option      "VendorName" "ATI Proprietary Driver"
    Option      "ModelName" "Generic Autodetecting Monitor"
    Option      "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option      "UseFastTLS" "1"
    BusID       "PCI:1:0:0" 
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth    24
    EndSubSection 
EndSection
```
[COLOR=#333333]
[SIZE=3]lshw -class video
[/SIZE][B][FONT=arial]
[/FONT][/B][/COLOR]
```
mojtaba@mojtaba-N61Jq:~$ lshw -class video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: Madison [Mobility Radeon HD 5730 / 6570M]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:64 memory:c0000000-cfffffff memory:d0020000-d003ffff ioport:d000(size=256) memory:d0000000-d001ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

[COLOR=#333333][B][FONT=arial]



[/FONT][/B][/COLOR]

---

