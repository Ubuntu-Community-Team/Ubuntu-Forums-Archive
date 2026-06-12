---
title: "resolution problem in Intel 855GM"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by S4ud1-Linux on 2008-02-28
hi guys 
iam using ubuntu 7.04 i have problem in resolution my cards
```
root@Ubuntu:~# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

i have only there resolution 
```
root@Ubuntu:~# xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60  
 1    640 x 480    ( 347mm x 260mm )   60  
 2    800 x 600    ( 347mm x 260mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none
```

i search in google and ubuntu forum many time all people suggestion
used 915resolution tools  
i install the tools 
```
 apt-get install 915resolution
```
and display all resolution 
```
root@Ubuntu:~# 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $29f
Mode Table Entries: 39

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 7c : 1280x801, 8 bits/pixel
Mode 7d : 1280x801, 16 bits/pixel
Mode 7e : 1280x801, 32 bits/pixel
```

and i used the last only 
```
root@Ubuntu:~# 915resolution 7e 1280 801 32
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 855GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $29f
Mode Table Entries: 39
```

and than restart GDM and also restart the machine but nothing
i System --> Preferences --> Screen Resolution 
1024x768 , 640x480 , 800x600 

and i found this post same my problem and same my card he success , i do everything but nothing change same resolution :(
[http://ubuntuforums.org/showthread.php?t=291865](http://ubuntuforums.org/showthread.php?t=291865)

and also i used 855resolution tools but nothing change :(

is there any solution for this problem 
my resolution bad please guys

---

### Post by S4ud1-Linux on 2008-02-28
up up up guys

---

