---
title: "Sound problem - no audio device detected"
date: 2018-09-29
forum: Hardware
---

### Post by mdallastella on 2018-09-29
Hello everyone

Since yesterday audio stopped working in my pc, right after connecting it to an external device through HDMI. Actually in a first moment it only stopped working with Firefox, but now the problem has extended to all sounds coming from the pc (sorry if my language isn't too technical). I fear that while trying to fix the Firefox problem I've made some mistake and now no audio device is detected.

[IMG]https://image.ibb.co/g70hnU/screenshot_resized.png[/IMG]

I've got Ubuntu 18.04.1. If I give the  sudo lshw -C multimedia command that's what I've got
```
marco@marco-HP-15-Notebook-PC:~$ sudo lshw -C multimedia
[sudo] password di marco: 
  *-multimedia:0            
       description: Audio device
       product: Broadwell-U Audio Controller
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:50 memory:c6310000-c6313fff
  *-usb:2
       description: Video
       product: HP Truevision HD
       vendor: Chicony Electronics Co., Ltd.
       physical id: 5
       bus info: usb@1:5
       version: 69.39
       capabilities: usb-2.00
       configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
  *-multimedia:1
       description: Audio device
       product: Wildcat Point-LP High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=64
       resources: irq:49 memory:c6314000-c6317fff
marco@marco-HP-15-Notebook-PC:~$ 
```


[/code]
Thank you in advance.

Marco

---

### Post by mdallastella on 2018-09-29
I wanted to check with the lsof | grep snd, that I've foudn being a command to detect what is using my audio device, and here's what I've got

```
lsof | grep snd 
gnome-she 1468                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     1468 1470            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
dconf\x20 1468 1471            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     1468 1472            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1487            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1488            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1489            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1490            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1491            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1492            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1493            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 1468 1494            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gsd-sound 1593                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     1593 1601            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     1593 1602            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
dconf\x20 1593 1644            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gsd-media 1634                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     1634 1670            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     1634 1671            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
dconf\x20 1634 1680            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
firefox   2577                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     2577 2583            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     2577 2584            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Gecko_IOT 2577 2585            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Timer     2577 2586            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Link\x20M 2577 2587            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Socket    2577 2588            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Wat 2577 2589            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2577 2590            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2577 2591            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2577 2592            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2577 2593            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
AudioIPC  2577 2594            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
AudioIPC  2577 2595            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Cache2    2577 2599            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Cookie    2577 2600            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
GMPThread 2577 2602            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Softwar~c 2577 2603            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Composito 2577 2604            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
VRListene 2577 2605            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2577 2606            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageIO   2577 2607            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
IPDL\x20B 2577 2611            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DOM\x20Wo 2577 2612            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
HTML5\x20 2577 2614            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2577 2621            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2577 2622            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2577 2623            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
firefox   2577 2624            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
firefox   2577 2625            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageBr~g 2577 2628            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
FS\x20Bro 2577 2633            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProcessHa 2577 2634            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DataStora 2577 2648            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DataStora 2577 2649            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
SysProxyS 2577 2650            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
dconf\x20 2577 2651            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProxyReso 2577 2652            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DataStora 2577 2653            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
URL\x20Cl 2577 2654            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Classif~  2577 2655            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Cache\x20 2577 2659            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
mozStorag 2577 2660            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
mozStorag 2577 2665            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DOM\x20Wo 2577 2670            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
localStor 2577 2675            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
mozStorag 2577 2679            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
mozStorag 2577 2680            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
QuotaMana 2577 2681            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DataStora 2577 2699            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DOM\x20Wo 2577 2700            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
SaveScrip 2577 2740            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
FS\x20Bro 2577 2744            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
mozStorag 2577 2763            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2577 2768            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2577 2769            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
mozStorag 2577 2772            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
mozStorag 2577 2845            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
FS\x20Bro 2577 2879            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
FS\x20Bro 2577 2921            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
VideoCapt 2577 2977            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
InotifyEv 2577 2978            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Web\x20Co 2626                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Chrome_~d 2626 2630            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     2626 2631            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     2626 2632            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Wat 2626 2640            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2626 2641            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2626 2642            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2626 2643            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2626 2644            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Socket    2626 2645            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Timer     2626 2646            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2626 2657            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageIO   2626 2658            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageBr~g 2626 2661            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
VideoChil 2626 2662            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProcessHa 2626 2663            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProfilerC 2626 2664            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
HTML5\x20 2626 2669            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2626 2672            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2626 2673            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2626 2674            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2626 2686            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2626 2713            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DOM\x20Fi 2626 2721            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Web\x20Co 2742                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Chrome_~d 2742 2746            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     2742 2747            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     2742 2748            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Wat 2742 2749            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2742 2750            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2742 2751            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2742 2752            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2742 2753            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Socket    2742 2754            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Timer     2742 2755            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2742 2756            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageIO   2742 2757            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageBr~g 2742 2758            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
VideoChil 2742 2759            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DOM\x20Fi 2742 2760            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProcessHa 2742 2761            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProfilerC 2742 2762            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
HTML5\x20 2742 2785            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2742 2787            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2742 2788            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2742 2789            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2742 2808            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2742 2810            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
dconf\x20 2742 2846            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Web\x20Co 2873                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Chrome_~d 2873 2876            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     2873 2877            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     2873 2878            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Wat 2873 2880            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2873 2881            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2873 2882            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2873 2883            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2873 2884            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Socket    2873 2885            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Timer     2873 2886            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2873 2887            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageIO   2873 2888            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageBr~g 2873 2889            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
VideoChil 2873 2890            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DOM\x20Fi 2873 2891            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProcessHa 2873 2892            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProfilerC 2873 2893            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
HTML5\x20 2873 2941            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2873 2942            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2873 2943            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2873 2944            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2873 2946            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2873 2962            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
MediaCach 2873 2963            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
MediaMana 2873 2975            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Cameras   2873 2976            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
AudioIPC  2873 2979            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
AudioIPC0 2873 2980            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
AudioIPC1 2873 2981            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
dconf\x20 2873 3041            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Web\x20Co 2919                 marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Chrome_~d 2919 2923            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gmain     2919 2924            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
gdbus     2919 2925            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Wat 2919 2926            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2919 2927            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2919 2928            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2919 2929            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
JS\x20Hel 2919 2930            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Socket    2919 2931            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
Timer     2919 2932            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2919 2934            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageIO   2919 2935            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImageBr~g 2919 2936            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
VideoChil 2919 2937            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
DOM\x20Fi 2919 2938            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProcessHa 2919 2939            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ProfilerC 2919 2940            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
HTML5\x20 2919 3067            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2919 3068            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2919 3069            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
StyleThre 2919 3070            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2919 3073            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28
ImgDecode 2919 3074            marco  mem       REG                8,2    487504   39330395 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.28

```

---

### Post by krooknews on 2018-09-30
Connection to PulseAudio failed. Automatic retry in 5s. In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigures. The situation can also arise when PulseAudio crashed and left stale details in the X11 Root Window. If this is the case, then PulseAudio should autospawn again, [or]("http://krooknews.com") if this is not configured you should run start-pulseaudio-x11 manually.

---

### Post by Yellow Pasque on 2018-10-01
Try this first:
```
rm -r ~/.config/pulse*
pulseaudio -k
```

---

