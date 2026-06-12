---
title: "Lenovo ThinkBook 16 G4+ IAP - display flickering"
date: 2023-03-24
forum: Hardware
---

### Post by pautorras on 2023-03-24
Hi folks,

I have some problems with main display of laptop Lenovo. Sometimes I've display flickering problems.

See attached some different system information:


**Snap installed software:**
Name                 Version          Rev    Tracking       Publisher   Notes
bare                 1.0              5      latest/stable  canonical&#10003;  base
canonical-livepatch  10.4.1           164    latest/stable  canonical&#10003;  -
core                 16-2.58.3        14946  latest/stable  canonical&#10003;  core
core20               20230308         1852   latest/stable  canonical&#10003;  base
firefox              111.0.1-2        2487   latest/stable  mozilla&#10003;    -
gnome-3-38-2004      0+git.6f39565    119    latest/stable  canonical&#10003;  -
gtk-common-themes    0.1-81-g442e511  1535   latest/stable  canonical&#10003;  -
snapd                2.58.3           18596  latest/stable  canonical&#10003;  snapd


**inxi -iG :**
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics driver: i915 v: kernel
  Device-2: NVIDIA GA107M [GeForce RTX 2050] driver: nvidia v: 525.85.05
  Device-3: Luxvisions Innotech Integrated Camera type: USB
    driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1: 1920x1080~60Hz
    2: 1920x1080~60Hz 3: 1920x1200~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2) v: 4.6 Mesa 22.2.5
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi
  IF: wlp0s20f3 state: down mac: 3c:e9:f7:42:25:c5
  Device-2: Intel Ethernet I219-V driver: e1000e
  IF: enp0s31f6 state: up speed: 1000 Mbps duplex: full
    mac: 98:8f:e0:65:0e:89
  IP v4: 192.16.70.80/24 type: noprefixroute scope: global
  IP v6: fe80::27c5:7a2c:dba1:39e3/64 type: noprefixroute scope: link
  Device-3: ASIX AX88179 Gigabit Ethernet type: USB driver: ax88179_178a
  IF: enx34298f7661fc state: down mac: 34:29:8f:76:61:fc
  IF-ID-1: vmnet1 state: unknown speed: N/A duplex: N/A
    mac: 00:50:56:c0:00:01
  IP v4: 192.168.102.1/24 scope: global
  IP v6: fe80::250:56ff:fec0:1/64 scope: link
  IF-ID-2: vmnet8 state: unknown speed: N/A duplex: N/A
    mac: 00:50:56:c0:00:08
  IP v4: 172.16.216.1/24 scope: global
  IP v6: fe80::250:56ff:fec0:8/64 scope: link
  WAN IP: 192.16.70.80


Flickering problems starts when remote desktop programs are running. Programs like Anydesk or Teamviewer.

I doubt the problem comes from the desktop interface being via snap as it has limitations (gnome-3-38-2004). 
If you think that this could be a problem, how can I uninstall this snap package and install without snap and without losing the desktop at any time?

Thanks in advance.

Pau

---

