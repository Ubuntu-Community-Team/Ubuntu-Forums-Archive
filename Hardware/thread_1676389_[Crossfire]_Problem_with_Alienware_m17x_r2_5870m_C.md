---
title: "[Crossfire] Problem with Alienware m17x r2 5870m Crossfire"
date: 2011-01-27
forum: Hardware
---

### Post by Buntolo on 2011-01-27
As the title says, I can't use Ati driver at all, Crossfire or not.

OS: Ubuntu 10.10 full updated
driver: Catalyst 10.12 from offical website

```
sudo aticonfig --lsa
* 0. 03:00.0 ATI Mobility Radeon HD 5800 Series 
  1. 02:00.0 ATI Mobility Radeon HD 5800 Series 

* - Default adapter
```

```
sudo aticonfig --adapter=0,1 --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-0
```

```
cat /etc/X11/xorg.conf
Section "ServerLayout"
   Identifier     "aticonfig Layout"
   Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver      "fglrx"
   BusID       "PCI:3:0:0"
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
```

If I reboot now I get black and empty screen, the only solution is to erase xorg.conf from live.

So I've retried:
```
sudo aticonfig --adapter=0,1 --initial
```
No reboot and immediately adding Crossfire

```
sudo aticonfig --cfa --adapter=0,1
CrossFire chain added
sudo aticonfig --cf on --adapter=0,1
Warning: No CrossFire chain defined for master adapter 1
CrossFire chain(s) enabled
```

But still getting black screen at reboot.

---

