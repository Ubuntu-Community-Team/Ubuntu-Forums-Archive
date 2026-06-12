---
title: "Laptop doesn't switch to external monitor"
date: 2012-07-17
forum: Hardware
---

### Post by frankbooth on 2012-07-17
Hello folks,

I've got an Asus 1001PX netbook running Lubuntu which I want to connect to an external monitor through VGA. Unfortunetly it doesn't work as the external monitor just goes to sleep. The monitor isn't broken, as it works on other machines. 

I'm not sure what's wrong, but I believe it could be my graphics card not being configured to use multiple/external displays.

Some system info that could be of use;

**xrandr:**
```

Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+   65.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  

```

**lspci | grep VGA:**
```

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

```

Any help would be very appreciated, as I've got no clue :(.

---

### Post by frankbooth on 2012-07-22
Bump.

---

