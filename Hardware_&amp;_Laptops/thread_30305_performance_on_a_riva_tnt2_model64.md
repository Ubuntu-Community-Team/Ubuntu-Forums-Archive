---
title: "performance on a riva tnt2 model64"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by iomicifikko on 2005-04-28
hi all, i have ubuntu installed on my old athlon 900mhz, ram 256MB  with a nvidia card: riva tnt2 model64 pro.
everything seems to work, nvidia drivers installed etc. i was just wondering if the graphic card was well configured couse i noticed that moving windows etc is not very "fluid" (maybe is just the old pc?)

running glxgears i get more or less 240fps. is that good for my hardware?
another strange thing:

teo@zull1234321:~ $ cat /proc/driver/nvidia/cards/0
Model:           RIVA TNT2 Model 64/Model 64 Pro
IRQ:             3
Video BIOS:      02.05.19.03.20
Card Type:       AGP

but

teo@zull1234321:~ $ cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput
of the 'dmesg' command and/or your system log file
for additional information on this problem.

any idea?

ps: direct rendering is ok ("yes"), 3d games like cube work fine and this is the nvidia device section in my XF86config-4:

Section "Device"
        Identifier      "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "RenderAccel"           "true"
        Option          "NvAGP"                 "1"
EndSection


thanks anyone, bye!

---

### Post by iomicifikko on 2005-04-28
giving a look at a few guides, ive read about the nvagp option : set to 1  uses nvagp, set to 2  uses agpgart module, if loaded. then i change config as explained:

set 

 Option "NvAGP" "2"

in nvidia device section in XF86Config-4 (uses agpgart if possible)

added

"agpgart"

in /etc/modules (u cant use it if u dont load it)

fast write and SBA are not supported by tnt2 riva, not too bad.

reboot pc.

something strange: loading glxgears i obtain sonething like this:

941 frames in 5.0 seconds = 188.200 FPS
1331 frames in 5.0 seconds = 266.200 FPS
1330 frames in 5.0 seconds = 266.000 FPS
1329 frames in 5.0 seconds = 265.800 FPS
1195 frames in 5.0 seconds = 239.000 FPS
3529 frames in 5.0 seconds = 705.800 FPS
1491 frames in 5.0 seconds = 298.200 FPS
1214 frames in 5.0 seconds = 242.800 FPS
1331 frames in 5.0 seconds = 266.200 FPS
1316 frames in 5.0 seconds = 263.200 FPS
1330 frames in 5.0 seconds = 266.000 FPS
1331 frames in 5.0 seconds = 266.200 FPS
1204 frames in 5.0 seconds = 240.800 FPS
1245 frames in 5.0 seconds = 249.000 FPS
1264 frames in 5.0 seconds = 252.800 FPS
1266 frames in 5.0 seconds = 253.200 FPS
3559 frames in 5.0 seconds = 711.800 FPS
2613 frames in 5.0 seconds = 522.600 FPS
1188 frames in 5.0 seconds = 237.600 FPS
1307 frames in 5.0 seconds = 261.400 FPS
1295 frames in 5.0 seconds = 259.000 FPS
1256 frames in 5.0 seconds = 251.200 FPS
1245 frames in 5.0 seconds = 249.000 FPS
1924 frames in 5.0 seconds = 384.800 FPS
1239 frames in 5.0 seconds = 247.800 FPS
2132 frames in 5.0 seconds = 426.400 FPS
4008 frames in 5.0 seconds = 801.600 FPS
1300 frames in 5.0 seconds = 260.000 FPS
1850 frames in 5.0 seconds = 370.000 FPS
7391 frames in 5.0 seconds = 1478.200 FPS
6440 frames in 5.0 seconds = 1288.000 FPS
7036 frames in 5.0 seconds = 1407.200 FPS
7054 frames in 5.0 seconds = 1410.800 FPS
7260 frames in 5.0 seconds = 1452.000 FPS
6035 frames in 5.0 seconds = 1207.000 FPS
6910 frames in 5.0 seconds = 1382.000 FPS
6199 frames in 5.0 seconds = 1239.800 FPS
5914 frames in 5.0 seconds = 1182.800 FPS
898 frames in 5.0 seconds = 179.600 FPS
4368 frames in 5.0 seconds = 873.600 FPS
6451 frames in 5.0 seconds = 1290.200 FPS
4798 frames in 5.0 seconds = 959.600 FPS
7193 frames in 5.0 seconds = 1438.600 FPS
5625 frames in 5.0 seconds = 1125.000 FPS
5602 frames in 5.0 seconds = 1120.400 FPS
5693 frames in 5.0 seconds = 1138.600 FPS
5574 frames in 5.0 seconds = 1114.800 FPS
2371 frames in 5.0 seconds = 474.200 FPS
7584 frames in 5.0 seconds = 1516.800 FPS
7984 frames in 5.0 seconds = 1596.800 FPS
8028 frames in 5.0 seconds = 1605.600 FPS
8020 frames in 5.0 seconds = 1604.000 FPS
8004 frames in 5.0 seconds = 1600.800 FPS
6790 frames in 5.0 seconds = 1358.000 FPS
5411 frames in 5.0 seconds = 1082.200 FPS
3699 frames in 5.0 seconds = 739.800 FPS
3396 frames in 5.0 seconds = 679.200 FPS
3495 frames in 5.0 seconds = 699.000 FPS
3556 frames in 5.0 seconds = 711.200 FPS
3635 frames in 5.0 seconds = 727.000 FPS
7206 frames in 5.0 seconds = 1441.200 FPS
7659 frames in 5.0 seconds = 1531.800 FPS
6700 frames in 5.0 seconds = 1340.000 FPS
6773 frames in 5.0 seconds = 1354.600 FPS

the fps started increasing that way  (over 1000) after starting 5 little gnome games together, and finally the best 1600 opening firefox, seems like ubuntu on my centrino laptop, why?


thanks, byez

more info can be found here
[http://www.gmpf.de/index.php/NVidia:X_config_options](http://www.gmpf.de/index.php/NVidia:X_config_options)
[http://www.gmpf.de/index.php/NVidia:AGP_Support](http://www.gmpf.de/index.php/NVidia:AGP_Support)
[http://www.gmpf.de/index.php/NVidia:Module_parameters](http://www.gmpf.de/index.php/NVidia:Module_parameters)

---

