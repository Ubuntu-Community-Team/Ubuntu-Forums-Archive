---
title: "unable to add a configuration with xrandr"
date: 2010-03-21
forum: Hardware
---

### Post by abelito8 on 2010-03-21
I am using xubuntu 9.10 on a aao 
the default settings did not support any other screen than 1024:900 and I have used xrandr to create new configurations, but when it comes to adding them it says I cannot...I have tried with VGS, DVI and others and it says it's wrong


abelito@Ernestino:~$ xrandr
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
  800x600_50.00 (0x10c)   30.8MHz
        h: width   800 start  824 end  896 total  992 skew    0 clock   31.0KHz
        v: height  600 start  603 end  607 total  621           clock   49.9Hz
  656x340_50.00 (0x10d)   14.2MHz
        h: width   656 start  672 end  736 total  816 skew    0 clock   17.5KHz
        v: height  340 start  343 end  353 total  356           clock   49.1Hz
abelito@Ernestino:~$ xrandr --addmode VGA-O 800x600
xrandr: cannot find output "VGA-O"


any help please?

---

