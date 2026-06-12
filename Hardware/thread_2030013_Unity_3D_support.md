---
title: "Unity 3D support"
date: 2012-07-20
forum: Hardware
---

### Post by Dadolinko on 2012-07-20
Hello there. I have HP pavilion g6 with intel/radeon graphics. Since I do not have option to set fixxed graphic card inside of BIOS, [AMD/Intel Hybrid Graphics works !](http://ubuntuforums.org/showthread.php?t=1930450) does not work for me as I do not have option to set default graphic card inside of BIOS. 

Since I have intel HD 3000 (2nd generation lspci | grep VGA) and radeon hd 6470m. I wonder if there is anyway to have unity 3D support from intergrated graphic card. I have also did
```
apt-get install libgl1-mesa-dri
```

Did I forget something ? Or due to hybrid graphics without bios option I cannot run 3D at all

---

### Post by krustenBrot on 2012-07-20
Please specify: Can you select it? Is it crashing?
I am running unity 3D right now. (Intel HD as well) and using my dedicated graphics card just for single applications

---

### Post by Dadolinko on 2012-07-20
Yes, so as I said. I do not have option in bios to select which graphic card I would like to use. If I install drivers via topic I gave before for AMD/Intel every time I do 
```
aticonfig --initial -f
``` 
and reboot notebook, I get thrown into low graphic mode. 

When I have freshly installed ubuntu 12.04 under graphics it says that I have **vesa sandy bridge**

```
/usr/lib/nux/unity_support_test -p
```
says that I cannot run unity 3D

with ```
apt-get install libgl1-mesa-dri
``` 3D doesn't work either.

I can run ubuntu (unity 3d). But for instance, lets say I have installed cairo-dock and if i want to run Cairo-dock with openGL, instead of icons i see black squares and it lags super alot/stop responding

---

### Post by N0oki3 on 2012-07-23
I have the same problem :d

---

### Post by N0oki3 on 2012-07-26
bump

---

### Post by N0oki3 on 2012-08-02
any1 know solution ?

---

