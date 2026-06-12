---
title: "[SOLVED] Conky + lm-sensors"
date: 2008-07-23
forum: General Help
---

### Post by tamoneya on 2008-07-23
I am having trouble getting conky to work with lm-sensors.  I get this error when I run conky:```
Conky: can't open '/sys/bus/i2c/devices/9191-0290/temp2_input': No such file or directory

```

It has to do with this line in conkyrc:```
${color #888888}cpu temp: ${color #CCCCCC}${i2c 9191-0290 temp 2} deg
```

When looking in /sys/bus/i2c/devices the directory is 100% empty.  I have run sensors-detect and restarted my computer and it still doesnt work.  running sensors however does return results so I lm-sensors is at least installed somewhat.  I guess it just isnt installed the way that conky is expecting.  I searched for a while but most of the solutions I found had to do with looking in the wrong directory in /sys/bus/i2c/devices. I have no directories in there so those solutions didnt work for me.

Here is the output of sensors:```
tamoneya@tamoneyat61:~$ sensors
thinkpad-isa-0000
Adapter: ISA adapter
fan1:       3093 RPM
temp1:       +58.0°C                                    
temp2:       +40.0°C                                    
temp3:       +35.0°C                                    
temp4:       +56.0°C                                    
temp5:       +32.0°C                                    
temp7:       +30.0°C                                    
temp9:       +39.0°C                                    
temp10:      +44.0°C                                    
temp11:      +48.0°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +55.0°C  (crit = +100.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +55.0°C  (crit = +100.0°C) 
```

---

### Post by tamoneya on 2008-07-30
still havent found out what is wrong with i2c.

```
sudo bump
```

---

### Post by easybake on 2008-07-31
> **tamoneya said:**
> still havent found out what is wrong with i2c.

```
sudo bump
```

You might be able to find them in your sys/bus/platform. But if you can't you might just have to use hwmon.

If you do then change your conkyrc to ```
${platform blahblah temp #
```

That's all i got.

---

### Post by tamoneya on 2008-07-31
> **easybake said:**
> You might be able to find them in your sys/bus/platform. But if you can't you might just have to use hwmon.

If you do then change your conkyrc to ```
${platform blahblah temp #
```

That's all i got.

I couldnt get platform to work but I did get hwmon to work.  While poking through directories I ran this command and got an interesting result:```
cat /sys/class/hwmon/hwmon1/device/temp1_label 
Core 0

```
and when I used hwmon2 instead of hwmon1 i found my other core ( i have a c2d).  So I added this code to conky and it worked.
```
${color #888888}Core 0: ${color #CCCCCC}${hwmon 1 temp 1} C  ${color #888888}Core 1: ${color #CCCCCC}${hwmon 2 temp 1} C
```

---

### Post by SchmilK on 2009-05-26
> **tamoneya said:**
> I couldnt get platform to work but I did get hwmon to work.  While poking through directories I ran this command and got an interesting result:```
cat /sys/class/hwmon/hwmon1/device/temp1_label 
Core 0

```
and when I used hwmon2 instead of hwmon1 i found my other core ( i have a c2d).  So I added this code to conky and it worked.
```
${color #888888}Core 0: ${color #CCCCCC}${hwmon 1 temp 1} C  ${color #888888}Core 1: ${color #CCCCCC}${hwmon 2 temp 1} C
```

WOOWOO!

That fixed my problem as well :D

I appreciate your post :D

conky is some good fun for modifying!!

---

### Post by m_duck on 2009-05-26
I know it's solved now but just to add if you wanted to display any of the other temperatures as well, you could have something like the following in your config.```
${execi 10 sensors | grep "temp7:" | cut -d+ -f2}
```

This would display the temperature associated with "sensors" output for "temp7", e.g. **30.0°C**.

---

