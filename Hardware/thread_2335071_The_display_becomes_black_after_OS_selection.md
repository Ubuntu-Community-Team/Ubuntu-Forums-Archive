---
title: "The display becomes black after OS selection"
date: 2016-08-25
forum: Hardware
---

### Post by 7881666-o on 2016-08-25
ubuntu minimal 16.04.1 32bit+ XFCE basic.
At the time of booting display works just fine. Then there is a menu to  select OS. Display still works just fine. But after I select OS display  immediately becomes black (it is still switched on). If I connect an  external monitor through VGA I can see a picture. In the display  settings a display is active and primary. Any ideas how to fix the  problem?

Hardware: Intel Atom D2550

 [http://www.avalue.com.tw/product/Panel-PC/Self-service/Self-service/FPC-08W27_2059#showarea](http://www.avalue.com.tw/product/Panel-PC/Self-service/Self-service/FPC-08W27_2059#showarea)


/usr/sbin/hwinfo --gfxcard
```

09: PCI 02.0: 0300 VGA compatible controller (VGA)
  [Created at pci.328]
  Unique ID: _Znp.TnfcNKFgcQ7
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: graphics card
  Device Name: "Onboard IGD"
  Model: "Intel Atom Processor D2xxx/N2xxx Integrated Graphics Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x0be2 "Atom Processor D2xxx/N2xxx Integrated Graphics Controller"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1999 
  Revision: 0x0b
  Driver: "gma500"
  Driver Modules: "drm"
  Memory Range: 0xdfb00000-0xdfbfffff (rw,non-prefetchable)
  I/O Ports: 0xf0f0-0xf0f7 (rw)
  IRQ: 43 (1 event)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00008086d00000BE2sv00008086sd00001999bc03sc00i00"
  Driver Info #0:
    Driver Status: gma500_gfx is active
    Driver Activation Cmd: "modprobe gma500_gfx"
  Config Status: cfg=no, avail=yes, need=no, active=unknown

Primary display adapter: #9
```


xrandr output:
```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024     60.02*+  75.02  
   1280x960      75.04    60.00  
   1152x864      75.00  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    60.00  
   720x400       70.08  
DVI-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DVI-1 disconnected (normal left inverted right x axis y axis)
eDP-0 connected 1024x600+0+0 (normal left inverted right x axis y axis) 518mm x 333mm
   1024x600      60.00*+  50.00
```

---

### Post by uwes on 2016-08-25
Sounds like a very similar problem I am facing a few threads away. Does it help to kill the OS by pressing the power button for a few seconds and then booting again?

---

### Post by 7881666-o on 2016-08-27
Accidentally, I found an old disk with magically modified Ubuntu12 where everything works correctly.
The most interesting thing is, that lsmod there shows 'cedarview_gfx' but Ubuntu16 lsmod shows 'gma500'.

lsmod
```
Module                  Size  Used by
nf_conntrack_ipv6      13581  1 
nf_defrag_ipv6         13175  1 nf_conntrack_ipv6
ip6table_filter        12711  1 
ip6_tables             22528  1 ip6table_filter
xt_tcpudp              12531  4 
nf_conntrack_ipv4      19084  1 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
xt_conntrack           12664  2 
nf_conntrack           73847  3 nf_conntrack_ipv6,nf_conntrack_ipv4,xt_conntrack
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  6 ip6table_filter,ip6_tables,xt_tcpudp,xt_conntrack,iptable_filter,ip_tables
joydev                 17393  0 
psmouse                97340  0 
serio_raw              13027  0 
cedarview_gfx         381314  4 
snd_hda_codec_hdmi     31823  1 
snd_hda_codec_realtek   174385  1 
ttm                    64734  1 cedarview_gfx
drm_kms_helper         32561  1 cedarview_gfx
drm                   196391  6 cedarview_gfx,ttm,drm_kms_helper
snd_hda_intel          32719  0 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              28931  1 snd_pcm
i2c_algo_bit           13199  1 cedarview_gfx
snd                    62250  7 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              14635  1 snd
mac_hid                13077  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  19115  1 cedarview_gfx
shpchp                 32265  0 
lp                     17455  0 
parport                40930  1 lp
ext2                   67987  2 
usbhid                 41937  0 
hid                    81731  1 usbhid
pata_jmicron           12651  2 
e1000e                140131  0
```

---

